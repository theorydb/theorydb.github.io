---
layout: post  
title: "Memory Structure"  
subtitle: "Memory Structure"  
categories: think
tags: 
comments: true  
header-img: img/post_img/memorytitle.png
---  

# 메모리 구조에 대해 알아보자
- 아래 링크된 글들을 읽으며 정리해 보았다.
	> - <https://genesis8.tistory.com/181>
	> - <https://jinshine.github.io/2018/05/17/%EC%BB%B4%ED%93%A8%ED%84%B0%20%EA%B8%B0%EC%B4%88/%EB%A9%94%EB%AA%A8%EB%A6%AC%EA%B5%AC%EC%A1%B0/>
	> - <http://www.tcpschool.com/c/c_memory_structure>
	> - <https://velog.io/@hidaehyunlee/%EB%A9%94%EB%AA%A8%EB%A6%AC-%EA%B5%AC%EC%A1%B0%EB%A5%BC-%EC%95%8C%EC%95%84%EB%B3%B4%EC%9E%90>
	> - <http://www.programmerinterview.com/data-structures/difference-between-stack-and-heap/>
	> - <https://goodgid.github.io/Memory-Structure/>
<hr/>   
## 메모리 구조
프로그램을 실행할 때 컴퓨터의 메모리는 데이터를  
[Code](#code)  
[Data](#data)  
[Stack](#stack)  
[Heap](#heap)  
이렇게 4가지로 분류되는 영역에 저장 공간을 할당해 사용한다.
개략적으로 그리면 아래와 같다.
![Memorystr](https://D-Gun.github.io/assets/img/post_img/memorystr.png)   
### Code
- 코드영역, 텍스트 영역이라고 불린다.
- Source code와 함수, 제어문, 상수가 저장된다.
- Hex파일이나 BIN파일 메모리다. 즉 컴파일 된 기계어로 저장된다는 말이다.
- Read Only인 변수가 저장된다.
- CPU는 이 영역에 저장되어 있는 명령어를 하나씩 가져가서 처리하게 된다.
### Data
- Static영역이라고 불리기도 한다.
- 전역변수(Global Variables), Static변수(Static Variables), 배열(Array), 구조체(Structure)가 저장된다. (_Static함수의 경우는 해당되지 않으니, 이와 혼동하지 말자._)
- 프로그램의 시작과 동시에 할당되고, 프로그램이 종료될 때까지 메모리는 소멸되지 않는다.
- 초기화된 데이터(Initialized data)는 이 영역에 저장된다.
- 초기화 되지 않은 데이터(Uninitialized data)는 BSS(Block Stated Symbol)에 저장된다. (BSS는 나중에 한번 더 정리하겠다.)
- Read-Write인 변수가 저장된다.(Static변수와 전역변수는 변경될 수 있으므로.)
### Stack
- 그렇다. 자료구조의 그 Stack과 동일한 구조다.
- push동작으로 데이터를 저장하고, pop동작으로 데이터를 인출한다.
- 후입선출(LIFO, Last In First Out)방식으로 동작한다.
- 함수의 호출과 관계되는 지역변수(Local Variables), 매개변수(Parameters)가 저장된다.
- 컴파일 시 크기가 결정된다.
- 함수의 호출과 함께 할당되고, 함수의 호출이 완료되면 소멸한다.
- 이 영역에 저장되는 함수의 호출 정보를 Stack Frame이라 한다.
- 할당은 메모리의 높은 주소->낮은 순서로 할당된다.
- 크기가 제한되어 있다.(제한된 크기는 OS에 따라 다르다)
- 이미 생성되어 있는 Stack 공간에 포인터의 위치만 바꿔주는 원리이므로, Heap 영역의 데이터보다 처리 속도가 빠르다.
- 하지만 크기의 제한으로, Stack 영역의 크기를 초과하게 되면 Heap 영역을 침범하여 오작동을 일으킬 수 있기 때문에, (Stack Overflow현상) 유연성이 부족하다.
- Stack영역에 저장되는 변수는 크기를 재설정 할 수 없다.
### Heap
- 동적 할당 영역, 사용자가 직접 할당하고 소멸 시킬 수 있다.
- 런타임에 크기가 결정된다.
- C, C++같은 Unmanaged Language의 경우 사용자가 직접 소멸 시켜줘야 한다.(_예로는, C: malloc()-free(), C++: new연산자 - delete연산자 사용_)
- Unmanaged Language에서 사용자가 이 영역의 데이터를 소멸 시키지 않았을 경우, 메모리 누수(Memory Leaking) 현상이 일어나 이후 일어날 대재앙의 씨앗을 심게 된다.
- Java, C# 같은 Managed Language 의 경우 생성된 데이터는 Garbage collection을 통해 소멸 시키기 때문에, 사용자가 직접 소멸 시킬 필요가 없다.
- 사용자에 의해서 동적으로 할당되기 때문에 크기의 재설정이 가능하므로,
	- 개체의 개수나 크기를 미리 알 수 없는 경우
	- 개체가 Stack영역의 크기를 초과한 경우<br>에 사용이 가능하다.
- 사용자가 원하는 만큼 할당하기 때문에 메모리의 효율적인 관리가 가능하다.
- 하지만 할당 작업과 해체 작업으로 인한 속도 저하가 일어나므로 Stack보다는 느리다.
- 응용 프로그램에서 이중 해제, 해제 후 블록 사용, 블록 경계를 벗어난 덮어쓰기 등 Heap 블록을 적절하게 사용하지 않을 경우 힙 손상으로 인해 속도 저하를 발생될 수 있다.
- 다중 프로세서 시스템(Multithreading System)에서 두 개 이상의 Thread가 동시에 데이터에 Access를 시도하게 되면 경합이 발생하여 속도 저하가 일어날 수 있다.
- 위 문제를 해결하기 위한 방법은 직렬화(Serialize)를 통해 해결 가능하다.
- Stack과 마찬가지로 Heap영역을 초과하는 데이터는 Stack 영역을 침범하게 된다.(Heap Overflow현상)
