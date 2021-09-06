## State Hook - useState

> `함수형 컴포넌트`에 `상태`를 부여하는 함수

```javascript
import React, { useState } from "react";

function Example() {
  // "count"라는 새 상태 변수를 선언합니다
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );
}
```

<br>

### useState 특징

- `useState`는 현재의 state 값과 이 값을 업데이트하는 함수를 쌍으로 제공.
- class의 `this.setState`와 거의 유사하지만, 이전 state와 새로운 state를 합치지 않는다는 차이점.
- `useState`는 인자로 초기 state 값을 하나 받음.
- `state`는 컴포넌트가 다시 렌더링 되어도 그대로 유지.

<br>

### useState 사용하기

- state 가져오기

```javascript
<p>You clicked {count} times</p>
```

- state 갱신하기

```javascript
<button onClick={() => setCount(count + 1)}>Click me</button>
```

- state 객체 갱신하기

만약 `setPeople({ message: "hello world" })`으로 작성하면, 나머지 요소들은 삭제된다.

그러므로 `스트레이 연산자`를 이용해서 전체 객체 요소를 가져와야한다.

```javascript
const [people, setPeople] = useState({
  name: "peter",
  age: 24,
  message: "rameom message",
});

const chaneMessage = () => {
  setPeople({ ...people, message: "hello world" });
};
```

- 유동적으로 state 갱신하기

<br>

#### 예시 1 - setTimeout

첫번째 코드는 2초안에 숫자가 변경되도, 그값을 무시하고 원래 가지고있는 값을 `+1`한다.  
두번째 코드는 2초안에 숫자가 변경되면, 그값을 `+1`한다.

```javascript
setTimeout(() => {
  setValue(value + 1);
}, 2000);
```

```javascript
setTimeout(() => {
  setValue((prevState) => {
    return prevState + 1;
  });
}, 2000);
```

<br>

#### 예시2 - filter

```javascript
const removeItem = (id) => {
  let newPeople = people.filter((person) => person.id !== id);
  setPeople(newPeople);
};
```

```javascript
const removeItem = (id) => {
  setPeople((oldPeople) => {
    let newPeople = oldPeople.filter((person) => person.id !== id);
    return newPeople;
  });
};
```
