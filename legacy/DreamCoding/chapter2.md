`created at 2023.02.10`

## 🎃 **왜 리액트인가?**

- 웹, 모바일 앱을 손쉽게 만들수 있게 해준다.
- 심플한 정적 사이트부터 복잡한 규모까지!
- 정말 많은 곳에서 리액트를 사용하며 가장 많이 쓰이는 웹프레임워크이다.
- SPA(Single Page Application), CSR(Client Side Rendering)

## 🎃 라이브러리와 프레임워크 차이점

- 프레임워크 : routing, ui, State management, http clients 모두 갖춰져 있는 것으로 다 알아야함(앵귤러나 안드로이드스튜디오)
- 라이브러리 : 조금 더 좁은 문제를 해결하기 위한 작은 솔루션 단위
- 리액트는 자바스크립트의 라이브러리로 UI를 만들수 있게 도와준다. 따라서, 필요 시에 네트워크나 라우팅, 상태관리 등의 다양한 라이브러리 선택하여 사용하면 된다.

## 🎃 리액트 철학

- 리액트란 컴포넌트들의 집합으로 리액트 어플리케이션을 잘 만든다는것은 컴포넌트들을 잘 만드는 것이다.
- 좋은 컴포넌트란? 컴포넌트 내부에서는 응집도가 높고 다른 컴포넌트들과는 연결되어 있지 않고, 독립적이며 재사용성이 높은 컴포넌트이다.

## 🎃 컴포넌트 나누는 기준?

- **재사용성** : DRY Don’t Repeat Yourself
- **단일책임** : SR Single Responsibility

## 🎃 리액트 동작 원리

- 리액트는 컴포넌트들의 집합이며, 컴포넌트는 함수형태로 정의되며 함수의 반환값은 자바스크립트의 XML 문법인 **`JSX`**이다.
- 리액트는 데이터의 **`State`**(내부상태)와 **`Props`**(외부로부터 전달받은 상태)를 나타내는 **`Render`**가 있다.
- 리액트는 **`Virtual Dom Tree`**를 가지며 이전의 돔트리와 변경되는 부분만 확인하여 상태가 변경될때마다 **`Re-Render`** 되며, 실제로 변경된 부분만 화면에 업데이트 된다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bcd17b76-e954-4176-aaae-7a3a518fc111/Untitled.png)

## 🎃 리액트 훅이란?

- 기존 클래스 컴포넌트의 로직들은 재사용이 어려웠고, this 바인딩 이슈가 있어 함수형 컴포넌트가 개발되었다.
- 리액트훅이란 리액트의 재사용가능한 로직들(State and lifecycle feature)을 의미하며 use로 시작한다.(예 : **`useState`**, **`useEffect`**, **`useUser`**, **`useRef`**, **`useMemo`**, **`useCallback`** etc.)
