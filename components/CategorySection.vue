<template>
  <section class="section bg-white">
    <div class="container">
      <div class="mb-12 text-center">
        <h2 class="text-3xl md:text-4xl font-bold mb-4">Browse by Category</h2>
        <p class="text-gray-600 max-w-2xl mx-auto">Explore our diverse range of course categories and find the perfect fit for your learning goals.</p>
      </div>
      
      <div class="grid grid-cols-2 md:grid-cols-4 gap-6">
        <div v-for="(category, index) in categories" :key="category.name"
          v-motion="{ initial: { opacity: 0, y: 20 }, visible: { opacity: 1, y: 0, transition: { delay: index * 100 } } }">
          <NuxtLink :to="`/courses?category=${category.slug}`" class="block group">
            <div class="relative overflow-hidden bg-gray-100 rounded-xl aspect-square flex items-center justify-center transition-all duration-300 group-hover:shadow-lg group-hover:scale-[1.02]">
              <div class="absolute inset-0 bg-gradient-to-br opacity-90"
                :class="[`from-${category.color}-100`, `to-${category.color}-500`]"></div>
              <img :src="category.image" :alt="category.name" class="absolute inset-0 w-full h-full object-cover mix-blend-overlay opacity-40">
              <span class="relative text-lg font-bold text-gray-900">{{ category.name }}</span>
            </div>
            <div class="mt-4 text-center">
              <span class="text-gray-800 font-medium">{{ category.courseCount }} courses</span>
            </div>
          </NuxtLink>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue';

const categories = ref([
  {
    name: 'Development',
    slug: 'development',
    image: 'https://images.pexels.com/photos/270373/pexels-photo-270373.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1',
    courseCount: 124,
    color: 'primary'
  },
  {
    name: 'Design',
    slug: 'design',
    image: 'https://images.pexels.com/photos/326501/pexels-photo-326501.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1',
    courseCount: 89,
    color: 'secondary'
  },
  {
    name: 'Business',
    slug: 'business',
    image: 'https://images.pexels.com/photos/3184339/pexels-photo-3184339.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1',
    courseCount: 65,
    color: 'accent'
  },
  {
    name: 'Marketing',
    slug: 'marketing',
    image: 'https://images.pexels.com/photos/905163/pexels-photo-905163.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1',
    courseCount: 43,
    color: 'success'
  }
]);
</script>