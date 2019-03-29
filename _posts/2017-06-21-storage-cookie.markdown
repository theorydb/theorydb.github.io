---
layout: post
title:  "[web]로컬스토리지, 세션스토리지 그리고 쿠키"
subtitle:   "로컬스토리지, 세션스토리지 그리고 쿠키"
categories: devlog
tags: web storage cookie
---

오늘은 웹에서 스토리지와 쿠키에 대해서 알아보려한다.

## 스토리지와 쿠키

---

클라이언트의 정보를 저장하는 역할을 하는 것에는 크게 스토리지와 쿠키가 있다.

### 스토리지

스토리지는 말그대로 저장소를 이야기 하는데, 데이터를 저장하는 역할을 한다. HTML5에서 추가된 스펙으로 키와 벨류가 쌍으로 저장되는 키-벨류 스토리지이다.

종류는 로컬 스토리지와 세션 스토리지 두 종류로 나뉜다. 두 스토리지의 차이점은 영구성이다. 로컬스토리지는 특별히 지우지 않는 한 계속 브라우저에 남아있는 스토리지인 반면에, 세션스토리지는 브라우저가 닫힐 경우 제거된다.

이런 특징 때문에 서로 사용처들이 다른데, 로컬스토리지는 보통 지속적으로 필요한 [자동로그인](https://isme2n.github.io/web/2017/06/13/security-remember-me/)이나 설정값 데이터등을 저장하고, 세션스토리지에는 간단한 입력폼 정보라던가를 저장해서 문제시 복구하는 기능으로 사용되곤한다.

물론 클라이언트의 저장소에 저장하는 것이기 때문에 민감한 정보(비밀번호 등)는 저장하지 않는 것이 좋다.

### 쿠키

쿠키도 역시 키-벨류 저장소인데, 만료기한도 함께 있는 저장소이다. HTTP요청시 사용자의 쿠키 정보가 서버로 전달되어 사용자를 구별하곤한다.

## 쿠키의 단점

---

그렇다면 왜 쿠키라는 기능이 있는데 스토리지를 만든 것일까?

### 용량

먼저, 쿠키는 사이즈가 매우 작다. 쿠키는 4kb의 용량을 한계로 가지고 있는 저장소로, 많은 양의 데이터를 저장할 수 없다.

### 속도

쿠키는 매 HTTP요청마다 포함되어 서버에 전달된다. 물론 쿠키는 4kb의 매우 작은 용량이지만 매요청마다 필요하지 않은 데이터가 전달 되는 것은 낭비이다.

### 보안

쿠키는 사용자의 로컬에도 저장되고, 매 HTTP요청마다 전달된다. 쿠키는 별도의 암호화 없이 전달되기 때문에 로컬또는 요청이 도청당하면 사용자의 정보가 쉽게 도난당할 수 있다.

<script async src="//pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
<ins class="adsbygoogle"
     style="display:block; text-align:center;"
     data-ad-format="fluid"
     data-ad-layout="in-article"
     data-ad-client="ca-pub-9134477021095729"
     data-ad-slot="3873336698"></ins>
<script>
     (adsbygoogle = window.adsbygoogle || []).push({});
</script>

## 스토리지의 장점과 사용

---

### 장점

스토리지는 쿠키의 문제점을 보안하기위해 나온 것이기 때문에 쿠키의 단점을 대부분 커버하였다. 스토리지의 용량은 꽤 크고, HTTP요청 때 전달되지 않으며, 표준을 지켜 설계한다면 보안도 한층 강화할 수 있다.

스토리지의 용량은 쿠키에 비해 상대적으로 큰데, 표준에서는 한사이트당 5mb를 권장한다. 키와 벨류값만 저장하기엔 충분히 큰 사이즈이다.

또한 서버에 전송되지 않기 때문에, 자원 낭비에 대해 크게 고려할 필요가 없다.

### 사용

스토리지는 브라우저, 디바이스 등등의 환경을 많이 타고, 그 때문에 제대로 작동을 하지 않을 수도있다. 그러므로 꼭 필요한 주요한 정보라면 서버에서 관리를 해야하며, 스토리지는 없어도 되지만 있으면 좋은 기능을 구현하는 것이 좋다.

예를들어 '팝업 일주일간 열지않기'라거나 '글쓰기 도중 나갔을 때 내용 복구하기'등의 기능에 사용할 수 있다.

## 사용법

---

### 쿠키

쿠키는 보통 따로 함수를 만들어서 사용한다.

```js
function setCookie(cname, cvalue, exdays) {

    var d = new Date();

    d.setTime(d.getTime() + (exdays*24*60*60*1000));

    var expires = "expires="+d.toUTCString();

    document.cookie = cname + "=" + cvalue + "; " + expires;

}



function getCookie(cname) {

    var name = cname + "=";

    var ca = document.cookie.split(';');

    for(var i=0; i<ca.length; i++) {

        var c = ca[i];

        while (c.charAt(0)==' ') c = c.substring(1);

        if (c.indexOf(name) != -1) return c.substring(name.length,c.length);

    }

    return "";

}

```

### 스토리지

스토리지는 setItem,getItem,remove,clear 등의 함수를 이용해서 사용한다.

```js
localStorage.setItem('name', 'isme2n');
localStorage.setItem('gender', 'male');
localStorage.getItem('name'); // isme2n
localStorage.getItem('gender'); // male
localStorage.removeItem('gender');
localStorage.getItem('name'); // isme2n
localStorage.getItem('gender'); // null (삭제됨)
localStorage.clear(); // 전체 삭제
```

## 마치며

---

쿠키와 스토리지는 서로 대립되는 관계가 아니다. 쿠키와 스토리지를 적절히 혼합하여 사용하면 더 좋은 서비스를 만들 수 있을 것이다.
