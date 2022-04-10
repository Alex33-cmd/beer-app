<script setup>
import { ref } from 'vue'

defineProps({
  msg: String
})

const API_URL = `https://random-data-api.com/api/`
const data = ['users/random_user', 'beer/random_beer']

const randomBeer = ref(data[1])
const beer = ref(null)

async function fetchData() {
  beer.value = null;
  const url = `${API_URL}${randomBeer.value}`
  beer.value = await (await fetch(url)).json()
}

fetchData()

function Capitalize(str) {
  return str[0].toUpperCase() + str.slice(1)
}

</script>

<template>
  <h2>Beer</h2>
  <p v-if="!beer">Loading...</p>
  <!-- <pre v-else>{{ beer }}</pre> -->
  <ul v-else>
    <!-- <li v-for="opts, keyName in beer" :key="keyName">
      <span class="option">{{ Capitalize(keyName) }}: </span>
      <span class="item">{{opts}}</span>
    </li> -->
    <li><span class="option">Brand:</span> {{ beer.brand }}</li>
    <li><span class="option">Name:</span> {{ beer.name }}</li>
    <li><span class="option">Style:</span> {{ beer.style }}</li>
    <li><span class="option">Hop:</span> {{ beer.hop }}</li>
    <li><span class="option">Yeast:</span> {{ beer.yeast }}</li>
    <li><span class="option">Malts:</span> {{ beer.malts }}</li>
    <li><span class="option">Ibu:</span> {{ beer.ibu }}</li>
    <li><span class="option">Alcohol:</span> {{ beer.alcohol }}</li>
    <li><span class="option">Blg:</span> {{ beer.blg }}</li>
  </ul>
  <button @click="fetchData">Fetch next beer</button>
</template>

<style scoped>
ul {
  list-style: none;
  padding: 0;
}
.option{
  font-weight: 800;
  color: rgb(124, 75, 0);
}
button {
  font-size: 1.2rem;
  padding: 1rem;
  background-color: bisque;
}
</style>
