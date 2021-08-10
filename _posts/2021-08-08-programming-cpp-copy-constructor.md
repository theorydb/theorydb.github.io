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
int main(void)
{
    //Class Person은 생성자에서 new를 이용한 동적할당, 소멸자에서 delete를 이용한 메모리의 해제를 진행한다고 가정.
    /*~Person()
    {
      delete []name;
      cout<<"called desstructor!"<<endl;
    }*/
    Person man1("Lee dong woo", 29);
    Person mas2=man1; //객체가 2개 생성된다.
    man1.ShowPersonInfo();
    man2.ShowPersonInfo();
}

//result
//생성자는 2번 실행

//called destructor!
//소멸자 한번만 실행
```

디폴트 복사 생성자는 멤버 대 멤버를 단순히 복사만 하므로, 다음의 구조를 띠게 된다.(객체 내에 함수는 표현하지 않음.)

![이미지](https://yeram522.github.io/assets/img/programming/cpp/2021-08-08-programming-cpp-copy-constructor-shallowcopy "shallowcopy")



따라서 복사의 결과로 하나의 문자열을 두 개의 객체가 동시에 참조하는 꼴을 만들어 버린다.



man2의 객체의 소멸과정에서 man2가 참조하던 문자열은 이미 소멸된 상태이기 때문에,

`delte []name;`

man1객체의 소멸자에 포함되어 있는 위의 문장은 이미 지워진 문자열을 대상으로 delete연산을 하기 때문에 문제가 된다.

![이미지](https://yeram522.github.io/assets/img/programming/cpp/2021-08-08-programming-cpp-copy-constructor-shallowcopy-1 "shallowcopy-1")



`깊은 복사의 예시`

![이미지](https://yeram522.github.io/assets/img/programming/cpp/2021-08-08-programming-cpp-copy-constructor-deepcopy "deepcopy")



📌 '깊은 복사'를 위한 복사 생성자의 정의

