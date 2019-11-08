<template>
  <div id="app">
    <Login />
    <!-- <Register /> -->
  </div>
  
</template>

<script>
import Login from './views/Login'
import Register from './views/Register'

export default {
  name: 'App',
  components: {
    Login,
    Register
  },
  data() {
    return {
      message: 'Hello world',
    };
  },
};
</script>

<style scoped>
</style>