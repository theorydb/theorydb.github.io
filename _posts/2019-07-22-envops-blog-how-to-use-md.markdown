---
layout: post
title:  "[Jekyll Blog] 마크다운(Markdown) 사용법 및 예제"
subtitle: "마크다운(Markdown)"
categories: envops
tags: envops blog github pages jekyll markdown  
comments: true
---


## 개요
> 지금 당장 필요한 `마크다운(Markdown)` 문법부터 단계적으로 배워봅니다.  
  
- 목차
	- [Markdown이란?](#) 
	- [Markdown 에디터 뭘 쓸까?](#)
	- [Markdown의 문법1(반드시 알아야 하는)](#)
	- [Markdown의 문법2(부가기능)](#)
	- [실전연습](#)
	- [이미지 관리 및 업로드](#)
	- [작성 중 소소한 Tip 그리고 문제 해결방법](#)
  
  
## Markdown이란?  
---
[Markdown](http://kirkstrobeck.github.io/whatismarkdown.com/)은 문서 작성을 지원하는 태그(Tag) 형식의 문법이다. 
> __What is Markdown? (출처 - 위키백과)__  
> 마크다운(markdown)은 일반 텍스트 문서의 양식을 편집하는 문법이다. README 파일이나 온라인 문서, 혹은 일반 텍스트 편집기로 문서 양식을 편집할 때 쓰인다. 마크다운을 이용해 작성된 문서는 쉽게 HTML 등 다른 문서형태로 변환이 가능하다.  

* __익숙한 MSWord나 한글(HWP)로 작성하면 안 되나요?__  
가능하다. 하지만 `WEB에서 글을 쓰고 싶다면` 이 둘은 적합한 도구가 아니다. 세상의 거의 모든 컨텐츠가 WEB 기반으로 생산되고 소비되기 때문에 이 문제는 중요하다. 물론 이런 편집기로도 Save As(다른 이름으로 저장) 기능을 통해 HTML 확장자로 변환 후 WEB에 올릴수도 있지만 소스코드의 양을 보면 경악을 금치 못하게 된다. 더욱이 스타일, 표 등이 온전하게 변환되지 않아 전용 편집기에서 보는 것과 동일한 모양으로 보기 힘들다.

* __WEB문서라면 HTML이나 웹 프로그래밍 언어를 써도 되잖아요.__   
가능하다. 하지만 `생산성(작성 속도 및 편리성)에 큰 차이`가 있다. 더욱이 WEB언어를 모르는 사람이라면 익숙하지 않은 프로그래밍의 문법을 다시 배우고 능숙해지는데 꽤 큰 노력과 긴 시간을 필요로 하게 될 것이다.

* __그 외에 좋은점은 뭔가요?__   
  - 배우기가 정말 `쉽고 직관적`이다.  
  - Text로 저장한 후 `HTML으로의 변환이 가능`하다. 변환을 지원하는 도구나 Eco(생태계)가 매우 많다.  
  - Text로 저장하기 때문에 `Git을 통한 버전관리가 가능`하고, `용량이 적어 보관이 용이`하다.  
  - Python의 주피터노트북, R의 R Markdown 등 다른 기술에의 진입장벽을 낮춰준다.  

* __안 좋은점은?__  
유일하게 안 좋은 점이 하나 있는데 표준이 없다. 핵심 문법을 제외하고는 에디터 도구에 따라 결과물이 약간 달라질 수 있다.    
  
## Markdown 에디터 어떤거 쓸까?  
---
윈도우 메모장으로 써도 된다. 하지만 그따위 것을 쓰려고 이 포스팅을 보시진 않을 것이다.

* __선정기준__
  - Q. 다양한 표현 가능하겠어?  
    논문 수준 수식, 다양한 Icon 이미지, Code Block, UML 다이어그램,.. 등
  - Q. 어디에 저장되니?  
    PC에만 저장되어서 USB에 들고 다녀야 하는건지? 클라우드 개념으로 어디서든 수정 가능한건지?
  - Q. 퍼블리쉬(Publish)도 가능해?  
    Git, 구글드라이브, 블로거, 드랍박스, 워드브레스, 텀블러, 내 PC, 개발서버, .. 등 
  - Q. 얼마면 돼? 얼마나 편리한데? 등
  - 온라인(인터넷)이 차단(비행기, 네트워크 장애, 비용 문제 등)될 때도 대비하자구!

* __추천 에디터__  
  + [Prose.io](https://theorydb.github.io/envops/2019/07/04/envops-blog-posting-prose-io/)      
    - 끝내준다.
    - 언제 어디서나 접속 가능하다. 
    - Git에 접속하여 배포없이 바로 Markdown의 수정이 가능하다.
    - 위 링크를 클릭하여 필자가 작성한 Prose.io 설치 및 사용법을 알아보자.  
  + [StackEdit](https://stackedit.io)  
    - 이 역시 강추한다.
    - 위에 열거한 구글드라이브, Git, 텀블러 전부 저장 및 배포 가능하다.
    - 어느 PC에서 접속해도 동시성이 보장된다. 
    - 예쁜 Icon부터 논문수식까지 거의 모든 마크다운 표현이 가능하다.
  + [MarkdownPad](http://markdownpad.com/)  
    - 위 링크에서 다운로드 가능하다.
    - 클라우드 공유 방식이 아닌 PC에 설치하는 프로그램이다.
    - 기능이 아주 뛰어나다고 할 순 없으나 인터넷이 끊긴 경우 요긴하다.
    - 온라인이 보통 훌륭하지만 가끔 서버가 다운되거나 인터넷이 느린 경우 PC에서 작업하기 때문에 빠르게 사용할 수 있다는 점이 장점이다.
    - 무료버전은 한계가 많다.(특히 편집탭이 4개밖에 열리지 않는다.)

* __그 외의 에디터__   
  + [MacDown(for MAC)](https://macdown.uranusjr.com/)  
  + <https://jbt.github.io/markdown-editor>

일단 초보자라면 위 MarkdownPad 공식 사이트에 접속해서 PC에 설치한 후 다음의 문법을 따라 타이핑해보자. 설치는 아주 쉽다. 그냥 다운로드 버튼을 눌러 PC에 저장 및 실행한 후, Next 버튼만 누르면 금방 깔린다.   

온라인 에디터의 경우 클라우드 환경의 복잡한 부가기능을 배우느라 Markdown 자체에 선택과 집중을 못할수도 있다. 나중에 차차 가입하여 사용하시길 바란다. 
  
  

## Markdown의 반드시 알아야 하는 문법  
---
글을 작성할 때 한번 이상 사용하는 주요 문법들을 간추려 글을 쓰는 순서대로 기술하였다. 처음 접하는 분들은 이 부분만 숙지하고 바로 예제를 작성하신 후, 궁금한 점이 있을 때 [Markdown의 기타 문법](#)으로 넘어가시기 바란다.

---
*  __[1단계] `헤더(Header)` : 제목, 문단별 제목을 쓰고 싶을 때__  
글의 구조(개요) 및 큰 틀을 잡을 때 사용한다.  
  
```
# 제목 1단계
## 제목 2단계  
### 제목 3단계
#### 제목 4단계
##### 제목 5단계
###### 제목 6단계 
```
  
# 제목 1단계
## 제목 2단계  
### 제목 3단계
#### 제목 4단계
##### 제목 5단계
###### 제목 6단계 
  
---
*  __[2단계] `수평선` : 내용을 구분하고 싶을 때__      
  
```
---
```
  
---
  
---
*  __[3단계] `엔터키(줄바꿈, 개행)` : 라인을 바꾸고 싶을 때__  
  
```
띄어쓰기 2번을 입력하면.(from)  (to)<!-- from과 to 사이에 스페이스 2번 입력-->
줄이 바뀐다.
```
  
띄어쓰기 2번을 입력하면.(from)  (to)
줄이 바뀐다.
    
---
*  __[4단계] `목록(List)` : 요소를 나열할 때__  
  
```
1. 순서있음  
  1. 첫번째
  1. 두번째
  1. 세번째
1. 순서목록2
1. 순서목록3
  
+ 순서없음
    - 홍길동
      * 중대장
        + 프로실망러
```
  
1. 순서있음  
  1. 첫번째
  1. 두번째
  1. 세번째
1. 순서목록2
1. 순서목록3
  
+ 순서없음
    - 홍길동
      * 중대장
        + 프로실망러
  
---
*  __[5단계] `강조` : 문장 내 강조하고 싶은 단어를 눈에 띄게__  
  
```
__볼드(진하게)__  
_이탤릭체(기울여서)_    
~~취소선~~  
<u>밑줄</u>  
```
  
__볼드(진하게)__  
_이탤릭체(기울여서)_    
~~취소선~~  
<u>밑줄</u>  
  

---
*  __[6단계] `인용구` : 인용할 경우 또는 분위기 전환시에도 사용(중복 형태 가능)__  
  
```
> 위키백과?
>> 중대장 드립 검색
>>> "오늘 중대장은 너희에게 실망했다"
```
  
> 위키백과?
>> 중대장 드립 검색
>>> "오늘 중대장은 너희에게 실망했다"  
  
---
*  __[7단계] `링크(Link)` : 클릭하면 다른 페이지, 다른 부분으로 이동 가능__  
  
```
유형1(`설명어`를 클릭하면 URL로 이동) : [TheoryDB 블로그](https://theorydb.github.io "마우스를 올려놓으면 말풍선이 나옵니다.")  
유형2(URL 보여주고 `자동연결`) : <https://theorydb.github.io>  
유형3(동일 파일 내 `문단 이동`) : [동일파일 내 문단 이동](#markdown의-반드시-알아야-하는-문법)  
```
  
유형1(`설명어`를 클릭하면 URL로 이동) : [TheoryDB 블로그](https://theorydb.github.io "마우스를 올려놓으면 말풍선이 나옵니다.")  
유형2(URL 보여주고 `자동연결`) : <https://theorydb.github.io>  
유형3(동일 파일 내 `문단 이동`) : [동일파일 내 문단 이동](#markdown의-반드시-알아야-하는-문법)  
>__유형3 문단 매칭방법__ :   
>제목(header)를 복사 붙여넣기 후,  
>1)`특수문자`제거  
>2)스페이스를 갯수만큼 `-`로 변경  
>3) 대문자->`소문자`로 변경   
>예) "#Markdown!  장점" -> "#markdown--장점"
  
유형4(상대 경로로 서버 내 파일이동) 기능은 쓸 일이 거의 없어 제외한다.  
  
---
*  __[8단계] `이미지(Image)` : 이미지 보여주기__  
  
```
유형1(`이미지` 삽입) :  
![이미지](https://theorydb.github.io/assets/img/think/2019-06-25-think-future-ai-1.png "인공지능")
  
유형2(`사이즈를 조절`하고 싶은 경우 HTML 태그로 처리) :   
<img src="https://theorydb.github.io/assets/img/think/2019-06-25-think-future-ai-1.png" width="300" height="200"> 

유형3(이미지 삽입 후, `링크 걸기`)
[![이미지](https://theorydb.github.io/assets/img/think/2019-06-25-think-future-ai-1.png)](https://theorydb.github.io/think/2019/06/25/think-future-ai/)  
```
  
유형1(`이미지` 삽입) :  
![이미지](https://theorydb.github.io/assets/img/think/2019-06-25-think-future-ai-1.png "인공지능")
  
유형2(`사이즈를 조절`하고 싶은 경우 HTML 태그로 처리) :   
<img src="https://theorydb.github.io/assets/img/think/2019-06-25-think-future-ai-1.png" width="300" height="200"> 

유형3(이미지 삽입 후, `링크 걸기`)
[![이미지](https://theorydb.github.io/assets/img/think/2019-06-25-think-future-ai-1.png)](https://theorydb.github.io/think/2019/06/25/think-future-ai/)
  
이상 글을 쓸 때 매번 사용하는 Markdown의 문법을 알아보았다. 

## Markdown의 유용한 부가기능  
---
이 Chapter에서 배울 것들은 위의 기능보다는 사용 빈도가 낮지만 굉장히 고차원 적인 표현을 가능하게 해주는 매우 유용한 문법들이다. 필요할 때마다 참고하여 익히면 큰 도움이 될 것이다.  

---
*  __[1단계] `표(Table)` : 표 그리기__  
  
```
|                  | 수학                        | 평가              |  
|:--- | ---: | :---: |  
| 철수             | 90            | 참잘했어요. |  
| 영희           | 50            | 분발하세요. |
```
  
|                  | 수학                        | 평가              |  
|:--- | ---: | :---: |  
| 철수             | 90            | 참잘했어요. |  
| 영희           | 50            | 분발하세요. |
  
> * 라인 단위로 생각하면서 구분자(`|`)로 열을 구분해주면 위와 같이 대충 그려도 알아서 예쁘게 완성된다.  
> * 헤더(머리글)를 분리하고 싶은 경우, 위 예제와 같이 2번째 라인에 `---`을 사용하면 된다.
> * 정렬이 필요한 경우, 콜론(`:`) 기호를 구분선(`---`) 왼쪽, 오른쪽, 양쪽에 배치한다.      
   
---
*  __[2단계] `수식` : 수학, 논문분석 등에 사용__  
  
```
$$f(x)= if x < x_{min} : (x/x_{min})^a$$  
$$otherwise : 0$$  
$$P(w)=U(x/2)(7/5)/Z$$  
$$p_{\theta}(x) = \int p_{\theta}(2z)p_{\theta}(y\mid k)dz$$  
$$x = argmax_k((x_t-x_u+x_v)^T*x_m)/(||x_b-x_k+x_l||)$$  
```

$$f(x)= if x < x_{min} : (x/x_{min})^a$$  
$$otherwise : 0$$  
$$P(w)=U(x/2)(7/5)/Z$$  
$$p_{\theta}(x) = \int p_{\theta}(2z)p_{\theta}(y\mid k)dz$$  
$$x = argmax_k((x_t-x_u+x_v)^T*x_m)/(||x_b-x_k+x_l||)$$  
  
> * 필자가 사용하는 지킬 테마는 별도 설정없이 위 예제와 같이 자유롭게 사용할 수 있다.   
> * 수식 표현에 제한이 있는 경우, `MathJax` Javascript를 include하여 사용한다.
> ```
> <script type="text/javascript" 
> src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS_HTML">
> </script>
> ```
> * 표현형식은 [Latex](https://en.wikibooks.org/wiki/LaTeX/Mathematics) 표기법과 동일하다.
  
---
*  __[3단계] `UML 다이어그램` : 순서도, 흐름도 등을 표현할 때 유용하다.__  
  
```flow
st=>start: Start
e=>end
op=>operation: My Operation
cond=>condition: Yes or No?

st->op->cond
cond(yes)->e
cond(no)->op
```

st=>start: Start
e=>end
op=>operation: My Operation
cond=>condition: Yes or No?

st->op->cond
cond(yes)->e
cond(no)->op
  
> * 필자가 사용하는 지킬 테마는 별도 설정없이 위 예제와 같이 자유롭게 사용할 수 있다.   
> * 수식 표현에 제한이 있는 경우, `MathJax` Javascript를 include하여 사용한다.
> ```
> <script type="text/javascript" 
> src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS_HTML">
> </script>
> ```
> * 표현형식은 [Latex](https://en.wikibooks.org/wiki/LaTeX/Mathematics) 표기법과 동일하다.
  


## 실전연습  
---
이제 Markdown의 거의 모든 문법을 알아보았다. `백문이 불여일타`이므로 반드시 직접 마크다운 문서를 작성해보자.

1. 연습문제1 : 위의 문법 실습을 그대로 타이핑하는 문서 만들기  
2. 연습문제2 : 이 포스팅과 동일한 문서 만들기  
최대한 정답 없이 위에서 배운 문법을 이용하여 본 포스팅과 동일하게 만들어보자.  
성공한다면 앞으로 그 어떤 마크다운 문서 작성도 두렵지 않을 것이다.   

> __`연습문제2 정답`__   
> 1. [필자의 블로그 Github](https://github.com/theorydb/theorydb.github.io)에 접속  
> 2. 우측의 `Clone or download`(녹색버튼) 클릭  
> 3. `/theorydb.github.io-master/_posts/` 폴더 이동  
> 4. `2019-07-22-envops-blog-how-to-use-md.markdown`를 확인 






이로써 Tipue Search 오픈소스를 활용하여 블로그에 멋진 검색 기능을 구축하였다. 다음 기능으로는 Jekyll 기반 블로그의 `Disqus` 댓글 기능 추가에 대하여 포스팅 할 예정임을 미리알려드린다.  


> Jekyll 기반의 깃헙 페이지 블로그 구축 포스팅은 계속될 예정입니다. 처음 구축하는 방법부터 올리려고 했는데 시간 부족으로 계속 미루고 있네요^^; 포스팅 순서가 어긋나더라도 차후 개인적으로 구현하려는 목표가 모두 완성되는대로 `구축을 위한 설계도` 개념의 포스팅에서 통합 정리 및 링크부여를 통해 가급적 편하게 보시며 구축하실 수 있도록 노력하겠습니다. 읽어주셔서 감사합니다. 