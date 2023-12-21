<script setup>
import { ref } from 'vue'
const lists = ref([''])

const listTitle = ref('')

const newInput = () => {
  listTitle.value = ''
}

// to add stuff
const addTo = () => {
  fetch('http://localhost:3000/lists/', {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({ title: listTitle.value, purchased: 'false' })
  })
    .then((res) => res.json())
    .then((lists) => newInput())
}
</script>

<template>
  <!-- create input form and button to add items -->
  <div v-for="list in lists">
    <form @submit.prevent="addTo" class="shop-form">
      <label class="form-label">
        <input
          @keyup.enter="submit"
          v-model.trim="listTitle"
          type="text"
          class="add-list"
          placeholder="What do you need"
        />Add To List
      </label>

      <button @submit.prevent="addToList" class="btn btn-add">I Need This</button>
      <!-- I have to create a delete button function -->
    </form>
  </div>
</template>
