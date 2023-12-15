<script setup>
import { ref } from 'vue'
import ShopForm from './ShopForm.vue'

const lists = ref([''])
</script>

<template>
  <ShopForm />
  <div class="listOfShop">
    <li v-for="{ lists, title } in items">{{ title }}</li>
  </div>
</template>
