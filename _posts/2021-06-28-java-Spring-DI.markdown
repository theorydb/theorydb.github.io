---  
layout: post  
title: "Spring-DI"  
subtitle: "member access"  
categories: java
tags: 
comments: true  
header-img:
---  

# Spring Framework-DI
- 이 내용은 뉴렉처 채널의 너튜브를 보고 정리를 위해 작성하는 것이다.
- 자세한 내용은 아래의 너튜브 링크를 참고하자.
- [뉴렉처 - 스프링 프레임워크 강의 5강 - Dependency를 직접 Injection하기](https://youtu.be/gtqctgfywn4)
---
## DI?
- DI(Dependency Injection)
	- Dependency를 주입하는 작업을 의미한다.
      - Dependency는 또 뭔가? 한글로 번역하면 의존성, 종속성이라고 한단다.
      - 코드에서 두 모듈간의 연결.
      - 객체지향 언어에서는 두 class간의 관계라고도 말한다.
      - 일반적으로 둘 중 하나가 어떤 용도의 사용을 위해 다른 하나를 사용한다.
- 그렇다면, ```Exam exam = new Exam();```의 구문을 생각해보자. 여기서, Exam()이라는 생성자의 내용이 업데이트 되었다면, 해당 부분의 수정을 위해 Exam()생성자를 사용한 코드는 모두 수정해야 한다.
- 이 상태를 결합력이 높은 상태라고 부른다.
- 저런 구성의 코드가 100줄이 있다고 가정하면? 일일히 다 수정을 해야하는 상황이 생길수도 있다.
- 이런 불편함을 해결하기 위해 이 내용을 수정할수 있도록 결합력을 낮출 필요가 있다는 말이다.
- 여기서 사용되는 것이 DI이다.
- 그렇다면 어떻게 DI를 하는 것인가?
  - 세가지로 나누어 진행한다.
    - Constructor Injection
    - Field Injection
    - Method Injection
- 아래의 링크에서 자세한 내용을 확인하자.
  - [DEPENDENCY(의존성)이란?](https://tony-programming.tistory.com/entry/Dependency-%EC%9D%98%EC%A1%B4%EC%84%B1-%EC%9D%B4%EB%9E%80)

## 그럼, DI를 직접 만들어 보도록 하자.
- 아래 구문들을 보며 DI를 직접 만드는 과정을 살펴 보도록 하자.
- Spring Framework를 사용하지 않고 만들어 보면서 Framework의 고마움을 느껴 보도록 하자.

<br>

Program 부분
```java
package spring.di;

//entity부분 형성
import spring.di.entity.Exam; // Exam interface를 생성하고 객체를 생성한다.
import spring.di.entity.NewlecExam; // Exam 인터페이스를 implements하는 NewlecExam class를 생성하고,  interface의 method를 overriding함으로서 해당 method를 구현한다.

//ui부분 형성
import spring.di.ui.ExamConsole; // ExamConsole 인터페이스 사용
import spring.di.ui.GridExamConsole; // ExamConsole 인터페이스를 implements하는 GridExamConsole class를 생성하고 interface의 method overriding 하여 method실체 구현
import spring.di.ui.InlineExamConsole; // ExamConsole 인터페이스를 implements하는 InlineExamConsole class를 생성하고 interface의 method overriding 하여 method실체 구현

public class Program {

	public static void main(String[] args) {

		Exam exam = new NewlecExam(); // Exam 인터페이스를 이용해 객체를 생성한다.
		//ExamConsole console = new InlineExamConsole(exam); // ExamConsole 인터페이스를 이용해 객체를 생성하고, InlineExamConsole생성자에 exam을 Injection.
		ExamConsole console = new GridExamConsole(exam); // ExamConsole 인터페이스를 이용해 객체를 생성하고, GridExamConsole생성자에 exam을 Injection.
		console.print(); // 생성된 객체인 console의 print method에 접근
	}
}
```

<br>

Exam interface
<br>

```java
package spring.di.entity; //entity package에 interface 생성

public interface Exam {
	int total();
	float avg();
}
```

<br>

NewlecExam class
<br>

```java
package spring.di.entity;

public class NewlecExam implements Exam { //Exam interface를 implements
	private int kor;
	private int eng;
	private int math;
	private int com;
	
	
	//Exam interface의 method를 overriding으로 구현
	@Override
	public int total() {
		return kor + eng + math + com;
	}
	
	@Override
	public float avg() {
		return total()/4.0f;
	}
}

```
## Entity는 뭐야?
- 이 내용은 아래의 링크를 참조하여 만들었다.
    - [엔티티란 무엇일까?](https://rh-cp.tistory.com/78)
  - 자세한 내용은 링크를 참고 바란다.
- Entity는 RDB(관계형 데이터베이스)에서 사용되는 용어로, 데이터의 집합, 개체를 의미한다.
- Entity는 아래와 같은 특징을 가진다.
  - Entity는 유일한 식별자를 가지고 있어야 한다. 예) 구로동 주민 Entity에서는 주민번호, 회원 Entity에서는 ID
  - Entity는 2개 이상의 인스턴스를 가지고 있어야 한다.
  - Entity는 반드시 Attribute(속성)을 가지고 있어야 한다. 예) 학생 Entity에서는 학번, 이름, 학년 등..
  - 다른 Entity와 최소 한개 이상의 관계가 있어야 한다.
  - 업무에서 관리되어야 하는 집합이어야 한다.
- Entity는 그 구성에 따라 아래의 종류로 나뉜다.

<br>

#### 유형, 무형에 따른 종류
|종류|내용|예시|
| :---: | :--- | :--- |
| 유형 Entity | 지속적으로 사용되는 Entity | 학생, 선생님..etc
| 개념 Entity | 물리적 형태가 없는 Entity | 보험상품, 조직..etc
| 사건 Entity | Business process를 실행하면서 생성되는 Entity | 주문, 취소, 수수료..etc

<br>

#### 발생 시점에 따른 종류
|종류|내용|예시|
| :---: | :--- | :--- |
| 기본 Entity | 키 Entity 라고 불린다. 다른 엔티티에 영향을 받지 않는 독립적으로 생성되는 Entity | 고객, 상품..etc
| 중심 Entity | 기본 Entity와 행위 Entity 중간에서 기본 Entity로부터 발생하고 행위 Entity를 생성한다. | 주문, 취소, 체결..etc
| 행위 Entity | 2개 이상의 Entity로부터 발생된다. | 주문내용, 취소내용..etc