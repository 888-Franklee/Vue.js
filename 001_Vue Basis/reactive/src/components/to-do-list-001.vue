<script setup>
import { reactive } from 'vue'


const todoList = reactive({
  items: []
})

const addTodo = (task) => {
  todoList.items.push({ id: Date.now(), task })
}

const removeTodo = (id) => {
  todoList.items = todoList.items.filter(task => task.id !== id)
}
</script>

<template>
  <div>
    <h2>Todo List</h2>
    <input v-model="newTask" placeholder="New Task" />
    <button @click="addTodo(newTask)">Add Task</button>
    <ul>
      <li v-for="item in todoList.items" :key="item.id">
        {{ item.task }}
        <button @click="removeTodo(item.id)">Remove</button>
      </li>
    </ul>
  </div>
</template>
