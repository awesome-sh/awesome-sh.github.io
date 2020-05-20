---
layout: post
title:  "[React] React Context 이해하기"
categories: React
tags: React Context
---

<h3>React Context ?</h3>

    - 'Context'는 모든 레벨에 props를 전달하지 않고,
        컴포넌트 트리를 통해 data를 전달하는 방법을 제공 함
    

    - 리액트에서는 data를 props를 이용해 단방향 (상위 -> 하위) 으로 전달 함


<h3>그럼, Context는 언제 사용할까?</h3>

    - 'Global'(전역)으로 처리해야하는 Data를 공유하기 위해 설계 됨


    - 'Context'를 사용하면, 중간 Element들을 통해 props가 전달 되는 것을 막을 수 있음


    - 많은 Component들에서 같은 데이터에 접근해야 하는 경우에 사용 함




 
[참고] Dongmin Jang - https://medium.com/@Dongmin_Jang