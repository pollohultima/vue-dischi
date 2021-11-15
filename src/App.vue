<template>
  <div id="app">
    <SiteHeader />
  </div>
</template>

<script>
import SiteHeader from "./components/SiteHeader.vue";
//import SiteMain from "./components/SiteMain.vue";

export default {
  name: "App",
  components: {
    SiteHeader,
  },
};
</script>

<style lang="scss">
@import "../node_modules/bootstrap/scss/bootstrap.scss";
</style>
