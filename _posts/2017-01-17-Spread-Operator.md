---
layout: post
title:  "[ES6] spread operator"
date:   2017-01-16
categories: [JavaScript]
comments: true
tags: [JavaScript,VanillaJS,ES6,ES2015]
---

- 전개 연산자(spread operator)는 표현식(expression)은 2개 이상의 인수arguments(함수 호출 용)나 2개 이상의 요소elements(배열 리터럴 용) 또는 2개 이상의 변수(비구조화 할당 용)가 예상되는 곳에 확장될 수 있도록 합니다

<!--more-->

### [spread operator](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Spread_operator)

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
