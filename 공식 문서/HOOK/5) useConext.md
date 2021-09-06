## useConext

> createContext: context 생성

> useContext: context 조회

### 참고 사이트

- [React Hooks: useContext](https://xiubindev.tistory.com/105)

<br>

## useRef

> 1. 특정 DOM을 선택 (js의 `getElementtById()`와 같은 기능)

> 2. 컴포넌트의 독립적인 데이터이며, 리렌더링 여부와 상관없이 같은 값이 유지

- Ref 객체 생성

useRef에 파라미터를 넣어주면(initialValue), `.current`의 기본값이 된다.

```java
import React, { useRef } from 'react';

const refContainer = useRef(initialValue);
```

- 선택하고 싶은 DOM에 속성으로 ref값 설정

```java
<input ref={refContainer}/>
```

처음에 `initialValue`값과 `Element`값을 가지고 있는 것을 볼 수 있다.

<img src="./images/2021-07-07-16-09-25.png./" width=500>

ref 속성으로 연결이되면 `Element`값으로 세팅이 된다.

<img src="./images/2021-07-07-16-18-14.png./" width=500>

- DOM 처리
  `.current`는 선택하고자하는 DOM을 가리킨다.

```java
//ex. 포커싱하기

refContainer.current.focus();
```
