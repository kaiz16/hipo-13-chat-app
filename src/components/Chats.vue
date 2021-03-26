<template>
  <div class="wrapper">
    <div class="message" v-for="message in messages" v-bind:key="message._id">
      <!-- how to use font-awwesome in Vue?? -->
      <!-- import '@fortawesome/fontawesome-free/css/all.css' -->
      <div style="width: 10vw" class="fa fa-user-circle fa-3x"></div>
      <div style="width: 90vw">
        <div class="chatLog">
          <b>{{ message.username }}</b>
          <i>{{ message.created_at }}</i>
        </div>
        <div class="chatBubble">
          <p>{{ message.text }}</p>
        </div>
      </div>
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
  display: flex;
  margin-bottom: 20px;
}
.chatLog {
  display: flex;
  justify-content: space-between;
}
.chatBubble {
  padding:10px;
  border:1px solid black;
  border-radius: 5px  20px 20px;
}
p {
  margin: 0;
}
</style>
