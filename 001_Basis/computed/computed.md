# computed
## 基本構文
```
import { ref, computed } from 'vue'

const count = ref(0)

const doubleCount = computed(() => count.value * 2);
```
## 読み取り専用のcomputed
```
<template>
  <div>
    <p>フルネーム: {{ fullName }}</p>
    <button @click="updateName">名前を変更</button>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const firstName = ref('太郎')
const lastName = ref('山田')

const fullName = computed(() => `${firstName.value} ${lastName.value}`)

const updateName = () => {
  firstName.value = '花子';
  lastName.value = '佐藤';
}
</script>
```
## 読み書き可能なcomputed
```
<template>
  <div>
    <p>フルネーム: {{ fullName }}</p>
    <input v-model="fullName" />
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const firstName = ref('太郎')
const lastName = ref('山田')

const fullName = computed({
  get: () => `${firstName.value} ${lastName.value}`, // 値を取得
  set: (newValue) => {
    const parts = newValue.split(' ');
    firstName.value = parts[0] || '';
    lastName.value = parts[1] || '';
  },
})
</script>
```
## computedのメリット
### 1.繰り返し使用されても再計算されず、依存データが変更された場合にのみ再評価されます。
### 2.テンプレート内で複雑な計算を避け、読みやすいコードを実現します。
### 3.どのデータに依存しているかが直感的にわかります。