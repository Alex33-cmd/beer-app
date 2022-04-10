<script setup>
import Heading from './components/Heading.vue'
import User from './components/User.vue'
import Beer from './components/Beer.vue'
</script>

<template>
  <div >
    <img alt="Beer logo" src="./assets/logo.png" />
    <Heading msg="Beer App v0.5" />
    <User />
    <Beer />
  </div>
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
