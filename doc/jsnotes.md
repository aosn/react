JavaScript Notes
===

概要
---

JavaScriptを体系的に学んだメンバーがいないため、基礎・要点や学習中に出た質疑をまとめる。
また周辺技術は多岐に渡るため、なるべくそれらを排除して簡潔なドキュメントを目指す。

### 型
- boolean
  - true, false

- number
  - `1`, `1.23`, `NaN`
  - 整数型は存在しない

- string
  - `"abc"`, `'abc'`, [ES2015] ``` `${new Date()}` ```
  - `"`, `'`に基本的に違いはない（片方が文字型だったりはしない）

- Array
  - ['a', 2, {}]

- Function
  - 第1級(first-class)オブジェクト
    - 名前付き関数
      ```js
      function double(x) { return 2 * x; };
      double(3); // 6
      ```

    - 無名関数
      ```js
      var double = function(x) { return 2 * x; };
      double(3); // 6
      ```

- Object
  - `{}`
  - e.g.
    ```js
    var obj = {
      p1: 123,
      p2: 'abc',
      p3: function() { return 'ppp'; }
    };
    obj.p1; // 123
    obj['p2']; // 'abc'
    obj.p3(); // 'ppp'
    ```

- null


### this
呼び出しコンテキスト

#### 1. `this === window`

```html
<!DOCTYPE html>
<html>
<body>
<script type="text/javascript">
alert(this.document === window.document); // true
</script>
</body>
</html>
```

#### 2. コンストラクタ関数での `this`

```js
function Apple() {
  this.color = 'red';
  this.tastes = 'sweet';
  this.eat = function() {
    alert('delicious!!');
  };
}
var apple = new Apple();
console.log(apple.color); // 'red'
console.log(apple.tastes); // 'sweet'
apple.eat(); // alert 'delicious!!'
```

#### 3. メソッド呼び出し

```js
function getTitle() {
  return this.document.title;
}
console.log(getTitle()); // this === window ページのタイトルが出力される

var obj = {
  document: {
    title: 'AWESOME TITLE!!'
  },
  getTitle: getTitle
};
console.log(obj.getTitle()); // 'AWESOME TITLE!!'
```

#### 4. `call`, `apply`

```js
function getName(prefix, postfix) {
  return prefix + this.name + postfix;
}
var dog = { name: 'Pochi' };
var cat = { name: 'Tama' };

console.log(getName.call(dog, 'Kawaii', 'Chan')); // 'KawaiiPochiChan'
console.log(getName.apply(cat, ['Goodbye', 'San'])); // 'GoodbyeTamaSan'
```

### 関数
### オブジェクト
### スコープ
### prototype
