## Redux

> 상태관리 라이브러리

> 모든 컴포넌트들이 state 를 쉽게 공유

`리액트`의 데이터 흐름은 `단방향`이다.

이는 몇 가지 까다로운 상황을 만들게 된다.  
부모 컴포넌트에서 최하위 자식까지 상태를 전달할때 긴 경로를 거치게 되며,  
좌측 하단의 자식 컴포넌트에서 발생한 이벤트에 의해 다른 루트에 있는 컴포넌트의 상태 변화를 불러일으켜야 하는 상태에 대한 관리가 어려울 수 있다.

`리덕스`는 이러한 `상태관리`를 효율적으로 제공한다.

즉, 상태값을 컴포넌트에 종속시키지 않고, 상태관리를 `바깥`에서 할 수 있게 해준다.

<img src="https://user-images.githubusercontent.com/62600984/132782514-ab3ec4f0-3035-4b24-80e6-f4e9cf7dd4a7.png" width=700>

<>

## Redux의 흐름

<img src="https://user-images.githubusercontent.com/62600984/132782542-178e268b-53c8-4db9-8bc1-0094ba152663.png" width=700>

<img src="https://user-images.githubusercontent.com/62600984/132782556-9b575856-0cca-46ce-a816-edee0a2620d7.png" width=700>
