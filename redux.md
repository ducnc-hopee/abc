# Redux

## 1/ Install redux-toolkit

install the required dependencies for Redux Toolkit and Redux Thunk:

```bash
yarn add @reduxjs/toolkit react-redux redux-thunk
```

## 2/ Create slices

You can create slice file as sample code belown:

```tsx
// src/store/slices/authSlice.ts
import { createSlice } from '@reduxjs/toolkit';

type TAuthState = {
  isAuthenticated: boolean;
};

const initialState: TAuthState = {
  isAuthenticated: false,
};

const authSlice = createSlice({
  name: 'auth',
  initialState,
  reducers: {
    login: (state) => {
      state.isAuthenticated = true;
    },
    logout: (state) => {
      state.isAuthenticated = false;
    },
  },
});

export const { login, logout } = authSlice.actions;
export default authSlice.reducer;

```

## 3/ **Set Up Redux Store with Middleware**:

Follow the steps mentioned earlier to create a Redux store in your `store/index.ts` file. In addition, you'll configure Redux Thunk middleware to handle asynchronous actions.

```tsx
import { combineReducers, configureStore, Middleware } from '@reduxjs/toolkit';
import thunkMiddleware from 'redux-thunk';
import authReducer from './slices/authSlice';

const loggerMiddleware: Middleware = (store) => (next) => (action) => {
  // eslint-disable-next-line no-console
  console.log('Action:', action);
  // eslint-disable-next-line no-console
  console.log('State before:', store.getState());

  const result = next(action);

  // eslint-disable-next-line no-console
  console.log('State after:', store.getState());
  return result;
};

const middleware = [loggerMiddleware, thunkMiddleware];

const rootReducer = combineReducers({
  auth: authReducer,
});

const store = configureStore({
  middleware,
  enhancers: [],
  devTools: true,
  reducer: rootReducer,
});

export default store;
```

#### 4/ **Wrap your App with Provider redux**:

```tsx
//pages/_app.tsx
import { Provider } from 'react-redux';
import store from '~store';

function MyApp({ Component, pageProps }) {
  return (
    <Provider store={store}>
      <Component {...pageProps} />
    </Provider>
  );
}

export default MyApp;
```
