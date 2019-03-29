---
layout: post
title:  "[node]passport 사용자 인증 원리"
subtitle:   "passport 사용자 인증 원리"
categories: devlog
tags: nodejs
comments: true
---

Passport는 node에서 사용하는 범용 인증모듈이다. 다양한 인증 프로토콜을 지원하며, 소셜로그인도 손쉽게 구현할 수 있다. 실제로 Passport에서 사용자 인증을 구현하는 법을 살펴보자.

## 인증 방법

---

Passport는 다양한 인증에 대해 미리 구현해 놓았는데, 그걸 Strategy라고한다. Facebook 소셜 인증을 위해서는 facebook strategy를, Google 소셜 인증을 위해서는 google strategy를 사용하면 되는 식이다.

또한 Passport로 자체 인증처리를 하는 방법으로 LocalStrategy를 사용하는데, 일반적으로 자체 서비스의 인증을 구현할 때 사용한다.
