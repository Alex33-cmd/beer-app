<script setup>
import Heading from './components/Heading.vue'
import Beer from './components/Beer.vue'
</script>

<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <Heading msg="Beer App v0.3" />
  <Beer />
</template>

<style>
html {
  background: #000;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #fff700;
  margin-top: 60px;
}
</style>
