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
  <div class="listOfShop">
    <ul v-for="list in lists" :key="list.id" class="listItems">
      <h3 class="list-head">{{ list.title }}</h3>
      <DeleteList :list="list" @listDeleted="getLists" />
      <AddToList :propId="list.id" :listProp="list" />
      <div v-for="item in list.items" :key="item.id">
        <li class="list-items">{{ item.itemName }} {{ item.purchased }}</li>
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
