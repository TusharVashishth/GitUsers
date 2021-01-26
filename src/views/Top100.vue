<template>
  <div class="container">
    <div class="py-3">
      <h3>Top Users</h3>
    </div>
    <div class="loading" v-if="isLoading">
      <div class="spinner-grow text-success" role="status"></div>
    </div>
    <div class="row" v-else>
      <div class="col-lg-4 col-md-6" v-for="user in users" :key="user.id">
        <div class="top100 bg-dark">
          <div class="top100__left">
            <img :src="user.avatar_url" alt="user" />
          </div>
          <div class="top100__right">
            <h5>{{ user.login }}</h5>
            <a :href="user.html_url" target="__blank" class="btn btn-warning"
              >GitHub
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      users: [],
      isLoading: true,
    };
  },
  mounted() {
    this.isLoading = true;
    fetch("https://api.github.com/users?per_page=80")
      .then((res) => res.json())
      .then((data) => {
        this.users = data;
        this.isLoading = false;
      })
      .catch((err) => console.log(err));
  },
};
</script>

<style>
.top100 {
  display: flex;
  border-radius: 5px;
  z-index: 1;
  margin-bottom: 40px;
}
.top100__left {
  flex: 0.2;
}
.top100__left > img {
  width: 150px;
  height: 150px;
  object-fit: contain;
}
.top100__right {
  flex: 0.8;
  padding-left: 20px;
}
.loading {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 80vh;
}
</style>