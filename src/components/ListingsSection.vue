<template>
  <SortBar />

  <div class="px-4 pb-6">
    <div class="grid grid-cols-1 md:grid-cols-2 gap-4 mb-12">
      <PropertyCard v-for="i in 4" :key="i" />
    </div>
  </div>
</template>

<script setup>
import SortBar from './SortBar.vue'
import PropertyCard from './PropertyCard.vue'
</script>
