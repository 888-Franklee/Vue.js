<script setup>
import { reactive } from 'vue'

const state = reactive({
    count: 0,
    message: "Hello! VUE3"
})

const increment = () => {
    state.count++
}

const decrement = () => {
    state.count--
}
</script>

<template>
    <div class="container">
        <p class="count">Count: {{ state.count }}</p>
        <div class="buttons">
            <button @click="increment" class="btn increase">Increase Count</button>
            <button @click="decrement" class="btn decrease">Decrease Count</button>
        </div>
        <p class="message">{{ state.message }}</p>
        <input v-model="state.message" class="input" placeholder="Type a message">
    </div>
</template>

<style scoped>
.container {
    font-family: Arial, sans-serif;
    text-align: center;
    margin: 20px auto;
    padding: 20px;
    max-width: 400px;
    border: 1px solid #ddd;
    border-radius: 10px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    background-color: #f9f9f9;
}

.count {
    font-size: 24px;
    font-weight: bold;
    margin-bottom: 15px;
    color: #333;
}

.buttons {
    margin-bottom: 15px;
}

.btn {
    padding: 10px 20px;
    margin: 0 5px;
    border: none;
    border-radius: 5px;
    font-size: 16px;
    cursor: pointer;
    transition: background-color 0.3s ease;
}

.increase {
    background-color: #4caf50;
    color: white;
}

.increase:hover {
    background-color: #45a049;
}

.decrease {
    background-color: #f44336;
    color: white;
}

.decrease:hover {
    background-color: #e53935;
}

.message {
    font-size: 18px;
    color: #555;
    margin-bottom: 10px;
}

.input {
    width: calc(100% - 20px);
    padding: 10px;
    font-size: 16px;
    border: 2px solid #ccc;
    border-radius: 5px;
    outline: none;
    box-sizing: border-box;
    transition: border-color 0.3s ease;
}

.input:focus {
    border-color: #061389;
}
</style>
