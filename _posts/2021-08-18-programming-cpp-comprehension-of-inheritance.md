---
layout: post
title: "[c++] 상속(Inheritance)의 이해"
subtitle: "Comprehension of Inheritance"
categories: programming
tags: cpp study
comments: true
header-img: img/programming/cpp/0000-00-00-programming-cpp-book-cover-1.JPG
---

> `상속`에 관한 내용을 다룬다.
>
> `윤성우의 열혈 C++` 교재를 바탕으로 작성되었다.

- 목차
  - [상속에 들어가기에 앞서](#상속에-들어가기에-앞서)
  - [상속의 문법적인 이해](#상속의-문법적인-이해)
  - [protected 선언과 세 가지 형태의 상속](#protected-선언과-세-가지-형태의-상속)
  - [상속을 위한 조건](#상속을-위한-조건)

---



## 상속에 들어가기에 앞서

👀 상속은 특히 적용이 중요한 문법이다.  따라서, 확실히 이해하고 적절한 때에 선별적으로 적용할 수 있도록 노력하자!😉




📌 상속(Inheritance)의 이해를 위한 접근 방식 제안

​       ✔<span style = "color :green">**1단계** : 문제의 제시</span>

​                상속과 더불어 다형성의 개념을 적용해야만 해결 가능한 문제를 먼저 제시한다.

​       ✔<span style = "color :green">**2단계** : 기본 개념 소개</span>

​                 상속의 문법적 요소를 하나씩 소개해 나간다. 그리고 그 과정에서 앞서 제시한 문제의 해결책을 함께 고민한다.

​       ✔<span style = "color :green">**3단계** : 문제의 해결</span>

​                  처음 제시한 문제를, 상속을 적용하여 해결한다.✨



📌 상속에 대한 새로운 관점의 이해

​       _<span style = "color:gray">과거에는 "기존에 정의해 놓은 클래스의 재활용을 목적으로 만들어진 문법적 요소가 상속이다."라는 관점으로 상속을 바라보았다.</span>_



📌 문제 제시를 위한 시나리오 도입

`상속의 이해를 위한 예시 클래스 스크립트.cpp`

​    🔎  **가상의 문제를 제시** 👉  A회사가 운영하는 '급여관리 '시스템이고, 직원의 근무형태는 '정규직'하나이다. 이 시스템은 정규직 직원을 관리하기 위한 형태로 설계되었다.

```c++
class PermanentWorker //'정규직'이라는 객체: 데이터적 성격이 강하다.
{
private:
    char name[100];
    int salary; //매달 지불해아 하는 급여액
public:
    PermanentWorker(char* name, int money)
        :salary(money)
    {
       strcpy(this->name name);     
    }
    int GetPay() const
    {
        return salary;
    }
    void ShowSalaryInfo() const
    {
        cout<<"name: "<<name<<endl;
        cout<<"salary: "<<GetPay()<<endl<<endl;
    }
};
```

```c++
class EmployeeHandler //handler->기능적 성격이 강하다.
{
private:
    PermanentWorker* empList[50];
    int empNum;
public:
    EmployeeHandler():empNum(0)
    { }
    void AddEmployee(PermanentWorker* emp)//정규직 class를 인수로 받음
    {
        for(int i=0; i<empNum;i++)
            empList[i]->ShowSalaryInfo();
    }
    void ShowTotalSalary() const
    {
        int sum=0;
        for(int i=0; i<empNum; i++)
            sum+=empList[i]->GetPay();
        cout<<"salary sum: "<<sum<<endl;
    }
    ~EmployeeHandler()
    {
        for(int i=0; i<empNum; i++)
            delete empList[i];
    }
}
```

👉 `class EmployeeHandler`는 기능적 성격이 강한데, 이렇게 기능의 처리를 실제로 담당하는 클래스를 가리켜 **'컨트롤(control) 클래스'**또는 **'핸들러(handler)클래스'**라 한다.




`위의 두 클래스를 기반으로 작성된 main함수.cpp`

```c++
int main(void)
{
    // 직원관리를 목적으로 설계된 컨트롤 클래스의 객체 생성
    EmployeeHandler handler;
    
    // 직원 등록
    handler.AddEmployee(new PermanentWorker("Kim",1000));
    handler.AddEmployee(new PermanetWorker("Lee",1500));
    handler.AddEmployee(new PermanentWorker("Jun", 2000));
    
    // 이번 달에 지불해야 할 급여의 정보
    handler.ShowAllSalaryInfo();
    
    // 이번 달에 지불해야 할 급여의 총합
    handler.ShowTotalSalary();
    return 0;
}
```


📌 문제의 제시

​       🔎  앞서 만든 시스템을 사용하던 A회사가 다음과 같은 요구를 했다.

>   " 부서가 세분화 되어, 직원이 늘면서 직원의 고용형태가 달라졌다. 영업직,임시직이 추가 되었다."

👉 단순히 종류가 늘은 것이 아닌 고용직의 급여, 영업직의 급여, 임시직의 급여가 각각 다른 계산방식으로 적용되어야 한다.

 _이러한 문제는 `클래스`만 늘린다고 해결 되는 것이아니다. 각각의 클래스에서의 함수, 그리고 그것들을 관리하는 배열들도 각각 생성해야한다._

<p>

🤔 <span style = "color : red">결과적으로 전체 코드를 바꿔야한다.</span>


---



## 상속의 문법적인 이해

📌 상속이란?

> UnivStudent 클래스가 Person 클래스를 상속한다.

   👉  `UnivStudent `클래스가 `Person `클래스를 상속하게 되면, UnivStudent 클래스는 Person 클래스가 지니고 있는 모든 멤버를 물려받는다. 즉, UnivStudent 객체에는 UnivStudent 클래스에 선언되어 있는 멤버뿐만 아니라 Person 클래스에 선언되어 있는 멤버도 존재하게 된다.



📌상속의 방법과 그 결과

`class Person 예시.cpp`

```c++
class Person
{
private:
    int age; //나이
    char name[50]; //이름
public:
    Person(int myage, char * myname) : age(myage)
    {
        strcpy(name, myname);
    }
    void WhatYourName() const
    {
        cout<<"My name is "<<name<<endl;
    }
};
```

`class Univstudent 예시.cpp`

```c++
class UnivStudent : public Person //Person 클래스의 public 상속을 의미함
{
private:
    char major[50]; // 전공과목
public:
    UnivStudent(char * myname, int myage, char * mymajor)
        : Person(myage, myname)
        {
            strcpy(major, mymajor);
        }
    void WhoAreYou() const
    {
        WhatYourName();
        HowOldAreYou(); //클래스 내부에 정의 되어 있지 않아도 상속받은 Person클래스의 멤버함수이기 떄문에 호출이 가능하다.
        cout<<"My major is"<<major<<endl<<endl;
    }
};
```

💡 `상속`을 하게 되면  **상속의 대상이 되는 클래스의 멤버**까지도 **객체 내**에 **포함**이 된다.



📌 상속받은 클래스의 생성자 정의

```c++
UnivStudent(char*myname, int myage, char * mymajor)
    : Person(myage, myname) //member initialize, Person의 멤버를 초기화 하기 위한 인자의 전달 까지 요구하고 있다.
{
   strcpy(major, mymajor); //멤버변수에 복사     
}
```

❔ **UnivStudent의 생성자는 Person 클래스의 멤버까지 초기화해야 할 의무가 있을까?**

​      UnivStudent 객체가 생성되면, 그 객체 안에는 다음의 멤버변수가 존재하게 된다.

     -  Person의 멤버변수  : age, name
     -  UnivStudent의 멤버변수:  major

​       _따라서, UnivStudent 생성자는 Person 클래스의 멤버까지 초기화해야할 의무가 있다._

 💡 <span style = "color :goldenrod">UnivStudent 생성자가 Person 클래스의 생성자를 호출해서 Person 클래스의 멤버를 초기화 하는 것이 좋다!😉</span>






📌 상속관련 완전한 예제의 확인 및 실행

```c++
#include <iostream>
#include <cstring>
using namespace std;

class Person
{
private:
    int age; //나이
    char name[50]; //이름
public:
    Person(int myage, chsr * myname) : age(myage)
    {
        strcpy(name, myname);
    }
    void WhatYourName() const
    {
        cout<<"My name is "<<name<<endl;
    }
    void HowOldAreYou() const
    {
        cout<<"I'm"<<age<<" years old"<<endl;
    }
};

class UnivStudent : public Person
{
private:
    char major[50]; //전공과목
public:
    UnivStudent(char * myname, int myage, char * mymajor)
        : Person(myage, myname) //Person 객체의 'private'멤버이기 떄문에 public 함수를 통해 간접적으로 접근해야 한다.
    {
      strcpy(major, mymajor);    
    }
    void WhoAreYou() const
    {
        WhatYourName();
        HowOldAreYou();
        cout<<"My major is "<<major<<endl<<endl;
    }               
};

int main(void)
{
    UnivStudent ustd1("Lee", 22, "Computer eng.");
    ustd1.WhoAreYou();
    
    UnivStudent ustd2("Yoon", 21, "Electronic eng.");
    ustd2.WhoAreYou();
    return 0;
}
```

> ❔ UnivStudent 클래스의 멤버함수(또는 생성자) 내에서는 Person 클래스에 Private으로 선언된 멤버변수 age와 name에 접근이 가능한가?

💡 **접근 제한의 기준은 [클래스]() 이다.** 클래스 외부에서는 private 멤버에 접근이 불가능하다. 따라서 UnivStudent의 멤버함수 내에서는 Person의 멤버변수에 `직접접근`이 불가능하다.

​    ✔ `private`으로 선언된 멤버도 상속이 이루어 진다.

​    ✔ `직접접근`이 불가능 하기 때문에, Person클래스 내에 있는 `public함수`를 통해서 [간접적으로]() 접근 해야 한다. 👉   <span style = "color : orange">_**정보의 은닉**은 하나의 객체 내에서도 진행이 된다._ </span>








📌  용어의 정리

|       Person       |  ↔   |     UnivStudent      |
| :----------------: | :--: | :------------------: |
|    상위 클래스     |  ↔   |      하위클래스      |
| 기초(base) 클래스  |  ↔   | 유도(derived) 클래스 |
| 슈퍼(super) 클래스 |  ↔   |   서브(sub) 클래스   |
|    부모 클래스     |  ↔   |     자식 클래스      |

👀 `기초 클래스`와 `유도 클래스`라는 말이 일반적으로 사용된다.




📌 유도 클래스의 객체 생성과정

```c++
#include <iostream>
using namespace std;

class SoBase
{
private:
    int baseNum;
public:
    SoBase() : baseNum(20)
    {
        cout<<"SoBase()"<<endl;
    }
    SoBase(int n) :baseNum(n)
    {
        cout<<"SoBase(int n)"<<endl;
    }
    void ShowBaseData()
    {
        cout<<baseNum<<endl;
    }
};

class SoDerived : public SoBase
{
private:
    int derivNum;
public:
    SoDerived() : derivNum(30) //기초 클래스의 생성자에 대한 언급이 없다.
    {
        cout<<"SoDerived()"<<endl;
    }
    SoDerived(int n) : derivNum(n) //기초 클래스의 생성자에 대한 언급이 없다.
    {
        cout<<"SoDerived(int n)"<<endl;
    }
    SoDerived(int n1, int n2): SoBase(n1), derivNum(n2) //n1을 인자로 받는 기초클래스의 생성자를 직접 명시하고 있다.
    {
        cout<<"SoDerived(int n1, int n2)"<<endl;
    }
    void ShowDerivData()
    {
        ShowBaseData();
        cout<<derivNum<<endl;
    }
};

int main(void)
{
    cout<<"case1.... "<<endl;
    SoDerived dr1;
    dr1.ShowDerivData();
    cout<<"----------"<<endl;
    cout<<"case2..... " <<endl;
    SoDerived dr2(12);
    dr2.ShowDerivData();
    cout<<"----------"<<endl;
    cout<<"case3..... "<<endl;
    SoDerived dr3(23, 24);
    dr3.ShowDerivData();
    return 0;
}
```

💡 `유도 클래스의 객체생성 과정`에서 **기초 클래스의 생성자**는 <span style = "color : red">100% </span>호출된다.

💡 유도 클래스의 생성자에서 [기초 클래스의 생성자 호출을 명시히지 않으면,]() 기초 클래스의 `void 생성자가 호출`된다.



✔ <span style = "color : green">`유도 클래스`의 객체 생성과정에서는 생성자가 `두번` 호출된다.(기초 클래스의 생성자 & 유도 클래스의 생성자 )</span>



> [클래스의 멤버는 해당 클래스의 생성자를 통해서 초기화 해야 한다.]()






📌 유도 클래스 객체의 소멸과정

```c++
#include <iostream>
using namespace std;

class SoBase
{
private:
    int baseNum;
public:
    SoBase(int n) :baseNum(n)
    {
        cout<<"SoBase() : "<<baseNum<<endl;
    }
    ~SoBase()
    {
        cout<<"~SoBase() : "<<baseNum<<endl;
    }
};

class SoDerived : public SoBase
{
private:
    int derivNum;
public:
    SoDerived(int n) : SoBase(n), derivNum(n)
    {
        cout<<"SoDerived() : "<<derivNum<<endl;
    }
    ~SoDerived()
    {
        cout<<"~SoDerived() : "<<derivNum<<endl;
    }
};

int main(void)
{
    SoDerived drv(15);
    SoDerived drv(27);
    return 0;
}

//result
/*
SoBase() : 15
SoDerived() :15
SoBase() :27
SoDerived(): 27
~SoDerived(): 27
~SoBase() :27
~SoDerived() :15
~SoBase() : 15
*/
```

💡 유도 클래스의 객체가 소멸될 때에는, 유도 클래스의 소멸자가 실행되고 난 다음에 기초 클래스의 소멸자가 실행된다.

💡 스택에 생성된 객체의 소멸순서는 생성순서와 **반대**이다.



✔<span style = "color : green">`생성자`에서 **동적 할당**된 `메모리 공간`은 `소멸자`에서 **해제**한다.</span>

```c++
#include <iostream>
#include <cstirng>
using namespace std;

class Person
{
private:
    cahr * name;
public:
   Person(char * myname)
   {
       name = new char[strlen(myname)+1];
       strcpy(name, myname);
   }
   ~Person()
   {
       delete []name; //소멸자에서 생성자에서 할당한 메모리 공간을 해제해도록 정의하였다.
   }    
   void WhatYourName() const
   {
       cout<<"My name is "<<name<<endl;
   }
};

class UnivStudent : public Person
{
private:
    char * major;
public:
    UnivStudent(char * myname, char * mymajor)
        :Person(myname)
    {
       major = new char[strlen(mymajorj)+1];
       strcpy(major, mymajor);
    }
    ~UnivStudent()
    {
        delete []major; //유도 생성자에서는 자신의 생성자에 할당된 메모리 공간에 대한 해제만 책임지고 있다. 기초 클래스의 소멸자가 호출이 되면서 기초 클래스의 생성자에서 할당한 메모리 공간을 해제하기 떄문이다.
    }
    void WhoAreYou() const
    {
        WhatYourName();
        cout<<"My major is "<<major<,endl<<endl;
    }                  
};

int main(void)
{
    UnivStudent st1("Kim", "Mathmatics");
    st1.WhoAreYou();
    UnivStudent st2("Hong", "Physics");
    st2.WhoAreYou();
    return 0;
}

```

---




## protected 선언과 세 가지 형태의 상속

📌 protected로 선언된 멤버가 혀용하는 접근의 범위

​     🔎 **c++의 접근제어 지시자** :  `private `, `protected` , `public` 

​     🔎 **허용하는 접근 범위** :  `private ` < `protected` < `public` 

```c++
class Base
{
private:
    int num1;
protected:
    int num2;
public:
    int num3;
    void ShowData()
    {
        cout<<num1<<", "<<num2<<", "<<num3;
    }
};

class Derived : public Base
{
public:
    void ShowBaseMember()
    {
        cout<<num1; //compile error
        cout<<num2; //compile OK
        cout<<num3; //compile OK
    }
}
```

💡 `protected`로 선언된 멤버변수는 이를 상속하는 유도 클래스에서 접근이 가능하다.

(반면에, `private`은 유도 클래스에서는 접근이 불가능하다.)








📌 세가지 형태의 상속

```c++
class Derived : public Base
{
    .....
}
class Derived : protected Base
{
    .....
}
class Derived : private Base
{
    .....
}
```








📌 **protected** 상속

```c++
class Base
{
private:
    int num1;
protected:
    int num2;
public:
    int num3;
};

class Derived :  protected Base
{
  //empty!  
};
```

`protected`상속이 의미하는 바 👉 _protected 보다 접근 범위가 넓은 멤버는 protected로 변경시켜서 상속하겠다._

_따라서 클래스는 다음과 같은 형태가 된다.

```c++
class Derived : protected Base
{
접근불가: //num1은 private이기 때문에 유도 클래스에서는 아예 접근이 불가능하다.
    int num1;
protected:
    int num2;
public:
    int num3;
};
```








📌 **private**  상속

```c++
class Base
{
private:
    int num1;
protected:
    int num2;
public:
    int num3;
};

class Derived :  private Base
{
  //empty!  
};
```

`private`상속이 의미하는 바 👉 _private 보다 접근 범위가 넓은 멤버는 private로 변경시켜서 상속하겠다._ 

_따라서 `protected`와 `public`을 변경시켜, 클래스는 다음과 같은 형태가 된다.

```c++
class Derived : private Base
{
접근불가: //num1은 private이기 때문에 유도 클래스에서는 아예 접근이 불가능하다.
    int num1;
private: 
    int num2;
private: 
    int num3;
};
```

👉 num2와 num3는Derived 클래스 내에서만 접근이 가능한 멤버가 된다.








🤔 만약 다른 클래스가 Derived 클래스를 다음과 같이 상속한다면..............

```c#
class DeDerived : public Derived
{
    //empty!
};
```

```c++
class DeDerived : public Derived
{
접근불가: 
    int num1;
접근불가: 
    int num2;
접근불가: 
    int num3;
};
```

👉 `private 상속이 이뤄진 클래스를 다시 상속할 경우` , 멤버함수를 포함하여 모든 멤버가 '접근불가'가 되기 때문에 사실상 의미 없는 상속이 되고 만다.






📌 **protected** 상속

> ✔ private을 제외한 나머지는 그냥 그대로 상속한다.
>
> ✔ C++의 상속은 public 상속만 있다고 생각해라.

---


## 상속을 위한 조건

📌 상속을 위한 기본 조건인 **IS-A** 관계의 성립

- 전화기 ➡ 무선 전화기 ( 무선 전화기는 일종의 전화기이다.= 무선 전화기 is a 전화기)
- 컴퓨터 ➡ 노트북 컴퓨터 ( 노트북 컴퓨터는 일종의 컴퓨터이다.= 노트북 컴퓨터 is a 컴퓨터)

✔ 상속관계가 성립하려면 기초 클래스와 유도 클래스간에 `IS-A`관계가 성립해야 한다.

`ISAInheritance.cpp 예제`

```c++
#include <iostream>
#include <cstrng>
using namespace std;

class Computer
{
private:
    char owner[50];
public:
    Computer(char * name)
    {
        strcpy(owner, name);
    }
    void Calculate()
    {
        cout<<"요청 내용을 계산합니다."<<endl;
    }
};

class NotebookComp : ppublic Computer
{
privatet:
    int Battery;
public:
    NoteBookComp(char * name, int initChag)
        :Computer(name), Battery(initChag)
    { }
    void Charging() { Battery +=5;}
    void UseBattery() {Battery -=1;}
    void MovinCal()
    {
        if(GetBatteryInfo()<1)
        {
            cout<<"충전이 필요합니다."<<endl;
            return;
        }
        cout<<"이동하면서 ";
        Calculater();
        UseBattery();
    }
    int GetBatteryInfo() { return Battery; }
};

class TabletNotebook : public NotebookComp
{
private:
    char regstPenModel[50];
public:
    TabletNotebook(char * name, int initChag, char * pen)
        : NotebookComp(name, initChag)
    {
        strcpy(regstPenModel, pen);    
    }
    void Write(char * penInfo)
    {
        if(GetBatteryInfo()<1)
        {
            cout<<"충전이 필요합니다."<<endl;
            return;
        }
        it(strcmp(regstPenModel,  penInfo)!=0)
        {
            cout<<"등록된 펜이 아닙니다.";
            return;
        }
        cout<<"필기 내용을 처리합니다."<<endl;
        UseBattery();
    }
};

int main(void)
{
    NotebookComp nc("이수종", 5);
    TabletNotebook tn("정수영", 5, "ISE-241-242");
    nc.MovingCal();
    tn.Write("ISE-241-242");
    return 0;
}
```








📌 **HAS-A** 관계도 상속의 조건은 되지만 복합 관계로 이를 대신하는 것이 일반적이다.

   ✔ `소유`의 관계

`HASInheritance.cpp 예제` 

HAS-A 관계를 상속으로 표현한 예제이다.

```c++
#include <iostream>
#include <cstring>
using namespace std;

class Gun
{
private:
    int bullet; //장전된 총알의 수
public:
    Gun(int bnum) : bullet(bnum)
    { }
    void Shot()
    {
        cout<<"BBANG!"<<endl;
        bullet--;
    }
};

class Police : public Gun
{
private:
    int handcuffs; //소유한 수갑의 수
public:
    Police(int bnum, unt bcuff)
        : Gun(bnum), handcuffs(bcuff)
    { }
    void PutHandcuff()
    {
        cout<<"SNAP!"<<endl;
        handcuffs--;
    }
};

int main(void)
{
    Police pman(5,3); //총알 5, 수갑 3
    pman.Shot();
    pman.PutHandcuff();
    return 0;
}

```

✏

`HASComposite.cpp 예제`

```c++
# include <iostream>
# include <cstirng>
using namespace std;

class Gun
{
private:
    int bullet; //장전된 총알의 수
public:
    Gun(int bnum) : bullet(bnum)
    { }
    void Shot()
    {
        cout<<"BBANG!"<<endl;
        bullet--;
    }
};

class Police
{
private:
    int handcuffs; // 소유한 수갑의 수
    Gun * pistol; //소유하고 있는 권총
public:
    Police(int bnum, int bcuff)
        : handcuffs(bcuff)
        {
            if(bnum>0)
                pistol=new Gun(bnum);
            else
                pistol=NULL;
        }
    void PutHandcuff()
    {
        cout<<"SNAP!"<<endl;
        handcufs--;
    }
    void Shot()
    {
        if(pistol == NULL)
            cout<<"Hut BBANG!"<<endl;
        else
            pistol ->Shot();
    }
    ~Police()
    {
        if(pistol !=NULL)
            delete pistol;
    }
};

int main(void)
{
    Police pman1(5, 3);
    pman1.Shot();
    pman1.PutHandcuff();
    
    Police pman2(0, 3); //권총을 소유하지 않은 경찰
    pman2.Shot();
    pman2.PutHandcuff();
    return 0;
}
```

💡  앞서 **HAS-A**관계를 상속으로 표현한 경우

      - 권총을 소유하지 않은 경찰을 표현해야 함
      - 경찰이 권총과 수갑뿐만 아니라, 전기봉도 소유하기 시작함.

과 같은 요구사항들을 반영하기가 쉽지 않다.



_상속으로 묶인 두 개의 클래스는 강한 연관성을 띤다._

_상속은 IS-A 관계의 표현에 매우 적절하다. 그리고 경우에 따라서는 HAS-A 관계의 표현에도 사용될 수 있으나, 이는 프로그램의 변경에 많은 제약을 가져다 줄 수 있다._

