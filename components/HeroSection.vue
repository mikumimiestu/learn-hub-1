<template>
  <section class="relative overflow-hidden bg-gray-900 py-20 md:py-32">
    <!-- Background Pattern -->
    <div class="absolute inset-0 bg-gradient-to-br from-primary-900/70 to-gray-900">
      <div class="absolute inset-0 opacity-20" style="background-image: url('https://images.pexels.com/photos/3184339/pexels-photo-3184339.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1'); background-size: cover; background-position: center; mix-blend-mode: overlay;"></div>
    </div>
    
    <div class="container relative">
      <div class="grid grid-cols-1 md:grid-cols-2 gap-12 items-center">
        <div v-motion="{ initial: { opacity: 0, x: -50 }, enter: { opacity: 1, x: 0, transition: { delay: 100 } } }">
          <h1 class="text-4xl md:text-5xl font-bold text-white mb-6 leading-tight">
            Unlock Your <span class="text-accent-400">Potential</span> with Premium Courses
          </h1>
          <p class="text-lg text-gray-300 mb-8 max-w-xl">
            Discover high-quality courses taught by industry experts. Elevate your skills and advance your career with our comprehensive learning platform.
          </p>
          <div class="flex flex-wrap gap-4">
            <NuxtLink to="/courses" class="btn btn-primary">
              Explore Courses
            </NuxtLink>
            <NuxtLink to="/premium" class="btn text-white border border-white/30 hover:bg-white/10 focus:ring-white">
              Join Premium
            </NuxtLink>
          </div>
          <div class="mt-8 flex items-center text-gray-300">
            <div class="flex -space-x-2">
              <img src="https://images.pexels.com/photos/220453/pexels-photo-220453.jpeg?auto=compress&cs=tinysrgb&w=800" alt="Student" class="w-10 h-10 rounded-full border-2 border-white">
              <img src="https://images.pexels.com/photos/774909/pexels-photo-774909.jpeg?auto=compress&cs=tinysrgb&w=800" alt="Student" class="w-10 h-10 rounded-full border-2 border-white">
              <img src="https://images.pexels.com/photos/1222271/pexels-photo-1222271.jpeg?auto=compress&cs=tinysrgb&w=800" alt="Student" class="w-10 h-10 rounded-full border-2 border-white">
              <div class="w-10 h-10 rounded-full border-2 border-white bg-primary-600 flex items-center justify-center text-xs font-semibold">+5k</div>
            </div>
            <span class="ml-4 text-sm">Join over 5,000 students learning daily</span>
          </div>
        </div>
        
        <div class="relative" v-motion="{ initial: { opacity: 0, y: 50 }, enter: { opacity: 1, y: 0, transition: { delay: 300 } } }">
          <div class="relative z-10 bg-white rounded-2xl shadow-xl overflow-hidden">
            <img src="https://images.pexels.com/photos/4144294/pexels-photo-4144294.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1" 
              alt="Student learning" class="w-full h-72 object-cover object-center" />
            <div class="p-6">
              <div class="flex justify-between items-center mb-4">
                <span class="badge badge-premium">Featured Course</span>
                <div class="flex items-center text-yellow-500">
                  <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
                    <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
                  </svg>
                  <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
                    <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
                  </svg>
                  <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
                    <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
                  </svg>
                  <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
                    <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
                  </svg>
                  <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
                    <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
                  </svg>
                </div>
              </div>
              <h3 class="text-lg font-semibold mb-2">Complete Web Development Bootcamp</h3>
              <p class="text-gray-600 text-sm mb-4">Learn modern web development from scratch and build real-world projects</p>
              <div class="flex justify-between items-center">
                <span class="text-accent-700 font-bold">Rp120.000</span>
                <NuxtLink to="/courses/1" class="btn btn-primary py-2 px-4">Enroll Now</NuxtLink>
              </div>
            </div>
          </div>
          
          <!-- Decorative elements -->
          <div class="absolute top-4 -left-4 w-24 h-24 bg-accent-500 rounded-full opacity-20 blur-xl animate-pulse"></div>
          <div class="absolute bottom-12 -right-8 w-32 h-32 bg-primary-500 rounded-full opacity-20 blur-xl animate-pulse"></div>
        </div>
      </div>
    </div>
  </section>
</template>