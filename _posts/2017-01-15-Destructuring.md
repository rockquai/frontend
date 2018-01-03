---
layout: post
title:  "[ES6] destructuring"
date:   2017-01-15
categories: [JavaScript]
comments: true
tags: [JavaScript,VanillaJS,ES6,ES2015]
---

- 비구조화 할당(destructuring assignment) 구문은 배열 또는 객체에서 데이터를 별개(distinct) 변수로 추출할 수 있게 하는 JavaScript 식(expression).
- Array Destructuring
- Object Destructuring

<!--more-->

### [Destructuring](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment0)

#### 1. Array Destructuring

```js
const numbers = [1,2,3,4,5];
const [one, two, three, four, five] = numbers;
// const one = numbers[0];
// const two = numbers[1];
// const three = numbers[2];
// const four = numbers[3];
// const five = numbers[4];
// const six = numbers[5]; //undefined

console.log(one);
console.log(two);
```

```js
const numbers = [1,2,3,4,5];
const [one, , , ,five] = numbers;

console.log(one); // 1
console.log(five); // 5

const sum1 = ([a, b, c, d, e]) => {
    console.log(a + b + c + d + e);
}

sum1(numbers); // 15

const sum2 = ([a, b, c]) => {
    console.log(a + b + c); // a:1, b:2, c: 3
}
sum2(numbers); // 6

const sum3 = ([a, b, ...c]) => {
    console.log(c);
}

sum3(numbers); // [3, 4, 5]
```

#### 2. Object Destructuring

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



