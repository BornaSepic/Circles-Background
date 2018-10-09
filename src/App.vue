<template>
  <div id="app">
    <BackgroundContainer />
  </div>
</template>

<script>
import BackgroundContainer from './components/BackgroundContainer.vue'

export default {
  name: 'App',
  components: {
    BackgroundContainer
  }
}
</script>

<style>
body{
  margin: 0px;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 0px;
  height: 100vh;
}
</style>
