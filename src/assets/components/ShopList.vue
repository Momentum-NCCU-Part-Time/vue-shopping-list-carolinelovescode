<script setup>
import { ref } from 'vue'
// show list of items, GET request on the list component

const lists = ref([''])
const truePurch = ref(false)
const itemName = ref([''])

fetch('http://localhost:3000/lists/', {
  method: 'GET'
})
  .then((res) => res.json())
  .then((item) => (lists.value = item))
// .then((item) => (lists.value = console.log(item)))
</script>

<template>
  <div v-for="list in lists" class="listOfShop">
    <ul>
      <h3>{{ list.id }} {{ list.title }}</h3>

      <li v-for="item in list.items">{{ item.itemName }} {{ item.purchased }}</li>

      <!-- {{
        console.log(itemName)
      }} -->
      <input v-model="truePurch" type="checkbox" />
      <!-- {{
        truePurch
      }} -->
    </ul>
  </div>
</template>
