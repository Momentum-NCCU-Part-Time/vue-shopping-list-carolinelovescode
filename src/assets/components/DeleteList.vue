<script setup>
import { ref } from 'vue'

const lists = ref([''])
const listTitle = ref('')

const deleteList = () => {
  fetch('http://localhost:3000/lists/:id', {
    method: 'DELETE',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({ title: listTitle.value })
  })
    .then((res) => res.json())
    .then((data) => (lists.value = data))
}
</script>

<template>
  <div v-for="list in lists">
    <button v-on:submit.prevent="deleteList" class="btn-del">I Don't Need This</button>

    {{ lists }}
  </div>
</template>
