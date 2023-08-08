<script setup>
import {RouterLink} from 'vue-router'
import {ref, reactive} from 'vue'
import router from '../router';

const userData = reactive({});
let message = ref('')

// Register User function 
function register() {
    if(!userData.username || !userData.password){
        message.value = 'Please fill all fields'
    }else{
        localStorage.setItem('user', JSON.stringify(userData))
        router.push('/')
    }
    
    
}

</script>

<template>
    <section class="flex h-screen w-full">
      <div class="w-1/2" style="background-image: url(https://images.unsplash.com/photo-1690555575753-7aa27df96b52?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=774&q=80); background-repeat: no-repeat; background-size: cover;">
        <h1 class="mb-5 text-2xl mt-10 ml-10 text-white">Register Page</h1>
      </div>
      <div class="w-1/2 flex flex-col justify-center items-center bg-gray-200">
        <h2 class="mb-5 text-xl text-gray-600">Login or register</h2>
        <div class="w-full max-w-xs">
          <form class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4">
            <div class="mb-4">
              <label class="block text-gray-700 text-sm font-bold mb-2" for="name">Name</label>
              <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" v-model="userData.name"  type="text" placeholder="Your Name">
            </div>
            <div class="mb-4">
              <label class="block text-gray-700 text-sm font-bold mb-2" for="username">Email</label>
              <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" v-model="userData.username" type="email" placeholder="user@example.com" v-validate="{ required: true, email: true }">
            </div>
            <div class="mb-6">
              <label class="block text-gray-700 text-sm font-bold mb-2" for="password">
                Password
              </label>
              <input class="shadow appearance-none border  rounded w-full py-2 px-3 text-gray-700 mb-3 leading-tight focus:outline-none focus:shadow-outline" v-model="userData.password" type="password" placeholder="**********">
              <p class="text-red-500 text-xs italic">{{ message }}</p>

            </div>

            <div class="flex items-center justify-between">
              <RouterLink to="/" class="inline-block align-baseline font-bold text-sm text-orange-600 hover:text-orange-800">Login</RouterLink>

              <button class="bg-orange-600 hover:bg-orange-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline" @click="register()" type="button">
                Register
              </button>
            </div>
          </form>
          <p class="text-center text-gray-500 text-xs">
            &copy;2023 HUMAUN KABIR. All rights reserved.
          </p>
        </div>
      </div>
    </section>
  </template>

<style lang="scss" scoped>

</style>