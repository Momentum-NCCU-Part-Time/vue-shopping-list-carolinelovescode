<script setup>
import { ref } from 'vue'
// show list of items, GET request on the list component

const lists = ref([''])
const truePurch = ref(false)
fetch('http://localhost:3000/lists/', {
  method: 'GET'
})
  .then((res) => res.json())
  .then((item) => (lists.value = item))
</script>

<template>
  <div class="listOfShop">
    <ul>
      <li v-for="list in lists">{{ list.id }}{{ list.title }}</li>
      <input v-model="truePurch" type="checkbox" />
      {{
        truePurch
      }}
    </ul>
  </div>
</template>
