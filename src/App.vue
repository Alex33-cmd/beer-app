<script setup>
import { ref } from 'vue'
import Heading from './components/Heading.vue'
import User from './components/User.vue'
import Beer from './components/Beer.vue'
</script>

<template>
  <Heading />
  <div class="content-wrapper">
    <User />
    <Beer />
  </div>
</template>

<style>
:root {
  --color-black: #000;
  --color-white: #fff;
  --primary-color-0: #FFC48C;
  --primary-color-1: #EBA15B;
  --primary-color-2: #D38235;
  --primary-color-3: #AF6219;
  --primary-color-4: #894403;
  --primary-color-5: #643335;
  --primary-color-6: #3F2021;
  --primary-color-7: #25282A;
  --border-radius: 1rem;
}

html {
  background: var(--primary-color-0);
  background: radial-gradient(circle, rgba(255,196,140,1) 0%, rgba(235,161,91,1) 20%, rgba(211,130,53,1) 50%, rgba(175,98,25,1) 80%, rgba(137,68,3,1) 100%); 
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: var(--primary-color-7);
  margin: 0 auto;
  margin-top: 60px;
}
.header-wrapper{
  text-align: center;
}
.content-wrapper {
  max-width: 1000px;
  margin: 0 auto;
  /* display: flex;
  flex-flow: row wrap;
  justify-content: space-between; */
  display: grid;
  grid-template-columns: repeat(auto-fill, 400px);
  justify-content: center;
}
.content-wrapper-beer-user {
  text-align: center;
  position: relative;
  margin: 2rem;
  padding: 2rem;
  background: var(--primary-color-0);
  border: 1px var(--primary-color-5) solid;
  border-radius: var(--border-radius);
  -webkit-box-shadow: 3px 3px 6px 0px rgba(0,0,0,0.75);
  -moz-box-shadow: 3px 3px 6px 0px rgba(0,0,0,0.75);
  box-shadow: 3px 3px 6px 0px rgba(0,0,0,0.75);
}
.beer-user-option{
  font-weight: 800;
  color: var(--primary-color-4);
}
</style>
