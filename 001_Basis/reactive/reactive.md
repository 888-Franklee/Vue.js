# reactiveの基本的な使い方

## 1. reactive のインポート
```
import { reactive } from 'vue';
```
## 2. リアクティブデータの作成
```
<script setup>
import { reactive } from 'vue';

// reactiveでリアクティブデータを作成
const state = reactive({
  count: 0,
  message: 'こんにちは！',
  items: []
});

// データを操作する関数
const increment = () => {
  state.count++;
};
</script>

<template>
  <div>
    <p>カウント: {{ state.count }}</p>
    <button @click="increment">増加</button>
    <p>{{ state.message }}</p>
  </div>
</template>
```

## 3. reactiveの特徴
+ reactive はオブジェクトや配列全体をリアクティブにします。
+ プリミティブ値（数値や文字列など）には ref を使用することを推奨。
+ reactive でラップされたオブジェクトや配列の変更を Vue が自動的に追跡し、UI を更新します。
+ オブジェクト内のネストされたプロパティもリアクティブになります。

## 4. reactiveの注意点
+ 単一のプリミティブ値（数値や文字列）の場合、reactive の代わりに ref を使います。
+ reactive を使用しても、関数や非オブジェクト型（プリミティブ）をそのままリアクティブにすることはできません。
+ JavaScript のプロキシを利用してリアクティブを実現しているため、一部のデータ操作（delete など）は特別な注意が必要です。

## 5.オブジェクトの操作
```
<script setup>
import { reactive } from 'vue';

const user = reactive({
  name: '太郎',
  age: 25,
  hobbies: ['読書', 'サッカー']
});

const addHobby = (hobby) => {
  user.hobbies.push(hobby);
};

const updateName = (newName) => {
  user.name = newName;
};
</script>

<template>
  <div>
    <p>名前: {{ user.name }}</p>
    <p>年齢: {{ user.age }}</p>
    <p>趣味: {{ user.hobbies.join(', ') }}</p>
    <button @click="addHobby('料理')">趣味を追加</button>
    <button @click="updateName('花子')">名前を変更</button>
  </div>
</template>

```
