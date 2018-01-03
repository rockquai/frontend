---
layout: post
title:  "React란?"
date:   2017-06-01
categories: [react]
comments: true
tags: [React,JavaScript,ES6,library]
---

- [출처: inflearn - velopert님 강의](https://www.inflearn.com/course/react-%EA%B0%95%EC%A2%8C-velopert/)
- React 소개 (장점, 단점, 특징)

<!--more-->

---

### [React 소개](https://velopert.com/775)
#### React
- React는 페이스북에서 개발한 유저인터페이스 라이브러리로서 개발자로 하여금 재사용 가능한 UI를 생성.
- 페이스북, 인스타그램, 야후, 넷플릭스를 포함한 많은 큰 서비스에서 사용.

#### React의 장점
- 배우기 간단하다
- 뛰어난 `Garbage Collection` 메모리 관리 성능
- 서버 & 클라이언트 렌더링 (이를 통해 브라우저측의 초기 렌더링 딜레이를 줄이고, SEO 호환도 가능)
- Component의 가독성이 매우 높고 간단하여 쉬운 유지보수가 가능
- 매우 간편한 UI 수정 및 재사용
- 페이스북이 밀어준다
- 다른 프레임워크나 라이브러리와 혼용가능

#### React의 단점
- `VIEW ONLY` 어플리케이션의 View 레이어만 다루므로 이 외의 부분은 다른 기술을 사용해야 함
    - Ajax, Router 등의 기능은 직접 구현하거나 다른 모듈을 설치하여 사용.
- React 버전 v15부터 `IE8 이하 버전을 지원하지 않는다`

#### React의 특징
- `Virtual DOM` 을 사용
- `JSX` : JSX 는 JavaScript 의 확장 문법
- `Components` : React는 모두 Component 에 대한 것. React 개발을 할 때는 모든 것을 Component 로서 생각
