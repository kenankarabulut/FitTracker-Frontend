<!-- src/components/TheWelcome.vue -->
<script setup lang="ts">
import { ref } from 'vue'

const entries = ref([
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
