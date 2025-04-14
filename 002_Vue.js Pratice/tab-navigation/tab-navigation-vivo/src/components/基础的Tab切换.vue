<template>
    <div class="container">
      <h2>Simple Tab Navigation</h2>
      <div class="tabs">
        <div
          v-for="(tab, index) in tabs"
          :key="index"
          class="tab-item"
          :class="{ active: selectedIndex === index }"
          @click="selectedIndex = index"
        >
          {{ tab.label }}
        </div>
      </div>
      <div class="tab-content">
        {{ tabs[selectedIndex].content }}
      </div>
    </div>
</template>
  
<script setup>
import { ref } from 'vue'

const tabs = ref([
  { label: "Home", content: "Welcome to the Home Page!" },
  { label: "Profile", content: "This is your Profile section." },
  { label: "Settings", content: "Adjust your settings here." }
])

const selectedIndex = ref(0)
</script>

  
<style scoped>
.container {
  text-align: center;
  padding: 20px;
  background-color: #f8f9fb;
}

.tabs {
  display: flex;
  justify-content: center;
  padding: 10px;
  background: white;
  border-radius: 10px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

.tab-item {
  padding: 10px 20px;
  cursor: pointer;
  font-size: 16px;
  color: #444;
  border-radius: 10px;
  transition: all 0.3s ease;
}

.tab-item.active {
  background-color: blue;
  color: white;
}

.tab-content {
  margin-top: 20px;
  font-size: 18px;
  color: #333;
}
</style>