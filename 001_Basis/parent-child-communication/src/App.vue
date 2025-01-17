<template>
  <div>
    <ChildComponent title="こんにちは" :count="10" />
  </div>
</template>

<script setup>
import ChildComponent from './components/ChildComponent.vue'
</script>