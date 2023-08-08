<script setup>
import { ref } from "vue";

// State variables
const username = ref("");
const password = ref("");

const newUsername = ref("");
const newPassword = ref("");
const conformPassword = ref("");
const isLoggedIn = ref(false);
const isRegisterFormVisible = ref(false);

// Event handlers
function submitFrom() {
  isLoggedIn.value = true;
}

function handleRegister() {
  // Perform password matching validation
  if (newPassword.value !== conformPassword.value) {
    alert("Passwords do not match. Please try again.");
  } else {
    isLoggedIn.value = true;
  }
}

function showRegisterForm() {
  isRegisterFormVisible.value = true;
}

function showLoginForm() {
  isRegisterFormVisible.value = false;
}
</script>

<template>
  <section
    class="h-screen w-full flex bg-gradient-to-r from-indigo-500/25 via-purple-500/25 to-pink-500/25"
    id="app"
  >
    <!-- Show welcome message if the user is logged in -->
    <div
      v-if="isLoggedIn"
      class="w-full h-screen flex justify-center items-center flex-col text-white bg-gradient-to-r from-indigo-500 via-purple-500 to-pink-500"
    >
      <h2 class="mb-5 text-5xl">Welcome, {{ username }}!</h2>
      <p class="text-2xl">You are now logged in.</p>
    </div>

    <!-- Show login and registration forms if the user is not logged in -->
    <div v-else class="grid grid-cols-2">
      <div
        class="h-screen w-[650px]"
        style="
          background-image: url(https://images.unsplash.com/photo-1614082242765-7c98ca0f3df3?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=870&q=80);
          background-repeat: no-repeat;
          background-size: cover;
        "
      >
        <h1
          class="font-extrabold text-4xl text-white mt-10 ml-10 inline-block p-2 bg-gradient-to-r from-indigo-500/75 via-purple-500/75 to-pink-500/75 rounded-xl"
        >
          Let's Go
        </h1>
      </div>

      <div class="flex flex-col justify-center items-center">
        <!-- Login form -->
        <form
          class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4"
          v-if="!isRegisterFormVisible"
          @submit.prevent="submitFrom"
        >
          <div class="mb-4 w-80">
            <label
              class="block text-gray-700 text-sm font-bold mb-2"
              required
              for="username"
            >
              Username
            </label>
            <input
              v-model="username"
              required
              class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
              id="username"
              type="text"
              placeholder="Username"
            />
          </div>
          <div class="mb-6 w-80">
            <label
              class="block text-gray-700 text-sm font-bold mb-2"
              for="password"
              required
            >
              Password
            </label>
            <input
              v-model="password"
              class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 mb-3 leading-tight focus:outline-none focus:shadow-outline"
              required
              id="password"
              type="password"
              placeholder="******************"
            />
          </div>
          <div class="flex items-center justify-between">
            <button
              class="bg-orange-600 hover:bg-orange-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
              type="submit"
            >
              Sign In
            </button>
            <a
              class="inline-block align-baseline font-bold text-sm text-orange-600 hover:text-orange-800"
              href="#"
              @click="showRegisterForm"
            >
              Or Register
            </a>
          </div>
        </form>

        <!-- Registration form -->
        <form
          class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4"
          v-if="isRegisterFormVisible"
          @submit.prevent="handleRegister"
        >
          <div class="mb-4 w-80">
            <label
              class="block text-gray-700 text-sm font-bold mb-2"
              for="Username"
              required
            >
              Username
            </label>
            <input
              v-model="username"
              class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
              id="Username"
              type="text"
              placeholder="Username"
              required
            />
          </div>
          <div class="mb-4 w-80">
            <label
              class="block text-gray-700 text-sm font-bold mb-2"
              for="newPassword"
              required
            >
              New Password
            </label>
            <input
              v-model="newPassword"
              class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 mb-3 leading-tight focus:outline-none focus:shadow-outline"
              required
              id="newPassword"
              type="password"
              placeholder="******************"
            />
          </div>
          <div class="mb-6 w-80">
            <label
              class="block text-gray-700 text-sm font-bold mb-2"
              for="conformPassword"
              required
            >
              Conform Password
            </label>
            <input
              v-model="conformPassword"
              class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 mb-3 leading-tight focus:outline-none focus:shadow-outline"
              required
              id="conformPassword"
              type="password"
              placeholder="******************"
            />
          </div>
          <div class="flex items-center justify-between">
            <button
              class="bg-green-600 hover:bg-green-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
              type="submit"
            >
              Register
            </button>
            <a
              class="inline-block align-baseline font-bold text-sm text-green-600 hover:text-green-800"
              href="#"
              @click="showLoginForm"
            >
              Back to Login
            </a>
          </div>
        </form>

        <p class="text-center text-gray-500 text-xs">
          &copy;2023 Acme Corp. All rights reserved.
        </p>
      </div>
    </div>
  </section>
</template>
<style scoped></style>
