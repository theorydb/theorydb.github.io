---
layout: post
title:  "[web]브라우저가 웹페이지를 그리는 법"
subtitle:   "브라우저가 웹페이지를 그리는 법"
categories: devlog
tags: web devlog
---

이제 우리는 HTML을 사용하여 브라우저에 다양한 요소들을 표현하고, CSS로 요소들을 꾸밀 줄 알며,  JavaScript로 페이지를 조작할 수있다.

이 다음에 생각해 보아야 할 건 '실제 브라우저가 어떻게 돌아가는가?'이다. 원리를 알아야 최적화가 가능하다. 이떄까지 아무 물감으로 그림을 그렸다고 한다면, 종이와 물감의 상관관계를 파악하는 과정 말이다.

## Critical Rendering Path

---

일반적으로 디스플레이는 1초에 화면을 60번 그린다. 짧게 60fps(frame per second)라는 표현으로 대체할 수 있다.

디스플레이가 1초에 60번 바뀌는데 웹페이지가 1초에 10번 그려진다면, 버벅이는 현상이 발생한다. 우리는 이런 현상을 Jank라고 부른다.

자, 그럼 웹페이지의 렌더링을 최적화 한다는 것은 브라우저가 1초에 60번 렌더링 할 수 있도록 하면된다. "참, 쉽죠?"

### 어떻게 해야하죠?

웹페이지 최적화를 위해 우린 느린 부분을 찾아서 개선해야한다. 어떤 부분이 느린지를 찾으려면 웹페이지가 화면을 어떻게 그리는지를 알아야 한다. 브라우저가 화면을 그리는데 사용하는 엔진에는 크게 두 종류가 있는데, 크롬과 사파리의 Webkit엔진과 파이어폭스의 Gecko 엔진이 있다.

브라우저가 이런 엔진을 사용해서 화면을 그리는 데 거치는 주요한 과정을 우리는 'Critical Rendering Path'라고 부른다. 해석하면 '주요 렌더링 경로'.

웹페이지를 호출하는 방식의 큰 그림을 그려보자.

### Critical Rendering Path

1. HTML데이터를 파싱한다.

2. 파싱한 결과로 DOM Tree를 만든다.

3. 파싱 중 CSS파일 링크를 만나면 CSS파일을 요청해서 받고, CSS 파일을 읽어 CSSOM(CSS Object Model)을 만든다.

4. DOM Tree와 CSSOM을 사용해 Render Tree를 만든다.

5. Render Tree의 노드들이 화면의 어디에 위치할지 계산한다.

6. 웹페이지를 그린다.

## 심화공부

---

### 1. HTML 파싱

브라우저는 응답으로 받아온 HTML문서를 DOM으로 만들기 위해 각각의 요소를 파싱한다. 이 과정에서 미디어파일(이미지나 비디오등)을 만나면 추가 요청을 보낸다.

JavaScript를 만나면 실행할 때까지 파싱을 멈춘다.

### 2. DOM 만들기

브라우저는 읽어들인 HTML 바이트 데이터를 문자열로 바꾸게 된다. 이렇게 바꾼 문자열을 다시 읽어서, HTML 토큰으로 변환한다. 태그의 경우 StartTag와 EndTag로 바뀌게 된다.

토큰들은 다시 노드로 바뀌게 되는데, StartTag와 EndTag사이에 있는 노드들은 자식노드로 들어간다. 즉 트리모양이 되는데, 이 과정이 끝나면 DOM Tree가 생성되는 것이다.

### 3. CSSOM 만들기

HTML을 파싱하다 CSS링크를 만나면, CSS파일을 받아온다. CSS파일은 파싱과정을 거쳐 역시 Tree형태의 CSSOM으로 만들어진다.

CSS 파싱은 cascading규칙(부모의 특성을 자식이 이어받음)이 추가되는 점을 제외하고는 HTML파싱과 동일하다.

CSSOM이 구성이 되어야 다음 과정을 밟을 수 있기 때문에, CSS는 렌더링의 블라킹 요소라고도 한다.

### 4. Render Tree

DOM과 CSSOM을 합쳐 Render Tree를 만든다. Render Tree는 DOM Tree에 있는 것들 중에 실제 보이는 것들로만 이루어진다.

즉, display:none으로 설정되어 있는 것은 DOM Tree에 있어도 Render Tree에는 없다. 마찬가지로 head태그안의 메타내용들은 Render Tree에는 존재하지 않는다.

Render Tree에는 Render Object Tree, Render Layer Tree, Render Style Tree, InlineBox Tree등이 포함되어있다.

Render Object Tree가 보이는 것들로 이루어진 트리이다. block, inline, image, text 등등의 Object가 있는데, div는 block, span은 inline 요소에 배정되는 것이다.

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

Render Object의 필요에 따라 Render Layer가 만들어진다. 그리고 Render Layer중에 GPU처리가 필요하면 Graphic Layer가 만들어진다. 대표적인 예는 아래와 같다.

- CSS 3D Transform(translate3d, preserve-3d 등)이나 perspective 속정이 적용된 경우

- CSS 애니메이션함수나 필터함수를 사용하는 경우

- video나 canvas 요소를 사용하는 경우

- 자식 요소가 레이어로 구성된 경우

- z-index가 낮은 형제 요소가 레이어로 구성된 경우

일반적인 상황이라면 레이어는 하나만 사용하게 된다.

### 5. Layout

Render Tree가 만들어지면, 이제 각각의 노드들이 어디에 위치할 지 계산하는 과정을 거친다. 이 과정을 Layout과정이라고 한다. position, width, height 등등 위치에 관련된 부분들을 계산한다.

width:100%인 상태에서 브라우저를 리사이즈하면, Render Tree는 변경되지 않고 Layout 이후 과정만 다시 거치게 된다.

### 6. Paint

Layout과정을 거쳐 계산을 마치면, 실제 그리는 작업(Paint)에 들어가게 된다. 실제로 픽셀이 그려지는 작업이다. 만약 Render Layer가 2개 이상이면 각각의 Layer를 그린 뒤 하나의 이미지로 Composite하는 과정을 거친 뒤 브라우저에 실제로 그려지게 된다.

색이 바뀐다거나 노드의 스타일이 바뀌는 걸로는 Layout 과정을 거치지 않고 Paint만 일어난다.

## 간단한 최적화 팁

---

- 애니메이션이 들어간 노드는 positon:fixed 또는 position:absolute로 지정한다.

애니메이션은 엄청난 Layout 비용이 들어간다. 이 때 absolute나 fixed로 전체 레이아웃과 분리해주면 애니메이션이 필요한 노드만 계산하게 된다.

그렇지 않을 경우 무든 노드들을 재계산 해야하기 때문에 아주 많은 비용이 들어 느려지게 된다.

- 동일 요소에 스타일 변경은 가급적 한번에 처리한다.

```js
function changeDivStyle(){
    var sampleEl = document.getElementById("sample");
        sampleEl.style.cssText = 'background:blue; width:200px;height:50px;';
}
changeDivStyle();
```
