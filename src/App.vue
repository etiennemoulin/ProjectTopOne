<template>
  <Raccoon msg="Welcome to Your Vue.js App"/>
</template>
<!-- vif velse contenu conditionnel -->
<script>
import Raccoon from './components/Raccoon.vue'

export default {
  name: 'App',
  components: {
    Raccoon
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
