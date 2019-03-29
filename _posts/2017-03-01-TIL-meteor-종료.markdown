---
layout: post
title:  "METEOR 프로세스 터미널 명령으로 종료시키기"
subtitle:   "개발할 때 터미널 명령어는 익숙하면 편하다."
categories: devlog
tags: linux devlog
---

개발할 때 터미널 명령어는 익숙하면 편하다.

> kill -9 \`ps ax \| grep node \| grep meteor \| awk '{print $1}'\`

이렇게 호출하면 meteor 프로세스를 전부 kill할 수 있다.
