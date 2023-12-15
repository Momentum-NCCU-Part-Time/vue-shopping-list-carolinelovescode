<script setup>
import { ref } from 'vue'
// import ShopList from './ShopList.vue'
// import App from '../../App.vue'

const lists = ref([''])
const addList = ref('')
</script>

<template>
  <!-- create input form and button to add items -->

  <form class="shop-form">
    <input v-model.trim="addList" type="text" class="add-list" placeholder="What do you need?" />
    {{ addList }}
    <button v-on:click="items.push" class="btn-add">I Need This</button>
    <!-- <p>{{ list || 'You Got It All' }}</p> -->
  </form>
  <!-- <ShopList /> -->
</template>
