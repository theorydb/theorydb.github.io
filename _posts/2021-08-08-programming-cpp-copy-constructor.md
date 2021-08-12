---
layout: post
title: "[cpp] 복사 생성자(Copy Constructor)"
subtitle: "copy constructor"
categories: programming
tags: cpp 
comments: true

---

>
>
>`복사 생성자`에 관한 내용을 다룬다.

- 개요
  - '복사 생성자'와의 첫 만남





## 복사 생성자와의 첫 만남

---

📌 C++ 스타일의 초기화

```c++
//우리는 지금까지 다음과 같은 방식으로 변수와 참조자를 선언 및 초기화 해왔다.
int num=20;
int &ref=num;

//하지만, C++에서는 다음과 같은 방식으로 선언 및 초기화가 가능하다.
int num(20);
int &ref(num);
```

위의 두가지 초기화 방식은 결과적으로 동일하다.



```c++
class SoSimple()
{
private:
    int num1;
    int num2;
public:
    SoSimple(int n1,int n2 : num(n1), num(n2))
    { }
    void ShowSimplwData()
    {
        cout<<num1<<endl;
        cout<<num2<<endl;
    }
};

int main(void)
{
    SoSimple sim1(15, 20);
    SoSimple sim2=sim1; //객체 sim1의 값이 객체 sim2로 복사된다. 생성자는??
    sin2.ShowSimpleData();
    return 0;
}
```



📌SoSimple sim2(sim1);

   - SoSimple형 객체를 생성해라.
   - 객체의 이름은 sim2로 정한다.
   - sim1을 인자로 받을 수 있는 생성자의 호출을 통해서 객체생성을 완료한다.

⚠ _하지만_  위의 객체 생성문에서 호출하고자 하는 생성자는 다음과 같이 **SoSimple 객체를 인자로 받을 수 있는 생성자이다.**

```c++
SoSimple(SoSimple &copy)
{
    .....
}
```



```c++
#include <iostream>
using namespace std;

class SoSimple
{
private:
    int num1;
    int num2;
public:
    SoSimple(int n1, int n2)
        :num1(n1), num2(n2)
    {
       //empty     
    }
    SoSimple(SoSimple &copy) //객체를 인자로 받는 생성자 추가
        :num1(copy.num1), num2(copy.num2) ///member initialize로 멤버 대 멤버 복사
    {
      cout<<"Called SoSimple(SoSimple &copy)"<<endl;
    }
    void ShowSimpleData()
    {
        cout<<num1<<endl;
        cout<<num2<<endl;
    }
};

int main(void)
{
    SoSimple sim1(15, 30);
    cout<<"생성 및 초기화 직전"<<endl;
    SoSimple sim2=sim1; //SoSimple sim2(sim1);으로 변경
    cout<<"생성 및 초기화 직후"<<endl;
    sim2.ShowSimpleData();
    return 0;      
}
```

<span style = "color : blue">이러한 생성자를 가리켜 별도로 `복사 생성자(copy consturctor)`라 부른다.</span>



```c++
 SoSimple(const SoSimple &copy)
        :num1(copy.num1), num2(copy.num2) 
    {
      cout<<"Called SoSimple(SoSimple &copy)"<<endl;
    }
```

_멤버 대 멤버의 복사에 사용되는 원본을 변경시키는 것은 복사의 개념을 무너뜨리는 행위가 되기 때문에, 키워드 `const`를 삽입해서 이러한 실수를 막아 놓는 것이 좋다._



📌 자동으로 삽입이 되는 디폴트 복사 생성자

```c++
class SoSimple
{
private:
    int num1;
    int num2;
public:
    SoSimple(int n1, int n2) : num1(n1), num2(n2)
    {   }
    SoSimple(const SoSimple &copy) : num1(copy.num1), num2(copy.num2)
    {   }
};
```



  [**복사 생성자를 정의하지 않으면, 멤버 대 멤버의 복사를 진행하는 디폴트 복사 생성자가 자동으로 삽입된다.**]()



📌 변환에 의한 초기화! 키워드 `explicit`으로 막을 수 있다.

```c++
explicit SoSimple(const SoSimple &copy)
          : num1(copy.num1), num2(copy.num2)
{
   //empty!!          
}
```

SoSimple sim2=sim1; 은  SoSimple sim2(sim1);으로 `묵시적 형변환`이 일어나서 `복사 생성자`가  `호출`된다.

이러한 `묵시적 형변환`을 막기 위해서 앞서 말한 <span style = "color : blue">`explicit`</span>을 사용하면, 대입 연산자를 이용한 객체의 생성 및 초기화는 불가능 하다.



​    🔎 전달인자가 `하나`인 생성자가 있다면, 이 역시 `묵시적 형변환`이 발생한다.

```c++
class AAA
{
private:
    int num;
public:
    AAA(int n) : num(n){ }
    ....
};
```

위와 같이 정의된 클래스가 있을 경우,

`AAA obj = 3;`  을 통해 객체 생성이 가능하다.

이는 `AAA obj(3);`으로 변환 되어 **_묵시적 형변환_**이  이루어진다.



_따라서_  키워드 `explicit`가 생성자에 선언되면, <u>묵시적 형변환을 허용하지 않기 때문에</u>

`AAA obj(3);` 과 같은 형태로 객체를 생성할 수 밖에 없다.







## 깊은 복사와 얕은 복사

---

디폴트 복사 생성자는 멤버 대 멤버의 복사를 진행한다. 그리고 이러한 방식의 복사를 가리켜 **'얕은 복사(shallow copy)'**라 하는데, [이는 멤버변수가 힙의 메모리 공간을 참조하는 경우에 문제가 된다.]()



📌 디폴트 복사 생성자의 문제점

```c++
#include <iostream>
#include <cstirng>
using namespace std;

Class Person
{
private:
    char * name;
    int age;
public:
    Person(char *myname, int myage)
    {
        int len=strlen(myname)+1;
        name=new char[len];
        strcpy(name, myname);
        age=myage;
    }
    void showPersonInfo() const
    {
        cout<<"이름: "<<name<<endl;
        cout<<"나이: "<<age<<endl;
    }
    ~Person()
    {
      delete []name;
      cout<<"called desstructor!"<<endl;
    }
}
int main(void)
{
    //Class Person은 생성자에서 new를 이용한 동적할당, 소멸자에서 delete를 이용한 메모리의 해제를 진행하고 있다.
  
    Person man1("Lee dong woo", 29);
    Person mas2=man1; //객체가 2개 생성된다.
    man1.ShowPersonInfo();
    man2.ShowPersonInfo();
    
    return 0;
}

//result
//생성자는 2번 실행

//called destructor!
//소멸자 한번만 실행
```



디폴트 복사 생성자는 멤버 대 멤버를 단순히 복사만 하므로, 다음의 구조를 띠게 된다.(객체 내에 함수는 표현하지 않음.)

![이미지](https://yeram522.github.io/assets/img/programming/cpp/2021-08-08-programming-cpp-copy-constructor-shallowcopy.JPG?raw=true)



따라서 복사의 결과로 하나의 문자열을 두 개의 객체가 동시에 참조하는 꼴을 만들어 버린다.



man2의 객체의 소멸과정에서 man2가 참조하던 문자열은 이미 소멸된 상태이기 때문에,

`delte []name;`

man1객체의 소멸자에 포함되어 있는 위의 문장은 이미 지워진 문자열을 대상으로 delete연산을 하기 때문에 문제가 된다.

![이미지](https://yeram522.github.io/assets/img/programming/cpp/2021-08-08-programming-cpp-copy-constructor-shallowcopy-1.JPG?raw=true)







📌 '깊은 복사'를 위한 복사 생성자의 정의

![이미지](https://yeram522.github.io/assets/img/programming/cpp/2021-08-08-programming-cpp-copy-constructor-deepcopy.JPG?raw=true)

  위의 형태로 복사가 이루어진다면, 객체 별로 각각 문자열을 참조하기 때문에, 위에서 언급한 객체 소멸과정에서의 문제는 발생하지 않는다. 

_이러한 형태를 가리켜 `깊은 복사(deep copy)`라 한다._

_멤버뿐만 아니라, 포인터로 참조하는 대상까지 깊게 복사한다는 뜻이다._

```c++
#include <iostream>
#include <cstirng>
using namespace std;

Class Person
{
private:
    char * name;
    int age;
public:
    Person(char *myname, int myage)
    {
        int len=strlen(myname)+1;
        name=new char[len];
        strcpy(name, myname);
        age=myage;
    }
    //깊은 복사(deep copy)를 위해 아래의 생성자를 추가하였다.
    Person(const Person& copy): age(copy.age)
    {
        name.new char[strlen(copy.name)+1];
        strcpy(name, copy.name);
    }
    
    void showPersonInfo() const
    {
        cout<<"이름: "<<name<<endl;
        cout<<"나이: "<<age<<endl;
    }
    ~Person()
    {
      delete []name;
      cout<<"called desstructor!"<<endl;
    }
}
int main(void)
{
    //Class Person은 생성자에서 new를 이용한 동적할당, 소멸자에서 delete를 이용한 메모리의 해제를 진행하고 있다.
  
    Person man1("Lee dong woo", 29);
    Person man2=man1; //객체가 2개 생성된다.
    man1.ShowPersonInfo();
    man2.ShowPersonInfo();
    
    return 0;
}
```



깊은 복사를 구현하기 위해 위의 코드에 다음과 같은 정의의 생성자를 추가하였다.

```c++
 Person(const Person& copy): age(copy.age)
    {
        name.new char[strlen(copy.name)+1];
        strcpy(name, copy.name);
    }
```

- 멤버변수 age의 멤버 대 멤버 복사
- 메모리 공간 할당후 문자열 복사, 그리고 할당된 메모리의 주소 값을 멤버 name에 저장.



## 복사 생성자의 호출시점

---

📌 복사 생성자가 호출되는 시점은?

​    복사 생성자가 호출되는 시점은 크게 3가지로 구분할 수 있다.

- case 1: 기존에 생성된 객체를 이용해서 새로운 객체를 초기화하는 경우.

```c++
Person man1("Lee dong woo",29);
Person man2=man1 //복사 생성자 호출
```



- case 2: Call-by-value 방식의 함수호출 과정에서 **객체를 인자로 전달하는 경우.**
- case3: 객체를 반환하되, **참조형으로 반환하지 않는 경우.**



위 3가지 케이스는 

``객체를 새로 생성해야 한다. 단, 생성과 동시에 동일한 자료형의 객체로 초기화해야 한다!``

라는 공통점을 지닌다.



📌 메모리 공간의 할당과 초기화가 동시에 일어나는 상황!

[1]

`int num1=num2;`

위의 문장은 num1이라는 이름의 메모리 공간을 <span style = "color : violet">할당과 동시에</span> num2에 저장된 값으로 <span style = "color : violet">초기화</span> 시키는 문장이다.



[2]  

```c++
int SimpleFunc(int n)
{
    .....
}
int main(void)
{
    int num=10;
    SimpleFunc(num); //호출되는 순간 매개변수 n이 할당과 동시에 초기화!
    ....
}
```

위 코드에서 SimpleFunc가 호출되는 순간에 매개변수 n이 할당과 동시에 변수 num에 저장되어 있는 값으로 초기화된다.



[3]

```c++
int SimpleFunc(int n)
{
    ....
    return n;  //반환하는 순간 메모리 공간이 할당되면서 동시에 초기화!
}
int main(void)
{
    int num=10;
    cout<<SimpleFunc(num)<<endl;
}
```

반환되는 값을 별도의 변수에 저장하는 것과 별개로, 값을 반환하면 반환된 값은 별도의 메모리 공간이 할당되어 저장이된다.

`cout<<SimpleFunc(num)<<endl;`

반환 되는 값을 메모리 공간의 어딘가에 저장해 놓지 않았다면, cout에 의한 출력이 불가능하다.

출력되기 위해서는 그 값을 **참조**할 수 있어야 하고, 참조가 가능하려면 메모리 공간의 어딘가에 저장되어야 한다.

_"함수가 값을 반환하면, 별도의 메모리 공간이 할당되고, 이 공간에 반환 값이 저장된다.(반환 값으로 초기화 된다)."_

`따라서`  객체의 전달도 기본 자료형의 인자전달과 차이가 없다.

```c++
SoSimple SimpleFucObj(SoSimple ob)
{
    ....
        return ob; //반환하는 순간 메모리 공간이 할당되면서 동시에 초기화!
}
```

위의 `return문`이 실행되는 순간, SoSimple 객체를 위한 메모리 공간이 할당되고, 이 공간에 할당된 객체는 반환되는 객체 ob내용으로 초기화 된다.





📌할당 이후, 복사 생성자를 통한 초기화

   `초기화`는 멤버 대 멤버가 복사되는 형태로 이뤄져야 하기 때문에, `객체`의 초기화는 `복사 생성자의 호출`의 방식으로 진행된다.

_`디폴트 복사생성자`는 멤버 대 멤버가 복사되도록 정의가 가능하기 때문에, 적절한 초기화 방식이다.



:star:`PassObjCopycon.cpp`  : Call-by-value 방식의 함수호출 과정에서 **객체를 인자로 전달하는 경우.**

```c++
#include <iostream>
using namespace std;

class SoSimple
{
private:
    int num;
public:
    SoSimple(int n) : num(n)
    { }
    SoSimple(const SoSimple& copy) : num(copy.num)
    {
        cout<<"Called SoSimple(const SoSimple& copy)"<<endl;
    }
    void ShowData()
    {
        cout<<"num: "<<num<<endl;
    }
};

void SimpleFuncObj(SoSimple ob)
{
    ob.ShowData();
}

int main(void)
{
    SoSimple obj(7);
    cout<<"함수호출 전"<<endl;
    SimpleFuncObj(obj);
    cout<<"함수호출 후"<<endl;
    return 0;
}

//result::
//함수호출 전
//Called SoSimple(const SoSimple& copy)
//num: 7
//함수호출 후
```

❔ 그렇다면 복사 생성자의 호출 주제는 obj일까, ob일까?



​                                                                  `복사생성자의 호출관계`

![이미지](https://yeram522.github.io/assets/img/programming/cpp/2021-08-08-programming-cpp-copy-constructor-avoke-copy-constructor.JPG?raw=true)



위의 그림과 같이 초기화 대상은 `ob`객체이다.

그리고 ob객체는 obj객체로 초기화 된다.

_따라서 ob객체의 복사 생성자가 호출되면서, obj객체가 인자로 전달되어야 한다._





:star:`ReturnObjCopycon.cpp` : 객체를 반환하되, **참조형으로 반환하지 않는 경우.**

```c++
#include <iostream>
using namespace std;

class SoSimple
{
private:
    int num;
public:
    SoSimple(const SoSimple& copy) : num(copy.num)
    {
        cout<<"Called SoSimple(const SoSimple& copy)"<endl;
    }
    SoSimple& AddNum(int n)
    {
        num +=n;
        return *this;
    }
    void ShowData()
    {
        cout << "num: "<<endl;
    }
};

SoSimple SimpleFuncObj(SoSimple ob)
{
    cout<<"return 이전"<<endl;
    return ob;
}

int main(void)
{
    SoSimple obj(7);
    SimpleFuncObj(obj).AddNum(30).ShowData();
    obj.ShowData();
    return 0;
}
```



