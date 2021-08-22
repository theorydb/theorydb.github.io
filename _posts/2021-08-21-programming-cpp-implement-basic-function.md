---
layout: post
title: "[c++]gamepack:기본 기능 구현"
subtitle: "Implement Basic function"
categories: programming
tags: cpp opengl gamedev
comments: true
header-img: img/programming/cpp/0000-00-00-programming-cpp-game-lecture-cover.JPG
---

> `홍정모`교수님의 `게임 만들기 연습 문제 패키지`를 수강하고 작성한 문서이다.
>
> `키보드`,`마우스`와의 상호작용 및 `소리재생`에 대해 다루고 있다.

---

## 1.1 실시간 상호작용 어플리케이션의 구조

`Game2D.h`

```c++
...
		virtual void update()  
		{
			// draw
			// play sould
			// physics update
			// etc.
		}
...
```

✔ Virtual 선언을 통해 외부에서 함수를 오버라이드 할 수 있도록 정의해 놓았다.

.

`main.cpp`

```c++
namespace jm
{
	class RotatingStarExample : public Game2D
	{
		float time = 0.0f;
	public:
		void update() override //주석
		{
			rotate(time * 10.0f); //1s에 180'
			drawFilledStar(Colors::gold, 0.4f, 0.25);

			time += this->getTimeStep();
		}
	};
}
```

🔎 클래스 **RotationStar Example**은 **Game2D** 클래스를 상속하고 있다.

`update()`함수를 사용할 때, Game2D 클래스의 멤버함수를 **오버라이드** 했다고 명시

👉[`override`라고 선언!!]()

.

.

.

## 1.2 기본적인 그리기 - 이동, 회전, 애니메이션

### 🕹 점과 선 그리기



`점(Point)`

```c++
const vec2 point = vec2(0.0f, 0.0f);
const vec2 point_1(0.0f, 0.0f); //생성자로 바로 선언 가능.
drawPoint(Colors::black, point, 5.0f);
```

.

`선(Line)`

```c++
const vec2 p0(0.0f, 0.0f); 
const vec2 p1(0.5f, 0.5f);
const vec2 p2(0.5f ,0.0f);

drawLine(Colors::red, p0, Colors::blue, p1);
drawLine(Colors::red, p1, Colors::blue, p2);
drawLine(Colors::red, p2, Colors::blue, p0);
```

👀 삼각형을 그렸다.

.

.

.

### 🕹 이동

```c++
const float dx = 0.1f;
const float dy = 0.2f;
			
// translation : 어떤 형태를 유지하면서 그대로 이동시키는 것.
const vec2 p0(0.0f + dx, 0.0f + dy); 
const vec2 p1(0.5f + dx, 0.5f + dy);
const vec2 p2(0.5f + dx, 0.0f + dy);

drawLine(Colors::red, p0, Colors::blue, p1);
drawLine(Colors::red, p1, Colors::blue, p2);
drawLine(Colors::red, p2, Colors::blue, p0);
```

✔ 변수 dx와 dy의 값 변경으로 삼각형을 좌표계에서 이동시킬 수 있다.

​       👉 **좌표의 값이 변경되었다.**

.

```c++
translate(0.1f, 0.0f);

const vec2 p0(0.0f, 0.0f); 
const vec2 p1(0.5f, 0.5f);
const vec2 p2(0.5f, 0.0f);

drawLine(Colors::red, p0, Colors::blue, p1);
drawLine(Colors::red, p1, Colors::blue, p2);
drawLine(Colors::red, p2, Colors::blue, p0);
```

✔ 점들의 [좌표가 변경되지 않았음]()에도 삼각형이 0.1f만큼 이동하였다.

​       👉 **좌표계(공간) 자체가 이동되었다.**

.

```c++
beginTransformation(); //이동 전 시작점을 지정.
translate(0.1f, 0.0f);

const vec2 p0(0.0f, 0.0f); 
const vec2 p1(0.5f, 0.5f);
const vec2 p2(0.5f, 0.0f);

drawLine(Colors::red, p0, Colors::blue, p1);
drawLine(Colors::red, p1, Colors::blue, p2);
drawLine(Colors::red, p2, Colors::blue, p0);

endTransformation(); //이동했던 좌표계가 원상태로 돌아옴.

translate(-0.1f, 0.0f);

drawLine(Colors::red, p0, Colors::blue, p1);
drawLine(Colors::red, p1, Colors::blue, p2);
drawLine(Colors::red, p2, Colors::blue, p0);
```

`result`

<img src="https://yeram522.github.io/assets/img/programming/cpp/2021-08-22-programming-cpp-game-lecture-1.JPG" width="300" height="300"/>

.

.

.

### 🕹 회전

```c++
drawWiredBox(Colors::gold, 0.5f, 0.22f);

rotate(30.0f);
drawWiredBox(Colors::skyblue, 0.5f, 0.22f);
```

`result` 👉 회전이 원점에서 이루어졌다.

<img src="https://yeram522.github.io/assets/img/programming/cpp/2021-08-22-programming-cpp-game-lecture-2.JPG" width="300" height="300"/>

.

```c++
setLineWidth(3.0f);

//원점 박스 생성(gold one)
drawWiredBox(Colors::gold, 0.5f, 0.25f);

//회전(blue one)
beginTransformation();
rotate(30.0f); //0.00위치에서 생성.
drawWiredBox(Colors::skyblue, 0.5f, 0.25f);
endTransformation();

//이동하면서 회전(red one)
beginTransformation();
translate(0.25f, 0.0f);
rotate(30.0f); //0.00위치에서 생성.
drawWiredBox(Colors::red, 0.5f, 0.25f);
endTransformation();
```

컴퓨터 그래픽스에 사용되는 API는 내부적으로 역순으로 진행된다.

`drawWiredBox` ▶ `rotate` ▶  `translate`    순으로 적용.

<img src="https://yeram522.github.io/assets/img/programming/cpp/2021-08-22-programming-cpp-game-lecture-3.JPG" width="300" height="300"/>

➕

`rotate와 translate 함수 순서를 바꾼 경우`

```c++
// blue one
beginTransformation();
rotate(30.0f); //0.00위치에서 생성.
translate(0.25f,0.0f);		
drawWiredBox(Colors::blue, 0.5f, 0.25f);
endTransformation();
```

`result` 

<img src="https://yeram522.github.io/assets/img/programming/cpp/2021-08-22-programming-cpp-game-lecture-4.JPG" width="300" height="300"/>

`회전은 무조건 원점기준으로 진행된다.`

<img src="https://yeram522.github.io/assets/img/programming/cpp/2021-08-22-programming-cpp-game-lecture-5.JPG" width="300" height="300"/>

⚠<span style = "color : red"> `translate`과 `rotate`의 순서가 달라지면, 결과도 달라진다!!</span>

.

.

.

### 🕹 원점이 아닌 곳에서의 회전

💡 <span style = "color:goldenrod">**원점이 아닌 점이 원점에 위치할 수 있도록 이동시킨 후 회전한다.**</span>

<img src="https://yeram522.github.io/assets/img/programming/cpp/2021-08-22-programming-cpp-game-lecture-6.JPG" width="300" height="300"/>

1. 물체를 통째로 들어서 원점이 아닌점이 원점에 위치하도록 한다.

<img src="https://yeram522.github.io/assets/img/programming/cpp/2021-08-22-programming-cpp-game-lecture-7.JPG" width="300" height="300"/>

```c++
setLineWidth(3.0f);

const vec2 center_of_rot(0.25f, 0.0f);

translate(-center_of_rot); // !
drawWiredBox(Colors::gold, 0.5f, 0.25f);
drawPoint(Colors::black, center_of_rot, 5.0f);
```

2. 원점에 대해서 회전

<img src="https://yeram522.github.io/assets/img/programming/cpp/2021-08-22-programming-cpp-game-lecture-8.JPG" width="300" height="300"/>

```c++
setLineWidth(3.0f);

const vec2 center_of_rot(0.25f, 0.0f);

rotate(45.0f);// !
translate(-center_of_rot);
drawWiredBox(Colors::gold, 0.5f, 0.25f);
drawPoint(Colors::black, center_of_rot, 5.0f);
```



3. 다시 원래 위치로 복원한다.

<img src="https://yeram522.github.io/assets/img/programming/cpp/2021-08-22-programming-cpp-game-lecture-9.JPG" width="300" height="300"/>

```c++
setLineWidth(3.0f);

const vec2 center_of_rot(0.25f, 0.0f);

translate(center_of_rot);
rotate(45.0f);
translate(-center_of_rot);
drawWiredBox(Colors::gold, 0.5f, 0.25f);
drawPoint(Colors::black, center_of_rot, 5.0f);
```

.

✔ 회전이 좌표중심이 아닌 검은점을 기준으로 회전된 것을 확인할 수 있다!

<img src="https://yeram522.github.io/assets/img/programming/cpp/2021-08-22-programming-cpp-game-lecture-10.JPG" width="300" height="300"/>

.

🔎`회전 기준점`을 변경했을때.

<img src="https://yeram522.github.io/assets/img/programming/cpp/2021-08-22-programming-cpp-game-lecture-11.JPG" width="300" height="300"/>

.

.

.

### 🕹 스케일링

```c++
setLineWidth(3.0f);
drawWiredBox(Colors::skyblue, 0.5f, 0.5f); //크기 조정 전(blue one)

scale(2.0f, 0.25f); // !
drawWiredBox(Colors::gold, 0.5f, 0.5f); //크기 조정 후(gold one)
```

<img src="https://yeram522.github.io/assets/img/programming/cpp/2021-08-22-programming-cpp-game-lecture-12.JPG" width="300" height="300"/>

.

`rotation과 animaion`

```c++
float time;

void update() override
{
   setLineWidth(3.0f);

   rotate(time * 10.0f);
   scale(2.0f, 0.25f);
   drawWiredBox(Colors::gold, 0.5f, 0.5f);

   time += this->getTimeStep();

}
```

<img src="https://yeram522.github.io/assets/img/programming/cpp/2021-08-22-programming-cpp-game-lecture-13.gif" width="300" height="300"/>

.

🔎 rotation과 scale의 순서를 바꾼경우

```c++
float time;

void update() override
{
   setLineWidth(3.0f);

    scale(2.0f, 0.25f);
	rotate(time * 10.0f);//rotation과 scale의 순서를 변경
    //컴파일러는 rotate먼저 실행함.
	drawWiredBox(Colors::gold, 0.5f, 0.5f);

	time += this->getTimeStep();

}
```

<img src="https://yeram522.github.io/assets/img/programming/cpp/2021-08-22-programming-cpp-game-lecture-14.gif" width="300" height="300"/>

.

`rotation과 animaion 그리고 translate`

1️⃣ ::  `translate`  ▶  `rotate` ▶`scale` 

```c++
float time;

void update() override
{
   setLineWidth(3.0f);

    scale(2.0f, 0.25f);
    rotate(time * 10.0f);
    translate(0.5f, 0.0f);
	drawWiredBox(Colors::gold, 0.5f, 0.5f);

	time += this->getTimeStep();

}
```

<img src="https://yeram522.github.io/assets/img/programming/cpp/2021-08-22-programming-cpp-game-lecture-15.gif" width="300" height="300"/>

✔ 회전하는 공간 자체가 scale이 되어있다.

.

2️⃣ ::  `scale` ▶ `translate`  ▶  `rotate` 

```c++
float time;

void update() override
{
   setLineWidth(3.0f);
   
   rotate(time * 10.0f);
   translate(0.5f, 0.0f);
   scale(2.0f, 0.25f);
   drawWiredBox(Colors::gold, 0.5f, 0.5f);

   time += this->getTimeStep();

}
```

<img src="https://yeram522.github.io/assets/img/programming/cpp/2021-08-22-programming-cpp-game-lecture-16.gif" width="300" height="300"/>

.

3️⃣ ::  `scale`  ▶ `rotate`   ▶  `translate` 

```c++
float time;

void update() override
{
   setLineWidth(3.0f);
    
   translate(0.5f, 0.0f);
   rotate(time * 10.0f);
   scale(2.0f, 0.25f);
   drawWiredBox(Colors::gold, 0.5f, 0.5f);

   time += this->getTimeStep();

}
```

<img src="https://yeram522.github.io/assets/img/programming/cpp/2021-08-22-programming-cpp-game-lecture-17.gif" width="300" height="300"/>

.

4️⃣ ::  `scale`  ▶ `rotate`   ▶  `translate`  ▶ `rotate`  

```c++
float time;

void update() override
{
   setLineWidth(3.0f);
    
   rotate(time * 10.0f);
    
   translate(0.5f, 0.0f);
   rotate(time * 10.0f);
   scale(2.0f, 0.25f);
   drawWiredBox(Colors::gold, 0.5f, 0.5f);

   time += this->getTimeStep();

}
```

<img src="https://yeram522.github.io/assets/img/programming/cpp/2021-08-22-programming-cpp-game-lecture-18.gif" width="300" height="300"/>

👀 자전도 하면서 공전도 하고 있다!



📑`21.08.21.SAT`

- `Union`에 대해서 알아보기.
- [Assignment](): Solar System 만들어보기(+태양이 자전하는 움직임도 포함해보기!)🌞
- [Assignment](): 얼굴 그리기

.

.

.

## 1.3 상호작용 맛보기: 키보드 입력과 반응

```c++
class MouseExample : public Game2D
	{
	public:
		void update() override
		{
			const vec2 mouse_pos = getCursorPos();
			
			if (this->isMouseButtonPressed(GLFW_MOUSE_BUTTON_1) == true)
			{
				translate(mouse_pos);
				drawFilledCircle(Colors::gold, 0.1f);
			}
		
			if (this->isMouseButtonPressed(GLFW_MOUSE_BUTTON_2))
			{
				translate(mouse_pos);
				drawFilledCircle(Colors::red, 0.1f);
			}
		}
	};
```



## 1.4 마우스 입력

