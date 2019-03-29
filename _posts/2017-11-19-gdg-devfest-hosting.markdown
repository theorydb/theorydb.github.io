---
layout: post
title:  "[GDG DEVFEST] github과 cloud flare로 무료 웹 호스팅하기"
subtitle:   "DEVFEST"
categories: review
tags: event
comments: true
---

JAM Stack

Javascript

API

Markup

---

staticgen에서 스태틱 사이트 제너레이터를 확인해보세요

---

성능이 좋다 - CDN으로 전세계 엣지

보안이 좋다 - 비즈니스 로직 처리는 API가 함. 

---

베스트 프렉티스

모든 프로젝트는 CDN에 업로드

배포시 CDN 캐시는 즉시 폐기

배포는 모든 변경 파일이 업로드 완료 시에 적용

git으로 버전관리를 하고 단일 표준 명령어(npm install)로 어플리케이션 빌드

babel, postCSS, webpack과 같은 모던 빌드 도구 활용하여 최신 JS문법 사용

빌드 자동화

---

배포

github pages + cloudFlare

깃헙 페이지스

사용자, 그룹, 프로젝트의 정적 웹 사이트 호스팅 무료 제공

github.io도메인을 이용하여 HTTPS/SSL 지원

지킬 기반의 기본 템플릿 지원

사용제한 - 1기가 제한 / 월 100기가 대역폭 / 시간당 10개 빌드

클라우드 플레어

무료로 CDN, DNS, SSL 인증서... 역방향 프록시 역할 수행

사용제한 - 개인 도메인

---

Netlify

깃헙 페이지스와 클라우드플레어기능을 모두 가지고 있어서 쉬움. 지속배포도 쉽게 된다.

---

S3 + CloudFront

유료

---

서비스의 목적에 맞는 웹 기술 스택을 선택하자.

목적과 맞다면 JAMstack을 고려하자.

세상 좋은 공짜 서비스 참 많다.

