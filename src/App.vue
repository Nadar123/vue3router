<template>
  <div id="app">
    <div id="nav">
      <NavBar></NavBar>
      <transition name="fade">
        <router-view :key="$route.path" />
      </transition>
    </div>
  </div>
</template>
<script>
import NavBar from "./components/NavBar.vue";
export default {
  components: {
    NavBar
  }
};
</script>
<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
// .slide-enter-active,
// .slide-leave-active {
//   transition: opacity 0.6s, transform 1s;
// }
// .slide-enter,
// .slide-leave-to {
//   opacity: 0;
//   transform: translateX(-2%);
// }
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease-in-out;
}
.fade-enter,
.fade-leave-to {
  opacity: 0;
}
</style>
