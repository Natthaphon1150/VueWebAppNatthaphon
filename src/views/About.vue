<script setup>
import { ref } from 'vue'

const show = ref(true)
const list = ref([1, 2, 3])
</script>

<template><br><br><br>
  <button @click="show = !show">Toggle List</button>
  <button @click="list.push(list.length + 1)">Push Number</button>
  <button @click="list.pop()">Pop Number</button>
  <button @click="list.reverse()">Reverse List</button>

  <ul v-if="show && list.length">
    <li v-for="item of list">{{ item  }}</li>
  </ul>
  <p v-else-if="list.length">list is not empty, hidden.</p>
  <p v-else>List is empty.</p>
</template>

<script>
export default {
  name: "About",
};
</script>