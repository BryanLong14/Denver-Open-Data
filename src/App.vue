<template>
  <div id="app">
    <!-- <img src="./assets/logo.png"> -->
    <BaseMap msg="Welcome to Denver Open Data Map"/>
  </div>
</template>

<script>
import BaseMap from "./components/BaseMap.vue";

export default {
  name: "app",
  components: {
    BaseMap
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
