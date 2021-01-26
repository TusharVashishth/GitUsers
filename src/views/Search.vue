<template>
  <div class="search">
    <div class="container">
      <form @submit.prevent="test" class="search__form">
        <input type="text" v-model="search" placeholder="Search Users" />
        <i class="fas fa-search"></i>
      </form>
      <div class="search__loading" v-if="isLoading">
        <div class="spinner-grow text-success" role="status"></div>
      </div>
      <div v-if="Object.keys(user).length > 0 && user?.message !== 'Not Found'">
        <div class="search__content">
          <div class="row">
            <div class="col-md-4">
              <div class="search__contentImg">
                <img :src="user?.avatar_url" :alt="user.login" />
              </div>
            </div>
            <div class="col-md-8">
              <ul class="list-group text-white">
                <li
                  class="list-group-item bg-dark d-flex justify-content-between align-items-center"
                >
                  Name
                  <span class="badge">{{ user?.login }}</span>
                </li>
                <li
                  class="list-group-item bg-dark d-flex justify-content-between align-items-center"
                >
                  Email
                  <span class="badge">{{
                    user.email ? user.email : "N/A"
                  }}</span>
                </li>
                <li
                  class="list-group-item bg-dark d-flex justify-content-between align-items-center"
                >
                  Bio
                  <span class="badge">{{ user.bio ? user.bio : "N/A" }}</span>
                </li>
                <li
                  class="list-group-item bg-dark d-flex justify-content-between align-items-center"
                >
                  Location
                  <span class="badge">{{
                    user.location ? user.location : "N/A"
                  }}</span>
                </li>
                <li
                  class="list-group-item bg-dark d-flex justify-content-between align-items-center"
                >
                  GitHub Url
                  <a
                    :href="user?.html_url"
                    target="__blank"
                    class="btn btn-link"
                    >Click here</a
                  >
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>
      <div
        class="search__loading"
        v-else-if="
          Object.keys(user).length > 0 && user?.message === 'Not Found'
        "
      >
        <h2>No User Found ☹</h2>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      search: "",
      isLoading: false,
      user: {},
    };
  },

  methods: {
    test() {
      this.user = {};
      this.isLoading = true;
      fetch(`https://api.github.com/users/${this.search}`)
        .then((res) => res.json())
        .then((data) => {
          this.user = data;
          this.isLoading = false;
        })
        .catch((err) => console.log(err));
    },
  },
};
</script>

<style>
.search {
  margin-top: 40px;
}
.search__form {
  display: flex;
  align-items: center;
}
.search__form > input {
  background-color: #54565e;
  color: #fff !important;
  width: 100%;
  border: none;
  padding: 10px;
  border-radius: 20px;
  outline: none;
}

.search__form > i {
  font-size: 25px;
  margin-left: 5px;
}
.search__loading {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 100px;
  border-radius: 10px;
}
.search__content {
  margin-top: 100px;
}
.search__contentImg img {
  width: 150px;
  height: 150px;
  object-fit: contain;
  border-radius: 10px;
}
.headColor {
  color: #caffbf;
}

/*  Media Query */

@media screen and (max-width: 768px) {
  .search__contentImg {
    display: flex;
    justify-content: center;
    margin-bottom: 20px;
  }
}
</style>