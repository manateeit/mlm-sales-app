<template>
  <div :class="{ 'dark': isDarkMode }" class="h-screen">
    <div class="flex h-full bg-gray-100 dark:bg-gray-900">
      <!-- Sidebar (Collapsible) -->
      <aside :class="isCollapsed ? 'w-20' : 'w-64'" class="bg-white dark:bg-gray-800 text-gray-900 dark:text-white transition-all duration-300 flex flex-col justify-between">
        <div>
          <div class="p-4 flex items-center justify-between">
            <h1 v-if="!isCollapsed" class="text-2xl font-bold">Crowd1099</h1>
            <button @click="toggleSidebar" class="focus:outline-none">
              <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"></path>
              </svg>
            </button>
          </div>
          <nav class="mt-8">
            <ul class="space-y-2">
              <!-- Dashboard -->
              <li>
                <a @click="setPage('dashboard')" class="flex items-center p-2 text-gray-900 dark:text-white hover:bg-gray-200 dark:hover:bg-gray-700 rounded cursor-pointer">
                  <!-- Dashboard Icon -->
                  <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6 mr-3">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M8.25 21v-4.875c0-.621.504-1.125 1.125-1.125h2.25c.621 0 1.125.504 1.125 1.125V21m0 0h4.5V3.545M12.75 21h7.5V10.75M2.25 21h1.5m18 0h-18M2.25 9l4.5-1.636M18.75 3l-1.5.545m0 6.205 3 1m1.5.5-1.5-.5M6.75 7.364V3h-3v18m3-13.636 10.5-3.819" />
                  </svg>
                  <span v-if="!isCollapsed">Dashboard</span>
                </a>
              </li>

              <!-- Team Tracker -->
              <li>
                <a @click="setPage('team-tracker')" class="flex items-center p-2 text-gray-900 dark:text-white hover:bg-gray-200 dark:hover:bg-gray-700 rounded cursor-pointer">
                  <!-- Team Tracker Icon -->
                  <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6 mr-3">
                    <path stroke-linecap="round" stroke-linejoin="round" d="m21 7.5-2.25-1.313M21 7.5v2.25m0-2.25-2.25 1.313M3 7.5l2.25-1.313M3 7.5l2.25 1.313M3 7.5v2.25m9 3 2.25-1.313M12 12.75l-2.25-1.313M12 12.75V15m0 6.75 2.25-1.313M12 21.75V19.5m0 2.25-2.25-1.313m0-16.875L12 2.25l2.25 1.313M21 14.25v2.25l-2.25 1.313m-13.5 0L3 16.5v-2.25" />
                  </svg>
                  <span v-if="!isCollapsed">Team Tracker</span>
                </a>
              </li>

              <!-- Commissions -->
              <li>
                <a @click="setPage('commissions')" class="flex items-center p-2 text-gray-900 dark:text-white hover:bg-gray-200 dark:hover:bg-gray-700 rounded cursor-pointer">
                  <!-- Commissions Icon -->
                  <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6 mr-3">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M12 6v12m-3-2.818.879.659c1.171.879 3.07.879 4.242 0 1.172-.879 1.172-2.303 0-3.182C13.536 12.219 12.768 12 12 12c-.725 0-1.45-.22-2.003-.659-1.106-.879-1.106-2.303 0-3.182s2.9-.879 4.006 0l.415.33M21 12a9 9 0 1 1-18 0 9 9 0 0 1 18 0Z" />
                  </svg>
                  <span v-if="!isCollapsed">Commissions</span>
                </a>
              </li>

              <!-- Profile -->
              <li>
                <a @click="setPage('profile')" class="flex items-center p-2 text-gray-900 dark:text-white hover:bg-gray-200 dark:hover:bg-gray-700 rounded cursor-pointer">
                  <!-- Profile Icon -->
                  <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6 mr-3">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M17.982 18.725A7.488 7.488 0 0 0 12 15.75a7.488 7.488 0 0 0-5.982 2.975m11.963 0a9 9 0 1 0-11.963 0m11.963 0A8.966 8.966 0 0 1 12 21a8.966 8.966 0 0 1-5.982-2.275M15 9.75a3 3 0 1 1-6 0 3 3 0 0 1 6 0Z" />
                  </svg>
                  <span v-if="!isCollapsed">Profile</span>
                </a>
              </li>
            </ul>
          </nav>
        </div>
        
        <!-- Toggle Mode (New) -->
        <div class="mt-auto mb-4">
          <a @click="toggleDarkMode" class="flex items-center p-2 text-gray-900 dark:text-white hover:bg-gray-200 dark:hover:bg-gray-700 rounded cursor-pointer">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6 mr-3">
              <path stroke-linecap="round" stroke-linejoin="round" d="M21.752 15.002A9.718 9.718 0 0118 15.75c-5.385 0-9.75-4.365-9.75-9.75 0-1.33.266-2.597.748-3.752A9.753 9.753 0 003 11.25C3 16.635 7.365 21 12.75 21a9.753 9.753 0 009.002-5.998z" />
            </svg>
            <span v-if="!isCollapsed">Toggle Mode</span>
          </a>
        </div>
      </aside>

      <!-- Main content -->
      <div class="flex-1 flex flex-col">
        <!-- Top navbar -->
        <header class="bg-white dark:bg-gray-800 p-4 flex justify-between items-center">
          <h1 class="text-lg font-semibold text-gray-900 dark:text-white">{{ currentPageTitle }}</h1>
          <div class="flex items-center space-x-4">
            <button class="bg-gray-200 dark:bg-gray-700 text-gray-800 dark:text-white p-2 rounded-full focus:outline-none">
              <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 12h14M12 5l7 7-7 7"></path>
              </svg>
            </button>
            <img src="https://via.placeholder.com/40" class="rounded-full w-10 h-10">
          </div>
        </header>

        <!-- Dashboard content -->
        <main class="flex-1 p-6 bg-gray-100 dark:bg-gray-900 text-gray-900 dark:text-white">
          <h2 class="text-2xl">Sample Content for {{ currentPageTitle }}</h2>
          <p>This is just a placeholder for your main content area.</p>
        </main>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const isCollapsed = ref(false)
const currentPage = ref('dashboard')
const isDarkMode = ref(false)

const toggleSidebar = () => {
  isCollapsed.value = !isCollapsed.value
}

const setPage = (page) => {
  currentPage.value = page
}

const toggleDarkMode = () => {
  isDarkMode.value = !isDarkMode.value
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

<style>
@import 'tailwindcss/base';
@import 'tailwindcss/components';
@import 'tailwindcss/utilities';
</style>