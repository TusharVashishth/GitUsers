<template>
  <div class="navbar">
    <div class="navbar__logo">
      <img src="../../assets/images/github1.png" alt="logo" />
      <h3>GitUsers</h3>
    </div>
    <div class="navbar__links" v-if="width > 768">
      <router-link :to="{ name: 'Home' }">Home</router-link>
      <router-link :to="{ name: 'Search' }">Search</router-link>
      <router-link :to="{ name: 'TopUsers' }">Top Users</router-link>
    </div>
  </div>
</template>

<script>
export default {
  props: ["width"],
};
</script>

<style scoped >
.navbar {
  display: flex;
  justify-content: space-between;
  padding: 10px;
  /* position: fixed;
  top: 0;
  width: 100%; */
}
.navbar__logo {
  display: flex;
  align-items: center;
  justify-content: center;
}
.navbar__logo > img {
  width: 40px;
  object-fit: contain;
}
.navbar__logo > h3 {
  font-family: "Playfair Display", serif;
  font-weight: bold;
  margin-left: 5px;
}

.navbar__links {
  text-decoration: none;
  font-size: 16px;
}
.navbar__links a {
  color: #fff;
  margin-right: 10px;
  font-weight: bold;
}
.navbar__links a:hover {
  text-decoration: none;
  color: #54565e;
}
.router-link-active {
  color: #caffbf !important;
}
</style>