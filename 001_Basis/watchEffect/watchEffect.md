# watchEffect
### Vue 3 の watchEffect は、リアクティブな依存関係を自動的に追跡して監視する方法です。依存するデータが変更されるたびに登録されたコールバック関数が実行されます。watch と異なり、特定のデータを明示的に指定する必要はありません。

## 基本構文
```
import { ref, watchEffect } from 'vue'

const count = ref(0)

watchEffect(() => {
  console.log(`現在のカウント: ${count.value}`);
})
```
## 簡単なカウント追跡
```
<template>
  <div>
    <p>カウント: {{ count }}</p>
    <button @click="increment">増加</button>
  </div>
</template>

<script setup>
import { ref, watchEffect } from 'vue'

const count = ref(0)

watchEffect(() => {
  console.log(`現在のカウント: ${count.value}`);
})

const increment = () => {
  count.value++;
}
</script>
```
##  複数の依存関係を追跡
```
<template>
  <div>
    <p>名前: {{ firstName }} {{ lastName }}</p>
    <button @click="changeName">名前を変更</button>
  </div>
</template>

<script setup>
import { ref, watchEffect } from 'vue'

const firstName = ref('太郎')
const lastName = ref('山田')

watchEffect(() => {
  console.log(`フルネーム: ${firstName.value} ${lastName.value}`);
})

const changeName = () => {
  firstName.value = '花子';
  lastName.value = '佐藤';
}
</script>
```
## watchEffect と watch の違い

|特徴 | watchEffect | watch |
|:--- | :--- | :--- |
|依存関係の指定 | 自動的に追跡 | 明示的に指定|
|初回実行 | 即時実行 | デフォルトでは初回実行されない（設定可能）|
|監視対象の範囲 | コールバック内で使用された全て | 明示的に指定したデータのみ|
|適用場面| シンプルで広範な依存関係の監視 | 特定のデータ変更を効率的に監視|
## 注意点
### 1.不要な再実行を防ぐ
### watchEffect は内部の依存関係が変更されるたびに再実行されるため、パフォーマンスに影響する場合があります。重い処理が含まれる場合は、watch で依存関係を明示的に指定するほうが良いです。
### 2.クリーンアップ関数の利用
### 副作用をクリーンアップする必要がある場合、onInvalidate を使用できます。
