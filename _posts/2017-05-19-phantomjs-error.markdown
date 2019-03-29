---
layout: post
title:  "Phantom immediately exited with: 127"
subtitle:   "phantomjs를 쓸 일이 생겼다."
categories:  devlog
tags: nodejs web

---

phantomjs를 쓸 일이 생겼다.

한창 열심히 만들고있는 요약서비스가 있다. 이 서비스에서 동적으로 생성되는 페이지(브런치의 글 리스트라던지, 네이버 블로그라던지)의 요소를 읽어올 수가 없는 문제가 있다는걸 깨달았다.

현재는 직접 DOM의 엘리먼트에 접근하는 방식을 사용하는데, 동적인 페이지에서 글을 가져오기 위해서 phantomjs를 사용해야 했다.

## Phantom immediately exited with: 127
---

자세한 이야기는 나중에 개발일지에 하기로 하고, 우선 환경은 AWS EC2에 우분투를 사용하고있다.

phantomjs를 설치하고 사용하는데 horseman라이브러리를 사용하였고, 실행해보니 Phantom immediately exited with: 127 이런 에러가 나타난다.

디펜던시가 있기 때문인데 아래와 같은 명령어로 해결 가능하다.

> $ sudo apt install -y libfontconfig

> $ sudo apt install -y libfreetype6

의존 라이브러리들을 설치하고나면 잘 실행된다.
