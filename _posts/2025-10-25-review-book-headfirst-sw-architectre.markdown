---  
layout: post  
title: "[리뷰] 헤드 퍼스트 소프트웨어 아키텍처"  
subtitle: "사고를 위한 학습 가이드"  
categories: review  
tags: review book sw 아키텍처 특성 트레이드오프 구성요소 ADR 결합도 모놀리식 분산 레이어드 모듈러 모놀리스 MSA 이벤트 다이어그램     
comments: true  
header-img: img/review/review-book-headfirst-sw-architectre-1.png
---  
  
> `한빛미디어` 출판사의 `"헤드 퍼스트 소프트웨어 아키텍처(라주 간디, 마크 리처드, 닐 포드 저/유동환, 최영수 역)"`를 읽고 작성한 리뷰입니다.  

![표지](https://theorydb.github.io/assets/img/review/review-book-headfirst-sw-architectre-1.png)  

---

> 모듈러, 마이크로서비스, 이벤트 기반 등 굵직한 아키텍처 개념들을 컴팩트한 분량으로 직관적으로 쉽게 전달하는 명작.   

시간이 지날수록 헤드 퍼스트 시리즈 출간 소식이 뜸한 느낌이 들어 아쉬웠는데, 정말 어려운 SW 아키텍처라는 주제로 새로운 책이 등장하여 반갑다. 

헤드 퍼스트 시리즈는 20년 전부터 정평이 나있듯 `오감을 자극하는 독특한 구성`이 차별점이다. 이 시리즈 외에는 이런 구성은 좀처럼 찾아보기 힘들다. 

그림 위주의 구성은 직관적인 이해를 바탕으로 빠른 이해를 돕고, 대화체를 사용하여 친근함을 높이고, 감성을 자극하여 장기 기억으로 이어질 수 있도록 도와주며, 주의를 기울이게 하여 파충류의 뇌(?)를 자극한다. 이러한 깊이 있는 이해를 바탕으로 연속적인 질문을 통해 더 깊은 사고를 가능하게 도와준다. 헤드 퍼스트 시리즈에서만 볼 수 있는 매우 독특한 구성이다. 

SW 아키텍처 주제야 말로 헤드 퍼스트식 구성에 매우 적합한 주제이다. SW 아키텍처는 대부분의 사람들이 어려워하고 무엇보다 재미를 느끼질 못한다. 나의 경우 `아래와 같은 이슈들이 SW 아키텍처를 재미없게 만든다`.

* 정답이 없다. 그래서 계속 고쳐야 한다.  
* 눈에 보이질 않는다. 그래서 설명하기도 어렵고, 깊은 사고를 요하니 힘들다.   
* 당장의 성과로 이어지지 않는다. 따라서, 현업에서 시간 낭비하는 사람으로 비춰지기 일쑤이다.  

이 책의 저자들은 위 단점들을 명확히 인지하고 있다. 이를 해결하고자 헤드 퍼스트 구성 방식으로 이 추상적인 주제를 최대한 가시화하고, 정답이 없기에 다양한 시도를 통해 현실의 사례에서 다양한 해결책을 찾을 수 있도록 지금까지 등장한 아키텍처들을 사례별로 설명한다. `모듈러 모놀리스, 마이크로서비스 아키텍처, 이벤트 기반 아키텍처 등이 그 예시`이다.  
![전체](https://theorydb.github.io/assets/img/review/review-book-headfirst-sw-architectre-5.png)  

예를 들어 아래 그림은 각각 `마이크로서비스 아키텍처와 이벤트 기반 아키텍처의 스케치`이다. 아래와 같이 각 주제에 대한 연습문제를 풀고 그리다보면 숨어있는 진의도 깨닫게 되고 이를 통해 현실의 문제에서 필요한 영역마다 해당 아키텍처를 쉽게 활용할 수 있도록 도와준다. 
![마이크로서비스](https://theorydb.github.io/assets/img/review/review-book-headfirst-sw-architectre-10.png)  
![이벤트 기반](https://theorydb.github.io/assets/img/review/review-book-headfirst-sw-architectre-11.png)  

마이크로서비스 그림을 보면 데이터베이스와 인터페이스가 잘게 분리되어 있고, 각 서비스는 자신만의 책임(로그인, 출제, 채점 등)에 초점을 맞춰 동작하며 API 등 인터페이스를 통해 통신이 이뤄짐을 알 수 있다.

반면, 이벤트 기반 그림의 경우 이벤트(로그인, 다음 문제, 답안 제출 등)가 발생할 때마다 관련 서비스(답안 처리, 자동 채점기 등)가 트리거되어 동작함을 쉽게 알 수 있다. 

이러한 예시를 통해 해당 아키텍처가 왜 등장했는지 깊이 있는 이해가 가능하다. 우리의 궁극적인 목적은 어느 아키텍처의 신봉자가 되는 것이 아니라 상황에 따라 적절한 설계를 하는 것이 주 목적이기 때문에 이 "왜"에 대한 이해는 매우 중요하다. 

위의 예시는 이 책이 갖고 있는 하나의 단편적인 소개에 지나지 않는다. 무엇보다 각각의 아키텍처 주제별들은 한권의 책으로도 충분히 이해하기가 어려운 편인데 이 책은 `단 한권의 책으로 수많은 주제를 일목요연하게 정리`함은 물론 직관적으로 이해시켜 필요한 시점에 구상할 수 있도록 도와준다는 점이다. 

아래 그림들은 각각 `다이어그램, 마이크로, 상호작용, 모듈러, MVC, 결합도, 액션과 액터, ADR` 등 아키텍처 관점에서 둘쨰가라면 서러운 중요한 주제들인데 한장의 페이지로 추상적이고 복잡한 개념을 얼마나 직관적으로 표현하는지 확인할 수 있다. 
![다이어그램](https://theorydb.github.io/assets/img/review/review-book-headfirst-sw-architectre-12.png)  
![마이크로](https://theorydb.github.io/assets/img/review/review-book-headfirst-sw-architectre-9.png)  
![상호작용](https://theorydb.github.io/assets/img/review/review-book-headfirst-sw-architectre-8.png)  
![모듈러](https://theorydb.github.io/assets/img/review/review-book-headfirst-sw-architectre-7.png)  
![MVC](https://theorydb.github.io/assets/img/review/review-book-headfirst-sw-architectre-6.png)  
![결합도](https://theorydb.github.io/assets/img/review/review-book-headfirst-sw-architectre-4.png)  
![액션과 액터](https://theorydb.github.io/assets/img/review/review-book-headfirst-sw-architectre-3.png)  
![ADR](https://theorydb.github.io/assets/img/review/review-book-headfirst-sw-architectre-3.png)  

각각의 내용을 일일이 소개하기엔 리뷰 목적에 벗어나는 일이겠지만, 리뷰에 장황하게 소개하고 싶은 충동이 든다. 위 다양한 주제들을 대부분의 독자들은 알고 있을 것이므로 스스로 알고 있는 개념과의 비교를 통해 이 책의 또다른 장점인 전달력이 얼마나 뛰어난지 비교해보기 바란다. 

`AI가 등장하며 설계는 더욱 중요해졌다.` 구현의 대부분 그리고 TDD 기반의 테스트와 배포에 이르는 자동화를 바이브 코딩 도구들에게 맡길 수 있는 시대가 되었다. 

`하지만 결국 지시를 내리는 것은 사람이다.` 현실의 문제에 어떤 아키텍처 도구를 사용할지 결정하고 책임지는 역할이 더욱 중요해졌으며 이러한 아키텍처와 설계 기법을 모르고 AI에게 지시를 내리는 것은 구슬이 서말이어도 꿰지 못하는 것과 같다. 

설계가 더욱 중요해진 이 시점에 CS 출신 전공자들에게는 말할 것도 없고, 특히 SW 엔지니어링 지식이 부족한 CS 전공 출신이 아닌 일반인 독자에게 더욱 추천하고 싶은 책이다. 

---

* [책소개 - 헤드 퍼스트 소프트웨어 아키텍처](https://www.yes24.com/product/goods/153613588)
