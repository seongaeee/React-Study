## Redux 시작하기

<br>

1. Redux 설치

```
npm install redux react-redux
```

<br>

2. Reducer 만들기

```javascript
//reducer
const counter = (state = 0, action) => {
  switch (action.type) {
    case "INCREMENT":
      return state + 1;
    case "DECREMENT":
      return state - 1;
  }
};
```

<br>

3. Redux 저장소 만들기

```javascript
import { createStore } from 'redux';
let store = createStore(counter);
```

`createStore` API로는 { `subscribe`, `dispatch`, `getState` }가 있다.

<br>

4. state 확인하기

`subscribe` 함수에 특정 함수를 전달해주면, 변화가 감지(액션이 디스패치) 되었을 때 마다 전달해준 함수가 호출된다.

리액트에서 리덕스를 사용하게 될 때 보통 이 함수를 직접 사용하는 일은 별로 없습니다. 그 대신에 react-redux 라는 라이브러리에서 제공하는 connect 함수 또는 useSelector Hook 을 사용하여 리덕스 스토어의 상태에 구독한다.

```javascript
store.subscribe(() => console.log(store.getState()));
```

<br>

5. action 만들기

```javascript
// action
const increament = () => {
  return {
    type: "INCREMENT",
  };
};
```

<br>

6. dispatch로 action 발생시키기

```javascript
store.dispatch(increament());
```

<br>

### 전체 샘플 코드

```javascript
import { createStore } from "redux";

// action
const increament = () => {
  return {
    type: "INCREMENT",
  };
};

const decrement = () => {
  return {
    type: "DECREMENT",
  };
};

//reducer
const counter = (state = 0, action) => {
  switch (action.type) {
    case "INCREMENT":
      return state + 1;
    case "DECREMENT":
      return state - 1;
  }
};

let store = createStore(counter);

//display it in the console
store.subscribe(() => console.log(store.getState()));

//dispatch
store.dispatch(increament());
store.dispatch(decrement());
```
