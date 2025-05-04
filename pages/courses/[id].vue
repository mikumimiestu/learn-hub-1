<template>
  <div>
    <!-- Course Header -->
    <section class="bg-primary-700 py-16">
      <div class="container">
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-8 items-center">
          <div>
            <div class="flex items-center mb-4">
              <NuxtLink to="/courses" class="text-primary-200 hover:text-white mr-2 flex items-center">
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 mr-1">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M10.5 19.5L3 12m0 0l7.5-7.5M3 12h18" />
                </svg>
                Back to Courses
              </NuxtLink>
              <span class="badge badge-premium flex items-center" v-if="course.isPremium">
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-4 h-4 mr-1">
                  <path fill-rule="evenodd" d="M10.788 3.21c.448-1.077 1.976-1.077 2.424 0l2.082 5.006 5.404.434c1.164.093 1.636 1.545.749 2.305l-4.117 3.527 1.257 5.273c.271 1.136-.964 2.033-1.96 1.425L12 18.354 7.373 21.18c-.996.608-2.231-.29-1.96-1.425l1.257-5.273-4.117-3.527c-.887-.76-.415-2.212.749-2.305l5.404-.434 2.082-5.005Z" clip-rule="evenodd" />
                </svg>
                Premium
              </span>
            </div>
            <h1 class="text-3xl md:text-4xl font-bold text-white mb-4">{{ course.title }}</h1>
            <p class="text-primary-100 text-lg mb-6">{{ course.description }}</p>
            
            <div class="flex items-center mb-6">
              <div class="flex mr-4 text-yellow-400">
                <svg v-for="i in 5" :key="i" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" 
                  :fill="i <= Math.floor(course.rating) ? 'currentColor' : 'none'" 
                  :stroke="i <= Math.floor(course.rating) ? 'none' : 'currentColor'"
                  class="w-5 h-5">
                  <path fill-rule="evenodd" d="M10.788 3.21c.448-1.077 1.976-1.077 2.424 0l2.082 5.006 5.404.434c1.164.093 1.636 1.545.749 2.305l-4.117 3.527 1.257 5.273c.271 1.136-.964 2.033-1.96 1.425L12 18.354 7.373 21.18c-.996.608-2.231-.29-1.96-1.425l1.257-5.273-4.117-3.527c-.887-.76-.415-2.212.749-2.305l5.404-.434 2.082-5.005Z" clip-rule="evenodd" />
                </svg>
                <span class="ml-2 text-white">{{ course.rating }} ({{ course.reviewCount }} reviews)</span>
              </div>
              <span class="text-primary-100">{{ course.students.toLocaleString() }} students</span>
            </div>
            
            <div class="flex items-center mb-8">
              <img :src="course.instructor.avatar" :alt="course.instructor.name" class="w-10 h-10 rounded-full mr-3 border-2 border-white">
              <div>
                <p class="text-white font-medium">{{ course.instructor.name }}</p>
                <p class="text-primary-200 text-sm">{{ course.instructor.title }}</p>
              </div>
            </div>
            
            <div class="flex flex-wrap gap-4">
              <NuxtLink :to="course.isPremium ? '/payment' : '/dashboard'" 
                class="btn bg-accent-600 hover:bg-accent-700 text-white">
                {{ course.isPremium ? `Enroll for $${course.price}` : 'Enroll for Free' }}
              </NuxtLink>
              <button class="btn text-white border border-white/30 hover:bg-white/10 focus:ring-white flex items-center">
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 mr-2">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M17.593 3.322c1.1.128 1.907 1.077 1.907 2.185V21L12 17.25 4.5 21V5.507c0-1.108.806-2.057 1.907-2.185a48.507 48.507 0 0111.186 0z" />
                </svg>
                Save for Later
              </button>
            </div>
          </div>
          
          <div class="relative"
            v-motion="{ initial: { opacity: 0, scale: 0.9 }, visible: { opacity: 1, scale: 1 } }">
            <div class="rounded-xl overflow-hidden shadow-xl">
              <img :src="course.image" :alt="course.title" class="w-full h-72 object-cover">
              <div class="bg-black/80 p-4 flex items-center justify-center">
                <button class="flex items-center text-white">
                  <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-12 h-12">
                    <path fill-rule="evenodd" d="M2.25 12c0-5.385 4.365-9.75 9.75-9.75s9.75 4.365 9.75 9.75-4.365 9.75-9.75 9.75S2.25 17.385 2.25 12zm14.024-.983a1.125 1.125 0 010 1.966l-5.603 3.113A1.125 1.125 0 019 15.113V8.887c0-.857.921-1.4 1.671-.983l5.603 3.113z" clip-rule="evenodd" />
                  </svg>
                  <span class="ml-2 text-lg font-medium">Watch Preview</span>
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
    
    <!-- Course Content -->
    <section class="section bg-white">
      <div class="container">
        <div class="grid grid-cols-1 lg:grid-cols-3 gap-12">
          <!-- Left Column: Course Details -->
          <div class="lg:col-span-2">
            <!-- What You'll Learn -->
            <div class="mb-12">
              <h2 class="text-2xl font-bold mb-6">What You'll Learn</h2>
              <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                <div v-for="(item, index) in course.learningOutcomes" :key="index" class="flex">
                  <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-6 h-6 text-green-500 mr-2 flex-shrink-0">
                    <path fill-rule="evenodd" d="M2.25 12c0-5.385 4.365-9.75 9.75-9.75s9.75 4.365 9.75 9.75-4.365 9.75-9.75 9.75S2.25 17.385 2.25 12zm13.36-1.814a.75.75 0 10-1.22-.872l-3.236 4.53L9.53 12.22a.75.75 0 00-1.06 1.06l2.25 2.25a.75.75 0 001.14-.094l3.75-5.25z" clip-rule="evenodd" />
                  </svg>
                  <span>{{ item }}</span>
                </div>
              </div>
            </div>
            
            <!-- Course Curriculum -->
            <div class="mb-12">
              <h2 class="text-2xl font-bold mb-6">Course Curriculum</h2>
              <div class="border border-gray-200 rounded-xl overflow-hidden divide-y divide-gray-200">
                <div v-for="(section, index) in course.curriculum" :key="index" class="bg-white">
                  <button @click="toggleSection(index)" class="flex justify-between items-center w-full p-4 text-left hover:bg-gray-50 transition-colors">
                    <div class="flex items-center">
                      <span class="font-medium text-lg">{{ section.title }}</span>
                      <span class="ml-2 text-sm text-gray-500">{{ section.lectures }} lectures • {{ section.duration }}</span>
                    </div>
                    <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" 
                      class="w-5 h-5 transition-transform" :class="{ 'rotate-180': openSections[index] }">
                      <path stroke-linecap="round" stroke-linejoin="round" d="M19.5 8.25l-7.5 7.5-7.5-7.5" />
                    </svg>
                  </button>
                  
                  <div v-show="openSections[index]" class="px-4 pb-4">
                    <ul class="divide-y divide-gray-100">
                      <li v-for="(lecture, lectureIndex) in section.content" :key="lectureIndex" class="flex items-center py-3">
                        <div class="mr-3">
                          <svg v-if="lecture.type === 'video'" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-5 h-5 text-primary-600">
                            <path fill-rule="evenodd" d="M2.25 12c0-5.385 4.365-9.75 9.75-9.75s9.75 4.365 9.75 9.75-4.365 9.75-9.75 9.75S2.25 17.385 2.25 12zm14.024-.983a1.125 1.125 0 010 1.966l-5.603 3.113A1.125 1.125 0 019 15.113V8.887c0-.857.921-1.4 1.671-.983l5.603 3.113z" clip-rule="evenodd" />
                          </svg>
                          <svg v-else-if="lecture.type === 'quiz'" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-5 h-5 text-accent-600">
                            <path fill-rule="evenodd" d="M2.25 12c0-5.385 4.365-9.75 9.75-9.75s9.75 4.365 9.75 9.75-4.365 9.75-9.75 9.75S2.25 17.385 2.25 12zm11.378-3.917c-.89-.777-2.366-.777-3.255 0a.75.75 0 01-.988-1.129c1.454-1.272 3.776-1.272 5.23 0 1.513 1.324 1.513 3.518 0 4.842a3.75 3.75 0 01-.837.552c-.676.328-1.028.774-1.028 1.152v.75a.75.75 0 01-1.5 0v-.75c0-1.279 1.06-2.107 1.875-2.502.182-.088.351-.199.503-.331.83-.727.83-1.857 0-2.584zM12 18a.75.75 0 100-1.5.75.75 0 000 1.5z" clip-rule="evenodd" />
                          </svg>
                          <svg v-else xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-5 h-5 text-gray-500">
                            <path fill-rule="evenodd" d="M5.625 1.5c-1.036 0-1.875.84-1.875 1.875v17.25c0 1.035.84 1.875 1.875 1.875h12.75c1.035 0 1.875-.84 1.875-1.875V12.75A3.75 3.75 0 0016.5 9h-1.875a1.875 1.875 0 01-1.875-1.875V5.25A3.75 3.75 0 009 1.5H5.625zM7.5 15a.75.75 0 01.75-.75h7.5a.75.75 0 010 1.5h-7.5A.75.75 0 017.5 15zm.75 2.25a.75.75 0 000 1.5H12a.75.75 0 000-1.5H8.25z" clip-rule="evenodd" />
                            <path d="M12.971 1.816A5.23 5.23 0 0114.25 5.25v1.875c0 .207.168.375.375.375H16.5a5.23 5.23 0 013.434 1.279 9.768 9.768 0 00-6.963-6.963z" />
                          </svg>
                        </div>
                        <div class="flex-grow flex justify-between">
                          <span>{{ lecture.title }}</span>
                          <div class="flex items-center">
                            <span class="text-sm text-gray-500 mr-3">{{ lecture.duration }}</span>
                            <div v-if="lecture.preview && !lecture.locked" class="badge bg-green-100 text-green-800 text-xs">Preview</div>
                            <div v-else-if="lecture.locked" class="text-gray-400">
                              <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-4 h-4">
                                <path fill-rule="evenodd" d="M12 1.5a5.25 5.25 0 00-5.25 5.25v3a3 3 0 00-3 3v6.75a3 3 0 003 3h10.5a3 3 0 003-3v-6.75a3 3 0 00-3-3v-3c0-2.9-2.35-5.25-5.25-5.25zm3.75 8.25v-3a3.75 3.75 0 10-7.5 0v3h7.5z" clip-rule="evenodd" />
                              </svg>
                            </div>
                          </div>
                        </div>
                      </li>
                    </ul>
                  </div>
                </div>
              </div>
            </div>
            
            <!-- Requirements -->
            <div class="mb-12">
              <h2 class="text-2xl font-bold mb-6">Requirements</h2>
              <ul class="space-y-2">
                <li v-for="(req, index) in course.requirements" :key="index" class="flex items-start">
                  <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-5 h-5 text-primary-600 mr-2 mt-0.5">
                    <path fill-rule="evenodd" d="M16.28 11.47a.75.75 0 010 1.06l-7.5 7.5a.75.75 0 01-1.06-1.06L14.69 12 7.72 5.03a.75.75 0 011.06-1.06l7.5 7.5z" clip-rule="evenodd" />
                  </svg>
                  <span>{{ req }}</span>
                </li>
              </ul>
            </div>
            
            <!-- Description -->
            <div class="mb-12">
              <h2 class="text-2xl font-bold mb-6">Description</h2>
              <div class="space-y-4 text-gray-700">
                <p v-for="(para, index) in course.descriptionFull" :key="index">{{ para }}</p>
              </div>
            </div>
            
            <!-- Instructor -->
            <div>
              <h2 class="text-2xl font-bold mb-6">Instructor</h2>
              <div class="bg-gray-50 rounded-xl p-6">
                <div class="flex items-start">
                  <img :src="course.instructor.avatar" :alt="course.instructor.name" class="w-20 h-20 rounded-full mr-6">
                  <div>
                    <h3 class="text-xl font-semibold mb-1">{{ course.instructor.name }}</h3>
                    <p class="text-gray-600 mb-3">{{ course.instructor.title }}</p>
                    <div class="flex items-center space-x-4 mb-4">
                      <div class="flex items-center">
                        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-5 h-5 text-yellow-500 mr-1">
                          <path fill-rule="evenodd" d="M10.788 3.21c.448-1.077 1.976-1.077 2.424 0l2.082 5.006 5.404.434c1.164.093 1.636 1.545.749 2.305l-4.117 3.527 1.257 5.273c.271 1.136-.964 2.033-1.96 1.425L12 18.354 7.373 21.18c-.996.608-2.231-.29-1.96-1.425l1.257-5.273-4.117-3.527c-.887-.76-.415-2.212.749-2.305l5.404-.434 2.082-5.005Z" clip-rule="evenodd" />
                        </svg>
                        <span class="text-sm font-medium">{{ course.instructor.rating }} Instructor Rating</span>
                      </div>
                      <div class="flex items-center">
                        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-5 h-5 text-gray-600 mr-1">
                          <path d="M4.5 6.375a4.125 4.125 0 118.25 0 4.125 4.125 0 01-8.25 0zM14.25 8.625a3.375 3.375 0 116.75 0 3.375 3.375 0 01-6.75 0zM1.5 19.125a7.125 7.125 0 0114.25 0v.003l-.001.119a.75.75 0 01-.363.63 13.067 13.067 0 01-6.761 1.873c-2.472 0-4.786-.684-6.76-1.873a.75.75 0 01-.364-.63l-.001-.122zM17.25 19.128l-.001.144a2.25 2.25 0 01-.233.96 10.088 10.088 0 005.06-1.01.75.75 0 00.42-.643 4.875 4.875 0 00-6.957-4.611 8.586 8.586 0 011.71 5.157v.003z" />
                        </svg>
                        <span class="text-sm font-medium">{{ course.instructor.students.toLocaleString() }} Students</span>
                      </div>
                      <div class="flex items-center">
                        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-5 h-5 text-gray-600 mr-1">
                          <path d="M11.645 20.91l-.007-.003-.022-.012a15.247 15.247 0 01-.383-.218 25.18 25.18 0 01-4.244-3.17C4.688 15.36 2.25 12.174 2.25 8.25 2.25 5.322 4.714 3 7.688 3A5.5 5.5 0 0112 5.052 5.5 5.5 0 0116.313 3c2.973 0 5.437 2.322 5.437 5.25 0 3.925-2.438 7.111-4.739 9.256a25.175 25.175 0 01-4.244 3.17 15.247 15.247 0 01-.383.219l-.022.012-.007.004-.003.001a.752.752 0 01-.704 0l-.003-.001z" />
                        </svg>
                        <span class="text-sm font-medium">{{ course.instructor.reviews.toLocaleString() }} Reviews</span>
                      </div>
                    </div>
                    <p class="text-gray-700">{{ course.instructor.bio }}</p>
                  </div>
                </div>
              </div>
            </div>
          </div>
          
          <!-- Right Column: Course Info -->
          <div class="lg:sticky lg:top-24 lg:self-start">
            <div class="bg-white rounded-xl shadow-lg overflow-hidden border border-gray-200">
              <div class="p-6">
                <h3 class="text-xl font-bold mb-4">This course includes:</h3>
                <ul class="space-y-3">
                  <li v-for="(feature, index) in course.features" :key="index" class="flex">
                    <span class="text-primary-600 mr-3" v-html="feature.icon"></span>
                    <span>{{ feature.text }}</span>
                  </li>
                </ul>
                
                <div class="mt-6 pt-6 border-t border-gray-200">
                  <h4 class="font-semibold mb-2">Material Access:</h4>
                  <p class="text-gray-700 mb-4">{{ course.accessInfo }}</p>
                  
                  <h4 class="font-semibold mb-2">Certification:</h4>
                  <p class="text-gray-700">{{ course.certificationInfo }}</p>
                </div>
                
                <div class="mt-6 pt-6 border-t border-gray-200">
                  <NuxtLink :to="course.isPremium ? '/payment' : '/dashboard'" class="btn btn-accent w-full mb-3">
                    {{ course.isPremium ? `Enroll for $${course.price}` : 'Enroll for Free' }}
                  </NuxtLink>
                  <div class="text-center text-sm text-gray-500">30-Day Money-Back Guarantee</div>
                </div>
              </div>
            </div>
            
            <!-- Share Course -->
            <div class="mt-6 bg-white rounded-xl shadow-sm p-6 border border-gray-200">
              <h3 class="font-bold mb-4">Share this course</h3>
              <div class="flex space-x-4">
                <a href="#" class="text-gray-600 hover:text-primary-600 transition-colors">
                  <svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true">
                    <path fill-rule="evenodd" d="M22 12c0-5.523-4.477-10-10-10S2 6.477 2 12c0 4.991 3.657 9.128 8.438 9.878v-6.987h-2.54V12h2.54V9.797c0-2.506 1.492-3.89 3.777-3.89 1.094 0 2.238.195 2.238.195v2.46h-1.26c-1.243 0-1.63.771-1.63 1.562V12h2.773l-.443 2.89h-2.33v6.988C18.343 21.128 22 16.991 22 12z" clip-rule="evenodd" />
                  </svg>
                </a>
                <a href="#" class="text-gray-600 hover:text-primary-600 transition-colors">
                  <svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true">
                    <path d="M8.29 20.251c7.547 0 11.675-6.253 11.675-11.675 0-.178 0-.355-.012-.53A8.348 8.348 0 0022 5.92a8.19 8.19 0 01-2.357.646 4.118 4.118 0 001.804-2.27 8.224 8.224 0 01-2.605.996 4.107 4.107 0 00-6.993 3.743 11.65 11.65 0 01-8.457-4.287 4.106 4.106 0 001.27 5.477A4.072 4.072 0 012.8 9.713v.052a4.105 4.105 0 003.292 4.022 4.095 4.095 0 01-1.853.07 4.108 4.108 0 003.834 2.85A8.233 8.233 0 012 18.407a11.616 11.616 0 006.29 1.84" />
                  </svg>
                </a>
                <a href="#" class="text-gray-600 hover:text-primary-600 transition-colors">
                  <svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true">
                    <path fill-rule="evenodd" d="M12.315 2c2.43 0 2.784.013 3.808.06 1.064.049 1.791.218 2.427.465a4.902 4.902 0 011.772 1.153 4.902 4.902 0 011.153 1.772c.247.636.416 1.363.465 2.427.048 1.067.06 1.407.06 4.123v.08c0 2.643-.012 2.987-.06 4.043-.049 1.064-.218 1.791-.465 2.427a4.902 4.902 0 01-1.153 1.772 4.902 4.902 0 01-1.772 1.153c-.636.247-1.363.416-2.427.465-1.067.048-1.407.06-4.123.06h-.08c-2.643 0-2.987-.012-4.043-.06-1.064-.049-1.791-.218-2.427-.465a4.902 4.902 0 01-1.772-1.153 4.902 4.902 0 01-1.153-1.772c-.247-.636-.416-1.363-.465-2.427-.047-1.024-.06-1.379-.06-3.808v-.63c0-2.43.013-2.784.06-3.808.049-1.064.218-1.791.465-2.427a4.902 4.902 0 011.153-1.772A4.902 4.902 0 015.45 2.525c.636-.247 1.363-.416 2.427-.465C8.901 2.013 9.256 2 11.685 2h.63zm-.081 1.802h-.468c-2.456 0-2.784.011-3.807.058-.975.045-1.504.207-1.857.344-.467.182-.8.398-1.15.748-.35.35-.566.683-.748 1.15-.137.353-.3.882-.344 1.857-.047 1.023-.058 1.351-.058 3.807v.468c0 2.456.011 2.784.058 3.807.045.975.207 1.504.344 1.857.182.466.399.8.748 1.15.35.35.683.566 1.15.748.353.137.882.3 1.857.344 1.054.048 1.37.058 4.041.058h.08c2.597 0 2.917-.01 3.96-.058.976-.045 1.505-.207 1.858-.344.466-.182.8-.398 1.15-.748.35-.35.566-.683.748-1.15.137-.353.3-.882.344-1.857.048-1.055.058-1.37.058-4.041v-.08c0-2.597-.01-2.917-.058-3.96-.045-.976-.207-1.505-.344-1.858a3.097 3.097 0 00-.748-1.15 3.098 3.098 0 00-1.15-.748c-.353-.137-.882-.3-1.857-.344-1.023-.047-1.351-.058-3.807-.058zM12 6.865a5.135 5.135 0 110 10.27 5.135 5.135 0 010-10.27zm0 1.802a3.333 3.333 0 100 6.666 3.333 3.333 0 000-6.666zm5.338-3.205a1.2 1.2 0 110 2.4 1.2 1.2 0 010-2.4z" clip-rule="evenodd" />
                  </svg>
                </a>
                <a href="#" class="text-gray-600 hover:text-primary-600 transition-colors">
                  <svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true">
                    <path fill-rule="evenodd" d="M19.812 5.418c.861.23 1.538.907 1.768 1.768C21.998 8.746 22 12 22 12s0 3.255-.418 4.814a2.504 2.504 0 0 1-1.768 1.768c-1.56.419-7.814.419-7.814.419s-6.255 0-7.814-.419a2.505 2.505 0 0 1-1.768-1.768C2 15.255 2 12 2 12s0-3.255.417-4.814a2.507 2.507 0 0 1 1.768-1.768C5.744 5 11.998 5 11.998 5s6.255 0 7.814.418ZM15.194 12 10 15V9l5.194 3Z" clip-rule="evenodd" />
                  </svg>
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
    
    <!-- Similar Courses -->
    <section class="section bg-gray-50">
      <div class="container">
        <h2 class="text-2xl font-bold mb-8">Similar Courses You May Like</h2>
        <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
          <CourseCard v-for="course in similarCourses" :key="course.id" :course="course" />
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref, computed, onMounted } from 'vue';

const route = useRoute();
const courseId = parseInt(route.params.id);

// Simulation of getting the course data based on ID
const selectedCourse = ref(null);
const openSections = ref([true, false, false]);
const similarCourses = ref([]);

// Sample data for the selected course
const courses = [
  {
    id: 1,
    title: 'Complete Web Development Bootcamp',
    description: 'Master HTML, CSS, JavaScript, React and Node.js with this comprehensive course.',
    descriptionFull: [
      'This comprehensive Web Development Bootcamp covers everything you need to know to become a full-stack web developer.',
      'You\'ll learn the latest technologies including HTML5, CSS3, JavaScript ES6+, React, Node.js, Express, and MongoDB. By the end of this course, you\'ll be able to build complete, responsive websites and web applications from scratch.',
      'Through hands-on projects and real-world examples, you\'ll gain practical experience that will prepare you for a career in web development. Whether you\'re a complete beginner or looking to level up your skills, this course has something for everyone.'
    ],
    image: 'https://images.pexels.com/photos/1181271/pexels-photo-1181271.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1',
    category: 'Development',
    rating: 4.9,
    reviewCount: 4578,
    price: 89.99,
    isPremium: true,
    students: 58972,
    instructor: {
      name: 'Alex Johnson',
      avatar: 'https://images.pexels.com/photos/220453/pexels-photo-220453.jpeg?auto=compress&cs=tinysrgb&w=800',
      title: 'Senior Web Developer & Educator',
      rating: 4.8,
      students: 154000,
      reviews: 12500,
      bio: 'Alex has over 10 years of experience in web development and has worked with companies like Google and Facebook. He\'s passionate about teaching and has helped thousands of students launch their careers in tech.'
    },
    learningOutcomes: [
      'Build 16 web development projects for your portfolio',
      'Learn the latest technologies, including JavaScript, React, Node and more',
      'Create a responsive website using HTML5, CSS3, and JavaScript',
      'Build RESTful APIs with Node.js and Express',
      'Implement authentication and security features',
      'Work with databases like MongoDB and MySQL',
      'Deploy your applications to production',
      'Understand web development best practices and patterns'
    ],
    requirements: [
      'No programming experience needed - I\'ll teach you everything you need to know',
      'A computer with access to the internet',
      'No paid software required - all tools used in the course are free',
      'A basic understanding of how to use a computer'
    ],
    curriculum: [
      {
        title: 'Section 1: Introduction to Web Development',
        lectures: 12,
        duration: '2h 15m',
        content: [
          { title: 'Welcome to the Course', duration: '5:22', type: 'video', preview: true, locked: false },
          { title: 'How the Internet Works', duration: '8:45', type: 'video', preview: true, locked: false },
          { title: 'Web Development Overview', duration: '10:15', type: 'video', preview: false, locked: false },
          { title: 'Setting Up Your Development Environment', duration: '15:30', type: 'video', preview: false, locked: false },
          { title: 'Your First Web Page', duration: '12:45', type: 'exercise', preview: false, locked: false }
        ]
      },
      {
        title: 'Section 2: HTML5 Fundamentals',
        lectures: 15,
        duration: '3h 20m',
        content: [
          { title: 'HTML Document Structure', duration: '9:30', type: 'video', preview: false, locked: false },
          { title: 'Working with Text Elements', duration: '12:15', type: 'video', preview: false, locked: false },
          { title: 'HTML Lists and Tables', duration: '14:22', type: 'video', preview: false, locked: true },
          { title: 'HTML Forms and Inputs', duration: '18:10', type: 'video', preview: false, locked: true },
          { title: 'Section Quiz', duration: '15 questions', type: 'quiz', preview: false, locked: true }
        ]
      },
      {
        title: 'Section 3: CSS Styling',
        lectures: 18,
        duration: '4h 45m',
        content: [
          { title: 'Introduction to CSS', duration: '11:20', type: 'video', preview: false, locked: true },
          { title: 'Selectors and Properties', duration: '15:45', type: 'video', preview: false, locked: true },
          { title: 'Box Model Explained', duration: '14:30', type: 'video', preview: false, locked: true },
          { title: 'Flexbox Layout', duration: '22:15', type: 'video', preview: false, locked: true },
          { title: 'CSS Grid Layout', duration: '25:18', type: 'video', preview: false, locked: true }
        ]
      }
    ],
    features: [
      { 
        text: '35 hours on-demand video', 
        icon: '<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-6 h-6"><path fill-rule="evenodd" d="M2.25 12c0-5.385 4.365-9.75 9.75-9.75s9.75 4.365 9.75 9.75-4.365 9.75-9.75 9.75S2.25 17.385 2.25 12zm14.024-.983a1.125 1.125 0 010 1.966l-5.603 3.113A1.125 1.125 0 019 15.113V8.887c0-.857.921-1.4 1.671-.983l5.603 3.113z" clip-rule="evenodd" /></svg>'
      },
      { 
        text: '90+ downloadable resources', 
        icon: '<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-6 h-6"><path fill-rule="evenodd" d="M12 2.25a.75.75 0 01.75.75v11.69l3.22-3.22a.75.75 0 111.06 1.06l-4.5 4.5a.75.75 0 01-1.06 0l-4.5-4.5a.75.75 0 111.06-1.06l3.22 3.22V3a.75.75 0 01.75-.75zm-9 13.5a.75.75 0 01.75.75v2.25a1.5 1.5 0 001.5 1.5h13.5a1.5 1.5 0 001.5-1.5V16.5a.75.75 0 011.5 0v2.25a3 3 0 01-3 3H5.25a3 3 0 01-3-3V16.5a.75.75 0 01.75-.75z" clip-rule="evenodd" /></svg>'
      },
      { 
        text: '15 coding exercises', 
        icon: '<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-6 h-6"><path fill-rule="evenodd" d="M14.447 3.027a.75.75 0 01.527.92l-4.5 16.5a.75.75 0 01-1.448-.394l4.5-16.5a.75.75 0 01.921-.526zM16.72 6.22a.75.75 0 011.06 0l5.25 5.25a.75.75 0 010 1.06l-5.25 5.25a.75.75 0 11-1.06-1.06L21.44 12l-4.72-4.72a.75.75 0 010-1.06zm-9.44 0a.75.75 0 010 1.06L2.56 12l4.72 4.72a.75.75 0 11-1.06 1.06L.97 12.53a.75.75 0 010-1.06l5.25-5.25a.75.75 0 011.06 0z" clip-rule="evenodd" /></svg>'
      },
      { 
        text: '16 real-world projects', 
        icon: '<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-6 h-6"><path d="M11.644 1.59a.75.75 0 01.712 0l9.75 5.25a.75.75 0 010 1.32l-9.75 5.25a.75.75 0 01-.712 0l-9.75-5.25a.75.75 0 010-1.32l9.75-5.25z" /><path d="M3.265 10.602l7.668 4.129a2.25 2.25 0 002.134 0l7.668-4.13 1.37.739a.75.75 0 010 1.32l-9.75 5.25a.75.75 0 01-.71 0l-9.75-5.25a.75.75 0 010-1.32l1.37-.738z" /><path d="M10.933 19.231l-7.668-4.13-1.37.739a.75.75 0 000 1.32l9.75 5.25c.221.12.489.12.71 0l9.75-5.25a.75.75 0 000-1.32l-1.37-.738-7.668 4.13a2.25 2.25 0 01-2.134-.001z" /></svg>'
      },
      { 
        text: 'Full lifetime access', 
        icon: '<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-6 h-6"><path d="M12.75 12.75a.75.75 0 11-1.5 0 .75.75 0 011.5 0zM7.5 15.75a.75.75 0 100-1.5.75.75 0 000 1.5zM8.25 17.25a.75.75 0 11-1.5 0 .75.75 0 011.5 0zM9.75 15.75a.75.75 0 100-1.5.75.75 0 000 1.5zM10.5 17.25a.75.75 0 11-1.5 0 .75.75 0 011.5 0zM12 15.75a.75.75 0 100-1.5.75.75 0 000 1.5zM12.75 17.25a.75.75 0 11-1.5 0 .75.75 0 011.5 0zM14.25 15.75a.75.75 0 100-1.5.75.75 0 000 1.5zM15 17.25a.75.75 0 11-1.5 0 .75.75 0 011.5 0zM16.5 15.75a.75.75 0 100-1.5.75.75 0 000 1.5zM15 12.75a.75.75 0 11-1.5 0 .75.75 0 011.5 0zM16.5 13.5a.75.75 0 100-1.5.75.75 0 000 1.5z" /><path fill-rule="evenodd" d="M6.75 2.25A.75.75 0 017.5 3v1.5h9V3A.75.75 0 0118 3v1.5h.75a3 3 0 013 3v11.25a3 3 0 01-3 3H5.25a3 3 0 01-3-3V7.5a3 3 0 013-3H6V3a.75.75 0 01.75-.75zm13.5 9a1.5 1.5 0 00-1.5-1.5H5.25a1.5 1.5 0 00-1.5 1.5v7.5a1.5 1.5 0 001.5 1.5h13.5a1.5 1.5 0 001.5-1.5v-7.5z" clip-rule="evenodd" /></svg>'
      },
      { 
        text: 'Certificate of completion', 
        icon: '<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-6 h-6"><path fill-rule="evenodd" d="M7.502 6h7.128A3.375 3.375 0 0118 9.375v9.375a3 3 0 003-3V6.108c0-1.505-1.125-2.811-2.664-2.94a48.972 48.972 0 00-.673-.05A3 3 0 0015 1.5h-1.5a3 3 0 00-2.663 1.618c-.225.015-.45.032-.673.05C8.662 3.295 7.554 4.542 7.502 6zM13.5 3A1.5 1.5 0 0012 4.5h4.5A1.5 1.5 0 0015 3h-1.5z" clip-rule="evenodd" /><path fill-rule="evenodd" d="M3 9.375C3 8.339 3.84 7.5 4.875 7.5h9.75c1.036 0 1.875.84 1.875 1.875v11.25c0 1.035-.84 1.875-1.875 1.875h-9.75A1.875 1.875 0 013 20.625V9.375zM6 12a.75.75 0 01.75-.75h.008a.75.75 0 01.75.75v.008a.75.75 0 01-.75.75H6.75a.75.75 0 01-.75-.75V12zm2.25 0a.75.75 0 01.75-.75h3.75a.75.75 0 010 1.5H9a.75.75 0 01-.75-.75zM6 15a.75.75 0 01.75-.75h.008a.75.75 0 01.75.75v.008a.75.75 0 01-.75.75H6.75a.75.75 0 01-.75-.75V15zm2.25 0a.75.75 0 01.75-.75h3.75a.75.75 0 010 1.5H9a.75.75 0 01-.75-.75zM6 18a.75.75 0 01.75-.75h.008a.75.75 0 01.75.75v.008a.75.75 0 01-.75.75H6.75a.75.75 0 01-.75-.75V18zm2.25 0a.75.75 0 01.75-.75h3.75a.75.75 0 010 1.5H9a.75.75 0 01-.75-.75z" clip-rule="evenodd" /></svg>'
      }
    ],
    accessInfo: 'Full lifetime access on mobile and desktop',
    certificationInfo: 'Earn a certificate of completion after finishing all course materials'
  },
  {
    id: 2,
    title: 'UX/UI Design Masterclass',
    description: 'Learn to create stunning user interfaces and enhance user experience.',
    descriptionFull: [
      'The UX/UI Design Masterclass is your comprehensive guide to creating beautiful, user-friendly interfaces that people love to use.',
      'You\'ll learn both the theory and practice of user experience and user interface design, from understanding user psychology to creating high-fidelity prototypes in industry-standard tools like Figma and Adobe XD.',
      'This course covers the entire design process from research and wireframing to prototyping and user testing. By the end, you\'ll have a professional portfolio showcasing your design skills to potential employers or clients.'
    ],
    image: 'https://images.pexels.com/photos/196644/pexels-photo-196644.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1',
    category: 'Design',
    rating: 4.8,
    reviewCount: 3287,
    price: 79.99,
    isPremium: true,
    students: 42568,
    instructor: {
      name: 'Sarah Williams',
      avatar: 'https://images.pexels.com/photos/774909/pexels-photo-774909.jpeg?auto=compress&cs=tinysrgb&w=800',
      title: 'UX Designer & Creative Director',
      rating: 4.9,
      students: 125000,
      reviews: 9800,
      bio: 'Sarah is a UX/UI design expert with over 12 years of experience working with brands like Apple, Airbnb, and Uber. She specializes in creating intuitive, accessible, and beautiful user interfaces.'
    },
    learningOutcomes: [
      'Master the principles of user experience design',
      'Create wireframes and prototypes using industry-standard tools',
      'Conduct user research and usability testing',
      'Design responsive interfaces for web and mobile',
      'Apply color theory and typography principles',
      'Create a professional UX/UI portfolio',
      'Present and justify your design decisions',
      'Understand design systems and component libraries'
    ],
    requirements: [
      'No prior design experience required',
      'A computer (Mac or Windows) with internet access',
      'Basic computer skills',
      'Free tools will be used for most of the course'
    ],
    curriculum: [
      {
        title: 'Section 1: Introduction to UX/UI Design',
        lectures: 10,
        duration: '1h 45m',
        content: [
          { title: 'Welcome to UX/UI Design Masterclass', duration: '4:15', type: 'video', preview: true, locked: false },
          { title: 'UX vs UI: Understanding the Difference', duration: '8:30', type: 'video', preview: true, locked: false },
          { title: 'The Design Process Overview', duration: '12:20', type: 'video', preview: false, locked: false },
          { title: 'Design Thinking Methodology', duration: '15:30', type: 'video', preview: false, locked: false },
          { title: 'Design Tools Introduction', duration: '10:15', type: 'video', preview: false, locked: false }
        ]
      },
      {
        title: 'Section 2: User Research',
        lectures: 12,
        duration: '2h 30m',
        content: [
          { title: 'Understanding Your Users', duration: '11:45', type: 'video', preview: false, locked: false },
          { title: 'User Personas Creation', duration: '14:20', type: 'video', preview: false, locked: false },
          { title: 'Conducting User Interviews', duration: '18:30', type: 'video', preview: false, locked: true },
          { title: 'User Journey Mapping', duration: '15:15', type: 'video', preview: false, locked: true },
          { title: 'Research Methods Quiz', duration: '10 questions', type: 'quiz', preview: false, locked: true }
        ]
      },
      {
        title: 'Section 3: Wireframing and Prototyping',
        lectures: 15,
        duration: '3h 15m',
        content: [
          { title: 'Introduction to Wireframing', duration: '10:30', type: 'video', preview: false, locked: true },
          { title: 'Creating Low-Fidelity Wireframes', duration: '22:15', type: 'video', preview: false, locked: true },
          { title: 'High-Fidelity Wireframes', duration: '25:40', type: 'video', preview: false, locked: true },
          { title: 'Interactive Prototyping', duration: '18:30', type: 'video', preview: false, locked: true },
          { title: 'User Testing with Prototypes', duration: '15:45', type: 'video', preview: false, locked: true }
        ]
      }
    ],
    features: [
      { 
        text: '25 hours on-demand video', 
        icon: '<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-6 h-6"><path fill-rule="evenodd" d="M2.25 12c0-5.385 4.365-9.75 9.75-9.75s9.75 4.365 9.75 9.75-4.365 9.75-9.75 9.75S2.25 17.385 2.25 12zm14.024-.983a1.125 1.125 0 010 1.966l-5.603 3.113A1.125 1.125 0 019 15.113V8.887c0-.857.921-1.4 1.671-.983l5.603 3.113z" clip-rule="evenodd" /></svg>'
      },
      { 
        text: '75 downloadable resources', 
        icon: '<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-6 h-6"><path fill-rule="evenodd" d="M12 2.25a.75.75 0 01.75.75v11.69l3.22-3.22a.75.75 0 111.06 1.06l-4.5 4.5a.75.75 0 01-1.06 0l-4.5-4.5a.75.75 0 111.06-1.06l3.22 3.22V3a.75.75 0 01.75-.75zm-9 13.5a.75.75 0 01.75.75v2.25a1.5 1.5 0 001.5 1.5h13.5a1.5 1.5 0 001.5-1.5V16.5a.75.75 0 011.5 0v2.25a3 3 0 01-3 3H5.25a3 3 0 01-3-3V16.5a.75.75 0 01.75-.75z" clip-rule="evenodd" /></svg>'
      },
      { 
        text: '10 practical exercises', 
        icon: '<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-6 h-6"><path fill-rule="evenodd" d="M14.447 3.027a.75.75 0 01.527.92l-4.5 16.5a.75.75 0 01-1.448-.394l4.5-16.5a.75.75 0 01.921-.526zM16.72 6.22a.75.75 0 011.06 0l5.25 5.25a.75.75 0 010 1.06l-5.25 5.25a.75.75 0 11-1.06-1.06L21.44 12l-4.72-4.72a.75.75 0 010-1.06zm-9.44 0a.75.75 0 010 1.06L2.56 12l4.72 4.72a.75.75 0 11-1.06 1.06L.97 12.53a.75.75 0 010-1.06l5.25-5.25a.75.75 0 011.06 0z" clip-rule="evenodd" /></svg>'
      },
      { 
        text: '5 real-world projects', 
        icon: '<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-6 h-6"><path d="M11.644 1.59a.75.75 0 01.712 0l9.75 5.25a.75.75 0 010 1.32l-9.75 5.25a.75.75 0 01-.712 0l-9.75-5.25a.75.75 0 010-1.32l9.75-5.25z" /><path d="M3.265 10.602l7.668 4.129a2.25 2.25 0 002.134 0l7.668-4.13 1.37.739a.75.75 0 010 1.32l-9.75 5.25a.75.75 0 01-.71 0l-9.75-5.25a.75.75 0 010-1.32l1.37-.738z" /><path d="M10.933 19.231l-7.668-4.13-1.37.739a.75.75 0 000 1.32l9.75 5.25c.221.12.489.12.71 0l9.75-5.25a.75.75 0 000-1.32l-1.37-.738-7.668 4.13a2.25 2.25 0 01-2.134-.001z" /></svg>'
      },
      { 
        text: 'Full lifetime access', 
        icon: '<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-6 h-6"><path d="M12.75 12.75a.75.75 0 11-1.5 0 .75.75 0 011.5 0zM7.5 15.75a.75.75 0 100-1.5.75.75 0 000 1.5zM8.25 17.25a.75.75 0 11-1.5 0 .75.75 0 011.5 0zM9.75 15.75a.75.75 0 100-1.5.75.75 0 000 1.5zM10.5 17.25a.75.75 0 11-1.5 0 .75.75 0 011.5 0zM12 15.75a.75.75 0 100-1.5.75.75 0 000 1.5zM12.75 17.25a.75.75 0 11-1.5 0 .75.75 0 011.5 0zM14.25 15.75a.75.75 0 100-1.5.75.75 0 000 1.5zM15 17.25a.75.75 0 11-1.5 0 .75.75 0 011.5 0zM16.5 15.75a.75.75 0 100-1.5.75.75 0 000 1.5zM15 12.75a.75.75 0 11-1.5 0 .75.75 0 011.5 0zM16.5 13.5a.75.75 0 100-1.5.75.75 0 000 1.5z" /><path fill-rule="evenodd" d="M6.75 2.25A.75.75 0 017.5 3v1.5h9V3A.75.75 0 0118 3v1.5h.75a3 3 0 013 3v11.25a3 3 0 01-3 3H5.25a3 3 0 01-3-3V7.5a3 3 0 013-3H6V3a.75.75 0 01.75-.75zm13.5 9a1.5 1.5 0 00-1.5-1.5H5.25a1.5 1.5 0 00-1.5 1.5v7.5a1.5 1.5 0 001.5 1.5h13.5a1.5 1.5 0 001.5-1.5v-7.5z" clip-rule="evenodd" /></svg>'
      },
      { 
        text: 'Certificate of completion', 
        icon: '<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-6 h-6"><path fill-rule="evenodd" d="M7.502 6h7.128A3.375 3.375 0 0118 9.375v9.375a3 3 0 003-3V6.108c0-1.505-1.125-2.811-2.664-2.94a48.972 48.972 0 00-.673-.05A3 3 0 0015 1.5h-1.5a3 3 0 00-2.663 1.618c-.225.015-.45.032-.673.05C8.662 3.295 7.554 4.542 7.502 6zM13.5 3A1.5 1.5 0 0012 4.5h4.5A1.5 1.5 0 0015 3h-1.5z" clip-rule="evenodd" /><path fill-rule="evenodd" d="M3 9.375C3 8.339 3.84 7.5 4.875 7.5h9.75c1.036 0 1.875.84 1.875 1.875v11.25c0 1.035-.84 1.875-1.875 1.875h-9.75A1.875 1.875 0 013 20.625V9.375zM6 12a.75.75 0 01.75-.75h.008a.75.75 0 01.75.75v.008a.75.75 0 01-.75.75H6.75a.75.75 0 01-.75-.75V12zm2.25 0a.75.75 0 01.75-.75h3.75a.75.75 0 010 1.5H9a.75.75 0 01-.75-.75zM6 15a.75.75 0 01.75-.75h.008a.75.75 0 01.75.75v.008a.75.75 0 01-.75.75H6.75a.75.75 0 01-.75-.75V15zm2.25 0a.75.75 0 01.75-.75h3.75a.75.75 0 010 1.5H9a.75.75 0 01-.75-.75zM6 18a.75.75 0 01.75-.75h.008a.75.75 0 01.75.75v.008a.75.75 0 01-.75.75H6.75a.75.75 0 01-.75-.75V18zm2.25 0a.75.75 0 01.75-.75h3.75a.75.75 0 010 1.5H9a.75.75 0 01-.75-.75z" clip-rule="evenodd" /></svg>'
      }
    ],
    accessInfo: 'Full lifetime access on mobile and desktop',
    certificationInfo: 'Earn a certificate of completion after finishing all course materials'
  }
];

// Logic to find the selected course and similar courses
onMounted(() => {
  const allCourses = [
    ...courses,
    {
      id: 3,
      title: 'Digital Marketing Fundamentals',
      description: 'Learn the core concepts of digital marketing and grow your online presence.',
      image: 'https://images.pexels.com/photos/905163/pexels-photo-905163.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1',
      category: 'Marketing',
      rating: 4.7,
      price: 0,
      isPremium: false,
      instructor: {
        name: 'Michael Chen',
        avatar: 'https://images.pexels.com/photos/614810/pexels-photo-614810.jpeg?auto=compress&cs=tinysrgb&w=800'
      }
    }
  ];
  
  // Find the selected course
  const course = allCourses.find(c => c.id === courseId);
  if (course) {
    selectedCourse.value = {...courses.find(c => c.id === courseId)};
    
    // Set page title
    useHead({
      title: `${selectedCourse.value.title} | LearnHub`
    });
    
    // Find similar courses in the same category
    similarCourses.value = allCourses
      .filter(c => c.category === course.category && c.id !== courseId)
      .slice(0, 3);
  } else {
    // Handle course not found
    navigateTo('/courses');
  }
});

// Method to toggle curriculum sections
const toggleSection = (index) => {
  openSections.value[index] = !openSections.value[index];
};

// Computed property to access the selected course
const course = computed(() => {
  return selectedCourse.value || {
    title: 'Course not found',
    description: 'The requested course could not be found.',
    curriculum: [],
    features: [],
    learningOutcomes: [],
    requirements: [],
    descriptionFull: [],
    instructor: {
      name: '',
      avatar: '',
      title: '',
      bio: ''
    }
  };
});
</script>