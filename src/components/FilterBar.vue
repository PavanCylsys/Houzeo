<template>
  <div class="bg-white md:bg-gray-50 border-b p-3 md:py-3 md:px-4">
    <div class="container mx-auto">
      
      <!-- Mobile View -->
      <div class="md:hidden">
        <div class="flex items-center gap-2">
          <!-- Search Bar -->
          <div class="flex-grow relative flex items-center border border-blue-600 rounded-full">
            <input 
              type="text" 
              value="Austin, TX" 
              class="w-full pl-4 pr-20 py-2.5 bg-transparent rounded-full focus:outline-none"
            />
            <button class="absolute right-12 text-gray-400 hover:text-gray-600 text-xl">
              &times;
            </button>
            <button class="absolute right-1.5 bg-blue-700 text-white rounded-full p-2 hover:bg-blue-800" @click="onSearch">
              <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"></path></svg>
            </button>
          </div>
          <!-- Filter Icon Button -->
          <button class="relative flex-shrink-0 border-2 border-blue-600 rounded-full p-2.5" @click="openFilters">
            <img src="../assets/images/Vector.svg" alt="Filters" class="w-5 h-5">
            <span v-if="activeFilterCount > 0" class="absolute -top-1 -right-1 bg-blue-600 text-white text-xs font-bold rounded-full h-5 w-5 flex items-center justify-center">
              {{ activeFilterCount }}
            </span>
          </button>
        </div>
        
        <div class="flex items-center justify-between gap-2 mt-3">
          <!-- Dropdowns (only first two for mobile) -->
          <div v-for="filter in filters.slice(0, 2)" :key="filter.label" class="relative flex-1 z-999">
             <button @click.stop="toggleDropdown(filter.label)" class="w-full flex items-center justify-between  py-2 rounded-lg border transition-all duration-300" 
                    :class="isActive(filter) ? 'bg-blue-50 border-blue-500 text-blue-600' : 'bg-white border-gray-400 text-gray-800'">
                {{ filter.value }}
                <svg class="w-4 h-4 ml-2" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" /></svg>
             </button>
             <!-- Dropdown content here as before -->
          </div>

          <button class="flex-1 bg-blue-700 text-white font-semibold px-4 py-2 rounded-lg hover:bg-blue-800 whitespace-nowrap">
            Save Search
          </button>
        </div>
      </div>

      <!-- Desktop View -->
      <div class="hidden md:flex flex-wrap items-center gap-3">
        <!-- Your existing desktop layout remains here -->
        <div class="relative flex-grow max-w-[280px]">
          <input type="text" value="Austin, TX" class="w-full pl-4 pr-10 py-2 border rounded-lg focus:ring-blue-500 focus:border-blue-500" />
          <button class="absolute inset-y-0 right-0 pr-3 flex items-center text-gray-400 hover:text-gray-600">
            &times;
          </button>
        </div>
        <button class="bg-blue-600 text-white p-2 rounded-lg hover:bg-blue-700" @click="onSearch">
          <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"></path></svg>
        </button>
        <div class="flex items-center gap-2">
            <div v-for="filter in filters.slice(0, 2)" :key="filter.label" class="relative">
              <button @click.stop="toggleDropdown(filter.label)" class="w-full flex items-center justify-between px-4 py-2 rounded-lg border transition-all duration-300" 
                      :class="isActive(filter) ? 'bg-blue-50 border-blue-500 text-blue-600' : 'bg-white border-gray-400 text-gray-800'">
                  {{ filter.value }}
                  <svg class="w-4 h-4 ml-2" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" /></svg>
              </button>
             <div v-if="openDropdown === filter.label" class="absolute mt-2 w-full bg-white border rounded-lg shadow-md z-20">
                <div v-for="option in filter.options" :key="option" @click="selectOption(filter, option)" class="px-4 py-2 cursor-pointer transition" :class="option === filter.value ? 'bg-blue-100 text-blue-700 font-medium' : 'hover:bg-gray-100'">
                  {{ option }}
                </div>
            </div>
          </div>
        </div>
        <div class="flex items-center gap-3">
          <button class="flex items-center px-4 py-2 border rounded-lg bg-white hover:bg-gray-100" @click="openFilters">
            <img src="../assets/images/Vector.svg" alt="Filters" class="w-[16px] h-[16px] mr-2"> Filters
          </button>
          <button class="flex items-center px-4 py-2 border rounded-lg bg-white hover:bg-gray-100" @click="openSaved">
            <img src="../assets/images/save.svg" alt="Saved" class="w-[16px] h-[16px] mr-2"> Saved
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { reactive, ref, onMounted, onBeforeUnmount, computed } from "vue"; // Add computed

// ... keep all existing script logic ...
const openDropdown = ref(null);
const filters = reactive([
// ...
  {
    label: "status",
    value: "For Sale",
    defaultValue: "For Sale",
    options: ["For Sale", "Sold", "Pending"],
    className: "" // Always visible
  },
  {
    label: "price",
    value: "Price",
    defaultValue: "Price",
    options: ["$0 - $100k", "$100k - $300k", "$300k+"],
    className: "" // Always visible
  },
  {
    label: "beds",
    value: "Beds & Baths",
    defaultValue: "Beds & Baths",
    options: ["1+", "2+", "3+", "4+"],
    className: "hidden md:block" // Hidden on mobile, visible on medium screens+
  },
  {
    label: "type",
    value: "Property Type",
    defaultValue: "Property Type",
    options: ["House", "Apartment", "Villa"],
    className: "hidden md:block" // Hidden on mobile, visible on medium screens+
  }
]);

// Add this computed property to count active filters for the badge
const activeFilterCount = computed(() => {
  return filters.reduce((count, filter) => {
    if (filter.value !== filter.defaultValue) {
      return count + 1;
    }
    return count;
  }, 0);
});

const isActive = (filter) => {
  return (
    openDropdown.value === filter.label ||
    filter.value !== filter.defaultValue
  );
};
const toggleDropdown = (label) => {
  openDropdown.value = openDropdown.value === label ? null : label;
};

const selectOption = (filter, option) => {
  filter.value = option;
  openDropdown.value = null;
};

/* Actions */
const onSearch = () => { console.log("Search clicked"); };
const openFilters = () => { console.log("Filters clicked"); };
const openSaved = () => { console.log("Saved clicked"); };

const handleClickOutside = () => {
  openDropdown.value = null;
};

onMounted(() => { document.addEventListener("click", handleClickOutside); });
onBeforeUnmount(() => { document.removeEventListener("click", handleClickOutside); });
</script>