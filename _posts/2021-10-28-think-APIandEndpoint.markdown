---  
layout: post  
title: "API? Endpoint?"  
subtitle: "API & Endpoint"  
categories: think
tags: 
comments: true  
header-img: img/post_img/apiendpoint.png
---  
## API와 Endpoint?
> 업무에서 자주 보였던 Endpoint에 대해 공부하다 보니, API와 연관되는 부분들이 많아서 이참에 정리 해보고자 한다.

#### API
---
- Application Programming Interface
	- 응용프로그램에서 운영 체제나 프로그래밍 언어가 제공하는 기능을 사용할 수 있도록 만든 Interface이다.
	- 인터넷에서 간단하게 정리되어 있는 많은 내용들의 표현을 빌리자면, 식당에서 서빙과 주문을 받는 홀의 직원? 웨이터? 라고 생각하면 되겠다.
	>API가 두 Application 사이에서 Interaction(상호작용) 할 수 있도록 도와주는 역할을 한다는 것이다.
	
	- 운영체제와 프로그래밍 언어에서 제공하는 기능을 응용프로그램에게 보여주고 ***(메뉴를 보여주고 주문을 받는다.)***
	- 사용자는 이를 보고선 운영체제와 프로그래밍 언어에서 지정한 형식에 따라 필요한 기능을 요청하는 구문을 작성한다 ***(주문을 한다. 여기서 API는 이 주문대로 주방의 요리사에게 주문내용을 전달한다.)***
	- 운영체제나 프로그래밍 언어는 구문에 따라 해당 기능을 실행한다. ***(요리를 만든다. 결과에 따른 return값을 응용프로그램에게 전달하는데, 이 역할을 API가 한다.)***
- Open API? Rest API? 
	- Open API
		- 말 그대로 개방된 API이다.
		- 네이버나 카카오의 Open API를 보면 알 수 있듯이, 네이버나 카카오에서 제공하는 기능을 Open API를 통해 누구나 사용할 수 있다.
	- Rest API?
		- **RE**presentational **S**tate **T**ransfer API의 약어.
		- REST 아키텍처의 제약 조건을 준수하는 API라는 말이다.
		- 종종 이 REST의 원리를 따르는 시스템을 **RESTful**이라고 부르기도 한다.
> REST라는 용어는 2000년 로이 필딩(Roy Fielding)의 박사학위 논문에서 소개되어진 소프트웨어 아키텍처의 한 형식이다.
- REST에 대한 자세한 내용은 아래 링크를 참고하면 되겠다.
	- [위키피디아-REST](https://ko.m.wikipedia.org/wiki/REST) 
	- HTTP Protocol에서는 다양한 메서드를 지원하지만, REST에서는 CRUD(Create, Read, Update, Delete)에 해당되는 아래의 메서드만 지원한다.
		-  POST(Create)
		- GET(Select,Read)
		- PUT(Update)
		- DELETE(Delete)

#### Endpoint
---
- '끝점', 말 그대로 끝에 위치한 노드를 의미한다.
- 우선, stack overflow 에 간단하게 정리되어 있는 내용을 참고하며 생각해보자.
	- [stack overflow - what is an endpoint?](https://stackoverflow.com/questions/2122604/what-is-an-endpoint)
-  내용을 보면, URI를 통해 resource에 접근하는 것 뿐만 아니라, 같은 URI라도 메서드에 따라 기능을 실행 할 수 있도록 구분되어진 끝지점의 정보 라고 생각하면 될듯 하다. 
	- 예시
		
|메서드|URL|
|:----|:----|
|GET|https://example.com/this-is-an-endpoint|
|GET|https://example.com/another-endpoint|
|POST|https://example.com/this-is-an-endpoint|

- 위의 표에서 같은 URL이지만 다른 메서드를 요청한다고 가정해보자 
	- GET /this-is-an-endpoint
	- POST /this-is-an-endpoint
	- 이렇게 같은 URI 지만 요청하는 메서드에 따라 다른 Endpoint가 사용된다.
- 이처럼 Endpoint는 메서드를 사용할 때 말고도, 어떤 리소스가 저장되어있는 위치를 나타내는 것이라 생각하면 쉬울 듯 하다.