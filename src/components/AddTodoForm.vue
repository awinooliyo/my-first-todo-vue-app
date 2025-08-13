<script setup>
import { defineEmits, ref } from 'vue'

const emit = defineEmits(['add-todo'])
const newTodo = ref('')

function submit() {
  const text = newTodo.value.trim()
  if (!text) return
  emit('add-todo', text)
  newTodo.value = ''
}
</script>

<template>
  <input
    v-model="newTodo"
    @keyup.enter="submit"
    placeholder="Add a todo and press Enter"
    autofocus
  />
</template>

<style scoped>
input {
  padding: 0.5rem;
  width: 100%;
  max-width: 400px;
  font-size: 1rem;
  margin-bottom: 1rem;
  border: 3px solid #42b883;
  border-radius: 5px;
  outline: none;
  transition: border-color 0.2s;
}

input:focus {
  border-color: #2c974b;
}
</style>
