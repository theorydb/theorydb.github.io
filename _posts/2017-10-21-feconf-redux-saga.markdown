---
layout: post
title:  "[FECONF 2017] redux thunk에서 redux saga로 이사하기"
subtitle:   "Deview"
categories: review
tags: event
comments: true
---

리덕스

클라이언트쪽 스테이트를 관리하기 위한 거대한 이벤트 루프

액션은 평범한 자바스크립트 객체

리듀서는 순수 함수

문제는 비동기 처리 - 리퀘스트, 석세스, 페일

Redux-Thunk 와 Redux-Promise

Thunk는 나쁘다 - 테스트, 디버깅이 어렵다. / 디스패치를 직접 실행하면서 스파게티코드 / 갑자기 어디서 겟스테이트

Redux-Saga

데이터 오케스트레이션 

액션은 평범한 자바스크립트 객체

비동기코드를 동기 코드처럼 쓸 수 있다.

테스트하기 좋다.

복잡한 데이터 처리를 도와줌

사가는 액션이 일어나는 순간 테이크로 받아들이고 풋해줌.

ES6 generator - ES6에 추가된 코루틴 함수 function으로 선언 yield 키워드를 만나면 스스로멈추고 컨트롤을 콜리에게 넘김

## 절차

사가를 미들웨어에 더해야함.

썽크 액션을 다시 코딩

뷰에 포함된 then코드를 사가로옮겨야하고

connect로 한 SSR도 Saga로 옮겨야하고



