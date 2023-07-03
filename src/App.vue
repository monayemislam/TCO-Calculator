<template>

  <div class="d-flex justify-content-center">
    <NybSysCalculator></NybSysCalculator>
  </div>
  
</template>

<script>
import NybSysCalculator from "./components/NybsysCalculator.vue";

export default {
  name: "App",
  components: {
    NybSysCalculator,
  },
};
</script>

<style scooped>
html,
body {
  padding: 0;
  margin: 0px;
  box-sizing: border-box;
}
#app {
  /* font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px; */
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
</style>
