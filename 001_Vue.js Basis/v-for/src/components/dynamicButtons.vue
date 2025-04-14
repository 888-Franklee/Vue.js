<template>
  <div class="container">
    <h3>DynamicButtons</h3>
    <div class="button-group">
      <button v-for="(label, index) in button" :key="index" @click="handleClick(label)">
        {{ label }}
      </button>
    </div>
  </div>
</template>

<script setup>
const button = ["Button1", "Button2", "Button3"]
const handleClick = (label) => {
  alert(`You clicked: ${label}`)
}
</script>

<style scoped>
/* ページ全体の中央揃えのための親コンテナ */
.container {
  display: flex; /* フレックスボックスを使う */
  flex-direction: column; /* 子要素を縦に並べる */
  align-items: center; /* 水平方向の中央揃え */
  justify-content: center; /* 垂直方向の中央揃え（高さが十分あるとき） */
  min-height: 100vh; /* 画面全体の高さを確保 */
  text-align: center; /* テキストを中央揃えに */
}

/* ボタンのグループ（v-for部分）にも中央配置を意識 */
.button-group {
  display: flex; /* 横並びに */
  gap: 16px; /* ボタン間のスペースを16pxに */
  flex-wrap: wrap; /* 小さい画面では折り返すように */
  justify-content: center; /* ボタン群も中央に */
  margin-top: 20px; /* タイトルとボタンの間にスペース */
}

/* ボタンのスタイル */
button {
  padding: 10px 20px;
  border: none;
  border-radius: 8px;
  background-color: #7c3aed;
  color: white;
  font-size: 16px;
  cursor: pointer;
  transition: background-color 0.3s ease, transform 0.2s ease;
}

/* ホバー時のエフェクト */
button:hover {
  background-color: #a78bfa;
  transform: scale(1.05);
}

/* フォーカス（キーボード操作）の視認性 */
button:focus {
  outline: 2px solid #c4b5fd;
  outline-offset: 2px;
}
</style>
