---
layout: post
title:  "[seoul.js] - ECMAScript2017"
subtitle:   "seoul.js - 밋업"
categories: review
tags: event
comments: true
---

## ECMAScript 2017
---
ECMA - 비영리 표준화 기구

ECMAScript - Javascript는 상표이기도함  분쟁을 피하기위해 에크마스크립트라고한다.

TC39(테크니컬 커미티) 에크마스크립트를 담당하는 ECMA 기구

### Object.values & Object.entries

Object.keys의 친구들

밸류즈 - 오브젝트의 벨류를 리턴해줌. 키가 기준임.

엔트리즈 -

### String padding

padStart는 앞쪽에 padEnd는 뒤쪽에 스페이스를 추가함.

### Object.getOwnPropertyDescriptors

Object.getOwnPropertyDescriptor( s가 빠진거 )는 이미 있던 기능.

해당오프젝트에 해당하는 모든 프로퍼티값을 객체로 출력해줌.

### Trailing commas in function parameter lists and calls

마지막요소에 ,를 적어도 에러가나지않음
```
a,
b,
c,
```
이런식

### Async functions

프로미스가 등장했었음 ECMAScript 2015부터

Async는 프로미스와 제너레이터를 합쳤다고보면된다.

프로미스에 기반. 프로미스를 좀 더 동기적으로 사용할 수 있게 해줌.

에러핸들링이 간편해짐. 함수 캐치않쓰고 트라이 캐치만드로도 잡을 수 있음.

프로미스는 댄으로 넘겨줘야하는 경우도 어싱크를 사용하면 다음라인에 바로 사용할 수 있다.

### Shared memory and atomics

워커끼리 메세지를 주고받는 방법.

1. 씨피유가 비트전송

2. 포스트메세지로 메모리를 클론
3. 메모리1을 메모리2로 옮겨버림(씨피유1이 메모리1에 접근하지 못하니 위험)

ArrayBuffer - 이미 있었음.
SAB - 공유가능.

SAB는 워커들이 서로다른속도로 작업을 하는 경우가 있기때문에 Atomics를 사용함.
