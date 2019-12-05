<template>
<div id="app">
  <router-view></router-view>

</div>
</template>

<script>
import VideoStory from "./components/VideoStory"
import Home from "./views/Home"



export default {
  name: "App",
  components: {
    VideoStory
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
