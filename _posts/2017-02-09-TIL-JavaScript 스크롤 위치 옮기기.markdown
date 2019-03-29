---
layout: post
title:  "JavaScript 스크롤 위치 옮기기"
subtitle:   "세로로 길게 늘어지는 모바일 디바이스 브라우저의 특성상"
date:   2017-02-09 20:21:33 +0900
categories: devlog
tag: devlog javascript dev
---

세로로 길게 늘어지는 모바일 디바이스 브라우저의 특성상 위치를 위치를 옮겨야 할 경우가 가끔 있다.

그 때 쓰는 메소드들을 찾았다.

> window.scrollTo(x,y);
> window.scrollBy(x,y);

## scrollTo
scrollTo는 Top부터 절대치 만큼의 x,y로 옮겨준다.

## scrollBy
scrollBy는 현재위치로부터 x,y만큼 옮겨준다.

나는 scrollBy를 써서 이번 이슈를 해결했다.
