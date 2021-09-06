## 클래스 컴포넌트 생명주기

클래스 컴포넌트 때는 라이프사이클이 **컴포넌트**에 중심이 맞춰져 있다.

- 클래스가 마운트 되려할 때(`componentWillMount`),
- 마운트 되고 나서(`componentDidMount`),
- 업데이트 되었을 때(`componentDidUpdate`),
- 언마운트(`componentWillUnmount`) 될 때 실행됐죠.

<br>

## 함수 컴포넌트 생명주기

**특정 데이터**에 대해서 라이프사이클이 진행된다.

클래스 컴포넌트에서는 componentWillMount, componentDidMount, componentDidUpdate, componentWillUnmount를 컴포넌트 당 한 번씩만 사용했다면,

데이터는 여러 개일 수 있으므로, useEffect는 `데이터의 개수에 따라 여러 번 사용`하게 됩니다.

<br>

## 데이터 흐름

그 state로부터 파생된 UI 또는 데이터는, 오직 트리구조에서 `자신의 “아래”`에 있는 컴포넌트에만 영향을 미친다.

<br>

## 참고 블로그

- [React Hooks! useEffect편(React 17버전)](https://www.zerocho.com/category/React/post/5f9a6ef507be1d0004347305)
