<template>
  <div id="app">
    <!-- <img src="./assets/logo.png"> -->
    <vueCalendarMarker/>
    <!-- <hello-world></hello-world> -->
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'
import vueCalendarMarker from './components/vue-calendar-marker'
export default {
  name: 'App',
  components: {
    vueCalendarMarker,
    HelloWorld
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
