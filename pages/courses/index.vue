<template>
  <div>
    <!-- Courses Hero -->
    <section class="bg-primary-700 py-16">
      <div class="container">
        <div class="max-w-2xl mx-auto text-center text-white">
          <h1 class="text-4xl md:text-5xl font-bold mb-4">Browse All Courses</h1>
          <p class="text-primary-100 text-lg mb-8">Discover our extensive library of courses to help you achieve your learning goals.</p>
          
          <!-- Search bar -->
          <div class="relative max-w-lg mx-auto">
            <input 
              v-model="searchQuery"
              type="text" 
              placeholder="Search for courses..." 
              class="input pl-12 pr-4 text-gray-800 w-full"
              @input="filterCourses"
            />
            <div class="absolute inset-y-0 left-0 flex items-center pl-4 pointer-events-none">
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 text-gray-500">
                <path stroke-linecap="round" stroke-linejoin="round" d="M21 21l-5.197-5.197m0 0A7.5 7.5 0 105.196 5.196a7.5 7.5 0 0010.607 10.607z" />
              </svg>
            </div>
          </div>
        </div>
      </div>
    </section>
    
    <!-- Filters and Courses -->
    <section class="section bg-gray-50">
      <div class="container">
        <div class="grid grid-cols-1 lg:grid-cols-4 gap-8">
          <!-- Filters Sidebar -->
          <div class="lg:col-span-1">
            <div class="bg-white rounded-xl shadow-sm p-6">
              <h3 class="text-lg font-semibold mb-4">Filters</h3>
              
              <!-- Categories -->
              <div class="mb-6">
                <h4 class="font-medium mb-3 text-gray-700">Categories</h4>
                <div class="space-y-2">
                  <div v-for="category in categories" :key="category.slug" class="flex items-center">
                    <input 
                      :id="`category-${category.slug}`" 
                      type="checkbox"
                      :value="category.slug"
                      v-model="selectedCategories"
                      class="w-4 h-4 rounded text-primary-600 focus:ring-primary-500"
                      @change="filterCourses"
                    />
                    <label :for="`category-${category.slug}`" class="ml-2 text-gray-700">{{ category.name }}</label>
                  </div>
                </div>
              </div>
              
              <!-- Price Range -->
              <div class="mb-6">
                <h4 class="font-medium mb-3 text-gray-700">Price</h4>
                <div class="space-y-2">
                  <div class="flex items-center">
                    <input 
                      id="price-free" 
                      type="checkbox"
                      value="free"
                      v-model="selectedPrices"
                      class="w-4 h-4 rounded text-primary-600 focus:ring-primary-500"
                      @change="filterCourses"
                    />
                    <label for="price-free" class="ml-2 text-gray-700">Free</label>
                  </div>
                  <div class="flex items-center">
                    <input 
                      id="price-paid" 
                      type="checkbox"
                      value="paid"
                      v-model="selectedPrices"
                      class="w-4 h-4 rounded text-primary-600 focus:ring-primary-500"
                      @change="filterCourses"
                    />
                    <label for="price-paid" class="ml-2 text-gray-700">Premium</label>
                  </div>
                </div>
              </div>
              
              <!-- Rating Filter -->
              <div class="mb-6">
                <h4 class="font-medium mb-3 text-gray-700">Rating</h4>
                <div class="space-y-2">
                  <div v-for="rating in [4, 3, 2]" :key="rating" class="flex items-center">
                    <input 
                      :id="`rating-${rating}`" 
                      type="checkbox"
                      :value="rating"
                      v-model="selectedRatings"
                      class="w-4 h-4 rounded text-primary-600 focus:ring-primary-500"
                      @change="filterCourses"
                    />
                    <label :for="`rating-${rating}`" class="ml-2 flex items-center">
                      <span class="mr-1">{{ rating }}+</span>
                      <div class="flex text-yellow-400">
                        <svg v-for="i in 5" :key="i" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" 
                          :fill="i <= rating ? 'currentColor' : 'none'" 
                          :stroke="i <= rating ? 'none' : 'currentColor'"
                          class="w-4 h-4">
                          <path fill-rule="evenodd" d="M10.788 3.21c.448-1.077 1.976-1.077 2.424 0l2.082 5.006 5.404.434c1.164.093 1.636 1.545.749 2.305l-4.117 3.527 1.257 5.273c.271 1.136-.964 2.033-1.96 1.425L12 18.354 7.373 21.18c-.996.608-2.231-.29-1.96-1.425l1.257-5.273-4.117-3.527c-.887-.76-.415-2.212.749-2.305l5.404-.434 2.082-5.005Z" clip-rule="evenodd" />
                        </svg>
                      </div>
                    </label>
                  </div>
                </div>
              </div>
              
              <!-- Reset Filters -->
              <button @click="resetFilters" class="btn btn-secondary w-full">
                Reset Filters
              </button>
            </div>
          </div>
          
          <!-- Courses Grid -->
          <div class="lg:col-span-3">
            <!-- Sort options -->
            <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center mb-6">
              <p class="text-gray-700 mb-3 sm:mb-0">
                <span class="font-medium">{{ filteredCourses.length }}</span> courses found
              </p>
              <div class="flex items-center">
                <label for="sort" class="text-sm text-gray-600 mr-2">Sort by:</label>
                <select 
                  id="sort" 
                  v-model="sortOption"
                  @change="filterCourses"
                  class="bg-white border border-gray-300 text-gray-700 text-sm rounded-lg focus:ring-primary-500 focus:border-primary-500 p-2.5"
                >
                  <option value="popular">Most Popular</option>
                  <option value="newest">Newest</option>
                  <option value="price-low">Price: Low to High</option>
                  <option value="price-high">Price: High to Low</option>
                  <option value="rating">Highest Rated</option>
                </select>
              </div>
            </div>
            
            <!-- Course grid -->
            <div v-if="filteredCourses.length > 0" class="grid grid-cols-1 md:grid-cols-2 xl:grid-cols-3 gap-6">
              <CourseCard v-for="course in filteredCourses" :key="course.id" :course="course" />
            </div>
            
            <!-- No results -->
            <div v-else class="bg-white rounded-xl shadow-sm p-10 text-center">
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-16 h-16 mx-auto mb-4 text-gray-400">
                <path stroke-linecap="round" stroke-linejoin="round" d="M15.182 16.318A4.486 4.486 0 0012.016 15a4.486 4.486 0 00-3.198 1.318M21 12a9 9 0 11-18 0 9 9 0 0118 0zM9.75 9.75c0 .414-.168.75-.375.75S9 10.164 9 9.75 9.168 9 9.375 9s.375.336.375.75zm-.375 0h.008v.015h-.008V9.75zm5.625 0c0 .414-.168.75-.375.75s-.375-.336-.375-.75.168-.75.375-.75.375.336.375.75zm-.375 0h.008v.015h-.008V9.75z" />
              </svg>
              <h3 class="text-xl font-semibold mb-2">No courses found</h3>
              <p class="text-gray-600 mb-6">Try adjusting your filters or search query.</p>
              <button @click="resetFilters" class="btn btn-primary">
                Clear Filters
              </button>
            </div>
            
            <!-- Load more button -->
            <div v-if="filteredCourses.length > 0 && filteredCourses.length < courses.length" class="mt-10 text-center">
              <button @click="loadMoreCourses" class="btn btn-secondary">
                Load More Courses
              </button>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref, onMounted, computed } from 'vue';

useHead({
  title: 'Courses | LearnHub'
});

// Categories
const categories = ref([
  { name: 'Development', slug: 'development' },
  { name: 'Design', slug: 'design' },
  { name: 'Business', slug: 'business' },
  { name: 'Marketing', slug: 'marketing' },
  { name: 'Photography', slug: 'photography' },
  { name: 'Music', slug: 'music' }
]);

// Filter state
const searchQuery = ref('');
const selectedCategories = ref([]);
const selectedPrices = ref([]);
const selectedRatings = ref([]);
const sortOption = ref('popular');
const visibleCourseCount = ref(9);

// All courses
const courses = ref([
  {
    id: 1,
    title: 'Complete Web Development Bootcamp',
    description: 'Master HTML, CSS, JavaScript, React and Node.js with this comprehensive course.',
    image: 'https://images.pexels.com/photos/1181271/pexels-photo-1181271.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1',
    category: 'Development',
    rating: 4.9,
    price: 89.99,
    isPremium: true,
    instructor: {
      name: 'Alex Johnson',
      avatar: 'https://images.pexels.com/photos/220453/pexels-photo-220453.jpeg?auto=compress&cs=tinysrgb&w=800'
    },
    date: '2023-11-15'
  },
  {
    id: 2,
    title: 'UX/UI Design Masterclass',
    description: 'Learn to create stunning user interfaces and enhance user experience.',
    image: 'https://images.pexels.com/photos/196644/pexels-photo-196644.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1',
    category: 'Design',
    rating: 4.8,
    price: 79.99,
    isPremium: true,
    instructor: {
      name: 'Sarah Williams',
      avatar: 'https://images.pexels.com/photos/774909/pexels-photo-774909.jpeg?auto=compress&cs=tinysrgb&w=800'
    },
    date: '2023-10-20'
  },
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
    },
    date: '2023-09-05'
  },
  {
    id: 4,
    title: 'Responsive Web Design',
    description: 'Master the art of creating websites that work flawlessly across all devices.',
    image: 'https://images.pexels.com/photos/326502/pexels-photo-326502.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1',
    category: 'Development',
    rating: 4.5,
    price: 69.99,
    isPremium: true,
    instructor: {
      name: 'Emma Johnson',
      avatar: 'https://images.pexels.com/photos/3763188/pexels-photo-3763188.jpeg?auto=compress&cs=tinysrgb&w=800'
    },
    date: '2023-08-12'
  },
  {
    id: 5,
    title: 'Product Photography Essentials',
    description: 'Learn how to capture stunning product photos for e-commerce and marketing.',
    image: 'https://images.pexels.com/photos/1092671/pexels-photo-1092671.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1',
    category: 'Photography',
    rating: 4.6,
    price: 49.99,
    isPremium: true,
    instructor: {
      name: 'David Rodriguez',
      avatar: 'https://images.pexels.com/photos/2379005/pexels-photo-2379005.jpeg?auto=compress&cs=tinysrgb&w=800'
    },
    date: '2023-07-25'
  },
  {
    id: 6,
    title: 'Business Strategy Fundamentals',
    description: 'Develop strategic thinking skills and learn to create effective business plans.',
    image: 'https://images.pexels.com/photos/3183183/pexels-photo-3183183.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1',
    category: 'Business',
    rating: 4.3,
    price: 59.99,
    isPremium: true,
    instructor: {
      name: 'Jessica Lee',
      avatar: 'https://images.pexels.com/photos/1239291/pexels-photo-1239291.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1'
    },
    date: '2023-06-18'
  },
  {
    id: 7,
    title: 'HTML & CSS Crash Course',
    description: 'A beginner-friendly introduction to HTML and CSS for web development.',
    image: 'https://images.pexels.com/photos/270360/pexels-photo-270360.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1',
    category: 'Development',
    rating: 4.2,
    price: 0,
    isPremium: false,
    instructor: {
      name: 'John Smith',
      avatar: 'https://images.pexels.com/photos/614810/pexels-photo-614810.jpeg?auto=compress&cs=tinysrgb&w=800'
    },
    date: '2023-05-10'
  },
  {
    id: 8,
    title: 'Music Production for Beginners',
    description: 'Learn the basics of digital music production with industry-standard tools.',
    image: 'https://images.pexels.com/photos/164821/pexels-photo-164821.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1',
    category: 'Music',
    rating: 4.4,
    price: 69.99,
    isPremium: true,
    instructor: {
      name: 'Marcus Davis',
      avatar: 'https://images.pexels.com/photos/2406949/pexels-photo-2406949.jpeg?auto=compress&cs=tinysrgb&w=800'
    },
    date: '2023-04-22'
  },
  {
    id: 9,
    title: 'Social Media Marketing',
    description: 'Master social media platforms to grow your business and engage customers.',
    image: 'https://images.pexels.com/photos/267482/pexels-photo-267482.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1',
    category: 'Marketing',
    rating: 4.1,
    price: 49.99,
    isPremium: true,
    instructor: {
      name: 'Amanda Thompson',
      avatar: 'https://images.pexels.com/photos/1840608/pexels-photo-1840608.jpeg?auto=compress&cs=tinysrgb&w=800'
    },
    date: '2023-03-15'
  },
  {
    id: 10,
    title: 'JavaScript Fundamentals',
    description: 'Build a solid foundation in JavaScript programming for web development.',
    image: 'https://images.pexels.com/photos/574070/pexels-photo-574070.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1',
    category: 'Development',
    rating: 4.7,
    price: 0,
    isPremium: false,
    instructor: {
      name: 'Alex Johnson',
      avatar: 'https://images.pexels.com/photos/220453/pexels-photo-220453.jpeg?auto=compress&cs=tinysrgb&w=800'
    },
    date: '2023-02-28'
  },
  {
    id: 11,
    title: 'Graphic Design Principles',
    description: 'Learn the essential principles of graphic design for print and digital media.',
    image: 'https://images.pexels.com/photos/1762851/pexels-photo-1762851.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1',
    category: 'Design',
    rating: 4.5,
    price: 59.99,
    isPremium: true,
    instructor: {
      name: 'Sarah Williams',
      avatar: 'https://images.pexels.com/photos/774909/pexels-photo-774909.jpeg?auto=compress&cs=tinysrgb&w=800'
    },
    date: '2023-01-20'
  },
  {
    id: 12,
    title: 'Entrepreneurship Masterclass',
    description: 'Learn how to build, grow, and scale a successful business from scratch.',
    image: 'https://images.pexels.com/photos/3184292/pexels-photo-3184292.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1',
    category: 'Business',
    rating: 4.8,
    price: 89.99,
    isPremium: true,
    instructor: {
      name: 'Robert Johnson',
      avatar: 'https://images.pexels.com/photos/614810/pexels-photo-614810.jpeg?auto=compress&cs=tinysrgb&w=800'
    },
    date: '2022-12-15'
  }
]);

const filteredCourses = ref([]);

// Apply filters and sorting
const filterCourses = () => {
  let result = [...courses.value];
  
  // Apply search filter
  if (searchQuery.value) {
    const query = searchQuery.value.toLowerCase();
    result = result.filter(course => 
      course.title.toLowerCase().includes(query) || 
      course.description.toLowerCase().includes(query)
    );
  }
  
  // Apply category filter
  if (selectedCategories.value.length > 0) {
    result = result.filter(course => 
      selectedCategories.value.includes(course.category.toLowerCase())
    );
  }
  
  // Apply price filter
  if (selectedPrices.value.length > 0) {
    result = result.filter(course => {
      if (selectedPrices.value.includes('free') && course.price === 0) return true;
      if (selectedPrices.value.includes('paid') && course.price > 0) return true;
      return false;
    });
  }
  
  // Apply rating filter
  if (selectedRatings.value.length > 0) {
    result = result.filter(course => {
      return selectedRatings.value.some(rating => course.rating >= rating);
    });
  }
  
  // Apply sorting
  switch (sortOption.value) {
    case 'popular':
      result.sort((a, b) => b.rating - a.rating);
      break;
    case 'newest':
      result.sort((a, b) => new Date(b.date) - new Date(a.date));
      break;
    case 'price-low':
      result.sort((a, b) => a.price - b.price);
      break;
    case 'price-high':
      result.sort((a, b) => b.price - a.price);
      break;
    case 'rating':
      result.sort((a, b) => b.rating - a.rating);
      break;
  }
  
  filteredCourses.value = result.slice(0, visibleCourseCount.value);
};

// Load more courses
const loadMoreCourses = () => {
  visibleCourseCount.value += 6;
  filterCourses();
};

// Reset all filters
const resetFilters = () => {
  searchQuery.value = '';
  selectedCategories.value = [];
  selectedPrices.value = [];
  selectedRatings.value = [];
  sortOption.value = 'popular';
  visibleCourseCount.value = 9;
  filterCourses();
};

// Initialize
onMounted(() => {
  // Check if there's a category in the URL
  const route = useRoute();
  const categoryParam = route.query.category;
  
  if (categoryParam) {
    selectedCategories.value = [categoryParam];
  }
  
  filterCourses();
});
</script>