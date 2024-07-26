# 4. 人生不是兜圈就是在做選擇

## 什麼是迴圈、什麼是判斷

我們的生活中，總是在重複一樣的事情，而每一次重複時做出不同的選擇，導致不同的結果。這就是迴圈與判斷。
程式沒有像是人生一樣複雜，只要告訴它要怎麼兜圈子、滿足怎樣的條件就不兜了，它就會乖乖的照著你的指示做。

### 迴圈

迴圈就是重複做一件事情，直到滿足某個條件才停止。在 JS 中，迴圈有三種，分別是 `for`、`while`、`do...while`。

#### for

`for` 迴圈是最常見的迴圈，它的結構如下：

```javascript
for (初始值; 條件; 遞增) {
  // 做的事情
}
```

`初始值` 是迴圈開始的值，`條件` 是迴圈繼續的條件，`遞增` 是迴圈每次增加的值。

```javascript
for (let i = 0; i < 10; i++) {
  console.log(i);
}
// 會印出 0, 1, 2, 3, 4, 5, 6, 7, 8, 9，第 10 次時條件不成立，迴圈停止
```

#### while

`while` 迴圈是當條件成立時就會一直重複做事情，它的結構如下：

```javascript
while (條件) {
  // 做的事情
}
```

```javascript
let i = 0;
while (i < 10) {
  console.log(i);
  i++;
}
// 會印出 0, 1, 2, 3, 4, 5, 6, 7, 8, 9，第 10 次時條件不成立，迴圈停止
```

所以你可以很簡單的搞出一個迴圈炸彈

```javascript
while (true) {
  console.log('炸裂吧，記憶體');
}

// 這個迴圈會一直重複印出 '炸裂吧，記憶體'，直到你的瀏覽器記憶體爆炸
// 很危險不要這樣玩
```

#### do...while

`do...while` 迴圈是先做一次事情，再判斷條件是否成立，如果成立就繼續做，不成立就停止，它的結構如下：

```javascript
do {
  // 做的事情
} while (條件)
```

```javascript
let i = 0;
do {
  console.log(i);
  i++;
} while (i < 10);
// 會印出 0, 1, 2, 3, 4, 5, 6, 7, 8, 9，第 10 次時條件不成立，迴圈停止
```

反過來，如果 i 一開始就是 10，則：

```javascript
let i = 10;
do {
  console.log(i);
  i++;
} while (i < 10);
// 會先印出 10，第 1 次判斷時條件就不成立，迴圈停止
```

### 判斷

判斷就是當滿足某個條件時，做某件事情。在 JS 中，判斷有 `if`、`else if`、`else`。

#### if

`if` 是最基本的判斷式，當條件成立時，就會執行裡面的程式碼，結構如下：

```javascript
if (條件) {
  // 做的事情
}
```

```javascript
let i = 10;
if (i < 10) {
  console.log('i 小於 10');
}
```

#### else

`else` 是當所有條件都不成立時，執行的程式碼，結構如下：

```javascript
if (條件) {
  // 做的事情
} else {
  // 以上皆非
}
```

```javascript
let i = 10;
if (i < 10) {
  console.log('i 小於 10');
} else {
  console.log('i 大於等於 10');
}
```

#### else if

`else if` 是當 `if` 的條件不成立時，再判斷下一個條件，結構如下：

```javascript
if (條件) {
  // 做的事情
} else if (條件) {
  // 做的事情
}else{
  // 以上皆非
}
```

要注意的是，`else if` 可以有多個，但只會執行第一個條件成立的程式碼。
而且一定要有 else，否則當所有條件都不成立時，程式會出錯。

```javascript
let i = 10;
if (i < 10) {
  console.log('i 小於 10');
} else if (i === 10) {
  console.log('i 等於 10');
} else {
  console.log('i 大於 10');
}
```

#### switch

`switch` 是當有多個條件時，可以使用 `switch` 來判斷，類似一個管線，當條件符合時，就會執行該條件的程式碼，結構如下：

```javascript
switch (變數) {
  case 條件1:
    // 做的事情
    break;
  case 條件2:
    // 做的事情
    break;
  default:
    // 以上皆非
}
```

```javascript
// 假設這是一個硬幣分類器，總共有 3 種硬幣，1 元、5 元、10 元
let i = 10;
switch (i) {
  case 1:
    console.log('這是 1 元');
    break;
  case 5:
    console.log('這是 5 元');
    break;
  case 10:
    console.log('這是 10 元');
    break;
  default:
    console.log('這不是硬幣');
}
```

`case`的條件可以是字串、數字、布林值，只要傳入的變數符合其中一個條件，就會執行該條件的程式碼。
但要注意的是，如果沒有加上 `break`，程式會繼續執行下一個條件的程式碼，所以一定要加上 `break`。
`default`是當所有條件都不成立時，執行的程式碼。

#### 三元運算子

三元運算子是一個簡單的判斷式，當條件成立時，執行第一個程式碼，否則執行第二個程式碼，很常用於變數賦值的判斷

```javascript
條件 ? 程式碼1 : 程式碼2
```

```javascript
let gender = 'man';

// 判斷 gender 是不是 'man'，是的話 aaron = 'male'，否則 aaron = 'female'
let aaron = gender === 'man' ? 'male' : 'female'; 
console.log(man)
```

## 打在一起做撒尿牛丸吶笨蛋

當然了，邏輯跟迴圈是可以一起用的，這樣就可以做出很多很有趣的事情了。

```javascript
for (let i = 0; i < 10; i++) {
  if (i % 2 === 0) {
    console.log(i + ' 是偶數');
  } else {
    console.log(i + ' 是奇數');
  }
}
```

或是當作迴圈的終止條件

```javascript
let i = 0;
while (i < 10) {
  if (i === 5) {
    break;
  }
  console.log(i);
  i++;
}
```

程式就是一種樂高積木，你可以用不同的方式組合出不同的結果，只要你有想像力，你就可以做出很多很有趣的事情。

## 總結

到目前為止，我很單純的只提 JavaScript 的基本語法，除了講到提升(Hoisting)時必須提到 `Window` 之外，我都儘可能的不要提到 `Dom, Bom` 這類跟瀏覽器相關的東西，因為我希望你能夠先了解 JavaScript 的基本語法，再去了解瀏覽器的相關操作。