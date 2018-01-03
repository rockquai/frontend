---
layout: post
title:  ".forEach() VS .map() VS .filter()"
date:   2017-01-07
categories: [JavaScript]
comments: true
tags: [JavaScript,VanillaJS]
---

- [.forEach()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)
- [.map()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)
- [.filter()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)

<!--more-->

---

### [.forEach()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)
- ECMASCript 5 Edition
- IE 6, 7,8 적용 안됨. 최신 브라우저 적용

```js
var movielist = [];
movielist.push('터널');
movielist.push('덕혜옹주');
movielist.push('부산행');
movielist.push('서울역');

movielist.forEach(function(item, idx) {
	console.log('item:', item); // 원소
	console.log('index: ', index); // 순서
	console.log('arr: ', arr);// 배열
	return 'item '+ idx +': ' + item;
	// console.log(`item: ${item}`, item); //ES2015
});
```

---

### [.map()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)
- ECMAScript 2015
- 크로스브라우징 이슈 

```js
var movielist = [];
movielist.push('터널');
movielist.push('덕혜옹주');
movielist.push('부산행');
movielist.push('서울역');

movielist.map(function(item, index, arr){
	console.log('item' + index + ':', item);
	// 한번만 실행하는 문구.
	// movielist lenght 4개 - 1 = 3이 되는 순간 한번만 실행.
	if ( index === movielist.length - 1 ) {
		 console.log('arr:', arr);
	}
});
```

---

### [.filter()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)

```js
function isBigEnough(value) {
  return value >= 10;
}

var filtered = [12, 5, 8, 130, 44].filter(isBigEnough);

console.log(filtered); //[12, 130, 44]
```

---

##### .forEach() VS .map() VS .filter() 공통점
- 매개변수가 callback 이고 callback을 실행할 때 this로서 사용하는 값.
- 매개변수로 들어간 callback 함수의 매개변수는 item(element), index, array 순서로 들어간다.  
- `IE하위버전(IE 6, 7, 8)`에 쓸 수 없다. `ECMASCript 5 Edition`
> 크로스브라우징 이슈 발생. 하위브라우저 `polyfill` 사용(작은 코드)

##### .forEach() VS .map() VS .filter() 차이점

  --   | .forEach() | .map() | .filter()
------| ---------- | ------ | ---------
반환   | 반환값이 없다 | 반환값이 있다(새로운 배열) |  반환값이 있다(새로운 배열: true를 반환, 그렇지 않으면 false)
