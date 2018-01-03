---
layout: post
title:  "Event Object"
date:   2017-01-10
categories: [JavaScript]
comments: true
tags: [JavaScript,VanillaJS]
---

- 모든 이벤트 핸들러에는 Event Object가 넘겨져 들어온다.
- Event Object는 발생한 이벤트에 대한 추가 정보를 제공한다.
- 추가 정보는 이벤트의 종류에 따라 조금씩 차이가 있다.

<!--more-->

#### Event Object Properties
- `event.type` click, keypress, focus
- `event.preventDefault();` 브라우저상의 기본 동작들을 방지한다.
- `event.stopPropagation();` Event의 흐름을 멈춘다. (capturing, bubbling을 막아준다)
- `event.target` 실제 Event가 발생한 Element.
- `evnet.currentTarget` event handler가 등록된 Element.

#### 1. [event.preventDefault()](https://developer.mozilla.org/ko/docs/Web/API/Event/preventDefault)
```html
<div>
  <input type="checkbox">
  <label for="checkbox">select</label>
</div>
```

```js
var div = document.querySelector('div');
var input = document.querySelector('input');

div.addEventListener('click', function(e) {
    console.log('div event');
});

input.addEventListener('click', function(e) {
    e.preventDefault(); // 체크박스가 체크 되지 않는다.
    console.log('input event');
});
```

#### 2. [event.stopPropagation()](https://developer.mozilla.org/ko/docs/Web/API/Event/stopPropagation)

```js
var first = document.querySelector('#first');
var second = document.querySelector('#second');
var third = document.querySelector('#third');

/* Event Capturing */
first.addEventListener('click', function (e) {
//   e.stopPropagation();
  console.log('Capturing:' + firstEl.id);
}, true);

second.addEventListener('click', function (e) {
//   e.stopPropagation();
  console.log('Capturing:' + secondEl.id);
}, true);

third.addEventListener('click', function (e) {
//   e.stopPropagation();
  console.log('Capturing:' + thirdEl.id);
}, true);

/* Event Bubbling */
firstEl.addEventListener('click', function (e) {
//   e.stopPropagation();
  console.log('Bubbling:' + firstEl.id);
});

secondEl.addEventListener('click', function (e) {
  e.stopPropagation();
  console.log('Bubbling:' + secondEl.id);
});

thirdEl.addEventListener('click', function (e) {
//   e.stopPropagation();
  console.log('Bubbling:' + thirdEl.id);
});
```

#### 3. Event target vs currentTarget

```html
<ul>
    <li id='one'>1</li>
    <li id='two'>2</li>
    <li id='three'>3</li>
    <li id='four'>4</li>
    <li id='five'>5</li>
</ul>
```

```js
var ul = document.querySelector('ul');

// event bubbing
ul.addEventListener('click', function(e) {
    console.log('Target:' + e.target.id); // 클릭한 li
    console.log('CurrentTarget:' + e.currentTarget.tagName); // ul
});
```
