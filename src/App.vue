<template>
  <div id='app'>
    <ToDo msg='I want to do...'/>
  </div>
</template>

<script>
import ToDo from './components/ToDo.vue'

export default {
  name: 'App',
  components: {
    ToDo
  }
}
</script>

<style>
  html {
    height: 100%;
    width: 100%;
    background-image: linear-gradient(to bottom, #af85b8, #bca1ca, #cbbdda, #ded9e8, #f4f4f4);
  }
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>
