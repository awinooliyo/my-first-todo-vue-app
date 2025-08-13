<template>
  <div class="counter">
    <h2>My Counter component</h2>
    <div class="count-display">{{ count }}</div>
    <div class="buttons">
      <button @click="decrement" :disabled="count <= 0">-</button>
      <button @click="increment">+</button>
      <button @click="reset">Reset</button>
    </div>
    <p>You've clicked {{ totalClicks }} times total!</p>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

//Reactive State
const count = ref(0)
const clicks = ref(0)

//Computed Property
const totalClicks = computed(() => clicks.value)

//Methods
const increment = () => {
  count.value++
  clicks.value++
}

const decrement = () => {
  if (count.value > 0) {
    count.value--
    clicks.value++
  }
}

const reset = () => {
  count.value = 0
  clicks.value++
}
</script>

<style scoped>
.counter {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  padding: 5rem;
  border: 2px solid #42b883;
  border-radius: 10px;
  margin: 1rem auto;
  background-color: #f9f9f9;
}

.count-display {
  font-size: 3rem;
  font-weight: bold;
  color: #42b883;
  margin: 1rem 0;
}

button {
  padding: 0.5rem 1rem;
  font-size: 1.1rem;
  border: 2px solid #42b883;
  background: white;
  color: #42b883;
  border-radius: 5px;
  cursor: pointer;
  transition: all 0.2s;
}

button:hover:not(:disabled) {
  background: #42b883;
  color: white;
}

button:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}
</style>
