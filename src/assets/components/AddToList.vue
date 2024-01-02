<script setup>
import { ref } from 'vue'
import { computed } from 'vue'

const newItem = ref('')
const lists = ref([''])
const props = defineProps({
  propId: Number,
  listProp: Object
})

const emit = defineEmits(['changeMade'])

const addListItem = () => {
  fetch('http://localhost:3000/lists/' + props.propId, {
    method: 'PATCH',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({
      title: props.listProp.title,
      items: [...props.listProp.items, { itemName: newItem.value, purchased: false }],
      updatedAt: new Date()
    })
  })
    .then((res) => res.json())
    .then((data) => {
      emit('changeMade', data)
      autoReset()
    })
  // .then((data) => (lists.value = data))
}
const autoReset = () => {
  newItem.value = ''
}
</script>

<template>
  <div>
    <form @submit.prevent="addListItem">
      <input type="text" v-model="newItem" @keyup.enter="submit" />
      <!-- This goes with the above: <input v-model="itemToUpdate" /> -->
      <button class="btn btn-edit">Add New Item</button>
    </form>
  </div>

  <!-- {{ editList }} -->
</template>
