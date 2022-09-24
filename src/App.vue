<template>
  <div id="app">
    <Home />
  </div>

</template>

<script>
import Home from "@/pages/home";
export default {
  name: 'App',
  components: {
    Home
  }
}
</script>

<style>
@import url('./styles/reset.css');
#app {
  font-family: "Roboto Light", sans-serif;
  padding: 10px;
}
</style>
