<template>
  <div>
    <section class="bg-gray-50 py-16">
      <div class="container max-w-4xl">
        <div class="mb-8 text-center">
          <h1 class="text-3xl md:text-4xl font-bold mb-3">Complete Your Purchase</h1>
          <p class="text-gray-600">You're just one step away from unlocking premium content</p>
        </div>
        
        <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
          <!-- Payment Form -->
          <div class="lg:col-span-2">
            <div class="bg-white rounded-xl shadow-sm overflow-hidden">
              <!-- Payment Steps -->
              <div class="flex border-b border-gray-200">
                <button 
                  @click="paymentStep = 'information'" 
                  class="flex-1 py-4 px-6 text-center font-medium"
                  :class="paymentStep === 'information' ? 'text-primary-700 border-b-2 border-primary-500' : 'text-gray-500'"
                >
                  Information
                </button>
                <button 
                  @click="paymentStep = 'payment'" 
                  class="flex-1 py-4 px-6 text-center font-medium"
                  :class="paymentStep === 'payment' ? 'text-primary-700 border-b-2 border-primary-500' : 'text-gray-500'"
                >
                  Payment
                </button>
                <button 
                  @click="paymentStep = 'confirmation'" 
                  class="flex-1 py-4 px-6 text-center font-medium"
                  :class="paymentStep === 'confirmation' ? 'text-primary-700 border-b-2 border-primary-500' : 'text-gray-500'"
                >
                  Confirmation
                </button>
              </div>
              
              <!-- Information Step -->
              <div v-if="paymentStep === 'information'" class="p-6" v-motion="{ initial: { opacity: 0 }, enter: { opacity: 1 } }">
                <h2 class="text-xl font-semibold mb-6">Personal Information</h2>
                
                <div class="space-y-4">
                  <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                    <div>
                      <label for="first-name" class="form-label">First Name</label>
                      <input type="text" id="first-name" v-model="formData.firstName" class="input" placeholder="Enter your first name">
                    </div>
                    <div>
                      <label for="last-name" class="form-label">Last Name</label>
                      <input type="text" id="last-name" v-model="formData.lastName" class="input" placeholder="Enter your last name">
                    </div>
                  </div>
                  
                  <div>
                    <label for="email" class="form-label">Email Address</label>
                    <input type="email" id="email" v-model="formData.email" class="input" placeholder="Enter your email address">
                  </div>
                  
                  <div>
                    <label for="phone" class="form-label">Phone Number (for WhatsApp confirmation)</label>
                    <input type="tel" id="phone" v-model="formData.phone" class="input" placeholder="Enter your phone number">
                  </div>
                </div>
                
                <div class="mt-8">
                  <button @click="paymentStep = 'payment'" class="btn btn-primary w-full">Continue to Payment</button>
                </div>
              </div>
              
              <!-- Payment Step -->
              <div v-if="paymentStep === 'payment'" class="p-6" v-motion="{ initial: { opacity: 0 }, enter: { opacity: 1 } }">
                <h2 class="text-xl font-semibold mb-6">Payment Details</h2>
                
                <div class="mb-6">
                  <div class="flex justify-between mb-2">
                    <label class="form-label">Payment Method</label>
                  </div>
                  <div class="grid grid-cols-4 gap-3">
                    <div 
                      v-for="method in paymentMethods" 
                      :key="method.id"
                      @click="formData.paymentMethod = method.id"
                      class="border rounded-lg p-3 flex items-center justify-center cursor-pointer transition-colors"
                      :class="formData.paymentMethod === method.id ? 'border-primary-500 bg-primary-50' : 'border-gray-200 hover:border-gray-300'"
                    >
                      <img :src="method.image" :alt="method.name" class="h-8 object-contain">
                    </div>
                  </div>
                </div>
                
                <div class="space-y-4">
                  <div>
                    <label for="card-number" class="form-label">Card Number</label>
                    <input type="text" id="card-number" v-model="formData.cardNumber" class="input" placeholder="0000 0000 0000 0000">
                  </div>
                  
                  <div class="grid grid-cols-2 gap-4">
                    <div>
                      <label for="expiry" class="form-label">Expiry Date</label>
                      <input type="text" id="expiry" v-model="formData.expiry" class="input" placeholder="MM/YY">
                    </div>
                    <div>
                      <label for="cvv" class="form-label">Security Code</label>
                      <input type="text" id="cvv" v-model="formData.cvv" class="input" placeholder="CVV">
                    </div>
                  </div>
                  
                  <div>
                    <label for="name-on-card" class="form-label">Name on Card</label>
                    <input type="text" id="name-on-card" v-model="formData.nameOnCard" class="input" placeholder="Enter the name on your card">
                  </div>
                </div>
                
                <div class="flex items-center mt-6">
                  <input type="checkbox" id="save-card" v-model="formData.saveCard" class="w-4 h-4 text-primary-600 rounded focus:ring-primary-500">
                  <label for="save-card" class="ml-2 text-sm text-gray-700">Save this card for future purchases</label>
                </div>
                
                <div class="mt-8 flex flex-col sm:flex-row space-y-3 sm:space-y-0 sm:space-x-3">
                  <button @click="paymentStep = 'information'" class="btn btn-secondary flex-1">
                    <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 mr-1">
                      <path stroke-linecap="round" stroke-linejoin="round" d="M15.75 19.5L8.25 12l7.5-7.5" />
                    </svg>
                    Back
                  </button>
                  <button @click="processPayment" class="btn btn-primary flex-1">
                    Complete Payment
                  </button>
                </div>
                
                <div class="mt-6 text-center text-sm text-gray-500">
                  <p>Your payment information is securely processed</p>
                  <div class="flex justify-center mt-2 space-x-3">
                    <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 text-gray-400">
                      <path stroke-linecap="round" stroke-linejoin="round" d="M16.5 10.5V6.75a4.5 4.5 0 10-9 0v3.75m-.75 11.25h10.5a2.25 2.25 0 002.25-2.25v-6.75a2.25 2.25 0 00-2.25-2.25H6.75a2.25 2.25 0 00-2.25 2.25v6.75a2.25 2.25 0 002.25 2.25z" />
                    </svg>
                    <span>Secure SSL Encryption</span>
                  </div>
                </div>
              </div>
              
              <!-- Confirmation Step -->
              <div v-if="paymentStep === 'confirmation'" class="p-6 text-center" v-motion="{ initial: { opacity: 0 }, enter: { opacity: 1 } }">
                <div class="mb-6">
                  <div class="w-20 h-20 bg-green-100 rounded-full mx-auto flex items-center justify-center">
                    <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-10 h-10 text-green-600">
                      <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75L11.25 15 15 9.75M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                    </svg>
                  </div>
                </div>
                
                <h2 class="text-2xl font-bold mb-2">Payment Successful!</h2>
                <p class="text-gray-600 mb-6">Your payment has been processed successfully.</p>
                
                <div class="bg-gray-50 rounded-lg p-4 mb-6 text-left">
                  <h3 class="font-semibold mb-2">Order Summary</h3>
                  <div class="flex justify-between mb-1">
                    <span>Annual Premium Plan</span>
                    <span>$119.88</span>
                  </div>
                  <div class="flex justify-between text-sm text-gray-500 mb-3">
                    <span>Billed annually</span>
                    <span>($9.99/month)</span>
                  </div>
                  <div class="border-t border-gray-200 pt-2 flex justify-between font-semibold">
                    <span>Total</span>
                    <span>$119.88</span>
                  </div>
                </div>
                
                <div class="bg-green-50 rounded-lg p-4 mb-6 text-left border border-green-200">
                  <div class="flex">
                    <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6 text-green-600 mr-2 flex-shrink-0">
                      <path stroke-linecap="round" stroke-linejoin="round" d="M7.5 8.25h9m-9 3H12m-9.75 1.51c0 1.6 1.123 2.994 2.707 3.227 1.129.166 2.27.293 3.423.379.35.026.67.21.865.501L12 21l2.755-4.133a1.14 1.14 0 01.865-.501 48.172 48.172 0 003.423-.379c1.584-.233 2.707-1.626 2.707-3.228V6.741c0-1.602-1.123-2.995-2.707-3.228A48.394 48.394 0 0012 3c-2.392 0-4.744.175-7.043.513C3.373 3.746 2.25 5.14 2.25 6.741v6.018z" />
                    </svg>
                    <div>
                      <h3 class="font-semibold text-green-800 mb-1">WhatsApp Confirmation</h3>
                      <p class="text-green-700 text-sm">You will receive a confirmation message on WhatsApp at {{ formData.phone }}</p>
                    </div>
                  </div>
                </div>
                
                <div class="mt-8">
                  <NuxtLink to="/dashboard" class="btn btn-primary">
                    Go to Your Dashboard
                  </NuxtLink>
                </div>
                
                <p class="mt-6 text-sm text-gray-500">
                  A receipt has been sent to {{ formData.email }}
                </p>
              </div>
            </div>
          </div>
          
          <!-- Order Summary -->
          <div class="lg:col-span-1">
            <div class="bg-white rounded-xl shadow-sm overflow-hidden sticky top-24">
              <div class="p-6">
                <h2 class="text-xl font-semibold mb-4">Order Summary</h2>
                
                <div class="flex items-center mb-6 pb-6 border-b border-gray-200">
                  <div class="bg-accent-100 w-16 h-16 rounded-lg flex items-center justify-center flex-shrink-0 mr-4">
                    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-8 h-8 text-accent-600">
                      <path fill-rule="evenodd" d="M10.788 3.21c.448-1.077 1.976-1.077 2.424 0l2.082 5.006 5.404.434c1.164.093 1.636 1.545.749 2.305l-4.117 3.527 1.257 5.273c.271 1.136-.964 2.033-1.96 1.425L12 18.354 7.373 21.18c-.996.608-2.231-.29-1.96-1.425l1.257-5.273-4.117-3.527c-.887-.76-.415-2.212.749-2.305l5.404-.434 2.082-5.005Z" clip-rule="evenodd" />
                    </svg>
                  </div>
                  <div>
                    <h3 class="font-semibold">Annual Premium Plan</h3>
                    <p class="text-sm text-gray-600">Billed yearly</p>
                  </div>
                </div>
                
                <div class="space-y-3 mb-6">
                  <div class="flex justify-between">
                    <span class="text-gray-600">Subtotal</span>
                    <span>$119.88</span>
                  </div>
                  <div class="flex justify-between">
                    <span class="text-gray-600">Tax</span>
                    <span>$0.00</span>
                  </div>
                  <div class="flex justify-between pt-3 border-t border-gray-200 font-semibold">
                    <span>Total</span>
                    <span>$119.88</span>
                  </div>
                </div>
                
                <div class="bg-gray-50 rounded-lg p-4 mb-6">
                  <h3 class="font-medium mb-2">What's included:</h3>
                  <ul class="space-y-2 text-sm">
                    <li class="flex items-start">
                      <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 text-green-500 mr-2 flex-shrink-0">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75L11.25 15 15 9.75M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                      </svg>
                      <span>Full access to all premium courses</span>
                    </li>
                    <li class="flex items-start">
                      <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 text-green-500 mr-2 flex-shrink-0">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75L11.25 15 15 9.75M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                      </svg>
                      <span>Downloadable resources and materials</span>
                    </li>
                    <li class="flex items-start">
                      <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 text-green-500 mr-2 flex-shrink-0">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75L11.25 15 15 9.75M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                      </svg>
                      <span>Monthly group mentoring sessions</span>
                    </li>
                    <li class="flex items-start">
                      <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 text-green-500 mr-2 flex-shrink-0">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75L11.25 15 15 9.75M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                      </svg>
                      <span>Course completion certificates</span>
                    </li>
                  </ul>
                </div>
                
                <div class="text-sm text-gray-600">
                  <p class="mb-2">7-day free trial, cancel anytime.</p>
                  <p>By completing this purchase, you agree to our <a href="#" class="text-primary-600 hover:underline">Terms of Service</a> and <a href="#" class="text-primary-600 hover:underline">Privacy Policy</a>.</p>
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
import { ref, reactive } from 'vue';

useHead({
  title: 'Checkout | LearnHub'
});

const paymentStep = ref('information');
const isProcessing = ref(false);

const formData = reactive({
  firstName: '',
  lastName: '',
  email: '',
  phone: '',
  paymentMethod: 'visa',
  cardNumber: '',
  expiry: '',
  cvv: '',
  nameOnCard: '',
  saveCard: false
});

const paymentMethods = [
  { id: 'visa', name: 'Visa', image: 'https://upload.wikimedia.org/wikipedia/commons/thumb/5/5e/Visa_Inc._logo.svg/2560px-Visa_Inc._logo.svg.png' },
  { id: 'mastercard', name: 'Mastercard', image: 'https://upload.wikimedia.org/wikipedia/commons/thumb/2/2a/Mastercard-logo.svg/1280px-Mastercard-logo.svg.png' },
  { id: 'amex', name: 'American Express', image: 'https://upload.wikimedia.org/wikipedia/commons/thumb/f/fa/American_Express_logo_%282018%29.svg/1200px-American_Express_logo_%282018%29.svg.png' },
  { id: 'paypal', name: 'PayPal', image: 'https://upload.wikimedia.org/wikipedia/commons/thumb/b/b5/PayPal.svg/2560px-PayPal.svg.png' }
];

const processPayment = () => {
  isProcessing.value = true;
  
  // Simulate payment processing
  setTimeout(() => {
    isProcessing.value = false;
    paymentStep.value = 'confirmation';
  }, 1500);
};
</script>