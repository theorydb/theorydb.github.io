---
layout: post
title:  "Meteor에서 publish 제대로 하기"
subtitle:   "Meteor에서 publish할 때 조심해야 하는 경우가 있다."
categories: devlog
tags: meteor devlog

---

Meteor에서 publish할 때 조심해야 하는 경우가 있다.

아주 간단한 예를 들어보자. 보통의 경우 user정보는 항시 받기 위해 퍼블리시를 할 것이다. 이 때 users 콜렉션을 전부 publish한다면 문제가 생긴다.

필요한 정보는 아이디, 프로필 사진정도 되는 정보인데, 비밀번호(물론 암호화 되어있겠지만 유출되는건 좋지않다.)같은건 내보낼 필요가 없다.

이 이슈는 보안에 관련한 이슈이기도 하지만, 속도 개선에도 도움이 된다.

가능하면 publish할 때는 최소한의 정보만 보낼 수 있도록 설계하는 습관을 들이자. 필요한 정보가 무엇인지 정의해 놓으면 편하다.

## 예시

---

가장 간단한 publish방법을 떠올리자면 아래와 같이 할 수있다.

### 개선하기 전 publish

```js
Meteor.publish('userData', function () {
    return Meteor.users.find();
})
```

이렇게 하면 유저의 패스워드나 개인신상 정보가 함께 달려가기 때문에 위험하다.

필요한 정보만 쓰기 위한 방법은 아래와 같다.

### 개선한 publish

```js
Meteor.publish('userData', function () {
    return Meteor.users.find({},{ fields : { profile: 1}});
})
```

이렇게하면 1로 체크 된 profile에 해당하는 정보를 줄 수있다.

간단한 설정만으로 보안과 속도 개선까지 되었다.
