<template>
    <div class="sidebar">
      <ul>
        <li 
          v-for="(item, index) in menuItems" 
          :key="index" 
          @mouseover="hoverIndex = index" 
          @mouseleave="hoverIndex = null"
          :class="{ hover: hoverIndex === index }"
        >
          {{ item }}
        </li>
      </ul>
    </div>
  </template>
  
<script setup>
import { ref } from 'vue'
  
const menuItems = ref([
    "手机",
    "电视",
    "家电",
    "笔记本 平板 显示器",
    "出行 穿戴",
    "耳机 音箱",
    "健康 儿童",
    "生活 箱包",
    "智能 路由器",
    "电源 配件"
])
  
const hoverIndex = ref(null)
</script>
  
<style scoped>
  .sidebar {
    width: 200px;
    background-color: #444;
    padding: 10px;
}
  
ul {
    list-style: none;/*list-style: none; は、CSS のプロパティで、リスト（<ul> や <ol>）のデフォルトのスタイル（例えば黒い●や番号）を削除するために使われます。 */
    padding: 0;
}
  
li {
    padding: 10px;
    color: white;
    cursor: pointer;
}
  
li.hover {
    background-color: rgb(213, 93, 7);
}
</style>
  