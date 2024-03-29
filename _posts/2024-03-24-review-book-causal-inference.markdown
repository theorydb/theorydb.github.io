---  
layout: post  
title: "[리뷰] 실무로 통하는 인과추론 with 파이썬"  
subtitle: "데이터 분석에서 정책 수립까지, 이론과 사례 연구를 통한 실용적인 학습법"  
categories: review  
tags: review book 통계 인과 추론 상관관계 인과관계 연관관계 ATE ATT CATE A/B테스트 회귀분석 성향점수 처치 실험 설계    
comments: true  
header-img: img/review/review-book-causal-inference-1.png
---  
  
> `한빛미디어` 출판사의 `"실무로 통하는 인과추론 with 파이썬(마테우스 파쿠레 저/신진수, 가짜연구소 인과추론팀 역)"`를 읽고 작성한 리뷰입니다.  

![표지](https://theorydb.github.io/assets/img/review/review-book-causal-inference-1.png)  

---

> AI가 아직 해결하기 힘든 난제이자 진리로 향하는 필수 도구인 인과추론의 개념과 도출 기법을 다룬 몇 안되는 희귀한 도서.

> "`인과관계`는 상관관계와 다르다."(이 책에서는 상관관계를 연관관계라는 단어로 표현한다.)

아이스크림이 많이 팔리면 상어에게 인간이 잡혀먹힐 확률이 높다라는 가정은 직관적으로 생각해도 말이 안되는 명제이지만 일상에서 생각보다 많은 사람들이 상관관게의 현상에 가려 잘못된 인과를 도출한다. 

실상 원인은 기온이고 그에 따른 결과로 아이스크림이 많이 팔릴 뿐이다. 기온이 올라가니 사람들이 해변에서 수영을 즐기는 빈도가 높아지고 자연스레 상어로 부터의 위험에 노출될 확률이 올라가는 것이다. 

그럼에도 해당 도메인 분야에 약간의 무지만 더한다면 상관관계와 인과관계를 구별하는 것은 생각보다 쉬운일이 아니다. 이 책은 통계학적 기법을 중심으로 그 차이를 분별해 낼 수 있는 능력을 키워주는 도서이자 나아가 통계 모델과 수학을 활용하여 관측된 데이터를 객관적으로 해석할 수 있는 방법을 도출하는데 도움을 준다. 

사실 인과추론은 결코 쉬운 주제가 아니다. 경험의 축적을 통해 충분히 인과관계를 밝힐 수 있는 직관이 확립된 일상생활이나 또는 수십년간의 연구를 통해 해당 도메인 분야에 내공이 쌓인 경우가 아니라면 결국은 관측 데이터를 통해 궁금증을 해결할 수 밖에 없기 때문이다. 

위험한 함정에 빠지지 않기위해 이 책에서는 `실제 데이터와 파이썬의 시각화를 통한 검증`을 거쳐가며 가급적 쉽게 인과추론의 타당성을 검증해 나간다. 
![예시데이터](https://theorydb.github.io/assets/img/review/review-book-causal-inference-2.png)  

책의 구성 상 차례대로 읽어나갈 것을 권하고 싶다. 특히 1장의 경우 인과추론 입문 과정의 필수지식을 담고 있기에 반드시 정독해야 한다. 인과추론의 기본 개념은 물론 관계 `심슨의 역설`과 같은 반드시 알아두어야 할 인과 함정 등의 내용이 등장한다.
![심슨의 역설](https://theorydb.github.io/assets/img/review/review-book-causal-inference-3.png)  

특히, ATE(평균 처치효과), 실험군에 대한 평균 처치효과(ATT), 조건부 평균 처치효과(CATE) 개념은 반드시 숙지해 둬야 할 개념이다. `인과추정량`을 모르고는 2장부터 마지막까지 이어지는 대부분의 내용을 이해하기 어려울 것이다. 
![인과추정량](https://theorydb.github.io/assets/img/review/review-book-causal-inference-6.png)  

인과의 함정을 피하기 위한 도구로 후반부 까지 지속적으로 검증에 도움을 주는 도구로 활용되기 때문이다.

초반부에는 인과를 검증하기 위한 어려 장치들이 등장한다. 통계학 진영에서 긴 세월동안 축적해 온 귀무가설의 p-value를 측정할 때 활용하는 `유의성 검증`부터 시각적 도구로 난해한 관계에 직관을 부여하는 `그래프 인과 모델` 등이 그러한 예시이다.
![유의성검증](https://theorydb.github.io/assets/img/review/review-book-causal-inference-4.png)  
![그래프인과모델](https://theorydb.github.io/assets/img/review/review-book-causal-inference-5.png)  

2부로 넘어가면 회귀분석을 활용하여 `편향을 제거`하는 방법이나 및 `성향점수`나 이중 강건 추정법을 활용하는데 마치 연안에서 망망대해를 나가는 과정에 비유할 수 있겠다. 

3부에서는 `머신러닝`을 활용한다. 그간 전통적인 통계 기법은 엄밀성을 강조한 나머지 추론한 결과의 신빙성은 보호할 수 있었으나 경영진이 의사결정하는데 있어 정작알고 싶은 가려운 구석은 긁어주지 못하는 한계를 가지고 있었다. 

최근 화두가 된 AI 진영의 기법이 더해지면서 보다 실용적으로 인과추론을 활용하는 시도들이 소개된다. `T, X, S러너`들이 대표적인 기법들인데 `개인화`에 초점을 맞춘다거나 편향을 제거하는데 보다 좋은 성과를 얻을 수 있다. 

4부는 개인적으로 가장 흥미롭게 읽었던 부분이다. 솔직히 통계학 전공이 아니기에 매 순간 이해하는데 어려움이 많았는데 이 파트는 더욱 이해하기 어려웠다. 인과에 시간이 더해지는 파트이다.

사실 인과 자체도 어려운 영역인데 시간 역시 만만치 않다. 시간을 정의내리는 것이 쉽지 않기 때문이다. 과학을 넘어 철학까지 이어지는 여정은 흥미롭고 신비한 여정이지만 그에 상응하는 고통도 수반한다. 누구도 시간을 흔쾌히 정의내리지 못한다. 아인슈타인의 시공간이 하나라는 개념이 더해지면 더욱 그렇다. 

문제는 인과는 정의만 쉽지 검증이 어렵다. 이 두 난해한 과제가 만나 시계열 분석은 물론 인과추론까지 접목되어 통계학에서 그간 애용된 `이중차분법`과 같은 모델이 만나니 왠만한 내공의 독자가 아니면 이 파트를 속시원히 설명하긴 어려울 듯 하다.

마지막 5부에서는 불연속 설계나 스위치 백 실험들이 등장하고 추가로 학습해 볼만한 주제들이 등장한다. 

저자는 이 책을 인과추론의 입문서 정도로 소개했지만 안에 담긴 내용은 `결코 입문서 수준이 아님`에 유의하길 바란다. Python 예제들은 직관을 도출하거나 난해한 통계 검증 기법을 시각화 시켜주는데 도움을 주지만 인과추론을 연역적으로 기술하는 도구는 아니다. 어디까지나 보조장치로 활용되기에 Python으로 인과추론을 이해하는 구성이라 생각하면 안될 것 같다. 

그보다는 머신러닌 진영의 기법이나 특히 통계학의 수학을 기반으로 한 연역 기법이 많이 활용되고 있어 Python과 같은 프로그래밍 스킬은 물론 통계학이나 수학적 지식의 베이스가 탄탄한 독자가 읽는 것이 이해에 무리가 없을거라 생각한다. 

개인적으로 인과추론은 향후 AGI에의 도달을 위해 해결해야 할 가장 큰 장애물 중 하나라고 생각한다. 현 시점 묵과할 주제가 아니라는 말이다. 

게다가 인과추론은 신생 학문이고 참조할 만한 레퍼런스가 너무 적다. 그런 의미에서 현 시점 이 책이 가지는 가치는 상당할 것으로 평할 수 있을 것이다. 한 단계 고차원적인 AI 기법의 하나이자 보다 정확한 진실을 향해 다가가는데 활용할 수 있는 도구로써 인과추론에 관심있는 독자들에게 본 도서의 일독을 권하는 바이다.

---

* [책소개 - 실무로 통하는 인과추론 with 파이썬](https://www.yes24.com/Product/Goods/125196916)
