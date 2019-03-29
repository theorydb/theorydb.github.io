---
layout: post
title:  "[Javascript]자바스크립트 성능 최적화 팁"
subtitle:   "자바스크립트 성능 최적화 팁"
categories: devlog
tags: devlog javascript
---

대부분의 언어가 그렇듯이 자바스크립트는 배우기도 쉽고 사용하기도 쉽지만, 잘 사용하기는 아주 어려운 언어이다. 그냥 작성해도 돌아는 가지만, 더욱 최적화 할 수 있는 방법을 알아보려한다.

## 문법

---

### || 연산자

 `||` 연산자는 참을 만나면 그 뒤는 연산을 하지 않으므로 if문 대신 사용 하면 코드량과 연산 횟수를 줄일 수 있다.

```js
var result;
if( some_var ){
    result = some_var;
}else{
    result = 'default value';
}

// || 연산자 사용
const result = some_var || 'default value';
```

### && 연산자

&& 연산자는 참을 만나야 다음 연산을 하므로 어떤 조건을 만족할 때 실행하도록 하는 코드에서 사용하면 코드량과 연산 횟수를 줄일 수 있다.

```js

var userID; ​
if (user && user.loggedIn) {
    userID = user.id;
} else {
    userID = null;
}

// && 연산자 사용
var userID = user && user.loggedIn && user.id

```

### double exclamation mark(!!)

!!표시를 사용하면 값의 유무를 판별할 수 있다.

```js
// 아래 경우를 제외하곤 true를 반환한다.
!!false === false
!!0 === false
!!"" === false
!!null === false
!!undefined === false
!!NaN === false

// !! 표시 사용
console.log(navigator.userAgent.match(/MSIE 8.0/));  // returns null or array
console.log(!!navigator.userAgent.match(/MSIE 8.0/));  // returns true or false
```

### scope

자바스크립트는 블록내부에서 점차 큰 범위로 탐색한다. scope와 지역변수를 활용하면 성능 향상을 기대할 수 있다.

```js

function selectorEx(){
    var target1 = document.getElementById('target1');
    var target2 = document.getElementById('target2');
}

//scope 활용
function enhancedSelectorEx(){
    var d = document;
    var target1 = d.getElementById('target1');
    var target2 = d.getElementById('target2');
}
```

### innerHTML

innerHTML 횟수는 최소한으로 하는 것이 좋다. 브라우저는 갱신할 때마다 렌더링을 거치게 되기 때문이다. 자세한 내용은 [브라우저가 웹을 그리는 법](https://isme2n.github.io/devlog/2017/07/06/browser-rendering/)에서 확인할 수 있다.

```js
//루프를 돌 때마다 브라우저가 웹페이지를 다시 그린다.
for(var i=0; i<100; i++){
    document.getElementById('list').innerHTML += "<li>list</li>";
}

let list = '';
for(var i=0; i<100; i++){
    list += "<li>list</li";
}

document.getElementById('list')+=list;
```

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

### 배정문

아래문법이 좀 더 효울적이다.

```js

var arr = [];   //good
var arr = new Array();  //bad

arr[i] = i;     //good
arr.push(i);    //bad

var obj = {};   //good
var obj = new Object(); //bad

obj.a = 1;  //good
obj["a"] = 1;   //bad

var str = "test";   //good
var str = new String("test");   //bad

```

추가로 배정은 한번에 하는 것이 좋다.

```js

/* array */
var array = new Array();
array[0] = 1;
array[1] = 1.5;

// 아래 코드가 더 효율적이다.
var array = [1, 1.5];

/* object */
var obj = new Object();
obj.hello = 'hello';
obj.world = 'world';

// 아래 코드가 더 효율적이다.
var obj = {
    hello : 'hello',
    world : 'world'
}

```

### 참조

참조 횟수를 최소한으로 줄이는 것이 좋다.

```js

// loop를 돌때마다 array 참조가 일어남.
for (var i = 0; i < arr.length; i++){
    ...
}

// 아래와 같이 구현하는게 성능에 더 효율적이다.
var l = arr.length;
for (var i = 0; i < l; i++) {
    ...
}

```

### try ~ catch

try ~ catch 구문안에 있는 코드는 컴파일러가 최적화하지 못한다. 성능에 민감한 함수들은 도우미 함수를 생성하는 것이 좋다.

```js

function helper_func() {
  // 성능에 민감한 작업.
}

try {
    ...

    helper_func();

    ...
} catch (e) {
    ...
}

```
