---
layout: post
title:  "Event Delegaion : Capturing VS Bubbling"
date:   2017-01-09
categories: [JavaScript]
comments: true
tags: [JavaScript,VanillaJS]
---

- `Evnet Capturing` : 넷스케이프, 거의 사용하지 않는다.
- `Event Bubbling` : MS, 사용을 많이 한다.

<!--more-->

#### 1. Evnet Capturing
- `EVENT_TAGET.addEventListener(EVENT_TYPE, EVENT_HANDLER, true);`
- 부모노드에서 자식노드로 이벤트가 전파
- 자식을 클릭하면 최상단 부모가 이벤트 핸들러가 실행되고 그 다음 자식에 이벤트가 실행

```html
<div class="parent">
    <button type="button">1</button>
    <button type="button">2</button>
    <button type="button">3</button>
    <button type="button">4</button>
</div>
```

### 2. Event Bubbling
- `EVENT_TAGET.addEventListener(EVENT_TYPE, EVENT_HANDLER, false);`
> `EVENT_TAGET.addEventListener(EVENT_TYPE, EVENT_HANDLER);`  false 기본값

- 자식노드부터 이벤트가 발생하여 부모로 이벤트가 전파
- 이벤트 타켓(본인) -> 바로 부모에 이벤트 실행 (최상단 부모까지)

```html
<div id="first">first
    <div id="second">second
        <div id="third">third</div>
    </div>
</div>
```

```js
// Capturing 실행되고 Bubbling 나중에 된다
var first = document.querySelector('#first');
var second = document.querySelector('#second');
var third = document.querySelector('#third');

var allElements = [first, second, third];

function setEventCapturing(index) {
    allElements[index].addEventListener('click', function() {
        console.log('capturing:' + allElements[index].id);
    }, true);
}

function setEventBubbling(index) {
    allElements[index].addEventListener('click', function(event) {
        console.log(event.type); // click
        console.log('bubbling:' + allElements[index].id);
    });
}

for(var i = 0; i < allElements.length; i++) {
    setEventCapturing(i);
    setEventBubbling(i);
}
```

```js
// for문안에 addEventListener 넣을 경우
// i가 최종 가리키는 4번째 값이 없기 때문에 (undefined)에러가 난다
for(var i = 0; i < allElements.length; i++) {
    allElements[i].addEventListener(function(e) {
        console.log('capturing:' + allElements[i].id);
    }, true);
}
```

