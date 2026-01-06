<template>
  <SortBar />

  <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
    <PropertyCard v-for="i in 4" :key="i" />
  </div>
</template>

<script setup>
import SortBar from './SortBar.vue'
import PropertyCard from './PropertyCard.vue'
</script>
