<script setup>
const fruits = [
  "バナナ",
  "アップル",
  "林檎",
  "オレンジ",
  "ブドウ",
  "イチゴ",
  "メロン",
  "スイカ",
  "パイナップル",
  "キウイ",
  "桃",
  "さくらんぼ",
  "梨",
  "マンゴー",
  "ライチ",
  "ブルーベリー",
  "ラズベリー",
  "カキ",
  "グレープフルーツ",
  "アボカド",
  "ココナッツ"
]
</script>

<template>
  <ul>
    <li v-for="(fruit, index) in fruits" :key="fruit">
    {{index+1}}{{ fruit }}
    </li>
  </ul>
</template>