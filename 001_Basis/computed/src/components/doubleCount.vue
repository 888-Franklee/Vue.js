<script setup>
import { ref, computed } from 'vue'

const count = ref(0)
const doubleCount = computed(() => count.value * 2)
</script>

<template>
  <div>
    <p>現在の値: {{ count }}</p>
    <p>計算後の値: {{ doubleCount }}</p>
    <button @click="count++">インクリメント</button>
  </div>
</template>
