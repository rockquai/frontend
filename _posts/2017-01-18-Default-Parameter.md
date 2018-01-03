---
layout: post
title:  "[ES6] default parameter"
date:   2017-01-18
categories: [JavaScript]
comments: true
tags: [JavaScript,VanillaJS,ES6,ES2015]
---

- 기본 함수 매개변수(default function parameter)를 사용하면 값이 없거나 `undefined`가 전달될 경우 매개변수를 기본값으로 초기화할 수 있다.

<!--more-->

### [default parameter](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Functions/Default_parameters)

```js
// ES5
function logName(name) {
    name = mane || 'claire';
    console.log(name);
}

logName(); // name = undefined || 'claire' =>  'claire'
logName('ken'); // 'ken'

// ES5
function logNumber1(num) {
    num = num || 123;
    console.log(num);
}

logNumber1(); // 124
logNumber1(0); // 123 => 의도한 값을 '0'인데 '0'이 거짓스런값이므로 123이 나온다
logNumber1(1000); // 1000

// ES5
function logNumber2() {
    if(num === undefined) num = 123;
    console.log(num);
}

logNumber2(); // 124
logNumber2(0); // 0
logNumber2(1000); // 1000

//ES6
const logName2 = (name = 'claire') => {
    console.log(name);
}

logName2(); // claire
logName2('ken') //ken

// ES6
const logNumber3 = (num = 123) => {
    console.log(num);
}

logNumber3(); // 124
logNumber3(0); // 0
logNumber3(1000); // 1000

// ES6
const getNumber = () => {
    console.log('aaa');
    return 123;
}

const logNumbers = ( num = getNumber() ) => {
    console.log(num);
}

logNumbers(); // 'aaa', 123 => 인자가 undefined일 때만 getNumber() 실행이 된다
logNumbers(1000); // 1000
```
