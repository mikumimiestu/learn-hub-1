<template>
  <div>
    <!-- Hero Section -->
    <section class="bg-gradient-to-br from-accent-900 to-accent-600 py-24">
      <div class="container">
        <div class="max-w-3xl mx-auto text-center">
          <span class="inline-block px-4 py-1 bg-accent-400/20 text-accent-100 rounded-full mb-4"
            v-motion="{ initial: { opacity: 0, y: -20 }, enter: { opacity: 1, y: 0 } }">
            Exclusive Premium Access
          </span>
          <h1 class="text-4xl md:text-5xl font-bold text-white mb-6 leading-tight"
            v-motion="{ initial: { opacity: 0 }, enter: { opacity: 1, transition: { delay: 200 } } }">
            Unlock the Full Potential of Your Learning Journey
          </h1>
          <p class="text-lg text-accent-100 mb-8 max-w-2xl mx-auto"
            v-motion="{ initial: { opacity: 0 }, enter: { opacity: 1, transition: { delay: 300 } } }">
            Join TNGDemy Premium to access our complete library of courses, receive personalized mentoring, 
            and earn recognized certificates to advance your career.
          </p>
          <div v-motion="{ initial: { opacity: 0, scale: 0.9 }, enter: { opacity: 1, scale: 1, transition: { delay: 400 } } }">
            <a href="#pricing" class="btn bg-white text-accent-700 hover:bg-accent-50">
              See Premium Plans
            </a>
          </div>
        </div>
      </div>
    </section>
    
    <!-- Features Section -->
    <section class="section bg-white">
      <div class="container">
        <div class="text-center mb-16">
          <h2 class="text-3xl md:text-4xl font-bold mb-4">Why Choose Premium?</h2>
          <p class="text-gray-600 max-w-2xl mx-auto">Discover the benefits that make TNGDemy Premium the preferred choice for serious learners.</p>
        </div>
        
        <div class="grid grid-cols-1 md:grid-cols-3 gap-10">
          <div class="text-center" v-motion="{ initial: { opacity: 0, y: 20 }, visible: { opacity: 1, y: 0 } }">
            <div class="bg-accent-100 w-20 h-20 rounded-full flex items-center justify-center mx-auto mb-5">
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-10 h-10 text-accent-600">
                <path stroke-linecap="round" stroke-linejoin="round" d="M12 6.042A8.967 8.967 0 006 3.75c-1.052 0-2.062.18-3 .512v14.25A8.987 8.987 0 016 18c2.305 0 4.408.867 6 2.292m0-14.25a8.966 8.966 0 016-2.292c1.052 0 2.062.18 3 .512v14.25A8.987 8.987 0 0018 18a8.967 8.967 0 00-6 2.292m0-14.25v14.25" />
              </svg>
            </div>
            <h3 class="text-xl font-semibold mb-3">Unlimited Course Access</h3>
            <p class="text-gray-600">Access our entire library of premium courses, covering the latest skills and technologies in high demand.</p>
          </div>
          
          <div class="text-center" v-motion="{ initial: { opacity: 0, y: 20 }, visible: { opacity: 1, y: 0, transition: { delay: 200 } } }">
            <div class="bg-primary-100 w-20 h-20 rounded-full flex items-center justify-center mx-auto mb-5">
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-10 h-10 text-primary-600">
                <path stroke-linecap="round" stroke-linejoin="round" d="M4.26 10.147a60.436 60.436 0 00-.491 6.347A48.627 48.627 0 0112 20.904a48.627 48.627 0 018.232-4.41 60.46 60.46 0 00-.491-6.347m-15.482 0a50.57 50.57 0 00-2.658-.813A59.905 59.905 0 0112 3.493a59.902 59.902 0 0110.399 5.84c-.896.248-1.783.52-2.658.814m-15.482 0A50.697 50.697 0 0112 13.489a50.702 50.702 0 017.74-3.342M6.75 15a.75.75 0 100-1.5.75.75 0 000 1.5zm0 0v-3.675A55.378 55.378 0 0112 8.443m-7.007 11.55A5.981 5.981 0 006.75 15.75v-1.5" />
              </svg>
            </div>
            <h3 class="text-xl font-semibold mb-3">Expert Mentorship</h3>
            <p class="text-gray-600">Connect with industry professionals who provide personalized guidance and feedback on your learning journey.</p>
          </div>
          
          <div class="text-center" v-motion="{ initial: { opacity: 0, y: 20 }, visible: { opacity: 1, y: 0, transition: { delay: 400 } } }">
            <div class="bg-secondary-100 w-20 h-20 rounded-full flex items-center justify-center mx-auto mb-5">
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-10 h-10 text-secondary-600">
                <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75L11.25 15 15 9.75M21 12c0 1.268-.63 2.39-1.593 3.068a3.745 3.745 0 01-1.043 3.296 3.745 3.745 0 01-3.296 1.043A3.745 3.745 0 0112 21c-1.268 0-2.39-.63-3.068-1.593a3.746 3.746 0 01-3.296-1.043 3.745 3.745 0 01-1.043-3.296A3.745 3.745 0 013 12c0-1.268.63-2.39 1.593-3.068a3.745 3.745 0 011.043-3.296 3.746 3.746 0 013.296-1.043A3.746 3.746 0 0112 3c1.268 0 2.39.63 3.068 1.593a3.746 3.746 0 013.296 1.043 3.746 3.746 0 011.043 3.296A3.745 3.745 0 0121 12z" />
              </svg>
            </div>
            <h3 class="text-xl font-semibold mb-3">Verified Certificates</h3>
            <p class="text-gray-600">Earn industry-recognized certificates upon course completion that validate your skills to employers.</p>
          </div>
        </div>
        
        <div class="grid grid-cols-1 md:grid-cols-2 gap-10 mt-16">
          <div class="bg-gray-50 rounded-xl overflow-hidden shadow-sm"
            v-motion="{ initial: { opacity: 0, x: -20 }, visible: { opacity: 1, x: 0 } }">
            <div class="p-8">
              <h3 class="text-2xl font-bold mb-4">More Premium Benefits</h3>
              <ul class="space-y-4">
                <li class="flex items-start">
                  <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6 text-green-500 mr-2 flex-shrink-0">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75L11.25 15 15 9.75M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                  </svg>
                  <span>Downloadable course materials and resources</span>
                </li>
                <li class="flex items-start">
                  <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6 text-green-500 mr-2 flex-shrink-0">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75L11.25 15 15 9.75M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                  </svg>
                  <span>Ad-free learning experience across all platforms</span>
                </li>
                <li class="flex items-start">
                  <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6 text-green-500 mr-2 flex-shrink-0">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75L11.25 15 15 9.75M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                  </svg>
                  <span>Priority customer support for all your questions</span>
                </li>
                <li class="flex items-start">
                  <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6 text-green-500 mr-2 flex-shrink-0">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75L11.25 15 15 9.75M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                  </svg>
                  <span>Live Q&A sessions with course instructors</span>
                </li>
                <li class="flex items-start">
                  <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6 text-green-500 mr-2 flex-shrink-0">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75L11.25 15 15 9.75M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                  </svg>
                  <span>Early access to new courses and updates</span>
                </li>
              </ul>
            </div>
          </div>
          
          <div class="bg-gray-50 rounded-xl overflow-hidden shadow-sm"
            v-motion="{ initial: { opacity: 0, x: 20 }, visible: { opacity: 1, x: 0 } }">
            <img src="https://images.pexels.com/photos/4145153/pexels-photo-4145153.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1" 
              alt="Premium learning" class="h-64 w-full object-cover">
            <div class="p-8">
              <h3 class="text-2xl font-bold mb-4">Premium Course Library</h3>
              <p class="text-gray-600 mb-4">Our premium course library includes specialized content in:</p>
              <div class="grid grid-cols-2 gap-2">
                <div class="bg-white p-3 rounded-lg shadow-sm text-center">
                  <span class="font-medium text-primary-700">Web Development</span>
                </div>
                <div class="bg-white p-3 rounded-lg shadow-sm text-center">
                  <span class="font-medium text-primary-700">UX/UI Design</span>
                </div>
                <div class="bg-white p-3 rounded-lg shadow-sm text-center">
                  <span class="font-medium text-primary-700">Data Science</span>
                </div>
                <div class="bg-white p-3 rounded-lg shadow-sm text-center">
                  <span class="font-medium text-primary-700">Machine Learning</span>
                </div>
                <div class="bg-white p-3 rounded-lg shadow-sm text-center">
                  <span class="font-medium text-primary-700">Digital Marketing</span>
                </div>
                <div class="bg-white p-3 rounded-lg shadow-sm text-center">
                  <span class="font-medium text-primary-700">Business Strategy</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
    
    <!-- Pricing Section -->
    <section id="pricing" class="section bg-gray-50">
      <div class="container">
        <div class="text-center mb-16">
          <h2 class="text-3xl md:text-4xl font-bold mb-4">Choose the Right Plan for You</h2>
          <p class="text-gray-600 max-w-2xl mx-auto">Select a plan that fits your learning goals and budget. All plans include our core premium features.</p>
        </div>
        
        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
          <!-- Monthly Plan -->
          <div class="bg-white rounded-xl shadow-lg overflow-hidden border border-gray-200 transition-transform duration-300 hover:scale-105"
            v-motion="{ initial: { opacity: 0, y: 20 }, visible: { opacity: 1, y: 0 } }">
            <div class="p-8">
              <h3 class="text-xl font-bold mb-2">Monthly Plan</h3>
              <p class="text-gray-600 mb-6">Perfect for short-term learning goals</p>
              <div class="mb-6">
                <span class="text-4xl font-bold">$14.99</span>
                <span class="text-gray-600">/month</span>
              </div>
              <ul class="space-y-3 mb-8">
                <li class="flex items-center">
                  <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 text-green-500 mr-2">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75L11.25 15 15 9.75M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                  </svg>
                  <span>Access to all premium courses</span>
                </li>
                <li class="flex items-center">
                  <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 text-green-500 mr-2">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75L11.25 15 15 9.75M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                  </svg>
                  <span>Course completion certificates</span>
                </li>
                <li class="flex items-center">
                  <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 text-green-500 mr-2">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75L11.25 15 15 9.75M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                  </svg>
                  <span>Downloadable resources</span>
                </li>
                <li class="flex items-center text-gray-400">
                  <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 mr-2">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
                  </svg>
                  <span>1-on-1 mentoring sessions</span>
                </li>
                <li class="flex items-center text-gray-400">
                  <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 mr-2">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
                  </svg>
                  <span>Career guidance sessions</span>
                </li>
              </ul>
              <NuxtLink to="/payment" class="btn btn-primary w-full">Get Started</NuxtLink>
            </div>
          </div>
          
          <!-- Annual Plan (Best Value) -->
          <div class="bg-white rounded-xl shadow-xl overflow-hidden border-2 border-accent-500 relative transform scale-105 z-10"
            v-motion="{ initial: { opacity: 0, y: 20 }, visible: { opacity: 1, y: 0, transition: { delay: 200 } } }">
            <div class="absolute top-0 left-0 right-0 bg-accent-500 text-white text-center py-2 font-medium">
              Most Popular
            </div>
            <div class="p-8 pt-14">
              <h3 class="text-xl font-bold mb-2">Annual Plan</h3>
              <p class="text-gray-600 mb-6">Best value for serious learners</p>
              <div class="mb-6">
                <span class="text-4xl font-bold">$9.99</span>
                <span class="text-gray-600">/month</span>
                <span class="ml-2 text-sm text-accent-700 font-medium">Save 33%</span>
              </div>
              <ul class="space-y-3 mb-8">
                <li class="flex items-center">
                  <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 text-green-500 mr-2">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75L11.25 15 15 9.75M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                  </svg>
                  <span>Access to all premium courses</span>
                </li>
                <li class="flex items-center">
                  <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 text-green-500 mr-2">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75L11.25 15 15 9.75M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                  </svg>
                  <span>Course completion certificates</span>
                </li>
                <li class="flex items-center">
                  <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 text-green-500 mr-2">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75L11.25 15 15 9.75M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                  </svg>
                  <span>Downloadable resources</span>
                </li>
                <li class="flex items-center">
                  <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 text-green-500 mr-2">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75L11.25 15 15 9.75M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                  </svg>
                  <span>Monthly group mentoring session</span>
                </li>
                <li class="flex items-center text-gray-400">
                  <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 mr-2">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
                  </svg>
                  <span>Career guidance sessions</span>
                </li>
              </ul>
              <NuxtLink to="/payment" class="btn bg-accent-600 hover:bg-accent-700 text-white w-full">Get Started</NuxtLink>
              <p class="text-center text-sm text-gray-500 mt-4">Billed annually at $119.88</p>
            </div>
          </div>
          
          <!-- Premium Plan -->
          <div class="bg-white rounded-xl shadow-lg overflow-hidden border border-gray-200 transition-transform duration-300 hover:scale-105"
            v-motion="{ initial: { opacity: 0, y: 20 }, visible: { opacity: 1, y: 0, transition: { delay: 400 } } }">
            <div class="p-8">
              <h3 class="text-xl font-bold mb-2">Premium Plan</h3>
              <p class="text-gray-600 mb-6">For career advancement & mastery</p>
              <div class="mb-6">
                <span class="text-4xl font-bold">$19.99</span>
                <span class="text-gray-600">/month</span>
              </div>
              <ul class="space-y-3 mb-8">
                <li class="flex items-center">
                  <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 text-green-500 mr-2">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75L11.25 15 15 9.75M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                  </svg>
                  <span>Access to all premium courses</span>
                </li>
                <li class="flex items-center">
                  <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 text-green-500 mr-2">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75L11.25 15 15 9.75M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                  </svg>
                  <span>Course completion certificates</span>
                </li>
                <li class="flex items-center">
                  <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 text-green-500 mr-2">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75L11.25 15 15 9.75M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                  </svg>
                  <span>Downloadable resources</span>
                </li>
                <li class="flex items-center">
                  <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 text-green-500 mr-2">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75L11.25 15 15 9.75M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                  </svg>
                  <span>Monthly 1-on-1 mentoring session</span>
                </li>
                <li class="flex items-center">
                  <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 text-green-500 mr-2">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75L11.25 15 15 9.75M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                  </svg>
                  <span>Career guidance & resume review</span>
                </li>
              </ul>
              <NuxtLink to="/payment" class="btn btn-primary w-full">Get Started</NuxtLink>
            </div>
          </div>
        </div>
        
        <div class="mt-12 text-center">
          <p class="text-gray-600 mb-2">All plans include a 7-day free trial. Cancel anytime.</p>
          <p class="text-gray-500 text-sm">By subscribing, you agree to our Terms of Service and Privacy Policy.</p>
        </div>
      </div>
    </section>
    
    <!-- Testimonials -->
    <section class="section bg-white">
      <div class="container">
        <div class="text-center mb-16">
          <h2 class="text-3xl md:text-4xl font-bold mb-4">What Our Premium Members Say</h2>
          <p class="text-gray-600 max-w-2xl mx-auto">Hear from our community of premium learners who have transformed their careers.</p>
        </div>
        
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          <div class="bg-gray-50 rounded-xl p-8 shadow-sm"
            v-motion="{ initial: { opacity: 0, y: 20 }, visible: { opacity: 1, y: 0 } }">
            <div class="flex mb-4 text-yellow-400">
              <svg v-for="i in 5" :key="i" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-5 h-5">
                <path fill-rule="evenodd" d="M10.788 3.21c.448-1.077 1.976-1.077 2.424 0l2.082 5.006 5.404.434c1.164.093 1.636 1.545.749 2.305l-4.117 3.527 1.257 5.273c.271 1.136-.964 2.033-1.96 1.425L12 18.354 7.373 21.18c-.996.608-2.231-.29-1.96-1.425l1.257-5.273-4.117-3.527c-.887-.76-.415-2.212.749-2.305l5.404-.434 2.082-5.005Z" clip-rule="evenodd" />
              </svg>
            </div>
            <blockquote class="text-gray-700 italic mb-6">
              "The premium membership was a game-changer for my career. The 1-on-1 mentoring sessions helped me navigate challenges in my projects, and the certificate from the Advanced React course helped me land my dream job."
            </blockquote>
            <div class="flex items-center">
              <img src="https://images.pexels.com/photos/220453/pexels-photo-220453.jpeg?auto=compress&cs=tinysrgb&w=800" alt="Member" class="w-12 h-12 rounded-full mr-4">
              <div>
                <div class="font-semibold">David Chen</div>
                <div class="text-sm text-gray-500">Frontend Developer</div>
              </div>
            </div>
          </div>
          
          <div class="bg-gray-50 rounded-xl p-8 shadow-sm"
            v-motion="{ initial: { opacity: 0, y: 20 }, visible: { opacity: 1, y: 0, transition: { delay: 200 } } }">
            <div class="flex mb-4 text-yellow-400">
              <svg v-for="i in 5" :key="i" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-5 h-5">
                <path fill-rule="evenodd" d="M10.788 3.21c.448-1.077 1.976-1.077 2.424 0l2.082 5.006 5.404.434c1.164.093 1.636 1.545.749 2.305l-4.117 3.527 1.257 5.273c.271 1.136-.964 2.033-1.96 1.425L12 18.354 7.373 21.18c-.996.608-2.231-.29-1.96-1.425l1.257-5.273-4.117-3.527c-.887-.76-.415-2.212.749-2.305l5.404-.434 2.082-5.005Z" clip-rule="evenodd" />
              </svg>
            </div>
            <blockquote class="text-gray-700 italic mb-6">
              "I was skeptical about paying for courses, but TNGDemy Premium exceeded my expectations. The quality of content, instructor support, and additional resources are worth every penny. I've completed 5 courses in 3 months!"
            </blockquote>
            <div class="flex items-center">
              <img src="https://images.pexels.com/photos/774909/pexels-photo-774909.jpeg?auto=compress&cs=tinysrgb&w=800" alt="Member" class="w-12 h-12 rounded-full mr-4">
              <div>
                <div class="font-semibold">Jessica Wang</div>
                <div class="text-sm text-gray-500">Product Manager</div>
              </div>
            </div>
          </div>
          
          <div class="bg-gray-50 rounded-xl p-8 shadow-sm"
            v-motion="{ initial: { opacity: 0, y: 20 }, visible: { opacity: 1, y: 0, transition: { delay: 400 } } }">
            <div class="flex mb-4 text-yellow-400">
              <svg v-for="i in 5" :key="i" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-5 h-5">
                <path fill-rule="evenodd" d="M10.788 3.21c.448-1.077 1.976-1.077 2.424 0l2.082 5.006 5.404.434c1.164.093 1.636 1.545.749 2.305l-4.117 3.527 1.257 5.273c.271 1.136-.964 2.033-1.96 1.425L12 18.354 7.373 21.18c-.996.608-2.231-.29-1.96-1.425l1.257-5.273-4.117-3.527c-.887-.76-.415-2.212.749-2.305l5.404-.434 2.082-5.005Z" clip-rule="evenodd" />
              </svg>
            </div>
            <blockquote class="text-gray-700 italic mb-6">
              "The career guidance session helped me pivot from marketing to UX design. My mentor provided a roadmap and recommended specific courses that aligned with my goals. Within 6 months, I secured my first UX role!"
            </blockquote>
            <div class="flex items-center">
              <img src="https://images.pexels.com/photos/2379005/pexels-photo-2379005.jpeg?auto=compress&cs=tinysrgb&w=800" alt="Member" class="w-12 h-12 rounded-full mr-4">
              <div>
                <div class="font-semibold">Michael Rodriguez</div>
                <div class="text-sm text-gray-500">UX Designer</div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
    
    <!-- FAQ Section -->
    <section class="section bg-gray-50">
      <div class="container">
        <div class="text-center mb-16">
          <h2 class="text-3xl md:text-4xl font-bold mb-4">Frequently Asked Questions</h2>
          <p class="text-gray-600 max-w-2xl mx-auto">Find answers to common questions about our premium membership.</p>
        </div>
        
        <div class="max-w-3xl mx-auto">
          <div v-for="(faq, index) in faqs" :key="index" 
            class="mb-4 border border-gray-200 rounded-lg overflow-hidden">
            <button 
              @click="toggleFaq(index)"
              class="flex justify-between items-center w-full p-6 text-left bg-white hover:bg-gray-50 transition-colors"
            >
              <span class="font-semibold text-lg">{{ faq.question }}</span>
              <svg 
                xmlns="http://www.w3.org/2000/svg" 
                fill="none" 
                viewBox="0 0 24 24" 
                stroke-width="1.5" 
                stroke="currentColor" 
                class="w-5 h-5 transition-transform duration-200"
                :class="{ 'rotate-180': faq.open }"
              >
                <path stroke-linecap="round" stroke-linejoin="round" d="M19.5 8.25l-7.5 7.5-7.5-7.5" />
              </svg>
            </button>
            <div 
              v-show="faq.open" 
              class="px-6 pb-6 text-gray-700"
            >
              <p>{{ faq.answer }}</p>
            </div>
          </div>
        </div>
      </div>
    </section>
    
    <!-- CTA Section -->
    <section class="bg-accent-700 py-16">
      <div class="container">
        <div class="max-w-3xl mx-auto text-center">
          <h2 class="text-3xl md:text-4xl font-bold text-white mb-6">Start Your Premium Journey Today</h2>
          <p class="text-accent-100 text-lg mb-8">
            Join thousands of learners who have transformed their careers with TNGDemy Premium.
          </p>
          <div>
            <NuxtLink to="/payment" class="btn bg-white text-accent-700 hover:bg-accent-50">
              Get Started with Premium
            </NuxtLink>
            <p class="text-accent-200 mt-4">7-day free trial, cancel anytime</p>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref } from 'vue';

useHead({
  title: 'Premium Membership | TNGDemy',
});

const faqs = ref([
  {
    question: "What's included in the premium membership?",
    answer: "Premium membership gives you unlimited access to all courses in our library, downloadable resources, completion certificates, mentoring sessions (depending on plan), and career guidance support.",
    open: true
  },
  {
    question: "Can I cancel my subscription at any time?",
    answer: "Yes, you can cancel your subscription at any time. If you cancel during your free trial period, you won't be charged. If you cancel after the trial period or during a paid subscription, you'll have access until the end of your billing period.",
    open: false
  },
  {
    question: "How do the mentoring sessions work?",
    answer: "Depending on your plan, you'll have access to group or 1-on-1 mentoring sessions with industry experts. These sessions are conducted via video call and can be scheduled through your dashboard. You can discuss course materials, get feedback on projects, or receive career advice.",
    open: false
  },
  {
    question: "Are the certificates recognized by employers?",
    answer: "Our certificates are well-respected in the industry and recognized by many employers. They verify that you've completed a comprehensive course and demonstrated proficiency in the subject matter. Many of our premium members have used our certificates to enhance their resumes and secure new jobs.",
    open: false
  },
  {
    question: "What if I'm not satisfied with the premium content?",
    answer: "We offer a 30-day money-back guarantee for all premium subscriptions. If you're not satisfied with the content or service, you can request a full refund within the first 30 days of your paid subscription.",
    open: false
  },
  {
    question: "Can I switch between subscription plans?",
    answer: "Yes, you can upgrade or downgrade your subscription plan at any time. If you upgrade, the new rate will be applied immediately. If you downgrade, the new rate will be applied at the start of your next billing cycle.",
    open: false
  }
]);

// Method to toggle FAQ items
const toggleFaq = (index) => {
  faqs.value[index].open = !faqs.value[index].open;
};
</script>