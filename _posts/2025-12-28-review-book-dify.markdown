---  
layout: post  
title: "[리뷰] Dify AI, 코드 없는 미래"  
subtitle: "클릭만으로 업무 프로세스 리빌드, 노코드 AI 자동화 실전 가이드"  
categories: review  
tags: review book AI Dify 노코드 API 챗봇 LLM RAG Agent 워크플로우 자동화 컨텐츠 생성 Ollama Qwen3   
comments: true  
header-img: img/review/review-book-dify-1.png
---  
  
> `한빛미디어` 출판사의 `"Dify AI, 코드 없는 미래(김정욱 저)"`를 읽고 작성한 리뷰입니다.  

![표지](https://theorydb.github.io/assets/img/review/review-book-dify-1.png)  

---

> 오픈소스 LLM 애플리케이션 플랫폼인 Dify를 넘어 AI 세계의 주류 기술을 하나로 엮어 활용할 수 있게 구성된 점이 인상적이다.

Dify 이전에도 RAGFlow, Langflow, Flowise, n8n, Botpress와 같은 AI 기술의 통합을 지향하는 다양한 플랫폼들이 존재했지만 Dify는 이들을 한번 더 래핑한 느낌이다. 

먼저 Dify를 짧게 요약하자면 `오픈소스 LLM 애플리케이션 플랫폼`으로 노코드 방식의 AI 에이전트 개발을 가능하게 해준다. 

`워크플로우, RAG, 에이전트 프레임워크, 모델 관리, 모니터링` 등의 기능을 제공하고 노코드 기반으로 동작할 수 있게 해주며 클라우드나 온프레미스 가리지 않고 지원한다는 점이 인상적이다. 

이 책은 `리뷰분석, 경쟁사 분석, 블로그 요약, 글로벌 동향 요약 등 다양한 실습`을 통해 Dify를 쉽게 익힐 수 있게 도와주는 것이 일차 목표로 보이지만, 사실 그 이상의 매력을 품고 있는 책이다. 

저자가 서문에서 밝혔듯이 `AI 설계 사고`에 중점을 둔 책이라는 점이 이 책의 가장 매력적인 부분이다. Dify는 현재 AI 기반 서비스 및 기술의 대부분을 녹이고 있는 플랫폼이기에 AI 세계의 대세로 자리매김하고 있지만 워낙 이 분야의 기술의 변화가 빠른 만큼 언제까지 독보적인 위치를 점유할 수 있을지는 미지수이기도 하다. 

이런 시점에서 중요한 것은 쏟아지는 정보 속에서 `노이즈와 시그널을 구별할 줄 아는` 능력인데 특정 플랫폼 혹은 서비스 하나하나에 연연할 것이 아니라 전반적으로 어떤 기술들이 주류로 채택받고 있는지 어떻게 변화하고 있는지 숲을 볼줄 아는 능력이 중요한 시기인 것 같다. 

예를 들어보자. 아래 그림과 같이 Dify를 통해 클릭 기반으로 노코드로 LLM에서 파생된 기술을 활용할 수 있다. 청크 설정에서 리랭크, 임베딩 등의 개념은 각각의 개념 하나로 책 한권도 모자랄만한 주제의 영역이다. 
![Dify](https://theorydb.github.io/assets/img/review/review-book-dify-2.png)  

시대의 변화가 빠른만큼 이런 AI 개념들이 무엇인지 깊이있게 팔 시간은 없을지라도 확실한 개념을 잡아둬서 Dify 이후 다른 플랫폼이 나오더라도 유사한 기능을 빠르게 찾아 동일한 결과를 내는 서비스를 지향할 정도의 능력은 갖춰야 하는데 이 책은 앞서 언급했듯 Dify 기능 자체가 아닌 AI 설계 사고에 초점을 맞추고 있어 대세 `AI 개념과 기술 트렌드의 흐름을 쉽게 잡을 수 있다`는 점이 큰 장점이다. 

그만큼 꼼꼼하고 친절한 전달력과 AI 기술과 개념을 중간중간 잘 정리한다는 점이 돋보인다. AI 관련 사업을 진행하다보면 토큰 비용 산정 및 예산 확보 영역이 은근 귀찮은 영역인데 이 부분의 핵심은 컨텍스트 윈도우 산정에 달려있다. 

컨텍스트 윈도우가 무엇인지 아래 그림으로 한번에 전달하고 있는데 이렇게 쉽게 표현한 경우를 찾기가 쉽지 않다. 
![컨텍스트 윈도우](https://theorydb.github.io/assets/img/review/review-book-dify-7.png)  

또한, 3대 LLM API 서비스 이용요금도 아래와 같이 잘 정리하고 있어 이 책 하나만으로도 AI 사업을 진행하는데 많은 영역에서 불편을 줄여주기에 인상적이다. 저자가 정말 정성들여 책을 쓴 흔적이 군데군데 느껴진다. 
![OPENAI](https://theorydb.github.io/assets/img/review/review-book-dify-8.png)  
![CLAUDE](https://theorydb.github.io/assets/img/review/review-book-dify-9.png)  
![GEMINI](https://theorydb.github.io/assets/img/review/review-book-dify-10.png)  

Dify에서 연동가능한 각종 Agent API 목록이나, 네이버와의 MCP 연동, 워크플로우의 활용법 및 핵심 개념도 아래 그림과 같이 핵심 위주로 담아내고 있어 AI 생태계의 전반을 조망하기 용이하다. 
![Agent](https://theorydb.github.io/assets/img/review/review-book-dify-3.png)  
![MCP](https://theorydb.github.io/assets/img/review/review-book-dify-4.png)  
![워크플로우](https://theorydb.github.io/assets/img/review/review-book-dify-5.png)  

사실 여기까지만 해도 참 높은 점수를 주고 싶은 책인데 마지막 부록 부분에서는 온프레미스 방식으로 Dify를 설치하는 부분, Ollama나 Qwen3와 같은 오픈소스 LLM을 설치하는 방법도 안내를 하고 있어 현존하는 AI 대세 기술을 집대성한 느낌이 들었다. AI 시대에도 책이 가지는 가치와 방향성을 잘 드러내는 양서라는 생각이 들었다. 
![Ollama](https://theorydb.github.io/assets/img/review/review-book-dify-6.png)  

그 외에도 Zapier와의 연동을 통해 플랫폼 구글, 슬랙 등 대세 플랫폼과의 연동은 물론 AI가 상황을 판단하고 최적의 행동을 선택하는 지능형 자동화에 이르기까지 생태계 전반을 엮어주는 책이기에 단순히 Dify를 넘어 빠르게 AI 트렌드 변화를 파악하기에 제 격이다. 

AI 분야에 종사하는 독자라면 Dify 채택 여부와 무관하게 꼭 한번 일독을 권하고 싶다.

---

* [책소개 - Dify AI, 코드 없는 미래](https://www.yes24.com/product/goods/167437364)
