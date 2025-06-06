---  
layout: post  
title: "[리뷰] 멀티패러다임 프로그래밍"  
subtitle: "객체지향, 함수형, 명령형의 통합적 사고로 구현하는 소프트웨어 설계와 구현"  
categories: review  
tags: review book 프로그래밍 멀티패러다임 OOP 명령형 이터러블 함수형 제너레이터 비동기 동시성 Setting todo app    
comments: true  
header-img: img/review/review-book-multiparadigm-programming-1.png
---  
  
> `한빛미디어` 출판사의 `"멀티패러다임 프로그래밍(유인동 저)"`를 읽고 작성한 리뷰입니다.  
![표지](https://theorydb.github.io/assets/img/review/review-book-multiparadigm-programming-1.png)  

---

> 왜 멀티패러다임이 필요한지 본질을 알게 해주는 저자의 내공에 놀랐고, 이론과 실무의 간극을 없애는 전달력에 한 번 더 놀랐다.

간만에 또 불세출의 명작이 등장했다. 10년 전에 읽었던 멀티패러다임 프로그래밍을 다룬 또 하나의 명작 "브루스 테이트의 세븐 랭귀지《Seven Languages in Seven Weeks》"의 신선함을 다시금 느끼게 해준 명작이 이번엔 국내 저자에 의해 출간되어 더욱 기쁘다. 

세븐랭귀지는 Ruby, Io, Prolog, Scala, Erlang, Clojure, Haskell 등 7개의 언어를 다루면서 언어나 패러다임은 도구일뿐 개발자로 하여금 `멀티패러다임`을 통한 문제 해결 본질에 집중하게끔 나무보다 숲을 보는 안목을 키워줬던 책이다. 

반면 본 도서는 앞선 도서 대비 국내 저자의 저술인만큼 `가독성`이나 `전달력` 측면에서 현저히 뛰어나고, 또 ES6나 ES2017 등 그 이후 `10년 간의 변화`를 살펴보며 멀티패러다임 프로그래밍이 어떻게 정착했는지를 엿볼 수 있다. 

무엇보다 실무에 즉시 적용할 수 있는 예제가 풍부히 수록되고, 원리에서 출발하여 실무에 적용하는 과정 즉, `왜 활용하는지`에 대한 부분을 구체적으로 보여줌으로써 `이론과 실무의 간극을 메우는` 구성이 탁월하다.

25년 전 대학시절 C언어로 온갖 서비스를 구현하는 고수 선배의 코딩을 어깨너머 지켜본 적이 있다. C언어로 인코더나 디코더를 직접 구현하며 cgi로 웹 프로그램을 만들고, socket 통신은 물론, 게임 등 장르를 가리지 않는 탁월함에 적잖이 놀랐다. 

그 중 가장 인상깊었던 프로젝트는 당시 OOP 개념이 지금처럼 전방위에 퍼지지 않았던 시점임에도 절차지향 프로그래밍의 대명사였던 C언어를 가지고 OOP 흉내를 내는 과정이었다. 

`구조체를 객체와 유사하게 활용하고, 내부에 함수 포인터를 활용하여 메소드 처럼 활용하는` 방식이었는데 그도 모잘라 define 매크로를 활용하여 마치 요즘의 타입 추론과 함수형 언어를 흉내내는 것이 영락없는 무림세계 그것도 마교의 교주 천마같은 느낌이었다. 

그 과정을 지켜보는 것은 굉장히 흥미로웠는데 까마득한 후배인 나로써는 C언어를 저렇게 Pythonic하게 활용하는 것이 맞는지 궁금증이 들기도 했고, 때로는 안정성에 문제가 있을 것 같은 불안감이 들기도 했고, 그럼에도 필요한 요소요소마다 언어를 철저히 도구로 수려하게 활용함에 감탄하기도 했다.

이런 고수가 있었는가 하면 또 한편으로는 개발자 커뮤니티에선 별 쓰잘데기 없는 논쟁이 벌어지기도 햇다. C언어와 PHP언어 중 무엇이 훌륭하냐는 어리석은 논의였는데 프로그래밍을 당시 무협 세계에 종종 빗대었던 개발자들의 이상한 습성은 흡사 정사대전을 보는 듯 했다. 

사실 문제의 본질을 파악하여 해결하기 위한 과정이 중요하기에 도구가 목적이 아닌이상 도구의 쓰임새를 논할일이지 그 자체의 우수성을 따지는 것은 정말 불필요한 논쟁이다. 그럼에도 그때는 범용 언어인 C언가 훨씬 잘낫다느니, 콩나물을 사러가는데 자전거를 타야지 쓸데없이 그랜저를 타고가는게 맞냐며 PHP를 옹호하는 등 각자 나름의 개똥철학을 펼치며 스스로가 좋아하는 문파(?)를 비호하는 어리석은 무림인이 널리고 널렸다.

아무튼 이 책은 다양한 언어들이 가진 특성을 제대로 이해하고 선택하며 문제해결에 최적의 방안을 찾기 위한 언어 및 패러다임의 장점만 뽑아낸 조화를 추구하는 책이다. 더 나아가 저자의 풍부한 경험을 바탕으로 이론과 실무의 간극을 메워준다. 

저자는 국내 굴지의 기업에서 경험을 쌓았으며 타입스크립트, 오브젝티브-C, 자바, Node.js 등 다양한 언어를 다뤄왔고, fx.js 창시자로 오픈소스 메인테이너 활동까지 참여해 온 고수이다. 

무엇보다 책의 내용과 전달력이 저자의 능력을 입증한다. 책의 내용은 마치 `라이브코딩`을 보는 듯 전달력이 뛰어나며, 구체적인 예시를 들어 Why 문제에 대한 본질을 전달하는 과정은 예술의 경지에 가깝다. 

예를 들어 본문 중에 `NodeList가 왜 상속이 아닌 interface를 활용했는지`에 대한 답변을 예시를 통해 명쾌하게 설명한 부분이 있다. 

한 컨트리뷰터가 NodeList에 Array를 상속받도록 작성하여 배포한 사례를 가정하는 부분이 좋은 예시가 되겠다. 이후 Array에 변경을 가할 때마다 NodeList를 함께 고려해야 하는 의존성이라는 본질을 발견한다. 이는 오픈소스 기여 경험이 있는 개발자라면 흔히 경험을 통해 얻는 좋은 예시인데 이처럼 이론을 실무로 설명할 수 있는 저자의 내공과 경험은 의심할 여지가 없다. 

프로그래밍의 `패러다임`에는 여러 형태가 존재한다. 순차적으로 명령을 수행하는 원시적인 절차지향 프로그래밍에서 부터 객체와 클래스 중심의 객체지향 프로그래밍, 상태 없이 순수 함수 중심을 추구하는 함수형 프로그래밍, 선언적으로 규칙과 조건을 명시하는 논리형 프로그래밍, 그 외에도 데이터 지향 프로그래밍 등 다양한 패러다임이 존재한다. 

반면 지난 20~30년간 국내 IT 시장은 너무 편식한 경향이 없지 않다. `Java 중심의 OOP`에 너무 집중했고 SI 기반이 찍어내기식 돈만 바라보는 업체들의 행태 덕분에 편식은 점차 심해졌고, 건전한 개발자 생태계 발전에 적잖은 걸림돌로 작용했다. 

또한 요즘엔 또 다른 의미의 편식이 존재한다. `프레임워크`에 너무 의존하다보니, 대체로 후배들은 설계적 관점 즉, 멀티패렅다임 프로그래밍 수준의 숲을 보는 능력이 매우 떨어진다.

앞으로 `AI의 물결`이 모든 것을 바꾸는 시대가 다가오는데 프롬프팅 하나만 봐도 알 수 있듯 이제 `질문을 정말 잘해야하는 시대`가 다가왔다. 사실 질문을 잘할 수 있으려면 본질을 파악하는 능력이 중요하다. 

본질을 파악하고 가진 요소들을 얼마나 잘 `오케스트레이션`하여 AI로 하여금 원하는 것을 얼마나 빠르게 얻을 수 있는지에 대한 능력이 중요한 시대가 된 것이다. 

GoF 디자인 패턴 등장배경에서 볼 수 있듯 본 도서는 앞으로 AI와 그 사용자들이 만들어 나갈 변화에 필요한 숨은 진의를 파악할 수 있는 `AI 시대에 필요한 교본`과도 같은 책이라 할 수 있다. 

AI가 발전하며 데이터가 더욱 중요해졌고 이는 프로그래밍의 발전 방향에 `데이터가 상당한 종속성을 행사`하는 계기가 되었다. 개인적으로 이터러블이 프로그래밍 언어론에 지대한 영향력을 행사하는 것은 `데이터와 자료구조`에 기인한다고 본다.

List, Array와 같은 자료구조를 활용하는 한 for문 형식은 피할 수 없게 되었는데 수치형 집합을 GPU가 병렬 연산하는 트렌드까지 만나면서 한 층 더 나아가 `선형대수`의 번창에 이르는 변화를 주도했다. 

유사 군 데이터를 처리하는데 있어 프로그래밍은 next() 구조를 도입할 수 밖에 없었고 연역적으로 프로그래밍만 독립적으로 놓고 보던 초기 모델은 점차 데이터에 종속된 귀납방식으로 변모했다. 이 또한 어디까지나 문제 해결을 위한 당연 수순이다.

`비동기` 또한 패러다임을 바꾼 지대한 요소이다. 웹과 모바일의 등장으로 기다림 없이 다른 일을 할 수 있도록 극도의 `효율성`을 추구하는 과정이 필요한 시대가 되었다. 가장 큰 요인은 `I/O 문제`에서 발생하는 데 프런트엔드 진영이라면 앞서 언급한 UX 부분 백엔드라면 리소스를 제어하는 부분이 이에 해당한다. 

대신 개발자로 하여금 `실행 순서를 제어하는 능력`을 요하는 부작용(?)이 생겼다. 실무적으로는 `가독성이나 안정성` 측면에 빨간불을 켠 셈이다. 모든 것은 트레이드 오프가 발생하니 어쩔 수 없는 문제이다. 

이 책에서 잘 정리하고 있듯 자바스크립트 진영만 봐도 ES6에서의 Promise 도입, 2017년 async-await 채택의 현상은 이런 시대상을 반영한다. 

객체 진영의 `반복자 패턴에 함수형 진영의 일급함수가 결합`하기 시작한 것이다. class 문법을 도입하며 동시에 순회규약 도입했다. 덕분에 `지연평가나 리스트프로세싱`이 가능해졌다. 

메타 프로그래밍에서 한발 더 나아가 멀티패러다임이 대세가 되면서 함수는 다른 호출측 함수의 인자처럼 활용되며(일급함수-고계함수), 코드를 데이터와 로직이 담긴 List로 보는 관점으로 리스트 프로세싱이 탄생했다. 

이 부분에 대한 구체적인 예시는 115p를 참조하면 된다. LISP에 착안하여 map(f, iterator)형식의 `Pipe Operator`를 만들어 보는 과정의 전반을 이해할 수 있다면 그리 어렵지 않은 이야기인데 이는 저자의 통찰과 전달력 덕분임을 강조하고 싶다. 
![Pipe Operator115](https://theorydb.github.io/assets/img/review/review-book-multiparadigm-programming-2.png)  

이 책에 소개되진 않았지만 내가 자주 활용하는 Python 진영의 인기쟁이 Pandas 라이브러리에 apply(), map(), applymap(), agg(), transform(), filter(), pipe() 함수 등이 흔히 활용되는 것도 이런 멀티패러다임의 영향이다. 

책의 전반부(1~4장)은 멀티패러다임이 등장하게 된 `Why 즉, 본질`에 집중한다. 

수학적 원리, 불변성과 순수성, 예측가능성, 병렬처리, 비동기처리, 데이터처리, 쪼개어 연결하는 과정, typeof 키워드로 안전함을 보장하는 타입 추론, promise, 반복자 이터레이터의 변화, 제너레이터에서 yield와 iterator 반환의 결합, for...of 문법과 Symbol.iterator 시그니처의 활용, 커링, 변수같은 일급함수, 일급함수를 호출하는 고차함수(일급함수의 호출측), 필요한 시점에 필요한 만큼만 꺼내쓰는 지연평가, 고차원의 다형성을 제공하는 제네릭, 객체 모델링, 유연성과 확장성, 책임소재, 협업지향, 추상화, 캡슐화, 전개연산자(...), 구조 분해, 상속과 인터페이스의 활용 방법, 비동기 처리 등 정신없는 풍랑을 거치다보면 어느덧 함수형이 무엇인지, 객체지향이 무엇인지 별 의미가 없는 정반합의 완숙한 경지에 이른다. 

후반부는 전반부에서 키운 내공을 바탕으로 현실의 세계를 평정한다. 패턴과 예제 중심으로 문제 해결의 본질을 `어떻게 활용할지`에 대한 저자의 사고방식을 쫓아가다보면 자연스럽게 내공을 운용할 수 있게 된다. 
![동시성핸들링](https://theorydb.github.io/assets/img/review/review-book-multiparadigm-programming-3.png)  

명쾌하게 탄탄하게 쌓인 개념을 바탕으로 자연스럽게 손과 머리로 체화되는 과정이란..이렇게 이론과 실무의 경계를 지우는 저자의 내공과 전달력에 경의를 표하고 싶다.

책이란게 원래 사놓고 안보는 독자가 대다수겠지만 초급자에게는 1장만 해석되어도 프로그래밍의 세계가 달리 보일 것이다. 중급자는 5장만 따라해 봐도 본인의 실무 내공에 큰 변화가 있을것 같다. 

아마도 보이지 않던것이 보이기 시작할텐데 시간, 속도, 시간복잡도, 프로세스, 메모리와 같은 H/W 리소스에 이르는 보`이지 않는 것들이 보이고 신경쓰이기 시작할 것`이다.

적어도 IT 서적 중 이렇게 전달력이 높은 저자를 본적이 없다. 다년 간의 내공과 강의 경험 없이는 이게 가능할까 싶다. 우리나라에도 이런 책이 존재한다는 것이 자랑스러울 정도이다. 왠만한 유관분야 원서보다도 이 책으로 시작하는 것을 추천하고 싶다.

---

* [책소개 - 멀티패러다임 프로그래밍](https://www.yes24.com/product/goods/145367977)
