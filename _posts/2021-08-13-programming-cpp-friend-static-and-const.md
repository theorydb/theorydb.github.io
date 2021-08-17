---
layout: post
title: "[c++] friend와 static 그리고 const"
subtitle: "friend,static and const"
categories: programming
tags: cpp study
comments: true
header-img: img/programming/cpp/0000-00-00-programming-cpp-book-cover-1.JPG
---

> `friend`,`static`,`const`에 관한 내용을 다룬다.
>
> `윤성우의 열혈 C++` 교재를 바탕으로 작성되었다.

- 개요
  - [const와 관련해서 아직 못다한 이야기](#const와-관련해서-아직-못다한-이야기)
        - const 객체와 const 객체의 특성들
        - const와 함수 오버로딩

  - [클래스와 함수에 대한 friend 선언](#클래스와-함수에-대한-friend-선언)
           - 클래스의 friend 선언
           - 함수의 friend선언

  - [C++ 에서의 static](#cpp-에서의-static)
            - C언어에서 이야기한 static
            - static 멤버변수(클래스 변수)
            - static 멤버변수의 또 다른 접근방법
       - static 멤버함수
       - 키워드 mutable

  



## const와 관련해서 아직 못다한 이야기

---

📌 const 객체와 const 객체의 특성들

​     `const int num=10;` 과 같이 변수를 상수화 하듯이.

객체도 상수화 할 수 있다. 👉 `const SoSimple sim(20);`



✔ <span style = "color : green">이렇게 객체에 const 선언이 붙게 되면, 이 객체를 대상으로는 [const 멤버함수만 호출이 가능하다.]()</span>

`객체의 const 선언` 의 의미👉   **"이 객체의 데이터 변경을 허용하지 않겠다." **



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
    SoSimple& AddNum(int n)
    {
        num+=m;
        return *this;
    }
    void ShowData() const
    {
        cout<<"num: "<<num<<endl;
    }
};

int main(void)
{
    const SoSimple obj(7);  //const 객체 생성
    //obj.AddNum(20); //멤버함수 AddNum()은 const함수가 아니여서 호출 불가능
    obj.ShowData(); //const함수이기 떄문에 const객체를 대상으로 호출 가능!
    return 0;
}
```

💡 멤버변수에 저장된 값을 수정하지 않는 함수는 가급적 const로 선언해서, const 객체에서도 호출이 가능하도록 할 필요가 있다.





📌 const와 함수 오버로딩

함수의 오버로딩이 성립하려면 [매개변수의 수나 자료형이 달라야 한다](), 하지만 <span style = "color : red">const의 선언유무</span>도 **함수 오버로딩**의 조건에 해당이 된다.

```c++
void SimpleFunc() {....}
void SimpleFunc() const {....}
```







## 클래스와 함수에 대한 friend 선언

---

📌 클래스의 friend 선언

​    👉 A 클래스가 **B 클래스를 대상**으로 friend 선언을 하면, **B 클래스**는 **A 클래스의 private 멤버에 직접 접근이 가능**하다.

​    👉 단, **A 클래스도** B 클래스의 private 멤버에 직접 접근이 가능 하려면, **B 클래스가 A 클래스를 대상으로 friend 선언을 해줘야 한다.**

_`friend선언` 은[private 멤버의 접근]()을 허용하는 선언이다._



```c++
Class Boy
{
private:
    int height; //키
    friend class Girl;// Girl 클래스를 friend로 선언함
public:
    Boy(int len) : hight(len)
    {  }
    ....
};

class Girl
{
private:
    char phNum[20]; //전화번호
public:
    Girl(char * num)
    {
        strcpy(phnum, num);
    }
    void ShowYourFriendInfo(Boy &frn)
    {
        cout<<"His height: "<<frn.height<<endl;  //private 멤버에 접근.
        //Boy클래스의 private 멤버에 접근하고 있다.
    }
};
```



📄`Friend선언 예시.cpp`

```c++
#include <iostream>
#include <cstring>
using namespace std;

class Girl; //Girl 이라는 이름이 클래스의 이름을 미리 선언한다.
//* 정의가 뒤에 나오는 함수의 호출을 위해서, 함수의 원형을 선언하듯이, 클래스도 선언이 가능하다.

class Boy
{
private:
    int height;
    friend class Girl; //Girl 클래스에 대한 friend 선언
    //private 영역에도 friend의 선언이 가능하다.
    //friend와 class를 같이 선언 할 수 있다.
public:
    Boy(int len): height(len)
    { }
    void ShowourFriendInfo(Girl &frn);
    //정의되지 않은 클래스를 사용했음에도 컴파일이 가능한 이유는, 앞서 Girl이라는 클래스의 이름을 미리 알렸기 때문이다.
};

//Girl이라는 클래스가 정의되었다.
//Boy클래서의 ShowYourFriendInfo 함수가 정의되기에 앞서 Girl클래스가 등장했음을 주목하자!
class Girl
{
private:
    char phNum[20];
public:
    Girl(char * num)
    {
        strcpy(phNum,num);
    }
    void ShowYourFriendInfo(Girl &frn);
    friend class Boy; //Boy 클래스에 대한 friend 선언
};

//Boy클래스 외부에 함수를 정의 하였다.
void Boy::ShowYourFriendInfo(Girl &phNum)
{
    cout<<"Her phone number: "<<frn.phNum<<endl;
    //이 문장을 제대로 컴파일 하기 위해서는, Girl클래스에 멤버변수 phNum이 존재한다는 사실을 알아야 하기 떄문에, 함수의 정의가 Girl클래스의 정의보다 뒤에 위치한 것이다.
}

//Girl클래스 외부에 함수를 정의 하였다.
void Girl::ShowYourFriendInfo(Boy &frn)
{
    cout<<"His height: "<<frn.height<<endl;
}

int main(void)
{
    Boy boy(170);
    Girl girl("010-1234-5678");
    boy.ShowYourFriendInfo(girl);
    girl.ShowYourFriendInfo(boy);
    return 0;
}
```



---

❔ <span style = "color : violet">Friend 선언은 언제?</span>

   c++문법 중에 논란이 되었던 것 중 하나가, `friend`선언이다.

**`Friend`선언은 객체지향의 대명사 중 하나인 `정보은닉`을 무너뜨리는 문법이기 떄문이다.**

따라서 가급적으로 사용하지 않는 연습을 하고, 좋게 사용되는 경우는 `연산자 오버로딩`을 공부하면서 보게 될 것이다.

---





📌함수의 friend선언

​    `전역함수`를 대상으로도, `클래스의 멤버함수`를 대상으로도 friend 선언이 가능하다.

```c++
#include <iostream>
using namespace std;

class Point;
//Point가 클래스의 이름임을 선언

class PointOP
{
private:
    int opcnt;
public:
    PointOP() : opcnt(0)
    { }
    //PointOP클래스 안의 함수 선언 떄문에, 앞서 class Point를 선언해주었다.
    Point PointAdd(const Point&, const Point&);
    Point PointSub(const Point&, const Point&);
    
    ~PointOP()
    {
        cout<<"Operation times: "<<copcnt<<endl;
    }
};

class Point
{
private:
    int x;
    int y;
public:
    Point(const int &xpos, const int &ypos) : x(pos), y(ypos)
    { }
    friend Point PointOP::PointADD(const Point&, const Point&);
    friend Point PointOP::PointSub(const Point&, const Point&);
    //pointOP 클래스의 멤버함수 PointAdd와 PointSub에 대해 friend 선언을 하고 있음.
    friend void ShowPointPos(const Point&);
    //코드 맨 아랫단에 선언된 함수 ShowPointPos에 대해 friend선언을 하고 있다. 
};

Point PointOP::PointADD(const Point& pnt1, const Point& pnt2)
{
    opcnt++;
    return Point(pnt1.x+pnt.x, pnt1.y+pnt2.y);
    //Point클래스의 friend로 선언되어있기 떄문에, PointOP에서도 Point클래스의 private멤버에 접근이 가능하다.
}

Point PointOP::PointSub(const Point& pnt1, const Point& pnt2)
{
    opcnt++;
    return Point(pnt1.x-pnt2.x, pnt1.y-pnt2.y);
    //Point클래스의 friend로 선언되어있기 떄문에, PointOP에서도 Point클래스의 private멤버에 접근이 가능하다.
}

int main(void)
{
    Point pos1(1,2);
    Point pos2(2,4);
    PointOP op;
    
    ShowPointPos(op.PointAdd(pos1,pos2));
    ShowPointPos(op.PointSub(pos2,pos1));
    //ShowPointPos 함수도 Point클래스의 friend로 선언되었기 떄문에 private 멤버에 접근이 가능하다.
    return 0;
}

void ShowPointPos(const Point& pos)
{
    cout<<"x: "<<pos.x<<", ";
    cout<<"y: "<<pos.y<<endl;
}
```

🔎 **`friend void ShowPointPos(const Point&);`**

 위의 friend 선언에는, `friend 선언` 이외에, 

`void ShowPointPos(const Point&);` 라는 [함수원형 선언]()이 포함되어있다.

따라서 friend 선언을 위해서 별도의 함수원형으 선언할 필요는 없다.







## Cpp 에서의 static

---

📌 C언어에서 이야기한 static

      - `전역변수`에 선언된 `static`의 의미

​        👉 **선언된 파일 내**에서만 **참조**를 **허용**하겠다는 의미

- `함수 내`에 선언된 `static`의 의미

​        👉 **한번만 초기화**되고, 지역변수와 달리 **함수를 빠져나가도 소멸되지 않는다.**

```c++
#include <iostream>
using namespace std;

void Counter()
{
    static int cnt; //static 변수는 전역변수와 마찬가지로 초기화하지 않으면 0으로 초기화된다.그리고 이 문장은 딱 한번 실행이 된다. 즉, cnt는 Counter함수가 호출될 때마다 새롭게 할당되는 지역변수가 아니다!!!
    cnt++;
    cout<<"Current cnt: "<<cnt<<endl;
}

int main(void)
{
    for(int i=0; i<10; i++)
        Counter();
    return 0;
}
```





📌 전역변수가 필요한 상황

```c++
#include <iostream>
using namespace std;

int simObjCnt=0; //SoSimple 객체 수를 세기 위한 전역변수
int cmxObjCnt=0; //SoComplex 객체 수를 세기 위한 전역변수

class SoSimple
{
public:
    SoSimple()
    {
        //객체가 생성될때마다 해당 전역변수의 값이 증가하도록, 생성자 내에서 증가연산을 하고 있다.
        simObjCnt++;
        cout<<simObjCnt<<"번째 SoSimple 객체"<<endl;
    }
};

class SoVomplex
{
public:
    SoComplex()
    {
        //객체가 생성될때마다 해당 전역변수의 값이 증가하도록, 생성자 내에서 증가연산을 하고 있다.
        cmxObjCnt++;
        cout<<cmxObjCnt<<"번째 SoComplex 객체"<<endl;
    }
    SoComplex(SoComplex &copy)
    {
        //객체가 생성될때마다 해당 전역변수의 값이 증가하도록, 생성자 내에서 증가연산을 하고 있다.
        cmxObjCnt++;
        cout<<cmxObjCnt<<"번째 SoComplex 객체"<<endl;
    }

};

int main(void)
{
    SoSimple sim1;
    SoSimple sim2;
    
    SoComplex com1;
    SoComplex com2=com1;
    SoComplex();
    
    return 0;
}


//result
/*
1번째 SoSimple 객체
2번째 SoSimple 객체
1번째 SoComplex 객체
2번째 SoComplex 객체
3번째 SoComplex 객체
*/

```



[simObjCnt](): `SoSimple 객체`들이 **공유**하는 변수

[cmxObjCnt]():  `SoComplex 객체`들이 **공유**하는 변수

👉 **모두 전역변수** 이므로 어디서나 접근이 가능하기 때문에 제한을 지켜줄 장치가 존재하지 않는다.

​      💡 <Span style = "color : Orange">따라서,  **각 클래스**의 `static 멤버`로 **선언**하면, 이러한 문제의 소지를 없앨 수 있다.</span>





📌static 멤버변수(클래스 변수)

​     👉   <span style = "color : purple">일반적인 멤버변수와 달리 클래스당 `하나씩만 생성`되기 때문에 `클래스 변수`라고도 한다.</span>

```c++
class SoSimple
{
private:
    static int simObjCnt; //static 멤버변수, 클래스 변수
public:
    SoSimple()
    {
        simObjCnt++;
        cout<<simObjCny=0<<"번째 SoSimple 객체"<<endl;
    }
};
int SoSimple::simObjCnt=0; //static 멤버변수의 초기화
```

🔎`int SoSimple::simObjCnt=0;`코드에 선언된 **static 변수** `simObjCnt`는 SoSimple 객체가 생성될 때마다 함께 생성되어 객체별로 유지되는 변수가 아니다. 객체를 생성하건 생성하지 않건, 

​              ✔<span style = "color : green">      _메모리 공간에 **딱 하나만 할당**이 되어서 **공유**되는 **변수**이다._</span>



```c++
int main(void)
{
    SoSimple sim1;
    SoSimple sim2;
    SoSimple sim3;
    ....
}
```

과 같이 총3개의 `SoSimple`객체를 생성하게 되면, 세개의 객체가 static변수 `simObjCnt`를 공유하는 구조가 된다.



`static 멤버변수와 객체의 관계`

![이미지](https://yeram522.github.io/assets/img/programming/cpp/2021-08-13-programming-cpp-friend-static-and-const-1.JPG)

⚠ [객체 내에 simObjCnt가 존재하는 것이 아닌, 객체 외부에 있지만 `멤버변수처럼` 접근할 수 있는 권한이 주어진 것! ]()

​      ✔<span style = "color:green">_생성 및 소멸 시점도 전역변수와 **동일**하다._</span>

```c++
#include <iostream>
using namespace std;

class SoSimple
{
private:
    static int simObjCnt; //SoSimple 내에 선언된 static 변수 이므로, SoSimple 객체에 의해 공유된다.
public:
    SoSimple()
    {
        //SoSimple의 멤버함수(생성자) 내에서는 마치 멤버변수인 것처럼 접근이 가능하다.
        //static 변수를 멤버변수로 오해는 금지!
        simObjCnt++;
        cout<<simObjCnt<<"번째 SoSimple 객체"<<endl;
    }
};
int SoSimple::simObjCnt=0; //static변수의 초기화
//생성자가 아닌 클래스 외부에서 초기화 해야하는 이유는????

class SoComplex
{
private:
    static int cmxObjCnt; //SoComplex 객체에 의해 공유되는 SoComplex에 선언된 static 변수
public:
    SoComplex()
    {
        //SoComplex의 멤버함수(생성자) 내에서는 마치 멤버변수인 것처럼 접근이 가능하다.
        cmxObjCnt++;
        cout<<cmxObjCnt<<"번째 SoComplex 객체"<<endl;
    }
    SoComplex(SoComplex &copy)
    {
        cmxObjCnt++;
        cout<<cmxObjCnt<<"번째 SoComplex 객체"<<endl;
    }
};
int SoComplex::cmxObjCnt=0;//static변수의 초기화

int main(void)
{
    SoSimple sim1;
    SoSimple sim2;
    
    SoComplex cmx1;
    SoComplex cmx2=cmz1;
    SoComlex();
    return 0;                                                               
}
```

---

❔    <span style = "color : coral">`static 변수`를 **생성자**에서 **초기화** 하면 `안되는` 이유</span>

​      만약, `SoSimple`의 생성자를 다음과 같이 정의한다면, 객체가 생성될 때마다 변수 simObjCnt는 0으로 초기화된다.

```c++
SoSimple()
{
    simObjCnt=-;
    simObjCnt++;
    cout<<simObjCnt<<"번째 SoSImple 객체"<<endl;
}
```

_왜냐하면, 변수 simObjCnt는 객체가 생성될 때 동시에 생성되는 변수가 아니고, 이미 메모리 공간에 할당이 이뤄진 변수이기 때문이다._

​    👉 따라서, `int SoSimple::simObjCnt = 0;` 으로 static 멤버변수의 초기화 문법이 <span style = "color : goldenrod">**별도로 정의**되어 있다.</span>

---





📌 static 멤버변수의 또 다른 접근방법

​     `static 멤버변수`는 어디서든 **접근이 가능한 변수**이다. 

   - static 멤버가  `private`으로 선언

     👉**해당 클래스**의 **객체**들만 [접근 가능]()

- static 멤버가 `public`으로 선언

​       👉**클래스의 이름 **또는 **객체의 이름**을 통해서 [어디서든 접근 가능]()

```c++
#include <iostream>
using namespace std;

class SoSimple
{
public:
    static int simObjCnt; //static 변수가 public 으로 선언!
public:     //불필요하지만 변수와 함수의 구분을 목적으로 삽입하기도 함
    SoSimple()
    {
       simObjCnt++;   
    }
};
int SOSimple::simObjCnt=0; //static 변수 초기화

int main(void)
{
    //객체를 하나도 생성하지 않은 상태임에도 불구하고, 클래스의 이름을 이용해서 simObjCnt에 접근을 할 수 있다.(static 멤버변수가 객체 내에 존재하지 않음을 증명.)
    cout<<SoSimple::simObjCnt<<"번째 SoSimple 객체"<<endl;
    SoSimple sim1;
    SoSimple sim2;
    
    cout<<SoSimple::simObjCnt<<"번째 SoSimple 객체"<<endl;
    
    //객체 sim1,sim2를 이용한 static 멤버변수 접근은 멤버변수 접근과 같은 오해를 불러일으키기 때문에 지양한다.
    cout<<sim1.simObjCnt<<"번째 SoSimple 객체"<<endl;
    cout<<sim2.simObjCnt<<"번째 SoSimple 객체"<<endl;
    return 0;
}

//result
/*
0번째 SoSimple 객체
1번째 SoSimple 객체
2번째 SoSimple 객체
2번째 SoSimple 객체
*/
```





📌static 멤버함수

  `static 멤버변수`와 특성이 동일하다.

- 선언된 클래스의 모든 객체가 공유한다.
- public으로 선언이 되면, 클래스의 이름을 이용해서 호출이 가능하다.
- 객체의 멤버로 존재하는 것이 아니다.



⚠ <span style = "color : firebrick">다음과 같은 코드는 컴파일 에러를 일으킨다.</span>

      ```c++
      class SoSimple
      {
      private:
          int num;
          static int num2;
      public:
          SoSimple(int n):num1(n)
          { }
          static void Adder(int n)
          {
              num1+=n; //컴파일 에러 발생
              num2+=n;
          }
      };
      int SoSimple::num2=0;
      ```

​           ✔ 객체의 멤버가 아니기 떄문에, 멤버 변수 접근 불가능

​           ✔ 객체생성 이전에도 호출 가능한 static 함수이기 떄문에, 멤버변수 접근 불가능

​           ✔ 멤버 변수에 접근해도, 어떤 객체의 멤버 변수에 접근해야 하는지 불확실.

   

​    👉 <span style = "color : hotpink">`static 멤버함수`   내에서는 **static 멤버변수**와 **static 멤버함수**만 호출이 가능하다.</span>

​         _이러한 특성을 잘 활용한다면,  대부분 경우에 있어서 전역변수와 전역함수를 대체할 수 있다._





📌 const static 멤버

    - **클래스 내에** 선언된 `const 멤버변수(상수)`의 초기화:  `이니셜라이저`를 통해 가능
    - **const static**으로 선언된 `멤버변수(상수)`:  `선언과 동시`에 초기화 가능  ⬇

```c++
#include <iostream>
using namespace std;

//국가별 면적 크기를 정해 놓은 클래스, const static 상수는 하나의 클래스에 둘 이상이 보이는 것이 보통이다.
class ContryArea
{
public:
    const static int RUSSIA = 1707540;
    const static int CANADA = 998467;
    const static int CHINA = 957290;
    const static int SOUTH_KOREA = 9922;
};

int main(void)
{
    //정의된 "상수"에  접근하기 위해서 굳이 객체를 생성할 필요는 없다. 클래스의 이름을 통해서 직접 접근하는 것이 편하고, 접근하는 대상에 대한 정보를 쉽게 노출 할 수 있다.
    cout<<"러시아 면적:"<<CountryArea::RUSSIA<<"km"<<endl;
    cout<<"캐나다 면적:"<<CountryArea::CANADA<<"km"<<endl;
    cout<<"중국 면적:"<<CountryArea::CHINA<<"km"<<endl;
    cout<<"한국 면적:"<<CountryArea::SOUTH_KOREA<<"km"<<endl;
    return 0;
}
```

👉 `const static 멤버변수`는, 클래스가 [정의될 때 지정된 값이 유지되는 상수]()이기 떄문에, 위 예제에서 보이는 바와 같이 **초기화가 가능**하도록 **문법으로 정의**하고 있다.





📌 키워드 mutable

​      👉 `const 함수 내`에서의 **값의 변경**을 **예외적**으로 **허용**한다.

```c++
#include <iostream>
using namespace std;

class SoSimple
{
private:
    int num1;
    mutable int num2; //const 함수에 대해 예외를 둔다!
public:
    SoSimple(int n1. int n2)
        : num1(n1),num2(n2)
    { }
    void ShowSimpleData() const
    {
        cout<<num1<<", "<<num2<<endl;
    }
    void CopyToNum2() const
    {
        num2=num1;
        //const 함수 내에서 num2에 저장된 값을 변경하고 있다. num2가 mutable로 선언되었기 떄문에 가능!
    }
};

int main(void)
{
    SoSimple sm(1,2);
    sm.ShowSimpleData();
    sm.CopyToNum2();
    sm.ShowSimpleData();
    return 0;
}
```

⚠ `num1=num2;`와 같이 대입 연산을 거꾸라 진행하는 상황을 방지한다는 측면에서 좋을 수 있겠지만, 어찌되었든 c++의 키워드인 const의 선언을 의미 없게 만들기 떄문에 제한적이고 매우 예외적인 경우에 한해서 사용해야한다.

