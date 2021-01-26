<template>
  <Banner />
  <TopUser />
  <Footer />
</template>

<script>
import Banner from "../components/Banner";
import TopUser from "../components/TopUsers";
import Footer from "../components/Footer";

export default {
  name: "Home",
  components: { Banner, TopUser, Footer },
};
</script>
