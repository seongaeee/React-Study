## 컴포넌트란?

> UI 재사용 가능한 개별적인 여러 조각

<br>

### 함수 컴포넌트

```javascript
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```

<br>

### 화살표 함수 표현

화살표 함수를 통해 `간단`하게 함수 컴포넌트를 생성할 수 있다.

```javascript
const Person = () => <h2>john doe</h2>;
const Message = () => {
  return <p>this is my message</p>;
};
```

<br>

### 컴포넌트 합성

컴포넌트는 자신의 출력에 `다른 컴포넌트`를 참조할 수 있다.

```javascript
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

function App() {
  return (
    <div>
      <Welcome name="Sara" />
      <Welcome name="Cahal" />
      <Welcome name="Edite" />
    </div>
  );
}

ReactDOM.render(<App />, document.getElementById("root"));
```

<br>

### 클래스 컴포넌트

```javascript
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```

<br>

## Props

### Props 처리

props는 `읽기 전용`이다.

따라서 props를 `순수 함수`을 통해 처리해야한다.

> 순수 함수: 입력 값을 바꾸려 하지 않는 함수

- 순수 함수

```javascript
function sum(a, b) {
  return a + b;
}
```

- 비순수 함수

```javascript
function withdraw(account, amount) {
  account.total -= amount;
}
```

<br>

### 컴포넌트와 Props

상위 컴포넌트가 하위 컴포넌트에게 전달해주는 데이터를 `props`라고 한다.

`상위 컴포넌트`에서 태그에 `속성`을 전달하면,

`하위 컴포넌트`에서 `props.속성`을 통해 속성 값을 이용할 수 있다.

만약 props에서 전달하지 않은 속성 값을 참조해도 오류는 나지 않는다.

```javascript
function BookList() {
  return (
    <div>
      <Book job="developer" />
    </div>
  );
}
```

```javascript
const Book = (props) => {
  return(
    <div>
      <h1>{div.job}<h1>
    </div>
  );
}
```

<br>

### Props Destructuring

> Destructuring: 비구조화 / 구조 분해, 객체에서 값을 추출하는 문법

- Before Destructuring Assignment

```javascript
const Greet = (props) => {
  return (
    <div>
      <h1>
        Hello {props.name} a.k.a {props.heroName} // 객체이므로 이렇게 사용할 수 있다.
      </h1>
    </div>
  );
};
```

- After Destructuring Assignment (1) : 함수 인자 안에서 분해

```javascript
const Greet = ({ name, heroName }) => {
  // props 객체가 여기로 전달되므로, 이 자리에서 직접 프로퍼티를 추출할 수 있다.
  console.log(name); // Diana
  return (
    <div>
      <h1>
        Hello {name} a.k.a {heroName} // value가 출력된다.
      </h1>
    </div>
  );
};
```

- After Destructuring Assignment (2) : 함수 본문 안에서 분해

```javascript
const Greet = (props) => {
  const { name, heroName } = props;
  return (
    <div>
      <h1>
        Hello {name} a.k.a {heroName}
      </h1>
    </div>
  );
};
```

<br>

### Spread Operator (전개 구문)

> Spread Operator: 배열, 객체의 값들을 받아오거나 확장.

```javascript
const singerOne = ["청하", "여자아이들", "우주소녀"];
const singerTwo = ["홍대광", "악동뮤지션", "볼빨간사춘기"];
const combinedOne = singerOne.concat(singerTwo); // Spread Operator 쓰지 않을때
const combinedTwo = [...singerOne, ...singerTwo];
```

```javascript
const singerName = {
  name: "청하",
};
const singerAge = {
  age: "24",
};
const combinedSinger = {
  ...singerName,
  ...singerAge,
  birthplace: "대한민국",
};
```

이를 React에 Props에 적용해보면 다음과 같다.

```javascript
books = [
  {
    img: __,
    title: __,
    author: __,
  },
  {
    img: __,
    title: __,
    author: __,
  },
];

function BookList(){
  return(
    <div>
      {books.map((book) => {
        return <Book {...book}>
      })}
    </div>
  );
}

const Book = ({img, title, author}) => {
  return ();
}
```

<br>

## 참고 블로그

- [React에 필요한 Javascript 개념정리(2)](https://medium.com/@saerombang11/react%EC%97%90-%ED%95%84%EC%9A%94%ED%95%9C-javascript-%EA%B0%9C%EB%85%90%EC%A0%95%EB%A6%AC-2-eddaac716f75)
