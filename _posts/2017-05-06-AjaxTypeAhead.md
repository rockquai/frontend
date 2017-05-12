---
layout: post
title:  "Ajax Type Ahead"
date: 2017-05-06
categories: [JavaScript30]
comments: true
tags: [JavaScript,ES6,VanillaJS]
image:
  feature: ../assets/javascript30/js30-06.jpg
---

### [Fetch API](http://hacks.mozilla.or.kr/2015/05/this-api-is-so-fetching/)
- Fetch API 의 가장 유용하고, 핵심적인 함수는 `fetch()` 함수
- 가장 간단한 형태의 `fetch()` 함수는 URL 을 인자로 받고 응답을 처리하기 위한 `promise`를 반환.
- 응답을 처리할 때 `Response` 객체를 이용 할 수 있다

<!--more-->

{% highlight javascript %}
fetch(endpoint)
    .then(blob => blob.json())
    .then(data => cities.push(...data));
{% endhighlight %}

### code & view
- [github code](https://github.com/rockquai/JavaScript30/blob/master/06-Ajax%20Type%20Ahead/script.js)
- [view](https://rockquai.github.io/JavaScript30/06-Ajax%20Type%20Ahead/)

##### [출처 : [javascript30.com] 30 Day Vanilla JS Coding Challenge](https://javascript30.com/)
