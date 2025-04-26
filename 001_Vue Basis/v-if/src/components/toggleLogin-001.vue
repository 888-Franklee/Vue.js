<template>
    <div>
      <button @click="toggleLogin">Toggle Login</button>
      <p v-if="isLoggedIn">ログインしています</p>
      <p v-else>ログインしていません</p>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  
  const isLoggedIn = ref(false)
  
  const toggleLogin = () => {
    isLoggedIn.value = !isLoggedIn.value
  }
  </script>
  