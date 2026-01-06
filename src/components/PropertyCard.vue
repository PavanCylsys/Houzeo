<template>
  <div
  class="bg-white border rounded-lg shadow-md group
  w-full mx-auto
  overflow-visible sm:overflow-hidden
  max-w-full sm:max-w-sm transition-all duration-300
         sm:hover:shadow-xl sm:hover:-translate-y-1"
>

    <div class="relative overflow-hidden">

      <img
        :src="images[currentImage]"
        alt="Property Image"
        class="w-full h-48 sm:h-52 object-cover transition-all duration-500"
      />

      <button
  v-if="images.length > 1"
  @click="prevImage"
  class="absolute left-2 top-1/2 -translate-y-1/2
         bg-white bg-opacity-80 p-2 rounded-full
         text-xl font-bold
         opacity-100 sm:opacity-0 sm:group-hover:opacity-100
         transition"
>
  ‹
</button>


<button
  v-if="images.length > 1"
  @click="nextImage"
  class="absolute right-2 top-1/2 -translate-y-1/2
         bg-white bg-opacity-80 p-2 rounded-full
         text-xl font-bold
         opacity-100 sm:opacity-0 sm:group-hover:opacity-100
         transition"
>
  ›
</button>


      <div
        v-if="images.length > 1"
        class="absolute bottom-2 left-1/2 -translate-x-1/2
               flex space-x-2
               opacity-100 sm:opacity-0 sm:group-hover:opacity-100
               transition"
      >
        <span
          v-for="(_, index) in images"
          :key="index"
          @click="currentImage = index"
          class="w-2.5 h-2.5 rounded-full cursor-pointer
                 border border-white"
          :class="currentImage === index
            ? 'bg-white'
            : 'bg-white/40'"
        ></span>
      </div>

  
      <div
        class="absolute top-2 left-2 bg-white bg-opacity-90
               px-2 py-1 rounded-full text-xs font-semibold"
      >
        6 days on Houzeo
      </div>
      <button
  @click.stop="toggleLike"
  class="absolute top-2 right-2 bg-white bg-opacity-80
         p-2 rounded-full transition cursor-pointer"
>
  <span
    class="text-xl transition-all duration-300"
    :class="[
      isLiked ? 'text-red-500 animate-pulse scale-110' : 'text-gray-400'
    ]"
  >
    {{ isLiked ? '❤️' : '🤍' }}
  </span>
</button>


      <div class="absolute bottom-0 left-0 right-0 h-20
                  bg-gradient-to-t  to-transparent">

      </div>
    </div>
    <div class="p-4">

      <div class="flex items-center justify-between mb-2">
        <div class="flex items-center">
          <span class="w-3 h-3 bg-green-500 rounded-full mr-2"></span>
          <p class="text-sm font-medium">House For Sale</p>
        </div>

        <div class="flex items-center text-gray-500 text-sm">
          👁️ <span class="ml-1">2.3k</span>
        </div>
      </div>

      <p class="text-xl sm:text-2xl font-bold text-gray-900 mb-1">
        $3,349,000
      </p>

      <div class="flex flex-wrap items-center gap-4 text-gray-600 mb-2 text-sm">
        <span><b>4</b> Beds</span>
        <span><b>3</b> Baths</span>
        <span><b>998</b> sqft</span>
      </div>

      <p class="text-sm text-gray-600 truncate">
        2856 Meadow Park Ave, Henderson, NV 89052
      </p>

      <p class="text-xs text-gray-500 mt-1">
        Nashville (Real Tracs Mid) MLS-TN as distributed by MLS GRID
      </p>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import imageOne from '../assets/images/imageOne.png'
import imageTwo from '../assets/images/imageTwo.png'
import imageThree from '../assets/images/imageThree.png'
import imageFour from '../assets/images/imageFour.png'
const images = [
imageOne,
imageTwo,
imageThree,
imageFour,
]

const currentImage = ref(0)
const isLiked = ref(false)

const toggleLike = () => {
  isLiked.value = !isLiked.value
}
const nextImage = () => {
  currentImage.value =
    currentImage.value === images.length - 1
      ? 0
      : currentImage.value + 1
}

const prevImage = () => {
  currentImage.value =
    currentImage.value === 0
      ? images.length - 1
      : currentImage.value - 1
}
</script>
