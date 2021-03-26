<template>
  <div id="app">
    <!-- If user is not logged in authenticate first -->
    <Authenticate
      v-if="isLoggedIn === false"
      v-on:loggedIn="isLoggedIn = true"
    ></Authenticate>
    
    <!-- else show chats -->
    <div class="main" v-else>
      <Chats></Chats>
      <SendMessage></SendMessage>
    </div>
  </div>
</template>

<script>
import Authenticate from "./components/Authenticate.vue";
import Chats from "./components/Chats.vue";
import SendMessage from "./components/SendMessage.vue";
export default {
  name: "App",
  data() {
    return {
      isLoggedIn: false, // is flag to check for authentication
    };
  },
  components: {
    Authenticate,
    Chats,
    SendMessage,
  },
};
</script>

<style>
html,
body {
  padding: 0;
  margin: 0;
  background: #edf1f5;
  width: 100%;
  height: 100%;
}
</style>
