<template>
  <section class="section bg-primary-700 relative overflow-hidden">
    <!-- Background pattern -->
    <div class="absolute inset-0 opacity-10">
      <div class="absolute transform -rotate-12 bg-white/10 -left-10 w-[600px] h-[300px] rounded-[100px]"></div>
      <div class="absolute transform rotate-12 bg-white/10 -right-10 bottom-20 w-[600px] h-[300px] rounded-[100px]"></div>
    </div>
    
    <div class="container relative">
      <div class="max-w-3xl mx-auto text-center">
        <h2 class="text-3xl md:text-4xl font-bold text-white mb-6" v-motion="{ initial: { opacity: 0, y: 20 }, visible: { opacity: 1, y: 0 } }">
          Unlock Premium Content and Accelerate Your Learning
        </h2>
        <p class="text-lg text-primary-100 mb-8 max-w-xl mx-auto" v-motion="{ initial: { opacity: 0 }, visible: { opacity: 1, transition: { delay: 200 } } }">
          Join thousands of satisfied students and take your skills to the next level with our premium courses and exclusive content.
        </p>
        <div v-motion="{ initial: { opacity: 0, scale: 0.9 }, visible: { opacity: 1, scale: 1, transition: { delay: 400 } } }">
          <NuxtLink to="/premium" class="btn bg-white text-primary-700 hover:bg-primary-50">
            Explore Premium Plans
          </NuxtLink>
        </div>
        
        <div class="mt-12 grid grid-cols-1 md:grid-cols-3 gap-6">
          <div class="bg-white/10 backdrop-blur-sm rounded-xl p-6" 
            v-motion="{ initial: { opacity: 0, y: 20 }, visible: { opacity: 1, y: 0, transition: { delay: 200 } } }">
            <div class="w-12 h-12 bg-primary-500 rounded-full flex items-center justify-center mx-auto mb-4">
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6 text-white">
                <path stroke-linecap="round" stroke-linejoin="round" d="M12 6.042A8.967 8.967 0 006 3.75c-1.052 0-2.062.18-3 .512v14.25A8.987 8.987 0 016 18c2.305 0 4.408.867 6 2.292m0-14.25a8.966 8.966 0 016-2.292c1.052 0 2.062.18 3 .512v14.25A8.987 8.987 0 0018 18a8.967 8.967 0 00-6 2.292m0-14.25v14.25" />
              </svg>
            </div>
            <h3 class="text-xl font-semibold text-white mb-2 text-center">Exclusive Content</h3>
            <p class="text-primary-100 text-center">Access premium courses and materials not available to free users.</p>
          </div>
          
          <div class="bg-white/10 backdrop-blur-sm rounded-xl p-6" 
            v-motion="{ initial: { opacity: 0, y: 20 }, visible: { opacity: 1, y: 0, transition: { delay: 300 } } }">
            <div class="w-12 h-12 bg-primary-500 rounded-full flex items-center justify-center mx-auto mb-4">
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6 text-white">
                <path stroke-linecap="round" stroke-linejoin="round" d="M9.813 15.904L9 18.75l-.813-2.846a4.5 4.5 0 00-3.09-3.09L2.25 12l2.846-.813a4.5 4.5 0 003.09-3.09L9 5.25l.813 2.846a4.5 4.5 0 003.09 3.09L15.75 12l-2.846.813a4.5 4.5 0 00-3.09 3.09zM18.259 8.715L18 9.75l-.259-1.035a3.375 3.375 0 00-2.455-2.456L14.25 6l1.036-.259a3.375 3.375 0 002.455-2.456L18 2.25l.259 1.035a3.375 3.375 0 002.456 2.456L21.75 6l-1.035.259a3.375 3.375 0 00-2.456 2.456zM16.894 20.567L16.5 21.75l-.394-1.183a2.25 2.25 0 00-1.423-1.423L13.5 18.75l1.183-.394a2.25 2.25 0 001.423-1.423l.394-1.183.394 1.183a2.25 2.25 0 001.423 1.423l1.183.394-1.183.394a2.25 2.25 0 00-1.423 1.423z" />
              </svg>
            </div>
            <h3 class="text-xl font-semibold text-white mb-2 text-center">Expert Mentoring</h3>
            <p class="text-primary-100 text-center">Get personalized guidance from industry experts and instructors.</p>
          </div>
          
          <div class="bg-white/10 backdrop-blur-sm rounded-xl p-6" 
            v-motion="{ initial: { opacity: 0, y: 20 }, visible: { opacity: 1, y: 0, transition: { delay: 400 } } }">
            <div class="w-12 h-12 bg-primary-500 rounded-full flex items-center justify-center mx-auto mb-4">
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6 text-white">
                <path stroke-linecap="round" stroke-linejoin="round" d="M11.35 3.836c-.065.21-.1.433-.1.664 0 .414.336.75.75.75h4.5a.75.75 0 00.75-.75 2.25 2.25 0 00-.1-.664m-5.8 0A2.251 2.251 0 0113.5 2.25H15c1.012 0 1.867.668 2.15 1.586m-5.8 0c-.376.023-.75.05-1.124.08C9.095 4.01 8.25 4.973 8.25 6.108V8.25m8.9-4.414c.376.023.75.05 1.124.08 1.131.094 1.976 1.057 1.976 2.192V16.5A2.25 2.25 0 0118 18.75h-2.25m-7.5-10.5H4.875c-.621 0-1.125.504-1.125 1.125v11.25c0 .621.504 1.125 1.125 1.125h9.75c.621 0 1.125-.504 1.125-1.125V18.75m-7.5-10.5h6.375c.621 0 1.125.504 1.125 1.125v9.375m-8.25-3l1.5 1.5 3-3.75" />
              </svg>
            </div>
            <h3 class="text-xl font-semibold text-white mb-2 text-center">Completion Certificates</h3>
            <p class="text-primary-100 text-center">Earn recognized certificates to showcase your skills to employers.</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
// You can add animation logic here if needed
</script>