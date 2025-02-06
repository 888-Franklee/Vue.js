<template>
    <div class="container">
      <h1>日本の都道府県</h1>
      <label for="regionSelect">地方を選択</label>
      <select id="regionSelect" v-model="selectedRegion" @change="updateOutput">
        <option value="" disabled>地方を選択してください</option>
        <option v-for="(prefectures, region) in japanRegions" :key="region" :value="region">
          {{ region }}
        </option>
      </select>
      <div class="output">
        <strong v-if="selectedRegion">{{ selectedRegion }}</strong>
        <div v-if="selectedRegion">{{ japanRegions[selectedRegion]?.join('、') }}</div>
        <div v-else>地方を選択してください</div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        japanRegions: {
          "北海道地方": ["北海道"],
          "東北地方": ["青森県", "岩手県", "宮城県", "秋田県", "山形県", "福島県"],
          "関東地方": ["茨城県", "栃木県", "群馬県", "埼玉県", "千葉県", "東京都", "神奈川県"],
          "中部地方": ["新潟県", "富山県", "石川県", "福井県", "山梨県", "長野県", "岐阜県", "静岡県", "愛知県"],
          "近畿地方": ["三重県", "滋賀県", "京都府", "大阪府", "兵庫県", "奈良県", "和歌山県"],
          "中国地方": ["鳥取県", "島根県", "岡山県", "広島県", "山口県"],
          "四国地方": ["徳島県", "香川県", "愛媛県", "高知県"],
          "九州地方": ["福岡県", "佐賀県", "長崎県", "熊本県", "大分県", "宮崎県", "鹿児島県", "沖縄県"]
        },
        selectedRegion: ""
      };
    },
    methods: {
      updateOutput() {
        if (this.selectedRegion) {
          alert(`${this.selectedRegion}が選択されました！`)
        } else {
          alert("地方を選択してください！")
        }
      }
    }
  };
  </script>
  
  <style>
  body {
    margin: 0;
    padding: 0;
    font-family: Arial, sans-serif;
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    background: linear-gradient(135deg, #a825ea, #ba81cb);
    background-image: url('./assets/nihon.png');
    background-position: center;
    background-repeat: no-repeat;
    background-size: contain;
  }
  
  .container {
    background: hsl(240, 20%, 97%);
    border-radius: 12px;
    box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
    padding: 25px;
    width: 360px;
    text-align: center;
  }
  
  h1 {
    color: #da1515;
    font-size: 22px;
    margin-bottom: 20px;
  }
  
  select {
    width: 100%;
    padding: 10px;
    font-size: 16px;
    border-radius: 6px;
    border: 1px solid #ddd;
    outline: none;
    transition: border-color 0.3s;
  }
  select:focus {
    border-color: #1976d2;
  }
  
  .output {
    margin-top: 20px;
    padding: 15px;
    background: #f5f5f5;
    border-radius: 8px;
    border: 1px solid #ddd;
    max-height: 300px;
    overflow-y: auto;
    font-size: 16px;
    text-align: left;
    white-space: pre-wrap;
    color: #444;
  }
  .output strong {
    color: #5249dc;
  }
  
  .output::-webkit-scrollbar {
    width: 8px;
  }
  .output::-webkit-scrollbar-thumb {
    background-color: #aaa;
    border-radius: 4px;
  }
  .output::-webkit-scrollbar-thumb:hover {
    background-color: #888;
  }
  </style>
  