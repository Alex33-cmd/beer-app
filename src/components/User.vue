<script setup>
import { ref } from 'vue'

defineProps({
  msg: String
})

const API_URL = `https://random-data-api.com/api/`
const data = ['users/random_user', 'beer/random_beer']

const randomUser = ref(data[0])
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
</script>

<template>
    <h2>User</h2>
  <p v-if="!user">Loading...</p>
  <!-- <pre v-else>{{ user }}</pre> -->
  <ul v-else>
    <li><img id="userAvatar" alt="User avatar" v-bind:src="user.avatar" /></li>
    <li><span class="option">Name:</span> {{ user.first_name + ' ' + user.last_name }}</li>
    <li><span class="option">Age:</span> {{ calcAge(user.date_of_birth)  }}</li>
    <li><span class="option">Employment:</span> {{ user.employment.title }}</li>
  </ul>
</template>

<style scoped>
ul {
  list-style: none;
  padding: 0;
}
#userAvatar {
  max-width: 200px;
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
