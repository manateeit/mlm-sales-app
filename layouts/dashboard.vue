<template>
    <div class="flex h-screen bg-gray-100">
      <!-- Left sidebar -->
      <div class="w-64 bg-white shadow-md">
        <!-- Sidebar content -->
        <div class="p-4">
          <h2 class="text-xl font-semibold">Menu</h2>
          <!-- Add menu items here -->
        </div>
      </div>
  
      <div class="flex-1 flex flex-col overflow-hidden">
        <!-- Header -->
        <header class="bg-white shadow-sm">
          <div class="max-w-7xl mx-auto py-4 px-4 sm:px-6 lg:px-8 flex justify-between items-center">
            <h1 class="text-lg font-semibold">Dashboard</h1>
            <button @click="logout" class="text-sm text-gray-600 hover:text-gray-900">Logout</button>
          </div>
        </header>
  
        <!-- Main content -->
        <main class="flex-1 overflow-x-hidden overflow-y-auto bg-gray-200">
          <div class="container mx-auto px-6 py-8">
            <slot />
          </div>
        </main>
      </div>
    </div>
  </template>
  
  <script setup>
  import { useAuthStore } from '~/stores/auth'
  import { useRouter } from 'vue-router'
  
  const authStore = useAuthStore()
  const router = useRouter()
  
  const logout = async () => {
    try {
      await authStore.logout()
      router.push('/login')
    } catch (error) {
      alert(error.message)
    }
  }
  </script>