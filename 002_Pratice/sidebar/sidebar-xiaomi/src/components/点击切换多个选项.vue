<template>
    <div class="sidebar">
      <ul>
        <li 
          v-for="(item, index) in menuItems" 
          :key="index" 
          @click="toggleSelection(index)"
          :class="{ selected: selectedItems.includes(index) }"
        >
          {{ item }}
        </li>
      </ul>
    </div>
</template>
  
<script setup>
import { ref } from 'vue'
  
const menuItems = ref(["苹果", "香蕉", "橘子", "葡萄", "西瓜"])
const selectedItems = ref([])
  

const toggleSelection = (index) => {
  if (selectedItems.value.includes(index)) {
    selectedItems.value = selectedItems.value.filter(i => i !== index)
  } else {
    selectedItems.value.push(index)
  }
}

</script>
  
<style scoped>
.sidebar {
  width: 200px;
  background-color: #444;
  padding: 10px;
}
ul {
  list-style: none;
  padding: 0;
}
li {
  padding: 10px;
  color: white;
  cursor: pointer;
}
.selected {
  background-color: rgb(0, 153, 255);
}
</style>
  