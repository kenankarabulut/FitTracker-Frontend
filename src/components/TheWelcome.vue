<!-- src/components/TheWelcome.vue -->
<script setup lang="ts">
import { onMounted, ref } from 'vue'
import axios from 'axios'

interface FitTrackerEntry {
  id: number
  name: string
  gram: number
  calories: number
  carbohydrates: number
  protein: number
  date: string
}

const entries = ref<FitTrackerEntry[]>([])

async function load() {
  const baseUrl = import.meta.env.VITE_BACKEND_BASE_URL
  const response = await axios.get<FitTrackerEntry[]>(baseUrl + '/entries')
  entries.value = response.data
}

onMounted(() => {
  load()
})
</script>

<template>
  <div class="diary">
    <h2>Meine Einträge</h2>
    <ul>
      <li v-for="entry in entries" :key="entry.id">
        <strong>{{ entry.name }}</strong> ({{ entry.gram }}g) – {{ entry.calories }} kcal
      </li>
    </ul>
  </div>
</template>

<style scoped>
.diary {
  margin-top: 1rem;
}
li {
  padding: 0.4rem 0;
}
</style>
