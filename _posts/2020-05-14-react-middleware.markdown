---
layout: post
title:  "[React] Redux Middleware 리덕스 미들웨어 이해하기"
categories: React
tags: React Redux Middleware 비동기 액션
---

<h3>Redux Middleware</h3>

네트워크 요청의 상태관리와 전달받은 데이터 상태관리를 더욱 효율적이고 쉽게 할 수 있도록 도와 주는 것

<hr/>

<h3>Redux Middleware 역할</h3>

Action이 Dispatch 되어서 이를 처리하기 전에, 사전에 지정된 작업들을 설정 함

미들웨어는 "Action과 Reducer 사이의 중간 역할자" 라고 이해 할 수 있음


Reducer가 Action을 처리하기 전, Middleware가 할 수 있는 작업들

<hr />

```
예) 단순히 전달받은 Action을 Console에 기록할 수 있음

예) 전달받은 Action에 기반하여 Action을 취소하거나,

    다른 종류의 Action을 추가적으로 Dispatch 할 수 있음

예) 액션의 정보를 가로채서 가공하여 리듀서로 전달 시켜 줄수도 있음
```


Middleware는 특히 비동기 작업을 할 때 유용함

Middleware를 직접 만들 수 있지만,

오픈소스 커뮤니티에서는 전문적으로 잘 만들어진 Middleware들이 많음


<hr />

<h3>비동기 작업을 처리하기 위한 미들웨어 알아보기</h3>

대표적으로 많이 사용 미들웨어는,

- redux-thunk

- redux-promise-middleware

- redux-pender




<h3>Redux-thunk</h3>

Redux를 사용하는 Application에서 가장 기본적으로 사용됨

Redux 공식 문서에서도 해당 라이브러리를 사용하여 비동기 작업을 다루고 있음



<h3>'thunk'는 무엇일까?</h3>

특정 작업을 나중에 하도록 미루기 위해서 함수(Function) 형태로 감싸진 것을 말함

```
const hello = 'Hello!!';
```

이 코드는 hello 변수에 'Hello!!' 문자열이 바로 담기게 됨

```
const hello = () => return 'Hello!!';
```

위와 같이 바꾸면, hello()를 호출해야만 문자열이 반환 됨


Redux-thunk는

객체 대신 "함수를 생성하는 액션 생성 함수" 를 작성 할 수 있게 해줌

특정 액션이 몇초뒤에 실행 되도록, 현재상태에 따라 액션을 무시 하도록 하는 등의

행위는 일반 액션 생성자로 할 수 없음


하지만 redux-thunk는 가능하게 해줌

```
    const INCREMENT_COUNTER = 'INCREMENT_COUNTER';

    function increment() {
        return {
            type: INCREMENT_
        };
    }

    function incrementAsync() {
        return dispatch => {
            // 'dispatch'를 파라미터로 가지는 함수를 리턴 함
            setTimeout(() => {
                dispatch(increment());
            }, 1000);
        };
    }
```

이렇게 만들어 놓은 뒤,

나중에 store.dispatch(incrementAsync()); 하게 되면

INCREMENT_COUNTER 액션이 1초뒤에 디스패치 됨



추가적으로, 리턴 함수에서 dispatch, getState 를 파라미터로 받게 한다면

현재 스토어의 상태에도 접근 할 수가 있음

현재의 스토어 상태의 값에 따라 액션이 dispatch 될 지 무시 될지도 정해 줄 수 있게 됨



<h3>redux-thunk 설정방법</h3>

store 생성이 이루어 지는 곳에서 (createStore)

applyMiddleware() 함수에 인자로 Redux-thunk를 넣어 주면 됨


예)

```
    import { createStore, applyMiddleware } from 'redux';
    import { modules } from './modules';
    import reduxThunk from 'redux-thunk';

    const store = createStore(modules, applyMiddleware(reduxThunk))

    export default store;
```
