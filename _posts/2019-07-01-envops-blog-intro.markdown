---
layout: post
title:  "[Jekyll Blog] (개요) 블로그를 만들어 볼까?"
subtitle:   "블로그 만들기 개요"
categories: envops
tags: envops blog intro   
comments: true
---


## 개요
> 블로그를 만들 때 고려할 사항과 만드는 방법 개요에 대하여 알려드립니다.  
  
- 목차
	- [내가 블로그를 만든 이유](#) 
	- [다른 사람이 블로그를 만든 이유](#)
	- [어떤 블로그가 완성되어 있을지 상상해보세요!(체크리스트)](#)
	- [(Where) 어디에 만들것인가? 어떤 플랫폼과 기술을 활용할까?](#)
	- [그래서 당신은 어떤 플랫폼과 기술로 이 블로그를 만들었나요?](#)
	- [(How-To) 어떻게 만들면 되나요? 글은 어떻게 쓰죠?](#)
	- [그 외 다른 플랫폼 및 기술을 위한 참고사이트](#)
  
  
## 내가 블로그를 만든 이유  
---
지금 이 포스트를 읽고 계신 여러분은 분명 `블로그나 만들어 볼까?`라는 생각을 한번 이상은 해 보신 분일 것이다. 똑같은 질문에 대한 필자의 대답과 고민의 흔적을 아래에 포스팅 하였으니 이 글이 시행착오를 줄이는데 보탬이 되었으면 한다. 
 
* __글을 너무쓰고 싶은 순간에 종이가 없다면, 길 위의 바위에 정으로 글을 새길 욕망이 있는가?__  
"글쓴이에게 이 정도 열망은 있어야 명작이 탄생할 수 있는 것이다." 대학시절 한 은사님께서 하신 말씀이다. 비록 이 정도의 열망은 없지만, 1만시간의 법칙 때문일까? 요즘들어 부쩍 배우고 익혀온 기술들을 정리하고 싶어 손과 머리가 근질거릴 때가 많았다. 더불어 요즘 큰 관심을 가지고 있는 데이터 사이언스 분야에 대한 지식을 정리할 곳이 간절했다. 비슷한 느낌이 든다면 여러분도 블로그를 운영할 때가 온 것이 아닐까? 

* __Entity보다는 Relation을 좋아합니다.__
개인적인 사고방식의 취향이라고 해야할까? 학창 시절부터 단편 지식을 완벽하게 숙지 못했더라고 그 지식이 다른 지식과 어떻게 연결되어 큰 숲을 이루는지에 관심이 많았다. 새로운 것을 배우면 이미 머리속의 엄청난 거미줄 어느 모퉁이에 매달아야 하는지 고민을 하게된다. 이런 사고 방식에서 TAG 기반으로 엮은 나만의 지식 데이터를 쌓기에 블로그만한 것이 없을 것이라 생각했다. 

* __프로그래머라면 Jekyll Github Pages 정도의 블로그는 되어야지!__  
이런 허세 때문에 Jekyll 기반의 블로그를 운영하는 것은 아니지만 직업적으로는 꽤 의미있는 말이다. 어느 분야에 종사하시는 분일지라도 `제너럴리스트 vs 스페셜리스트`사이의 고민은 항상 있으실 것이다. 둘 다 정통한 T자형 인재가 정답이겠지만 시간, 재능, 운의 한계로 쉽지 않은 길이다.   
필자는 프로그래머로 Front-end 보다는 Back-end 기술을 주로 다루며, 서비스보다는 공공 위주 프로젝트를 다루기 때문에 트렌드에 노출될 기회가 적다. 적어도 내 블로그만큼은 자주 다루기 힘든 Front-end 기술, 트렌드에 뒤떨어지지 않는 기술, 다루고 싶은 기술을 활용하여 지적인 욕구도 충족시키고 제너럴리스트로서의 요건도 갖추고 싶었던 것이 블로그를 운영하는 또 하나의 이유라고 할 수 있겠다.

* __여러분의 두뇌는 CPU, Memory, 하드디스크 어느쪽에 가까운가요?__  
사고력을 의미하는 CPU, 메타인지를 의미하는 Memory(~~필자가 멋대로 정한 비유다.~~), 기억력을 의미하는 HardDisk, 아니면 습득이 빠르고 생각을 전달하는 능력이 탁월한 I/O? 필자는 두뇌를 주로 CPU와 Memory의 기능에 가깝게 활용한다. 때문에 자연스럽게 타 영역에 대한 보완이 필요했는데 특히 기억력을 보완하기 위한 수단으로 블로그를 운영한다.

* __진리탐구의 연장선 상에 연결되고 싶네요!__  
거창하게 써서 부끄럽다. 비록 개똥철학과 지식일지는 모르겠지만 내 아들에게 그간 노력하며 얻은 지식을 조금이라도 쉽고 빠르게 전달하고 싶은 계기가 컸다. 조금 더 욕심을 부리자면 세상 모든 사람들의 시간을 조금이라도 줄여주는데 기여를 하고 싶다.  


## 다른 사람이 블로그를 만든 이유  
---
그렇다면 다른 사람들은 왜 블로그를 운영하는 것일까? 이 포스팅을 읽는 분들께는 이 질문이 더 중요할지도 모르겠다. 조사한 바 크고 작은 이유가 너무도 많았다.

* 구글 애드센스를 장착하여 광고 수익을 내기 위해서
* 사업상 마케팅 수단이 필요하여
* 1인기업, 파워블로그 등의 활동으로 수익 창출을 위하여(유튜버와 유사)
* 취미가 글쓰기이거나 쓰는 동안 생각이 정리되며 스트레스가 풀려서 
* 많은 이들과 지식, 노하우를 공유하고 싶어서 
* 배운 지식을 정리하며 메타적 사고를 넓히고자
* 취업, 경력관리, 이직에 도움이 되어서 
* PC에 쌓여가는 지식을 정리하고, 연결하고, 온라인에 연결하여 접근성을 확보하기 위해서 
* SNS 할성화 및 온오프 모임을 위하여
* 육아, 가정, 사람을 위해 또는 지식의 공유를 위해 
* Markdown을 써보고 싶어서, 내용에 방해를 받고싶지 않아서
* 다른 사람의 정보를 모아놓기 위해서, 즐겨찾기 용도로 
* 외로워서, 관심이 필요해서, 똑똑해보여, 주위에서 너무 많이들 운영하길래, 심심해서
  
그 외 여러가지 목적이 있지만 어떤 이유든 블로그에 글을 쓰기 위한 충분한 동기가 되지 않을까? 
  
## 어떤 블로그가 완성되어있을지 상상해보세요!(체크리스트)  
---
블로그를 만들기로 마음 먹었다면, 내 블로그가 미래에 어떤 모습으로 운영되고 있을지 생각해볼 필요가 있다.

* __(Why) 왜 써야할까요?__  
이 질문이 가장 중요하지만, 위에서 이미 답이 나왔기에 블로그를 쓰기로 결정했을 것이다.

* __(What) 뭘 써야할까요?__  
주로 다루게 될 주제가 무엇인지 생각해보는 것이 좋다. 분야는 너무나도 다양하다.  
  - 일기장, 일상, 전원생활, 철학, 소설, ...
  - 리뷰, 육아, 교육, 주식, 자기계발, ... 
  - 게임, 취미, 여행, 요리, 건축, ...
  - 역사, 문화, 정치, 종교, 사회, 과학, 예술, ...등    
어느 정도 범위를 좁혀놔야 글쓰기의 생활화에 부담이 되지 않아 가볍게 출발할 수 있는 지구력을 갖게되고, 블로그 플랫폼 및 Tech 선정에 도움이 된다. 

* __(Who) 누가 읽을까요?__
~~아무도 없을지도 모른다.ㅎㅎㅎ~~ 하지만 깊게 생각해 볼 문제다. 포스팅하는 문체, 전개방식을 선택하는 계기가 되고 역시 플랫폼 선정 시 여러번 삭제했다 만드는 등의 시행착오를 줄이게 된다. 더불어 글의 분량, 수준(난이도)을 결정하는데 도움이 된다.

* __(When) 언제 써야 할까요? 계속 쓸 수는 있을까요?__
귀중한 시간을 들여 블로그를 제작한 의미가 퇴색하지 않도록 꾸준히 글을 쓰는 일상 습관이 중요하다. 시간과 공간적으로 글쓰기에 문제는 없을지 대비해보고 계속 운영할 수 있게하는 원동력이 무엇일지 다시금 `Why`를 되새기면서 스스로의 동기부여가 중요하다. 
  
여기까지는 생각을 정리해보는 것만으로 충분했다. 이제부터는 직접 블로그를 개설하는 방법에 대하여 기술적으로 다루어보겠다.
  

## (Where) 어디에 만들것인가? 어떤 플랫폼과 기술을 활용할까?

1. __블로그를 만들 수 있다면 돈을 써도 상관없어요!...__  
돈이 없다면 이 파트는 건너뛰셔도 무방하다. 돈이 있다면 웹호스팅에 관하여 생각해봐야한다.

2. __글쓰는 것만 집중하고 싶고, 약간의 기능만 있으면 됩니다!__

3. __홈페이지처럼 내 마음, 내 취향대로 만들고, 바꾸고, 꾸미고 싶어요!__

4. __데이터베이스로 평생 내 자료를 소장하고, 에디팅하고 싶고, 분석도 하고 싶네요!__

사이트비교


## 그래서 당신은 어떤 플랫폼과 기술로 이 블로그를 만들었나요?

* Jekyll + Git 을 선택한 이유
  - ㅁ
 

## (How-To) 어떻게 만들면 되나요? 글은 어떻게 쓰죠? 
간단하다. 아래의 순서대로 링크를 클릭하시며 포스팅을 참고하여 만들면 된다. 진행 단계별로 아직 링크가 걸리지 않은 경우 조만간 포스팅할 예정이다.
 
* 기본 블로그 구축  
  1. 블로그 테마 선정 및 디폴트 부가기능 활용
  2. Github Pages 및 Jekyll 설치
  3. 개인의 취향에 맞도록 디자인 및 환경설정 변경
  4. 파비콘 만들기
  
* 블로그 기능 확장  
  1. 검색기능 추가
  1. 블로그 댓글기능 추가
  2. 구글 애널리틱스로 방문자 유입 분석
  3. 구글 검색엔진 등록을 유리하게
  4. 구글 애드센스를 장착하여 용돈벌기
  5. 편리한 운영을 위한 기타 설정 및 오류 발생시 대처방법

* 편하게 글쓰자  
  1. Git 활용법
  2. Markdown 작성 방법
  3. Prose.io를 이용하여 Markdown을 온라인에서 작성하고 Git없이 배포하기 
  4. 이미지 캡션 활용


## 그 외 다른 플랫폼 및 기술을 위한 참고사이트 

위대한 구글신께 물어보니 역시나 훌륭한 site search plugin을 발견하게 되었다. 그 이름하여 [`Tipue Search`](http://www.tipue.com/search/)! 메인 페이지를 들어가보니 대문에 `제이쿼리를 활용하여 만들었고 무료이며 빠르다`라고 자랑하고 있다. (실제로 자랑 할 만 하다.) 쓸만한지 테스트가 필요하시면 본 블로그 좌측메뉴 About 밑에 붙어있는 검색창을 사용해보시기 바란다.   
  

## Disqus 회원가입  
---
필자의 블로그에 구현된 기능이 맘에 드셨다면 바로 설치를 시작해보자.  

1. Github Repository 접속 : [`https://github.com/jekylltools/jekyll-tipue-search`](https://github.com/jekylltools/jekyll-tipue-search)  
![그림1](https://theorydb.github.io/assets/img/envops/2019-07-03-envops-site-search-1.jpg)  
2. `Clone or download` 를 클릭하여, `jekyll-tipue-search-master.zip` 파일을 다운받아 압축을 푼다.    
3. 압축을 풀면 나오는 `search.html`파일을 본인의 깃헙 블로그 최상위 디렉토리(예: C:\githubPages\theorydb.github.io)에 복사한다.
![그림2](https://theorydb.github.io/assets/img/envops/2019-07-03-envops-site-search-2.jpg)    
![그림3](https://theorydb.github.io/assets/img/envops/2019-07-03-envops-site-search-3.jpg)    
4. `압축을 푼 폴더/assets/`안에 있는 `tipuesearch` 폴더를 본인의 깃헙 블로그 `최상위 디렉토리/assets/`(예: C:\githubPages\theorydb.github.io\assets\tipuesearch)아래에 복사한다.
![그림4](https://theorydb.github.io/assets/img/envops/2019-07-03-envops-site-search-4.jpg)    

이것으로 설치는 끝났다. 참 쉽죠~?  
이제 환경설정을 통해 블로그에 적용해 보자.
   

## Disqus 설치  
---
Jekyll 테마에 따라 설정이 약간 다를 수 있다. 본 블로그의 테마는 `Clean Blog`로, 동일한 테마를 사용하시는 경우 그대로 적용하면 된다. (운영중인 테마가 달라 적용에 어려움이 있는 경우 맨 하단의 Disqus에 댓글을 남겨주시면 아는 범위내에서 최대한 설명해 드리겠습니다.)   

1. `본인의 깃헙 블로그 최상위 디렉토리/_config.yml` (예:C:\githubPages\theorydb.github.io\_config.yml) 파일을 열어 맨 아래에 다음의 코드를 추가한다.
	```yml
	tipue_search:
		include:
			pages: false
			collections: []
		exclude:
			files: [search.html, index.html, tags.html]
			categories: []
			tags: []
	```
![그림5](https://theorydb.github.io/assets/img/envops/2019-07-03-envops-site-search-5.jpg)     
>* include 부분의 `pages: false`의 설정은 pages 레이아웃에 해당하는 일반 html페이지는 검색하지 않겠다는 것을 의미한다.(포스트 내용 검색에 집중하기 위함) 
>* exclude 부분의 `search.html, index.html, tags.html` 페이지는 검색에서 제외하겠다는 것을 의미한다.  

1. `본인의 깃헙 블로그 최상위 디렉토리/_includes/head.html` (예: C:\githubPages\theorydb.github.io\_includes\head.html) 파일을 열어 `META`영역 제일하단, `LINKS`영역 바로 위의 위치에 다음의 코드를 추가한다.  
	```javascript
	<!-- tipuesearch -->
	<link rel="stylesheet" href="/assets/tipuesearch/css/tipuesearch.css">
	<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
	<script src="/assets/tipuesearch/tipuesearch_content.js"></script>
	<script src="/assets/tipuesearch/tipuesearch_set.js"></script>
	<script src="/assets/tipuesearch/tipuesearch.min.js"></script>
	```
![그림6](https://theorydb.github.io/assets/img/envops/2019-07-03-envops-site-search-6.jpg)  
  
1. `본인의 깃헙 블로그 최상위 디렉토리/search.html` (예: C:\githubPages\theorydb.github.io\search.html) 파일을 열어 아래 그림과 같이 설정한다.  
![그림7](https://theorydb.github.io/assets/img/envops/2019-07-03-envops-site-search-7.jpg)  
> * `layout : page` 부분은 포스팅이 담기는 레이아웃 명칭이다.(테마에 따라 다를 수 있음) 
> * `permalink: /search/` 부분은 다음 단계에서 설정할 검색어 및 버튼 Element의 form 태그 내 action 속성과 일치시켜야 한다.
> * `'wholeWords' : false` 속성은 한글 검색을 가능하게 하는 옵션이다.
> * `'showTime' : false` 속성은 검색이 완료되기 까지 소요된 시간을 표시하는 옵션이다.
> * `'minimumLength' : 1` 속성은 최소 검색 글자수에 대한 설정으로 필자는 한단어 이상이면 검색가능하게 설정하였다.  
> * 그 외의 옵션은 Tipue 메인홈페이지 [`Tipue Search`](http://www.tipue.com/search/)에 접속하여 `Options in the .tipuesearch() method`에서 상세하게 확인할 수 있다. 
  
1. 마지막으로 `본인의 깃헙 블로그 최상위 디렉토리/_includes/sidebar.html` (예: C:\githubPages\theorydb.github.io\_includes\sidebar.html) 파일을 열어 아래 그림과 같이 설정한다.  
> [주의사항]
> `sidebar.html` 페이지를 수정하는 이유는 필자가 검색창을 붙이길 원하는 위치의 페이지가 sidebar.html이기 때문입니다. 
> 본인의 블로그에 검색창을 붙일 위치를 정한 후 해당 파일 및 파일 내 위치를 정한 후 해당 부분을 수정해야합니다.  

	```html
    <form action="/search">
      <div class="tipue_search_left">
        <img src="{{ "/assets/tipuesearch/search.png" | relative_url }}" class="tipue_search_icon">
      </div>
      <div class="tipue_search_right">
        <input type="text" name="q" id="tipue_search_input" pattern=".{1,}" title="At least 1 characters" required></div>
      <div style="clear: both;"></div>
    </form>
	```  
![그림8](https://theorydb.github.io/assets/img/envops/2019-07-03-envops-site-search-8.jpg)  
> * `action="/search"` 설정은 위의 search.html 파일의 permalink 속성과 일치시킨것이다.
> * `pattern=".{1,}"` 속성은 검색어가 1글자 이상이면 검색을 허용한다는 의미로 활용하는 정규표현식 설정이다. 
> * `title="At least 1 characters"` 설정은 위의 pattern을 지키지 않은 채 검색을 시도할 경우 나타나는 알림메시지 문구이다.
  
1. 설치가 마무리 되었으므로 아래 그림과 같이 검색이 잘 동작하는지 확인한다.
![그림9](https://theorydb.github.io/assets/img/envops/2019-07-03-envops-site-search-9.jpg)   
   
## 디테일 마무리 및 추가기능  
---
Tipue Search의 디폴트 기능만 설치된 상태이므로 필자는 블로그에 보다 친화적으로 어울릴 수 있도록 기능을 수정해보았다. 이번 단계는 귀차니즘 가동 시 건너뛰셔도 무방하다. 

1. `검색 입력창` 사이즈 조정을 위해 `C:\githubPages\theorydb.github.io\assets\tipuesearch\css\tipuesearch.css`의 CSS 속성을 변경하였다.  
	```css
	#tipue_search_input
	{
	     color: #333;
	     max-width: 150px;
	     max-height: 20px;
		padding: 17px;
		border: 2px solid #626591;
		border-radius: 0;
		-moz-appearance: none;
		-webkit-appearance: none;
	     box-shadow: none; 
		outline: 0;
		margin: 0;
	}
	```

1. `검색버튼(돋보기모양)`이 좌측 메뉴의 배경색에 가려져 잘 보이지 않아 색상을 조절하였고, 본 테마의 img 태그 CSS 속성이 검색창 모양을 삐뚫어져 보이게 만들어 해당 태그의 CSS속성을 상속받아 사이즈를 수정하였다. 마찬가지로 `C:\githubPages\theorydb.github.io\assets\tipuesearch\css\tipuesearch.css` 파일에서 아래와 같이 CSS 속성을 변경하였다.  
	```css
	.tipue_search_icon
	{
	     width: 19px;
	     height: 19px;
	     margin-bottom: 0rem;
	     background-color: #626591;
	}
	.tipue_search_left
	{
	     float: left;
	     padding: 10px 5px 0 0;
	     color: #e3e3e3;
	     max-height: 20px;
	}
	```

이로써 Tipue Search 오픈소스를 활용하여 블로그에 멋진 검색 기능을 구축하였다. 다음 기능으로는 Jekyll 기반 블로그의 `Disqus` 댓글 기능 추가에 대하여 포스팅 할 예정임을 미리알려드린다.  


> Jekyll 기반의 깃헙 페이지 블로그 구축 포스팅은 계속될 예정입니다. 처음 구축하는 방법부터 올리려고 했는데 시간 부족으로 계속 미루고 있네요^^; 포스팅 순서가 어긋나더라도 차후 개인적으로 구현하려는 목표가 모두 완성되는대로 `구축을 위한 설계도` 개념의 포스팅에서 통합 정리 및 링크부여를 통해 가급적 편하게 보시며 구축하실 수 있도록 노력하겠습니다. 읽어주셔서 감사합니다. 