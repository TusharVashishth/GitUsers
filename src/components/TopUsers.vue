<template>
  <div class="topUser">
    <h3>Top Users</h3>
    <div class="topUser__list" v-if="topUsers?.length > 0">
      <div class="topUser__content" v-for="user in topUsers" :key="user.id">
        <img :src="user.avatar_url" alt="user" :key="user" />
        <p>{{ user.login }}</p>
      </div>
    </div>
    <div class="topUser__list" v-else>
      <div
        class="topUser__content topUser__contentLoading"
        v-for="color in bgColors"
        :key="color"
        :style="{ backgroundColor: color }"
      >
        <h5>Loading...</h5>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      topUsers: [],
      bgColors: [
        "#ffadad",
        "#ffc6ff",
        "#bdb2ff",
        "#a0c4ff",
        "#9bf6ff",
        "#caffbf",
        "#fdffb6",
        "#ffd6a5",
      ],
    };
  },
  created() {
    fetch("https://api.github.com/users?per_page=10")
      .then((res) => res.json())
      .then((data) => (this.topUsers = data))
      .catch((err) => console.log(err));
  },
};
</script>

<style>
.topUser {
  padding: 10px;
}
.topUser__list {
  display: flex;
  overflow-x: scroll;
  margin-bottom: 10px;
  padding: 10px;
}

.topUser__list::-webkit-scrollbar {
  display: none;
}
.topUser__content {
  display: flex;
  flex-direction: column;
  margin-right: 10px;
  background-color: #54565e;
  border-radius: 10px;
  transition: all 500ms;
  padding: 0px 10px;
  padding-top: 10px;
  padding-bottom: 5px;
  cursor: pointer;
}

.topUser__content:hover {
  transform: scale(1.08);
}
.topUser__content > img {
  width: 150px;
  height: 150px;
  object-fit: contain;
}
.topUser__contentLoading {
  display: flex;
  justify-content: center;
  align-items: center;
  min-width: 180px;
  height: 180px;
  color: #000;
}
/* * Media Query */
@media screen and (max-width: 768px) {
  .topUser__list {
    margin-bottom: 50px;
  }
}
</style>