# 2. JavaScript起手式


## 定義
讓我抄一下 ChatGPT 的定義：

> JavaScript 是一種高級、直譯式程式語言，主要用於網頁開發。它是一種基於原型、函數先行的語言，是一種多範式語言，支援物件導向程式設計、命令式程式設計、以及函數式程式設計。它提供語法來操控瀏覽器，例如：DOM 操作、事件處理、以及 AJAX 技術等等。

其實說得很對。

但回到最原始的解釋，JavaScript 就是一種可以操控瀏覽器的程式語言，它是由上往下直譯的。
因為它的直譯式特性，所以可以直接在瀏覽器上執行，本質上它跟其他程式語言沒有太大的差異。

尤其在 Node.js 推出後 JavaScript 只要具備 Node 環境，就可以像是撰寫 Shell 那樣讓電腦執行一些指令，這樣的特性讓 JavaScript 在網頁開發以外的領域也有了更多的應用，例如：簡單的指令集成、後端伺服器、桌面應用程式等等。

那麼，要怎麼開始使用 JavaScript 呢？
很簡單，無論你是用 Chrome、Firefox、Safari、Edge 還是其他瀏覽器，都可以直接在開發者工具的 Console 輸入 JavaScript 來執行。

```javascript
console.log('Hello, World!');
```

你會在 Console 看到 `Hello, World!` 的字串被印出來。

又或者是

```javascript
alert('Hello, World!');
```

你會看到瀏覽器跳出一個對話框，顯示 `Hello, World!` 的字串。

:::info
接下來的文章中，我會將 JavaScript 簡稱為 JS。
有些地方會括號加入一些英文名詞，這會對你之後排錯有幫助，通常 JS 報錯的訊息都會有這些名詞XD
:::

## 變數的宣告與定義 (Variables Declaration and Definition)

上面只是牛刀小試，JS 的功能遠不止這些。
讓我來看看 JS 的變數。

在開始聊變數之前，我先來看看什麼是變數(`Variable`)。
變數：是用來儲存資料的容器，它實際上就是存在記憶體的一塊空間，用來存放資料。
要使用變數，首先要先宣告(`Declare`)它，告訴電腦我要使用這個變數，名字是什麼。

:::info
變數名稱原則上可以使用任何字元，除了特定 JS 程式碼的保留字、數字開頭、特殊符號等。
特殊符號可以使用底線 `_` 或是 `$`。
由於JS支援 unicode，所以也可以使用中文、日文、韓文等等，但是不建議使用。

命名方式約定俗成可以分成駝峰式(`camelCase`)、底線式(`snake_case`)、帕斯卡式(`PascalCase`)等等。

1. 駝峰式：第一個單字小寫，之後的單字首字大寫，例如：`myName`
2. 底線式：所有單字小寫，用底線 `_` 連接，例如：`my_name`
3. 帕斯卡式：所有單字首字大寫，例如：`MyName`

通常 JS 的變數命名都是使用駝峰式。
:::

```javascript
var a; // undefined
```

這樣就宣告了一個變數 `a`，但是這個變數是空的，沒有任何值。
賦予(`Assign/Assignment`)變數值的動作叫做定義(`Definition`)，也就是告訴電腦這個變數的值是什麼。

```javascript
var a;
a = 1;
```

在 JS 中，變數的宣告有三種方式

|類型|說明|範例|
|---|---|---|
|var|宣告一個變數，並可以賦予值|`var a = 1;`|
|let|宣告一個區域變數，只在區域內有效|`let a = 1;`|
|const|宣告一個常數，不可更改|`const a = 1;`|

以下我詳細說明這三種宣告方式：

### var 宣告

```javascript   
var a = 1;
a=2;
```
告訴瀏覽器宣告一個變數 `a`，並賦予值 `1`，之後可以更改 `a` 的值。

### const 宣告

```javascript
const PI = 3.14159;
PI = 3.14; // Error
```
告訴瀏覽器宣告一個常數 `PI`，並賦予值 `3.14159`，但是 `PI` 是不可以被更改的。

### let 宣告

```javascript
let a = 1;
a = 2;
```
告訴瀏覽器宣告一個區域變數 `a`，並賦予值 `1`，之後可以更改 `a` 的值。

這時候你一定會有個疑問，看起來 `var` 和 `let` 很像，那我要用哪一個？
那我就需要先理清一下為什麼 JS 會在 ES6 之後推出 `let` 這個宣告方式了。

:::info
`ES6` 是 `ECMAScript 6` 的簡稱，是 JavaScript 的一個版本，也是目前最新的版本。
之後會特別拉一個章節來介紹 ES6 的新特性，這邊先知道 `let, const` 是 ES6 新出的宣告方式就好。
:::

## var 的問題以及 let 的出現

在 ES6 之前，JS 只有 `var` 這個宣告方式，但是 `var` 有一個很大的問題，就是變數的作用域問題。

```javascript
var aaron = 'aaron';
console.dir(window)
console.log(window.aaron == aaron); // true
```
執行以上的程式碼，你會發現 `aaron` 這個變數被宣告在 `window` 這個物件下，所以當我調用 `aaron` 時，會調用 `window` 的 `aaron`
實務上，我在設計架構時不會將所有的程式碼都放在同個檔案中，也就是說如果有任意兩個檔案裡面同時都有一個變數 `aaron`，那麼這兩個變數 `aaron` 就會互相影響，很容易就會出現跟預期不同的結果。
會有這樣的結果，是因為 JS 對於 var 宣告的變數會進行 Hoisting(提升)，也就是將變數的宣告提升到最上面，讓這個變數成為整個環境裡的全域共用變數，這時候它的作用域(Scope)就等於全域。

### 提升(Hoisting)

使用 var 宣告的變數會被提升到程式碼的最上面，這樣就可以在變數被宣告之前使用，只是這個變數的值會是 `undefined`。

```javascript
console.log(a); // undefined
var a = 1;

// 等同於   
var a;
console.log(a); // undefined
a = 1;
```

另外 Function 也會被提升，這樣就可以在 Function 被宣告之前使用。

```javascript
foo(); // Hello, World!
function foo() {
    console.log('Hello, World!');
}

// 等同於
function foo() {
    console.log('Hello, World!');
}
foo(); // Hello, World!
```

所以你可能會很常看到這種寫法：

```javascript
console.log(add(1,1) + multiply(2,2));

function add(a, b) {
    return a + b;
}

function multiply(a, b) {
    return a * b;
}
```

除此之外的變數都必須先宣告再使用，否則會報錯。

```javascript
console.log(a); // a is not defined
let a = 1;

console.log(PI); // PI is not defined
const PI = 3.14159; 
```

### 作用域(Scope)

作用域是指變數的有效範圍，也就是說變數在哪裡可以被使用。
在 ES6 之前，JS 只有全域作用域和函數作用域，也就是說變數只有全域和函數兩種作用域。
而且使用 var 宣告的全域變數會被註冊到 `window` 物件下，容易產生變數污染。

```javascript

// 全域作用域
var a = 1; // 沒有被包在任何函數裡面，所以是全域變數，會被註冊到 window 物件下，也就是 window.a = 1;
let c = 3; // 沒有被包在任何函數裡面，所以是全域變數，但是不會被註冊到 window 物件下

function foo() { // 函數作用域  
    var b = 2; // -------| b 的作用域只在這個方框裡
    console.log(b); //   | 函式結束後 b 就會被釋放，所以 b 不能在函式外被使用
}//----------------------|

foo();
console.log(b); // b is not defined
```

另外一提，作用域的位置是相對的，外層作用域可以被內層作用域存取，但是內層作用域不能被外層作用域存取。

```javascript
var a = 1;

function foo() {
    console.log(a); // 1
}
foo();
```

還有一種情況，就是外層作用域的變數名稱跟內層作用域的變數名稱相同，這時候內層作用域的變數權重會比外層作用域的變數高，所以讀取到的是內層作用域的變數。

```javascript
var a = 1;
function foo() {
    var a = 2;
    console.log(a); // 2
}
foo();
console.log(a); // 1
```

最後介紹一下區塊作用域(Block Scope)，上述提到的全域作用域和函數作用域都是區塊作用域的一種，只是範圍不同，而 ES6 之後推出的一種特有語法 `{}` 可以不需要宣告函式就可以建立一個區塊作用域，它一樣會直譯，從上到下執行，只是多了一塊作用域來限制內層的變數。

```javascript
{
    let a = 1;
    console.log(a); // 1
}
```