## JSX

> JavaScript를 확장한 문법 ( `JS` + `XML` ) 으로 JS와 마크업 코드를 함께 작성할 수 있다.

> React `엘리먼트` 생성

<br>

### JSX에 표현식 사용

JSX의 `{}`안에는 `JavaScript의 표현식`을 넣을 수 있다.

```javascript
const name = "Josh Perez";
const element = <h1>Hello, {name}</h1>;

ReactDOM.render(element, document.getElementById("root"));
```

```javascript
function formatName(user) {
  return user.firstName + " " + user.lastName;
}

const user = {
  firstName: "Harper",
  lastName: "Perez",
};

const element = <h1>Hello, {formatName(user)}!</h1>;

ReactDOM.render(element, document.getElementById("root"));
```

<br>

### JSX도 표현식!

```javascript
function getGreeting(user) {
  if (user) {
    return <h1>Hello, {formatName(user)}!</h1>;
  }
  return <h1>Hello, Stranger.</h1>;
}
```

<br>

### JSX 속성

태그 속성을 정의할 수 있으며

속성이 문자 리터럴이면 `""`, 표현식이면 `{}`을 사용한다.

```javascript
const element = <div tabIndex="0"></div>;
const element = <img src={user.avatarUrl}></img>;
```

<br>

### JSX 자식 정의

태그가 비었다면 `/>`로 바로 닫아줘야한다.

JSX 태그는 자식을 포함할 수 있으며, 자식이 있을땐 `()`로 감싸준다.

```javascript
const element1 = <img src={user.avatarUrl} />;

const element2 = (
  <div>
    <h1>Hello!</h1>
    <h2>Good to see you here.</h2>
  </div>
);
```

<br>

### JSX 주입 공격 방지

모든 항목은 렌더링 되기 전에 `문자열로 변환`되기 때문에, `XXS(익명의 사람이 코드 삽입) 공격 방지`가 가능하다.

<br>

### JSX는 객체!

```javascript
const element = <h1 className="greeting">Hello, world!</h1>;
```

다음과 같이 JSX를 이용하여 엘리먼트를 만들었다.

하지만 JSX는 `React.createElement()`를 호출하는 편리한 문법이다.

```javascript
const element = React.createElement("h1", { className: "greeting" }, "Hello, world!");
```

ReactElement는 내부적으로 다음 값을 가지는 `객체`이다.

```javascript
// 주의: 다음 구조는 단순화되었습니다
const element = {
  type: "h1",
  props: {
    className: "greeting",
    children: "Hello, world!",
  },
};
```

<br>

### JSX에 CSS 적용하기

`style={}`에서 `json`을 넣는 형식이다.

```javascript
<h1 style={{ color: "red" }}>Hello Style!</h1>
```

<br>

## 참고 사이트

-[리액트를 처음부터 배워보자. — 02. React.createElement와 React.Component 그리고 ReactDOM.render의 동작 원리](https://medium.com/react-native-seoul/react-%EB%A6%AC%EC%95%A1%ED%8A%B8%EB%A5%BC-%EC%B2%98%EC%9D%8C%EB%B6%80%ED%84%B0-%EB%B0%B0%EC%9B%8C%EB%B3%B4%EC%9E%90-02-react-createelement%EC%99%80-react-component-%EA%B7%B8%EB%A6%AC%EA%B3%A0-reactdom-render%EC%9D%98-%EB%8F%99%EC%9E%91-%EC%9B%90%EB%A6%AC-41bf8c6d3764)
