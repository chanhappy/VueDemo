<template>
  <div id="app">
    <AwesomeSwiperTest />
  </div>
</template>

<script>
// import HelloWorld from "./components/HelloWorld.vue";
import AwesomeSwiperTest from './components/AwesomeSwiperTest.vue'

export default {
  name: "App",
  components: {
    // HelloWorld,
    AwesomeSwiperTest
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
