---
layout: post
title:  "[Sentry]ReactNative에 Sentry 달기"
subtitle:   "에러 리포트 툴 Sentry"
categories: devlog
tags: tool nodejs react-native

---

## Sentry

Sentry는 다양한 언어, 프레임워크에서 에러를 리포트해주는 툴이다. 에러를 모두 웹, 웹훅으로 쏠 수 있어 슬랙으로도 볼 수 있고, 모든 에러를 종합해서 웹에서 확인할 수 있다. 로깅을 꽤 자세히 해주기때문에 아주 쓸만하다. 센트리 외에도 다양한 툴이 있는데, 익숙하기도 하고 가장 활발하고 가성비 좋은거 같아서 센트리를 쓰기로했다.

## 문제

Sentry를 ReactNative에 연동하는 과정은 아주 쉬운데 라이브러리를 설치하고, 링크를 걸면 된다. 근데 여기서 문제가 발생했다. 모든 상황에서 나타나는지는 확인하지 않았지만 `fatal error: 'RNSentry.h' file not found` 이러한 에러가 발생하였다.

RN 버전이 `0.4x` 이상일 경우 발생하는 현상으로, pod가 설치되지 않은 것을 확인했다. 조치는 아래와 같이 처리했다.

```
cd ios
pod repo update
pod install
```

