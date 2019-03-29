---
layout: post
title:  "react-redux-material-meteor-kr"
subtitle:   "react-redux-material front-end x meteor back-end"
categories: doc
tags: dev boilerplate react meteor
---

react-redux-material front-end x meteor back-end

# 본문 

이 프로젝트는 두개의 앱을 가지고 있습니다. 하나는 React를 비롯한 클라이언트 앱, 다른 하나는 Meteor를 기반한 백엔드 앱 입니다.

이렇게 앱을 분리함으로써 하나의 Meteor 백엔드와 다른 다양한 클라이언트 앱(ReactNative, Angular, React...등등)과 연동할 수 있습니다.

백엔드와 클라이언트 앱과의 통신은 DDP(Distributed Data Protocol)로 이루어집니다. 백엔드와 클라이언트는 서로를 전혀 모르지만 같은 언어로 대화하는 것 뿐입니다.

# 스택

create-react-app

react-redux

react-router

asteroid

react-s-alert

material-ui

meteor


# 기능

routing과 로그인 기능이 구현되었습니다.

# 어떻게 작동하나요?
프로젝트를 클론하고, 아래처럼하여 Meteor 백엔드를 엽니다.

>$ cd {project_name}/rm-back
>
>$ npm install
>
>$ meteor -p 9000

9000번 포트로 백엔드를 열고, 터미널 하나를 더 확장해 클라이언트를 엽니다.

>$ cd {project_name}/rm-front
>
>$ npm install
>
>$ npm start

이 후, 브라우저에서 localhost:3000으로 접속하면 테스트를 해볼 수 있습니다. 이 앱은 Meteor 벡엔드와 통신하고 있습니다.

DDP 연결은 asteroid.js파일에 구성되어있습니다. 백엔드 데이터를 구독할 수 있고 리스너를 설정할 수 있습니다.

# 장점

Webpack, React 및 모든 기능을 사용할 수 있는 아키텍처를 구성했습니다. 빠르고 간단한 구성으로 Meteor 실시간 백엔드도 갖추었습니다.
많은 프론트앤드 앱과 하나의 Meteor 백엔드 앱이 연결될 수 있을 것입니다.우리만의 BaaS같은 것을 만들 수 있을 것입니다.
