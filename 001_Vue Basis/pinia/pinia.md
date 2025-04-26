# pinia

## インストール
```
npm install pinia
```
## PiniaをVueアプリに登録
```
import { createApp } from 'vue'
import { createPinia } from 'pinia'
import App from './App.vue'

const app = createApp(App)
const pinia = createPinia()

app.use(pinia);
app.mount('#app')
```
## Storeの作成
```
import { defineStore } from 'pinia'

export const useMainStore = defineStore('main', {
  state: () => ({
    count: 0,
  }),
  actions: {
    increment() {
      this.count++;
    },
  },
})
```
## コンポーネントでの利用
```
<script setup>
import { useMainStore } from '@/stores/main'
const mainStore = useMainStore()

function incrementCount() {
  mainStore.increment();
}
</script>

<template>
  <div>
    <p>カウント: {{ mainStore.count }}</p>
    <button @click="incrementCount">増やす</button>
  </div>
</template>
```