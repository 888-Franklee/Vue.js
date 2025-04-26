<template>
    <h3>带颜色的水果列表：</h3>
    <ul>
      <li
        v-for="fruit in fruits"
        :key="fruit"
        :style="{ backgroundColor: getRandomColor() }"
      >
        {{ fruit }}
      </li>
    </ul>
  </template>
  
  <script setup>
  const fruits = ["苹果", "香蕉", "橙子", "葡萄", "西瓜"]
  
  const getRandomColor = () => {
    const letters = "0123456789ABCDEF"
    let color = "#"
    for (let i = 0; i < 6; i++) {
      color += letters[Math.floor(Math.random() * 16)]
    }
    return color
  }
  </script>
  