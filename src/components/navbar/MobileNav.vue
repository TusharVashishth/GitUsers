<template>
  <div class="mobileNavbar">
    <div class="mobileNavbar__iconText">
      <router-link :to="{ name: 'Home' }">
        <i class="fas fa-home"></i>
      </router-link>
    </div>
    <div class="mobileNavbar__iconText">
      <router-link :to="{ name: 'Search' }">
        <i class="fas fa-search"></i>
      </router-link>
    </div>
    <div class="mobileNavbar__iconText">
      <router-link :to="{ name: 'TopUsers' }">
        <i class="fas fa-user"></i>
      </router-link>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style>
.mobileNavbar {
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
  background-color: #191414;
  display: flex;
  justify-content: space-around;
  padding-top: 10px;
  padding-bottom: 5px;
  padding: 10px;
  z-index: 1000;
}
.mobileNavbar__iconText {
  display: flex;
  align-items: center;
}
.mobileNavbar__iconText > a {
  text-decoration: none;
  color: #fff;
}
.router-link-active {
  color: #caffbf !important;
}
.mobileNavbar__iconText:hover {
  text-decoration: none;
  color: #fff;
}
</style>