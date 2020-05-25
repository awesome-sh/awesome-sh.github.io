---
layout: post
title:  "[PostgreSQL] 확장프로그램 PostGIS 적용하기"
categories: Database
tags: PostgreSQL PostGIS Extention WebGIS pgAdmin
---

이 포스팅은 PostgreSQL과 PostGIS가 설치되어 있다는 가정하에 진행됩니다.

PostgreSQL과 PostGIS를 먼저 설치해해 주세요.

PostgreSQL 다운로드
<https://www.postgresql.org/download/>

<hr/>

모두 설치하셨다면 pgAdmin을 실행해줍니다.   

pgAdmin은 오라클의 SQL Developer와 같은 PostgreSQL 전용 GUI 툴입니다.
    
PostgreSQL을 선택 -> Object -> Create -> Database 선택

<img src="{{ "/img/in-post/191031/1.png" | relative_url }}">   

<hr/>

Database 이름을 지정해주고 Save 클릭

<img src="{{ "/img/in-post/191031/2.png" | relative_url }}">

이렇게 새로운 데이터베이스를 생성해보았습니다.

이제부터 생성된 데이터베이스에 PostGIS 확장 프로그램을 적용시켜 보겠습니다.

<hr/>

아래 그림처럼 현재 데이터베이스에 Functions 항목에는 아무것도 존재하지 않습니다.

<img src="{{ "/img/in-post/191031/3.png" | relative_url }}">

자 그럼, 적용해봅시다

생성된 데이터베이스를 선택한 후 -> 상단에 Tools -> Query Tool 선택해줍니다.

<img src="{{ "/img/in-post/191031/4.png" | relative_url }}">

그러면 아래와 같은 Query Editor 창이 열리게 됩니다.

이제 쿼리를 날려줍시다

```
CREATE EXTENSION postgis;
```

<img src="{{ "/img/in-post/191031/5.png" | relative_url }}">

입력하신 뒤, 에디터 상단에 번개모양 아이콘을 클릭하시거나 [F5]을 누르시면 쿼리가 실행됩니다.

<img src="{{ "/img/in-post/191031/6.png" | relative_url }}">

<hr/>

성공적으로 새로 생성한 데이터베이스에 PostGIS Extension을 추가했습니다.

자 이제 pgAdmin을 새로고침 한 뒤 다시

Server -> Databases -> 생성한 데이터베이스 -> Schemas -> Public -> Functions로 가봅시다.

<img src="{{ "/img/in-post/191031/7.png" | relative_url }}">

비어있던 Functions에 공간정보를 계산할 수 있는 함수들이 한 바가지 들어가 있는 걸 볼 수 있습니다.

<hr/>

다음 포스팅에서는 공간 함수를 어떻게 이용하는지에 대해 알아보겠습니다.

감사합니다.