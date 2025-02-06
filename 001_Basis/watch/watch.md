# watch
## 単一のデータを監視
```
<template>
  <div>
    <p>現在のカウント: {{ count }}</p>
    <button @click="increment">カウントを増やす</button>
  </div>
</template>

<script setup>
import { ref, watch } from 'vue'

const count = ref(0)

watch(count, (newValue, oldValue) => {
  console.log(`カウントが変更されました: ${oldValue} → ${newValue}`);
})

const increment = () => {
  count.value++;
}
</script>
```
## 複数データの監視
```
<template>
  <div>
    <p>名前: {{ firstName }} {{ lastName }}</p>
    <button @click="changeName">名前を変更</button>
  </div>
</template>

<script setup>
import { ref, watch } from 'vue'

const firstName = ref('太郎')
const lastName = ref('山田')

watch([firstName, lastName], ([newFirst, newLast], [oldFirst, oldLast]) => {
  console.log(`名前が変更されました: ${oldFirst} ${oldLast} → ${newFirst} ${newLast}`);
})

const changeName = () => {
  firstName.value = '花子';
  lastName.value = '佐藤';
}
</script>
```
## 深い監視（オブジェクトの中身を監視）
### オブジェクトのプロパティ（user.name や user.age）の変化を監視する場合は、deep: true オプションを使います。
```
<template>
  <div>
    <p>ユーザー情報:</p>
    <p>名前: {{ user.name }}</p>
    <p>年齢: {{ user.age }}</p>
    <button @click="updateAge">年齢を増やす</button>
  </div>
</template>

<script setup>
import { reactive, watch } from 'vue'

const user = reactive({
  name: '太郎',
  age: 25,
});

watch(
  user,
  (newValue, oldValue) => {
    console.log('ユーザー情報が変更されました:', oldValue, '→', newValue);
  },
  { deep: true }
);

const updateAge = () => {
  user.age++;
};
</script>
```
## 特定のプロパティを精確に監視
```
<template>
  <div>
    <p>ユーザー名: {{ user.name }}</p>
    <p>年齢: {{ user.age }}</p>
    <button @click="updateName">名前を変更</button>
    <button @click="updateAge">年齢を変更</button>
  </div>
</template>

<script setup>
import { reactive, watch } from 'vue';

const user = reactive({
  name: '太郎',
  age: 25,
})

watch(
  () => user.name, // 監視するプロパティを指定
  (newValue, oldValue) => {
    console.log(`名前が変更されました: ${oldValue} → ${newValue}`);
  }
)

const updateName = () => {
  user.name = '花子';
}

const updateAge = () => {
  user.age++;
}
</script>
```
## 初回実行とウォッチャーの停止
### immediate: true オプションを使うと、監視開始時に即座にコールバックを実行します。また、watch の戻り値を使えば監視を停止することもできます。
```
<template>
  <div>
    <p>現在のカウント: {{ count }}</p>
    <button @click="increment">カウントを増やす</button>
    <button @click="stopWatcher">ウォッチャーを停止</button>
  </div>
</template>

<script setup>
import { ref, watch } from 'vue'

const count = ref(0)

const stop = watch(
  count,
  (newValue, oldValue) => {
    console.log(`カウントが変更されました: ${oldValue} → ${newValue}`);
  },
  { immediate: true } 
)

const increment = () => {
  count.value++;
}

const stopWatcher = () => {
  stop();
  console.log('ウォッチャーを停止しました');
}
</script>
```
