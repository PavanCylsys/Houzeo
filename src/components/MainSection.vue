<template>
  <div class="flex flex-col md:flex-row h-[calc(100vh-128px)]">
    <div class="hidden md:block w-1/2">
      <MapSection />
    </div>

    <div class="w-full md:w-1/2 p-4 overflow-y-auto h-full">
      <ListingsSection />
    </div>
  </div>
</template>

<script setup>
import MapSection from './MapSection.vue'
import ListingsSection from './ListingsSection.vue'
</script>
