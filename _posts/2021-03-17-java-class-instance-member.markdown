---  
layout: post  
title: "Class, Instance member in java"  
subtitle: "member access"  
categories: java
tags: 
comments: true  
header-img:
---  

# java에서 class와 instance의 접근
- 이 내용은 생활코딩의 너튜브를 보고 정리를 위해 작성하는 것이다.
- 자세한 내용은 아래의 너튜브 링크를 참고하면 되겠다.
- [생활코딩 - Java - 클래스 맴버, 인스턴스 맴버 (4/4) : 타입별 비교](https://youtu.be/AiquVwHyeGQ)
---
## Class? Instance?
- Class
	- 추상적으로 분류되는 한 부류를 의미한다.
	- 외제차 M사의 E클래스, S클래스, B사의 7시리즈, 3시리즈 같이 나뉘어지는 부류다. 
	- 한 객체를 생성할 때(Instance화 할 때) 적용되는 설계도 역할을 한다.
	- main함수에서 생성되는 객체(instance)는 Class에 작성된 내용과 동일하게 생성된다.
	- 식육목 -> 고양이아목 -> 고양이상과 -> 고양이과 처럼 나뉘는 부류를 일컫는다.
	- 위의 글에서 고양이과는 고양이상과를 상속받는다. 자세한 부분은 상속에 대해 이야기 할 때 다시 다루도록 한다. 
- Instance
	- Class에 작성된 형식을 바탕으로 객체를 생성함을 의미한다.
    - 예를 들어, PickupTruck 클래스에서 생성한 Truck1은 PickupTruck를 Instance화 하여 생성된 객체이다.
      - 여기서 객체인 Truck1은 color, size, isAutomationTranfer 등 클래스에서 작성되었던 내용들이 적용되는 것이다.
      - 고양이과의 클래스에서 생성된 누렁이, 점박이, 까망이 는 고양이과의 클래스를 바탕으로 생성된 인스턴스이다. (여기서 인스턴스 명은 누렁이, 점박이, 까망이) 

## Class 멤버와 Instance 멤버의 접근
- 아래 구문에서 Class멤버인 Static변수와 int형 변수, 이 Class를 바탕으로 생성한 Instance의 멤버로의 접근에 대해 알아보자.
```java
class C1 { //클래스 C1
	static int static_variable = 1;
	// 클래스 Static 변수 선언
	
	int instance_variable = 2;
	// 객체 생성 시 인스턴스 변수로 선언됨
	
	static void static_static() { // Static 메소드로 Static 변수 접근
		System.out.println("Static 메소드 실행, Static 변수의 값은"+static_variable+"이다"); // Static 메소드에서 클래스의 Static 변수 출력
	}
	
	static void static_instance() { // Static 메소드로 인스턴스 변수 접근
		//클래스 메소드에서는 인스턴스 변수에 접근 불가함.
		//System.out.println(instance_variable);
	}
	void instance_static() { // 인스턴스 메소드로 Static 변수 접근
		//인스턴스 메소드에서는 클래스 변수에 접근 할 수 있다.
		System.out.println("인스턴스 메소드 실행, static 변수의 값은"+static_variable+"이다" );
	}
	void instance_instance() { // 인스턴스 메소드로 인스턴스 변수 접근
		System.out.println("인스턴스 메소드 실행, instance 변수의 값은" +instance_variable+"이다");
	}

}
```
- 위와 같이 작성된 클래스는 아래 구문처럼 사용된다.
```java
public class ClassMemberDemo{
	public static void main(String[] args) { //메인함수
		C1 c = new C1(); //C1형식의 객채 c생성
		
		//인스턴스를 이용해서 Static 메소드에 접근-> 성공
		//인스턴스 메소드가 Static 변수에 접근 ->성공
		c.static_static();
		
		//인스턴스를 이용해서 Static 메소드에 접근->성공
		//Static 메소드가 인스턴스 변수에 접근->실패
		c.static_instance();
		
		//인스턴스를 이용해서 인스턴스 메소드에 접근->성공
		//인스턴스 메소드가 클래스 변수에 접근->성공
		c.instance_static();
		
		//인스턴스를 이용해서 인스턴스 메소드에 접근->성공
		//인스턴스 메소드가 인스턴스 변수에 접근->성공
		c.instance_instance();
		
		//클래스를 이용해서 클래스 메소드에 접근->성공
		//클래스 메소드가 클래스 변수에 접근->성공
		C1.static_static();
		
		//클래스를 이용해서 클래스 메소드에 접근->성공
		//클래스 메소드가 인스턴스 변수에 접근->실패
		C1.static_instance();
		
		//클래스를 이용해서 인스턴스 메소드에 접근->실패
		//C1.instance_static();
		
		//클래스를 이용해서 인스턴스 메소드에 접근->실패
		//C1.instance_instance();
	}
}
```