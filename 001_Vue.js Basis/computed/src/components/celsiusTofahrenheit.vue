<template>
  <div>
    <p>摂氏: {{ celsius }}</p>
    <p>華氏: {{ fahrenheit }}</p>
    <button @click="fahrenheit = 68">華氏を 68 度に設定</button>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';

const celsius = ref(0);

const fahrenheit = computed({
  get: () => (celsius.value * 9) / 5 + 32,
  set: (value) => {
    celsius.value = ((value - 32) * 5) / 9;
  },
});
</script>
