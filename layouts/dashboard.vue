<template>
  <div class="flex h-screen bg-gray-900">
    <!-- Sidebar -->
    <aside class="w-64 bg-gray-800 text-white">
      <div class="p-4 flex items-center justify-between">
        <h1 class="text-2xl font-bold">Flowbite</h1>
        <button @click="toggleSidebar" class="focus:outline-none">
          <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"></path>
          </svg>
        </button>
      </div>
      <nav class="mt-8">
        <ul class="space-y-2">
          <li>
            <a href="#" class="flex items-center p-2 text-white hover:bg-gray-700 rounded">
              <svg class="w-6 h-6 mr-3" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 12h18M3 12l6 6M3 12l6-6"></path>
              </svg>
              Dashboard
            </a>
          </li>
          <!-- Add more sidebar items with icons here -->
        </ul>
      </nav>
    </aside>

    <!-- Main content -->
    <div class="flex-1 flex flex-col">
      <!-- Top navbar -->
      <header class="bg-gray-800 p-4 flex justify-between items-center">
        <input type="text" class="w-1/3 bg-gray-700 text-white p-2 rounded-lg" placeholder="Search...">
        <div class="flex items-center space-x-4">
          <button class="bg-gray-700 text-white p-2 rounded-full focus:outline-none">
            <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 12h14M12 5l7 7-7 7"></path>
            </svg>
          </button>
          <img src="https://via.placeholder.com/40" class="rounded-full w-10 h-10">
        </div>
      </header>

      <!-- Dashboard content -->
      <main class="flex-1 p-6 bg-gray-900 text-white">
        <!-- Revenue Card -->
        <div class="bg-gray-800 p-6 rounded-lg mb-6">
          <h2 class="text-4xl font-bold">$45,385</h2>
          <p class="text-gray-400">Sales this week</p>
          <div class="flex justify-between items-center mt-4">
            <div class="text-green-400 text-sm">12.5% ↑</div>
            <a href="#" class="text-blue-500">Sales Report</a>
          </div>
        </div>

        <!-- Chart -->
        <div class="bg-gray-800 p-6 rounded-lg">
          <!-- Placeholder for Chart -->
          <p>Chart content goes here (use a charting library like Chart.js)</p>
        </div>
      </main>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const toggleSidebar = () => {
  // Add logic for collapsing/expanding sidebar if needed
}
</script>

<style scoped>
/* Add custom styles if needed */
</style>