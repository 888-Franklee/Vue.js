<script setup>
import { useCounterStore } from '@/stores/counter'
const counterStore = useCounterStore()
console.log(counterStore)
</script>

<template>
    <button @click="counterStore.increment">{{ counterStore.count }}</button>
    {{ counterStore.doubleCount }}
</template>