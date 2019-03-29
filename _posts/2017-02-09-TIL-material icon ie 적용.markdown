---
layout: post
title:  "React Material Icon IE 적용"
subtitle:   "Material Icon을 적용한 React 프로젝트는"
date:   2017-02-09 20:21:33 +0900
categories: devlog
tags: react material icon ie devlog
---

Material Icon을 적용한 React 프로젝트는 IE 10 이하에서 적용이 안된다.

사실 IE가 문제가 아니라 모바일에 어떤 진짜 듣도보도 못한 어떤 브라우저에서 안돌아가는데 보이게 만들어달라길래 삽질을 좀 했다.

팀에 디자이너도 없고 다른 아이콘 가져다 쓰기엔 불편해서 연구해봤다.

chrome의 Element Inspector를 뒤져보니 .material-icon CSS에


> -webkit-font-feature-settings : 'liga';

이런게 숨어있었다.

다른 환경에서 조정해주기 위해인거 같은데

material icon을 사용하는 곳의 CSS에 아래와 같이 추가해줬다.

> i.material-icons { -webkit-font-feature-settings : 'liga'; }


결과는 성공. IE에서도 나타난다.

제발 다른데서도 잘 먹길 바란다.
