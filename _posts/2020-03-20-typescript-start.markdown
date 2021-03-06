---
layout: post
title:  "TypeScript 환경 구성 및 기초 예제"
categories: Typescript
tags: Typescript 타입스크립트
---


이번 포스팅은 타입스크립트에 대해 알아보고 기초 문법들을 살펴보겠습니다.

<h3>타입스크립트를 왜 쓸까?</h3>

에러를 방지하기 위해 많은 단위 테스트들이 필요하지만,

타입스크립트를 통해 이런 오류들에 대해 선언과 동시에 예방? 할 수 있고,

타입스크립트 컴파일러에 의해 코드 오타, 타입에러 등 컴파일 타임에 모든 유형 오류를 알려주기 때문에

코딩과 동시에 에러를 잡을 수 있어 코드품질 향상을 도와줄 수 있다.

<hr>

<h3>타입스크립트 환경 구성하기</h3>

타입스크립트 설치

```
  $ yarn global add typescript 또는
  $ npm install -g typescript
```

그 다음, 아래 명령어를 입력하면   
타입스크립트 설정파일인 (tsconfig.json) 파일이 생성됩니다.

```
  $ tsc --init
```

그럼 설정파일을 살펴 볼까요?   
/tsconfig.json

```
{
  "compilerOptions": {
    "target": "es5",
    "module": "commonjs",
    "strict": true,
    "esModuleInterop": true
  }
}
```

<ul>
  <li>target : 컴파일된 코드가 실행될 환경을 설정</li>
  <li>module : 컴파일된 코드가 사용할 모듈 시스템을 설정</li>
  <li>strict : 모든 타입을 체크할 것인지 예(true), 아니오(false)</li>
  <li>esModuleInterop : commonjs 모듈 형태로 이루어진 파일을 ES2015 모듈 형태로 불러올 수 있도록 할것인지 예(true), 아니오(false)</li>
</ul>

<hr>

타입스크립트 설정파일에서 한가지를 추가해 줍니다.   
/tsconfig.json

```
{
  "compilerOptions": {
    "target": "es5",
    "module": "commonjs",
    "strict": true,
    "esModuleInterop": true,
    "outDir" : "./dist"
  }
}
```

<h3>타입스크립트 파일 만들어 보기</h3>

프로젝트 경로에 src 폴더를 만들고, 그 안에 test.ts 파일을 만들어 줍시다.

src/test.ts
```
  const hello: string = 'Hello Typescript';
  console.log(hello);
```

위 코드에서 변수가 선언된 이후에 (: string) 이것이 바로   
해당 변수에 타입을 선언(명시)하는 것입니다.

만약 선언(명시) 타입에 일치하는 않는 타입의 값이 해당 변수로 들어올 때 에러가 발생합니다.

<hr>

```
  let hello: string = 'Hello Typescript';
  console.log(hello);
  hello = 1;
```

위와 같이 코드를 변경해보면 에러가 발생하는 것을 확인 하실 수 있습니다.

다시 코드를 원복 한 뒤

터미널에 아래 명령어를 입력해 줍니다.

```
  $ tsc
```

입력하고 나면 아까 설정해두었던 /dist 폴더 안에

ES2015로 변환된 test.js가 생성 되어있을 겁니다.

test.js 파일을 열어보게 되면

변수 선언시 명시했던 타입들은 컴파일 과정에서 모두 사라지게 됩니다.

<hr>

<h3>타입스크립트 예시 모음</h3>   

```
  // 내 나이
  let age: number = 0;
  console.log(age);
  age = "서른하나";   // 에러

  // 내 이름
  let name: string = "박성화";
  console.log(name);
  name = parksunghwa; // 에러

  // 생일 지남?
  let birth: boolean = false;
  console.log(birth);
  birth = "true"; // 에러

  // 내가 좋아하는 것들
  let likes: '음악' | '테크' | '전자기기' | '게임';
  likes = '등산'   // 등산 극혐 에러
  // 위에 좋아하는것에 포함되지 않아 에러 발생
```