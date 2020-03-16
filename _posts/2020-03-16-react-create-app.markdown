---
layout: post
title:  "React Project, create-react-app으로 시작하기"
categories: React
tags: React create-react-app
---

<img src="{{ "/assets/200316/1.png" | relative_url }}">   

이번 포스팅은 첫번째 React 프로젝트, create-react-app으로 시작해보기 입니다.

create-react-app 명령어는 최신 모듈들이 적용되어 생성된다는 사실.

React Project의 Generator 라고 칭해도 될만큼 빠른 속도와 개발환경을 구성해줍니다.

그럼 시작해볼까요.

터미널을 열고, 프로젝트가 생성될 곳으로 이동해준 뒤

create-react-app 모듈을 Global 로 설치 해줍시다.

```
npm i -g create-react-app
```

<hr>

설치가 완료 된 후, 리액트 앱을 생성합니다.

create-react-app [프로젝트명, 대문자가 들어가지 않도록합니다.]

```
create-react-app first-react-project

cd first-react-project
```

<hr>

생성된 프로젝트 경로로 들어가 보시게 되면
아래와 같은 구조로 React 프로젝트가 생성되어 있습니다.

```
first-react-project
  README.md
  node_modules/     -> 모듈들이 담겨 있는 장소
  package.json
  public/
    favicon.ico
    index.html
    manifest.json
  src/
    App.css
    App.js
    App.test.js
    index.css
    index.js
    logo.svg
    registerServiceWorker.js
```

자, 이제 프로젝트를 실행해볼까요

```
npm start
```

위 명령어를 실행하게 되면,

localhost:3000 주소로 React 어플리케이션이 구동되며

리액트 로고가 빙글빙글 돌아가는 모습과 함께 Index 페이지가 열리게 됩니다.

<hr>

create-react-app에 포함된 기본적인 모듈들에 대해서는

다음 포스팅을 통해 이야기 해보겠습니다.