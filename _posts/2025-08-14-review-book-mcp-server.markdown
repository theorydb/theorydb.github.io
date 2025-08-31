---  
layout: post  
title: "[리뷰] 나만의 MCP 서버 만들기 with 커서 AI"  
subtitle: "현직 AI Specialist에게 배우는 MCP! Cursor AI, Claude Desktop으로 MCP의 기본을 경험한다"  
categories: review  
tags: review book AI MCP 커서 클로드데스크톱 스미더리 stdio SSE Agent LLM Tavily Brave Search Google Map   
comments: true  
header-img: img/review/review-book-mcp-server-1.png
---  
  
> `길벗` 출판사의 `"나만의 MCP 서버 만들기 with 커서 AI(서지영 저)"`를 읽고 작성한 리뷰입니다.  

![표지](https://theorydb.github.io/assets/img/review/review-book-mcp-server-1.png)  

---

> 커서 및 클로드 데스크톱을 활용하여 AI 생태계 속 다양한 에이전트와 도구를 MCP로 연결하는 방법을 익힐 수 있고, 실습을 쉽게 따라할 수 있게 디테일한 설명 및 구성상 안배가 돋보인다.

최근 AI 에이전트 시대의 도래로 `MCP(Multi-Channel Protocol)와 A2A(Authority to Authority)` 프로토콜이 각광받고 있다. 전자는 멀티 채널을 통합 관리하는 플랫폼이고, 후자는 기관 간 직접 연계 및 데이터, 서비스 교환을 위한 시스템이다. 

이 책은 두개의 큰 축 중 하나인 MCP(Multi-Channel Protocol)를 다룬 도서이다. 기본 개념과 동작 원리부터 시작해 실습 환경 구축과 실제 활용까지의 내용을 한 권에 담은 점이 인상적인 책으로 LangChain 기반의 프로그래밍을 해본 독자라면 3일 정도면 충분히 실습을 따라해보며 기술 및 개념을 습득할 수 있다. 

`MCP의 개념`은 본 도서 서두에 그림 비유를 통해 쉽게 파악할 수 있다. 
![MCP구조](https://theorydb.github.io/assets/img/review/review-book-mcp-server-2.png)  
![에이전트구조](https://theorydb.github.io/assets/img/review/review-book-mcp-server-3.png)  

MCP는 다수의 AI 에이전트와 도구, 그리고 외부 서비스 간 소통을 가능하게 하는 마치 공통의 언어로, 서버-클라이언트 방식, 통신 프로토콜(studio, SSE), 입출력 명세, 상태 관리 등 핵심 스펙을 쉽게 파악할 수 있도록 도와준다. 

전반부의 가장 큰 매력은 MCP와 `OpenAI Function Calling 간의 상세 비교`를 통해 MCP가 얼마나 체계적이고 효율적으로 사용자 명령어를 도구 호출과 결과 반환까지 한 곳에서 다룰 수 있는지 알려준다는 점에 있다. 
![mcp_stdio소스](https://theorydb.github.io/assets/img/review/review-book-mcp-server-7.png)  

기능 호출 방식이 겹치는 복잡한 AI 업무를 MCP로 단일화하면, 여러 도구와 에이전트 사이의 인터페이스 문제를 획기적으로 해소할 수 있다는 점을 실감시킨다. 더불어 MCP가 에이전트를 연결해 복잡한 명령어를 자연어로 통제하면서 동시에 여러 외부 도구를 사용할 수 있는 모듈형 시스템 설계를 돕는다는 점을 쉽게 이해할 수 있다.

이 책의 가장 인상적인 부분은 2부부터 진행되는 `실습 파트`라 할 수 있다. 바이브 코딩 도구인 커서 AI와 클로드 데스크톱, 그리고 스미더리 같은 도구 생태계와 MCP 서버를 직접 활용하며 연계한다.

특히, `커서`의 경우 조금 더 깊이 있게 다루는 데 단축키 활용법을 상세히 알려주는 등 개발자들이 빠르게 생산성을 올릴 수 있게 도와준다.

예를 들어, 블록 선택 후 Ctrl+L로 채팅과 분석 작업을 시작하고, Ctrl+K로 효율적인 편집, 탭 두 번으로 주석 작성, 생성 결과 승인과 거절 단축키 등은 커서를 능숙하게 다루는 데 필수적이다. 덕분에 커서 활용에 대한 능숙도를 높일 수 있음은 물론 MCP 제품 생태계에 대한 이해도 또한 쉬워진다.
![커서](https://theorydb.github.io/assets/img/review/review-book-mcp-server-4.png)  

또한 MCP 프로토콜과 관련하여 코드 구성과 통신 방식을 다룰 때는, `JSON 명세`를 활용한 프로토콜 예시를 통해 실제 입력과 출력을 가늠케 하며, 코드 스니펫을 통해 내부 데이터 흐름이 어떻게 이뤄지는지 명확히 파악할 수 있다. 
![mcp_json](https://theorydb.github.io/assets/img/review/review-book-mcp-server-5.png)  

MCP 서버 관리 화면을 통해 여러 `MCP 서버 등록과 상태 확인 방법`도 안내하며, `스미더리` 인증 방식 변경과 공용 MCP 서버 연동법 등 실무 환경의 구체적인 부분도 빠짐없이 알려준다. 
![mcp관리](https://theorydb.github.io/assets/img/review/review-book-mcp-server-6.png)  
![스미더리](https://theorydb.github.io/assets/img/review/review-book-mcp-server-8.png)  

특히, 스미더리는 MCP의 주요 생태계로 향후 AI 기반 솔루션을 구축하는 데 있어 AI 에이전트 간 협업을 쉽게 활용하기 위해 반드시 알아두었으면 한다. 

실습은 크게 `커서 기반과 클로드 데스크톱 기반`으로 나뉘는데, 커서 기반 실습에서는 Visual Studio Code에 Python 확장을 설치한 후 FastMCP 라이브러리를 사용해 도구 등록 및 실행 방법을 단계별로 친절하게 설명한다. 

클로드 데스크톱 기반 실습은 MCP 서버 관련 .py 파일을 지정된 클로드 설치 경로에 복사하고, JSON 편집을 통해 연동하여 실제 클라우드 데스크톱 환경에서 MCP 서버를 구동하는 과정까지 상세히 안내한다. 

아울러 서지영 저자님의 책은 그간 여러번 읽어왔는데, 늘 `이해하기 쉽고 핵심을 통찰한 구성 그리고 디테일한 설명`이 마음에 드는 부분이다. 

이 책 역시 다르지 않은데 MCP 서버 구축을 위한 API 키 발급 절차, 환경 변수 설정법, 그리고 GitHub 계정 생성과 같은 실습의 기초부터 차근차근 안내해, MCP 초보자라도 단계별로 따라 하다 보면 어렵지 않게 MCP 환경에 적응할 수 있다.

MCP를 적용하려는 개발자가 마주할 수 있는 시행착오와 실무 노하우를 꼼꼼히 담은 점도 빼놓을 수 없다. 예컨대 스미더리 허브 인증 방식 변경, JSON 설정 복사 방식, 공개 MCP 서버 연결에 대한 최신 정보는 실전에 바로 활용할 수 있는 팁이다. 

이 책은 AI 생태계 속 다양한 에이전트와 도구를 자연스럽게 연결하고 운영하는 방법론을 체득하게 한다. AI 협업 시스템을 직접 설계하고 확장하는 데 든든한 밑거름이 되어주는 내용이기에 개발자, 실무자로서 최신 AI 인프라 구축 역량을 키우고자 하는 이들에게 추천하고 싶다.

---

* [책소개 - 나만의 MCP 서버 만들기 with 커서 AI](https://www.yes24.com/product/goods/150009569)
