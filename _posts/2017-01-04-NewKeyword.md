---
layout: post
title:  "this의 값을 판단 방법 'new keyword'"
date:   2017-01-04
categories: [JavaScript]
comments: true
tags: [JavaScript,VanillaJS]
---

### this의 값을 판단 방법 `new keyword`
- new를 사용하면 다음 4가지 발생
    - 1. 완전 새로운 `빈 객체(Objcect)`를 생성함
    - 2. 새로 만든 빈 객체를 `또 다른 객체에 연결`
    - 3. 새로 만들어진 빈 객체가 해당 함수의 `this` 값으로 넘겨짐
    - 4. 해당 함수에서의 retrun 이 없으면 빈 객체가 return. 

<!--more-->

```js
// ex1.
function Person() {
    this.age = 30; // retrun 값이 없으면 자동으로 빈 객체가 retrun.
    console.log(this.age);
}

var age = 40;
var person = new Person(); // constructor call.
```

```js
// ex1.
(function() {
    function Person() {
        this.age = 30;
        // return this; // 이 부분이 생략 되어 있다
        // return; //
    }

    // Constructor Call.
    var person = new Person();
    console.log(person);    
})();

//ex2. usually capitalied
(function() {
    // Called Constructor function
    function Person(name, age, sex) {
        this.name = name;
        this.age = age;
        this.sex = sex;
    }

    // person1, person2를 Called "instances" 부른다
    var person1 = new Person('ken', 34, 'm');
    var person2 = new Person('jane', 30, 'f');
})();
```
