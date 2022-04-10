<script setup>
import { ref } from 'vue'

const API_URL = `https://random-data-api.com/api/`;
const randomUser = ref('users/random_user')
const user = ref(null)

async function fetchUser() {
  user.value = null;
  const url = `${API_URL}${randomUser.value}`
  user.value = await (await fetch(url)).json()
}

fetchUser()

function calcAge(birthDate) {
  const today = new Date();
  const birthday = new Date(birthDate);
  
  let age = today.getFullYear() - birthday.getFullYear();
  const month = today.getMonth() - birthday.getMonth();

  if (month < 0 || (month === 0 && today.getDate() < birthday.getDate())) {
    age--
  }
  return age;
}

let isLoaded = false;
function onImgLoad() {
  isLoaded = true;
  console.log(isLoaded);
}
</script>

<template>
  <div class="content-wrapper-beer-user" v-if="!user"></div>
  <!-- <pre v-else>{{ user }}</pre> -->
  <div class="content-wrapper-beer-user" v-else>
    <h2>Hello, {{user.first_name}}!</h2>
    <img id="userAvatar" alt="User avatar" v-bind:src="user.avatar" onerror="this.onerror=null;this.src='src/assets/no-image.png'" />
    <ul>
      <li><span class="beer-user-option">Name:</span> {{ user.first_name + ' ' + user.last_name }}</li>
      <li><span class="beer-user-option">Age:</span> {{ calcAge(user.date_of_birth)  }}</li>
      <li><span class="beer-user-option">Employment:</span> {{ user.employment.title }}</li>
    </ul>
  </div>
</template>

<style scoped>
img {
  margin: 0 auto;
  border: 1px var(--primary-color-6) solid;
  border-radius: 50%;
  /* border-radius: var(--border-radius); */
  box-shadow: 3px 3px 6px 0px var(--primary-color-5);
}
ul {
  text-align: left;
  list-style: none;
  padding: 0;
}
#userAvatar {
  max-width: 200px;
}
</style>
