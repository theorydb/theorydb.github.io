---  
layout: post  
title: "[리뷰★] RAG 마스터 : 랭체인으로 완성하는 LLM 서비스"  
subtitle: "멀티모달·그래프 RAG·에이전트·파인튜닝까지"  
categories: review  
tags: review book AI LLM RAG Langchain 프롬프트 벡터DB 멀티모달 고도화 그래프DB 파이프라인 랭그래프 파인튜닝 임베딩    
comments: true  
header-img: img/review/review-book-rag-master-1.png
---  
  
> `프리렉` 출판사의 `"RAG 마스터 : 랭체인으로 완성하는 LLM 서비스(브라이스 유, 조경아, 박수진, 김재웅 저)"`를 읽고 작성한 리뷰입니다.  

![표지](https://theorydb.github.io/assets/img/review/review-book-rag-master-1.png)  

---

> RAG 고도화 전략에서 LLM 파인튜닝에 이르는 RAG 기술을 총 망라한 책. 전달력과 가독성이 일품이다.   

RAG 기술을 다룬 책 중 가히 최고점을 줘도 손색이 없는 책이다. 물론 번역서 중 이 책 수준의 훌륭한 책이 여럿 있지만 한국인 저자가 직접 집필한 책이라 특히 `전달력과 가독성` 부분에서는 만점을 주고 싶은 책이다. 

다루고 있는 기술의 범위 또한 방대하여 최근 등장한 `MCP, A2A를 제외하면 LLM 활용 기술의 거의 모든 것`이 녹아있다. 저자들의 연구 수준이 돋보일 정도로 이론적으로도 완성도가 높고, 실무적으로는 다양한 예시와 경험이 담겨있어 독자의 시행착오를 크게 줄여준다.

지금까지 기술서를 최소 1천권은 넘게 읽었고, 리뷰만 해도 300권 가까이 작성을 해 왔는 데 그중 최고 레벨에 해당하는 전달력과 가독성을 자랑한다. 다른 기술서들도 이 책의 전달력과 가독성을 교본 삼았으면 좋겠다는 생각이 든다. 

책은 크게 세 부분으로 나뉜다. 전반부 1~3장은 RAG와 Langchain 등 LLM을 활용하는 데 필요한 `기본 기술`을 다룬다. 

전반부의 돋보이는 장점은 마치 `라이브 코딩 강의`를 보는 듯한 구성이다. LangChain 모듈이 발전해 온 과정을 추적하면서 실습 또한 이전 코드 대비 향상된 기능의 핵심만 쉽게 파악할 수 있도록 구성되어 이해하기가 쉽다. 이 과정을 통해 핵심을 제외한 코드들을 반복적으로 확인할 수 있기에 자연스럽게 LLM 활용 기술을 숙달할 수 있다.

예를 들면 OpenAI() 클래스를 LangChain 모듈의 ChatOpenAI() 클래스로 대체하는 예제를 수행하며 어떤 방식으로 종속성을 탈피할 수 있는지 확인할 수 있도록 차이점을 중심으로 예제를 수행하고 발전의 트렌드를 이해하기 쉽도록 핵심 개념을 전달한다.

책의 가독성을 높이는 대표적인 수단으로는 위에서 설명한 바와 같이 핵심 개념의 흐름을 체계적으로 정리하는 것 외에도 좋은 그림과 예시를 드는 방법이 있다. 아래 그림은 챗봇 실습을 진행할 RAG 구성도를 보여주는데 지금까지 봐 온 `그 어떤 그림 보다도 핵심만 명쾌히 전달`하는 느낌을 받을 수 있었다. 
![RAG 구성도](https://theorydb.github.io/assets/img/review/review-book-rag-master-4.png)  
![멀티모달 구성도](https://theorydb.github.io/assets/img/review/review-book-rag-master-6.png)  

또한, 후반부와 연계된 기술을 초반에 미리 설명하여 `전체적인 체계`를 쉽게 잡을 수 있게 도와준다. 단순히 전반부에 임베딩 API를 사용하는 것을 넘어 다양한 임베딩 전략을 소개하고 이를 파인튜닝 할 경우 비용 절감과 같은 이득을 취할 수 있음을 소개한다. 
![임베딩](https://theorydb.github.io/assets/img/review/review-book-rag-master-2.png)  

벡터DB의 경우도 단순히 책쓰기 편한 크로마 같은 예제를 실습하고 마는 것이 아니라 다양한 벡터DB의 장단점을 살펴보고 이에 대한 레퍼런스 출처도 제공한다. 
![벡터DB](https://theorydb.github.io/assets/img/review/review-book-rag-master-3.png)  

더불어 `실무에 있어 시행착오와 소요 시간을 최소화` 할 수 있도록 저자들의 다양한 경험이 소개된다. LLM과 연관된 생태계 기술인 Streamlit, Pyngrok과 연계하여 서비스를 쉽게 구성할 수 있는 방법이 소개된다. 

에코 기술은 다른 책에도 흔하게 소개되는 부분이지만 아래 그림과 같이 매우 디테일한 부분까지 안내되고 있는 점이 돋보인다. 저자들이 실무 경험을 통해 시간이 많이 소요된 부분, 시행착오에 걸렸던 부분들을 놓치지 않고 짚어주는 꼼꼼함이 인상적이었다.
![Pyngrok](https://theorydb.github.io/assets/img/review/review-book-rag-master-5.png)  

중반부는 `RAG 고도화 전략`이 핵심이다. 기본적인 RAG를 뛰어넘어 성능을 고도화하는 다양한 기법과 더불어 그래프 RAG, 랭그래프, 리액트 에이전트 기술을 다룬다. 

RAG 고도화 파트는 주요 전략들을 일목요연하게 정리하여 `초반에 체계를 잡는데 도움`이 되며 각 전략별로 실습을 수행하다보면 자연스레 성능을 개선할 수 있는 스킬을 숙달할 수 있다. 
![RAG고도화](https://theorydb.github.io/assets/img/review/review-book-rag-master-7.png)  
![다중질의](https://theorydb.github.io/assets/img/review/review-book-rag-master-8.png)  

Self RAG나 자체교정 RAG 파트만 봐도 다른 레퍼런스들은 쓸데없이 복잡하게 설명하여 지루한 반면 이 책은 이론적으로 `핵심만` 잘 요약하여 전달하며 실습을 통해 나머지를 이해할 수 있도록 구성한다.
![Self RAG](https://theorydb.github.io/assets/img/review/review-book-rag-master-9.png)  
![자체교정 RAG](https://theorydb.github.io/assets/img/review/review-book-rag-master-11.png)  

더불어 추후 필요시 논문이나 `다른 이론과 연계`하여 서비스를 확장할 수 있도록 도와준다. 본문에 반영하기엔 너무 방대한 기술이지만 추후 서비스 확장 혹은 또 다른 해결책을 찾을 때 도움이 될 수 있는 연계 연구자료가 군데군데 수록되어있어 실무에 매우 유익했다. 아래 그림과 같이 그리닝 기법의 연구 내용 소개가 그 예시이다.
![Gleaning](https://theorydb.github.io/assets/img/review/review-book-rag-master-10.png)  

후반부는 파인튜닝이 핵심이다. 개인적으로는 실무에서 궁극적으로 파인튜닝 LLM을 로컬에서 도입할 예정인데, `LLM Qwen 파인튜닝` 실습 부분은 로컬 LLM 전반을 이해하는데 많은 도움을 받을 수 있었다. 

임베딩 파인튜닝 부분 또한 연계하고자 하는 LLM과 호환만 된다면 불필요한 `토큰 비용을 줄일 수 있는` 부분이라 관심이 많았는데 저자들의 경험을 기반으로 한 성능 개선에서 평가에 이르는 절차가 꼼꼼하게 소개되어있어 유익했다. 

결론적으로 이 책은 LLM 활용 기술의 범위, 전달력과 가독성, 이론과 실무의 완성도, 경험과 노하우를 통한 시행착오의 최소화 등 다양한 측면에서 만점에 가까운 책이다. 

그동안 다른 RAG 도서를 읽어도 진입장벽을 뛰어넘지 못했거나, API 레퍼런스에 소개된 기술 정도는 익히고 있으나 그 이상 넘어가지 못했던 독자들에게 특히 도움이 될 것이며 그 외에도 RAG를 다루는 모든 독자에게 도움이 될거라 확신한다. 

---

* [책소개 - RAG 마스터 : 랭체인으로 완성하는 LLM 서비스](https://www.yes24.com/product/goods/144689418)
