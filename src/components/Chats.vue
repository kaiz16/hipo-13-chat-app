<template>
  <div class="wrapper">
    <div class="message" v-for="message in messages" v-bind:key="message._id">
      <p class="text">{{ message.text }}</p>
      <p class="time">{{ message.created_at }}</p>
      <p class="user">{{ message.username }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      messages: [],
    };
  },
  mounted() {
    setInterval(() => {
      this.getMessages();
    }, 1000);
  },
  methods: {
    getMessages() {
      // Get method to get all the messages
      fetch("https://gg-chat-app-api.herokuapp.com/messages")
        .then((response) => response.json())
        .then((json) => {
          this.messages = json;
        });
    },
  },
};
</script>
<style>
.message {
  margin-left: 10px;
}
</style>
