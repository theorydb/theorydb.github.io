---
layout: post
title:  "[Jekyll Blog] GitHub & Jekyll 사용법"
subtitle:   "GitHub & Jekyll"
categories: envops
tags: envops blog github pages jekyll  
comments: true
---


## 개요
> 포스트 배포에 꼭 필요한 부분만 골라낸 `GitHub`와 `Jekyll`의 사용법에 대해서 배워봅시다.  
  
- 목차
	- [GitHub란?](#)
	- [Git Bash Shell](#)
	- [처음 1번만 쓰고 안쓰는 명령어](#)  
	- [매일 쓰는 명령어(글 쓸 때마다)](#)
	- [가끔 쓰는 명령어(오류발생 등)](#)
	- [더 알고 싶다면...](#)
  
  
## GitHub란?  
---
살다보면 아래와 같은 곤란한 경험에 부딪히게 된다.

* __[`GitHub`](https://github.com/). 꼭 써야하나요?__   
> __"무엇을 상상하든 그 파일은 최종파일이 아니다."__  
![그림1](https://theorydb.github.io/assets/img/fun/final-real.jpg)

분명히 최종파일을 만들었건만, 여러분이 생각하는 그 파일은 최종파일이 아니었던 그 경험.. 누구나 가지고 계실것이다. 문제는 나중에 보거나 다른 사람이 보면 진짜 최종이 뭔지 모른다. Git을 쓰시면 다 해결된다.  

* __기껏 회사에서 수정했건만.. 집에 있는 파일 또 수정해야 하나?__   
이것도 자주 겪는 경험이다. 별것 아닌것 같으면서도 은근 짜증난다. 그래서 사람들은 드랍박스, 구글드라이브나 심지어 USB에만 파일을 저장하는 사람도 있다. Git을 쓰시면 다 해결된다.   

* __열심히 고쳤는데 다른 사람이 고치면서 내가 수정한 것 다 날라갔다!__  
이건 정말 열받는다. 기억을 되살리며 했던짓을 반복하는 일이란 사람이라면 견딜 수 없다. 역시 Git을 쓰시면 다 해결된다.  

쉽게 정리하자면 Git은 __분산(`여러명이 수정할 수 있다.`)버전(`최최..종을 알아서 관리해준다.`)관리시스템__이며, GitHub는 Git으로 생산된 코드, 문서 등의 산출물이 저장되는 말 그대로 __Git저장소__라고 할 수 있겠다.  
이제 아래 [`GitHub 공식 홈페이지 가이드`](https://guides.github.com/activities/hello-world/)의 설명이 무슨 의미인지 이해되실 것이다.
> __What is GitHub?__  
> GitHub is a code hosting platform for version control and collaboration.  
> It lets you and others work together on projects from anywhere.  
  
다음은 위키백과의 설명이다.
> __깃(Git /ɡɪt/)__  
> 컴퓨터 파일의 변경사항을 추적하고 여러 명의 사용자들 간에 해당 파일들의 작업을 조율하기 위한 분산 버전 관리 시스템이다. 
> 소프트웨어 개발에서 소스 코드 관리에 주로 사용되지만[6] 어떠한 집합의 파일의 변경사항을 지속적으로 추적하기 위해 사용될 수 있다. 

그 외 많은 장점이 있지만 위 문제들 때문에 골치가 아프셨다면, 그리고 반드시 해결하고 싶으시다면 Git은 필수다!


## Git Bash Shell  
---
Git을 사용하는 방법은 크게 2가지가 있다.  

* __Git Bash vs Git GUI__  
Bash란 커맨드모드로 텍스트 기반의 명령어를 통해서 Git을 사용하는 방법을 말하고, GUI는 화면을 마우스로 제어하여 Git을 사용하는 방법이다. 이 블로그에서는 Bash방식을 사용함을 미리 알려드린다. 필자가 Bash를 고집하는 이유는 다음과 같다.  
>* 화면은 변해도 명령어는 변하지 않는다. (GUI 화면이 바뀌면 새로 배워야 한다.)
>* 키보드만 써도 된다.(속도가 빠르며, GUI는 마우스를 써야 하므로 더 신경쓸 것이 많다.)
>* 기술을 학습할 때는 명령어 방식이 본질에 집중하기 좋아 학습 능률이 향상된다. 
기존에 GUI 방식으로 활용하셨던 분, 너무 어려워서 GUI가 편하신 분은 어쩔 수 없겠지만 이 블로그를 통해 처음으로 익히시는 분이라면 Bash방식을 활용하셨으면 한다.   


* __그럼 이거 프로그래머만 쓸 수 있는거 아냐?__  
아니다. 물론 프로그램 코드 관리가 주 목적이지만 `일반문서도` 얼마든지 관리 및 공유가 가능하다. 예를 들자면 [`개발 블로그 모음`](https://github.com/theorydb/awesome-devblog)을 클릭하셔서 구경하시기 바란다. 이름은 개발자 블로그지만 코드 하나 없는 순수 문서이다.  
  

## 처음 1번만 쓰고 안쓰는 명령어
---
	```yml
	tipue_search:
		include:
			pages: false
			collections: []
		exclude:
			files: [search.html, index.html, tags.html]
			categories: []
			tags: []
	```


## 더 알고 싶다면...  
---
여기까지 블로그를 운영하기 위한 최소한의 Git 사용법에 대해 알아보았다. Git 사용법에 대해 자세히 열거하자면 자체 컨텐츠만으로 블로그 하나는 꽉 채울 수 있는 엄청난 분량이 나오게 되니 이 블로그의 취지에 맞지않아 생략한다.

대신 더 많은 기능을 배우고 싶다면 아래 유용한 링크들을 클릭하시길 바란다.   
* "GitHub 공식 가이드" : [`바로가기`](https://guides.github.com/activities/hello-world/)
* "누구나 쉽게 이해할 수 있는 Git 입문" : [`바로가기`](https://backlog.com/git-tutorial/kr/)  
* "버전관리를 들어본적 없는 사람들을 위한 DVCS - Git" : [`바로가기`](https://www.slideshare.net/ibare/dvcs-git)  
* "svn 능력자를 위한 git 개념 가이드" : [`바로가기`](https://www.slideshare.net/einsub/svn-git-17386752)  



지금까지 Git에 대해 알아보았다. 블로그, 문서, 프로그래밍 언어 가릴것 없이 중복과 버전관리로 인해 받는 스트레스가 사라지시길 바란다.  
