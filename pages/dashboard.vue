<template>
  <div>
    <section class="bg-gray-50 py-16">
      <div class="container">
        <div class="grid grid-cols-1 lg:grid-cols-4 gap-8">
          <!-- Sidebar -->
          <div class="lg:col-span-1">
            <div class="bg-white rounded-xl shadow-sm overflow-hidden sticky top-24">
              <div class="p-6 border-b border-gray-200">
                <div class="flex items-center">
                  <img src="https://images.pexels.com/photos/220453/pexels-photo-220453.jpeg?auto=compress&cs=tinysrgb&w=800" 
                    alt="User Avatar" class="w-12 h-12 rounded-full mr-4">
                  <div>
                    <h3 class="font-semibold">John Smith</h3>
                    <span class="text-sm text-gray-600">Premium Member</span>
                  </div>
                </div>
              </div>
              <nav class="p-2">
                <button 
                  v-for="item in navItems" 
                  :key="item.id"
                  @click="activeTab = item.id"
                  class="w-full flex items-center p-3 rounded-lg transition-colors text-left mb-1"
                  :class="activeTab === item.id ? 'bg-primary-50 text-primary-700' : 'text-gray-700 hover:bg-gray-50'"
                >
                  <span class="mr-3" v-html="item.icon"></span>
                  <span>{{ item.name }}</span>
                </button>
              </nav>
              <div class="p-6 border-t border-gray-200">
                <NuxtLink to="/" class="flex items-center text-gray-700 hover:text-primary-700 transition-colors">
                  <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 mr-2">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M15.75 9V5.25A2.25 2.25 0 0013.5 3h-6a2.25 2.25 0 00-2.25 2.25v13.5A2.25 2.25 0 007.5 21h6a2.25 2.25 0 002.25-2.25V15M12 9l-3 3m0 0l3 3m-3-3h12.75" />
                  </svg>
                  <span>Logout</span>
                </NuxtLink>
              </div>
            </div>
          </div>
          
          <!-- Main Content -->
          <div class="lg:col-span-3">
            <!-- My Courses Tab -->
            <div v-if="activeTab === 'courses'" class="space-y-8">
              <div class="flex justify-between items-center">
                <h1 class="text-2xl md:text-3xl font-bold">My Courses</h1>
                <div class="flex">
                  <label for="course-filter" class="sr-only">Filter Courses</label>
                  <select 
                    id="course-filter" 
                    v-model="courseFilter"
                    class="bg-white border border-gray-300 text-gray-700 text-sm rounded-lg focus:ring-primary-500 focus:border-primary-500 p-2.5"
                  >
                    <option value="all">All Courses</option>
                    <option value="in-progress">In Progress</option>
                    <option value="completed">Completed</option>
                  </select>
                </div>
              </div>
              
              <!-- In Progress Courses -->
              <div>
                <h2 class="text-xl font-semibold mb-4">In Progress</h2>
                <div class="grid grid-cols-1 gap-6">
                  <div v-for="course in inProgressCourses" :key="course.id" 
                    class="bg-white rounded-xl shadow-sm overflow-hidden border border-gray-200 transition-transform hover:shadow-md"
                    v-motion="{ initial: { opacity: 0, y: 20 }, visible: { opacity: 1, y: 0 } }">
                    <div class="flex flex-col md:flex-row">
                      <div class="md:w-1/4">
                        <img :src="course.image" :alt="course.title" class="h-48 md:h-full w-full object-cover">
                      </div>
                      <div class="p-6 md:w-3/4 flex flex-col">
                        <div class="flex-grow">
                          <div class="flex justify-between items-start mb-2">
                            <h3 class="text-lg font-semibold">{{ course.title }}</h3>
                            <span v-if="course.isPremium" class="badge badge-premium">Premium</span>
                          </div>
                          <p class="text-gray-600 text-sm mb-4">{{ course.description }}</p>
                          <div class="mb-4">
                            <div class="flex justify-between mb-1 text-sm">
                              <span>Progress</span>
                              <span>{{ course.progress }}%</span>
                            </div>
                            <div class="w-full bg-gray-200 rounded-full h-2">
                              <div class="bg-primary-600 h-2 rounded-full" :style="{ width: `${course.progress}%` }"></div>
                            </div>
                          </div>
                          <div class="text-sm text-gray-600 mb-4">
                            <span>Last accessed: {{ course.lastAccessed }}</span>
                          </div>
                        </div>
                        <div class="mt-auto pt-4 border-t border-gray-100 flex flex-col sm:flex-row sm:justify-between">
                          <div class="flex items-center">
                            <img :src="course.instructor.avatar" :alt="course.instructor.name" class="w-8 h-8 rounded-full mr-2">
                            <span class="text-sm">{{ course.instructor.name }}</span>
                          </div>
                          <NuxtLink :to="`/courses/${course.id}`" class="btn btn-primary py-2 mt-3 sm:mt-0">
                            Continue Learning
                          </NuxtLink>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
              
              <!-- Completed Courses -->
              <div v-if="completedCourses.length > 0">
                <h2 class="text-xl font-semibold mb-4">Completed</h2>
                <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                  <div v-for="course in completedCourses" :key="course.id" 
                    class="bg-white rounded-xl shadow-sm overflow-hidden border border-gray-200 transition-transform hover:shadow-md"
                    v-motion="{ initial: { opacity: 0, y: 20 }, visible: { opacity: 1, y: 0 } }">
                    <div class="relative">
                      <img :src="course.image" :alt="course.title" class="w-full h-40 object-cover">
                      <div class="absolute top-0 right-0 bg-green-600 text-white text-xs py-1 px-2 rounded-bl-lg">
                        Completed
                      </div>
                    </div>
                    <div class="p-5">
                      <h3 class="text-lg font-semibold mb-2">{{ course.title }}</h3>
                      <div class="flex justify-between items-center mb-4">
                        <span class="badge bg-gray-100 text-gray-800">{{ course.category }}</span>
                        <div class="flex items-center">
                          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-5 h-5 mr-1 text-yellow-500">
                            <path fill-rule="evenodd" d="M10.788 3.21c.448-1.077 1.976-1.077 2.424 0l2.082 5.006 5.404.434c1.164.093 1.636 1.545.749 2.305l-4.117 3.527 1.257 5.273c.271 1.136-.964 2.033-1.96 1.425L12 18.354 7.373 21.18c-.996.608-2.231-.29-1.96-1.425l1.257-5.273-4.117-3.527c-.887-.76-.415-2.212.749-2.305l5.404-.434 2.082-5.005Z" clip-rule="evenodd" />
                          </svg>
                          <span>{{ course.rating }}</span>
                        </div>
                      </div>
                      <div class="flex items-center justify-between mt-4 pt-4 border-t border-gray-100">
                        <div class="flex items-center">
                          <img :src="course.instructor.avatar" :alt="course.instructor.name" class="w-6 h-6 rounded-full mr-2">
                          <span class="text-xs text-gray-600">{{ course.instructor.name }}</span>
                        </div>
                        <NuxtLink :to="`/courses/${course.id}`" class="text-primary-600 hover:text-primary-700 text-sm font-medium">
                          Review
                        </NuxtLink>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
              
              <!-- Course Recommendations -->
              <div>
                <h2 class="text-xl font-semibold mb-4">Recommended For You</h2>
                <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                  <div v-for="course in recommendedCourses" :key="course.id" 
                    class="bg-white rounded-xl shadow-sm overflow-hidden border border-gray-200 transition-transform hover:shadow-md"
                    v-motion="{ initial: { opacity: 0, y: 20 }, visible: { opacity: 1, y: 0 } }">
                    <img :src="course.image" :alt="course.title" class="w-full h-40 object-cover">
                    <div class="p-5">
                      <div class="flex justify-between items-start mb-2">
                        <span class="badge bg-gray-100 text-gray-800">{{ course.category }}</span>
                        <span v-if="course.isPremium" class="badge badge-premium">Premium</span>
                      </div>
                      <h3 class="text-lg font-semibold mb-2">{{ course.title }}</h3>
                      <p class="text-gray-600 text-sm mb-4 line-clamp-2">{{ course.description }}</p>
                      <div class="flex justify-between items-center mt-4 pt-4 border-t border-gray-100">
                        <div class="flex items-center">
                          <img :src="course.instructor.avatar" :alt="course.instructor.name" class="w-6 h-6 rounded-full mr-2">
                          <span class="text-xs text-gray-600">{{ course.instructor.name }}</span>
                        </div>
                        <NuxtLink :to="`/courses/${course.id}`" class="text-primary-600 hover:text-primary-700 text-sm font-medium">
                          View Course
                        </NuxtLink>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
            
            <!-- Certificates Tab -->
            <div v-if="activeTab === 'certificates'" class="space-y-8">
              <h1 class="text-2xl md:text-3xl font-bold">My Certificates</h1>
              
              <div class="bg-white rounded-xl shadow-sm overflow-hidden p-6">
                <div v-if="certificates.length > 0">
                  <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                    <div v-for="certificate in certificates" :key="certificate.id" 
                      class="border border-gray-200 rounded-lg overflow-hidden hover:shadow-md transition-shadow"
                      v-motion="{ initial: { opacity: 0, y: 20 }, visible: { opacity: 1, y: 0 } }">
                      <div class="p-5 border-b border-gray-200 bg-gray-50">
                        <h3 class="font-semibold">{{ certificate.course }}</h3>
                        <p class="text-sm text-gray-600">Completed on {{ certificate.completedDate }}</p>
                      </div>
                      <div class="p-5">
                        <p class="mb-4 text-sm text-gray-700">This certificate verifies that <span class="font-medium">John Smith</span> successfully completed the course.</p>
                        <div class="flex flex-col sm:flex-row justify-between items-center space-y-3 sm:space-y-0">
                          <div class="text-sm text-gray-600">
                            Certificate ID: {{ certificate.id }}
                          </div>
                          <div class="flex space-x-2">
                            <button class="btn btn-secondary py-1.5 px-3">
                              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-4 h-4 mr-1">
                                <path stroke-linecap="round" stroke-linejoin="round" d="M9 8.25H7.5a2.25 2.25 0 00-2.25 2.25v9a2.25 2.25 0 002.25 2.25h9a2.25 2.25 0 002.25-2.25v-9a2.25 2.25 0 00-2.25-2.25H15m0-3l-3-3m0 0l-3 3m3-3V15" />
                              </svg>
                              Download
                            </button>
                            <button class="btn bg-accent-600 hover:bg-accent-700 text-white py-1.5 px-3">
                              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-4 h-4 mr-1">
                                <path stroke-linecap="round" stroke-linejoin="round" d="M7.217 10.907a2.25 2.25 0 100 2.186m0-2.186c.18.324.283.696.283 1.093s-.103.77-.283 1.093m0-2.186l9.566-5.314m-9.566 7.5l9.566 5.314m0 0a2.25 2.25 0 103.935 2.186 2.25 2.25 0 00-3.935-2.186zm0-12.814a2.25 2.25 0 103.933-2.185 2.25 2.25 0 00-3.933 2.185z" />
                              </svg>
                              Share
                            </button>
                          </div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div v-else class="text-center py-12">
                  <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-16 h-16 mx-auto text-gray-400 mb-4">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M19.5 14.25v-2.625a3.375 3.375 0 00-3.375-3.375h-1.5A1.125 1.125 0 0113.5 7.125v-1.5a3.375 3.375 0 00-3.375-3.375H8.25m0 12.75h7.5m-7.5 3H12M10.5 2.25H5.625c-.621 0-1.125.504-1.125 1.125v17.25c0 .621.504 1.125 1.125 1.125h12.75c.621 0 1.125-.504 1.125-1.125V11.25a9 9 0 00-9-9z" />
                  </svg>
                  <h3 class="text-lg font-semibold mb-1">No Certificates Yet</h3>
                  <p class="text-gray-600 mb-4">Complete courses to earn certificates</p>
                  <NuxtLink to="/courses" class="btn btn-primary">
                    Browse Courses
                  </NuxtLink>
                </div>
              </div>
            </div>
            
            <!-- Profile Tab -->
            <div v-if="activeTab === 'profile'" class="space-y-8">
              <h1 class="text-2xl md:text-3xl font-bold">My Profile</h1>
              
              <div class="bg-white rounded-xl shadow-sm overflow-hidden">
                <div class="bg-primary-700 h-32 relative">
                  <div class="absolute -bottom-12 left-8">
                    <div class="relative">
                      <img src="https://images.pexels.com/photos/220453/pexels-photo-220453.jpeg?auto=compress&cs=tinysrgb&w=800" 
                        alt="User Avatar" class="w-24 h-24 rounded-full border-4 border-white">
                      <button class="absolute bottom-0 right-0 bg-primary-600 text-white p-1 rounded-full">
                        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-4 h-4">
                          <path stroke-linecap="round" stroke-linejoin="round" d="M6.827 6.175A2.31 2.31 0 015.186 7.23c-.38.054-.757.112-1.134.175C2.999 7.58 2.25 8.507 2.25 9.574V18a2.25 2.25 0 002.25 2.25h15A2.25 2.25 0 0021.75 18V9.574c0-1.067-.75-1.994-1.802-2.169a47.865 47.865 0 00-1.134-.175 2.31 2.31 0 01-1.64-1.055l-.822-1.316a2.192 2.192 0 00-1.736-1.039 48.774 48.774 0 00-5.232 0 2.192 2.192 0 00-1.736 1.039l-.821 1.316z" />
                          <path stroke-linecap="round" stroke-linejoin="round" d="M16.5 12.75a4.5 4.5 0 11-9 0 4.5 4.5 0 019 0zM18.75 10.5h.008v.008h-.008V10.5z" />
                        </svg>
                      </button>
                    </div>
                  </div>
                </div>
                
                <div class="pt-16 pb-8 px-8">
                  <div class="mb-8">
                    <h2 class="text-xl font-semibold mb-4">Personal Information</h2>
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                      <div>
                        <label for="profile-first-name" class="form-label">First Name</label>
                        <input type="text" id="profile-first-name" class="input" value="John" placeholder="First Name">
                      </div>
                      <div>
                        <label for="profile-last-name" class="form-label">Last Name</label>
                        <input type="text" id="profile-last-name" class="input" value="Smith" placeholder="Last Name">
                      </div>
                      <div>
                        <label for="profile-email" class="form-label">Email Address</label>
                        <input type="email" id="profile-email" class="input" value="john.smith@example.com" placeholder="Email Address">
                      </div>
                      <div>
                        <label for="profile-phone" class="form-label">Phone Number</label>
                        <input type="tel" id="profile-phone" class="input" value="+1 (555) 123-4567" placeholder="Phone Number">
                      </div>
                    </div>
                  </div>
                  
                  <div class="mb-8">
                    <h2 class="text-xl font-semibold mb-4">Profile Information</h2>
                    <div class="space-y-6">
                      <div>
                        <label for="profile-bio" class="form-label">Bio</label>
                        <textarea id="profile-bio" rows="4" class="input" placeholder="Tell us about yourself">Web developer focused on front-end technologies. Currently learning React and Vue.js to expand my skillset.</textarea>
                      </div>
                      <div>
                        <label for="profile-job" class="form-label">Job Title</label>
                        <input type="text" id="profile-job" class="input" value="Frontend Developer" placeholder="Job Title">
                      </div>
                      <div>
                        <label class="form-label">Areas of Interest</label>
                        <div class="mt-2 flex flex-wrap gap-2">
                          <div class="flex items-center">
                            <input type="checkbox" id="interest-webdev" class="w-4 h-4 text-primary-600 rounded focus:ring-primary-500" checked>
                            <label for="interest-webdev" class="ml-2 text-sm text-gray-700">Web Development</label>
                          </div>
                          <div class="flex items-center">
                            <input type="checkbox" id="interest-design" class="w-4 h-4 text-primary-600 rounded focus:ring-primary-500" checked>
                            <label for="interest-design" class="ml-2 text-sm text-gray-700">UX/UI Design</label>
                          </div>
                          <div class="flex items-center">
                            <input type="checkbox" id="interest-mobile" class="w-4 h-4 text-primary-600 rounded focus:ring-primary-500">
                            <label for="interest-mobile" class="ml-2 text-sm text-gray-700">Mobile Development</label>
                          </div>
                          <div class="flex items-center">
                            <input type="checkbox" id="interest-data" class="w-4 h-4 text-primary-600 rounded focus:ring-primary-500">
                            <label for="interest-data" class="ml-2 text-sm text-gray-700">Data Science</label>
                          </div>
                        </div>
                      </div>
                    </div>
                  </div>
                  
                  <div>
                    <h2 class="text-xl font-semibold mb-4">Account Settings</h2>
                    <div class="space-y-6">
                      <div>
                        <label for="profile-password" class="form-label">Change Password</label>
                        <input type="password" id="profile-password" class="input" placeholder="New Password">
                      </div>
                      <div>
                        <label for="profile-password-confirm" class="form-label">Confirm Password</label>
                        <input type="password" id="profile-password-confirm" class="input" placeholder="Confirm New Password">
                      </div>
                      <div>
                        <label class="form-label">Notification Preferences</label>
                        <div class="mt-2 space-y-2">
                          <div class="flex items-center justify-between">
                            <label for="notify-course-updates" class="text-sm text-gray-700">Course updates</label>
                            <div class="relative inline-block w-10 mr-2 align-middle select-none">
                              <input type="checkbox" id="notify-course-updates" class="sr-only peer" checked>
                              <div class="w-10 h-5 bg-gray-300 rounded-full peer peer-checked:bg-primary-600"></div>
                              <div class="absolute w-4 h-4 bg-white rounded-full left-0.5 top-0.5 peer-checked:left-5 transition-all duration-200"></div>
                            </div>
                          </div>
                          <div class="flex items-center justify-between">
                            <label for="notify-promotions" class="text-sm text-gray-700">Promotions and offers</label>
                            <div class="relative inline-block w-10 mr-2 align-middle select-none">
                              <input type="checkbox" id="notify-promotions" class="sr-only peer" checked>
                              <div class="w-10 h-5 bg-gray-300 rounded-full peer peer-checked:bg-primary-600"></div>
                              <div class="absolute w-4 h-4 bg-white rounded-full left-0.5 top-0.5 peer-checked:left-5 transition-all duration-200"></div>
                            </div>
                          </div>
                        </div>
                      </div>
                    </div>
                  </div>
                  
                  <div class="mt-8 pt-6 border-t border-gray-200 flex justify-end">
                    <button class="btn btn-primary">Save Changes</button>
                  </div>
                </div>
              </div>
            </div>
            
            <!-- Settings Tab -->
            <div v-if="activeTab === 'settings'" class="space-y-8">
              <h1 class="text-2xl md:text-3xl font-bold">Settings</h1>
              
              <div class="bg-white rounded-xl shadow-sm overflow-hidden p-6">
                <!-- Account Settings -->
                <div class="mb-8">
                  <h2 class="text-xl font-semibold mb-4">Account Settings</h2>
                  <div class="space-y-6">
                    <div>
                      <label for="settings-email" class="form-label">Email Address</label>
                      <input type="email" id="settings-email" class="input" value="john.smith@example.com">
                    </div>
                    <div class="flex justify-between items-center py-3 border-t border-b border-gray-200">
                      <div>
                        <h3 class="font-medium">Premium Membership</h3>
                        <p class="text-sm text-gray-600">You are currently on the Annual Premium plan</p>
                      </div>
                      <button class="btn btn-secondary py-2">Manage Subscription</button>
                    </div>
                    <div class="flex justify-between items-center">
                      <div>
                        <h3 class="font-medium">Delete Account</h3>
                        <p class="text-sm text-gray-600">Permanently delete your account and all data</p>
                      </div>
                      <button class="btn bg-red-600 hover:bg-red-700 text-white py-2">Delete Account</button>
                    </div>
                  </div>
                </div>
                
                <!-- Notification Settings -->
                <div class="mb-8">
                  <h2 class="text-xl font-semibold mb-4">Notification Settings</h2>
                  <div class="space-y-4">
                    <div class="flex items-center justify-between">
                      <div>
                        <h3 class="font-medium">Email Notifications</h3>
                        <p class="text-sm text-gray-600">Receive course updates and new content alerts</p>
                      </div>
                      <div class="relative inline-block w-10 mr-2 align-middle select-none">
                        <input type="checkbox" id="settings-email-notifications" class="sr-only peer" checked>
                        <div class="w-10 h-5 bg-gray-300 rounded-full peer peer-checked:bg-primary-600"></div>
                        <div class="absolute w-4 h-4 bg-white rounded-full left-0.5 top-0.5 peer-checked:left-5 transition-all duration-200"></div>
                      </div>
                    </div>
                    <div class="flex items-center justify-between">
                      <div>
                        <h3 class="font-medium">SMS Notifications</h3>
                        <p class="text-sm text-gray-600">Receive text messages for important updates</p>
                      </div>
                      <div class="relative inline-block w-10 mr-2 align-middle select-none">
                        <input type="checkbox" id="settings-sms-notifications" class="sr-only peer">
                        <div class="w-10 h-5 bg-gray-300 rounded-full peer peer-checked:bg-primary-600"></div>
                        <div class="absolute w-4 h-4 bg-white rounded-full left-0.5 top-0.5 peer-checked:left-5 transition-all duration-200"></div>
                      </div>
                    </div>
                    <div class="flex items-center justify-between">
                      <div>
                        <h3 class="font-medium">Marketing Communications</h3>
                        <p class="text-sm text-gray-600">Receive promotional offers and news</p>
                      </div>
                      <div class="relative inline-block w-10 mr-2 align-middle select-none">
                        <input type="checkbox" id="settings-marketing" class="sr-only peer" checked>
                        <div class="w-10 h-5 bg-gray-300 rounded-full peer peer-checked:bg-primary-600"></div>
                        <div class="absolute w-4 h-4 bg-white rounded-full left-0.5 top-0.5 peer-checked:left-5 transition-all duration-200"></div>
                      </div>
                    </div>
                  </div>
                </div>
                
                <!-- Privacy Settings -->
                <div>
                  <h2 class="text-xl font-semibold mb-4">Privacy Settings</h2>
                  <div class="space-y-4">
                    <div class="flex items-center justify-between">
                      <div>
                        <h3 class="font-medium">Profile Visibility</h3>
                        <p class="text-sm text-gray-600">Allow other students to see your profile</p>
                      </div>
                      <div class="relative inline-block w-10 mr-2 align-middle select-none">
                        <input type="checkbox" id="settings-profile-visibility" class="sr-only peer" checked>
                        <div class="w-10 h-5 bg-gray-300 rounded-full peer peer-checked:bg-primary-600"></div>
                        <div class="absolute w-4 h-4 bg-white rounded-full left-0.5 top-0.5 peer-checked:left-5 transition-all duration-200"></div>
                      </div>
                    </div>
                    <div class="flex items-center justify-between">
                      <div>
                        <h3 class="font-medium">Course Progress Sharing</h3>
                        <p class="text-sm text-gray-600">Share your course progress on the platform</p>
                      </div>
                      <div class="relative inline-block w-10 mr-2 align-middle select-none">
                        <input type="checkbox" id="settings-progress-sharing" class="sr-only peer">
                        <div class="w-10 h-5 bg-gray-300 rounded-full peer peer-checked:bg-primary-600"></div>
                        <div class="absolute w-4 h-4 bg-white rounded-full left-0.5 top-0.5 peer-checked:left-5 transition-all duration-200"></div>
                      </div>
                    </div>
                    <div class="flex items-center justify-between">
                      <div>
                        <h3 class="font-medium">Data Collection</h3>
                        <p class="text-sm text-gray-600">Allow us to collect usage data to improve services</p>
                      </div>
                      <div class="relative inline-block w-10 mr-2 align-middle select-none">
                        <input type="checkbox" id="settings-data-collection" class="sr-only peer" checked>
                        <div class="w-10 h-5 bg-gray-300 rounded-full peer peer-checked:bg-primary-600"></div>
                        <div class="absolute w-4 h-4 bg-white rounded-full left-0.5 top-0.5 peer-checked:left-5 transition-all duration-200"></div>
                      </div>
                    </div>
                  </div>
                </div>
                
                <div class="mt-8 pt-6 border-t border-gray-200 flex justify-end">
                  <button class="btn btn-primary">Save Changes</button>
                </div>
              </div>
            </div>
            
            <!-- Help Tab -->
            <div v-if="activeTab === 'help'" class="space-y-8">
              <h1 class="text-2xl md:text-3xl font-bold">Help & Support</h1>
              
              <div class="bg-white rounded-xl shadow-sm overflow-hidden p-6">
                <div class="mb-8">
                  <h2 class="text-xl font-semibold mb-4">Frequently Asked Questions</h2>
                  <div class="space-y-4">
                    <div v-for="(faq, index) in helpFaqs" :key="index" class="border border-gray-200 rounded-lg overflow-hidden">
                      <button 
                        @click="faq.open = !faq.open"
                        class="w-full flex justify-between items-center p-4 text-left hover:bg-gray-50 transition-colors"
                      >
                        <span class="font-medium">{{ faq.question }}</span>
                        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" 
                          class="w-5 h-5 transition-transform" :class="{ 'rotate-180': faq.open }">
                          <path stroke-linecap="round" stroke-linejoin="round" d="M19.5 8.25l-7.5 7.5-7.5-7.5" />
                        </svg>
                      </button>
                      <div v-if="faq.open" class="px-4 pb-4">
                        <p class="text-gray-700">{{ faq.answer }}</p>
                      </div>
                    </div>
                  </div>
                </div>
                
                <div class="mb-8">
                  <h2 class="text-xl font-semibold mb-4">Contact Support</h2>
                  <div class="space-y-6">
                    <div>
                      <label for="support-subject" class="form-label">Subject</label>
                      <input type="text" id="support-subject" class="input" placeholder="What do you need help with?">
                    </div>
                    <div>
                      <label for="support-message" class="form-label">Message</label>
                      <textarea id="support-message" rows="4" class="input" placeholder="Describe your issue in detail"></textarea>
                    </div>
                    <div>
                      <button class="btn btn-primary">Submit Ticket</button>
                    </div>
                  </div>
                </div>
                
                <div>
                  <h2 class="text-xl font-semibold mb-4">Alternative Ways to Get Support</h2>
                  <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                    <a href="#" class="flex items-center p-4 border border-gray-200 rounded-lg hover:border-primary-500 transition-colors">
                      <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6 text-primary-600 mr-3">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M2.25 6.75c0 8.284 6.716 15 15 15h2.25a2.25 2.25 0 002.25-2.25v-1.372c0-.516-.351-.966-.852-1.091l-4.423-1.106c-.44-.11-.902.055-1.173.417l-.97 1.293c-.282.376-.769.542-1.21.38a12.035 12.035 0 01-7.143-7.143c-.162-.441.004-.928.38-1.21l1.293-.97c.363-.271.527-.734.417-1.173L6.963 3.102a1.125 1.125 0 00-1.091-.852H4.5A2.25 2.25 0 002.25 4.5v2.25z" />
                      </svg>
                      <div>
                        <h3 class="font-medium">Phone Support</h3>
                        <p class="text-sm text-gray-600">Call us at +1 (555) 123-4567</p>
                      </div>
                    </a>
                    <a href="#" class="flex items-center p-4 border border-gray-200 rounded-lg hover:border-primary-500 transition-colors">
                      <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6 text-primary-600 mr-3">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M7.5 8.25h9m-9 3H12m-9.75 1.51c0 1.6 1.123 2.994 2.707 3.227 1.129.166 2.27.293 3.423.379.35.026.67.21.865.501L12 21l2.755-4.133a1.14 1.14 0 01.865-.501 48.172 48.172 0 003.423-.379c1.584-.233 2.707-1.626 2.707-3.228V6.741c0-1.602-1.123-2.995-2.707-3.228A48.394 48.394 0 0012 3c-2.392 0-4.744.175-7.043.513C3.373 3.746 2.25 5.14 2.25 6.741v6.018z" />
                      </svg>
                      <div>
                        <h3 class="font-medium">Live Chat</h3>
                        <p class="text-sm text-gray-600">Chat with our support team</p>
                      </div>
                    </a>
                    <a href="#" class="flex items-center p-4 border border-gray-200 rounded-lg hover:border-primary-500 transition-colors">
                      <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6 text-primary-600 mr-3">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M15.75 17.25v3.375c0 .621-.504 1.125-1.125 1.125h-9.75a1.125 1.125 0 01-1.125-1.125V7.875c0-.621.504-1.125 1.125-1.125H6.75a9.06 9.06 0 011.5.124m7.5 10.376h3.375c.621 0 1.125-.504 1.125-1.125V11.25c0-4.46-3.243-8.161-7.5-8.876a9.06 9.06 0 00-1.5-.124H9.375c-.621 0-1.125.504-1.125 1.125v3.5m7.5 10.375H9.375a1.125 1.125 0 01-1.125-1.125v-9.25m12 6.625v-1.875a3.375 3.375 0 00-3.375-3.375h-1.5a1.125 1.125 0 01-1.125-1.125v-1.5a3.375 3.375 0 00-3.375-3.375H9.75" />
                      </svg>
                      <div>
                        <h3 class="font-medium">Knowledge Base</h3>
                        <p class="text-sm text-gray-600">Browse our help articles</p>
                      </div>
                    </a>
                    <a href="#" class="flex items-center p-4 border border-gray-200 rounded-lg hover:border-primary-500 transition-colors">
                      <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6 text-primary-600 mr-3">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M18 18.72a9.094 9.094 0 003.741-.479 3 3 0 00-4.682-2.72m.94 3.198l.001.031c0 .225-.012.447-.037.666A11.944 11.944 0 0112 21c-2.17 0-4.207-.576-5.963-1.584A6.062 6.062 0 016 18.719m12 0a5.971 5.971 0 00-.941-3.197m0 0A5.995 5.995 0 0012 12.75a5.995 5.995 0 00-5.058 2.772m0 0a3 3 0 00-4.681 2.72 8.986 8.986 0 003.74.477m.94-3.197a5.971 5.971 0 00-.94 3.197M15 6.75a3 3 0 11-6 0 3 3 0 016 0zm6 3a2.25 2.25 0 11-4.5 0 2.25 2.25 0 014.5 0zm-13.5 0a2.25 2.25 0 11-4.5 0 2.25 2.25 0 014.5 0z" />
                      </svg>
                      <div>
                        <h3 class="font-medium">Community Forum</h3>
                        <p class="text-sm text-gray-600">Connect with other students</p>
                      </div>
                    </a>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';

useHead({
  title: 'Dashboard | LearnHub'
});

const activeTab = ref('courses');
const courseFilter = ref('all');

const navItems = [
  {
    id: 'courses',
    name: 'My Courses',
    icon: '<svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5"><path stroke-linecap="round" stroke-linejoin="round" d="M12 6.042A8.967 8.967 0 006 3.75c-1.052 0-2.062.18-3 .512v14.25A8.987 8.987 0 016 18c2.305 0 4.408.867 6 2.292m0-14.25a8.966 8.966 0 016-2.292c1.052 0 2.062.18 3 .512v14.25A8.987 8.987 0 0018 18a8.967 8.967 0 00-6 2.292m0-14.25v14.25" /></svg>'
  },
  {
    id: 'certificates',
    name: 'Certificates',
    icon: '<svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5"><path stroke-linecap="round" stroke-linejoin="round" d="M11.48 3.499a.562.562 0 011.04 0l2.125 5.111a.563.563 0 00.475.345l5.518.442c.499.04.701.663.321.988l-4.204 3.602a.563.563 0 00-.182.557l1.285 5.385a.562.562 0 01-.84.61l-4.725-2.885a.563.563 0 00-.586 0L6.982 20.54a.562.562 0 01-.84-.61l1.285-5.386a.562.562 0 00-.182-.557l-4.204-3.602a.563.563 0 01.321-.988l5.518-.442a.563.563 0 00.475-.345L11.48 3.5z" /></svg>'
  },
  {
    id: 'profile',
    name: 'Profile',
    icon: '<svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5"><path stroke-linecap="round" stroke-linejoin="round" d="M15.75 6a3.75 3.75 0 11-7.5 0 3.75 3.75 0 017.5 0zM4.501 20.118a7.5 7.5 0 0114.998 0A17.933 17.933 0 0112 21.75c-2.676 0-5.216-.584-7.499-1.632z" /></svg>'
  },
  {
    id: 'settings',
    name: 'Settings',
    icon: '<svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5"><path stroke-linecap="round" stroke-linejoin="round" d="M9.594 3.94c.09-.542.56-.94 1.11-.94h2.593c.55 0 1.02.398 1.11.94l.213 1.281c.063.374.313.686.645.87.074.04.147.083.22.127.324.196.72.257 1.075.124l1.217-.456a1.125 1.125 0 011.37.49l1.296 2.247a1.125 1.125 0 01-.26 1.431l-1.003.827c-.293.24-.438.613-.431.992a6.759 6.759 0 010 .255c-.007.378.138.75.43.99l1.005.828c.424.35.534.954.26 1.43l-1.298 2.247a1.125 1.125 0 01-1.369.491l-1.217-.456c-.355-.133-.75-.072-1.076.124a6.57 6.57 0 01-.22.128c-.331.183-.581.495-.644.869l-.213 1.28c-.09.543-.56.941-1.11.941h-2.594c-.55 0-1.02-.398-1.11-.94l-.213-1.281c-.062-.374-.312-.686-.644-.87a6.52 6.52 0 01-.22-.127c-.325-.196-.72-.257-1.076-.124l-1.217.456a1.125 1.125 0 01-1.369-.49l-1.297-2.247a1.125 1.125 0 01.26-1.431l1.004-.827c.292-.24.437-.613.43-.992a6.932 6.932 0 010-.255c.007-.378-.138-.75-.43-.99l-1.004-.828a1.125 1.125 0 01-.26-1.43l1.297-2.247a1.125 1.125 0 011.37-.491l1.216.456c.356.133.751.072 1.076-.124.072-.044.146-.087.22-.128.332-.183.582-.495.644-.869l.214-1.281z" /><path stroke-linecap="round" stroke-linejoin="round" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z" /></svg>'
  },
  {
    id: 'help',
    name: 'Help & Support',
    icon: '<svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5"><path stroke-linecap="round" stroke-linejoin="round" d="M9.879 7.519c1.171-1.025 3.071-1.025 4.242 0 1.172 1.025 1.172 2.687 0 3.712-.203.179-.43.326-.67.442-.745.361-1.45.999-1.45 1.827v.75M21 12a9 9 0 11-18 0 9 9 0 0118 0zm-9 5.25h.008v.008H12v-.008z" /></svg>'
  }
];

// Certificates data
const certificates = ref([
  {
    id: 'CERT-12345',
    course: 'Complete Web Development Bootcamp',
    completedDate: 'June 15, 2023'
  },
  {
    id: 'CERT-67890',
    course: 'UX/UI Design Masterclass',
    completedDate: 'August 22, 2023'
  }
]);

// Help FAQs
const helpFaqs = ref([
  {
    question: 'How do I access my course materials?',
    answer: 'You can access your course materials by navigating to "My Courses" in your dashboard and clicking on the course you want to view. All course content, including videos, downloadable resources, and assignments, will be available there.',
    open: true
  },
  {
    question: 'How do I download my certificate?',
    answer: 'To download your certificate, go to the "Certificates" section in your dashboard. Find the certificate you want to download and click the "Download" button. You can save it as a PDF file or print it directly.',
    open: false
  },
  {
    question: 'How can I change my payment method?',
    answer: 'You can change your payment method by going to the "Settings" tab, then selecting "Account Settings". Under the "Premium Membership" section, click on "Manage Subscription" and you will be able to update your payment details.',
    open: false
  },
  {
    question: 'What happens when my subscription expires?',
    answer: 'When your subscription expires, you will lose access to premium courses and features. Your account will revert to a free membership, but you will still have access to any free courses you have enrolled in. You can renew your subscription at any time.',
    open: false
  }
]);

// Courses data
const allCourses = ref([
  {
    id: 1,
    title: 'Complete Web Development Bootcamp',
    description: 'A comprehensive guide to modern web development, covering HTML, CSS, JavaScript, React, and Node.js.',
    image: 'https://images.pexels.com/photos/1181271/pexels-photo-1181271.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1',
    category: 'Development',
    rating: 4.9,
    progress: 75,
    lastAccessed: 'Today',
    status: 'in-progress',
    isPremium: true,
    instructor: {
      name: 'Alex Johnson',
      avatar: 'https://images.pexels.com/photos/220453/pexels-photo-220453.jpeg?auto=compress&cs=tinysrgb&w=800'
    }
  },
  {
    id: 2,
    title: 'UX/UI Design Masterclass',
    description: 'Learn to create stunning user interfaces and enhance user experience with modern design principles.',
    image: 'https://images.pexels.com/photos/196644/pexels-photo-196644.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1',
    category: 'Design',
    rating: 4.8,
    progress: 100,
    lastAccessed: '2 days ago',
    status: 'completed',
    isPremium: true,
    instructor: {
      name: 'Sarah Williams',
      avatar: 'https://images.pexels.com/photos/774909/pexels-photo-774909.jpeg?auto=compress&cs=tinysrgb&w=800'
    }
  },
  {
    id: 3,
    title: 'Digital Marketing Fundamentals',
    description: 'Learn the core concepts of digital marketing and grow your online presence effectively.',
    image: 'https://images.pexels.com/photos/905163/pexels-photo-905163.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1',
    category: 'Marketing',
    rating: 4.7,
    progress: 35,
    lastAccessed: 'Yesterday',
    status: 'in-progress',
    isPremium: false,
    instructor: {
      name: 'Michael Chen',
      avatar: 'https://images.pexels.com/photos/614810/pexels-photo-614810.jpeg?auto=compress&cs=tinysrgb&w=800'
    }
  },
  {
    id: 4,
    title: 'JavaScript for Beginners',
    description: 'A solid foundation in JavaScript programming for web development.',
    image: 'https://images.pexels.com/photos/574070/pexels-photo-574070.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1',
    category: 'Development',
    rating: 4.6,
    progress: 100,
    lastAccessed: '1 week ago',
    status: 'completed',
    isPremium: false,
    instructor: {
      name: 'John Smith',
      avatar: 'https://images.pexels.com/photos/2379004/pexels-photo-2379004.jpeg?auto=compress&cs=tinysrgb&w=800'
    }
  }
]);

// Filter courses based on status
const inProgressCourses = computed(() => {
  return allCourses.value.filter(course => course.status === 'in-progress');
});

const completedCourses = computed(() => {
  return allCourses.value.filter(course => course.status === 'completed');
});

// Recommended courses (different from enrolled courses)
const recommendedCourses = ref([
  {
    id: 5,
    title: 'Advanced React Patterns',
    description: 'Master advanced React patterns and build scalable applications.',
    image: 'https://images.pexels.com/photos/11035380/pexels-photo-11035380.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1',
    category: 'Development',
    rating: 4.9,
    isPremium: true,
    instructor: {
      name: 'Alex Johnson',
      avatar: 'https://images.pexels.com/photos/220453/pexels-photo-220453.jpeg?auto=compress&cs=tinysrgb&w=800'
    }
  },
  {
    id: 6,
    title: 'Data Science Fundamentals',
    description: 'Learn the basics of data science, statistics, and machine learning.',
    image: 'https://images.pexels.com/photos/577585/pexels-photo-577585.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1',
    category: 'Data Science',
    rating: 4.8,
    isPremium: true,
    instructor: {
      name: 'Emma Watson',
      avatar: 'https://images.pexels.com/photos/1239291/pexels-photo-1239291.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1'
    }
  },
  {
    id: 7,
    title: 'Mobile App Development with Flutter',
    description: 'Build cross-platform mobile apps with Flutter and Dart.',
    image: 'https://images.pexels.com/photos/1092644/pexels-photo-1092644.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1',
    category: 'Development',
    rating: 4.7,
    isPremium: true,
    instructor: {
      name: 'Robert Chen',
      avatar: 'https://images.pexels.com/photos/2379005/pexels-photo-2379005.jpeg?auto=compress&cs=tinysrgb&w=800'
    }
  }
]);
</script>