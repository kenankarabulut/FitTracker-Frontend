<script setup lang="ts">
import { ref } from 'vue'

// Spiegelt die Java-Klasse FitTrackerEntry aus dem Backend
interface FitTrackerEntry {
  id: number
  name: string
  gram: number
  calories: number
  carbohydrates: number
  protein: number
  registered: boolean
  date: string
}

const entries = ref<FitTrackerEntry[]>([
  {
    id: 1,
    name: 'Haferflocken',
    gram: 80,
    calories: 296.0,
    carbohydrates: 47.0,
    protein: 10.8,
    registered: false,
    date: '2026-10-19',
  },
  {
    id: 2,
    name: 'Magerquark',
    gram: 250,
    calories: 170.0,
    carbohydrates: 10.0,
    protein: 30.0,
    registered: true,
    date: '2026-10-19',
  },
  {
    id: 2,
    name: 'Hähnchenbrustfillet',
    gram: 250,
    calories: 170.0,
    carbohydrates: 5.0,
    protein: 30.0,
    registered: true,
    date: '2026-5-12',
  },
])
</script>

<template>
  <div class="diary">
    <h2>Meine Einträge</h2>
    <ul>
      <li v-for="entry in entries" :key="entry.id">
        <strong>{{ entry.name }}</strong> ({{ entry.gram }}g) – {{ entry.calories }} kcal
        <span>[{{ entry.registered ? 'DB' : 'Manuell' }}]</span>
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
