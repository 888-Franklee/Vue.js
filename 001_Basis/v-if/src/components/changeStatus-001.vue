<template>
  <div class="container">
    <button class="toggle-button" @click="changeStatus">次のステータスへ</button>

    <p 
      v-if="status === 'loading'" 
      class="status-message loading" 
      :class="{ visible: isVisible }"
    >
      読み込み中...
    </p>

    <p 
      v-else-if="status === 'success'" 
      class="status-message success" 
      :class="{ visible: isVisible }"
    >
      読み込みが完了しました！
    </p>

    <p 
      v-else-if="status === 'error'" 
      class="status-message error" 
      :class="{ visible: isVisible }"
    >
      エラーが発生しました。
    </p>

    <p 
      v-else 
      class="status-message unknown" 
      :class="{ visible: isVisible }"
    >
      状態が不明です。
    </p>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const status = ref('loading')
const isVisible = ref(false)
const statuses = ['loading', 'success', 'error', 'unknown']

let index = 0;

const changeStatus = () => {
  index = (index + 1) % statuses.length
  status.value = statuses[index]
  isVisible.value = true  // 每次状态切换时显示消息
}

onMounted(() => {
  isVisible.value = true
})
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
  padding: 12px 25px;
  font-size: 16px;
  font-weight: bold;
  color: #fff;
  background-color: #58067b;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease, transform 0.2s ease;
}

.toggle-button:hover {
  background-color: #1176be;
  transform: scale(1.05);
}

.toggle-button:active {
  background-color: #004085;
}

.status-message {
  margin-top: 20px;
  padding: 12px 20px;
  font-size: 18px;
  font-weight: bold;
  border-radius: 8px;
  opacity: 0;
  transform: translateY(-10px);
  transition: opacity 0.5s ease, transform 0.3s ease;
}

.status-message.visible {
  opacity: 1;
  transform: translateY(0);
}

.status-message.loading {
  background-color: #f39c12;
  color: #340456;
}

.status-message.success {
  background-color: #0a952b;
  color: #190446;
}

.status-message.error {
  background-color: #e74c3c;
  color: #a00909;
}

.status-message.unknown {
  background-color: #bdc3c7;
  color: #080101;
}
</style>
