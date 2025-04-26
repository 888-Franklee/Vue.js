<template>
    <div class="container">
      <h3>戦国</h3>
      <div
        v-for="(classGroup, classIndex) in classList"
        :key="classIndex"
        class="class-group"
      >
        <h4>クラス{{ classIndex + 1 }}：</h4>
        <ul>
          <li
            v-for="(student, studentIndex) in classGroup"
            :key="`${classIndex}-${studentIndex}`"
          >
            {{ student }}
          </li>
        </ul>
      </div>
    </div>
</template>
  
  <script setup>
  const classList = [
    ["織田", "豊臣", "秀吉"],
    ["武田", "上杉", "毛利"],
    ["黒田", "勝家", "明智"],
  ];
  </script>
  
  <style scoped>
  .container {
    padding: 20px;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    background-color: #fdfcff;
    text-align: center; /* 全体の文字を中央寄せ */
  }
  
  h3 {
    font-size: 24px;
    color: #5a189a;
    border-bottom: 2px solid #9d4edd;
    padding-bottom: 5px;
    margin-bottom: 15px;
  }
  
  h4 {
    font-size: 18px;
    color: #7b2cbf;
    margin-top: 20px;
  }
  
  ul {
    list-style: none;
    padding-left: 0;
  }
  
  li {
    background-color: #e0aaff;
    margin: 6px auto; /* 中央寄せ＋縦方向に隙間 */
    padding: 8px 12px;
    border-radius: 6px;
    transition: background-color 0.3s;
    cursor: pointer;
    display: inline-block; /* テキストを中央に */
    min-width: 100px;
  }
  
  li:hover {
    background-color: #c77dff;
    color: white;
  }
  </style>
  