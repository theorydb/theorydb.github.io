---
layout: post
title: "[c++]Gamepack:section01_(1.2)과제"
subtitle: "Making Solar System and Drawing Face"
categories: programming
tags: cpp opengl gamedev assignment
comments: true
header-img: img/programming/cpp/0000-00-00-programming-cpp-game-lecture-cover.JPG
---

> `홍정모`교수님의 [ `게임 만들기 연습 문제 패키지`](https://www.inflearn.com/course/c-2#)를 수강하고 작성한 문서이다.
>
> 교수님이 내주신 `과제`에 대한 `해결`을 담고 있다.
>
> 탱크예제 총알 문제 해결하기[✔], 걷고있는 사람의 형태 및 행동 완성시키기[✔]

---

## jm::TankExample().run();

<img src="https://yeram522.github.io/assets/img/programming/cpp/2021-08-23-programming-cpp-making-tank-ex-and-walking-person-1.gif" width="300" height="300"/>

🤔 총알은 잘 날아가긴 하는데,,,, 발사된 총알이 화면을 벗어나기 전에 한번더 space키를 눌러서 총알을 발사시키면, 기존에 날아가고 있던 총알은 사라지고 새로 발사되게 된다. _이러한 과정에서 메모리 누수가 일어날 수 있다._  이를 해결해보자!

- [ ] TODO: allow multiple bullets
- [ ] TODO: delete bullets when they go out of the screen



.
