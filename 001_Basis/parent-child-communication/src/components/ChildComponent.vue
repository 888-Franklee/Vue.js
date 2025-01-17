<template>
    <div>
      <h1>{{ title }}</h1>
      <p>カウント: {{ count }}</p>
    </div>
  </template>
  
  <script setup>
  defineProps({
    title: String, 
    count: {
      type: Number,
      required: true,
    },
  });
  </script>