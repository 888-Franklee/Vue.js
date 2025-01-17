# コンポーネントを引用する方法
## コンポーネントの登録
### 1.グローバル登録
### グローバル登録を行うと、どのコンポーネントでも利用できます。通常、main.jsで設定します。
### Vue2
```
import Vue from 'vue';
import MyComponent from './components/MyComponent.vue';

Vue.component('MyComponent', MyComponent);

new Vue({
  render: h => h(App),
}).$mount('#app');
```
### Vue3
```
import { createApp } from 'vue';
import App from './App.vue';
import MyComponent from './components/MyComponent.vue';

const app = createApp(App);
app.component('MyComponent', MyComponent);

app.mount('#app');
```
### 2.ローカル登録
### ローカル登録を行うと、特定の親コンポーネント内でのみ利用できます。（Vue 2 と Vue 3 共通）
### 方法１
```
<script>
import MyComponent from './components/MyComponent.vue'

export default {
  components: {
    MyComponent
  }
}
</script>
```
### 方法２
```
<script setup>
import MyComponent from './components/MyComponent.vue'
</script>
```
## コンポーネントの使用
```
<template>
  <div>
    <MyComponent/>
  </div>
</template>
```
