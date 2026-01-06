<template>
  <header class="bg-white border-b sticky top-0 z-50">
    <div class="container mx-auto px-4">
      <div class="relative flex items-center justify-between h-20">

        <!-- Desktop Left Side: Logo and Navigation -->
        <div class="hidden md:flex items-center space-x-10">
          <a href="#" class="flex-shrink-0">
             <img src="../assets/images/Group.svg" alt="Houzeo" class="w-[123.94px] h-[34.3px]">
          </a>
          <nav class="hidden md:flex items-center space-x-8">
            <a href="#" class="nav-link flex items-center"> Product
              <svg class="h-5 w-5 ml-1 text-gray-500" viewBox="0 0 20 20" fill="currentColor"><path fill-rule="evenodd" d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z" clip-rule="evenodd" /></svg>
            </a>
            <a href="#" class="nav-link">How Houzeo Works</a>
            <a href="#" class="nav-link">Reviews</a>
            <a href="#" class="nav-link flex items-center"> Buy
              <svg class="h-5 w-5 ml-1 text-gray-500" viewBox="0 0 20 20" fill="currentColor"><path fill-rule="evenodd" d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z" clip-rule="evenodd" /></svg>
            </a>
            <a href="#" class="nav-link flex items-center"> Sell
              <svg class="h-5 w-5 ml-1 text-gray-500" viewBox="0 0 20 20" fill="currentColor"><path fill-rule="evenodd" d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z" clip-rule="evenodd" /></svg>
            </a>
            <a href="#" class="nav-link">Pricing</a>
            <a href="#" class="nav-link flex items-center"> Resources
              <svg class="h-5 w-5 ml-1 text-gray-500" viewBox="0 0 20 20" fill="currentColor"><path fill-rule="evenodd" d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z" clip-rule="evenodd" /></svg>
            </a>
          </nav>
        </div>

        <!-- Desktop Right Side -->
        <div class="hidden md:flex items-center space-x-6">
          <a href="#" class="nav-link">Sign In</a>
          <div class="text-right">
            <div class="text-left font-semibold text-gray-800 whitespace-nowrap">(844) 448-0110</div>
            <div class="text-xs text-gray-500 whitespace-nowrap">(9am to 6pm CST, Mon-Sat)</div>
          </div>
          <button class="bg-[linear-gradient(270deg,_#0E5293_0%,_#2876C1_97.2%)] text-white font-semibold p-2 text-sm rounded-lg transition-colors whitespace-nowrap">
            Start Free Listing
          </button>
        </div>

        <!-- Mobile Hamburger (Left) -->
        <div class="md:hidden">
          <button class="text-gray-600 hover:text-gray-800">
            <svg class="w-7 h-7" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16m-7 6h7"></path>
            </svg>
          </button>
        </div>

        <!-- Mobile Logo (Center) -->
        <div class="md:hidden absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2">
          <a href="#">
            <img src="../assets/images/Group.svg" alt="Houzeo" class="w-[123.94px] h-[34.3px]">
          </a>
        </div>

        <!-- Mobile Profile (Right) -->
        <div class="md:hidden">
          <button class="text-gray-600 hover:text-gray-800">
            <svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M5.121 17.804A13.937 13.937 0 0112 16c2.5 0 4.847.655 6.879 1.804M15 10a3 3 0 11-6 0 3 3 0 016 0zm6 2a9 9 0 11-18 0 9 9 0 0118 0z"></path>
            </svg>
          </button>
        </div>

      </div>
    </div>
  </header>
</template>

<style scoped>
.nav-link {
 /* @apply text-gray-600 hover:text-blue-600 font-medium transition-colors whitespace-nowrap; */
}
</style>