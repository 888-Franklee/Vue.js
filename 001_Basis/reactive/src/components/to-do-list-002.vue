<template>
    <div id="app" class="container">
      <div class="todo-app">
        <h1 class="title">Vue 2 Todo List</h1>
        <div class="input-container">
          <input 
            v-model="newTask" 
            placeholder="Add a new task" 
            @keyup.enter="addTask" 
            class="task-input"
          />
          <button @click="addTask" class="add-button">Add</button>
        </div>
        <ul class="task-list">
          <li 
            v-for="(task, index) in tasks" 
            :key="index" 
            class="task-item"
          >
            <span 
              :class="{ completed: task.completed }" 
              class="task-text" 
              @click="toggleComplete(index)"
            >
              {{ task.text }}
            </span>
            <button 
              @click="deleteTask(index)" 
              class="delete-button"
            >
              ✕
            </button>
          </li>
        </ul>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        newTask: '',
        tasks: []
      };
    },
    methods: {
      addTask() {
        if (this.newTask.trim() !== '') {
          this.tasks.push({ text: this.newTask, completed: false });
          this.newTask = '';
        }
      },
      toggleComplete(index) {
        this.tasks[index].completed = !this.tasks[index].completed;
      },
      deleteTask(index) {
        this.tasks.splice(index, 1);
      }
    }
  };
  </script>
  
  <style scoped>
  
  body, html {
    margin: 0;
    padding: 0;
    height: 100%;
    font-family: 'Arial', sans-serif;
    background-color: #f4f4f4;
  }
  
  .container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    width: 100vw; 
    background-color: #f9f9f9; 
  }
  
  .todo-app {
    width: 100%;
    max-width: 400px;
    padding: 20px;
    background: #fff;
    border-radius: 10px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    text-align: center;
  }
  
  .title {
    color: #333;
    margin-bottom: 20px;
    font-size: 24px;
    font-weight: bold;
  }
  
  .input-container {
    display: flex;
    justify-content: space-between;
    margin-bottom: 20px;
  }
  
  .task-input {
    flex: 1;
    padding: 10px;
    font-size: 16px;
    border: 1px solid #ddd;
    border-radius: 5px;
    margin-right: 10px;
  }
  
  .add-button {
    background-color: #42b883;
    color: #fff;
    border: none;
    padding: 10px 15px;
    font-size: 16px;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s;
  }
  
  .add-button:hover {
    background-color: #369974;
  }
  
  .task-list {
    list-style: none;
    padding: 0;
  }
  
  .task-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 5px;
    margin-bottom: 10px;
    background-color: #fafafa;
    transition: box-shadow 0.3s;
  }
  
  .task-item:hover {
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  }
  
  .task-text {
    font-size: 16px;
    cursor: pointer;
  }
  
  .task-text.completed {
    text-decoration: line-through;
    color: gray;
  }
  
  .delete-button {
    background: none;
    border: none;
    color: #e74c3c;
    font-size: 18px;
    cursor: pointer;
    transition: color 0.3s;
  }
  
  .delete-button:hover {
    color: #c0392b;
  }
  </style>
  