---
layout: post
title:  "[Jekyll Blog] Tipue Search 플러그인으로 검색기능 만들기"
subtitle:   "Tipue Search 플러그인으로 검색기능 만들기"
categories: envops
tags: envops blog jekyll site search tipue
comments: true
---


## 개요
> `Tipue Search`를 활용하여, 블로그 포스트를 검색 기능을 만들어봅니다.  
  
- 목차
	- [Tipue Search란?](#R이란-무엇인가) 
	- [Tipue Search 설치(Window PC 버전)](#R설치Window-PC-버전)
	- [Tipue Search 환경설정](#R-Studio-환경설정)
	- [최적화 적용을 위한 디테일 마무리](#R-Studio-환경설정)
  
  
## Tipue Search란?
---
블로그를 운영하다보니 검색 기능이 필요해졌다. 시간이 지날수록 포스트 개수가 늘어나게 되는 것은 당연한 일이기 때문이다. 기술 블로그는 다른 이들과 기술을 공유하는 목적도 있지만, 개인적으로 효율적인 기억 관리를 위해 활용하기도 하는데 정작 본인이 필요할 때 포스트가 어디있는지 기억이 나지 않아 한참 해맨다면 무슨 소용이 있을까? 검색기능을 만들어보기로 결심하였다!
  
* __검색 기능을 뭘로 만들지?__  
우리나라 개발 환경의 고질적인 병폐일까? 검색 기능을 구현하기 위해 가장 먼저 떠오른 것이 슬프게도 DB였다. Oracle, Mysql, Pgsql,... 어떤것을 설치해서 운영할까? 클라우드를 이용해야 하나?

* __아~ 맞다. 이 블로그는 Jekyll로 만들었지!__  
당연히 데이터가 DB에 있어야 DB 검색 기능을 활용할 수 있다. 정적 컴파일러 Jekyll로 제작되는 이 깃헙 페이지에 DB는 당연히 고려대상이 아니다. 그렇다면 Front-End 기술의 핵심 언어인 JavaScript를 이용해서 만들어야 하나 고민하던 중 sitemap.xml, feed.xml이 생각났다. XML구조로 Data가 모여있으니 XML 파싱을 이용하여 검색기능을 구현하자고 맘먹던 중 귀차니즘이 밀려왔다. 난 Front-End 기술을 공유하기 위해 블로그를 만든것이 아닌데.. 데이터 사이언스 기술 공유가 목적인데 이걸 굳이 만들어야 하나?^^;   

* __Jekyll도 있는데 Front-End 검색기능이 없겠어?__  
위대한 구글신께 물어보니 역시나 훌륭한 site search plugin을 발견하게 되었다. 그 이름하여 [`Tipue Search`](http://www.tipue.com/search/)!! 대표사이트를 들어가보니 대문에 `제이쿼리를 활용하여 만들었고 무료이며 빠르다`라고 자랑한다. (실제로도 그렇다.) 실제 구현된 기능은 본 블로그 좌측메뉴 About 하단의 검색창을 사용해보시기 바란다.   
  

## Tipue Search 설치(Window PC 버전)
---
본 블로그에 구현된 데모 기능이 맘에 드셨다면 바로 설치를 시작해보자.  

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
   

## Tipue Search 환경설정  
---
Jekyll 테마에 따라 설정이 약간 다를 수 있다. 본 블로그의 테마는 `Clean Blog`로, 동일한 테마를 사용하시는 경우 그대로 적용하면 된다. (운영중인 테마가 달라 적용에 어려움이 있는 경우 맨 하단의 Disqus에 댓글을 남겨주시면 아는 범위내에서 최대한 설명해 드리겠습니다.)   

1. `본인의 깃헙 블로그 최상위 디렉토리/_config.yml`(예:C:\githubPages\theorydb.github.io\_config.yml) 파일을 편집기로 열어 맨 아래에 다음의 코드를 추가한다.  
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
  
![그림8](https://theorydb.github.io/assets/img/dev/r/2019-05-01-dev-r-rinstall-8.png)   
2. Free 버전 `DOWNLOAD` 버튼을 클릭(그 외 버전은 사용제품으로 비용을 지불해야 한다.)  
![그림9](https://theorydb.github.io/assets/img/dev/r/2019-05-01-dev-r-rinstall-9.png)
3. `RStudio 1.2.1355-Windows 7+ (64bit)` 버튼을 클릭(버전은 계속 변경됨)  
![그림10](https://theorydb.github.io/assets/img/dev/r/2019-05-01-dev-r-rinstall-10.png)
4. 다운로드 완료 후, `RStudio-1.2.1335.exe`파일을 더블 클릭하여 설치(디폴트로 `Next`만 누르면 설치됨)  
![그림11](https://theorydb.github.io/assets/img/dev/r/2019-05-01-dev-r-rinstall-11.png)
5. 설치가 완료되면 윈도우 시작버튼을 눌러 하단 검색창에 `rstudio`를 입력 후, 검색된 프로그램을 클릭하여 실행한다.   
![그림18](https://theorydb.github.io/assets/img/dev/r/2019-05-01-dev-r-rinstall-18.png)
7. 정상적으로 설치되었는지 확인하기 위해, `Console`탭에서 아래와 같이 소스코드를 입력  

8. 그림과 같이 입력한 문자열이 그대로 나오면 정상적으로 설치가 완료된 것이다. 
![그림12](https://theorydb.github.io/assets/img/dev/r/2019-05-01-dev-r-rinstall-12.png)

## R Studio 환경설정   
---
R Studio을 보다 편리하게 사용하기 위한 몇가지 Tip을 소개한다.

1. 편집기 `인코딩` 방식 변경
   - 그림과 같이 `Tools> Global Options > Code > Saving > Change버튼 > UTF-8선택` 순서로 클릭)  
   ![그림13](https://theorydb.github.io/assets/img/dev/r/2019-05-01-dev-r-rinstall-13.png)
   - 설정을 변경하면 자동으로 R를 껐다 켤것인지 묻는데 `Yes`를 눌러준다.
   ![그림14](https://theorydb.github.io/assets/img/dev/r/2019-05-01-dev-r-rinstall-14.png)

2. 편집기 코딩 폰트 등 스타일 변경 : `Tools> Global Options > Appearance > 폰트, 사이즈, 테마 등 선택`  
   ![그림17](https://theorydb.github.io/assets/img/dev/r/2019-05-01-dev-r-rinstall-17.png)

3. 화면 레이아웃 변경 : `Tools> Global Options > Pane Layout > 화면 위치별 원하는 레이아웃 선택`  
   ![그림16](https://theorydb.github.io/assets/img/dev/r/2019-05-01-dev-r-rinstall-16.png)

4. 자동줄바꿈 기능 해제 : `Tools> Global Options > Code > Editing > Soft-wrap R source files 체크해제`  
   ![그림15](https://theorydb.github.io/assets/img/dev/r/2019-05-01-dev-r-rinstall-15.png)  
   ※ 참고로 코드 실행 시 `Ctrl+Enter`키를 누르면 멀티라인 실행이 가능하다.


이로써 R을 사용하기 위한 사전작업이 모두 완료되었다. 다음 포스트에는 간단한 R의 사용방법에 대하여 설명하겠다.

