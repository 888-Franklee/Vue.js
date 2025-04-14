<template><div class="container">
      <button class="toggle-button" @click="toggleVisibility">Toggle Visibility</button>
      <p class="message" v-if="isVisible">
        このメッセージは isVisible が true のときだけ表示されます。
      </p>
    </div>
</template>
  
<script setup>
import { ref } from 'vue'
  
const isVisible = ref(false)
  
const toggleVisibility = () => {
    isVisible.value = !isVisible.value
}
</script>
  
<style scoped>
 
.container {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin: 50px auto;
    padding: 20px;
    background-color: #f9f9f9;
    border: 1px solid #ddd;
    border-radius: 10px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    max-width: 400px;
    text-align: center;
}
  
.toggle-button {
    padding: 10px 20px;
    font-size: 16px;
    font-weight: bold;
    color: #fff;
    background-color: #5d0887;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s ease, transform 0.2s ease;
}
  
.toggle-button:hover {
    background-color: #0b0f83;
    transform: scale(1.05);
}
  
.toggle-button:active {
    background-color: #004085;
}
  
.message {
    margin-top: 20px;
    padding: 10px 20px;
    background-color: #28a745;
    color: #fff;
    font-size: 18px;
    font-weight: bold;
    border-radius: 5px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    animation: fade-in 0.5s ease;
}
  
@keyframes fade-in {
    from {
      opacity: 0;
      transform: translateY(-10px);
    }
    to {
      opacity: 1;
      transform: translateY(0);
    }
}
</style>
  