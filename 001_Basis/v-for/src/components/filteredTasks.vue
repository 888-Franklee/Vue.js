<template>
    <h3>过滤前的任务列表：</h3>
    <ul>
        <li v-for="task in tasks" :key="task">{{ task }}</li>
    </ul>
    <h3>过滤后的任务列表：</h3>
    <ul>
        <li v-for="task in filteredTasks" :key="task">{{ task }}</li>
    </ul>
  </template>
  
  <script setup>
  import { ref, computed } from "vue"
  
  const tasks = ref(["学习 Vue.js", "完成作业", "锻炼身体", "复习", "休息"])
  const filteredTasks = computed(() => tasks.value.filter((task) => task.includes("学")))
  </script>
  