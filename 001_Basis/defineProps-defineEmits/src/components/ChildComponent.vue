<template>
  <div>
    <h2>子コンポーネント</h2>
    <button @click="sendMessage">メッセージを送信</button>
  </div>
</template>

<script setup>
import { defineEmits } from 'vue';

const emit = defineEmits(['send-message']);

function sendMessage() {
  emit('send-message', 'こんにちは、親コンポーネント！');
}
</script>
