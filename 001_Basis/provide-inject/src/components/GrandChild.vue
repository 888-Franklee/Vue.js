<script setup>
import { inject } from 'vue'

const count = inject('count')
</script>

<template>
  <div>
    <h1>孫コンポーネント</h1>
    <p>カウント: {{ count }}</p>
  </div>
</template>

