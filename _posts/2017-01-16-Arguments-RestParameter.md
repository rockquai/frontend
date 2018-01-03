---
layout: post
title:  "[ES3] arguments VS [ES6] rest parameter"
date:   2017-01-16
categories: [JavaScript]
comments: true
tags: [JavaScript,VanillaJS,ES6,ES2015]
---

- 나머지 매개변수(rest parameter) 구문은 정해지지 않은 수(an indefinite number, 부정수) 인수를 배열로 나타낼 수 있게 합니다.

<!--more-->

### [rest parameter](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Functions/rest_parameters)
-  `...` 나머지 인자들을 모아서 배열로 변환

```js
// NO GOOD
function foo(a, ...b, c) {
    ...
}

// GOOD
// `...c` : Array로 변수에 활당
function foo(a, b, ...c) {
    console.log(c); // ['c', 'd', 'e', 'f'];
    console.log(Array.isArray(c));  // true
}

foo('a', 'b', 'c', 'd', 'e', 'f');
// a = 'a', b = 'b', c = 'c', 'd', 'e', 'f'
```

```js
function foo(a,b,c) {
    console.log(arguments);
}

foo(1,2,3,4,5);  // 1,2,3,4,5
```

### [ES3] arguments VS [ES6] rest parameter
```javascript
// [ES3] arguments
function getSomeCoffe3(collection) {
    console.log(collection); // 1
    console.log('arguments: ', arguments); // [1, 2,3, 4, 5, 6, 7]
}
getSomeCoffe3(1,2,3,4,5,6,7);

// [ES6] rest parameter
function getSomeCoffe6(...collection) {
    console.log('collection', collection); //  [1, 2,3, 4, 5, 6, 7]
    console.log('arguments', arguments); // [1, 2,3, 4, 5, 6, 7]
}
getSomeCoffe6(1,2,3,4,5,6,7);
```

### [ES6] default parameter & template string & interpolation
- sass문법과 유사. `${radius}` 

```javascript
function borderRadious( radius = '4px' ) {
    return `
        -webkit-border-radius: ${radius};
        -moz-border-radius: ${radius};
        border-radius: ${radius};
    `;
}

borderRadious() // 초기값 4px
borderRadious('6px') // 6px로 들어감.
```








---

#### 4. [spread operator](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Spread_operator)

```js
function add(a, b) {
    return a + b;
}

const a = [1, 2];
const b = add(a[0], a[1]); // a[0] = 1, a[1] = 2
const c = add(...a); // a = [1,2]; => Array를 개별 인자로 만들어준다.
```

```js
const arr1 = [1,2,3];
const arr2 = [4,5,6];

var total = [ ...arr1, ...arr2 ];

console.log(total); // 1,2,3,4,5,6
console.log(Array.isArray(total));  // true
```

---

### 5. [Destructuring](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment)
- 비구조화 할당(destructuring assignment) 구문은 배열 또는 객체에서 데이터를 별개(distinct) 변수로 추출할 수 있게 하는 JavaScript 식(expression).
- Object Destructuring
- Array Destructuring

#### Object Destructuring

```js
const address = {
    city : 'new york',
    state : 'NY',
    zipcode : '10003'
}

const { city, state } = address;
// const city = address.city;
// const state = address.state;

console.log(city + ', ' + state); // new your, NY

const { city: c, state: s } = address;
// const c = address.city;
// const s = address.state;

console.log(c + ', ' + s); // new your, NY

function logAddress({ city, state }) {
    console.log(city + ', ' + state);
}

logAddress(address); // new your, NY
```



#### [default parameter](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Functions/Default_parameters)
- 기본 함수 매개변수(default function parameter)를 사용하면 값이 없거나 `undefined`가 전달될 경우 매개변수를 기본값으로 초기화할 수 있다.

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
