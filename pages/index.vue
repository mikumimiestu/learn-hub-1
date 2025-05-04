<template>
  <div>
    <!-- Coming Soon Banner -->
    <div class="bg-yellow-100 border-l-4 border-yellow-500 p-4 mb-8">
      <div class="flex items-center">
        <div class="flex-shrink-0">
          <svg class="h-5 w-5 text-yellow-500" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor">
            <path fill-rule="evenodd" d="M8.257 3.099c.765-1.36 2.722-1.36 3.486 0l5.58 9.92c.75 1.334-.213 2.98-1.742 2.98H4.42c-1.53 0-2.493-1.646-1.743-2.98l5.58-9.92zM11 13a1 1 0 11-2 0 1 1 0 012 0zm-1-8a1 1 0 00-1 1v3a1 1 0 002 0V6a1 1 0 00-1-1z" clip-rule="evenodd" />
          </svg>
        </div>
        <div class="ml-3">
          <p class="text-sm text-yellow-700">
            <span class="font-bold">Coming Soon!</span> We're working hard to bring you amazing content. Stay tuned for exciting updates!
          </p>
        </div>
      </div>
    </div>

    <!-- Logo
    <div class="p-4">
      <img src="/assets/logo.png" alt="TNGDemy Logo" class="h-10 w-auto" />
    </div> -->

    <!-- Sections -->
    <HeroSection />
    <FeaturedCourses />
    <CategorySection />
    <TestimonialsSection />
    <CTASection />
  </div>
</template>