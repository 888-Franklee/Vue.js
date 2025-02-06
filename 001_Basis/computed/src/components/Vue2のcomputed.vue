<script>
export default {
  data() {
    return {
      count: 0,
    };
  },
  computed: {
    doubleCount() {
      return this.count * 2;
    },
  },
};
</script>

<template>
  <div>
    <p>現在の値: {{ count }}</p>
    <p>計算後の値: {{ doubleCount }}</p>
    <button @click="count++">インクリメント</button>
  </div>
</template>
