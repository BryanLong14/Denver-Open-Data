<template>
  <div id="app">
    <!-- <img src="./assets/logo.png"> -->
    <CrimeMap msg="Welcome to Denver Open Data Map"/>
  </div>
</template>

<script>
import CrimeMap from "./components/CrimeMap.vue";

export default {
  name: "app",
  components: {
    CrimeMap
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
