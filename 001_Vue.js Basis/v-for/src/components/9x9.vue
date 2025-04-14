<template>
  <div>
    <div v-for="i in 9" :key="i">
      <span v-for="j in i" :key="j">{{ j }}×{{ i }}={{ j * i }}</span>
    </div>
  </div>
</template>

<script setup>
// 特にスクリプトの記述は不要です（ロジックはテンプレート内で完結）
</script>

<style scoped>
span {
  display: inline-block; /* インラインブロック：横並びになりつつ、幅や高さの指定が可能 */
  width: 100px; /* 各セルの幅を100ピクセルに固定 */
  padding: 5px 10px; /* 上下5px、左右10pxの内側余白 */
  border: 1px solid purple; /* 紫色の1ピクセル実線のボーダー */
  margin: 4px; /* 要素同士の間に4ピクセルの外側余白を追加 */
  border-radius: 5px; /* 角を5ピクセルだけ丸くして柔らかい印象に */
  box-shadow: 2px 2px 2px purple; /* 紫色の影を付けて立体感を出す */
  text-align: center; /* テキストを中央揃えにする */
  transition: background-color 0.3s ease; /* 背景色の変更時に0.3秒のアニメーションを適用 */
}

span:hover {
  background-color: #a681f6; /* ホバー時（マウスが上に乗ったとき）の背景色を淡い紫に変更 */
}
</style>
