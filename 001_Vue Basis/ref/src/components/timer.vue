<script setup>
import { ref } from 'vue'

const seconds = ref(0)
let timer = null

const start = () => {
  if (!timer) {
    timer = setInterval(() => {
      seconds.value++
    }, 1000)
  }
}

const pause = () => {
  clearInterval(timer)
  timer = null
}

const reset = () => {
  pause()
  seconds.value = 0
}
</script>

<template>
  <div>
    <h2>時間: {{ seconds }} 秒</h2>
    <button @click="start">開始</button>
    <button @click="pause">一時停止</button>
    <button @click="reset">リセット</button>
  </div>
</template>
