<script setup>
import { defineProps, defineEmits } from 'vue'
import TodoItem from './TodoItem.vue'

const { todos } = defineProps({
  todos: Array,
})

const emit = defineEmits(['toggle-done', 'delete-todo'])

function toggleDone(id) {
  emit('toggle-done', id)
}

function deleteTodo(id) {
  emit('delete-todo', id)
}
</script>

<template>
  <ul>
    <TodoItem
      v-for="todo in todos"
      :key="todo.id"
      :todo="todo"
      @toggle-done="toggleDone"
      @delete-todo="deleteTodo"
    />
  </ul>
</template>

<style scoped>
ul {
  list-style: none;
  padding-left: 0;
  margin: 0;
}
</style>
