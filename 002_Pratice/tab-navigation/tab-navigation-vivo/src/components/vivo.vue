<template>
    <div class="container">
      <h2>Find the phone that's right for you</h2>
      <div class="tabs">
        <div 
          v-for="(item, index) in categories" 
          :key="index" 
          class="tab-item"
          :class="{ active: selectedIndex === index }"
          @click="selectedIndex = index"
        >
          {{ item }}
        </div>
      </div>
    </div>
</template>
  
<script setup>
import { ref } from 'vue'

const categories = ref(["All models", "X Series", "V Series", "Y Series", "T Series", "Accessories"])
const selectedIndex = ref(0) 
</script>
  
<style scoped>
.container {
  text-align: center;
  padding: 20px;
  background-color: #f8f9fb;
}

h2 {
  font-size: 24px;
  margin-bottom: 20px;
}

.tabs {
  display: flex;
  justify-content: center;
  background: white;
  padding: 10px;
  border-radius: 10px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

.tab-item {
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
  color: #444;
  border-radius: 20px;
  transition: all 0.3s ease;
}

.tab-item.active {
  background-color: blue;
  color: white;
}

.tab-item.active {
  background-color: blue;
  color: white;
}
</style>
  