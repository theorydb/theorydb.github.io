---
layout: post
title:  "개발자를 위한 JavaScript - 2 객체지향적 자바스크립트"
subtitle:   "자바스크립트의 객체지향적인 면모를 알아보자."
categories: devlog
tags: javascript
---

자바스크립트의 객체지향적인 면모를 알아보자.

## 서문
---

객체지향적인 개발은 복잡하고 탄탄해야하는 현대 개발 산업에 맞춰 진화한 개발방식이다. 현대의 거의 지배적인 방식이라고 볼 수 있다.

객체지향적인 언어라면 이미 Java, C++등을 알고 있을 수 있다. 두 언여 역시 자신만의 객체지향적인 개념을 가지고 있는데, 자바스크립트도 마찬가지다.

오늘은 자바스크립트의 객체지향적인 면모를 알아보자.

## 객체지향
---

객체지향의 기본은 객체를 만들고 그 객체들을 조합하여 하나의 프로그램을 만드는 것이라고 할 수 있다.

객체는 쉽게 말하면 변수와 메소드를 모은 것이라고 할 수 있다.

> 정확히 말해 변수와 메소드를 모은건 클래스라고 부른다. 클래스가 실제 할당되어 나온 인스턴스가 객체이다.
> 아마 전공자라면 대학교에서 객체지향프로그래밍또는 프로그래밍언어에서 배운 기억이 있을거다.

## 객체지향의 특징
---
흔히 말하는 객체지향적 사고를 하기 위해서는 객체지향의 특징을 알아야한다.

### 추상화

추상화라는건 사실 좀 추상적으로 들릴 수 있지만. 어떤 모듈또는 부품을 만든다고 생각하면 쉽다.

예를 들어 학교라는 프로그램을 만들때 선생님과 학생이라는 부품을 만드는 것이다.

### 캡슐화

캡슐화라는건 내부로직은 숨기고 사용방법만 노출하는 거라고 할 수 있다.

예를 들어 학생은 교수님이 성적을 어떻게 매기는지 모르지만, 교수님에게서 성적을 받아 볼 수 있다.

### 상속

상속은 말그대로 물려받는 것을 말한다.

예를 들어 학교라는 프로그램을 만들때 선생님과 학생, 관리원, 미화원 이라는 클래스는 모두 사람이라는 공통점이 있다. 이럴 때 사람이라는 상위 클래스를 만들어 각각의 객체에 사람의 특징을 물려줄 수 있다.

이럼으로써 사람에 해당하는 파트는 각 클래스에서 다시 작성할 필요가 없어진다.

### 다형성

다형성이란 조금씩 다른 방법으로 일을 하는 함수를 같은 이름으로 호출하는 것이라고 할 수 있다.

예를 들어 총을 쏘는 것과 활을 쏘는 것은 방법은 다르지만, '쏘세요!' 했을 때 두 경우 모두 쏘는 것을 말한다.

## 자바스크립트의 객체지향
---

### 생성자

자바스크립트에서 객체를 만들 때 함수를 이용한다. new를 붙여 함수를 부르면 객체가 리턴된다.

아래처럼 사용한다.

```js
function Person(name){
    this.name = name;
    this.greeting = function(){
        return 'Hello, I am '+ this.name;
    }
}

var dev = new Person('dev');
console.log(dev.greeting());
```

### prototype과 상속

prototype은 원형이라고 할 수 있다.

이를 사용해서 상속을 구현할 수 있다.

```js
function Person(name){
    this.name = name;
    this.greeting = function(){
        return 'Hello, I am '+ this.name;
    }
}

function Programmer(name){
    this.name = name;
    this.coding = function(){
    	return 'Hello '+ this.name+' World';
    }
}

Programmer.prototype = new Person();

var dev = new Programmer('dev');
console.log(dev.greeting());    //Hello, I am dev
console.log(dev.coding());      //Hello dev World
```

### Object

모든 객체가 상속하는 조상 객체이다. Object에 prototype을 사용해서 상속시키면 모든 객체에 영향을 미칠 수 있다.
