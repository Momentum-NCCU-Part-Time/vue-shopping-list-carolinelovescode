<script setup>
import { ref } from 'vue'
import App from '../../App.vue'

const lists = ref([''])

fetch('http://localhost:3000/notes/', {
  method: 'GET'
})
  .then((res) => res.json())
  .then((item) => (lists.value = item))
</script>

<template>
  <App />
  <div class="shop-list">
    <h2>CarolineLovesShoppingList</h2>
    <li></li>
  </div>
</template>
