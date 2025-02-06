# 参考

## 【HTML 属性 for】  
### for 属性は <label> と <output> で利用できる属性です。 <label> 要素上で使用された場合、このラベルが説明するフォーム要素を示します。 <output> 要素上で使用された場合、その出力欄で使用される値を表す要素間の関係を明示的に示すことができます。
```
<label for="username">Your name</label> <input type="text" id="username" />
```
<https://developer.mozilla.org/ja/docs/Web/HTML/Attributes/for>

## 【HTML 属性 disabled】
### disabled は論理属性で、存在する場合、その要素は変更不可、フォーカス不可、フォームへの送信不可となります。ユーザーはそのコントロールやフォームコントロールの子孫を編集したり、フォーカスしたりすることができません。

<https://developer.mozilla.org/ja/docs/Web/HTML/Attributes/disabled>

## 【HTMLのselectタグ】
```
<label for="pet-select">Choose a pet:</label>
<select id="pet-select">
  <option value="">--Please choose an option--</option>
  <option value="dog">Dog</option>
  <option value="cat">Cat</option>
  <option value="hamster">Hamster</option>
  <option value="parrot">Parrot</option>
  <option value="spider">Spider</option>
  <option value="goldfish">Goldfish</option>
</select>
```
<https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/option>

## 【v-forの基本】
### v-for は、配列やオブジェクトを繰り返し処理して要素を生成するためのディレクティブです。v-for="(value, key) in object" の形で使われ、オブジェクトや配列の中身を効率よくループ処理できます。

#### 1.配列の場合
```
<ul>
  <li v-for="item in items" :key="item.id">
    {{ item }}
  </li>
</ul>
```
#### 2.オブジェクトの場合
```
<ul>
  <li v-for="(value, key) in object" :key="key">
    {{ key }}: {{ value }}
  </li>
</ul>
```
### 3.v-forのkey　
### 共通の同じ親を持つ子は、ユニークなキーを持つ必要があります。キーが重複するとレンダリングエラーになります。v-for と組み合わせるのが最も一般的な使用例です:
```
<ul>
  <li v-for="item in items" :key="item.id">...</li>
</ul>
```
<https://cn.vuejs.org/api/built-in-special-attributes>

