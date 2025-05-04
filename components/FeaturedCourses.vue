<template>
  <section class="section bg-gray-50">
    <div class="container">
      <div class="mb-12 text-center">
        <h2 class="text-3xl md:text-4xl font-bold mb-4">Featured Courses</h2>
        <p class="text-gray-600 max-w-2xl mx-auto">Discover our most popular courses, hand-picked by our team and loved by thousands of students.</p>
      </div>
      
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8">
        <CourseCard v-for="course in featuredCourses" :key="course.id" :course="course" />
      </div>
      
      <div class="mt-12 text-center">
        <NuxtLink to="/courses" class="btn btn-primary">
          View All Courses
        </NuxtLink>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue';

const featuredCourses = ref([
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
    }
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
    }
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
    }
  }
]);
</script>