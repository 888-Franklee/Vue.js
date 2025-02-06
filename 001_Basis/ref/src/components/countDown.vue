<script setup>
import { ref, watch } from 'vue'

const countdown = ref(10)
let timer = null

const startCountdown = () => {
  countdown.value = 10
  timer = setInterval(() => {
    countdown.value--
  }, 1000)
}

watch(countdown, (newValue) => {
  if (newValue <= 0) {
    clearInterval(timer)
  }
})
</script>

<template>
  <div>
    <h2 v-if="countdown > 0">残り: {{ countdown }} 秒</h2>
    <h2 v-else>終了！</h2>
    <button @click="startCountdown">スタート</button>
  </div>
</template>
