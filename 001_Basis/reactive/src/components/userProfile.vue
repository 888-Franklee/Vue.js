<template>
    <div class="container">
        <div class="profile">
            <p>User Profile</p>
            <p>Name: {{ user.name }}</p>
            <p>Age: {{ user.age }}</p>
            <p>City: {{ user.address.city }}</p>
            <input v-model="user.address.city" placeholder="Update City">
        </div>
    </div>
</template>

<script setup>
import { reactive } from 'vue'

const user = reactive({
    name: "Frank",
    age: 28,
    address: {
        city: "Beijing",
        country: "China"
    }
})
</script>

<style scoped>

.container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh; 
    background-color: #efe9f1; 
    margin: 0;
}


.profile {
    font-family: Arial, sans-serif;
    padding: 20px;
    border: 1px solid #ddd;
    border-radius: 10px;
    background-color: #f0d9d6;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    max-width: 400px;
    width: 90%; 
}

p {
    font-size: 16px;
    color: #333;
    margin-bottom: 10px;
}

input {
    width: calc(100% - 20px);
    padding: 10px;
    font-size: 14px;
    border: 2px solid #ccc;
    border-radius: 5px;
    outline: none;
    transition: border-color 0.3s ease;
}

input:focus {
    border-color: #180872;
}
</style>
