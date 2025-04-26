# 子から親への通信
## 子コンポーネント：
```
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
```
## 親コンポーネント：
```
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
```
