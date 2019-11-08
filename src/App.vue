<template>
  <div>
    <Navbar @change-page="changePage"></Navbar>
    <transition name="home" mode="out-in">
      <Content v-if="page === 'home'" key="home"></Content>
      <Uploader v-if="page === 'uploader'" key="uploader"></Uploader>
    </transition>
  </div>
</template>

<script>
import Navbar from "./components/Navbar";
import Content from "./components/Content";
import Uploader from "./components/Uploader";

export default {
  data() {
    return {
      page: "home"
    };
  },
  components: {
    Navbar,
    Content,
    Uploader
  },
  methods: {
    changePage(value) {
      this.page = value;
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