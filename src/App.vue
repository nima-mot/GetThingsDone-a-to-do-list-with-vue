<script setup>
import { ref, onMounted, computed, watch } from 'vue'

const todos = ref([])
const name = ref('')

const input_content = ref('')
const input_category = ref(null)

const todo_asc = computed(() => todos.value.sort((a,b) => {
  return b.createdAt - a.createdAt
}))

watch(name, (newVal) => {
  localStorage.setItem('name', newVal)
})

onMounted(() => {
  name.value = localStorage.getItem('name') || ''
})

</script>

<template>

  <main class="app">

    <section class="greeting">
      
     <h2 class="title">
      What's up, <input type="text" placeholder="Inter you'r name here" v-model="name">
     </h2> 

    </section>

  </main>

</template>