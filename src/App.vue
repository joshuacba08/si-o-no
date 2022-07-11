<template>
  <Indecision />
</template>

<script>
import Counter from "./components/Counter.vue";
import Indecision from "./components/Indecision.vue";

export default {
  name: "App",
  components: {
    Counter,
    Indecision,
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  padding:40px 10px;
  color: #2c3e50;
  min-height: 100vh;
  width: 100vw;
  background-color: #fefdff;
  background-image: url("data:image/svg+xml,%3Csvg width='20' height='20' viewBox='0 0 20 20' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='%23c7c6c8' fill-opacity='0.4' fill-rule='evenodd'%3E%3Ccircle cx='3' cy='3' r='3'/%3E%3Ccircle cx='13' cy='13' r='3'/%3E%3C/g%3E%3C/svg%3E");
}
</style>
