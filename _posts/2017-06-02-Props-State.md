---
layout: post
title:  "props & state"
date:   2017-06-02
categories: [react]
comments: true
tags: [React,JavaScript,ES6,library]
---

- [출처: inflearn - velopert님 강의](https://www.inflearn.com/course/react-%EA%B0%95%EC%A2%8C-velopert/)
- props
- state

<!--more-->

---

### props
- props는 부모 컴포넌트로부터 물려받는 속성
- 컴포넌트 내부의 `Immutable Data`
- JSX 내부에 `{ this.props.propsName }`
- 컴포넌트를 사용 할 때, < > 괄호 안에 `propsName="value"`
- `this.props.children`은 기본적으로 갖고있는 props로서, `<Cpnt>여기에 있는 값이 들어간다.</Cpnt>`

#### props를 이용한 예제

```js
// index.js
import React from 'react'
import ReactDOM from 'react-dom'
import App from './components/App';

ReactDOM.render(
    <App />,
    document.getElementById('root')
);
```

```js
// App.js
import React from 'react';
import Codelab from './Codelab';

class App extends React.Component {
    render(){
        return (
            <Codelab
                name={this.props.name}
                number={this.props.number}
            >
                {this.props.children}
            </Codelab>
        );
    }
}
export default App;
```

```js
// Codelab.js
import React from 'react';

class Codelab extends React.Component {
    render() {
        return (
            <div>
            <h1>Hello {this.props.name}</h1>
            <h2>{this.props.number}</h2>
            <div>{this.props.children}</div>
            </div>
        );
    }
}

// Type 검증
// isRequired : 필수 입력
Codelab.propTypes = {
    name : React.PropTypes.string,
    number : React.PropTypes.number.isRequired
};

// defaultProps : 기본값 설정
Codelab.defaultProps = {
    name : 'Unknown',
    number : '50'
}

export default Codelab;
```

---

### state
- 컴포넌트 내부에서 값을 변경, 활용하기 위한 데이터.
- 유동적인 데이터
- JSX 내부에 `{ this.state.stateName }`
- 초기값 설정이 필수, 생성자(constructor) 에서 `this.state = { }` 으로 설정
- 값을 수정 할 때에는 `this.setState({ val: 'new_val' })`, 렌더링 된 다음엔 `this.state =` 절대 사용하지 말것
- React에서 사용하는 이벤트 시스템은 브라우저에서 사용되는 JavaScript의 네이티브 이벤트와 같은 인터페이스를 가지고 있다

#### state를 이용한 `Counter` 만들기

```js
// App.js
import React from 'react';
import Counter from './Counter';

class App extends React.Component {
    render(){
        return (
            <Counter />
        );
    }
}
export default App;
```

```js
import React from 'react';

class Counter extends React.Component {
    // constructor 파라미터는 props는 Counter가 만들어질때 전달받을 props.
    // super를 통하여 상속받은 `React.Component`. 즉 Parent 생성자 메서드를 먼저 실행.
    // `super(props);`를 먼저 실행해줘야 `this.state`, `props`를 접근할 수 있디.
    // value 기본값
    constructor(props) {
        super(props);
        this.state = {
            value: 0
        };
    }

    // handleClick()의 `this` 알 수 없으므로, 따라 this를 바인딩 해줘야 한다.
    // onClick={this.handleClick.bind(this)}
    handleClick() {
        // bad
        // this.state.value = this.state.value + 1;
        // this.forceUpdate();

        // good
        this.setState({
            value : this.state.value + 1
        });
    }

    render() {
        return (
            <div>
                <h2>{this.state.value}</h2>
                <button onClick={this.handleClick.bind(this)}>Press Me</button>
            </div>
        );
    }
}

export default Counter;
```

### code & view
- [github code](https://github.com/rockquai/React-Express/tree/master/01-03.React-Basic)