<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <Calculadora msg="Calculadora Básica"/>
  </div>
</template>

<script>
import Calculadora from './components/Calculadora.vue'

export default {
  name: 'App',
  components: {
    Calculadora
  }
}
</script>

<style>
@font-face {
    font-family: FonteTitle;
    src: url("../src/assets/fonts/Saira-Bold.ttf");
}
#app {
  font-family: FonteTitle;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
