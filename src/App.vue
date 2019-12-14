<template>
  <div id="app">
    <cadastra-conta></cadastra-conta>
  </div>
</template>

<script>
import cadastraConta from "./components/cadastraConta";

export default {
  name: 'app',
  components: {
    cadastraConta
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
