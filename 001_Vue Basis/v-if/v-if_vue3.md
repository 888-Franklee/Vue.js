
# Vue 3: `v-if` 徹底攻略ガイド

## ✅`v-if` とは？

`v-if` は、Vue 3における**条件付きレンダリング**を行うためのディレクティブです。  
条件が `true` の場合のみ、その要素またはコンポーネントがDOMに描画されます。  
条件が `false` の場合、DOMツリー上にその要素は存在しません。

---

## ✅基本的な使い方

```vue
<template>
  <div v-if="isVisible">こんにちは、世界！</div>
</template>

<script setup>
import { ref } from 'vue'

const isVisible = ref(true)
</script>
```

---

## ✅`v-else` と `v-else-if`

### `v-else`

```vue
<template>
  <div v-if="isLoggedIn">ようこそ！</div>
  <div v-else>ログインしてください。</div>
</template>
```

### `v-else-if`

```vue
<template>
  <div v-if="status === 'loading'">読み込み中...</div>
  <div v-else-if="status === 'success'">成功しました！</div>
  <div v-else-if="status === 'error'">エラーが発生しました。</div>
  <div v-else>未知の状態です。</div>
</template>
```

---

## ✅`v-if` と `<template>` タグの併用

複数要素を一括で条件付きレンダリングする場合、`<template>`タグを使います。

```vue
<template>
  <template v-if="showContent">
    <h1>タイトル</h1>
    <p>これは本文です。</p>
  </template>
</template>
```

※ `<template>`自体はDOMに現れません。

---

## ✅`v-if` と `v-show` の違い

| 特徴      | v-if                           | v-show                        |
|:----------|:-------------------------------|:------------------------------|
| 初期コスト | 高い（条件ごとにDOM操作）         | 低い（単にCSSで表示/非表示）   |
| 実行コスト | 低頻度な切り替えに向いている         | 高頻度な切り替えに向いている     |
| 仕組み    | DOM自体を追加・削除する             | display: none を切り替える        |

- 頻繁に表示・非表示を切り替えるなら `v-show` が向いています。
- 状態が稀にしか変わらないなら `v-if` を選びましょう。

---

## ✅高度な話題

### 1. `v-if` と `key` の使い方

動的にコンポーネントを切り替える場合、`key`を付けて正しいライフサイクルを保証するのが推奨されます。

```vue
<template>
  <component :is="currentView" :key="currentView"></component>
</template>
```

- `key`を指定しないと、Vueはコンポーネントを再利用してしまい、意図しない動作になることがあります。
- `key`を与えることで、正しくマウント・アンマウントが発生します。

---

### 2. `v-if` と コンポーネントライフサイクル

- `v-if` でコンポーネントが初めて表示されるとき、**`onMounted`** が呼ばれます。
- 再び `false` になった場合、そのコンポーネントは破棄され、**`onUnmounted`** が呼ばれます。

これを利用して、リソース管理（WebSocket接続やタイマー解除など）を適切に行うことができます。

---

### 3. パフォーマンスチューニング

- **多くの`v-if`があると初期レンダリングが重くなる**ので注意。
- 可能なら事前フィルタリングして、必要な要素だけをv-ifで出すように設計しましょう。
- コンポーネント単位で条件を切り出すとさらに効率的。

---

### 4. `v-if` と 非同期処理

非同期にデータを取得して表示切り替えする場合は、ローディング状態を管理するのが重要です。

```vue
<template>
  <div v-if="isLoading">読み込み中...</div>
  <div v-else>{{ userData.name }}</div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const isLoading = ref(true)
const userData = ref(null)

onMounted(async () => {
  const res = await fetch('/api/user')
  userData.value = await res.json()
  isLoading.value = false
})
</script>
```

---

### 5. 遅延レンダリング（Lazy Rendering）テクニック

初期表示で必要ないものは、`v-if`と合わせて**Intersection Observer API**と組み合わせると、さらに効率的です。

```vue
<script setup>
import { ref, onMounted } from 'vue'

const show = ref(false)

onMounted(() => {
  const observer = new IntersectionObserver(([entry]) => {
    if (entry.isIntersecting) {
      show.value = true
      observer.disconnect()
    }
  })
  observer.observe(document.querySelector('#lazy-content'))
})
</script>

<template>
  <div id="lazy-content">
    <div v-if="show">遅延ロードされたコンテンツ</div>
  </div>
</template>
```

---

### 6. リアクティブ変数の罠

- `v-if` で使う変数がリアクティブ（`ref`や`reactive`）でないと、Vueは更新を検知できません。
- 普通のJavaScript変数だと表示が変わらないので注意！

間違い例：

```vue
<script setup>
let isVisible = true // ❌ refを使うべき
</script>
```

正しい例：

```vue
<script setup>
import { ref } from 'vue'

const isVisible = ref(true) // ⭕
</script>
```

---

## ✅まとめ

- `v-if`は条件に応じたDOM操作を担当。
- 頻繁に切り替わるなら`v-show`を使う。
- `key`を適切に使い、正しいコンポーネントライフサイクルを維持する。
- パフォーマンスを意識し、非同期・遅延レンダリングと組み合わせるとさらに効率的。


