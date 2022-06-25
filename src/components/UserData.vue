<template>
  <div>
    <h2>{{ userName }}</h2>
    <h3>{{ age }}</h3>
  </div>
</template>

<script setup>
import { defineProps, computed } from "vue";

const props = defineProps({
  firstName: String,
  lastName: String,
  age: Number
})

const userName = computed(() => `${props.firstName} ${props.lastName}`)
</script>