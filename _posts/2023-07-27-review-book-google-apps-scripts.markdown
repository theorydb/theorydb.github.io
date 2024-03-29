---  
layout: post  
title: "[리뷰] 자동화 실무 사례로 배우는 구글 앱스 스크립트"  
subtitle: "대시보드, 이메일, 재고 관리 등 실전 프로젝트로 익히는 스프레드시트 & GAS 프로그래밍"  
categories: review  
tags: review book 구글 앱스 스크립트 스프레드시트 이메일 라이브러리 캘린더 문서 등록 관리 프로그래밍        
comments: true  
header-img: img/review/review-book-google-apps-scripts-1.png
---  
  
> `제이펍` 출판사의 `"자동화 실무 사례로 배우는 구글 앱스 스크립트(박용 저)"`를 읽고 작성한 리뷰입니다.  

![표지](https://theorydb.github.io/assets/img/review/review-book-google-apps-scripts-1.png)  

---

> 구글 스프레드 시트와 같은 워크스페이스 제품을 100점 만점으로 활용하는 방법을 다룬 책으로 특히 구글 앱스 스크립트를 활용하여 더욱 풍부하게 기능을 즐길 수 있는 방법들이 소개되어 있다.

구글 스프레드 시트, 캘린더 등 `구글 워크스페이스`를 만점 수준으로 활용하는 방법을 담은 책이다. 

특히, 후반부에는 구글 앱스 스크립트를 활용하여 워크스페이스 도구 간 정보를 공유하거나 웹서버 없이도 간단한 웹프로그래밍을 만들 수 있도록 구글 앱스 스크립트의 기초 문법을 배워 후원 문서 발행 프로그램을 만들어보는 과정을 거친다.

이 책을 보기 전까지는 스스로 구글 워크스페이스를 제법 잘 활용하고 있다고 착각한 것 같다. 

예전에 구글 설문지를 활용할 일이 있었다. 일반적인 설문지를 만들어 배포하는 것은 하나도 어려울 것이 없었지만 회사에 적을 두지 않은 외부인이나 익명으로 작성한 글을 거를 필요가 있다는 것이 문제였다.

그때 처음으로 구글 앱스 스크립트를 사용하게 되었는데 배포 당시 해당자의 사번과 같은 특정 고유값에 대한 암호값을 함께 전송 후 설문 응답이 수신된 데이터의 암호값이 고유값과 불일치 하는 경우 설문 응답 모데이터에서 제외하는 방법을 사용하여 꽤 요긴하게 활용한 적이 있다. 

그런 특별한 사례가 아니더라도 구글 워크스페이스는 클라우드 기반의 서비스이기에 다수의 인원이 동시에 접속하여 수정이 가능하다는 장점 및 로컬 PC 및 서버 간 동기화를 고려할 필요가 없었기에 늘 애용해왔다. 

하지만 이 책에 나온 내용을 하나씩 실습하며 그동안 구글 워크스페이스에서 제공하는 기능의 10%도 채 제대로 활용하지 못하였음을 알고 꽤 충격을 먹었다.

너무 많은 것들을 새로 배웠지만 `가장 인상적이었던 대표 기능`을 꼽으라면 `3가지` 정도로 요약할 수 있을 것 같다. 

우선, 간단한 `웹프로그램을 개발`할 수 있다는 사실에 놀랐다. 웹프로그래밍을 만드는 거야 크게 어려운 일은 아니지만 문제는 이를 운영할 수 있는 서버나 클라우드 환경 등 인프라로 인한 비용을 감당하기 어려워 쉽게 운영해오지 못했다. 
![웹프로그래밍](https://theorydb.github.io/assets/img/review/review-book-google-apps-scripts-4.png)  

이 책의 가장 큰 챕터에 소개되는 후원자 문서 발행 프로그램의 실습을 그대로 따라하다보면 간단한 기능의 웹페이지를 쉽게 만들 수 있다. 결과를 스프레드시트에 저장하며 DB처럼 활용하고, 구글 독스에 연동하여 리포트로 발행하는 등 구글 워크스페이스 제품군의 기능을 엮어 완성된 형태의 웹 서비스를 쉽게 만들 수 있다는 사실에 놀랐다. 

데이터 분석이나 AI를 학습하며 구글 코랩을 활용해 실시간으로 원하는 AI 이미지들을 만들어 내곤 했었는데 이런 전통적인 웹 프로그램도 서비스 가능한 형태로 만들 수 있다는 사실에 놀랐다. 

그 과정에 필요한 구글 앱스 스크립트는 `자바스크립트와 문법도 매우 유사`하고 이 책에서 구글 라이브러리의 활용법을 친절하게 설명해주고 있어 웹 프로그래밍을 경험한 사람이라면 큰 어려움 없이 간단한 웹프로그램을 개발하여 활용할 수 있을 것이다. 

다음으로 유익했던 것은 `스프레드시트를 DB처럼 활용`하는 기능이다. 주로 Sqlite 같은 DB를 개인적으로 활용하지만 인터넷에 연결되지 않아 동기화 측면에서 늘 불편했었는데 이젠 스프레드시트를 편리하게 이용할 수 있을 듯 하다. 
![DB화](https://theorydb.github.io/assets/img/review/review-book-google-apps-scripts-3.png)  

Python과 Pandas를 활용한 데이터 분석이 꽤 편리해졌음에도 아직도 Sql을 활용하는 것 만큼 편리하진 않다. 스프레드 시트에 `SQL을 활용`할 수 있다는 것을 이번에 처음 알았는데 엑셀과 비슷한 스프레드 시트의 직관적이지 못한 기능들 때문에 난이도 있는 사용을 꺼려왔는데 SQL과 거의 유사한 문법이 지원된다는 것을 알게되어 너무 반가웠다. 

마지막으로 엑셀과 비교 시 기능이 대동소이하지만 엑셀과 똑같은 기능을 찾으려면 어떻게 해야 하는지 난감한 적이 많았다. 이 책의 1, 2부를 따라하다보니 `엑셀과 비슷한 기능을 수행하는 기능들이 어디 숨어있는지` 명확히 알 수 있었다. 
![스프레드시트](https://theorydb.github.io/assets/img/review/review-book-google-apps-scripts-2.png)  

아무래도 구글 클라우드 제품중에서도 스프레드시트는 가장 많이 애용되는 서비스일 것이기에 저자 분도 스프레드시트에 익숙할 수 있도록 상당한 지면을 할애하신 것 같다. 덕분에 기초에 충실할 수 있어 좋았고 전달력 좋은 본 도서 덕분에 늘 미뤄왔던 엑셀과의 기능 비교 및 습득을 이 참에 정리해 볼 수 있어 좋았다. 

이 책은 구글 클라우드 및 워크스페이스의 기능을 100%에 가깝게 활용하고 싶은 분 혹은 개인적 업무의 자동화 등을 꿈꾸는 분께 꼭 추천하고 싶은 책이다. 이 책에 소개된 기능을 충실히 학습한다면 스스로 해야 할 잡무들을 효율적으로 개선하는 데 많은 도움이 될 것이다. 더불어 프로그래밍 세계에 입문하는 일반인에게도 추천하고 싶다. 


---

* [책소개 - 자동화 실무 사례로 배우는 구글 앱스 스크립트](https://www.yes24.com/Product/Goods/119851785)
