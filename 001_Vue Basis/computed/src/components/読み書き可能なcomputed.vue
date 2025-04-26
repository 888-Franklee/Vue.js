<script setup>
import { ref, computed } from 'vue';

const count = ref(0);

const doubleCount = computed({
  get: () => count.value * 2,
  set: (value) => {
    count.value = value / 2;
  },
});
</script>

<template>
  <div>
    <p>現在の値: {{ count }}</p>
    <p>計算後の値: {{ doubleCount }}</p>
    <button @click="count++">インクリメント</button>
    <button @click="doubleCount = 10">計算値を 10 に設定</button>
    <!-- <button @click="doubleCount.value = 10">計算値を 10 に設定</button> -->
  </div>
</template>
