---
layout: post
title:  "[JavaScript] Array에서 특정 객체 찾기"
subtitle:   "[JavaScript] Array에서 특정 객체 찾기"
categories: devlog
tags: javascript array
---

자바스크립트 배열에서 오브젝트를 찾아보자.

나같은 경우는 보통 배열의 특정 값을 지우려고 할 때 인덱스를 찾는 경우가 많다.

### 배열에서 특정 값 지우기

```js

let arr = ['a','b','c'];

arr.splice(arr.indexOf('b'),1);

arr === ['a','c']

```

근데 배열이 오브젝트 배열이라면 어떻게 찾아야 할지 한번 더 고민해 보아야한다.

```js
if (충분한 고민 === true){
    아래로();
}else{
    위로();
}
```

이럴땐 하나씩 꺼내서 비교하는 방법이 있다.

### map을 이용한 오브젝트 배열 탐색

```js

arr.map(x => x.value).indexOf('something');

````

워 생각보다 간단하다. 함수개념을 알고 있다면 금방 응용할 수 있다.

한가지 더. 충분히 큰 배열에서 탐색할 때 위의 방법보다 더 빠르다고 알려진 방법이 있는데, 한번 보자.

### findIndex

```js

arr.findIndex(x => x.value === 'something');

````

배열에서 뭐 하나 찾는데도 방법이 이렇게 많다.
