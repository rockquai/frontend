---
layout: post
title:  "컴포넌트 매핑을 이용한 'Contact' 만들기"
date:   2017-06-03
categories: [react]
comments: true
tags: [React,JavaScript,ES6,library]
---

- [출처: inflearn - velopert님 강의](https://www.inflearn.com/course/react-%EA%B0%95%EC%A2%8C-velopert/)
- 컴포넌트 매핑 (Component Mapping)

<!--more-->

---

### 컴포넌트 매핑을 이용한 `Contact` 만들기

```js
// index.js
ReactDOM.render(
    <App />,
    document.getElementById('root')
);
```

```js
// App.js
import React from 'react';
import Contact from './Contact';

class App extends React.Component {
    render(){
        return (
            <Contact />
        );
    }
}
export default App;
```

```js
// Contact.js
import React from 'react';
import ContactInfo from './ContactInfo';

class Contact extends React.Component {

    constructor(props) {
        super(props);
        this.state = {
            contactData: [
                { name : 'Abet', phone : '010-0000-0001' },
                { name : 'Betty', phone : '010-0000-0002' },
                { name : 'Charlie', phone : '010-0000-0003' },
                { name : 'David', phone : '010-0000-0004' }
            ]
        }
    }

    // rendering 내부에 메소드 생성
    render() {
        const mapToComponents = (data) => {
            return data.map( (contact, index) => {
                return (<ContactInfo contact={contact} key={index}/>);
            });
        };
        // mapToComponents() 메소드 사용하기
        return (
            <div>
                <h1>Contacts</h1>
                <div>{mapToComponents(this.state.contactData)}</div>
            </div>
        );
    }
}

export default Contact;
```

```js
// ContactInfo.js
import React from 'react';

class ContactInfo extends React.Component {
  render() {
    return (
      <div>{this.props.contact.name} {this.props.contact.phone}</div>
    )
  }
}

export default ContactInfo;
```

### code & view
- [github code](https://github.com/rockquai/React-Express/tree/master/01-03.React-Basic)