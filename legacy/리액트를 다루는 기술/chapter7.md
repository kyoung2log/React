`created at 2021.01.17`

`props`는 **properties를 줄인 표현**으로 **컴포넌트 속성을 설정할 때 사용하는 요소**이다. `props` 값은 해당 컴포넌트를 불러와 사용하는 **부모 컴포넌트에서만 설정할 수 있다**.

# 🔴 JSX 내부에서 props 렌더링

> MyComponent.js

```jsx
import React, { Component } from 'react';

class MyComponent extends Component {
  render() {
    return <div>안녕하세요, 제 이름은 {this.props.name} 입니다.</div>;
  }
}

export default MyComponent;
```

`props`에 접근할 때는 **`this` 키워드를 사용**하여 접근한다.

# 🟠 컴포넌트 사용할 때 props 값 설정

> App.js

```jsx
import React, { Component } from 'react';
import MyComponent from './MyComponent';

class App extends Component {
  render() {
    return <MyComponent name='React' />;
  }
}

export default App;
```

내가 만든 MyComponent의 name 속성을 설정 할 수 있다.

# 🟡 props 기본 값 설정 : defaultProps

위의 App.js 코드에서 `<MyComponent />` 의 `name="React”`를 지우게 되면 웹 브라우저에는 다음과 같이 출력된다.

**`props`** **값을 지정하지 않았을 때 기본 값으로 설정하는것을 `defaultProps`** 라고 한다. 다음은 `defaulProps`를 설정하는 전통적인 방법이다.

> MyComponent.js

```jsx
import React, { Component } from 'react';

class MyComponent extends Component {
  render() {
    return <div>안녕하세요, 제 이름은 {this.props.name} 입니다.</div>;
  }
}

MyComponent.defaultProps = {
  name: '기본 이름',
};

export default MyComponent;
```

defaultProps는 **클래스 내부에서 정의**할 수도 있다. 이 방법은 ES6 문법에서는 작동하지 않지만, create-react-app으로 만든 프로젝트는 기본적으로 transform-class-properties 문법을 사용해 ES6에서 적용할 수 있다.

> MyComponent.js

```jsx
import React, { Component } from 'react';

class MyComponent extends Component {
  static defaultProps = {
    name: '기본 이름',
  };
  render() {
    return <div>안녕하세요, 제 이름은 {this.props.name} 입니다.</div>;
  }
}

export default MyComponent;
```

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9dd0191b-c4b3-4dc8-ab3a-2a041af859b9/Untitled.png)

# 🟢 props 검증 : propTypes

컴포넌트의 필수 `props`를 지정하거나 **`props`타입을 지정할 때는 `propTypes`**를 사용한다.

> MyComponent.js

```jsx
import React, { Component } from 'react';
import PropTypes from 'prop-types';

class MyComponent extends Component {
  static defaultProps = {
    name: '기본 이름',
  };
  render() {
    return <div>안녕하세요, 제 이름은 {this.props.name} 입니다.</div>;
  }
}

MyComponent.propTypes = {
  name: PropTypes.string,
};

export default MyComponent;
```

코드 위쪽에 **`import PropTypes from 'prop-types'`** 를 적어주어 `propTypes`를 부른다.

그 다음에는 `defaultProps` 처럼 클래스 밖에서 설정해도 되고, 클래스 내부에서 설정할 수도 있다.

> MyComponent.js

```jsx
import React, { Component } from 'react';
import PropTypes from 'prop-types';

class MyComponent extends Component {
  static defaultProps = {
    name: '기본 이름',
  };
  static propTypes = {
    name: PropTypes.string,
  };
  render() {
    return <div>안녕하세요, 제 이름은 {this.props.name} 입니다.</div>;
  }
}

export default MyComponent;
```

`name props` 의 `type`을 문자열로 설정했다.

> App.js

```jsx
import React, { Component } from 'react';
import MyComponent from './MyComponent';

class App extends Component {
  render() {
    return <MyComponent name={3} />;
  }
}

export default App;
```

다음과 같이 App 컴포넌트에서 `MyComponent`의 `name`의 값에 문자열이 아닌 숫자를 전달해 준다면 브라우저의 개발자 도구에서는 다음과 같은 오류가 발생한다.

`name`의 `propTypes`를 문자열로 설정해 주었지만 전달된 값은 숫자이기 때문이다.

또한, **문자열 종류 외의 값을 컴포넌트에 전달할 때에는 `{}`**로 감싸주어야 한다.

### 필수 propTypes 설정

`props`를 지정하지 않았을 때, 오류 창을 띄우게 설정할 수 있다. **`propTypes`를 설정할 때 뒤에 `isRequired` 를 붙여 주면 된다.**

> MyComponent.js

```jsx
import React, { Component } from 'react';
import PropTypes from 'prop-types';

class MyComponent extends Component {
  static defaultProps = {
    name: '기본 이름',
  };
  static propTypes = {
    name: PropTypes.string,
    age: PropTypes.number.isRequired,
  };
  render() {
    return (
      <div>
        <p>안녕하세요, 제 이름은 {this.props.name} 입니다. </p>
        <p>저는 {this.props.age} 살 입니다.</p>
      </div>
    );
  }
}

export default MyComponent;
```

### 더 많은 propTypes 종류

- `array` : 배열
- `bool` : 참, 거짓
- `func` : 함수
- `number` : 숫자
- `object` : 객체
- `string` : 문자열
- `symbol` : ES6 문법의 심벌 개체
- `node` : 렌더링할 수 있는 모든 것(숫자, 문자열, element 또는 이들로 구성된 배열)
- `element` : 리액트 요소
- `instanceOf(MyClass)` : 특정 클래스의 인스턴스
- `oneOf([’Male’, ‘Female’])` : 주어진 배열 요소 중 값 하나
- `oneOfType([React.PropTypes.string, React.PropTypes.number])` : 주어진 배열 안의 종류 중 하나
- `arrayOf(React.PropTypes.number)` : 주어진 종류로 구성된 배열
- `objectOf(React.PropTypes.number)` : 주어진 종류의 값을 가진 객체
- `shape({name : React.PropTypes.string, age : React.PropTypes.number})` : 주어진 스키마를 가진 객체
- `any` : 아무 종류

### defaultProps와 propTypes는 꼭 사용해야 하나요?

이 두 가지 설정은 컴포넌트의 필수 사항은 아니지만, 큰 규모의 프로젝트를 진행해 다른 개발자와 협업을 한다면, 해당 컴포넌트에 어떤 `props`가 필요한지 쉽게 알 수 있어 개발 능률을 올릴수 있다.
