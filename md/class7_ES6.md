# JS的一次大躍進 - JavaScript ECMAScript 2015 (ES6)

現代開發 JS 應用的工程師們應該沒有不知道 ES6 的，因為 ES6 是 JS 近年來最大的一次更新。從2009年12月推出ES5後間隔了6年，2015年6月才推出ES6，並且這次的更新是一次大躍進，不僅增加了很多新的語法，也修正了很多 ES5 的問題，尤其是 匯入匯出(Import/Export) 語法的加入，讓 JS 也能夠像其他語言一樣進行模組化開發。甚至可以說 JS 可以分成 ES5 以前和 ES6 以後兩個時代。

那麼 ES6 (包含以後) 都有哪些新的語法呢？

## 變數宣告

前面在變數宣告的部分提到過，ES6 有新增了兩個變數宣告的方式：`let` 和 `const`，解決了 ES5 中 `var` 提升的問題。

```javascript
let a = 1
const b = 2
```

## 箭頭函式

```javascript
const add = (a, b) => a + b

// 等同於
const add = (a, b) => {
    return a + b
}

// 等同於
function add(a, b) {
    return a + b
}
```

箭頭函式是 ES6 中最常見的語法之一，它可以簡化函式的寫法。

## 模板字串

```javascript
const name = 'John'
const age = 18

// 使用模板字串
const message = `Hello, my name is ${name}, I'm ${age} years old.`

// 用加號把字串接起來
const message = 'Hello, my name is ' + name + ', I\'m ' + age + ' years old.'
```

模板字串是 ES6 中另一個常見的語法，它可以讓我們在字串中插入變數，可讀性更佳。

## 解構賦值

```javascript
const person = {
    name: 'John',
    age: 18
    say: function() {
        console.log(`Hello, ${this.name}`)
    }
}

const { name, age, say } = person // name = 'John', age = 18
say() // Hello, John

const arr = [1, 2, 3]
const [a, b, c] = arr // a = 1, b = 2, c = 3

function useState(n) {
  return [
    state: n,
    setState: function(value) {
        this.state = value
    }
  ]
} 

const [ state, setState ] = useState(0) // 偷渡一點點 React 的 useState XD
setState(1) // state = 1
```
解構賦值可以讓我們從物件或陣列中取出值，並且賦值給變數。
你就可以挑出你要的值，不用再一個一個取出來。

## 擴展運算符

```javascript
const arr1 = [1, 2, 3]

const arr2 = [...arr1, 4] // [1, 2, 3, 4]
```

擴展運算符 `...` 可以將陣列或物件展開成個別的值。概念上有點像是裝著 1, 2, 3 的箱子，用 `...` 可以把箱子打開，取出裡面的東西，放到另一個箱子裡。
只是要注意的是，擴展運算符展開後的值是複製(Call by value)，不是參照(Call by reference)，但是僅是第一層而已，若是多層的話，還是會參照到原本的物件。

跟擴展運算符很像的還有剩餘參數的語法，它僅用於 Function 的參數傳入時使用。

## 剩餘參數

```javascript
function avarage(...all) {
    let sum = 0
    for (let i = 0; i < all.length; i++) {
        sum += all[i]
    }
    return sum / all.length
}

console.log(avarage(1, 2, 3, 4, 5)) // 3
```
剩餘參數 `...` 可以將多個參數收集成陣列，但要注意的是，剩餘參數只能放在最後一個參數。

## 匯入匯出

```javascript
// lib.js
export const PI = 3.14159
export function add(a, b) {
    return a + b
}

// main.js
import { PI, add } from './lib.js'
console.log(PI) // 3.14159
console.log(add(1, 2)) // 3
```

或是

```javascript
// lib.js
export default function add(a, b) {
    return a + b
}

// main.js
import add from './lib.js'
```
`export const`, `export function` 是將變數或函式匯出，`import { } from '檔案路徑'` 是將變數或函式匯入。
`export default` 是將一個函式或變數設為預設匯出，`import 函式名稱 from '檔案路徑'` 是將預設匯出的函式或變數匯入。
匯入匯出是 ES6 中最重要的一個語法，它讓 JS 也能夠像其他語言一樣進行模組化開發。
你可以將一些工具函式或變數寫在一個檔案中，然後透過匯入的方式引入到你的程式中。


## 類別

```javascript
class Person {
    constructor(name, age) {
        this.name = name
        this.age = age
    }

    say() {
        console.log(`Hello, my name is ${this.name}`)
    }
}

const john = new Person('John', 18)
john.say() // Hello, my name is John
```

`class` 類別是 ES6 中新增的語法，它讓 JS 也能夠像其他語言一樣進行物件導向開發。
詳細可以參考上一篇文章。

## Promise

```javascript
function asyncFunc() {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve('Done')
        }, 1000)
    })
}

asyncFunc().then((result) => {
    console.log(result) // Done
})
```
`Promise` 是 ES6 中新增的語法，它可以解決 JS 中的函式呼叫地獄(函式波動拳)的問題，讓非同步程式碼更容易閱讀和維護。
關於非同步程式碼的部分，會在之後的文章中詳細介紹。

## async/await

```javascript
async function asyncFunc() {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve('Done')
        }, 1000)
    })
}

function main() {
    const result = await asyncFunc()
    console.log(result) // Done
}

main()
```
`async/await` 是 ES8 中新增的語法，它可以讓非同步程式碼更像同步程式碼一樣撰寫，讓程式碼更容易閱讀和維護。
關於非同步程式碼的部分，會在之後的文章跟 `Promise` 一起詳細介紹。