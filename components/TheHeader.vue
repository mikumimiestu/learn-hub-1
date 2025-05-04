<template>
  <header class="fixed top-0 left-0 right-0 bg-white/90 backdrop-blur-sm shadow-sm z-header h-header">
    <div class="container h-full flex items-center justify-between">
      <NuxtLink to="/" class="flex items-center">
        <span class="text-2xl font-bold text-primary-600">Learn<span class="text-accent-600">Hub</span></span>
      </NuxtLink>
      
      <!-- Desktop Navigation -->
      <nav class="hidden md:flex items-center space-x-8">
        <NuxtLink v-for="item in navItems" :key="item.text" :to="item.to" 
          class="text-gray-700 hover:text-primary-600 font-medium transition-colors duration-200"
          active-class="text-primary-600 font-semibold">
          {{ item.text }}
        </NuxtLink>
        <NuxtLink to="/premium" 
          class="text-accent-700 hover:text-accent-800 font-semibold transition-colors duration-200 flex items-center">
          <span>Premium</span>
          <span class="ml-1">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-5 h-5">
              <path fill-rule="evenodd" d="M10.788 3.21c.448-1.077 1.976-1.077 2.424 0l2.082 5.006 5.404.434c1.164.093 1.636 1.545.749 2.305l-4.117 3.527 1.257 5.273c.271 1.136-.964 2.033-1.96 1.425L12 18.354 7.373 21.18c-.996.608-2.231-.29-1.96-1.425l1.257-5.273-4.117-3.527c-.887-.76-.415-2.212.749-2.305l5.404-.434 2.082-5.005Z" clip-rule="evenodd" />
            </svg>
          </span>
        </NuxtLink>
      </nav>
      
      <!-- Auth Buttons -->
      <div class="hidden md:flex items-center space-x-4">
        <NuxtLink to="/login" class="btn btn-secondary py-2 px-4">Log in</NuxtLink>
        <NuxtLink to="/signup" class="btn btn-primary py-2 px-4">Sign up</NuxtLink>
      </div>
      
      <!-- Mobile Menu Button -->
      <button @click="isMobileMenuOpen = !isMobileMenuOpen" class="md:hidden text-gray-500 hover:text-gray-700">
        <svg v-if="!isMobileMenuOpen" xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
        </svg>
        <svg v-else xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
        </svg>
      </button>
    </div>
    
    <!-- Mobile Menu -->
    <div v-if="isMobileMenuOpen" 
      class="md:hidden absolute top-header left-0 right-0 bg-white border-t border-gray-200 shadow-lg"
      v-motion="{ initial: { opacity: 0, y: -20 }, enter: { opacity: 1, y: 0 } }">
      <div class="container py-4 flex flex-col space-y-4">
        <NuxtLink v-for="item in navItems" :key="item.text" :to="item.to" 
          @click="isMobileMenuOpen = false"
          class="py-2 px-4 text-gray-700 hover:bg-gray-50 rounded-lg">
          {{ item.text }}
        </NuxtLink>
        <NuxtLink to="/premium" 
          @click="isMobileMenuOpen = false"
          class="py-2 px-4 text-accent-700 font-semibold hover:bg-accent-50 rounded-lg flex items-center">
          <span>Premium</span>
          <span class="ml-1">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-5 h-5">
              <path fill-rule="evenodd" d="M10.788 3.21c.448-1.077 1.976-1.077 2.424 0l2.082 5.006 5.404.434c1.164.093 1.636 1.545.749 2.305l-4.117 3.527 1.257 5.273c.271 1.136-.964 2.033-1.96 1.425L12 18.354 7.373 21.18c-.996.608-2.231-.29-1.96-1.425l1.257-5.273-4.117-3.527c-.887-.76-.415-2.212.749-2.305l5.404-.434 2.082-5.005Z" clip-rule="evenodd" />
            </svg>
          </span>
        </NuxtLink>
        <div class="pt-2 border-t border-gray-100 flex flex-col space-y-2">
          <NuxtLink to="/login" @click="isMobileMenuOpen = false" class="btn btn-secondary">Log in</NuxtLink>
          <NuxtLink to="/signup" @click="isMobileMenuOpen = false" class="btn btn-primary">Sign up</NuxtLink>
        </div>
      </div>
    </div>
  </header>
  <!-- Header spacer -->
  <div class="h-header"></div>
</template>

<script setup>
import { ref } from 'vue';

const isMobileMenuOpen = ref(false);

const navItems = [
  { text: 'Home', to: '/' },
  { text: 'Courses', to: '/courses' },
  { text: 'Dashboard', to: '/dashboard' },
  { text: 'About', to: '/about' }
];
</script>