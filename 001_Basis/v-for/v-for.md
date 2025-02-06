# v-for

## 基本構文
```
<template>
  <ul>
    <li v-for="item in items" :key="item.id">
      {{ item.name }}
    </li>
  </ul>
</template>

<script setup>
import { ref } from 'vue'

const items = ref([
  { id: 1, name: 'りんご' },
  { id: 2, name: 'みかん' },
  { id: 3, name: 'ぶどう' },
])
</script>
```
```
<template>
  <ul>
    <li v-for="item in items" :key="item.id">
      {{ item.name }}
    </li>
  </ul>
</template>

<script>
export default {
  data() {
    return {
      items: [
        { id: 1, name: 'りんご' },
        { id: 2, name: 'みかん' },
        { id: 3, name: 'ぶどう' },
      ],
    };
  },
};
</script>
```
## オブジェクトのループ
```
<template>
  <ul>
    <li v-for="(value, key) in user" :key="key">
      {{ key }}: {{ value }}
    </li>
  </ul>
</template>

<script setup>
import { reactive } from 'vue'

const user = reactive({
  name: '太郎',
  age: 25,
  location: '東京',
})
</script>
```
```
<template>
  <ul>
    <li v-for="(value, key) in user" :key="key">
      {{ key }}: {{ value }}
    </li>
  </ul>
</template>

<script>
export default {
  data() {
    return {
      user: {
        name: '太郎',
        age: 25,
        location: '東京',
      },
    };
  },
};
</script>
```
## ネストしたループ
```
<template>
  <div v-for="(group, groupIndex) in groups" :key="groupIndex">
    <h3>グループ {{ groupIndex + 1 }}</h3>
    <ul>
      <li v-for="(item, index) in group.items" :key="index">
        {{ item }}
      </li>
    </ul>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const groups = ref([
  { items: ['A1', 'A2', 'A3'] },
  { items: ['B1', 'B2'] },
  { items: ['C1', 'C2', 'C3', 'C4'] },
])
</script>
```
```
<template>
  <div v-for="(group, groupIndex) in groups" :key="groupIndex">
    <h3>グループ {{ groupIndex + 1 }}</h3>
    <ul>
      <li v-for="(item, index) in group.items" :key="index">
        {{ item }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      groups: [
        { items: ['A1', 'A2', 'A3'] },
        { items: ['B1', 'B2'] },
        { items: ['C1', 'C2', 'C3', 'C4'] },
      ],
    };
  },
};
</script>
```
## Vue 3特有の改良点
### Composition APIとの統合：v-for は Composition API で定義したデータも直接操作できます。
```
<template>
  <ul>
    <li v-for="item in items" :key="item.id">{{ item.name }}</li>
  </ul>
</template>

<script>
import { ref } from 'vue';

export default {
  setup() {
    const items = ref([
      { id: 1, name: 'りんご' },
      { id: 2, name: 'みかん' },
      { id: 3, name: 'ぶどう' },
    ]);

    return { items };
  },
};
</script>
```
### Fragmentを活用したテンプレートの簡素化：v-for で複数要素を直接ループしてもラッパー要素が不要です。
```
<template>
  <template v-for="item in items">
    <h1 :key="item.id">{{ item.name }}</h1>
    <p :key="'desc-' + item.id">{{ item.description }}</p>
  </template>
</template>
```
## 注意点
### キーの一意性：キー (:key) は必ずユニークである必要があります。同じキーが複数存在するとバグの原因になります。
### 非同期データの扱い：非同期でデータを取得する場合も再描画を効率化するためにキーを正しく指定してください。