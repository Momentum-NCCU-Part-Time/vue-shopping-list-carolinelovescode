<script setup>
import { ref } from 'vue'
// import ShopList from './ShopList.vue'
// import App from '../../App.vue'

const lists = ref([''])
// get the notes to show up
fetch('http://localhost:3000/notes/', {
  method: 'GET'
})
  .then((res) => res.json())
  .then((item) => (lists.value = item))
</script>

<template>
  <form class="shop-list">
    <input v-model="lists" type="text" class="add-list" />
    <button class="btn-add">I Need This</button>
    <!-- <p>{{ lists || 'You Got It All' }}</p> -->
  </form>
  <!-- <ShopList /> -->
</template>
