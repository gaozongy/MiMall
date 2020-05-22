<template>
  <div id="app">
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: "app",
  mounted() {
    if (this.$cookie.get("userId")) {
      this.getUser();
      this.getCartCount();
    }
  },
  methods: {
    getUser() {
      this.axios.get("/user").then(response => {
        this.$store.dispatch("saveUserName", response.username);
      });
    },
    getCartCount() {
      this.axios.get("/carts/products/sum").then(response => {
        this.$store.dispatch("saveCartCount", response);
      });
    }
  }
};
</script>

<style lang="scss">
@import "./assets/scss/reset.scss";
</style>
