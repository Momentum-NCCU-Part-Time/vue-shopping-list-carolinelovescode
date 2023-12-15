<script setup>
import { ref } from 'vue'

const lists = ref['']
const listTitle = ref('')
</script>

// lists and their items on the page by Tuesday

<template>
  <div>
    <h1>Vue Shopping List</h1>
    <!-- your code here -->
  </div>
  <h2>{{ lists || 'You Got It All' }}</h2>

  <input v-model="lists" placeholder="What Do You Need?" />
</template>

<style scoped></style>
