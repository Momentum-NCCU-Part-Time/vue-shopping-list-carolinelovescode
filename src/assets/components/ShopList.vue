<script setup>
import { ref } from 'vue'
import DeleteList from './DeleteList.vue'

import ShopForm from './ShopForm.vue'
import AddToList from './AddToList.vue'

// show list of items, GET request on the list component

const lists = ref([''])
const truePurch = ref(false)
const itemName = ref([''])

const addItemToListOfItems = ref([''])

fetch('http://localhost:3000/lists/', {
  method: 'GET'
})
  .then((res) => res.json())
  .then((item) => (lists.value = item))
// .then((item) => (lists.value = console.log(item)))
</script>

<template>
  <div v-for="list in lists" class="listOfShop" :key="list.id">
    <ul class="listItems">
      <h3 class="list-head">{{ list.id }}{{ list.title }}</h3>
      <DeleteList />
      <AddToList :propId="list.id" :listProp="list.items" />
      <div v-for="item in list.items" :key="item.id">
        <li class="list-items">{{ item.id }}{{ item.itemName }} {{ item.purchased }}</li>
        <input v-model="truePurch" type="checkbox" />
      </div>
      <!-- {{
        console.log(itemName)
      }} -->

      <!-- {{
        truePurch
      }} -->
    </ul>
  </div>
</template>
