# v-model
## 単純な双方向バインディング
```
<template>
  <div>
    <input v-model="message" placeholder="メッセージを入力してください" />
    <p>入力したメッセージ: {{ message }}</p>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const message = ref('')
</script>
```
## 複数のプロパティをバインド
### Vue3では、1つのコンポーネントで複数の v-model を使用できます。これにより、異なるプロパティを個別にバインドできます。
```
<template>
  <custom-input v-model:title="title" v-model:content="content" />
  <p>タイトル: {{ title }}</p>
  <p>内容: {{ content }}</p>
</template>

<script setup>
import { ref } from 'vue';
import CustomInput from './CustomInput.vue';

const title = ref('');
const content = ref('');
</script>
```
###
CustomInput.vue
```
<template>
  <div>
    <input v-model="localTitle" placeholder="タイトル" />
    <textarea v-model="localContent" placeholder="内容"></textarea>
  </div>
</template>

<script setup>
import { ref, watch } from 'vue';

const localTitle = ref('');
const localContent = ref('');

export default {
  props: ['modelValue', 'modelValue:title', 'modelValue:content'],
  emits: ['update:title', 'update:content'],
};
</script>
```
## 修飾子の使用
### .trim 修飾子（入力値の先頭や末尾の空白を自動的に削除します。）
```
<template>
  <input v-model.trim="username" placeholder="ユーザー名を入力" />
</template>

<script setup>
import { ref } from 'vue'

const username = ref('')
</script>
```
## カスタムコンポーネントでの v-model
### 親コンポーネント
```
<template>
  <custom-input v-model="value" />
  <p>入力した値: {{ value }}</p>
</template>

<script setup>
import { ref } from 'vue';
import CustomInput from './CustomInput.vue';

const value = ref('');
</script>
```
### 子コンポーネント (CustomInput.vue)
```
<template>
  <input :value="modelValue" @input="updateValue" />
</template>

<script setup>
defineProps(['modelValue']);
defineEmits(['update:modelValue']);

const updateValue = (event) => {
  emit('update:modelValue', event.target.value);
};
</script>
```
