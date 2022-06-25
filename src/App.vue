<template>
  <section class="container">
    <user-data :first-name="firstName" :last-name="lastName" :age="age"></user-data>

    <button @click="newAge">Change Age</button>
    <div>
      <input type="text" placeholder="First Name" v-model.lazy="firstName" />
      <input type="text" placeholder="Last Name" ref="lastNameInput" />
      <button @click="setLastName">Set Last Name</button>
    </div>
  </section>
</template>

<script setup>
import { ref, watch } from "vue";

import UserData from "./components/UserData.vue";

const age = ref(30)
const firstName = ref('')
const lastNameInput = ref(null)
const lastName = ref('')

watch(age, ((newValue, oldValue) => {
  console.log('Old age: ' + oldValue);
  console.log('New age: ' + newValue);
}))

watch([firstName, lastName], ((newValues, oldValues) => {
  console.log('Old first name: ' + oldValues[0]);
  console.log('New first name: ' + newValues[0]);
  console.log('Old last name: ' + oldValues[1]);
  console.log('New last name: ' + newValues[1]);
}))

function newAge() {
  return age.value = 33;
}

function setLastName() {
  return lastName.value = lastNameInput.value.value
}

</script>

<style>
* {
  box-sizing: border-box;
}

html {
  font-family: sans-serif;
}

body {
  margin: 0;
}

.container {
  margin: 3rem auto;
  max-width: 30rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 1rem;
  text-align: center;
}
</style>