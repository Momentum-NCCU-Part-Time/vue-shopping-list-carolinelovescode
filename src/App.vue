<script setup>
import { ref } from 'vue'
import ShopForm from './assets/components/ShopForm.vue'

const lists = ref([])
// get the notes to show up by Tuesday
fetch('http://localhost:3000/notes/', {
  method: 'GET'
})
  .then((res) => res.json())
  .then((item) => (lists.value = item))
</script>

<template>
  <div>
    <h1>Caroline Loves Vue Shopping List</h1>
    <!-- your code here -->
  </div>

  <ShopForm />
</template>

<style scoped></style>
