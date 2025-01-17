# refの基本的な使い方

## 1. リアクティブな値の管理
```
<template>
  <div>
    <p>カウント: {{ count }}</p>
    <button @click="increment">増加</button>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const count = ref(0)

const increment = () => {
  count.value++; // 値を更新
};
</script>
```
## 2. 配列やオブジェクトのリアクティブ化
### 配列
```
<template>
  <div>
    <button @click="addItem">アイテムを追加</button>
    <ul>
      <li v-for="(item, index) in items" :key="index">{{ item }}</li>
    </ul>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const items = ref([])

const addItem = () => {
  items.value.push(`Item ${items.value.length + 1}`);
};
</script>
```
### オブジェクト
```
<template>
  <div>
    <p>名前: {{ user.name }}</p>
    <button @click="updateName">名前を更新</button>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const user = ref({
  name: 'John',
  age: 30,
});

const updateName = () => {
  user.value.name = 'Jane';
};
</script>
```

## 3. DOM要素への参照
```
<template>
  <div>
    <input ref="inputRef" type="text" />
    <button @click="focusInput">フォーカスを当てる</button>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const inputRef = ref(null)

const focusInput = () => {
  inputRef.value.focus(); // DOM要素にアクセスしてフォーカス
};
</script>
```

## 4. computedとの組み合わせ
```
<template>
  <div>
    <p>カウント: {{ count }}</p>
    <p>ダブルカウント: {{ doubleCount }}</p>
    <button @click="increment">増加</button>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const count = ref(0)

const doubleCount = computed(() => count.value * 2); 

const increment = () => {
  count.value++;
};
</script>
```
## 5. watchとの組み合わせ
```
<template>
  <div>
    <input v-model="name" placeholder="名前を入力してください" />
    <p>名前: {{ name }}</p>
  </div>
</template>

<script setup>
import { ref, watch } from 'vue'

const name = ref('')

watch(name, (newVal, oldVal) => {
  console.log(`名前が変更されました: ${oldVal} -> ${newVal}`);
});
</script>
```

## 6. フォームバリデーションの例
```
<template>
  <div>
    <form @submit.prevent="handleSubmit">
      <label>
        名前:
        <input v-model="name" type="text" />
      </label>
      <p v-if="nameError">{{ nameError }}</p>

      <label>
        年齢:
        <input v-model="age" type="number" />
      </label>
      <p v-if="ageError">{{ ageError }}</p>

      <button type="submit">送信</button>
    </form>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const name = ref('')
const age = ref(null)

const nameError = ref('')
const ageError = ref('')

const handleSubmit = () => {
  nameError.value = name.value ? '' : '名前を入力してください';
  ageError.value = age.value > 0 ? '' : '正しい年齢を入力してください';

  if (!nameError.value && !ageError.value) {
    alert(`名前: ${name.value}, 年齢: ${age.value}`);
  }
};
</script>
```
