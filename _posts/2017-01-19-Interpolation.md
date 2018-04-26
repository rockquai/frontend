---
layout: post
title:  "[ES6] interpolation"
date:   2017-01-19
categories: [JavaScript]
comments: true
tags: [JavaScript,VanillaJS,ES6,ES2015]
---

- 기본 함수 매개변수(default function parameter)를 사용하면 값이 없거나 `undefined`가 전달될 경우 매개변수를 기본값으로 초기화할 수 있다.

<!--more-->

### [백틱(Backtick)](http://hacks.mozilla.or.kr/2015/08/es6-in-depth-template-strings-2/)
- ES6는 템플릿 문자열(template string)이라고 불리는 새로운 종류의 문자열 표기법을 도입
- 템플릿 문자열은 일반 문자열과 비슷해 보이지만, '나 " 같은 통상적인 따옴표 문자 대신 `백틱(backtick) 문자` 를 사용
- 가장 간단하게 사용할 경우, 템플릿 문자열은 정말 일반 문자열과 똑같다
- String interpolation
- Sass문법과 유사. `${}`

```js
// 사용 예)
const oReq = new XMLHttpRequest();
oReq.addEventListener('load', (evt) => changeContents(evt, index));
oReq.open('GET', `http://jsonplaceholder.typicode.com/posts/${(index + 1)}`);
oReq.send();
onTabSelected(tabList[index], index);
```
