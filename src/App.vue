<template>
  <div id="app">
    <!-- If user is not logged in authenticate first -->
    <Authenticate v-if="isLoggedIn === false" />
    <!-- else show chats -->
    <div class="main" v-else>
      <Chats />
      <SendMessage />
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
      isLoggedIn: false,
    };
  },
  components: {
    Authenticate,
    Chats,
    SendMessage,
  },
};
</script>

<style></style>
