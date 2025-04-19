---  
layout: post  
title: "[리뷰] 제대로 시작하는 챗GPT와 AI 활용 with 파이썬"  
subtitle: "프롬프트 엔지니어링부터 음성 인식, 이미지 생성, 챗봇, 웹 서비스까지"  
categories: review  
tags: review book GPT python API 프롬프트 엔진니어링 위스퍼 CLIP DALLE 임베딩 파인튜닝 RAG   
comments: true  
header-img: img/review/review-book-gpt-for-py-dev-1.png
---  
  
> `한빛미디어` 출판사의 `"제대로 시작하는 챗GPT와 AI 활용 with 파이썬(에이먼 엘 암리 저/대니얼WJ 역)"`를 읽고 작성한 리뷰입니다.  

![표지](https://theorydb.github.io/assets/img/review/review-book-gpt-for-py-dev-1.png)  

---

> 현존하는 생성형 AI 모델 대부분을 쉽게 실습해보며 빠르게 활용법을 파악할 수 있다. 임베딩, 파인튜닝, RAG, Agent 같은 난이도 있는 기술도 핵심만 빠르게 흡수할 수 있도록 도와준다.

LLM의 중요한 장점 중 하나는 일반인이 프로그래밍 세계로 진입하는데 장벽을 매우 낮춰준다는 점이다. 덕분에 이 책에서 다루는 내용과 같이 일반인도 LLM의 도움을 받아 기존에 엄두도 내지 못했던 기능을 구현할 수 있게 되었다. 

다른 리뷰에서도 작성했지만 현시점만 놓고 봤을때 사실상 AI의 중요한 본질은 정량화, 비정형 데이터의 해석력에 있다고 생각한다. 비정형 해석 장벽이 낮아지면서 자연어로 프로그래밍 혹은 서비스를 만들 수 있는 가능성이 높아졌다. 

이 책은 OpenAI 진영의 비정형 데이터를 해석할 수 있는 다양한 모델들을 실습해보는 예제이다. 

그렇기에 눈에 띄는 장점은 다음 세가지를 들 수 있다. `첫번째로는 일반인이 따라갈 수 있는 난이도, 두번째로는 생성형 AI 모델의 전체 기능을 빠르게 훑을 수 있다는 점, 세번째로는 예시 기반으로 하니씩 실행해가며 쉽게 따라할 수 있다는 점`을 들 수 있다.

첫번째 장점은 저자가 서문에서도 밝힌 바와 같다. 기반 지식이 부족해도 자신만의 지식시스템을 구축하고자 독자에게 상당한 도움이 될 수 있는 책이다. 

대부분의 DevOps 환경 구성을 감춰줄 수 있는 구글 `코랩` 환경에서 실습이 이뤄지고, 초보자가 요금 폭탄을 맞는 실수를 피하기 위해 다양한 모델의 세부적인 `가격`까지 안내할 정도로 친절한 설명이 이어진다.
![코랩](https://theorydb.github.io/assets/img/review/review-book-gpt-for-py-dev-3.png)  
![가격](https://theorydb.github.io/assets/img/review/review-book-gpt-for-py-dev-4.png)  

물론 Python의 예제가 등장하여 프로그래밍을 해 본 독자라면 더 좋겠지만, 일단 프로그래밍을 모르더라도 깃허브에 올라온 예제를 그대로 필사하는 정도만으로도 원하는 기능을 구현하는데 큰 무리는 없을것이다. 

사실상 말이 프로그래밍이지 `OpenAI의 API를 호출`하는 형식의 코드가 대부분이기에 바둑으로 따지면 거의 외길 수순이다. 그대로 따라하면 큰 문제없이 수행된다. 

더불어 중간 중간 중요한 개념들은 자세하게 설명하며 짚어나가고 있기에 대략적인 개념 정도는 잡으며 실습할 수 있을 것이다. 예를 들어 아래 그림과 같이 `프롬프팅`이 무엇인지 개념도와 예시 설명을 들고 있다.
![프롬프팅](https://theorydb.github.io/assets/img/review/review-book-gpt-for-py-dev-5.png)  

초반부 프롬프팅과 같은 간단한 예제를 살펴보았다면 중반부에는 다양한 AI 모델을 체험할 수 있도록 구성되어 있다. DALL·E 모델을 활용하여 텍스트로 이미지를 생성해본다든가, 이미지를 합성해 보고, TTS나 이미지 분류 등을 실습하며 다양한 LLM의 활용법을 빠르게 익힐 수 있다. 
![이미지생성](https://theorydb.github.io/assets/img/review/review-book-gpt-for-py-dev-6.png)  
![이미지합성](https://theorydb.github.io/assets/img/review/review-book-gpt-for-py-dev-8.png)  

이 책은 OpenAI 중심의 모델을 주로 다루고 있지만, 부록을 참조하면 클로드와 같은 또 다른 진영의 AI 활용 실습을 진행해 볼 수 있다는 점도 장점이다.
![AI모델](https://theorydb.github.io/assets/img/review/review-book-gpt-for-py-dev-2.png)  

다만, 후반부에 해당하는 15장 임베딩 파트부터는 일반인이 따라하기에는 다소 벅찰 수도 있다. 그래도 예제대로 실습을 따라하며 주요 개념만 파악해보겠다는 자세로 진행하면 상당히 많은 지식을 얻을 수 있을것이다. 

임베딩의 경우 사실 개념상으로는 별게 없다. 이 세상의 자연어와 같은 텍스트를 단순히 숫자(조금 더 표현하면 벡터)로 변환해 주는 것이다. 

이를 통해 컴퓨터가 알아들을 수 있게 숫자로 변환이 가능해진다는 점, 나아가 코사인 유사도와 같은 수학적 도구를 사용할 수 있다는 점이 큰 특징인데 이를 통해 벡터 공간에 포진된 두 개념의 유사도를 구할 수 있고 이로써 LLM은 정규표현식에서 한걸음 더 나아간 의미 기반 검색도 가능해진다. 

다음의 예제는 `임베딩의 개념`을 아주 깔끔하게 소개해주는 예제이다. 입력된 자연어가 숫자 그것도 벡터 형태로 변환되어 출력되고 있음을 볼 수 있다. 
![임베딩](https://theorydb.github.io/assets/img/review/review-book-gpt-for-py-dev-7.png)  

여기서 한걸음 더 나아가면 독자가 보유한 자체 데이터로 기존 모델을 `파인튜닝` 할 수 있게 된다. 기능적인 측면만 놓고 봤을때는 나만의 별도 모델을 얻는 셈이다.

이 또한 일반인이 따라할 수 있을 듯 싶다. 파인튜닝 또한 OpenAI API에게 맡겨버리기 때문이다. 대시보드를 통해 아래 그림과 같이 모니터링 및 결과 확인이 가능하다. 
![파인튜닝 모니터링](https://theorydb.github.io/assets/img/review/review-book-gpt-for-py-dev-9.png)  
![파인튜닝 결과](https://theorydb.github.io/assets/img/review/review-book-gpt-for-py-dev-10.png)  

또한 부록을 포함하여 후반부에는 다양한 재미있는 예제들이 등장한다. 예를들면 `스트림릿과 깃허브`를 이용하여 건강상담 챗봇을 구현하는 예제가 그러하다. 둘 다 AI시대 각광받는 플랫폼이기에 비전공자들이 프로그래밍 세계에 진입할 수 있는 호기심 어린 좋은 예제라 생각한다.
![스트림릿과 깃허브1](https://theorydb.github.io/assets/img/review/review-book-gpt-for-py-dev-11.png)  
![스트림릿과 깃허브2](https://theorydb.github.io/assets/img/review/review-book-gpt-for-py-dev-12.png)  

그 외에도 RAG, Agent의 핵심 코드 정도를 다루고 있어 이 두 개념의 핵심을 빠르게 파악할 수 있는 예제도 등장한다. 최근 등장한 A2A, MCP와 같은 기술을 제외하고 굵직한 개념 정도는 이 책을 통해 실습 및 파악할 수 있는 셈이다.

결론적으로 이 책은 일반인, 기획자, 경영자에게 매우 많은 도움을 줄 수 있을 것 같다. 물론 개발자중에도 AI를 거의 접해본 적이 없다면 빠르게 현존하는 AI 모델의 특성을 파악하고 기획하는 서비스에 어떻게 활용할지 판단하는데 매우 큰 도움이 될 것이다. 

---

* [책소개 - 제대로 시작하는 챗GPT와 AI 활용 with 파이썬](https://www.yes24.com/product/goods/143895983)
