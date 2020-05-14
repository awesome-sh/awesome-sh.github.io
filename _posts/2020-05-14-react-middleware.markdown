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



예) 단순히 전달받은 Action을 Console에 기록할 수 있음

예) 전달받은 Action에 기반하여 Action을 취소하거나, 다른 종류의 Action을 추가적으로 Dispatch 할 수 있음

에) 액션의 정보를 가로채서 가공하여 리듀서로 전달 시켜 줄수도 있음



Middleware는 특히 비동기 작업을 할 때 유용함

Middleware를 직접 만들 수 있지만,

오픈소스 커뮤니티에서는 전문적으로 잘 만들어진 Middleware들이 많음