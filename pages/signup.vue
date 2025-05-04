<template>
    <div class="min-h-screen bg-gray-50 flex items-center justify-center">
      <div class="max-w-md w-full bg-white p-8 rounded-lg shadow-md">
        <h1 class="text-2xl font-bold text-center mb-6">Create New Account</h1>
        
        <form class="space-y-4">
          <div class="grid grid-cols-2 gap-4">
            <div>
              <label for="first-name" class="block text-sm font-medium text-gray-700">First Name</label>
              <input 
                type="text" 
                id="first-name" 
                class="mt-1 block w-full border border-gray-300 rounded-md shadow-sm py-2 px-3 focus:outline-none focus:ring-indigo-500 focus:border-indigo-500"
              >
            </div>
            
            <div>
              <label for="last-name" class="block text-sm font-medium text-gray-700">Last Name</label>
              <input 
                type="text" 
                id="last-name" 
                class="mt-1 block w-full border border-gray-300 rounded-md shadow-sm py-2 px-3 focus:outline-none focus:ring-indigo-500 focus:border-indigo-500"
              >
            </div>
          </div>
          
          <div>
            <label for="email" class="block text-sm font-medium text-gray-700">Email</label>
            <input 
              type="email" 
              id="email" 
              class="mt-1 block w-full border border-gray-300 rounded-md shadow-sm py-2 px-3 focus:outline-none focus:ring-indigo-500 focus:border-indigo-500"
              placeholder="your@email.com"
            >
          </div>
          
          <div>
            <label for="password" class="block text-sm font-medium text-gray-700">Password</label>
            <input 
              type="password" 
              id="password" 
              class="mt-1 block w-full border border-gray-300 rounded-md shadow-sm py-2 px-3 focus:outline-none focus:ring-indigo-500 focus:border-indigo-500"
              placeholder="••••••••"
            >
            <p class="mt-1 text-xs text-gray-500">At least 8 characters</p>
          </div>
          
          <div>
            <label for="confirm-password" class="block text-sm font-medium text-gray-700">Confirm Password</label>
            <input 
              type="password" 
              id="confirm-password" 
              class="mt-1 block w-full border border-gray-300 rounded-md shadow-sm py-2 px-3 focus:outline-none focus:ring-indigo-500 focus:border-indigo-500"
              placeholder="••••••••"
            >
          </div>
          
          <div class="flex items-center">
            <input id="terms" type="checkbox" class="h-4 w-4 text-indigo-600 focus:ring-indigo-500 border-gray-300 rounded">
            <label for="terms" class="ml-2 block text-sm text-gray-700">
              I agree to the <a href="#" class="text-indigo-600 hover:text-indigo-500">Terms</a> and <a href="#" class="text-indigo-600 hover:text-indigo-500">Privacy Policy</a>
            </label>
          </div>
          
          <div>
            <button type="submit" class="w-full flex justify-center py-2 px-4 border border-transparent rounded-md shadow-sm text-sm font-medium text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">
              Create Account
            </button>
          </div>
        </form>
        
        <p class="mt-4 text-center text-sm text-gray-600">
          Already have an account? 
          <a href="/login" class="font-medium text-indigo-600 hover:text-indigo-500">Sign in</a>
        </p>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'SignupPage'
  }
  </script>