---  
layout: post  
title: "[리뷰] 랭체인으로 실현하는 LLM 아키텍처"  
subtitle: "LLM 애플리케이션 아키텍처 설계와 실전 개발 퀵 가이드"  
categories: review  
tags: review book AI GPT LLM 랭체인 모델 RAG 캐싱 메모리 에이전트 Vector DB   
comments: true  
header-img: img/review/review-book-llm-architecture-1.png
---  
  
> `프리렉` 출판사의 `"랭체인으로 실현하는 LLM 아키텍처(조대협 저)"`를 읽고 작성한 리뷰입니다.  

![표지](https://theorydb.github.io/assets/img/review/review-book-llm-architecture-1.png)  

---

> RAG, 에이전트 등 LLM 중심 기술의 핵심 개념을 심플하게 담아낸 책으로 관련 기술을 빠르게 실전에 적용하는데 도움이 된다. 

`LLM, RAG, 에이전트` 기술을 다룬 책이다. 저자가 그 유명한 조대협님이신데, 역시 대협님의 글 답게 `핵심 개념`이 심플하게 잘 정리되어있고 중요한 개념이 빠지지 않게 기술되어 있다. 

책이든 블로그이든 저자의 글을 읽으면 복잡한 개념을 `단권화`한 느낌이 강하게 든다. 본인이 새로운 기술을 익히면서 핵심을 정리한 느낌인데 이 책 또한 그런 방식이 개인적으로 마음에 드는 부분이다. 

책은 크게 전반부와 후반부로 나뉜다. 3장까지의 전반부는 LLM과 그 주변 기술의 간략한 기능적 개요를 다룬다. 실습은 코랩으로 진행하기에 DevOps 부분을 신경쓰지 않아도 되어서 쉽게 따라할 수 있고 LLM은 구글의 제미나이를 활용한다.
![제미나이](https://theorydb.github.io/assets/img/review/review-book-llm-architecture-2.png)  

이 책의 장점과 다루는 핵심은 4장 이후의 후반부에서 다룬다. 보통의 책은 프롬프팅의 일반적인 기술만 다루는 데 반해 이 책은 예제 선택 방법론도 다루고 있어 유익하다.

예를 들면 `통계요약 알고리즘(MMR)`이 그러한데 유사도 기반을 측정하여 토픽의 다양성과 중복 문제를 해결할 수 있다. 다만, 연산량에 따른 응답시간이나 성능적인 부분을 고려해야 한다. 
![MMR](https://theorydb.github.io/assets/img/review/review-book-llm-architecture-3.png)  

또한 LLM을 더욱 깊이있게 사용할 수 있는 다양한 기능들이 소개되어 좋았다. Buffer Memory나 Summary Memory와 같은 `메모리 컴포넌트`를 쓸 일이 있었는데 이 책 덕분에 핵심만 빠르게 파악할 수 있어 많은 도움이 되었다. 
![메모리 컴포넌트](https://theorydb.github.io/assets/img/review/review-book-llm-architecture-4.png)  

이름에 걸맞게 핵심은 4장의 체인 파트라 할 수 있다. 이중에서도 "체인"을 다루는 파트가 빠르게 기술을 습득하는데 도움을 줬다. 순차적인 체인을 구성하는 것은 별로 어려운 일이 아니지만, 병렬로 복잡한 흐름을 구성하는 것은 처음에는 까다로운 편인데 이 책에 안내된 것처럼 `Advanced Sequential Chain`을 이용한 가이드를 참조하면 좋다. 
![Advanced Sequential Chain](https://theorydb.github.io/assets/img/review/review-book-llm-architecture-5.png)  

2023년 중반에 등장한 `LCEL`의 개념도 반드시 알아둬야 할 핵심 개념이다. 이를 통해 병렬처리, 비동기 처리, 스트리밍 등의 복잡한 처리를 단순화 할 수 있다. 아울러 본 도서에는 유틸리티 체인도 다루고 있는데 이렇듯 핵심개념을 놓치지 않고 심플하게 핵심을 잘 전달한다는 점이 이 책의 매력이다. 
![LCEL](https://theorydb.github.io/assets/img/review/review-book-llm-architecture-6.png)  

마지막 5장으로 넘어가면 LangChain의 기능을 더욱 보강해주는 `RAG` 기술을 다룬다. Pinecone과 같은 유명 벡터 데이터베이스를 함께 활용하는 실습 예제가 있어 반드시 실습을 따라할 것을 권하고 싶다. 벡터DB와 임베딩의 핵심 개념 정도는 알고 있어야 이해에 무리가 없는데 다음 그림이 배경 지식을 잘 설명하고 있다. 
![임베딩](https://theorydb.github.io/assets/img/review/review-book-llm-architecture-7.png)  

임베딩이나 검색 증강을 실습하고 나면 마지막으로 `에이전트와 툴`의 개념에 대해 학습한다. 이는 LLM을 넘어서 특히 사내 데이터를 연동하거나 외부 검색엔진을 이용하여 검색의 품질을 높이는 등 벡터DB나 외부 API 서비스 등의 툴과 연동할 수 있도록 프로토콜상 독립적인 기능을 부여하여 서비스의 확장성을 돕는 기술로 2024년의 화두가 되는 기술이기도 하다. 
![에이전트](https://theorydb.github.io/assets/img/review/review-book-llm-architecture-8.png)  

이렇듯 LLM과 관련된 핵심개념을 매우 간결하게 전달하는 것이 이 책의 특징이다. 핵심 개념을 중심으로 저자의 다양한 시도 혹은 잘 갖춰진 베이스라인이 소개되고 있어 빠른 시간내에 다양한 기술과 본질을 파악하는데 도움이 된다. 

물론 그만큼 내용상 중요하지 않은 부분들은 축약된 경향이 있고, 예제 또한 영문을 활용하고 있어 친숙하지 않은 면도 있어 입문자에게는 다소 난이도 있는 책으로 보일수도 있으나 중급 이상의 경험이 있는 독자라면 오히려 핵심을 빠르게 체득할 수 있어 만족스러운 구성이 아닐까 싶다. LLM의 핵심 기술을 빠르게 습득하고 싶은 독자에게 권하고 싶은 책이다.

---

* [책소개 - 랭체인으로 실현하는 LLM 아키텍처](https://www.yes24.com/Product/Goods/129778718)
