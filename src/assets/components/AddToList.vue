<script setup>
import { ref } from 'vue'
import { computed } from 'vue'

const newItem = ref('')
const lists = ref([''])
const props = defineProps({
  propId: Number,
  listProp: Object
})
/*
const emit = defineEmits(['update: listProp'])

const itemToUpdate = computed({
  get() {
    return props.listProp
  },
  set(itemToUpdate) {
    emit('update: titleProp', 'update: listProp')
  }
})
// auto reset for some of my functions add in the last .then
const autoReset = () => {
  newItem.value = ''
}*/

const addListItem = () => {
  fetch('http://localhost:3000/lists/' + props.propId, {
    method: 'PATCH',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({
      itemName: newItem.value,
      items: [...props.listProp, { itemName: newItem.value, purchased: false }]
    })
      .then((res) => res.json())
      .then((data) => console.log(data))
    // .then((data) => (lists.value = data))
  })
}
</script>

<template>
  <div>
    <form @submit.prevent="addListItem()">
      <input type="text" v-model="newItem" @keyup.enter="submit" />
      <!-- This goes with the above: <input v-model="itemToUpdate" /> -->
      <button class="btn btn-edit">Add New Item</button>
    </form>
  </div>

  <!-- {{ editList }} -->
</template>
