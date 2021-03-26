<template>
  <div class="wrapper">
    <!-- card component -->
    <div class="card">
      <input placeholder="Username" v-model="username" />
      <!-- method -->
      <button v-on:click="login()">Login</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      username: "",
    };
  },
  methods: {
    login() {
      // data validation ()
      if (this.username.length === 0){
        alert('No falsey values')
        return
      }

      // set the username in the session storage
      sessionStorage.setItem('username', this.username);
      // emit an event back to parent
      this.$emit('loggedIn')
    },
  },
};
</script>

<style>
.card {
  background: #ffffff;
  width: 200px;
  margin: 0 auto;
}
</style>
