<template>
  <div>
    <h2>{{ userName }}</h2>
    <h3>{{ age }}</h3>
  </div>
</template>

<script setup>
import { defineProps, computed, inject } from "vue";

const props = defineProps({
  firstName: String,
  lastName: String
})

const age = inject('age')

const userName = computed(() => `${props.firstName} ${props.lastName}`)
</script>