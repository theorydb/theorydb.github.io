---
layout: post
title: "[c++] 상속과 다형성"
subtitle: "Inheritance and Polymorphism"
categories: programming
tags: cpp study
comments: true
header-img: img/programming/cpp/0000-00-00-programming-cpp-book-cover-1.JPG
---

> `상속`과 `다형성`에 관한 내용을 다룬다.
>
> `윤성우의 열혈 C++` 교재를 바탕으로 작성되었다.

- 목차
  - 객체 포인터의 참조관계
  - 가상함수(Virtual Function)
  - 가상 소멸자와 참조자의 참조 가능성



---

## 객체 포인터의 참조관계

📌 객체 포인터 변수 : 객체의 주소 값을 저장하는 포인터 변수

`클래스를 기반으로도 포인터 변수를 선언할 수 있다.`

```c++
Person * ptr; //포인터 변수 선언
ptr=new Person(); //포인터 변수의 객체 참조
```

​    💡  <span style = "color : goldenrod">Person형 포인터는 Person 객체뿐만 아니라, Person을 상속하는 `유도 클래스`의 객체도 가리킬 수 있다.</span>

```c++
class Student : public Person
{
    .....
};

Person * ptr=new Student();

class PartTimeStudent : public Student
{
    ......
};

Person * ptr = new PartTimeStudent();
Student * ptr = new PartTimeStudent();
```

   ✨ 객체 포인터의 다음 특성은, 상속의 `IS-A`관계를 통해서 논리적으로 이해가 가능하다.

> C++에서, AAA형 포인터 변수는 AAA 객체 또는 AAA를 직접 혹은 간접적으로 상속하는 모든 객체를 가리킬 수 있다(객체의 주소 값을 저장 할 수 있다.)

​        👉 _유도 클래스의 객체를 기초 클래스의 일종으로 간주하기 때문이다._

.

.

📌 함수 오버라이딩

> EmployeeHandler 클래스가 저장 및 관리하는 대상이 Employee 객체가 되게 하면, 이후에 Employee 클래스를 직접 혹은 간접적으로 상속하는 클래스가 추가되었을 때, EmployeeHandler 클래서에는 변화가 발생하지 않는다.

```c++
class TemporaryWorker : public Employee
{
private:
    int workTime; // 이 달에 일한 시간의 합계
    int payPerHour; // 시간당 급여
public:
    TemporaryWorker(char * name, int pay)
        : Employee(name), workTime(0), payPerHour(pay)
     { }
    void AddWorkTime(int time)
    {
        workTime +=time;
    }
    int GetPay() const //이 달의 급여
    {
        return workTime*payPerHour;
    }
    void ShowSalaryInfo() const
    {
        ShowYourName();
        cout<<"salary: "<<GetPay()<<endl<<endl;
    }
};

class SalaryWorker: public PermanentWorker
{
private:
    int salesResult; // 월 판매실적
    double bonusRatio; // 상여금 비율
public:
    SalesWorker(char * name, int money, double ratio)
         : PermanentWorker(name, money), salesResult(0), bonusRatio(ratio)
    { }
    void AddSalesResult(int calue)
    {
        salesResult+=value;
    }
    int GetPay() const
    {
        return PermanentWorker::GetPay() //PermanentWorker의 GetPay 함수 호출
            + (int)( salesResult*bonusRatio);
    }
    void ShowSalaryInfo() const //PermanentWorker 클래스의 ShowSalaryInfo와 동일!
    {
        ShowYourName();
        cout<<"salary: "<<GetPay()>>endl<<endl; //SalesWorker의 GetPay함수가 호출됨
    }
}
```

🔎 <span style = "color : dodgerblue">**함수 오버라이딩**</span>

> `PermanentWorker 클래스`에도 `GetPay 함수`와 `ShowSalaryInfo 함수`가 있는데, 유도 클래스인 `SalesWorker 클래스`에서도 동일한 이름과 형태로 두 함수를 정의했다.

`함수 오버라이딩`이 되면, 오버라이딩 된 기초 클래스의 함수는, 오버라이딩을 한 유도 클래스의 함수에 **가려진다**.

.

`PermanentWorker::GetPay()` 👉 **오버 라이딩** 된 기초 클래스의 GetPay 함수를 호출하는 구문이다.

.

```c++
void ShowSalaryInfo() const //PermanentWorker 클래스의 ShowSalaryInfo와 동일!
    {
        ShowYourName();
        cout<<"salary: "<<GetPay()>>endl<<endl; //SalesWorker의 GetPay함수가 호출됨
    }
```

❔ PermanentWorker 클래스의 ShowSalaryInfo와 동일한데 오버라이딩 한 이유.

`PermanentWorker 클래스`의 `ShowSalaryInfo 함수 내`에서 호출되는 `GetPay 함수`는 [`PermanentWorker 클래스`에 정의된 `GetPay 함수`의 호출로 이어진다.]() 

_따라서 SalesWorker 클래스에 정의된 GetPay 함수가 호출되도록 SalesWorker 클래스에 별도의 ShowSalaryInfo 함수를 정의해야만 한다._

.

.

✨**함수 오버라이딩 VS 함수 오버로딩**✨

```
기초 클래스와 동일한 이름의 함수를 유도 클래스에서 정의한다고 해서 무조건 함수 오버라이딩이 되는 것은 아니다. 매개변수의 자료형 및 개수가 다르면, 이는 함수 오버로딩이 되어, 전달되는 인자에 따라서 호출되는 함수가 결정된다. 즉, 함수 오버로딩은 상속의 관계에서도 구성이 될 수 있다.
```

.

.

.

---

## 가상함수

📌 기초 클래스의 포인터로 객체를 참조하면,

```c++
class Base
{
public:
    void BaseFuc(){ cout<<"Base Function<<endl"}
};

class Derived : public Base
{
public:
    void DerivedFunc() { cout<<"Derived Function"<<endl;}
};

int main(void)
{
    Base * bptr=new Derived(); //컴파일 OK!
    bptr-> DerivedFunc(); //컴파일 Error!
}
```

🔎`bptr-> DerivedFunc();`의 컴파일 에러 원인!

   bptr이 `Base형` 포인터이기 떄문이다.

[C++ 컴파일러는 포인터 연산의 가능성 여부를 판단 할 때, 포인터의 자료형을 기준으로 판단하지, 실제 가리키는 객체의 자료형을 기준으로 판단하지 않는다.]()

.

📌 함수의 오버라이딩과 포인터 형 

```c++
#include <iostream>
using namespace std;

class First
{
public:
    void MyFunc() { cout<<"FirstFunc"<<endl; }
};

class Second: public First
{
public:
    void MyFunc() { cout<<"SecondFunc"<<endl;}
};

class Third: public Second
{
public:
    void MyFunc() { cout<<"ThisFunc"<<endl;}
};

//위 3개의 클래스가 상속관계로 연결되어 있으며, 모두 MyFunc 함수를 통해서 오버라이딩 관계를 형성하고 있다.

int main(void)
{
    Third * tptr=new Third();
    Second * sptr=tptr;
    First * fptr=sptr;
    
    fptr->MyFunc();
    sptr->MyFunc();
    tptr->MyFunc();
    delete tptr;
    return 0;
}
```

.

📌가상함수(Virtual Function)

> 함수를 오버라이딩을 했다는 것은, 해당 객체에서 호출되어야 하는 함수를 바꾼다는 의미인데, **포인터 변수의 자료형에 따라서 호출되는 함수의 종류가 달라지는 것**은 문제가 있어보인다.

👉 가상함수의 선언은 `virtual 키워드`의 선언을 통해 이루어진다.

가상함수가 선언되고 나면, 이 함수를 오버라이딩 하는 함수도 가상함수가 된다.

```c++
class First
{
public:
    virtual void MyFunc() { cout<<"FirstFunc"<<endl;}
};

//이미 MyFunc함수가 virtual로 선언되어서, 굳이 유도 클래스의 함수에 virtual 선언을 추가하지 않아도 가상함수가 된다.
class Second: public First
{
public:
    virtual void MyFunc() { cout<<"SecondFunc"<<endl;}
};

class Third: public Second
{
public:
    virtual void MyFunc() { cout<<"ThisFunc"<<endl;}
};

int main(void)
{
    Third * tptr = new Third();
    Second * sptr = tptr;
    First * fptr=sptr;
    
    fptr->MyFunc();
    sptr->MyFunc();
    tptr->Myfunc();
    delete tptr;
    return 0;
}
```

.

.

.

📌 순수 가상함수(Pure Virtual Function)와 추상 클래스(Abstract Class)

`기초클래스(Base Class)`👉 객체 생성이 목적이 아님

```c++
class Employee
{
private:
    char name[100];
public:
    Employee( char * name ){....}
    void ShowYourName() const { .... }
    virtual int GetPay() const
    {
        return 0;
    }
    virtual void ShowSalaryInfo() const
    { }
};                                                                          
```

`Employee * emp=new Employee("Lee Dong Sook");`과 같은 문장은 문법적으로 아무문제가 없지만, 객체생성이 목적이아닌  클래스로 만들어졌기 떄문에, **이러한 실수의 가능성이 있는 경로는 문법적으로 막아야 한다.**



 💡가상함수를 **'순수 가상함수'**로 선언하여 객체의 생성을 문법적으로 막는 것이 좋다.

```c++
class Employee
{
private:
    char name[100];
public:
    Employee(char * name){....}
    void ShowYourName() const{....}
    virtual int GetPay() const = 0; //순수 가상함수
    virtual void ShowSalaryInfo() const = 0; //순수 가상함수
}
```

`순수 가상함수`: 함수의 몸체가 정의되지 않은 함수

✔<span style = "color : green"> `0의 대입`을 표시하여 명시적으로 몸체를 정의하지 않았음을 컴파일러에게 알린다.</span>

✨`순수 가상함수의 이점`✨

       - 객체의 생성을 막을 수 있다.
       - 실제 실행이 되는 함수가 아님을 명확히 명시 할 수 있다.

> **하나 이상의 멤버함수**를 **순수 가상함수로 선언한 클래스**를 가리켜 `추상 클래스(abstract class)`라 한다.👉 완전하지 않은, **객체생성이 불가능한 클래스**라는 의미를 지닌다.

.

.

.

📌다형성(Polymorphism)

> '동질이상' : 모습은 같은데 형태는 다르다.

👉 문장은 같은데 결과는 다르다.

```c++
class First
{
public:
    virtual void SimpleFunc() { cout<<"First"<<endl;}
};

class Second: public First
{
public:
    virtusl void SimpleFunc() { cout<<"Second"<<endl;}
};

int main(void)
{
    First * ptr=new First();
    ptr->SimpleFunc(); //아래에 동일한 문장이 존재한다.
    delete ptr;
    
    ptr=new Second();
    ptr->SimpleFunc(); //위에 동일한 문장이 존재한다.
    delete ptr;
    return 0;
}
```

💡 같은 함수임에도 불구하고 다른 결과가 나오는 이유는 `포인터 변수` ptr이 참조하는 `객체의 자료형`이 다르기 때문이다.

.

.

.

---

## 가상 소멸자와 참조자의 참조 가능성

가상함수 말고도 virtual 키워드를 붙여줘야 할 대상이 하나 더 있다.

바로 `소멸자`이다.



📌 가상 소멸자 (Virtual Destructor)

```c++
#include <iostream>
using namespace std;

class First
{
private:
    char * strOne;
public:
    First(char * str)
    {
        strOne = new char[strlen(str)+1];
    }
    ~First()
    {
        cout<<"~First()"<<endl;
        delete []strOne;
    }
};

class Second: public First
{
private:
    char * strTwo;
public:
    Second(char * str1, char * str2):First(str1)
    {
        strTwo= new char[strlen(str2)+1];
    }
    ~Second()
    {
        cout<<"~Second()"<<endl;
        delete []strTwo;
    }
};

int main(void)
{
    First * ptr=new Second("simple", "complex");
    delete ptr;
    return 0;
}
```

👀 객체의 소멸을 `First형` 포인터로 명령하니, First 클래스의 소멸자만 호출되었다. 따라서 이러한 경우에는 `메모리 누수`가 발생하게 된다.

👉 객체 소멸 과정에서는 delete 연산자에 사용된 포인터 변수의 자료형에 상관없이 **모든 소멸자**가 호출 되어야 한다.

```c++
virtual ~First()
{
    cout<<"~First()"<<endl;
    delete []strOne;
}
```

.

📌 참조자의 참조 가능성

```c++
void GoodFuncion(const First &ref){....}
```

과 같은 함수를 보았을 때 판단해야하는 점.

✔ First 객체 또는 Fisrt를 직접 혹은 간접적으로 상속하는 객체가 인자의 대상이 된다.

✔ 인자로 전달되는 객체의 실제 자료형에 상관 없이 함수 내에서는 First 클래스에 정의된 함수만 호출 할 수 있다.