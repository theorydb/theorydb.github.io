---  
layout: post  
title: "[리뷰] 핸즈온 생성형 AI"  
subtitle: "GPT, 라마, 뮤직젠, 스테이블 디퓨전으로 배우는 트랜스포머와 확산 모델 활용법"  
categories: review  
tags: review book AI 트랜스포머 VAE GAN 오토인코더 스테이블디퓨전 파인튜닝 드림부스 인페인팅 컨트롤넷 오디오 허깅페이스 멀티모달   
comments: true  
header-img: img/review/review-book-handson-gen-ai-1.png
---  
  
> `한빛미디어` 출판사의 `"핸즈온 생성형 AI(오마르 산세비에로, 페드로 쿠엥카, 아폴리나리우 파소스, 조나단 휘태커 저/장윤경 역)"`를 읽고 작성한 리뷰입니다. 

![표지](https://theorydb.github.io/assets/img/review/review-book-handson-gen-ai-1.png)  

---

> 다양한 생성형 AI 모델을 빠르게 활용할 수 있는 방법은 물론 내재된 근간 원리에 대한 설명도 간결하다. 무엇보다 실전에서 발생하는 다양한 시행착오와 경험을 꼼꼼하게 수록한 점이 돋보인다.

텍스트, 영상, 음성 전반을 아우르는 트랜스포머, 스테이블 디퓨전과 U-Net, 멀티모달과 CLIP 등의 생성형 AI 모델의 `원리와 활용법`을 다룬 책이다. 

핸즈온 시리즈가 가지는 특징답게 원리를 빠르게 파악할 수 있다는 장점 외에도 빠르게 `베이스 라인 코드`를 구축하여 실무에 적용할 수 있도록 구성된 점이 돋보이는 장점이다. 

특히, 저자들은 허깅페이스에서 근무하는 만큼 실무에 필요한 다양한 모델들을 실무적으로 소개하는 것은 물론 하나의 파트를 할애하여 `파인튜닝 기법`을 소개하고 있다. 
![파인튜닝단계](https://theorydb.github.io/assets/img/review/review-book-handson-gen-ai-7.png)  

파인튜닝의 일반적인 `7단계` 과정을 하나씩 실습하며 진행하면 전반적인 감을 잡을 수 있다. 그 과정에서 지시 기반 파인튜닝과 같은 성능을 개선하는 디테일한 방법도 놓치지 않고 소개하고 있어 마음에 들었다. 설명의 분량이 부족할지언정 실무에서 필요한 과정 하나하나 놓치지 않고 짚어주는 부분은 책의 또 다른 별미이다.
![지시파인튜닝](https://theorydb.github.io/assets/img/review/review-book-handson-gen-ai-8.png)  

허깅페이스 커리어 배경 덕분에 잘 알지 못했던 모델들을 다양하게 접해볼 수 있다는 점도 장점이다. 
![파인튜닝](https://theorydb.github.io/assets/img/review/review-book-handson-gen-ai-6.png)  

다른 서적의 경우 보통은 텍스트 기반의 파인튜닝 기법 정도만 소개하는 반면 다소 다양한 방법론이 존재하는 스테이블 디퓨전 파인 튜닝을 소개하고 있는 것도 반가웠다. 
![SD파인튜닝](https://theorydb.github.io/assets/img/review/review-book-handson-gen-ai-9.png)  
![드림부스](https://theorydb.github.io/assets/img/review/review-book-handson-gen-ai-10.png)  

`멀티모달`이 대세인 만큼 텍스트, 영상, 음성 어느 한 영역에 집중하지 않고 다양한 모델들을 다루고 `CLIP`과 같은 모델과 더불어 멀티모달의 개념에 대해서도 설명하고 있다. 

그 외에도 생성형 AI의 `근간`이 된 트랜스포머나 VAE 등의 모델을 다루고 핵심 원리를 전달하고 있어 활용의 깊이를 더해주고, `검색 증강 생성(RAG)` 기법까지 연계하여 실무에 마주할 수 있는 다양한 실전 팁을 제공한다는 장점이 있다. 

핵심 기본 개념은 주로 파트1에 소개되는데 트랜스포머를 비롯 무엇하나 빠질 수 없는 중요한 개념이다. 이 기본 구성요소에 대한 이해 없이는 Gen AI를 깊이있게 파악하고 미세조정하기 어렵기 때문에 반드시 숙지해야 하는 개념이다. 
![트랜스포머](https://theorydb.github.io/assets/img/review/review-book-handson-gen-ai-2.png)  

텍스트 분야에서 트랜스포머를 설명했다면, 이미지 분야에서는 `GAN부터 U-Net`과 같은 스테이블 디퓨전의 핵심 모델의 개념과 원리를 설명한다.
![GAN](https://theorydb.github.io/assets/img/review/review-book-handson-gen-ai-4.png)  
![U-Net](https://theorydb.github.io/assets/img/review/review-book-handson-gen-ai-5.png)  

다만, 실전 중심으로 선 구현 후 조정하는 경우 먼저 파트2 이후를 읽고 나중에 파트1을 읽어도 될 것 같다. 잠재공간 탐색은 생성형 AI에서 활용되는 주요 원리임에도 당장의 서비스 구현에는 필요하지 않기 때문이다. 
![잠재공간탐색](https://theorydb.github.io/assets/img/review/review-book-handson-gen-ai-3.png)  

후반부에 이르면 `바늘찾기`와 같은 맥락 검색 평가 기법을 소개하며 검색의 품질을 높이는 방법들이 제시되는가 하면, 추론 서버와 학습 서버 각각의 메모리 요구사항과 같은 디테일한 부분도 잘 전달하고 있어 온프레미스 방식의 구축에 다양한 해법을 준다. 
![바늘찾기](https://theorydb.github.io/assets/img/review/review-book-handson-gen-ai-16.png)  
![추론서버 메모리요구사항](https://theorydb.github.io/assets/img/review/review-book-handson-gen-ai-17.png)  
![학습서버 메모리요구사항](https://theorydb.github.io/assets/img/review/review-book-handson-gen-ai-18.png)  

텍스트-이미지 모델의 경우 세부적으로 들어가면 리얼리티나 품질을 위한 다양한 기능이 존재하기 마련인데 `인페인팅이나 컨트롤넷`과 같은 다양한 기법들이 빠지지 소개되고 있어 유익했다. 
![인페인팅](https://theorydb.github.io/assets/img/review/review-book-handson-gen-ai-11.png)  
![컨트롤넷](https://theorydb.github.io/assets/img/review/review-book-handson-gen-ai-12.png)  

실무를 경험하며 저자들이 중요하다고 생각했거나 `시행착오`를 거친 주요 자료들의 핵심을 잘 정리한 느낌이다.

`음성` 파트의 경우 텍스트, 이미지 파트에 비해 파인튜닝 기법도 소개되지 않고 9장 한장 정도에 소개되어 있어 약간의 아쉬움도 있지만 파형 변환과 같은 필수적인 내용이 담겨있어 유익하다. 
![오디오생성](https://theorydb.github.io/assets/img/review/review-book-handson-gen-ai-13.png)  

대신, 향후 연구해보면 좋을 데이터셋이나 모델 등 필요한 부분은 꼼꼼하게 챙겨주고 있다.
![데이터셋](https://theorydb.github.io/assets/img/review/review-book-handson-gen-ai-14.png)  
![모델](https://theorydb.github.io/assets/img/review/review-book-handson-gen-ai-15.png)  

요약하자면, 클라우드 기반보다는 온프레미스 기반으로 LLM을 구축하여 활용하는 실무 진영에 더욱 도움되는 책으로 빠르게 Gen AI 기술을 익히고 구현해 보고 싶은 실무자들에게 일독을 권하고 싶다. 이 베이스 라인 코드들을 기반으로 조금 더 기술과 연구를 가미한다면 괜찮은 생성형 AI 기반의 서비스를 제작 및 제공할 수 있을 것이다.

---

* [책소개 - 핸즈온 생성형 AI](https://www.yes24.com/product/goods/148025270)

