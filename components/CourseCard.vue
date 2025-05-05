<template>
  <div class="card group h-full flex flex-col" 
    v-motion="{ initial: { opacity: 0, y: 20 }, visible: { opacity: 1, y: 0 } }">
    <div class="relative">
      <img :src="course.image" :alt="course.title" class="w-full h-48 object-cover" />
      <div v-if="course.isPremium" class="absolute top-3 right-3">
        <span class="badge badge-premium flex items-center">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-4 h-4 mr-1">
            <path fill-rule="evenodd" d="M10.788 3.21c.448-1.077 1.976-1.077 2.424 0l2.082 5.006 5.404.434c1.164.093 1.636 1.545.749 2.305l-4.117 3.527 1.257 5.273c.271 1.136-.964 2.033-1.96 1.425L12 18.354 7.373 21.18c-.996.608-2.231-.29-1.96-1.425l1.257-5.273-4.117-3.527c-.887-.76-.415-2.212.749-2.305l5.404-.434 2.082-5.005Z" clip-rule="evenodd" />
          </svg>
          Premium
        </span>
      </div>
    </div>
    <div class="p-5 flex-grow flex flex-col">
      <div class="flex-grow">
        <div class="flex items-center mb-2">
          <span class="badge bg-gray-100 text-gray-800">{{ course.category }}</span>
          <div class="ml-auto flex items-center text-yellow-500">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-4 h-4">
              <path fill-rule="evenodd" d="M10.788 3.21c.448-1.077 1.976-1.077 2.424 0l2.082 5.006 5.404.434c1.164.093 1.636 1.545.749 2.305l-4.117 3.527 1.257 5.273c.271 1.136-.964 2.033-1.96 1.425L12 18.354 7.373 21.18c-.996.608-2.231-.29-1.96-1.425l1.257-5.273-4.117-3.527c-.887-.76-.415-2.212.749-2.305l5.404-.434 2.082-5.005Z" clip-rule="evenodd" />
            </svg>
            <span class="ml-1 text-sm font-medium text-gray-700">{{ course.rating }}</span>
          </div>
        </div>
        <h3 class="text-lg font-semibold mb-2 group-hover:text-primary-600 transition-colors duration-200">{{ course.title }}</h3>
        <p class="text-gray-600 text-sm mb-4">{{ course.description }}</p>
        <div class="flex items-center mb-4">
          <img :src="course.instructor.avatar" :alt="course.instructor.name" class="w-8 h-8 rounded-full mr-2" />
          <span class="text-sm text-gray-700">{{ course.instructor.name }}</span>
        </div>
      </div>
      <div class="mt-auto pt-4 border-t border-gray-100 flex items-center justify-between">
        <div>
          <span v-if="course.isPremium" class="font-bold text-accent-700">Rp{{ course.price }}</span>
          <span v-else class="font-bold text-green-600">Free</span>
        </div>
        <NuxtLink :to="`/courses/${course.id}`" class="text-primary-600 hover:text-primary-700 font-medium text-sm">
          View Course
        </NuxtLink>
      </div>
    </div>
  </div>
</template>

<script setup>
defineProps({
  course: {
    type: Object,
    required: true
  }
});
</script>