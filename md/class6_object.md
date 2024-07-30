# 物件，滿天都是物件

## 物件的概念

先撇開工程、程式的角度，我們先探討何謂物件(`Object`)，物件是一種抽象的概念，比如說一個人，他是男的女的、年齡幾歲、身高多少、體重多重、體態胖瘦等等，而這些就可以被稱為是物件的屬性(`Attribute`)，而這個人會有一些行為(`Behavior`)，比如說走路、跑步、吃飯、睡覺等等，這些行為就可以被稱為是物件的方法(`Method`)。


而 JS 本身是一個很強調物件導向的語言，所以我們根據以上的敘述，我們可以嘗試著用 JS 描述一個人的物件：

```javascript
const person = {
  name: 'Aaron',
  age: 30,
  height: 170,
  weight: 70,
  shape: 'normal',
  walk: function() {
      console.log('walk');
  },
  run: function() {
      console.log('run');
  },
  eat: function() {
      console.log('eat');
  },
  sleep: function() {
      console.log('sleep');
  }
};
```

而這樣的一個物件如果要被建立多個，我們就需要一個模板，這個模板就是我們所謂的類別(Class)，而這個模板就像是一個蓋模具，可以用來生產多個相同的物件，而這個模板就是我們所謂的類別(Class)。

## 類別的概念

類別(Class)是一種抽象的概念，它是用來描述物件的模板，而這個模板可以用來建立多個相同的物件，而根據模板建立的這個物件可以被稱為實例(Instance)。
所以你可能聽過工程師們討論程式執行流程會說：「這個 `instance` 是在什麼時候建立的？誰建立的？到什麼時候消失？」，這個 `instance` 就是指的物件的實例。

而在 JS 中，我們可以透過 `class` 關鍵字來建立一個類別，而這個類別可以用來建立多個物件的實例，根據以上 `Person` 我們建立以下簡單的範例：

```javascript
class Person {
  constructor(name, age, height, weight, shape){
    this.name = name;
    this.age = age;
    this.height = height;
    this.weight = weight;
  }
    walk() {
        console.log(`${this.name} walk`);
    }
    run() {
        console.log(`${this.name} run`);
    }
    eat() {
        console.log(`${this.name} eat`);
    }
    sleep() {
        console.log(`${this.name} sleep`);
    }
}

const aaron = new Person('Aaron', 30, 170, 70, 'normal');
aaron.walk(); // Aaron walk
aaron.run(); // Aaron run
aaron.eat(); // Aaron eat
aaron.sleep(); // Aaron sleep

const bob = new Person('Bob', 25, 180, 80, 'fat');
bob.walk(); // Bob walk
bob.run(); // Bob run
bob.eat(); // Bob eat
bob.sleep(); // Bob sleep
```

`class Person` 內的 `constructor` 稱為`建構函式`，用來初始化物件的屬性，而 `walk、run、eat、sleep` 就是物件的方法，可以透過 `new` 關鍵字來建立物件的實例，並且傳入必要的參數(`Parameter`)就可以建立物件的實例。

## This 就是我的忍道

在物件的方法中，我們會看到 `this` 這個關鍵字，`this` 代表的是當前物件的實例，也就是說 `this.name` 代表的是當前物件的實例的 `name` 屬性，而 `this` 這個關鍵字是在物件的方法中才會出現的，而在物件的方法中，我們可以透過 `this` 來存取物件的屬性和方法。

但 this 並不是只會在類別中出現，它可以在 JS 的任何一個角落出現，但它的值會隨著執行的環境而改變，比如說：

```javascript

console.log(this) // 在沒有 Function 或是 類別包覆下，this 會指向全域物件，也就是 window

function add(x,y){
  console.log(this) // Function 的 this 也是 window
  return x+y
}

const obj = {
  name: 'Aaron',
  sayName: function() {
    console.log(this) // 在物件的方法中，this 會指向當前物件的實例，也就是 {name:'Aaron', sayName: ƒ}
  }
}
```

在全域的範圍下， `this` 會指向 `window`，不過如果是在嚴格模式下執行，所有指向 `window` 的 `this` 都會是 `undefined`

```javascript
function add(x,y){
  'use strict'
  console.log(this) // undefined
  return x+y
}

'use strict'
console.log(this) // undefined
```

## 繼承的概念

我們其實知道，人類還可以再根據性別分成男人、女人；根據種族分成白人、黑人、黃種人；根據地區分成亞洲人、歐洲人、非洲人等等，這些都可以被稱為是人類的子類別(Subclass)，而這些子類別可以繼承(Extend)人類的類別，這樣就可以達到程式碼的重用性，而這個概念就是所謂的繼承(Inheritance)。

繼承(Inheritance)是一種物件導向的概念，它是用來描述子類別(Subclass)可以繼承父類別(Parent Class)的屬性和方法，而這樣的機制可以達到程式碼的重用性，而在 JS 中，我們可以透過 `extends` 關鍵字來實現繼承的機制，以下是一個簡單的範例：

```javascript
class Person {
  constructor(name, age, height, weight, shape){
    this.name = name;
    this.age = age;
    this.height = height;
    this.weight = weight;
  }
  walk() {
      console.log(`${this.name} walk`);
  }
  run() {
      console.log(`${this.name} run`);
  }
  eat() {
      console.log(`${this.name} eat`);
  }
  sleep() {
      console.log(`${this.name} sleep`);
  }
}

class Man extends Person {
  constructor(name, age, height, weight, shape, penis){
    super(name, age, height, weight, shape);
    this.penis = penis;
  }

  // 這裡就不需要再重新定義 walk、run、eat、sleep 方法，會從父類別繼承下來

  // 男人特有的方法
  fight() {
      console.log('男人愛打架');
  }
}

class Woman extends Person {
  constructor(name, age, height, weight, shape, breast){
    super(name, age, height, weight, shape);
    this.breast = breast;
  }

  // 這裡就不需要再重新定義 walk、run、eat、sleep 方法，會從父類別繼承下來

  makeup() {
      console.log('女人愛化妝');
  }
}

const aaron = new Man('Aaron', 30, 170, 70, 'normal', '30CM')
aaron.walk(); // Aaron walk
aaron.run(); // Aaron run
aaron.eat(); // Aaron eat
aaron.sleep(); // Aaron sleep
aaron.fight(); // 男人愛打架
aaron.makeup(); // Error: aaron.makeup is not a function 男人沒有 makeup 方法

const tina = new Woman('Tina', 25, 160, 50, 'skinny', 'Dcup')
tina.walk(); // Tina walk
tina.run(); // Tina run
tina.eat(); // Tina eat
tina.sleep(); // Tina sleep
tina.fight(); // Error: tina.fight is not a function 女人沒有 fight 方法
tina.makeup(); // 女人愛化妝
```

透過繼承的概念，我們可以將共用的屬性和方法抽象到父類別中，而子類別只需要專注於自己特有的屬性和方法，這樣就可以達到程式碼的重用性，而且也可以讓程式碼更加的模組化。像是以上的範例，男人會有GG，而女人會有胸部，而無論男人女人都有吃喝拉撒睡等基本的行為，這樣的設計就可以讓程式碼更加的簡潔。


## 封裝的概念

而且如果有注意到吃喝拉撒睡這些基本行為的內容，會發現都是從物件內部的屬性去取得，而不是由外部傳入參數來達成的，這樣的設計就是所謂的封裝(Encapsulation)，將物件的屬性和方法封裝在物件內部，只需要透過物件的方法來存取物件的屬性，這樣就可以達到程式碼的安全性，而且也可以避免外部直接存取物件的屬性，這樣的設計就可以達到程式碼的安全性。

## 多型的概念

那麼如果我們想要讓男人的「吃」這個行為脫離原本人類的「吃」，我們可以用覆寫(Override)的概念，透過在子類別中重新定義父類別的方法，這樣就可以達到覆寫的效果，以下是一個簡單的範例：

```javascript
class Person {
  constructor(name, age, height, weight, shape){
    this.name = name;
    this.age = age;
    this.height = height;
    this.weight = weight;
  }
  walk() {
      console.log(`${this.name} walk`);
  }
  run() {
      console.log(`${this.name} run`);
  }
  eat() {
      console.log(`${this.name} eat`);
  }
  sleep() {
      console.log(`${this.name} sleep`);
  }
}

class Man extends Person {
  constructor(name, age, height, weight, shape, penis){
    super(name, age, height, weight, shape);
    this.penis = penis
  }

  eat(){
    console.log(`${name}：男人就是要大口吃肉、大口喝酒`)
  }

  fight() {
    console.log('男人愛打架');
  }
}

const person = new Person('John', 20, 180, 75)
person.eat(); // John walk.

const aaron = new Man('Aaron', 30, 170, 70, 'normal', '30CM')
aaron.eat(); // Aaron：男人就是要大口吃肉、大口喝酒
```

這樣覆寫父類別方法、讓子類別在同樣名稱的方法上可以具有不同行為的方式，就稱為多型(Polymorphism)。
繼承、封裝、多型這三個特性就稱為物件導向的三大特性，所以這就是為什麼稱 JavaScript 是一種物件導向的語言；可以被稱之為物件導向語言的不只 JS，還有 Java, C++, C#, Python 等等，還有更多就不一一列出了。

## 物件原本的寫法

上述提到的 `class` 是在 JavaScript ES6 之後才問世的。在 ES6 出現之前類別的宣告都是使用 Function 語法來建立的。

```javascript
function Person(name, age, height, weight, shape){
  this.name = name;
  this.age = age;
  this.height = height;
  this.weight = weight;
}

const aaron = new Person('Aaron', 30, 170, 70, 'normal');
```

而且類別的方法不是直接寫在 Function 裡，而是寫在物件的原型(`Prototype`)裡：

```javascript
Person.prototype.walk = function() {
  console.log(`${this.name} walk`);
}
Person.prototype.run = function() {
  console.log(`${this.name} run`);
}
Person.prototype.eat = function() {
  console.log(`${this.name} eat`);
}
Person.prototype.sleep = function() {
  console.log(`${this.name} sleep`);
}
```

那繼承呢？繼承也是透過原型來實現：

```javascript
function Man(name, age, height, weight, shape, penis){
  // 繼承 Person 的屬性
  Person.call(this, name, age, height, weight, shape)
  this.penis = penis
}

Man.prototype = Object.create(Person.prototype)
Man.prototype.constructor = Man

Man.prototype.fight = function(){
  console.log('男人就是愛打架')
}
```

### 函式物件的建構函式的 this 不一樣

前述提到 `this` 在 `Function` 中會指向 `window or undefined(嚴格模式)`，但其實是因為 `Function` 作為純函式使用的關係，
如果函式是作為物件的建構函式，透過 `new` 的方式呼叫，則 `this` 就會是該物件的實例本身

```javascript
function add(x,y){
  console.log(this) // 作為純函式使用時 Function 的 this 也是 window
  return x+y
}

function Circle(radius){
  this.radius = radius

  this.printThis = function(){
    console.log(this) // 在建構函式中，this 會指向當前物件的實例，也就是 new Circle(10)
  }
}

const circle = new Circle(10)
circle.printThis() // Circle {radius: 10, getThis: ƒ}
```

到這邊你肯定會問，什麼是原型？ ES6 之前的寫法也好難看懂喔！
在這個章節我們不會討論原型，而目前的開發生態也很少使用 ES6 之前這樣的函式類別了
甚至也很少用 `class` 物件類別了，取而代之的是鉤子 `hook`

這個小節算是一個歷史討論而已。
不過原型在 JS 是個很重要的概念，之後會專門再開一個章節討論。