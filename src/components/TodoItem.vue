<script setup>
// import { defineProps, defineEmits } from 'vue'

const props = defineProps({
  todo: Object,
})
const emit = defineEmits(['toggle-done', 'delete-todo'])

function toggle() {
  emit('toggle-done', props.todo.id)
}

function remove() {
  emit('delete-todo', props.todo.id)
}
</script>

<template>
  <li :style="{ textDecoration: todo.done ? 'line-through' : 'none' }" class="todo-item">
    <input type="checkbox" :checked="todo.done" @change="toggle" />
    {{ todo.text }}
    <button @click="remove">❌</button>
  </li>
</template>

<style scoped>
.todo-item {
  display: flex;
  align-items: center;
  margin-bottom: 0.5rem;
}

button {
  margin-left: auto;
  border: none;
  background: transparent;
  color: #ff4d4f;
  font-size: 1.2rem;
  cursor: pointer;
  transition: color 0.2s;
}

button:hover {
  color: #ff7875;
}
</style>
