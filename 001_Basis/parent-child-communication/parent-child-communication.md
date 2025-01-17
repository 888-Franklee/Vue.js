# Vueの父子間の通信方法
## 親から子への通信　方法1
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
import { defineProps } from 'vue' // defineProps や defineEmits はグローバルに提供されているため、明示的に import する必要がありません。書かなくても良いです。

defineProps({
  title: String, 
  count: {
    type: Number, 
    required: true, 
  },
});
</script>
```
## 親から子への通信　方法2
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
## 子から親への通信
### 子コンポーネント：
```
<template>
  <button @click="sendMessage">親に通知する</button>
</template>

<script>
export default {
  methods: {
    sendMessage() {
      this.$emit('message-sent', 'こんにちは、親コンポーネント！');
    },
  },
}
</script>
```
### 親コンポーネント：
```
<template>
  <div>
    <ChildComponent @message-sent="handleMessage" />
    <p>受信メッセージ: {{ message }}</p>
  </div>
</template>

<script>
import ChildComponent from './ChildComponent.vue';

export default {
  components: { ChildComponent },
  data() {
    return {
      message: '',
    };
  },
  methods: {
    handleMessage(msg) {
      this.message = msg;
    },
  },
};
</script>
```
## 双方向バインディング
### 親コンポーネント：
```
<template>
  <div>
    <ChildComponent v-model="message" />
    <p>親のメッセージ: {{ message }}</p>
  </div>
</template>

<script>
import ChildComponent from './ChildComponent.vue';

export default {
  components: { ChildComponent },
  data() {
    return {
      message: '初期メッセージ',
    };
  },
}
</script>
```
### 子コンポーネント：
```
<template>
  <input type="text" :value="modelValue" @input="$emit('update:modelValue', $event.target.value)" />
</template>

<script>
export default {
  props: {
    modelValue: String,
  },
}
</script>
```
## 親子間の直接的なメソッド呼び出し
### 子コンポーネント：
```
<template>
  <p>メソッドが呼び出されました！</p>
</template>

<script>
export default {
  methods: {
    logMessage() {
      console.log('子コンポーネントのメソッドが実行されました');
    },
  },
};
</script>
```
### 親コンポーネント：
```
<template>
  <div>
    <ChildComponent ref="child" />
    <button @click="callChildMethod">子のメソッドを呼び出す</button>
  </div>
</template>

<script>
import ChildComponent from './ChildComponent.vue';

export default {
  components: { ChildComponent },
  methods: {
    callChildMethod() {
      this.$refs.child.logMessage();
    },
  },
}
</script>
```
## VuexやPiniaを使った状態管理（補足）
### 親子間の通信が複雑化したり、複数のコンポーネント間で状態を共有したい場合は、状態管理ツール（VuexやPinia）を利用するのが便利です。
