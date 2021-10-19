<script setup>
import { defineProps, defineEmits, computed } from 'vue'

const props = defineProps({
  modelValue: { type: String, default: '' }
})

const emit = defineEmits([
  'update:modelValue',
  'submit'
])

const todo = computed({
  get() {
    return props.modelValue
  },
  set(val) {
    emit('update:modelValue', val)
  }
})

function submitTodo() {
  emit('submit')
  todo.value = ''
}
</script>

<template>
  <form @submit.prevent="submitTodo">
    <input v-model="todo" placeholder="What needs to be done?" />
    <button type="submit">Add Todo</button>
  </form>
</template>
