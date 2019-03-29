---
layout: post
title:  "기사요약 서비스의 구성"
subtitle:   "기사요약 서비스의 구성을 공유하려한다."
categories: doc
tags: doc summarization secreport
---

[secretary](https://chrome.google.com/webstore/detail/secretary/bijcgcgbhmeemlnidoigdcnokggknikb?hl=ko)라는 기사요약서비스와 [한줄IT](https://twitter.com/R2BQBbW6CM4oFBN)라는 기사요약 트윗을 만들었다. 그 과정에서 느낀 요약 서비스에 대해 이야기 해 보려한다.

## 기사요약서비스

---

정보의 홍수라는 말이 전혀 어색하지 않다. 웹에는 하루에도 수도 없이 글이 올라온다. 그 중에 질이 높은 기사를 찾아 읽는 것은 보물 찾기나 다름없다.

수많은 정보를 미리 요약해서 보고 더 유심히 읽고싶은 글들은 선택하여 보면 좋지 않을까? 라는 생각에서 시작 된 프로젝트가 [secretary](https://chrome.google.com/webstore/detail/secretary/bijcgcgbhmeemlnidoigdcnokggknikb?hl=ko)와 [한줄IT](https://twitter.com/R2BQBbW6CM4oFBN)이다.

## 기사요약서비스의 구성

---

기본적으로 기사요약 서비스를 구성하려면 두가지가 필요하다.

- 기사 본문찾기

- 기사 요약하기

어떤 플랫폼의 기사에서 우리는 본문을 찾아야 하고, 댓글이나 광고가 아닌 본문을 요약해야한다.

## 기사 본문찾기

---

모든 기사를 일일이 찾아서 한땀한땀 요약하는 것은 게으른 개발자로써 용납 할 수가 없다. 그렇다면 글을 자동으로 크롤링 해야하는데, 여기서 문제가 생긴다.

### 문제 1. 기사의 본문이 어디야?

대부분(아니 거의 모든) 사이트에는 네비게이션, 광고, 댓글, 메타정보 등등의 내가 원하지 않는 정보들이 담겨있다. 나는 오직 기사의 본문만을 긁어와서 요약 알고리즘을 돌릴건데, 대체 본문이 어딘지 어떻게 알 수 있을까?

솔직히 명확한 해결방법은 없다. 본문찾기 알고리즘은 현재도 개발중이다. 본문찾기 알고리즘의 종류는 다양한데, 눈으로 보는 것처럼 비쥬얼을 분석해서 찾는 방법, 가장 긴 파트를 찾는 방법 등등이 있다.

지금 제시한 방법 두가지 모두 문제가 있는 게 보일텐데, 예를 들어 댓글이 본문만큼 긴 경우도 더러있다(특히 시사, 정치 등의 파트에서).

뚜렷한 정답은 없지만, 본문찾기 알고리즘과 요약 알고리즘을 함께 적용해 해결하고 있다.

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

### 문제 2. 동적인 기사

네이버 블로그의 내용이나 브런치, 미디엄의 인기글들의 리스트는 동적으로 DOM이 생성된다. 이런 경우 일반적인 방법으로는 글을 크롤링 할 수가없다.

이런 경우는 파이썬의 셀레니움이나 팬텀JS 등을 사용하여 실제 브라우저에서 작동한 것처럼 DOM을 생성해서 읽어와야 한다.

## 기사 요약하기

---

기사의 본문을 찾았으면 기사를 요약해야한다. 현재 내가 가장좋아하는 요약방법은 [LexRank](https://www.cs.cmu.edu/afs/cs/project/jair/pub/volume22/erkan04a-html/erkan04a.html)라는 알고리즘이다.

이 알고리즘이 뭐냐면, 구글의 페이지랭크라는 알고리즘의 변형이라고 할 수있다. 구글에서 만든 페이지간의 연관성을 찾는 알고리즘인데, 이걸 문장으로 끌고 내려온게 바로 LexRank이다.

LexRank 알고리즘은 알고리즘을 공부했거나, 컴퓨터가 전공인 사람들은 아마 한번쯤 들어봤을 그래프 기반의 알고리즘이다.

쉽게 말해 문장간의 연관성을 아주 복잡하게(?) 찾아서 점수를 메기는 방식이다.

나는 결과물에 아주 만족하고 있다. 공부하는 사람은 역시 멋있다.

## 마치며

---

기사를 요약하는 서비스에 새롭게 쓰이는 건 거의 없다. 기사의 본문을 찾고, 요약하면 된다.

하지만 이 서비스가 플랫폼화 된다면, 사람들의 기사 소비가 한층 가치있어 질 것이다.
