<script setup>
import { ref } from 'vue'
import ShopForm from './assets/components/ShopForm.vue'
import ShopList from './assets/components/ShopList.vue'
import DeleteList from './assets/components/DeleteList.vue'
</script>

<template>
  <div>
    <h1>Caroline Loves Vue Shopping List</h1>
    <!-- your code here -->
  </div>
  <DeleteList />
  <ShopForm />
  <ShopList />
</template>

<style scoped></style>
