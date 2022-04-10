<script setup>
import { ref } from 'vue'

defineProps({
  msg: String
})

const API_URL = `https://random-data-api.com/api/`
const randomBeer = ref('beer/random_beer')
const beer = ref(null)

async function fetchBeer() {
  beer.value = null;
  const url = `${API_URL}${randomBeer.value}`
  beer.value = await (await fetch(url)).json()
}
fetchBeer()

function Capitalize(str) {
  return str[0].toUpperCase() + str.slice(1)
}
</script>

<template>
  
  <!-- <pre v-else>{{ beer }}</pre> -->
  <div class="content-wrapper-beer-user">
    <h2>Here is your beer:</h2>
    <div class="beer-user-options-container" v-if="!beer"></div>
    <div class="beer-user-options-container" v-else>
      <ul>
        <!-- <li v-for="opts, keyName in beer" :key="keyName">
          <span class="option">{{ Capitalize(keyName) }}: </span>
          <span class="item">{{opts}}</span>
        </li> -->
        <li><span class="beer-user-option">Brand:</span> {{ beer.brand }}</li>
        <li><span class="beer-user-option">Name:</span> {{ beer.name }}</li>
        <li><span class="beer-user-option">Style:</span> {{ beer.style }}</li>
        <li><span class="beer-user-option">Hop:</span> {{ beer.hop }}</li>
        <li><span class="beer-user-option">Yeast:</span> {{ beer.yeast }}</li>
        <li><span class="beer-user-option">Malts:</span> {{ beer.malts }}</li>
        <li><span class="beer-user-option">Ibu:</span> {{ beer.ibu }}</li>
        <li><span class="beer-user-option">Alcohol:</span> {{ beer.alcohol }}</li>
        <li><span class="beer-user-option">Blg:</span> {{ beer.blg }}</li>
      </ul>
    </div>
    <button @click="fetchBeer">Get New Beer</button>
  </div>
  
</template>

<style scoped>
.beer-user-options-container {
  height: 250px;
  text-align: left;
}
ul {
  list-style: none;
  padding: 0;
}
button {
  position: absolute;
  left: calc(50% - 80px);
  font-size: 1.2rem;
  padding: 1rem;
  /* margin: 1rem; */
  background: var(--primary-color-3);
  border: 1px var(--primary-color-6) solid;
  border-radius: var(--border-radius);
  box-shadow: 3px 3px var(--primary-color-7);
}
button:hover {
  transform: scale(1.03);
  box-shadow: 6px 6px 1px var(--primary-color-5);
  cursor: pointer;
}
button:active {
  transform: scale(0.97);
  box-shadow: 2px 2px var(--primary-color-7);
  cursor: pointer;
}
</style>
