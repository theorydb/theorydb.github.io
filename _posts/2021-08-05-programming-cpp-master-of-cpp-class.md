---
layout: post
title: "[c++] 클래스의 완성"
subtitle: "master of cpp class"
categories: programming
tags: cpp study
comments: true 
header-img: img/programming/cpp/0000-00-00-programming-cpp-book-cover-1.JPG
---

> `클래스`의 `중요요소` 관한 공부 내용을 다루고 있다.
>
> `윤성우의 열혈 C++` 교재를 바탕으로 작성되었다.

- 목차
  - [정보은닉(Information Hiding)](#정보은닉)
  - [캡슐화(Encapsulation)](#캡슐화)
  - [생성자(Constructor)와 소별자(Destructor)](#생성자와-소멸자)
  - [클래스와 배열 그리고 this 포인터](#클래스와-배열-그리고-this-포인터)



## 정보은닉

---

📌 정보은닉의 이해

```c++
#include <iostream>
using namespace std;

class Point
{
    public:
       int x; //x좌표의 범위는 0이상 100이하
       int y; //y좌표의 범위는 0이상 100이하
};

class Rectangle
{
    public:
       Point upleft; //멤버변수가 point type
       Point lowRight;
    
    public:
       void ShowRecInfo()
       {
           cout<<"좌 상단: "<<'['<<upLeft.x<<", ";
           cout<<upLeft.y<<']'<<endl;
           cout<<"우 하단: "<<'['<<lowRight.x<<", ";
           cout<<lowRight.y<<']'<<endl<<endl;
       }
};

int main(void)
{
    Point pos1={-2,4}; //멤버변수가 public으로 선언되면, 구조체 변수를 초기화하듯이 초기화 가능!
    Point pos2={5,9};
    Rectangle rec = {pos2,pos1};
    rec.ShowRecInfo();
    return 0;
}

//Result:  좌 상단: [5,9]  우 하단: [-2, 4]
```

⚠ 하지만 점의 좌표 값은 0~100사이여야 하는데 지켜지지 않았고, 좌 상단과 우 하단의 좌표값이 바뀐 것 같다. 



_**따라서** 이 코드는 **프로그래머의 실수**에 대한 **대책**이 하나도 준비되어 있지 않다_는 것을 알 수 있다.



**<span style = "color : blue">제한된 방법으로의 접근만 허용을 해서 잘못된 값이 저장되지 않도록 도와야 하고, 또 실수를 했을 때, 실수가 쉽게 발견되도록 해야한다.</span>**



`Point.h`   - Point header : Point class의 선언을 담는다.

```c++
#ifndef __POINT_H_
#define __POINT_H_

class Point
{
    private: //x,y를 private으로 선언해서 임의로 값이 저장되는 것을 막음.
      int x;
      int y;
    
    public:
      bool InitMembers(int xpos, int ypos);
      int GetX() const;
      int GetY() const;
      bool SetX(int xpos);
      bool SetY(int ypos);
};
#endif
      
}
```



`Point.cpp`

```c++
#include <iostream>
#include "Point.h"
using namespace std;

bool Point::InitMembers(int xpos, int ypos)
{
    if(xpos<0 || ypos<0)
    {
        cout<<"벗어난 범위의 값 전달"<<endl;
        return false;
    }
    
    x=xpos;
    y=ypos;
    return true;
}

int Point::GetX() const //const함수 : 값이 변하지 않음을 명시
{
    return x;
}

int Point::GetY() const
{
    return y;
}

bool Point::SetX(int xpos)
{
    if(0>xpos || xpos>100)
    {
        cout<<"벗어난 범위의 값 전달"<<endl;
        return false
    }
    x=xpos;
    return true;
}

bool Point::SetY(int ypos)
{
    if(0>ypos || ypos>100)
    {
        cout<<"벗어난 범위의 값 전달"<<endl;
        return false
    }
    y=ypos;
    return true;
}

//GetXXX,SetXXX으로 정의된 함수들은 엑세스 함수(access function)이다.
//멤버변수를 private으로 선언하면서 클래스 외부에서의 멤버변수 접근을 목적으로 정의되는 함수들이다.
```



📌 const 함수

​     **값변경 하지 않음을 암시**

​         👉 const 선언이 추가된 멤버함수 내에서 멤버변수의 값을 변경하는 코드가 삽입되면, 컴파일 에러가 발생한다.

​         👉 const 함수 내에서는 const가 아닌 함수의 호출이 제한된다.

C++에서는 `const`참조자를 대상으로 값의 변경 능력을 가진 함수의 호출을 허용하지 않는다.(실제 값의 변경여부에 상관없이)

_따라서 const참조자를 이용해서는 const함수만 호출이 가능하다._









## 캡슐화

---

🔎 `캡슐화`에는 기본적으로 `정보은닉`이 포함된다. 따라서 이왕이면 멤버변수가 보이지 않게 정보를 은닉해서 감싸는 것이 좋다.



```c++
#include <iostream>
using namespace std;

class SinivelCap
{
public:
    void Take() const { cout<<"콧물이 싹~ 납니다."<<endl;}
}

class SneezeCap
{
public:
    void Take() const { cout<<"재채기가 멎습니다."<<endl;}
}

class SnuffleCap
{
public:
    void Take() const { cout<<"코가 뻥 뚫립니다."<<endl;}
}

class CONTAC600
{
private:
    sin.Take();
    sne.Take();
    snu.Take();
};

class ColdPatient
{
public:
    void TakeCONTAC600(const CONTAC600 &cap) const {cap.Take();}
};

int main(void)
{
   CONTAC600 cap;
   ColdPatient sufferer;
    sfferer.TakeCONTAC600(cap);
    return 0;
}

```









## 생성자와 소멸자

---

지금까지는 객체를 생성하고 객체의 멤버변수의 초기화를 목적으로 `InitMembers`라는 이름의 함수를 정의하고 호출하였다. 하지만 `생성자`라는 것을 이용하면 객체도 생성과 동시에 초기화 할 수 있다.



📌생성자의 이해

```c++
class SimpleClass
{
private:
    int num;
public:
    SimpleClass(int n)  //생성자(constructor)
    {
        num = n;
    }
    
    int GetNum() const
    {
        return num;
    }
};
```



   - 클래스의 이름과 함수의 이름이 동일하다.

   - 반환형이 선언되어 있지 않으며, 실제로 반환하지 않는다.

      :star:객체 생성시 `딱 한번` 호출된다.

- [<span style = "color : green">생성자도 함수의 일종이니 _오버로딩_이 가능하다.</span>]()

- <span style = "color : green">생성자도 함수의 일종이니 매개변수에 '`디폴트 값`'을 설정할 수 있다.</span>

```c++
#include <iostream>
using namespace std;

class SimpleClass
{
private:
    int num1;
    int num2;
public:
    SimpleClass()
    {
        num1=0;
        num2=0;
    }
    SimpleClass(int n)
    {
        num1=n;
        num2-0;  
    }
    SimpleClass(int n1, int n2)
    {
        num1=n1;
        num2=n2;
    }
     /*
     SimpleClass(int n1=0, int n2=0)
     {
         num1=n1;
         num2=n2;
     }
     */
    
    void ShowData() const
    {
        cout<<num1<<' '<<num2<<endl;
    }
};


int main(void)
{
    SimpleClass sc1;
    sc1.ShowData();
    
    SimpleClass sc2(100); //int형 인자를 요구하는 생성자 사용
    //전역 및 지역변수의 형태로 객체 생성
    /*SimpleClass *ptr3=new SimplaeClass(100);*/ //동적할당 형태로 객체 생성
    sc2.ShowData();
    
    SimpleClass sc3(100,200);
    sc3.ShowData();
    return 0;t
}

//Compiler Result
/*
  0 0
  100 0
  100 200
  */


```

⚠ `인자가 없는` SimpleClass(){...} 로 정의된 생성자를 이용해서 객체를 생성 할 때는

아래와 같이 문장을 구성하면 안된다.

​      **SimpleClass sc1();**  (❌)  



💡 위의 문장을 **void형(인자를 받지 않는)** 생성자의 호출문으로 인정해버리면, 컴파일러는 이러한 문장을 만났을 떄, 이것이 <span style = "color : red">_객체생성문인지 함수의 원형선언인지를 구분할 수 없게 된다._</span> 그래서 이러한 유형의 문장은 객체생성이 아닌, `함수`의 `원형선언`에서만 사용하기로 약속했다.



📌멤버 이니셜라이저(Member Initializer)

​    [**멤버 이니셜라이저는 멤버변수로 선언된 객체의 생성자 호출에 활용된다.**]()

```c++
class Rectangle
{
private:
    Point upLeft;
    Point lowRight;
public:
    Rectangle(const int &x1, const int &y1, const int &x2,const int &y2);
    void ShowRecInfo() const;
};

Rectangle::Rectangle(const int &xq, const int &y1, const int &x2, const int &y2)
    :upLeft(x1,y1), lowRight(x2,y2)
{
   //empty     
}
```

🔎 **upLeft(x1,y1), lowRight(x2,y2)**가 의미하는 바는 각각 다음과 같다.

         - 객체 upLeft의 생성과정에서 x1과 y1을 인자로 전달받는 생성자를 호출하라
         - 객체 lowRight의 생성과정에서 x2와 y2을 인자로 전달받는 생성자를 호출하라.



...

_따라서,_

✔<span style ="color : green">객체 생성과정을 다음과 같이 정리 할 수 있다.</span>

    - 1️⃣<span style = "color : blue">단계</span> : 메모리 공간의 할당
   - 2️⃣<span style = "color : blue">단계</span> : 이니셜라이저를 이용한 멤버변수(객체)의 초기화
   - 3️⃣<span style = "color : blue">단계</span> : 생성자의 몸체부분 실행



그리고 생성자가 정의되어 있지 않더라도

[생성자는 반드시 호출]()된다. 우리가 `생성자`를 정의하지 않으면, `디폴트` `생성자`(default constructor)라는게 **자동으로 삽입**되어 `호출`이 된다.



📌멤버 이니셜라이저(Member Initializer)를 이용한 변수 및 const 상수(변수) 초기화

Member Initializer는 객체가 아닌 `멤버의 초기화`에도 사용할 수 있다. 

```c++
class SoSimple
{
private:
    int num1;
    int num2;
public:
    soSimple(int n1, int n2) : num(n1)
    {
        num2 = n2;
    }
    .......
};
```

_멤버변수 초기화는 생성자의 몸체에서 초기화하는 방법, 이니셜라이저를 이용하는 방법 중 선택 가능하다_



그러나 일반적으로 멤버변수 초기화는 `이니셜라이저`를 `선호`하는 편이다.

- `초기화의 대상`을 명확히 **인식** 할 수 있다.
- `성능`에 약간의 **이점**이 있다.



💡`const 변수`는 선언과 동시에 초기화 해야하기 때문에, <span style = "color : red">**const 멤버변수**도 이니셜라이저를 이용하면 **초기화**가 **가능**하다.</span>



📌 이니셜라이저의 이러한 특징은 멤버변수로 참조자를 선언할 수 있게 한다.

`const 변수`와 마찬가지로 `참조자`도 **선언과 동시에 초기화**가 이루어져야 한다.

```c++
class AAA
{
public:
    AAA()
    {
        cout<<"enmty object"<<endl;
    }
    void ShowYourName()
    {
        cout<<"I'm class AAA"<<endl;
    }
};

class BBB
{
private:
    AAA &ref; //참조자가 멤버변수로 선언, initialize을 통한 초기화 해야함
    const int &num; //const참조자 선언, 이니셜라이저를 통해 정수형 상수로도 초기화 가능.
public:
    BBB(AAA &r, const int &n)
        : ref(r),num(n)
    {
            //empty constructor body
    }
    void ShowYourName()
    {
        ref.ShowYoutName();
        cout<<"and"<<endl;
        cout<<"I ref num"<<num<<endl;
    }
};
```





📌 디폴트 생성자(Default Consturctor)

   메모리 공간의 할당 이후에 생성자의 호출까지 완료되어야 "객체"라고 할 수 있다. 즉, **객체가 되기 위해서는 반드시 하나의 생성자가 호출되어야 한다.** 

   _따라서 생성자를 정의하지 않는 클래스에는 `C++ 컴파일러`에 의해서 디폴트 생성자라는 것이 자동으로 삽입된다._

​         ✔   <span style = "color : green">디폴트 생성자는 **인자**를 **받지 않는다.**</span>

​         ✔   <span style = "color : green">모든 객체는 한번의 생성자 호출을 동반한다.</span>

​         ✔   <span style = "color : green">모든 객체는 한번의 생성자 호출을 동반한다.</span>

   ⚠단, 다음과 같이 `new 연산자`가 아닌, C언어의 malloc 함수를 대신 이용하면 생성자는 호출되지 않는다.

```c++
AAA  * ptr = (AAA*)malloc(sizeof(AAA));
```

malloc 함수호출 시, 실제로는 AAA 클래스의 크기정보만 바이트 단위로 전달되기 떄문에 생성자가 호출될 리 없다._따라서_  객체를 [<span style = "color : blue">동적으로 할당</span>하려는 경우에는 반드시 **new 연산자**를 이용해야 한다.]()

​                                    🔎 <span style = "color : blue">동적 할당</span> => `런타임 중`에 일어나도록!( 정적할당 = 컴파일 단계에서 일어남. )





📌 생성자 불일치

     ```c++
     class SoSimple
     {
     private:
         int num;
     public:
         SoSimple(int n) : num(n){}
     };
     ```

위와 같이 정의된 클래스에는 이미 생성자가 정의되어 있기 떄문에, `디폴트 생성자`가 삽입되지 않는다.

👉 `객체 생성 시`

​        SoSimple simObj1(10);                                    ⭕

​        SoSimple * simPtr1=new SoSimple(2);         ⭕



​        SoSimple simObj2;                                           ❌

​        SoSimple * simPtr2= new SpSimple;             ❌

​    ⚠ 위 두 줄의 문장에서 요구하는 생성자는 정의되지도 않고 자동으로 삽입되지도 않았기 때문에, 객체생성이  불가능하다.

​         SpSimple()  : num(0) { }

​      과 같은 형태로 생성자를 `추가`해야한다. ([오버로딩]()형태로 클래스 안에서의 생성자 추가를 의미.)





📌 private 생성자

   - 객체의 생성이 클래스의 외부에서 진행된다면 생성자는 `public`으로 선언되어야 한다.
   - 클래스 내부에서만 객체의 생성을 허용하려는 목적으로 생성자를 `private'으로 선언하기도 한다.

```c++
#include <iostream>
using namespace std;

class AAA
{
private:
    int num;
public: //클래스 외부에서는 이 생성자를 기반으로 객체를 생성.
    AAA():num(0){}
    AAA& CreateinitObj(int n) const
    {
        AAA * ptr = new AAA(n); //객체 동적생성
     
        return *ptr; 
        
        // private 생성자를 이용하영 객체를 생성 및 반환한다.
    }
    void ShowNum() const { cout<<um<<endl; }
private:
    AAA(int n)  : num(n) {}
};

int main(void)
{
    AAA base;
    base.ShowNum();
    
    AAA &obj1=base.CreateInitObj(3);
    //힙 영역에서 생성된 객체를 참조의 형태로 반환하고 있다.
    //힙에 할당된 메모리공간은 변수로 간주하여, 참조자를 통한 참조가 가능하다.
    obj1.ShowNum();
    
    AAA &obj2=base.CreateInitObj(12);
    obj2.ShowNum();
    
    delete &obj1;
    delete &obj2;
    return 0;
}
```





📌 소멸자의 이해와 활용

   `소멸자`는 `객체소멸`시 **반드시** 호출된다.

- 클래스의 이름 앞에  ` '~'`가 붙은 형태의 이름을 갖는다.
- 반환형이 선언되어 있지 않으며, 실제로 **반환하지 않는다.**
- 매개변수는 `void형`으로 선언되어야 하기 때문에 _오버로딩도, 디폴트 값 설정도 불가능하다._

```c++
~AAA(){ .... }
```



소멸자는 대개 생성자에서 할당한 리소스의 소멸에 사용된다. 생성자 내에서 new연산자를 이용해서 할당해 놓은 메모리 공간이 있다면, 소멸자에서는 delete 연산자를 이용해서 이 메모리 공간을 소멸한다.

```c++
~AAA()
{
    delete []name;
    cout<<"called destructor!"<<endl;
}
```







## 클래스와 배열 그리고 this 포인터

📌객체배열

​    <span style = "color : gray">객체로 이루어진 배열.</span>

```C++
//객체기반 배열 선언 형태
SoSimple arr[10];

//객체기반 배열 동적 할당 형태
SoSimple * ptrArr=new SoSimple[10];
```

​      ✔  <span style = "color : violet">단, 배열의 선언과정에서는 **호출할 생성자를 별도로 명시하지 못한다.**(생성자에 인자를 전달하지 못한다.)</span>

```c++
#include <iostream>
#include <cstring>
using namespace std;

class Person
{
private:
    char * name;
    int age;
public:
    Person(char *myname, int myage)
    {
        int Len=strlen(myname)+1;
        name = new char[len];
        strcpy(name, myname);
        age = myage;
    }
    person()
    {
        name = NULL;
        age = 0;
        cout<<"called Person()">>endl;
    }
    //배열 생성시 필요한 생성자 추가
    
    //원하는 데이터로의 초기화를 목적으로 정의된 함수
    void SetPersonInfo(char * myname, int myage)
    {
        name = myname;
        age = myage;
    }
    void ShowPErsonInfo() const
    {
        cout<<"이름: "<<name<<", ";
        cout<<"나이: "<<age<<endl;
    }
    ~person()
    {
        delete []name;
        cout<<"called destructor!"<<endl;
    }
};

int main(void)
{
    Person parr[3];
    char namestr[100];
    char * strptr;
    int age;
    int len;
    
    //반복문 안에서 이름과 나이정보를 입력 받아서, 객체를 초기화 하고 있음.
    for(int i=0; i<3; i++)
    {
        cout<<"이름: ";
        cin>>namestr;
        cout<<"나이: ";
        cin>>age;
        len=strlen(namestr)+1;
        strptr = new char[len];//동적할당
        strcpy(strptr, namestr);
        parr[i].SetPersonInfo(strptr, age); //함수를 이용해서 내부 멤버변수 값 변경
    }
    parr[0].ShowPersonInfo();
    parr[1].ShowPersonInfo();
    parr[2].ShowPersonInfo();
    return 0;
}
```





📌 객체 포인터 배열

   <span style = "color : gray">객체의 주소 값 저장이 가능한 포인터 변수로 이루어진 배열.</span>

```c++
#include <iostream>
#include <cstirng>
using namespace std;

class Person
{
    //바로 위의 클래스와 동일하여 생략
}

int main(void)
{
    Person * parr[3]; //포인터 배열 선언
    char namestr[100];
    int age;
    
    for(int i = 0; i<3 ; i++)
    {
        cout<<"이름: ";
        cin>>namestr;
        cout<<"나이: ";
        cin>>age;
        parr[i]= new Person(namestr, age); //객체 생성후, 객체 주소값을 배열에 저장
    }
    parr[0]->ShowPersonInfo();
    parr[1]->ShowPersonInfo();
    parr[2]->ShowPersonInfo();
    
    //총3회에 걸쳐서 new연산을 진행했으니, 총 3회에 걸쳐서 delete연산을 진행해야 한다.
    delete parr[0];
    delete parr[1];
    delete parr[2];
    return 0;
}
```





📌 this 포인터의 이해와 활용

   - 객체 자신의 주소 값을 의미
   - 주소 값과 자료형이 정해져 있지 않은 포인터.

```c++
#include <iostream>
using namespace std;

class TwoNumber
{
private:
    int num1;
    int num2;
public:
    TwoNumber(int num1, int num2)
    {
        this->num1=num1;
        this->num2=num2;
    }
    
}
```

​      👉 객체 내에 `private`으로 선언한 변수와 <u>생성자의 매개변수</u>의 이름이 같은 경우에 `this`포인터를 사용하여 접근 할 수 있다.





📌 [Self-Reference]()의 반환

​     Self-Reference: 객체 자신을 참조할 수 있는 참조자

```c++
#include <iostream>
using namespace std;

class SelfRef
{
private:
    int num;
public:
    SelfRef(int n) : num(n)
    {
        cout<<"객체생성"<<endl;
    }
    //반환형이 참조현 SelfRef&
    //객체가 자신을 참조할 수 있는 '참조 정보(값)'가 반환
    SelfRef& Adder(int n)
    {
        num+=n;
        return *this;
    }
    SelfRef& ShowTwoNumber()
    {
        cout<<num<<endl;
        return *this;
    }
};

int main(void)
{
    SelfRef obj(3);
    SelfRef &ref=obj.Adder(2);
    
    obj.ShowTwoNumber();
    ref.ShowTwmNumber();
    //참조자 ref는 객체 obj참조.
    ref.Adder(1).ShowTwmNumber().Adder(2).ShowTwoNumber();
    //Adder와 ShowTwoNumber가 객체의 참조값을 반환하기 떄문에 구성 가능한 문장!
    return 0;
}
```



📌 참조의 정보(참조 값)에 대한 이해

```c++
int main(void)
{
    int num=7;
    int &ref=num; //변수 num을 참조할 수 있는 참조의 정보가 전달된다.
}
```

<span style = "color : violet">"변수 num을 참조할 수 있는 참조 값이 참조자 `ref`에 전달되어, `ref`가 변수 num을 참조하게 된다"</span>

