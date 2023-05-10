<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <div>
      <div class="text-center py-10 rounded-md" role="group">
        <nav>
          <RouterLink class="px-4 py-2 text-sm font-medium text-gray-900 bg-white border border-lime-600 rounded-lg mr-2 hover:bg-gray-100 hover:text-lime-700 focus:z-10 focus:ring-2 focus:ring-lime-700 focus:text-lime-700" to="/app">App</RouterLink>
          <RouterLink class="px-4 py-2 text-sm font-medium text-gray-900 bg-white border border-lime-600 rounded-lg mr-2 hover:bg-gray-100 focus:z-10 focus:ring-2 focus:ring-lime-700 focus:text-lime-700" to="/">Home </RouterLink> 
        </nav>
      </div>
    <RouterView />
  </div>
</template>

<style scoped>
nav a.router-link-exact-active {
  color: #84cc16;
}
</style>
