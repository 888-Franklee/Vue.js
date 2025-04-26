<script setup>
import { ref, provide } from 'vue'
import ChildComponent from './components/Child.vue'

const count = ref(0)
provide('count', count)

function increment() {
  count.value++;
}
</script>

<template>
  <div>
    <h1>親コンポーネント</h1>
    <button @click="increment">カウントアップ</button>
    <ChildComponent />
  </div>
</template>

