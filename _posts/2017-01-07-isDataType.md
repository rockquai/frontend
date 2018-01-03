---
layout: post
title:  "올바른 데이터 유형을 체크하는 방법"
date:   2017-01-07
categories: [JavaScript]
comments: true
tags: [JavaScript,VanillaJS]
---

## 올바른 데이터 유형을 체크하는 방법
- `typeof` 키워드
- `instanseof` 키워드
- `.constructor` 속성
- 사용자 정의 헬퍼 함수 `isDtatType()`

<!--more-->

### 1. typeof 키워드
- typeof의 치명적인 설계 오류 : null, []를 올바르게 인식하지 못한다.

```javascript
var nu  = null, arr = [];

console.log('null', typeof nu); // object
console.log('arrary', typeof arr); // object
``` 

### 2. instanseof 키워드
- 실체화된 객체`instance` <-> 객체를 생성하는 생성자`constructor`
- e.g. Adobe Flash,  Adobe Illustrator, Sketch => `Symbols` 개념
- {실체화된 객체} `instanceof` [객체를 생성하는 생성자]
- 객체가 동일 객체형의 인스턴스이면 `true`를 반환한다.

```javascript
var check_array_data = arr instanceof Array;
var is_check_array_data = arr instanceof Object;
```

- 객체만이 생성자를 가진다. `null` 객체가 아니다. `null` 유형은 instanceof 키워드를 사용하여 데이터 체크가 불가능
- 이유는 instanceof 키워드는 객체만 판별이 가능!!!
- 객체가 아닌 것들(`null`, `undefined`)에는 사용할 수 없다.
- instanceof 키워드 사용시 주의가 필요한 부분 : 원시데이터 유형(9, '문자', false)은 올바르게 체크할 수 없다.
- 원시데이터는 값이기 때문에. instanceof의 조각이 아니기 때문에 쓸 수가 없다. 

```javascript
var num = 10, 
	str = 'java vs javascript',
	boo = !false;

console.log('num instanceof Number', num instanceof Number);  // false
console.log('num instanceof Number', num instanceof String);  // false
console.log('num instanceof Number', num instanceof Boolean); // false
```

### .constructor (생성자)
- 자바스크립트에 존재하는 실체화된 모든 객체(instance Object)는 기본적으로 가지고 있는 속성이다.
- {object}.constructor 속성(Property)
- 객체가 아닌 것들(null, undefined)에는 사용할 수 없다.

```javascript

var num = 10,
	str = 'java vs javascript',
	boo = !false,
	fnc = function() {},
	arr = [],
	obj = {};

console.log( 'num.constructor:', num.constructor ); // function Number() { [native code] }
console.log( 'num.constructor === Number:', num.constructor === Number ); // true

console.log( 'str.constructor:', str.constructor ); // function String() { [native code] }
console.log( 'str.constructor === String:', str.constructor === String ); // true

console.log( 'boo.constructor:', boo.constructor ); // function Boolean() { [native code] }
console.log( 'str.constructor === Boolean:', str.constructor === Boolean ); // true

console.log( 'fnc.constructor:', fnc.constructor ); // function Function() { [native code] }
console.log( 'fnc.constructor === Function:', fnc.constructor === Function ); // true

console.log( 'arr.constructor:', arr.constructor ); // function Array() { [native code] }
console.log( 'arr.constructor === Array:', arr.constructor === Array ); // true

console.log( 'obj.constructor:', obj.constructor ); // function Object() { [native code] }
console.log( 'arr.constructor === Object:', obj.constructor === Object ); // true
```

### 4. 데이터 유형을 올바르게 체크해주는 `isDataType()` 헬퍼 함수
- `Object` 모든 객체의 조상이자, 객체 생성자 함수
- 생성자 함수의 특징은 함수 이름의 첫 글자는 대문자.
- 생성자 함수는 `.prototype` 속성을 가짐.

#### [방법 1] `Object.prototype` 원형 객체의 능력 중에는 `.toString()` 함수가 있다.

```javascript
console.log(typeof Object.prototype.toString); // function
```

#### [방법 2] `Object.prototype.toString` 함수는 누군가 빌려쓸 수 있다. `메소드 빌려쓰기: call({data})`

```javascript
Object.prototype.toString.call({data}); // [Object {Date}]
```

#### [방법 3] 문자열에서 해당 데이터 이름을 가진 것을 잘라내야`slice` 한다.

```javascript
Object.prototype.toString.call({data}).slice(8, -1); // Data
```

#### [방법 4] 잘라낸 문자열(Data)을 `소문자`로 반환.

```javascript
Object.prototype.toString.call({data}).slice(8, -1).toLowerCase(); // data
```

### [완성] 데이터 유형을 올바르게 체크해주는 `isDataType()` 헬퍼 함수

```javascript
function isDataType(data) {
	return Object.prototype.toString.call(data).slice(8, -1).toLowerCase(); 
}
``` 
