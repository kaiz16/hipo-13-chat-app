<template>
  <div class="wrapper">
    <input type="text" v-model="newMessage" />
    <button v-on:click="sendMessage()">Submit</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newMessage: "",
    };
  },
  methods: {
    sendMessage() {

      if (this.newMessage.length === 0 ){
        alert('no')
        return
      }

      var url = "https://gg-chat-app-api.herokuapp.com/messages/create";

      fetch(url, {
        method: "POST",
        body: JSON.stringify({
          username: sessionStorage.getItem('username'),
          text: this.newMessage,
        }),
        headers: {
          "Content-type": "application/json",
        },
      })
        .then((response) => response.json())
        .then((json) => {
          console.log(json)
          this.newMessage = ''
        });
    },
  },
};
</script>
<style></style>
