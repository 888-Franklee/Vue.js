<script setup>
import { ref } from 'vue'

const bgColor = ref('#3498db')

const changeColor = () => {
  bgColor.value = `#${Math.floor(Math.random() * 16777215).toString(16)}`
}
</script>

<template>
  <div :style="{ backgroundColor: bgColor, padding: '20px', textAlign: 'center' }">
    <h2>背景色を変更する</h2>
    <button @click="changeColor">色を変える</button>
  </div>
</template>
