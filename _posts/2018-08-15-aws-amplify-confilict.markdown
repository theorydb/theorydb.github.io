---
layout: post
title:  "[AWS] aws-sdk와 aws-amplify 충돌"
subtitle:   "AWS"
categories: devlog
tags: AWS
comments: true
---

정말 오랜만에 글을 쓰는데 글을 쓸 힘이 없다. 너무 열심히 삽질을 했기 때문에.

## 결론

결론만 이야기하면 `aws-sdk`와 `aws-amplify`를 함께 설치하면 충돌이 난다. 나같은 경우는 크레덴셜 충돌이 나서 한참을 헤메었다.

심지어 한번 구현해보았던 이슈라 더 혼란이었는데... `aws-sdk`를 제겨하면서 해결했다.

개발같다.
