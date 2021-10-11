<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <Youtube/>
  <Vimeo/>
</template>

<script>
import Youtube from './components/Youtube.vue'
import Vimeo from './components/Vimeo.vue'

export default {
  name: 'App',
  components: {
    Youtube,
    Vimeo,
  }
}
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
