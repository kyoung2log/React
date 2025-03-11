`created at 2021.01.16`

# 💥 코드 이해

> **src/App.js**

```jsx
import React, { Component } from 'react';
import logo from './logo.svg';
import './App.css';

function App() {
  return (
    <div className='App'>
      <header className='App-header'>
        <img src={logo} className='App-logo' alt='logo' />
        <p>
          Edit <code>src/App.js</code> and save to reload.
        </p>
        <a className='App-link' href='https://reactjs.org' target='_blank' rel='noopener noreferrer'>
          Learn React
        </a>
      </header>
    </div>
  );
}

export default App;
```

### Module 사용

```jsx
 import React, {Component} from ‘react’;
```

위의 코드는 ‘node module 안에 있는 react 로부터 React를 사용하겠다’라는 의미이다.

### 번들링 (bundling)

파일을 모듈화해서 사용하는것은 Node.js의 기능으로 웹 브라우저에서는 이 기능을 지원하지 않는다. 하지만 **번들링(bundling) 도구**를 사용하면 `require`이나 `import`로 모듈을 불러왔을때 번들링되면서 여러개의 모듈을 하나로 합쳐준다. **번들(bundle)은 ‘묶는다’는 뜻으로 파일을 ‘묶듯이’ 연결하는 것**이다.

리액트 프로젝트에서는 src/index.js를 시작으로 필요한 파일을 다 불러와 합쳐준다.

번들링 도구는 Browserify, RequireJS webpack이 대표적인데, **리액트에서는 편의성과 확장성이 뛰어난 webpack**을 사용한다.

### 로더(loader)

번들링된 **파일들을 불러오는것은** **webpack의 로더(loader)**가 담당한다.

loader의 종류는 여러가지가 있다.

- css-loader : css 파일을 불러온다.
- file-loader : 웹 폰트나 미디어 파일을 불러온다.
- babel-loader : js 파일들을 불러오면서 ES6로 작성된 코드를 ES5 문법으로 변환해준다.

로더는 원래 직접 설치하고 설정해야 하지만, create-react-app이 이러한 과정을 대신해준다.

### 클래스 선언

```jsx
class App extends Component {
```

위의 코드는 App 이라는 클래스를 선언하는것이다. 이 클래스는 리액트 라이브러리 내부에 있는 `Component` 클래스를 상속한다.

새로운 클래스를 만들때는 다음과 같이 클래스를 선언한다.

```jsx
class Dog {
	constructor(name) {
		this.name = name;
	}
	say() {
		console.log(this.name + ' : 멍멍');
	}
}

const dog = new Dog('흰둥이');
dog.say(); //흰둥이 : 멍멍

render() {
	return (
		<div className="App">
			<div className="App-header">
				<img src={logo} className="App-logo" alt="logo" />
				<h2>Welcome to React</h2>
			</div>
			<p className="App-intro">
				To get started, edit <code>src/App.js</code> and save to reload.
			</p>
		</div>
	);
}
```
