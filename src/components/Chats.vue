<template>
  <div class="wrapper">
    <div class="message" v-for="message in messages" v-bind:key="message._id">
      <div class="leftColumn">
        <div class="userIcon">img</div>
      </div>
      <div class="rightColumn">
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
}
.leftColumn {
  width: 10%;
}
.rightColumn {
  width: 90%;
  margin-left: 10px;
  margin-bottom: 15px;
}
.userIcon {
  background: pink;
  border-radius: 50%;
  height: 40px;
  width: 40px;
  float: right;
}
.chatLog {
  display: flex;
  justify-content: space-between;
}
.chatBubble {
  background: white;
  padding: 15px;
  border: none;
  border-radius: 5px 20px 20px;
}
p {
  margin: 0;
}
@media only screen and (min-width: 1000px) {
  .leftColumn {
    width: 5%;
  }
}
</style>
