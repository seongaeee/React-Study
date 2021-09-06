## map

`map()`은 입력 배열을 처리하여 새로운 배열을 반환하는 함수이다.

이를 통해, 배열을 `엘리먼트 리스트`로 만들 수 있다.

```javascript
const numbers = [1, 2, 3, 4, 5];
const listItems = numbers.map((number) => <li>{number}</li>);
```

<br>

### 리스트 컴포넌트

컴포넌트에 리스트를 렌더링하면 중복되는 객체 처리에 용이하다.

```javascript
function NumberList(props) {
  const numbers = props.numbers;
  const listItems = numbers.map((number) => <li>{number}</li>);
  return <ul>{listItems}</ul>;
}
```

<br>

## filer

`filter()`는 주어진 함수를 통과하는 요소들을 모아 새로운 배열을 리턴해준다.

```javascript
array.fliter((num) => num !== 3);
```

<br>

## Key

> 엘리먼트에 안정적인 `고유성`을 부여

```javascript
const numbers = [1, 2, 3, 4, 5];
const listItems = numbers.map((number) => <li key={number.toString()}>{number}</li>);
```
