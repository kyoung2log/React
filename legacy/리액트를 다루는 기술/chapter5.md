`created at 2021.01.17`

# ❤ 감싸진 요소

컴포넌트에 여러 요소가 있다면 **부모요소 하나로 꼭 감싸야 한다**. Virtual DOM에서 컴포넌트 변화를 감지해 낼 때 효율적으로 비교할수 있도록 컴포넌트 내부는 **하나의 DOM 트리구조**로 구성되어야 한다.

```jsx
import React, { Component } from 'react'

class App extends Component {
  render() {
      return (
          <h1>리액트 안녕</h1>
          <h2>당신은 어썸한가요?</h2>
      )
  }
}
export default App;
```

```jsx
import React, { Component } from 'react';

class App extends Component {
  render() {
    const text = '당신은 어썸한가요?';
    const condition = true;

    return (
      <>
        <h1>리액트 안녕</h1>
        <h2>당신은 어썸한가요?</h2>
      </>
    );
  }
}
export default App;
```

리액트 v16 이상에서는 `Fregment` 컴포넌트가 도입되어 `div` 같은 것으로 감싸지 않고 여러 요소를 렌더링 하고 싶다면 리액트를 불러올 때 `Component`와 `Fragment`를 불러와서 사용가능하다.

# 🧡 자바스크립트 표현

JSX 내부에서는 `{ }`로 감싸서 자바스크립트 표현식을 쓸 수 있다.

### ES6의 `const` 와 `let`

**`const`** 는 ES6 문법에서 새로 도입한 것으로 **한 번 지정하고 나면 변경이 불가능한 상수**를 선언할 때 사용하는 키워드이고, **`let`은 동적인 값을 담을 수 있는 변수를 선언** 할 때 사용하는 키워드이다.

`let`과 `const`는 블록단위이므로, `if`문 내부에서 선언한 `a` 값은 `if`문 밖의 `a` 값을 변경하지 않는다.

`let`과 `const`를 사용할 때 **같은 블록 내부에서는 선언이 불가능**하며 **`const`는 한번 선언하면 재설정할수 없다.**

편하게 **기본적으로 `const`를 사용**하고, **해당 값을 바꾸어야 할 때(예 : `for`문)는 `let`을 사용**하면 된다.

# 💛 `if` 문 대신 조건부 연산자

JSX 내부의 자바스크립트 표현식에서는 **`if`문을 사용할 수 없다.** 하지만 **조건에 따라 렌더링**이 필요한 경우에서는 **조건부(삼항) 연산자를 사용**하면 된다.

```jsx
import React, { Component } from 'react';

class App extends Component {
  render() {
    const text = '당신은 어썸한가요?';
    const condition = true;

    return (
      <>
        <h1>리액트 안녕</h1>
        <h2>{text}</h2>
        {condition ? '참' : '거짓'}
      </>
    );
  }
}
export default App;
```

# 💚 `&&` 를 사용한 조건부 렌더링

특정 조건을 만족하거나 만족하지 않을 때, **다른값을 보여주고 싶다**면 위에서 언급한 **삼항 연산자**를 사용하는 것이 맞지만 특정 조건을 **만족할 때는 보여 주고, 만족하지 않을 때는 보여주고 싶지 않다**면 **`&&` 연산자로 조건부 렌더링**을 할수 있다.

JSX에서는 굳이 `null` 값을 사용하지 않아도 `false` 값을 렌더링 하면 아무것도 나타나지 않는다. 또한, JavaScript에서 **`true && expression`은 항상 `expression`으로 평가되고 `false && expression`은 항상 `false`로 평가**되기 때문에, `&&` 연산자를 사용하여 조건부 렌더링이 가능하다.

```jsx
{
  condition ? '보여주세요' : null;
}

{
  condition && '보여주세요';
}
```

# 💙 인라인 스타일링

리액트 DOM 요소에 스타일을 적용할 때에는 **문자열 형태로 적용할 수 없다**. 그러므로 CSS스타일을 **자바스크립트 객체 형식으로 만들어 적용**해야 한다. 이 때 자바스크립트의 객체 `key`에서는 `-`을 사용할수 없으므로, `background-color`는 `backgroundColor`로 바꿔서 작성한다.

```jsx
import React, { Component } from 'react';

class App extends Component {
  render() {
    const text = '당신은 어썸한가요?';
    const condition = true;
    const style = {
      backgroundColor: 'brown',
      border: '1px solid black',
      height: Math.round(Math.random() * 300) + 50,
      width: Math.round(Math.random() * 300) + 50,
      WebkitTransition: 'all',
      MozTransition: 'all',
      msTransition: 'all',
    };
    return (
      <>
        <h1>리액트 안녕</h1>
        <h2>{text}</h2>
        {condition && '보여주세요'}
        <div style={style}></div>
      </>
    );
  }
}
export default App;
```

# 💜 `class` 대신 `className`

리액트에서 `class`를 설정할 때는 **`class` 대신에 `className`을 사용**해야 한다. `class` 키워드는 이미 js에 존재하는 키워드이기 때문이다.

> src/App.js

```jsx
import React, { Component } from 'react';
import './App.css';
class App extends Component {
  render() {
    const text = '당신은 어썸한가요?';
    const condition = true;
    const style = {
      backgroundColor: 'brown',
      border: '1px solid black',
      height: Math.round(Math.random() * 300) + 50,
      width: Math.round(Math.random() * 300) + 50,
      WebkitTransition: 'all',
      MozTransition: 'all',
      msTransition: 'all',
    };
    return (
      <div className='my-div'>
        <h1>리액트 안녕</h1>
        <h2>{text}</h2>
        {condition && '보여주세요'}
        <div style={style}></div>
      </div>
    );
  }
}
export default App;
```

> src/App.css

```jsx
.my-div {
  background-color: aqua;
  font-size: 15px;
}
```

# 🤎 꼭 닫아야 하는 태그

html 코드를 작성할 때, `input`이나 `br` 태그는 태그를 닫지 않아도 문제가 생기지 않지만 **JSX에서는 태그를 꼭 닫아줘야 한다**. 태그를 닫지 않는다면 **Virtual DOM에서 트리 형태의 구조를 만들지 못하기** 때문에 오류가 발생한다.

```jsx
<form>
  First name:
  <br />
  <input type='text' name='firstname' />
  <br />
  Last name:
  <br />
  <input type='text' name='lastname' />
</form>
```

# 🖤 주석

일반적으로 주석을 작성할 때에는 `{/* 이런 형식으로 */}` 작성한다. 하지만 self-closed 요소에서는/>를 다음줄에 작성할 때 `{ }` 없이 작성할 수 있다

```jsx
import React, { Component } from 'react';
import './App.css';
class App extends Component {
  render() {
    const text = '당신은 어썸한가요?';
    const condition = true;
    const style = {
      backgroundColor: 'brown',
      border: '1px solid black',
      height: Math.round(Math.random() * 300) + 50,
      width: Math.round(Math.random() * 300) + 50,
      WebkitTransition: 'all',
      MozTransition: 'all',
      msTransition: 'all',
    };
    return (
      <div className='my-div'>
        {/* 요소 밖에서는 이렇게 작성해요.*/}
        <h1>리액트 안녕</h1>
        <h2>{text}</h2>
        {condition && '보여주세요'}
        <div
          style={style}
          // self-closed 태그에서만 작동하는 주석
          // 마지막 />가 꼭 새 줄에 있어야 합니다.
          /* 이렇게 작성해도 됩니다. */
        />
        // 여기에 쓰는건 그대로 렌더링 됩니다. /* 여기에선 주석 못 써요 */
      </div>
    );
  }
}
export default App;
```
