<script setup>
import { ref } from 'vue'

const count = ref(0)

const increase = () => {
    count.value++
}

const decrease = () => {
    count.value--
}
</script>

<template>
    <div class="counter-container">
        <p class="count">{{ count }}</p>
        <div class="button-group">
            <button class="btn increase" @click="increase">増加</button>
            <button class="btn decrease" @click="decrease">減少</button>
        </div>
    </div>
</template>

<style scoped>
.counter-container {
    text-align: center;
    padding: 20px;
    background-color: #f4f4f4;
    border-radius: 10px;
    width: 200px;
    margin: 50px auto;
    box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.1);
}

.count {
    font-size: 2rem;
    font-weight: bold;
    margin-bottom: 15px;
}

.button-group {
    display: flex;
    justify-content: center;
    gap: 10px;
}

.btn {
    padding: 8px 15px;
    font-size: 1rem;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: all 0.3s ease;
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
    background-color: #d32f2f;
}
</style>
