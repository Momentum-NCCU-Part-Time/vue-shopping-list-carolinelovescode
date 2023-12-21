<script setup>
import { ref } from 'vue'

const lists = ref([''])
const listTitle = ref('')

const deleteList = () => {
  fetch('http://localhost:3000/lists/', {
    method: 'DELETE',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({ title: listTitle.value })
  })
    .then((res) => res.json())
    .then((data) => (lists.value = data))
}
</script>

<template>
  <div>
    <!-- <button @click.prevent="deleteList(item.id)" :key="item.id" class="btn btn-del">
      I Don't Need This
    </button> -->
  </div>
</template>
