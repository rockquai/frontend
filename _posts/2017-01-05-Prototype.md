---
layout: post
title:  "Prototypes"
date:   2017-01-05
categories: [JavaScript]
comments: true
tags: [JavaScript,VanillaJS]
---

### Prototypes
- `Prototypes이란` 자바스크립트의 객체 지향적 활용에 있어서 가장 중요한 개념
- 객체에 걸린 링크
- window객체는 객체에 걸린 링크가 있는데 객체에 걸린 링크를 프로토타입이라고 한다.
- 스코프 체이닝을 통해 값을 찾으러 올라가다가 프로토타입에도 없을 경우에 에러가 난다.
- window객체는 객체에 걸린 링크가 있는데 객체에 걸린 링크를 프로토타입이라고 한다.
- 콘솔에 객체를 찍어보면 `__proto__`라고 링크가 걸려있는 객체가 나오는데 이 안에 링크가 걸려있는 객체 리스트가 나온다. `지양`
- 자바스크립트에는 클래스 개념이 없다. (ES6에도 클래스가 없다.)

<!--more-->

#### Constructor
- Objcect, String, Array, Function, Number
- `Function` ----> (.prototype)  `객체`
- `Function` (.constructor) <----  `객체`


```js
// Function : Function을 만드는 Constructor
Function.prototype.apply
Function.prototype.call
Function.prototype.bind
```

#### 이렇게 사용하지 않는다!

```js
var fn = new Function('console.log(3);');
fn(); // 3

var arr = new Array(3); // 3개의 아이템이 들어가면 값은 undefined.

console.log(typeof arr); // 0bjcect
console.log(Array.isArray(arr)); // Array type 체크할 때 사용. boolean으로 나온다.

var str = new String('name');
var str2 = 'ttt';

console.log(typeof str); // objcect
console.log(typeof str2); // string
```

##### `constructor`, `instanceof`, `Protoype Chain`
- Prototype Chain을 이용해서 OOP 사용. `Prototypal Inheritance`
- 만약에 Function 매소드 중에 bind가 없으면 Protoype Chain를 통해서 bind 매소드를 사용할 수 없다.
상속이라는 말이 개념은 없다. 위임이라는 개념이 맞다 `Behavior Delegation`
- Person.prototype -> Function.prototype -> Objcect.prototype -> null
- `__proto__` : prototype link

> [면접문제: Behavior Delegation - https://javascriptweblog.wordpress.com/2010/12/22/delegation-vs-inheritance-in-javascript/](https://javascriptweblog.wordpress.com/2010/12/22/delegation-vs-inheritance-in-javascript/)

```js
// ex1. constructor, instanceof
(function() {
    function Person(name) {
        this.name = name;
    }

    var name = new Person('claire');
    console.log(name.constructor); // Preson
    console.log(name instanceof Person); // true
})();

// ex2. Protoype Chain
(function() {    
    function Person(name) {
        this.name = name;
    }

    Person.prototype.logName = function() {
        console.log(this.name); // this ==> claire
    }

    var name = new Person('claire');
    console.log(name.__proto__); // __proto__ : 지양

    name.logName();
})();
```