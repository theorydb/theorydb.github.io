---  
layout: post  
title: "[리뷰] 랭체인으로 LLM 기반의 AI 서비스 개발하기"  
subtitle: "현직 AI Specialist에게 배우는 RAG! 랭체인, 오픈AI API, 스트림릿으로 8가지 서비스 구현까지"  
categories: review  
tags: review book LLM AI 랭체인 RAG GPT Python 챗봇 서비스 코랩 파인튜닝 퓨샷러닝 SLM OpenAI  
comments: true  
header-img: img/review/review-book-llm-service-with-langchain-1.png
---  
  
> `길벗` 출판사의 `"랭체인으로 LLM 기반의 AI 서비스 개발하기(서지영 저)"`를 읽고 작성한 리뷰입니다.  

![표지](https://theorydb.github.io/assets/img/review/review-book-llm-service-with-langchain-1.png)  

---

> 대표적 LLM인 OpenAI를 활용하여 빠르게 AI 서비스를 구현하는 방법을 안내한 책이다. 

이 책은 기술 서적 치고는 두께가 얇은 편이다. 그렇기에 내용을 빠르게 파악하고 기초적인 AI서비스를 `빠르게` 구현할 수 있다는 점이 큰 장점인데 이 책을 읽고 얻을 수 있는 큰 세가지를 뽑자면 다음과 같다. 

첫번째로는 LLM 중심의 AI서비스의 `트렌드`를 빠르게 이해할 수 있다는 점이다. 딥러닝이 등장한 후 배워야 할 것이 너무도 많아졌다. 게다가 바로 수익을 창출할 수 있는 수준의 LLM API들이 속속들이 등장하고 있기에 최근 트렌드는 모델의 코어나 연구 수준의 이해보다는 
이를 빠르게 활용하고 수익과 연결하는 부분으로 트렌드의 중심이 이동한 느낌이다. 
![LLM](https://theorydb.github.io/assets/img/review/review-book-llm-service-with-langchain-2.png)  
![트렌드](https://theorydb.github.io/assets/img/review/review-book-llm-service-with-langchain-3.png)  

주로 유명한 LLM의 API를 활용하여 그 위에 파인튜닝이나 랭체인을 활용하여 타 서비스와의 `차별화`를 두고 있고 내부적으로 임베딩의 기법에 차이를 두는 편인 것 같다. 그렇기에 전통 모델들의 학술 레벨 수준의 깊은 이해보다는 빠른 활용에 초점을 맞추는 것이 시간 없는 현실에 대응하는 올바른 방법이라는 생각도 든다. 
![임베딩](https://theorydb.github.io/assets/img/review/review-book-llm-service-with-langchain-4.png)  

그런 측면에서 이 책은 빠르게 LLM을 활용하는 기술을 익히고 싶은 프로그래머 외에도 기획자나 프로그래밍에 대해 거의 아는 것이 없는 입문자에게도 좋은 책이 되리라는 생각이 든다. 이 책을 가이드 삼아 OpenAI의 API 문서를 참고하고 창의성만 더해진다면 어쩌면 프로그래머들이 만들 수 있는 수준 이상의 좋은 서비스를 구현하는데 문제가 없어 보인다. 

두번째는 딥러닝 중심의 기술들의 `큰흐름`을 빠르게 익힐 수 있다는 점이다. 핵심 코어인 모델의 내부나 작동원리를 설명하는 내용은 거의 없지만 앞서 언급한 바와 같이 핵심 코어의 이해는 사실 상 덜 중요한 일이 되었다. 이미 GPT 수준의 LLM을 일반인이 만든다는 것이 불가능해졌기 때문이다. 

OpenAI API 하나만 제대로 숙지해도 딥러닝 중심의 기술 활용 능력을 신장시킬 수 있는 좋은 시대이기도 하다. 앞서 언급한 바와 같이 거대 LLM의 도움을 받아 각자 나름의 차별화가 중요한 시점이 되었는데 그 차별화된 영역은 일종의 작은 딥러닝 모델이라고 볼 수 있기에 전반적인 지식을 잘 익혀둘 필요가 있다. 

다만 그 과정에서 AI 트렌드가 빛의 속도로 움직이는 현 시점에 밑바닥부터 학술 레벨 수준의 깊은 이해를 익혀나가는데는 시간적 제약이 크고 손실이 크기에 빠르게 모델에서 서빙까지의 전반을 살필 필요가 있는데 이 책이 딥러닝 중심 기술을 빠르게 익히는데 큰 도움을 준다. 

마지막으로 OpenAI API를 활용하여 `눈에 보이는 서비스`를 가장 빠르게 만드는 방법이 소개되어있다. 그 어떤 독자도 이 책을 읽으면 이렇게 짧은 코드만으로 수준높은 서비스를 구현할 수 있다는 것에 매우 놀랄것이다. 
![예제](https://theorydb.github.io/assets/img/review/review-book-llm-service-with-langchain-5.png)  

물론 이 책의 코드만으로 서비스를 제공하는 것은 상당히 빈약하다. AWS와 같이 클라우드 혹은 서버리스를 운영할 수 있는 인프라 지식도 필요하고 소스코드에 편의기능을 추가할 리액트와 같은 프런트엔드 영역에 대한 학습도 필요하다. 

뿐만 아니라 서비스 행위를 DB에 기록한다거나 모바일 서비스에서의 자원 활용 등에 대한 고찰 등 다양한 영역의 심도있는 지식이 추가적으로 필요한 것도 사실이지만 그 부분들은 이 코어를 중심으로 단계적으로 배우며 살을 붙여나가면 된다. 

중요한 것은 API를 활용하여 수준 높은 서비스의 핵심을 바로 구현하는 방법을 안내한다는 것이며 PDF 요약하기 웹사이트 예제와 같이 눈에 보이는 서비스를 구현하다보면 생각보다 빠른 시간내에 굉장한 서비스를 기획할 수 있을 것이다. 
![PDF](https://theorydb.github.io/assets/img/review/review-book-llm-service-with-langchain-6.png)  

시대의 흐름에 맞게 빠르게 LLM을 활용한 서비스를 꿈꾸는 입문자들에게 추천하고 싶다. 

---

* [책소개 - 랭체인으로 LLM 기반의 AI 서비스 개발하기](https://www.yes24.com/Product/Goods/125134177)
