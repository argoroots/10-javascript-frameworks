<script setup>
import { ref, onMounted } from 'vue'
import TodoList from './components/TodoList.vue'
import TodoForm from './components/TodoForm.vue'

const todos = ref([])
const todoText = ref('')

onMounted(() => {
  const existingTodos = localStorage.getItem('todos')
  todos.value = JSON.parse(existingTodos) || []
})

function addTodo() {
  todos.value.push(todoText.value)
  localStorage.setItem('todos', JSON.stringify(todos.value))
}
</script>

<template>
  <img alt="Vue logo" src="./assets/logo.png" />

  <todo-list :todos="todos" />
  <todo-form v-model="todoText" @submit="addTodo" />
</template>

<style>
#app {
  font-family: system-ui;
  font-size: 0.8rem;
}
</style>
