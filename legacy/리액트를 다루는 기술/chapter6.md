`created at 2021.01.17`

# 1️⃣ src 디렉터리 내부에 MyComponent.js 파일 생성

# 2️⃣ 컴포넌트 초기 코드 작성

> MyComponent.js

```jsx
import React, { Component } from 'react';

class MyComponent extends Component {
  render() {
    return <div>나의 새롭고 멋진 컴포넌트</div>;
  }
}

export default MyComponent;
```

# 3️⃣ 모듈 내보내기 및 불러오기

### **모듈 내보내기(export)**

```jsx
export default MyComponent;
```

이 코드는 다른 파일에서 이 파일을 `import` 할 때, 위쪽에서 선언한 MyComponent 클래스를 불러오도록 설정한다.

### **모듈 불러오기(import)**

> App.js

```jsx
import React, { Component } from 'react';
import MyComponent from './MyComponent';

class App extends Component {
  render() {
    return <MyComponent />;
  }
}

export default App;
```
