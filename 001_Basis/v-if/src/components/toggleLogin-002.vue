<template>
    <div class="login-container">
        <button @click="toggleLogin" class="login-button">
            {{ isLoggedIn ? 'ログアウト' : 'ログイン' }}
        </button>
        <p class="login-message" :class="{ loggedIn: isLoggedIn, loggedOut: !isLoggedIn }">
            {{ isLoggedIn ? 'ログインしています' : 'ログインしていません' }}
        </p>
    </div>
</template>

<script setup>
import { ref } from 'vue'

const isLoggedIn = ref(false)

const toggleLogin = () => {
    isLoggedIn.value = !isLoggedIn.value
}
</script>

<style scoped>

.login-container {
    text-align: center;
    margin: 20px auto;
    padding: 20px;
    max-width: 400px;
    border: 1px solid #ddd;
    border-radius: 10px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    background: #f9f9f9;
}

.login-button {
    display: inline-block;
    padding: 10px 20px;
    font-size: 16px;
    font-weight: bold;
    color: white;
    background-color: #007bff;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s ease, transform 0.2s ease;
}

.login-button:hover {
    background-color: #0056b3;
    transform: scale(1.05);
}

.login-button:active {
    background-color: #003f88;
}


.login-message {
    margin-top: 20px;
    font-size: 18px;
    font-weight: bold;
}


.loggedIn {
    color: #28a745; 
}

.loggedOut {
    color: #dc3545;
}
</style>
