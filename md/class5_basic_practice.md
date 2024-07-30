# 牛刀小試

經過了前面的學習，我們已經掌握了一些基本的 JS 語法，現在來試試看吧！

## 計算陣列中的總和

請寫一個函式 `sum`，接收一個陣列，回傳陣列中的總和。

```javascript
function sum(arr) {
    // your code here
}

console.log(sum([1, 2, 3, 4, 5])) // 15
console.log(sum([5, 4, 3, 2, 1])) // 15
console.log(sum([5, 5, 5, 5, 5])) // 25
```

## 計算陣列中的平均值

請寫一個函式 `average`，接收一個陣列，回傳陣列中的平均值。

```javascript
function average(arr) {
    // your code here
}

console.log(average([1, 2, 3, 4, 5])) // 3
console.log(average([5, 4, 3, 2, 1])) // 3
console.log(average([5, 5, 5, 5, 5])) // 5
```

## 計算陣列中的最大值

請寫一個函式 `findMax`，接收一個陣列，回傳陣列中的最大值。

```javascript
function findMax(arr) {
    // your code here
}

console.log(findMax([1, 2, 3, 4, 5])) // 5
console.log(findMax([5, 4, 3, 2, 1])) // 5
console.log(findMax([5, 5, 5, 5, 5])) // 5
```

## 數字反轉

請寫一個函式 `reverse`，接收一個數字，回傳這個數字的反轉。

```javascript
funciton reverse(n) {
    // your code here
}

console.log(reverse(123)) // 321
console.log(reverse(12345)) // 54321
console.log(reverse(10000)) // 1
```

## 判斷質數

請撰寫一個函式 `isPrime`，接收一個數字，回傳這個數字是否為質數。

:::info
質數（Prime number）指的是除了 1 和本身以外，無法被其他正整數整除的數字。
:::

```javascript
function isPrime(n) {
    // your code here
}

console.log(isPrime(1)) // false
console.log(isPrime(2)) // true
console.log(isPrime(3)) // true
console.log(isPrime(10)) // false
```

## 尋找任意範圍內的質數

請撰寫一個函式 `findPrimes`，接收兩個數字，回傳這兩個數字之間（包含這兩個數字）的所有質數。

```javascript
function findPrimes(start, end) {
    // your code here
}

console.log(findPrimes(1, 10)) // [2, 3, 5, 7]
console.log(findPrimes(20,30)) // [23, 29]
```

## 計算字母出現的次數

請撰寫一個函式 `countLetters`，接收一個字串，回傳一個物件，表示字串中每個字母出現的次數。

```javascript
function countLetters(str) {
    // your code here
}

console.log(countLetters('hello')) // { h: 1, e: 1, l: 2, o: 1 }
console.log(countLetters('apple')) // { a: 1, p: 2, l: 1, e: 1 }
```

## 去掉陣列內重複的數字

請撰寫一個函式 `unique`，接收一個陣列，回傳一個新陣列，新陣列中不包含重複的數字。

```javascript
function unique(arr) {
    // your code here
}

console.log(unique([1, 1, 2, 3, 3])) // [1, 2, 3]
console.log(unique([1, 2, 2, 1, 4])) // [1, 2, 4]
```

接下來讓我們嘗試一些稍微難度高一點的題目！

## 直印九九乘法表

請撰寫一個函式 `printTimesTable`，接收一個數字 `n`，印出 `n` 乘 `n` 的九九乘法表。

```javascript
function printTimesTable(n) {
    // your code here
}

// 結果：
// 1 * 1 = 1
// 1 * 2 = 2
// 1 * 3 = 3
// ...
// 2 * 1 = 2
// 2 * 2 = 4
// 2 * 3 = 6
// ...
// 5 * 1 = 5
// 5 * 2 = 10
// 5 * 3 = 15
// ...
// 5 * 5 = 25
printTimesTable(5)
```

## 橫印九九乘法表

請撰寫一個函式 `printHorizontalTimesTable`，接收一個數字 `n`，印出 `n` 乘 `n` 的九九乘法表，並且橫向排列。

```javascript
function printHorizontalTimesTable(n) {
    // your code here
}

// 結果：
// 1 * 1 = 1  1 * 2 = 2  1 * 3 = 3  1 * 4 = 4  1 * 5 = 5
// 2 * 1 = 2  2 * 2 = 4  2 * 3 = 6  2 * 4 = 8  2 * 5 = 10
// 3 * 1 = 3  3 * 2 = 6  3 * 3 = 9  3 * 4 = 12  3 * 5 = 15
// 4 * 1 = 4  4 * 2 = 8  4 * 3 = 12  4 * 4 = 16  4 * 5 = 20
// 5 * 1 = 5  5 * 2 = 10  5 * 3 = 15  5 * 4 = 20  5 * 5 = 25
printHorizontalTimesTable(5)
```

## 等腰三角形

請撰寫一個函式 `printIsoscelesTriangle`，接收一個數字 `n`，印出 `n` 層的等腰三角形。

```javascript
function printIsoscelesTriangle(n) {
    // your code here
}

// 結果：
//     *
//    ***
//   *****
//  *******
// *********
printIsoscelesTriangle(5)
```

## 倒印等腰三角形

請撰寫一個函式 `printReverseIsoscelesTriangle`，接收一個數字 `n`，印出 `n` 層的倒印等腰三角形。

```javascript
function printReverseIsoscelesTriangle(n) {
    // your code here
}

// 結果：
// *********
//  *******
//   *****
//    ***
//     *
printReverseIsoscelesTriangle(5)
```

## 十進位轉二進位

請撰寫一個函式 `decimalToBinary`，接收一個數字 `n`，回傳這個數字的二進位表示法。

```javascript
function decimalToBinary(n) {
    // your code here
}

console.log(decimalToBinary(0)) // 0
console.log(decimalToBinary(1)) // 1
console.log(decimalToBinary(2)) // 10
console.log(decimalToBinary(3)) // 11
console.log(decimalToBinary(126)) // 1111110
console.log(decimalToBinary(87)) // 1010111
```

## 十進位轉十六進位

請撰寫一個函式 `decimalToHex`，接收一個數字 `n`，回傳這個數字的十六進位表示法。

:::info
十六進位表示法是一種使用 0-9 和 a-f 來表示數字的方法，其中 a 表示 10、b 表示 11、c 表示 12、d 表示 13、e 表示 14、f 表示 15。
所以 125 的十六進位表示法是 7d ，相當於 7 * 16 + 13 = 125。
:::

```javascript
function decimalToHex(n) {
    // your code here
}

console.log(decimalToHex(0)) // 0
console.log(decimalToHex(1)) // 1
console.log(decimalToHex(10)) // a
console.log(decimalToHex(15)) // f
console.log(decimalToHex(16)) // 10
console.log(decimalToHex(255)) // ff
```

