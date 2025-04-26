<script setup>
import { ref } from 'vue'

const fontSize = ref(16)

const increaseFont = () => {
  fontSize.value += 2
}

const decreaseFont = () => {
  fontSize.value -= 2
}
</script>

<template>
  <div>
    <p :style="{ fontSize: fontSize + 'px' }">フォントサイズを変更できます！</p>
    <button @click="increaseFont">大きくする</button>
    <button @click="decreaseFont">小さくする</button>
  </div>
</template>
