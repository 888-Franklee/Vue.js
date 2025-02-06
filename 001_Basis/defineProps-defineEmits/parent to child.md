# 親から子への通信　
## １．基本の書き方
### 親コンポーネント：
```
<template>
  <div>
    <ChildComponent title="こんにちは" :count="10" />
  </div>
</template>

<script setup>
import ChildComponent from './ChildComponent.vue'; // 子コンポーネントをインポート
</script>
```
### 子コンポーネント：
```
<template>
  <div>
    <h1>{{ title }}</h1>
    <p>カウント: {{ count }}</p>
  </div>
</template>

<script setup>
import { defineProps } from 'vue' 

defineProps({
  title: String, 
  count: {
    type: Number, 
    required: true, 
  },
});
</script>
```
#### defineProps や defineEmits はグローバルに提供されているため、明示的に import する必要がありません。import { defineProps } from 'vue'を書かなくても良いです。
### 親コンポーネント：
```
<template>
  <div>
    <ChildComponent title="こんにちは" :count="10" />
  </div>
</template>

<script>
import ChildComponent from './ChildComponent.vue';

export default {
  components: { ChildComponent },
}
</script>
```
### 子コンポーネント：
```
<template>
  <div>
    <h1>{{ title }}</h1>
    <p>カウント: {{ count }}</p>
  </div>
</template>

<script>
export default {
  props: {
    title: String,
    count: {
      type: Number,
      required: true,
    },
  },
};
</script>
```
## ２．refなどを使う時の書き方
### 親コンポーネント：
```
<template>
  <div>
    <ChildComponent title="こんにちは" :count=count />
  </div>
</template>

<script setup>
import ChildComponent from './components/ChildComponent.vue'
import {ref} from 'vue'
const count = ref(888)
</script>
```
### 子コンポーネント：
```
<template>
    <div>
      <h1>{{ title }}</h1>
      <p>カウント: {{ count }}</p>
    </div>
  </template>
  
  <script setup>
  defineProps({
    title: String, 
    count: {
      type: Number,
      required: true,
    },
  });
  </script>
```