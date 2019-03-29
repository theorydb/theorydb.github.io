---
layout: post
title:  "React Component - Stateless 또는 Stateful"
subtitle:   "React 컴포넌트를 만들다 고민이 생겼다."
categories:  devlog
tags: react component
---

React 컴포넌트를 만들다 고민이 생겼다.

> Stateless 컴포넌트를 만들까? Stateful 컴포넌트를 만들까?

결론부터 이야기하면 가능한 한 stateless 컴포넌트를 만들자.

## Stateless 또는 Stateful

---

React는 stateless functional components라는 컴포넌트를 정의하는 간단한 방법을 가지고 있다. 이 컴포넌트들은 순수 자바스크립트 함수를 사용한다.

stateless 컴포넌트를 사용하면서 몇가지 이점을 얻을 수 있다.

### 클래스가 필요하지 않다

stateless 컴포넌트는 순수함수로 이루어져있다. 덕분에 클래스를 사용하면서 나타날 수 있는 부작용들을 제거 할 수 있게 된다.


### this가 없다

stateless 컴포넌트는 그냥 함수다. 그래서 변덕이 심한 자바스크립트의 this 키워드를 피해갈 수 있다. 그럼으로써 컴포넌트는 이해하기 쉬워진다. 예제로 한번 비교해보자.

```js

<button onClick={this.something.bind(this)}>Do Something</button>

<button onClick={something}>Do Something</button>

```

stateless 컴포넌트는 bind가 필요가 없다. 클래스를 버림으로써 this를 bind할 필요가 없어진것이다. this가 얼마나 많은 개발자들을 괴롭혔는지를 생각하면 이건 상당한 이점이다.



### 어길 수 없다

stateless 컴포넌트는 presentational 컴포넌트로 사용하기 좋다. Presentational 컴포넌트는 행동보다는 UI에 집중하기 때문에, state를 사용하는걸 피하여야한다. 그러기위해 state는 보통 container라고 불리는 상위컴포넌트에서 관리되거나 Flux/Redux등으로 관리되어야한다. stateless 컴포넌트는 state와 lifecycle 을 지원하지 않는다. 우리는 그 덕분에 게으름을 방지할 수 있다.

바쁠 때 우리는 presentational 컴포넌트에 자꾸 스테이트를 추가하고 싶은 유혹에 빠진다. 분명 state를 추가하면 금방끝나! 하지만 stateless 컴포넌트를 사용하면 state를 추가할 수 없다. 지원을 안하니까. 우리 게으름도 허용되지 않는다. 우리는 게으름을 버리고, 우리의 stateless 컴포넌트가 프로그램적으로 순수한 컴포넌트로 유지된다.


### 뻥튀기된 컴포넌트와 나쁜 자료구조가 쉽게 발견된다.

인자가 많은 함수가 냄새나는 코드라는건 다들 알고있다. stateless 컴포넌트를 사용하면 인자 리스트에 컴포넌트의 의존성을 명확히 전달한다. 그러므로 주의가 필요한 구성요소를 쉽게 찾아 낼 수 있다.

문제가 생길 경우 컴포넌트를 분해하거나 전달하고있는 자료구조를 다시 생각해볼 수 있다. 물론 많은 분량의 props를 전달할 때는 가끔 객체로 보낼 수 있다. 하지만 props가 논리적으로 하나의 객체로 정의될만큼의 관련이 없다면 컴포넌트를 여러개로 리팩토링할 시기가 된 것이다.


### 이해하기 쉽다

stateless 컴포넌트를 보면 '이거 참 단순하고 보기 쉽구나' 라고 생각할 수 있다. 심지어 많은 markup과 함수들이 포함되어있더라도 개념적으로 단순하다. 순수함수이기때문이다.



### 테스트하기 쉽다

순수함수이기 때문에, assertion이 매우 간단하다. 이런 props를 줄게 저런 markup을 줘.라고 명시할 수 있다. stateless 컴포넌트와 함께라면 각가의 컴포넌트를 쉽게 테스트할 수 있다. 목업이나, 조작, 특별한 라이브러리등의 트릭을 사용하지 않아도


### 성능

stateless 컴포넌트는 곧 성능의 향상을 가져온다. 생명주기가 없기때문에 불필요한 메모리할당과 체킹을 하지 않아도 된다.

## 마치며
---

수많은 이유들로 우리는 가능한 한 stateless 컴포넌트를 사용해야한다는 결론에 도달했다. 실제로 [stateless 컴포넌트로 45%의 성능향상을 얻었다](https://medium.com/missive-app/45-faster-react-functional-components-now-3509a668e69f)는 사례를 적은 글도 있다.

우리는 성능을 개선할 수 있는 수많은 방법중 하나를 오늘 또 배웠다.
