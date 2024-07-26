# 3. 變數的型態（變態XD）與應用

上一個章節提到變數的宣告、定義，以及 var, function 的提升機制、變數的作用域等等，這一章節要來談談變數的型態。

首先，我們需要認知到一個事實：
> JavaScript 是一個很自由的語言，它不會強迫你去宣告變數的型態。
> 也就是說，你可以在宣告變數的時候不用指定型態。
> 而且在變數的生命週期中，這個變數的型態也可以隨時改變。
> 這樣的特性，讓 JS 在開發上更加的靈活。
> 但也因此，你會很痛苦。
> 因為實在是太髒了啊T^T

在 JavaScript 中，變數的型態可以分為基本型態（Primitive Type）和物件型態（Object Type）兩種。

## 基本型態（Primitive Type）

| 型態 | 描述 | 範例 |
| --- | --- | --- |
| Number | 數字，包括整數跟小數 | `var a = 123; console.log(a); // 123` |
| String | 字串 | `var a = 'Hello'; console.log(a); // Hello` |
| Boolean | 布林值，只會是 true or false | `var a = true; console.log(a); // true` |
| Undefined | 未定義的值 | `var a; console.log(a); // undefined` |
| Null | 空值 | `var a = null; console.log(a); // null` |

這裡要特別提一下 undefined 跟 null 的差別：
> undefined 是代表變數宣告了但沒有賦值，而 null 是代表變數有賦值，但值是空的。

其實這個 `null` 當初被設計時，是用來表示該變數是一個空的物件，但是後來發現這樣的設計有點問題，所以就變成了一個空值。
所以如果執行 `typeof null` 會發現它的型態是 `object`，這是一個歷史遺留問題，但如果修正這個問題可能會導致很多舊有的程式碼出問題，於是將錯就錯XD

但是當 undefined 跟 null 進行簡單比較時，會發現他們是相等的；型態比較才會不相等：
```javascript
console.log(undefined == null); // true
console.log(undefined === null); // false
```

這個小訣竅在判斷一個變數是否為 undefined 或 null 時很有用。

```javascript
var a;
if (!a) {
    console.log('a is undefined or null');
}
```

## 物件型態（Object Type）

物件型態是 JavaScript 中最重要的一個型態，因為 JavaScript 中的所有東西都是物件。

| 型態 | 描述 | 範例 |
| --- | --- | --- |
| Object | 物件 | `var a = {}; console.log(a); // {}` |
| Array | 陣列 | `var a = [1, 2, 3]; console.log(a); // [1, 2, 3]` |
| Function | 函式 | `var a = function() {}; console.log(a); // function() {}` |

### 陣列/數組 (Array)
Array 是一種特殊的物件，它的 key 是數字，而且有一些內建方法可以使用。

```javascript
var a = [1, 2, 3];
console.log(a[0]); // 1
console.log(a.length); // 3

a.push(4);
console.log(a); // [1, 2, 3, 4]

a.pop();
console.log(a); // [1, 2, 3]

a.shift();
console.log(a); // [2, 3]

a.unshift(1);
console.log(a); // [1, 2, 3]
```

### 函式 (Function)
Function 也是一種特殊的物件，它可以被當作參數傳遞，也可以被當作回傳值。
當然，Function 也可以被寫作變數。

```javascript

function add(a, b) {
    return a + b;
}

function sub(a, b) {
    return a - b;
}

function calc(a, b, op) {
    return op(a, b);
}

const mul = function(a, b) {
    return a * b;
}

console.log(calc(1, 2, add)); // 3
console.log(calc(1, 2, sub)); // -1
console.log(calc(1, 2, mul)); // 2
```

### 物件 (Object)

物件是 JavaScript 中最重要的一個型態，它是一種 key-value 的結構，可以用來儲存任何型態的資料。

```javascript
var a = {
    name: 'John',
    age: 18,
    sayHello: function() {
        console.log('Hello, my name is ' + this.name);
    }
};

console.log(a.name); // John
console.log(a.age); // 18
a.sayHello(); // Hello, my name is John
```

也可以用類似陣列的方式來存取物件的值：

```javascript
console.log(a['name']); // John
console.log(a['age']); // 18
a['sayHello'](); // Hello, my name is John
```

這樣的寫法在動態存取物件的值時很有用。

```javascript
var a = {
    name: 'John',
    age: 18
};

var key = 'name';
console.log(a[key]); // John
key = 'age';
console.log(a[key]); // 18
```

## 變數的運算與邏輯判斷

在 JavaScript 中，變數的運算跟邏輯判斷是很重要的一部分，這裡要介紹一些常見的運算符號。

### 運算符號

| 符號 | 描述 | 範例 |
| --- | --- | --- |
| + | 加法 | `var a = 1 + 2; console.log(a); // 3` |
| - | 減法 | `var a = 1 - 2; console.log(a); // -1` |
| * | 乘法 | `var a = 2 * 3; console.log(a); // 6` |
| / | 除法 | `var a = 6 / 2; console.log(a); // 3` |
| % | 取餘數 | `var a = 5 % 2; console.log(a); // 1` |
| ++ | 遞增 | `var a = 1; a++; console.log(a); // 2` |
| -- | 遞減 | `var a = 1; a--; console.log(a); // 0` |

遞增跟遞減配合等號可以有不同的效果：

```javascript
var a = 1;
a += 2; // a = a + 2
console.log(a); // 3

a -= 2; // a = a - 2
console.log(a); // 1
```

加號可以用來將布林值轉換成數字：

```javascript
console.log(+true); // 1
console.log(+false); // 0
```

### 邏輯判斷

| 符號 | 描述 | 範例 |
| --- | --- | --- |
| == | 等於 | `console.log(1 == 1); // true` |
| === | 等於（包括型態） | `console.log(1 === '1'); // false` |
| != | 不等於 | `console.log(1 != 2); // true` |
| !== | 不等於（包括型態） | `console.log(1 !== '1'); // true` |
| > | 大於 | `console.log(1 > 2); // false` |
| < | 小於 | `console.log(1 < 2); // true` |
| >= | 大於等於 | `console.log(1 >= 2); // false` |
| <= | 小於等於 | `console.log(1 <= 2); // true` |
| && | 且 | `console.log(true && false); // false` |
| \|\| | 或 | `console.log(true \|\| false); // true` |
| ! | 非 | `console.log(!true); // false` |

其中可以利用 `!!` 兩個反轉來將變數轉換成布林值：

```javascript
console.log(!!1); // 1 -> false ->true
console.log(!!0); // 0 -> true -> false
```


## 型態轉換

在 JavaScript 中，型態轉換是一個很重要的議題，因為 JavaScript 是一個弱型態的語言，所以型態轉換是很常見的事情。
比如說，當你將一個字串跟一個數字相加時，JavaScript 會將這個數字轉換成字串：

```javascript
var a = 1;
var b = '2';
console.log(a + b); // 12
```

但是如果一個數字跟字串相減時，JavaScript 會將這個字串轉換成數字：

```javascript
var a = 1;
var b = '2';
console.log(a - b); // -1
```

這樣的特性在開發上很方便，但也很容易出錯，所以在開發時要特別注意型態的轉換。
所以在 JavaScript 中，有一些內建的方法可以用來進行型態的轉換：

| 方法 | 描述 | 範例 |
| --- | --- | --- |
| parseInt | 將字串轉換成整數 | `console.log(parseInt('123')); // 123` |
| parseFloat | 將字串轉換成浮點數 | `console.log(parseFloat('123.45')); // 123.45` |
| String | 將數字轉換成字串 | `console.log(String(123)); // '123'` |
| Number | 將字串轉換成數字 | `console.log(Number('123')); // 123` |
| Boolean | 將數字或字串轉換成布林值 | `console.log(Boolean(0)); // false` |

不過最好的方式當然是開發者本身必須要能夠掌控變數的型態，盡可能避免不同型態的變數進行運算。