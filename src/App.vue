<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/loading.gif"> -->
    <ImageView/>
  </div>
</template>

<script>
import ImageView from './components/ImageView.vue'

export default {
  name: 'app',
  components: {
    ImageView
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
