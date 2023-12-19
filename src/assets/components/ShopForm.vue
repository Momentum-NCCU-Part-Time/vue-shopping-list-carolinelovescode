<script setup>
import { ref } from 'vue'
// import ShopList from './ShopList.vue'
// import App from '../../App.vue'

const lists = ref([''])
const addList = ref('')

const listTitle = ref('')
const listBody = ref('')

// to add stuff
const addTo = () => {
  fetch('http://localhost:3000/lists/', {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({ title: listTitle.value, body: listBody.value })
  })
    .then((res) => res.json())
    .then((lists) => lists)
}
</script>

<template>
  <!-- create input form and button to add items -->
  <div v-for="list in lists">
    <form v-on:submit.prevent="addTo" class="shop-form">
      <input
        v-model.trim="listTitle"
        type="text"
        class="add-list"
        placeholder="What/Where are we shopping?"
      />
      <input v-model.trim="listBody" type="text" class="add-body" placeholder="What do you need?" />
      <button v-on:submit.prevent="addToList" class="btn-add">I Need This</button>
      <!-- <p>{{ list || 'You Got It All' }}</p> -->
      <!-- I have to create a delete button function -->
      <button class="btn-del">I Don't Need This</button>
    </form>
  </div>
  <!-- <ShopList /> -->
</template>
