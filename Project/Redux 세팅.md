1. 아래의 명령어 입력

```markdown
npm install redux react-redux
```

<br>

2. Action.js, Reducer.js(+index.js), Type.js 만들기

```jsx
// Type.js
export const LOGIN_SUCCESS = 'LOGIN_SUCCESS';
```

```jsx
// Action.js
import {
  LOGIN_SUCCESS,
} from '../Type/LoginType';

export const LoginSuccess = id => {
  return {
    type: LOGIN_SUCCESS,
    payload: id,
  };
};
```

```jsx
// Reducer.js
import {
  LOGIN_SUCCESS,
} from '../Type/LoginType';

const initialState = {
  isLoggedin: false,
  userInfo: {},
};

const LoginReducer = (state = initialState, { type, payload }) => {
  switch (type) {
    case LOGIN_SUCCESS:
      return {
        ...state,
        isLoggedIn: true,
        userInfo: {
          email: payload.email,
          nickname: payload.nickname,
          role: payload.role,
          password: '',
        },
      };
    default:
      return state;
  }
};
```

```jsx
// index.js
import { combineReducers } from 'redux';
import LoginReducer from './LoginReducer';

export default combineReducers({
  LoginReducer,
});
```

<br>

3. store.js 만들기

```jsx
import { createStore } from 'redux';

const store = createStore(Reducer index 넣기);

export default store;
```

<br>

4. index.js 수정

```jsx
/* Redux */
import { Provider } from 'react-redux';
import store from './Redux/store';

ReactDOM.render(
  <React.StrictMode>
    <Provider store={store}>
      <App />
    </Provider>
  </React.StrictMode>,
  document.getElementById('root'),
);
```
