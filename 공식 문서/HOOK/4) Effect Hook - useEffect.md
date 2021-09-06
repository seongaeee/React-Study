## Effect Hook - useEffect

### side effects

> `side effects(effects)`: 리액트의 함수형 컴포넌트의 `로컬 상태`를 `컴포넌트 밖`에서 변경

> 컴포넌트 안에서 데이터를 가져오거나(fetch를 사용해서 api 정보를 가져오는 등) DOM을 직접 조작(onClick 등)하는 작업.

**왜 필요할까?**

`비동기 처리`를 한다고 하였을때, 값을 받아오기 위해 lifycycle 중에 서버와 통신하게 되면 화면이 잠시 멈춘다.

`effects`는 컴포넌트의 lifecycle과 무관하게 state를 업데이트하므로 유용하다.

<br>

### useEffect란?

> `useEffect`: function component 내에서 Side effects가 가능하게 한다.

- useEffect가 하는 일?

리액트에게 컴포넌트가 `렌더링 이후`에 어떤 일을 수행해야 하는지 알려준다.  
리액트는 우리가 넘긴 함수(effect라고 부른다)를 기억했다가 `DOM 업데이트를 수행한 이후`에 불러낸다.

```
렌더링, DOM 업데이트?
- 컴포넌트가 마운트 됐을 때 (처음 나타났을 때)
- 언마운트 됐을 때 (사라질 때)
- 업데이트 될 때 (특정 props, state가 바뀔 때)
```

- 렌더링의 정확한 과정은 다음과 같다.

```
1) 초기 렌더링
- 컴포넌트 정의
- 컴포넌트 정보를 이용해 렌더링(화면구성)
- 문자열 형식의 html코드 변환
- DOM 요소 주입

2) 리렌더링(업데이트)
- 데이터 업데이트
- 업데이트 된 데이터를 이용해 리렌더링
- 이전의 컴포넌트와 리렌더링된 컴포넌트 차이 비교
- 바뀐 요소들만 DOM에 반영
```

- useEffect를 컴포넌트 안에서 불러내는 이유?

컴포넌트 내부에 둠으로써 effect를 통해 `state` 변수(또는 그 어떤 prop에도)에 접근할 수 있게 된다.

- useEffect는 렌더링 이후에 매번 수행되는지?

그러하다. 기본적으로 첫번째 렌더링과 이후의 `모든 업데이트에서 수행`된다.  
리액트는 effect가 수행되는 시점에 이미 DOM이 업데이트되었음을 보장한다.

- 예시

```javascript
// Class를 사용하는 경우
class Example extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      count: 0
    };
  }

  componentDidMount() {
    document.title = `You clicked ${this.state.count} times`;
  }
  componentDidUpdate() {
    document.title = `You clicked ${this.state.count} times`;
  }
...
```

```javascript
// Hook을 이용하는 예시
import React, { useState, useEffect } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    document.title = `You clicked ${count} times`;
});
...
```

<br>

### useEffect 조건

다음과 같이 조건문 안에 `useEffect`를 쓸 수 없다.

```javascript
if (value > 1) {
  useEffect(() => {});
}
```

대신 `useEffect`안에 조건문을 써도 된다.

<br>

### useEffect dependency

`useEffect`을 사용하는 방법은 3가지가 있다.

```javascript
useEffect(() => {});
```

`dependency`가 없다면, 렌더링 할때마다 `useEffect`가 호출된다.

```javascript
useEffect(() => {}, []);
```

`dependency`가 있지만 아무 값이 들어있지 않다면, 초기 렌더링 할때만 `useEffect`가 호출된다.

```javascript
useEffect(() => {}, [name]);
```

`dependency`안에 변수가 들어있다면, 해당 변수의 값이 변할때만 `useEffect`가 호출된다.

<br>

### useEffect Cleanup

`cleanup(return함수)`는 `componentWillUnmount`와 같은 개념이다. 이는 선택적으로 사용한다.

동작과정은 다음과 같다.

```
1. prop나 state 업데이트
2. 컴포넌트 리렌더링
3. 이전 이펙트 클린업
4. 새로운 이펙트 실행
```

```javascript
useEffect(() => {
  ChatAPI.subscribeToFriendStatus(props.friend.id, handleStatusChange);
  return () => {
    ChatAPI.unsubscribeFromFriendStatus(props.friend.id, handleStatusChange);
  };
});
```

예시를 통해 자세히 알아보자.

해당 코드는 show를 눌러 화면 크기가 바뀔때마다 호출된다.

```java
useEffect(() => {
  window.addEventListener("resize", checkSize);
});
```

<img src="https://user-images.githubusercontent.com/62600984/132212197-2dad9f6f-e4fa-4abd-ac30-88489b01e6b5.png" width=400>

해당 코드는 show를 누를때마다 호출되며, 이전 이벤트가 사라지않는다.

```java
useEffect(() => {
  window.addEventListener("resize", checkSize);
}, []);
```

<img src="https://user-images.githubusercontent.com/62600984/132212234-f72add7f-c9e4-4d65-a0f6-8aec81b33856.png" width=400>

해당 코드는 show를 누를때마다 호출되며, 이전 이벤트가 사라진다.

```java
useEffect(() => {
  window.addEventListener("resize", checkSize);
  return () => {
    window.removeEventListener("resize", checkSize);
  };
}, []);
```


<br>

### useEffect fetch

#### async / await

> 비동기 코드를 마치 동기 코드처럼 보이게 작성할 수 있음

> `await` 해당하는 함수가 끝날때까지 기다림

```java
const users = async() => {
    return await getData();
}
```

#### fetch란?

> Javascript 내장 Web API

#### fetch - get (default)

```javascript
fetch("api 주소")
  .then((res) => res.json())
  .then((res) => {
    // data를 응답 받은 후의 로직
  });
```

`json.parse`는 모든 데이터를 변환시켜주지만 정보가 너무 많기 때문에,  
`json`을 이용해 body에 있는 정보들만 꺼내 변환한다.

`res.status`는 페이지의 상태값(ex. 404)을 가져올수있다.

#### fetch - post

```javascript
fetch("api", {
  method: "post",
  body: JSON.stringify({
    // 보낼 data
  }),
})
  .then((res) => res.json())
  .then((res) => {});
```

<br>

## 참고 블로그

- [[React] 10 - Hooks : useEffect (1)](https://velog.io/@delilah/React-10-Hooks)
- [[React] state & effect Hook 사용하기](https://euzl.github.io/react-hook_2/)
- [[React] 초기 렌더링과 리렌더링](https://brunch.co.kr/@eight-two-five/13)
- [useEffect 완벽 가이드 - 2편, 의존성 배열 deps와 클린업 함수](https://simsimjae.tistory.com/401)
