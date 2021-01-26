<template>
  <div v-if="screenWidth <= 768">
    <MobileNav />
  </div>
  <DesktopNav :width="screenWidth" />

  <router-view />
</template>
<script>
import DesktopNav from "./components/navbar/DesktopNav";
import MobileNav from "./components/navbar/MobileNav";
export default {
  components: {
    DesktopNav,
    MobileNav,
  },
  data() {
    return {
      screenWidth: null,
    };
  },
  mounted() {
    this.screenWidth = window.screen.width;
  },
};
</script>
<style>
@import url("https://fonts.googleapis.com/css2?family=Anton&family=Lato:ital@1&family=Playfair+Display&display=swap");

body {
  background-color: #040509;
}
#app {
  background-color: #040509;
  margin: 0;
  color: #fff;
  min-height: 100vh;
  overflow-x: hidden;
}
</style>
