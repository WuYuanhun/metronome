<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <Nome/>
</template>

<script>
import Nome from './components/Nome.vue'

export default {
  name: 'App',
  components: {
    Nome
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
