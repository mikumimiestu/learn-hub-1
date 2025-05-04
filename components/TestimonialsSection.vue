<template>
  <section class="section bg-gray-50">
    <div class="container">
      <div class="mb-12 text-center max-w-2xl mx-auto">
        <h2 class="text-3xl md:text-4xl font-bold mb-4">What Our Students Say</h2>
        <p class="text-gray-600">Hear from our community of learners who have transformed their skills and careers with TNGDemy.</p>
      </div>
      
      <div class="relative">
        <!-- Navigation buttons -->
        <button @click="prevTestimonial" 
          class="absolute left-0 top-1/2 -translate-y-1/2 z-10 bg-white rounded-full p-2 shadow-md hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-primary-500 md:-left-6 hidden md:block">
          <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5">
            <path stroke-linecap="round" stroke-linejoin="round" d="M15.75 19.5L8.25 12l7.5-7.5" />
          </svg>
        </button>
        
        <button @click="nextTestimonial" 
          class="absolute right-0 top-1/2 -translate-y-1/2 z-10 bg-white rounded-full p-2 shadow-md hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-primary-500 md:-right-6 hidden md:block">
          <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5">
            <path stroke-linecap="round" stroke-linejoin="round" d="M8.25 4.5l7.5 7.5-7.5 7.5" />
          </svg>
        </button>
      
        <div class="overflow-hidden">
          <div class="flex transition-transform duration-500 ease-in-out" :style="{ transform: `translateX(-${currentIndex * 100}%)` }">
            <div v-for="(testimonial, index) in testimonials" :key="index" class="min-w-full">
              <div class="bg-white rounded-xl p-8 shadow-sm mx-auto max-w-3xl">
                <div class="flex flex-col md:flex-row gap-6 items-center">
                  <div class="shrink-0">
                    <img :src="testimonial.avatar" :alt="testimonial.name" class="w-24 h-24 rounded-full object-cover border-4 border-primary-100">
                  </div>
                  <div>
                    <div class="flex mb-4 text-yellow-400">
                      <svg v-for="i in 5" :key="i" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-5 h-5">
                        <path fill-rule="evenodd" d="M10.788 3.21c.448-1.077 1.976-1.077 2.424 0l2.082 5.006 5.404.434c1.164.093 1.636 1.545.749 2.305l-4.117 3.527 1.257 5.273c.271 1.136-.964 2.033-1.96 1.425L12 18.354 7.373 21.18c-.996.608-2.231-.29-1.96-1.425l1.257-5.273-4.117-3.527c-.887-.76-.415-2.212.749-2.305l5.404-.434 2.082-5.005Z" clip-rule="evenodd" />
                      </svg>
                    </div>
                    <blockquote class="text-gray-700 italic mb-4">{{ testimonial.quote }}</blockquote>
                    <div>
                      <div class="font-semibold text-gray-900">{{ testimonial.name }}</div>
                      <div class="text-sm text-gray-500">{{ testimonial.title }}</div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        
        <!-- Indicators -->
        <div class="flex justify-center mt-6 space-x-2">
          <button v-for="(_, index) in testimonials" :key="index" 
            @click="setTestimonial(index)"
            class="w-2.5 h-2.5 rounded-full transition-colors duration-200"
            :class="index === currentIndex ? 'bg-primary-600' : 'bg-gray-300 hover:bg-gray-400'">
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue';

const testimonials = ref([
  {
    name: 'Emily Rodriguez',
    avatar: 'https://images.pexels.com/photos/774909/pexels-photo-774909.jpeg?auto=compress&cs=tinysrgb&w=800',
    title: 'UX Designer at Creative Tech',
    quote: 'The UX/UI Design Masterclass completely transformed my career. The instructor',
  },
  {
    name: 'Jason Kumar',
    avatar: 'https://images.pexels.com/photos/220453/pexels-photo-220453.jpeg?auto=compress&cs=tinysrgb&w=800',
    title: 'Full-Stack Developer',
    quote: 'I tried learning web development through various platforms, but TNGDemy',
  },
  {
    name: 'Sophia Chen',
    avatar: 'https://images.pexels.com/photos/1239291/pexels-photo-1239291.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1',
    title: 'Digital Marketing Specialist',
    quote: 'The Digital Marketing course provided practical, real-world strategies that I could immediately apply to my business. The instructor was responsive to questions and the community support was invaluable. Highly recommended!'
  }
]);

const currentIndex = ref(0);

const nextTestimonial = () => {
  currentIndex.value = (currentIndex.value + 1) % testimonials.value.length;
};

const prevTestimonial = () => {
  currentIndex.value = (currentIndex.value - 1 + testimonials.value.length) % testimonials.value.length;
};

const setTestimonial = (index) => {
  currentIndex.value = index;
};

// Auto slide functionality
let autoSlideInterval;

const startAutoSlide = () => {
  autoSlideInterval = setInterval(() => {
    nextTestimonial();
  }, 5000);
};

const stopAutoSlide = () => {
  clearInterval(autoSlideInterval);
};

// Start auto slide on component mount
onMounted(() => {
  startAutoSlide();
});

// Clean up on component unmount
onUnmounted(() => {
  stopAutoSlide();
});
</script>