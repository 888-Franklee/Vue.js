<template>
    <h2>深度嵌套对象的响应式处理</h2>
    <p>Theme : {{ data.settings.theme }}</p>
    <button @click="toggletheme">Toggle Theme</button>
    <p>Email Notifications: {{ data.settings.notification.email }}</p>
    <p v-if="data.settings.newFeature">New Feature: {{ data.settings.newFeature }}</p>
    <button @click="addProperty">Add New Feature</button>
</template>

<script setup>
import { reactive, watchEffect } from 'vue'

const data = reactive({
    settings: {
        theme: "light",
        notification:{
            email: true,
            sms: false
        },
    }
})

const toggletheme = ()=>{
    data.settings.theme = data.settings.theme === "light" ? "dark" : "light"
}

const addProperty = ()=>{
    data.settings.newFeature = "Enabled"
}

watchEffect(() => {
  console.log("Current theme:", data.settings.theme)
  console.log("Email notifications enabled:", data.settings.notification.email)
  if (data.settings.newFeature) {
    console.log("New feature:", data.settings.newFeature)
  }
})
</script>