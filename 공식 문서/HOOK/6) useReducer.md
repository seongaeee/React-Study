## useReducer

> 컴포넌트의 상태 업데이트 로직을 컴포넌트에서 분리

> useRedux와 비슷한 기능

- state: 현재 상태
- dispatch: action을 발생시키는 함수
- reducer: 상태 업데이트 로직을 담은 함수
- initialState: 초기상태

```java
const [state, dispatch] = useReucer(reducer, initialState)
```

```javascript
import React, { useReducer } from "react";

funcion reducer(state, action){
  switch(action.type){
    case 'INCREMENT':
      return state+1;
  }
}

function Counter(){
  const [state, dispatch] = useReucer(reducer, initialState)

  const onIncrease = () => {
    dispatch({type: 'INCREMENT'});
  }

  ...
}
```
