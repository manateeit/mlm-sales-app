<template>
  <div class="flex h-screen bg-gray-900">
    <!-- Sidebar (Collapsible) -->
    <aside :class="isCollapsed ? 'w-20' : 'w-64'" class="bg-gray-800 text-white transition-all duration-300">
      <div class="p-4 flex items-center justify-between">
        <h1 v-if="!isCollapsed" class="text-2xl font-bold">Flowbite</h1>
        <button @click="toggleSidebar" class="focus:outline-none">
          <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"></path>
          </svg>
        </button>
      </div>
      <nav class="mt-8">
        <ul class="space-y-2">
          <li :class="currentPage === 'dashboard' ? 'bg-gray-700' : ''">
            <a @click="setPage('dashboard')" class="flex items-center p-2 text-white hover:bg-gray-700 rounded cursor-pointer">
              <svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6 mr-3" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 12h18M9 5l7 7-7 7"></path>
              </svg>
              <span v-if="!isCollapsed">Dashboard</span>
            </a>
          </li>
          <li :class="currentPage === 'team-tracker' ? 'bg-gray-700' : ''">
            <a @click="setPage('team-tracker')" class="flex items-center p-2 text-white hover:bg-gray-700 rounded cursor-pointer">
              <svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6 mr-3" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"></path>
              </svg>
              <span v-if="!isCollapsed">Team Tracker</span>
            </a>
          </li>
          <li :class="currentPage === 'commissions' ? 'bg-gray-700' : ''">
            <a @click="setPage('commissions')" class="flex items-center p-2 text-white hover:bg-gray-700 rounded cursor-pointer">
              <svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6 mr-3" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"></path>
              </svg>
              <span v-if="!isCollapsed">Commissions</span>
            </a>
          </li>
          <li :class="currentPage === 'profile' ? 'bg-gray-700' : ''">
            <a @click="setPage('profile')" class="flex items-center p-2 text-white hover:bg-gray-700 rounded cursor-pointer">
              <svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6 mr-3" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"></path>
              </svg>
              <span v-if="!isCollapsed">Profile</span>
            </a>
          </li>
        </ul>
      </nav>
    </aside>

    <!-- Main content -->
    <div class="flex-1 flex flex-col">
      <!-- Top navbar -->
      <header class="bg-gray-800 p-4 flex justify-between items-center">
        <h1 class="text-lg font-semibold text-white">{{ currentPageTitle }}</h1>
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
        <h2 class="text-2xl">Sample Content for {{ currentPageTitle }}</h2>
        <p>This is just a placeholder for your main content area.</p>
      </main>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const isCollapsed = ref(false)
const currentPage = ref('dashboard')

const toggleSidebar = () => {
  isCollapsed.value = !isCollapsed.value
}

const setPage = (page) => {
  currentPage.value = page
}

const currentPageTitle = computed(() => {
  switch (currentPage.value) {
    case 'dashboard':
      return 'Dashboard'
    case 'team-tracker':
      return 'Team Tracker'
    case 'commissions':
      return 'Commissions'
    case 'profile':
      return 'Profile'
    default:
      return 'Dashboard'
  }
})
</script>

<style scoped>
/* Add custom styles if needed */
</style>
