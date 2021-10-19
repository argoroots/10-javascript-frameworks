<script setup>
import { defineProps } from 'vue'

const props = defineProps({
  todos: { type: Array, required: true }
})
</script>

<template>
  <ul>
    <li v-for="todo in todos" :key="todo">{{ todo }}</li>
  </ul>
</template>

<style scoped>
ul {
  padding: 0;
  list-style: none;
}
</style>
