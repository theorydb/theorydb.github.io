---
layout: post
title:  "[git]Feature Branch Workflow"
subtitle:   "Feature Branch Workflow"
categories:  devlog
tags: git feature

---

### Feature Branch Workflow

기존의 Centralized Workflow를 이용하고 있었다면, Feture Branch를 만드는건 아주 쉽게 개발자들간의 협업과 능률적인 의사소통을 촉진시킬 수 있는 방법이 될 것이다.


Feture Branch의 핵심 아이디어는 모든 feature 개발이 마스터 브랜치대신 전문 브랜치에서 이루어진다는 것이다. 이런 캡슐화는 많은 개발자들이 각자의 피쳐를 개발할때 메인 코드에 방해를 받지 않도록 해준다. 또한, 마스터 브랜치는 깨진코드를 포함하고 있지 않고, 이는 계속 코드를 합쳐야하는 환경에서는 아주 큰 장점이다.


피쳐 개발을 캡슐화하는건 pull requests 를 할 수 있게하는데, 이건 브랜치에 대한 토론을 이야기한다. 그리고 오피셜 프로젝트에 통합하기 전에 개발자들에게 서명할 기회를 준다. 만약 피쳐의 중간에서 스턱되었다면, 팀원들에게 제안받기위한 풀 리퀘스트 에스킹을 열수있다. 요점은 풀리퀘스트는 쉽게 팀이 서로의 일에 코맨트 할수 있다는 점이다.

### Feature Branch Workflow 이용법

featuer branch workflow는 여전히 central repository를 사용하며, master는 여전히 오피셜 프로젝트를 이야기한다. 하지만 개발자들은 local master에 직접 커밋하는 대신 새 feature를 개발할 때마다 새 브랜치를 매번생성한다. 피쳐 브랜치는 이름만 봐도 무엇을 개발하는지 설명이 되어야 한다. 이렇게 하면 각 브랜치에서 더 명확하고, 높은 집중도를 유지할 수 있다.


깃은 기술적으로는 마스터 브랜치와 피쳐 브랜치를 구별하지 않는다. 그렇기 때문에 개발자들은 일반적으로 깃을 이용하듯 커밋하고, 편집하면서 이용하면 된다.


게다가 피쳐브랜치는 central repository에 푸쉬할수있다. 이는 어떤 오피셜코드도 건드리지 않고 다른 개발자들과 피쳐를 공유하는것을 가능하게 한다 . 그러므로 마스터 브랜치는 단 하나의 특별한 브랜치이다. 여러가지 피쳐브랜치들을 저장하고 어떤 문제점도 가지고 있지 않는 central repository인 것이다. 물론 모든 이들이 로컬 커밋을 백업하기에도 피쳐브랜치 방식은 편리하다.
