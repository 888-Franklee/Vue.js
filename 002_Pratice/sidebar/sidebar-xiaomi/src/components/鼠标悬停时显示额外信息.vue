<template>
    <div class="sidebar">
        <ul>
            <li
            v-for="(item,index) in menuItems"
            :key="index" 
            @mouseover="hoverIndex = index"
            @mouseleave="hoverIndex = null"

            >
            {{ item }}
            <span v-if="hoverIndex === index" class="tooltip">詳細情報</span>
            </li>
        </ul>
    </div>
</template>

<script setup>
import { ref } from 'vue'

const menuItems = ref(["手机", "电脑", "平板", "耳机", "音箱"])

const hoverIndex = ref(null)

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
  position: relative;
}
.tooltip {
  position: absolute;
  left: 100%;
  top: 50%;
  transform: translateY(-50%);
  background: white;
  color: black;
  padding: 5px;
  border-radius: 5px;
  font-size: 12px;
  white-space: nowrap;
  box-shadow: 0 0 5px rgba(0,0,0,0.3);
}
</style>
