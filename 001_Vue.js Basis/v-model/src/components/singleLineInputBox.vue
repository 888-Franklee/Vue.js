<template>
    <div>
      <input v-model.lazy="message" placeholder="ご入力ください！" @keydown.enter="messageOk">
      <p>入力した内容：{{message}}</p>
    </div>
  
</template>
  
<script setup>
import { ref } from 'vue'
  
const message = ref("")

const messageOk = ()=>{
    if (message.value === "888"){
        alert('入力正解！')
    } else{
        alert('間違っている！')
    }
} 
</script>
  
<style scoped>
input {
    padding: 9px;
    margin-bottom: 10px;
    border: 2px solid #870909;
    border-radius: 4px;
}
p {
    font-size: 18px;
    color: #4a077a;
}
</style>
  