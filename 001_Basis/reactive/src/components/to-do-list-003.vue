<script setup>
import { reactive } from 'vue'

const state = reactive({
  todos: [],
  newTodo: ''
});

const addTodo = () => {
  if (state.newTodo.trim()) {
    state.todos.push(state.newTodo);
    state.newTodo = '';
  }
};

const removeTodo = (index) => {
  state.todos.splice(index, 1);
};
</script>

<template>
  <div class="todo-container">
    <h1>Vue3 To do list</h1>
    <div class="input-container">
      <input class="todo-input" v-model="state.newTodo" placeholder="输入新任务" />
      <button class="add-button" @click="addTodo">Add</button>
    </div>
    <ul class="todo-list">
      <li v-for="(todo, index) in state.todos" :key="index" class="todo-item">
        <span>{{ todo }}</span>
        <button class="delete-button" @click="removeTodo(index)">Delete</button>
      </li>
    </ul>
  </div>
</template>

<style scoped>
.todo-container {
  max-width: 400px;
  margin: 20px auto;
  font-family: Arial, sans-serif;
  text-align: center;
}

h1 {
  color: rgb(145, 20, 20);
  font-weight: 80px
}

.input-container {
  display: flex;
  justify-content: center;
  margin-bottom: 20px;
}

.todo-input {
  width: 70%;
  padding: 10px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 5px;
  margin-right: 10px;
}

.add-button {
  padding: 10px 20px;
  font-size: 16px;
  background-color: #4caf50;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.add-button:hover {
  background-color: #45a049;
}

.todo-list {
  list-style-type: none;
  padding: 0;
}

.todo-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #f9f9f9;
  padding: 10px;
  margin-bottom: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
}

.delete-button {
  padding: 5px 10px;
  font-size: 14px;
  background-color: #f44336;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.delete-button:hover {
  background-color: #e53935;
}
</style>
