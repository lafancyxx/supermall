<template>
  <div id="app">
    <maintabbar />
    <router-view />
  </div>
</template>
<script>
import Maintabbar from "./components/content/maintabbar/Maintabbar.vue";
export default {
  name: "app",
  components: {
    Maintabbar,
  },
};
</script>


<style>
@import "assets/css/base.css";
</style>
