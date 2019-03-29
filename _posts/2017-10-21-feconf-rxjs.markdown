---
layout: post
title:  "[FECONF 2017] RxJS 써야겠어요? 안써야겠어요?"
subtitle:   "Deview"
categories: review
tags: event
comments: true
---

RxJS

비동기 처리. RxJS말고 다른거 많지않나 - callback, promise, generator, async/await 심지어 표준

### 왜 RxJS?

자바 9 - 리액티브 위드 스프링 5

RxJs가 담당하는 영역 - 비동기 처리, 데이터 전파, 데이터 처리

RxJS는 일관된 방식으로 / 안전하게 / 데이터 흐름을 / 처리하는 라이브러리이다.

모든 어플리케이션은 궁극적으로 상태머신이다.

입력값은 어떤 것이 있는가? 

### 개발자의 고민

동기, 비동기

함수호출, 이벤트, 콜백, 프라미스

등등을 따로 처리해줘야함.

시간축을 관점으로 동기와 비동기는 같다.

RxJS로 하나의 방식으로 처리하자. 인터페이스의 단일화. - 모두 옵저버블로 처리하자.

모든 어플리케이션은 궁극적으로 상태머신의 집합이다.

Reactive Programming - 데이터가 자동으로 전파.

이미 알고있는 것 - 옵저버 패턴

RxJS - 개선된 옵저버 패턴

옵저버블 - 옵저버
섭스크라이브 - next, error, complete

### RxJS는(함수형프로그래밍) 고차함수를 제공한다.

고차함수 (HOC) 

사이드 이펙트

함수형프로그래밍은 순수함수를 지향한다. 같은입력 : 같은 출력 / 사이드 이팩트 지양



