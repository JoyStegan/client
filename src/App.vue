<template>
  <div>
    <Login @login="changeLogin" @change-page="changePage" v-if="!isLogin && page === 'login'"></Login>
    <Register v-if="page === 'register'" @change-page="changePage"></Register>
    <Navbar v-if="isLogin" @change-page="changePage" @login="changeLogin"></Navbar>
    <transition name="home" mode="out-in">
      <Content v-if="page === 'home' && isLogin" key="home"></Content>
      <Uploader v-if="page === 'uploader' && isLogin" key="uploader" @go="changePage"></Uploader>
    </transition>
  </div>
</template>

<script>
import Navbar from "./components/Navbar";
import Content from "./components/Content";
import Uploader from "./components/Uploader";
import Login from './views/Login'
import Register from './views/Register'

export default {
  name: 'App',
  components: {
    Login,
    Register,
    Navbar,
    Content,
    Uploader
  },
  data() {
    return {
      page: "login",
      isLogin: false
    };
  },
  methods: {
    changePage(value) {
      this.page = value;
    },
    changeLogin(value) {
      this.isLogin = value
    }
  },
  created () {
    if (localStorage.getItem('token')) {
      this.isLogin = true
      this.page = 'home'
    }
  }
};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css?family=Montserrat&display=swap');
* {
  font-family: 'Montserrat', sans-serif;
}

.fade-enter-active, .fade-leave-active {
  transition: opacity .8s
}
.fade-enter, .fade-leave-to {
  opacity: 0
}
.home-enter-active, .home-leave-active {
  transition: all .5s ease;
}
.home-enter, .home-leave-to /* .list-leave-active below version 2.1.8 */ {
  opacity: 0;
  transform: translateY(50px);
}

</style>