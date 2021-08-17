---
layout: post
title: "[c++] c++ 클래스의 기본"
subtitle: "basic of cpp class"
categories: programming
tags: cpp study
comments: true
header-img: img/programming/cpp/0000-00-00-programming-cpp-book-cover-1.JPG
---

> `구조체`와 `클래스`에 관한 공부 내용을 다루고 있다.
>
> `윤성우의 열혈 C++` 교재를 바탕으로 작성되었다.

- 목차
  - [CPP에서의 구조체 ](#cpp에서의-구조체)
    - C++에서의 구조체 변수의 선언
    - 구조체 안에 함수 삽입하기
    - 구조체 안에 enum 상수의 선언
    - 함수는 외부로 뺄 수 있다.
  - [클래스와 객체](#클래스와-객체)
    - 클래스와 구조체의 유일한 차이점
    - 접근제어 지시자(접근제어 레이블)
    - 용어정리: 객체(Object), 멤버변수, 멤버함수
    - C++에서의 파일분할
    - 인라인 함수는 헤더파일에 함께 넣어야 한다.
  - [객체지향 프로그래밍의 이해](#객체지향-프로그래밍의-이해)
    - 객체지향 프로그래밍의 이해
    - 객체를 이루는 것은 데이터와 기능
    - 멤버변수의 상수화에 대한 논의
    - '나(me)'를 표현하는 클래스의 정의
    - 클래스 기반의 두 가지 객체생성 방법
    - 객체간의 대화 방법(Message Passing 방법)  

##  CPP에서의 구조체

---

###### 📌 C++에서의 구조체 변수의 선언

​      `C언어`에서의 구조체 변수를 선언하는 법은 아래와 같다.

```c
struct Car basicCar;
struct Car simpleCar;
```

​     💡  `struct`를 생략하려면 `typedef`선언을 추가해야 한다.



​      하지만, `C++`에서는 별도의 typedef 선언 없이도 다음과 같이 변수를 선언할 수 있다.

``` c++
Car basicCar;
Car SimpleCar;
```



###### 📌 구조체 안에 함수 삽입하기

   1. 구조체 바깥에 함수가 있는 경우.

      매개변수를 통해서 연산의 대상 정보를 전달받고 함수 내에서도 참조자 car를 대상으로 연산(출력)한다.

      ```C++
      void ShowCarState(const Car &car)
      {
          cout<<"소유자ID" <<car.gamerID<<endl;
          cout<<"연료량: " <<car.fuleGauge<<"%"<<endl;
          cout<<"현재속도: " <<car.curSpeed<<"km/s"<<endl<<endl;
      }
      ```

​           🔎  `<<`연산자를 이용한`std::endl `의 출력은 <span style="color:green">개행</span>으로 이어진다.



2. 구조체 안에 함수가 삽입된 경우.

   함수가 구조체 내에 삽입되면서 구조체 내에서 선언된 변수에 `직접접근`이 가능해져서 연산의 대상에 대한 정보가 불필요하다.

   ```C++
   void ShowCarState()
   {
       cout<<"소유자ID" <<gamerID<<endl;
       cout<<"연료량: " <<fuleGauge<<"%"<<endl;
       cout<<"현재속도: " <<curSpeed<<"km/s"<<endl<<endl;
   }
   ```

   

###### 📌 구조체 안에 enum 상수의 선언

​       보통 상수를 선언 할 때 다음과 같이 코드를 작성한다.

       ```C++
       #define ID_LEN    20
       #define MAX_SPD   200
       #define FUEL_STEP 2
       #define ACC_STEP  10
       #define BRK_STEP  10
       ```

   






​       하지만 이 상수들이 어떠한 `구조체`에게만 의미가 있다면, <u>상수들도 구조체 내에 포함시키는 것이 좋을 수 있다.</u> (✔무조건 좋다는 것은 아님!)

        ```C++
        struct Car
        {
            enum
            {
                ID_LEN  =20,
                MAX_SPD =200,
                FUEL_STEP =2,
                ACC_STRP  =10,
                BRK_STEP  =10
            };
            
            char gamerID[ID_LEN];
            int fuelGauge;
            int curSpeed;
            
            void ShowCarState(){...}
            int Accel(){...}
            void Break(){...}
        };
        ```



💡_`enum`의 선언을 구조체 내부에 삽입하는 방법이 부담스럽다면, `이름공간`을 이용해서 상수가 사용되는 영역을 명시할 수 있다._

```C++
#include <iostream>
using namespace std;

namespace CAR_CONST
{
    enum
    {
        ID_LEN  =20,
        MAX_SPD =200,
        FUEL_STEP =2,
        ACC_STRP  =10,
        BRK_STEP  =10
    };
}

struct Car
{
    char gamerID[CAR_CONST::ID_LEN];
    int fuelGauge;
    int carSpeed;
    
    void ShowCarState(){...}
    int Accel()
    {
        if(fuelGauge<=0)
            return;
        else
            fuelGauge -= CAR_CONST::FUEL_STEP;
        
        if((curSpeed+CAR_CONST::ACC_STEP)>=CAR_CONST::MAX_SPD)
        {
            curSpeed=CAR_CONST::MAX_SPD;
            return;
        }
        curSpeed += CAR_CONST::ACC_STEP;
    }
    void Break(){...}
};
```

😊 `이름공간`을 지정해서 코드를 작성했기 때문에, 문장만 봐도 이 상수가 어느 영역에서 선언되고 사용되는 상수인지 쉽게 알 수 있다. _따라서 가독성이 좋아졌다고 할 수 있다._



###### 📌 함수는 외부로 뺄 수 있다.

​      함수가 포함되어 있는 구조체를 보는 순간, 다음의 정보들이 쉽게 눈에 들어와야 <u>코드의 분석이 용이하다.</u>

​                👉 선언되어 있는 `변수정보`

​                👉 정의되어 있는 `함수정보`

​      구조체 내에 정의된 함수의 수가 많거나 그 길이가 길다면, 다음과 같이 구조체 밖으로 함수를 빼낼 필요가 있다.

    ```C++
    struct Car
    {
        .....
        void ShoeCarState();
        void Accel();
        ....
    };
    
    void Car::ShowCarState()
    {
        .....
    }
    void Car::Accel()
    {
        .....
    }
    ```

💡 함수의 `원형선언`을 구조체 안에 두고, `함수의 정의`를  구조체 밖으로 빼내는 것이다.



## 클래스와 객체

---

###### 📌 클래스와 구조체의 유일한 차이점

​     키워드 struct를 대신해서 class를 사용하면, 구조체가 아닌 클래스가 된다. 즉, 아래의 코드는 클래스의 정의이다.

```c++
class Car
{
    char gamerID[CAR_CONST::ID_LEN];
    int fuelGauge;
    int curSpeed;
    
    void ShowCarState(){....}
    void Accel(){....}
    void Break(){....}
};
```

하지만 키워드를 바꾸면 **<span style="color:purple">구조체처럼 변수를 선언하지 못한다.</span>**

```c++
Car run99={"run99",100,0}; //(x)
//클래스 내에서 선언된 함수가 아닌, 다른 영역에서 변수를 초기화 하려고 했기 때문에 불가능하다.
//클래스 내에 선언된 변수는 클래스 내에 선언된 함수에서만 접근이 가능하다.
Car run00; //(0)
```

✔ <span style = "color : green">클래스를 정의하는 과정에서 각각의 변수 및 함수의 접근 허용범위를 별도로 선언해야 한다.</span>

_이것이 키워드 struct를 이용해서 정의하는 구조체와 키워드 class를 이용해서 정의하는 클래스의 유일한 차이점이다._  

###### 📌 접근제어 지시자(접근제어 레이블)

​       👉 [public]()            어디서든 접근허용

​       👉 [protected]()     상속관계에 놓여있을 때, 유도 클래스에서의 접근허용

​       👉 [private]()          클래스 내(클래스 내에 정의된 함수)에서만 접근허용



###### 📌 용어정리: 객체(Object), 멤버변수, 멤버함수

   - 객체

   - 멤버변수 : 클래스를 구성하는(클래스 내에 선언된) 변수

     ```c++
     char gamerID[CAR_CONST::ID_LEN];
     int fuelGauge;
     int curSpeed;
     ```

     

       - 멤버함수 : 클래스를 구성하는(클래스 내에 정의된) 함수

        ```c++
        void InitMembers(char * ID, int fuel);
        void ShowCarState();
        void Accel();
        void Break();
        ```



📌 C++에서의 파일분할

- Car.h    클래스의 `선언`을 담는다.

- Car.cpp  클래스의 `정의`(멤버함수의 정의)를 담는다.  

  

📌 인라인 함수는 헤더파일에 함께 넣어야 한다.

​    `인라인 함수`의 호출문장은 컴파일러에 의해서 `인라인 함수`의 몸체로 대체 되어야 한다.

때문에 인라인 함수는 클래스의 `선언`과 동일한 파일에 저장되어서 컴파일러가 동시에 참조할 수 있게 해야 한다.



## 객체지향 프로그래밍의 이해

---

📌 객체지향 프로그래밍의 이해

​      _객체지향 프로그래밍은 현실에 존재하는 사물과 대상, 그리고 그에 따른 행동을 있는 그대로 실체화시키는 형태의 프로그래밍이다._



📌 객체를 이루는 것은 데이터와 기능

- 행동(behavior)과 상태(state)

​    _객체는 하나 이상의 상태 정보(데이터)와 하나 이상의 행동(기능)으로 구성된다._



📌 멤버변수의 상수화에 대한 논의

​    아래와 같이 클래스의 멤버변수 선언문에서 초기화까지 하는 것은 불가능하다.

```c++
const int APPLE_PRICE=1000; //(X)
```

🔎 _이 문제는 클래스의 상속 챕터의 생성자로 해결할 수 있다._



📌 나(me)를 표현하는 클래스의 정의

- 클래스는 아무런 선언이 존재하지 않을 때 private으로 간주된다.[구조체는 public]()



📌 클래스 기반의 두 가지 객체생성 방법

```c++
ClassName objname;   //일반적인 변수의 선언방식
ClassName * ptrObj=new ClassName; //동적 할당방식(힙 할당방식)
```



📌 객체간의 대화 방법(Message Passing 방법)

​      _하나의 객체가 다른 하나의 객체에게 메세지를 전달하는 방법은 함수호출을 기반으로 한다. 그래서 객체지향에서는 이러한 형태의 함수호출을 가리켜 `메세지전달(Message Passing)`이라 한다._

