<template>
    <div class="container">
      <h2>Dynamic Tabs</h2>
      <div class="tabs">
        <div
          v-for="(tab, index) in tabs"
          :key="tab.id"
          class="tab-item"
          :class="{ active: selectedIndex === index }"
          @click="selectedIndex = index"
        >
          {{ tab.label }}
          <span class="close-btn" @click.stop="removeTab(index)">✖</span>
        </div>
        <button class="add-btn" @click="addTab">＋ Add Tab</button>
      </div>
      <div class="tab-content">
        {{ tabs[selectedIndex]?.content || "No tabs available" }}
      </div>
    </div>
</template>
  
<script setup>
import { ref } from 'vue'

const tabs = ref([
  { id: 1, label: "Tab 1", content: "Content of Tab 1" },
  { id: 2, label: "Tab 2", content: "Content of Tab 2" }
])

const selectedIndex = ref(0)
let nextId = 3

const addTab = () => {
  tabs.value.push({
    id: nextId++,
    label: `Tab ${nextId - 1}`,
    content: `Content of Tab ${nextId - 1}`
  })
  selectedIndex.value = tabs.value.length - 1
}

const removeTab = (index) => {
  tabs.value.splice(index, 1)
  if (selectedIndex.value >= tabs.value.length) {
    selectedIndex.value = tabs.value.length - 1
  }
}
</script>
  
<style scoped>
.container {
  text-align: center;
  padding: 20px;
}

.tabs {
  display: flex;
  gap: 5px;
  padding: 10px;
  background: white;
  border-radius: 10px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  overflow-x: auto;
}

.tab-item {
  display: flex;
  align-items: center;
  gap: 5px;
  padding: 10px 15px;
  cursor: pointer;
  font-size: 16px;
  color: #444;
  border-radius: 10px;
  transition: all 0.3s ease;
  position: relative;
}

.tab-item.active {
  background-color: blue;
  color: white;
}

.close-btn {
  font-size: 12px;
  cursor: pointer;
  color: red;
}

.add-btn {
  background-color: green;
  color: white;
  border: none;
  padding: 8px 12px;
  cursor: pointer;
  border-radius: 5px;
}
</style>