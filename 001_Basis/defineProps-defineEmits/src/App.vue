<template>
  <div>
    <h1>親コンポーネント</h1>
    <p>受け取ったメッセージ: {{ receivedMessage }}</p>
    <ChildComponent @send-message="handleMessage" />
  </div>
</template>

<script setup>
import ChildComponent from './components/ChildComponent.vue';
import { ref } from 'vue';

const receivedMessage = ref('');

function handleMessage(message) {
  receivedMessage.value = message;
}
</script>
