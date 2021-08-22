---
layout: post
title: "[c++]gamepack:1장 과제"
subtitle: "Making Solar System and Drawing Face"
categories: programming
tags: cpp opengl gamedev assignment
comments: true
header-img: img/programming/cpp/0000-00-00-programming-cpp-making-solar-system-and-drawing-face-cover.JPG
---

> `홍정모`교수님의 `게임 만들기 연습 문제 패키지`를 수강하고 작성한 문서이다.
>
> 교수님이 내주신 `과제`에 대한 해결을 담고 있다.
>
> ✔태양계 움직임 나타내기 ✔ 도형을 이용한 그림 그리기.

---

## jm::SolarSystem().run();

<img src="https://yeram522.github.io/assets/img/programming/cpp/0000-00-00-programming-cpp-making-solar-system-and-drawing-face-cover.JPG" width="300" height="300"/>

🧐 위의 그림처럼 멈춰있는 행성들이 각각 자전과 공전을 하도록 만들어라.

`SolarSystme.h`  _//예제 코드_

```c++

	class SolarSystem : public Game2D
	{
		float time = 0.0f;

	public:
		void update() override
		{
			beginTransformation();
			{
				
				//rotate(10.f * time);
				drawFilledStar(Colors::gold, 0.2f, 0.13f);	// Sun

				//rotate(15.f * time);
				translate(0.5f, 0.0f);
				drawFilledCircle(Colors::blue, 0.1f);		// Earth

				//rotate(90.f * time);
				translate(0.2f, 0.0f);				
				drawFilledCircle(Colors::yellow, 0.05f);	// Moon
			}
			endTransformation();

			time += this->getTimeStep();

		}
	};
```



⚒ 달이 지구를 공전하도록 만들기.

<img src="https://yeram522.github.io/assets/img/programming/cpp/2021-08-22-programming-cpp-making-solar-system-and-drawing-face-1.gif" width="300" height="300"/>

```c++
beginTransformation();
{
   drawFilledStar(Colors::gold, 0.2f, 0.13f);	// Sun

   translate(0.5f, 0.0f);
   drawFilledCircle(Colors::blue, 0.1f);		// Earth

   rotate(90.f * time);
   translate(0.2f, 0.0f);				
   drawFilledCircle(Colors::yellow, 0.05f);	// Moon
}
endTransformation();
```

<img src="https://yeram522.github.io/assets/img/programming/cpp/2021-08-23-programming-cpp-making-solar-system-and-drawing-face-2.JPG" width="300" height="300"/>

🔎 `rotate(회전)`은 원점을 중심으로 이루어지기 때문에, 0.2f를 이동한 상태에서 회전을 하고, 지구 도형과 같이 0.5f 평행이동 하므로 달이 지구를 공전 하는 것 처럼 보이는 것이다.

.

.

⚒ 지구가 태양을 공전하도록 만들기.

<img src="https://yeram522.github.io/assets/img/programming/cpp/2021-08-23-programming-cpp-making-solar-system-and-drawing-face-3.gif" width="300" height="300"/>

```c++
beginTransformation();
{
   drawFilledStar(Colors::gold, 0.2f, 0.13f);	// Sun

   rotate(15.f * time);
   translate(0.5f, 0.0f);
   drawFilledCircle(Colors::blue, 0.1f);		// Earth

   rotate(90.f * time);
   translate(0.2f, 0.0f);				
   drawFilledCircle(Colors::yellow, 0.05f);	// Moon
}
endTransformation();
```

👉 0.5만큼 이동시킨 후 회전을 시키면, 0.5f만큼의 반지름을 그리면서 지구가 태양을 공전한다.



⚒ 태양이 자전 하도록 만들기.

<img src="https://yeram522.github.io/assets/img/programming/cpp/2021-08-23-programming-cpp-making-solar-system-and-drawing-face-4.gif" width="300" height="300"/>

```c++
beginTransformation();
{
   rotate(10.f * time);
   drawFilledStar(Colors::gold, 0.2f, 0.13f);	// Sun

   rotate(15.f * time);
   translate(0.5f, 0.0f);
   drawFilledCircle(Colors::blue, 0.1f);		// Earth

   rotate(90.f * time);
   translate(0.2f, 0.0f);				
   drawFilledCircle(Colors::yellow, 0.05f);	// Moon
}
endTransformation();
```

👉 태양을 그린 후 회전을 시키면, 태양이 그려진 원점을 중심으로 회전이 진행되기 때문에, 그 자리에서 회전을 한다.

---

## jm::FaceExample().run();

<img src="https://yeram522.github.io/assets/img/programming/cpp/2021-08-23-programming-cpp-making-solar-system-and-drawing-face-5.gif.gif" width="300" height="300"/>

🧐 위의 예제 그림처럼 자신만의 얼굴을 만들자!

나는 요즘 핫한 춘식이를 만들어 보았다...😊

<img src="https://yeram522.github.io/assets/img/programming/cpp/2021-08-23-programming-cpp-making-solar-system-and-drawing-face-6.JPG" width="300" height="300"/>

```c++

class FaceExample : public Game2D
{
public:
	void update() override
	{
		// 춘식이 얼굴
		beginTransformation();
		{
			scale(1.125f, 1.0f);
			drawFilledCircle(Colors::babyyellow, 0.7f); // draw background object first
		}
		endTransformation();
	
		// 춘식이 left eye
		beginTransformation();
		{
			translate(-0.232f, 0.2f);
			drawFilledCircle(Colors::black, 0.0435f);
		}
		endTransformation();
        
		// 춘식이 right eye
		beginTransformation();
		{
			translate(0.232f, 0.2f);
			drawFilledCircle(Colors::black, 0.0435f);
		}
		endTransformation();

		translate(0.0f, -0.03f); //춘식이 하관 비율조정

		// 춘식이 오른쪽 수염
		beginTransformation();
		{
			setLineWidth(10.0f);

			const vec2 p0(0.1f, -0.038f);
			const vec2 p1(0.29f, 0.032f);

			const vec2 p2(0.1f, -0.08f);
			const vec2 p3(0.3f, -0.14f);
            
		    drawLine(Colors::black, p0, Colors::black, p1);
			drawLine(Colors::black, p2, Colors::black, p3);
		}
		endTransformation();

		// 춘식이 왼쪽 수염 -> 오른쪽수염의 y축 대칭!
		beginTransformation();
		{
			setLineWidth(10.0f);

			const vec2 p0(-0.1f, -0.038f);
			const vec2 p1(-0.29f, 0.032f);

			const vec2 p2(-0.1f, -0.08f);
			const vec2 p3(-0.3f, -0.14f);


			drawLine(Colors::black, p0, Colors::black, p1);
			drawLine(Colors::black, p2, Colors::black, p3);
		}
		endTransformation();

		// 춘식이 오른쪽 코
		beginTransformation();
		{
	    	rotate(-25.0f);		// 10 degrees rotated 
			scale(1.0f, 0.7f);
			translate(0.07f, -0.05f);
			drawFilledCircle(Colors::white, 0.165f);
		}
    	endTransformation();

		// 춘식이 왼쪽 코
		beginTransformation();
		{
			rotate(25.0f);		// 10 degrees rotated 
			scale(1.0f,0.7f);
			translate(-0.07f, -0.05f);
			drawFilledCircle(Colors::white, 0.165f);
		}
		endTransformation();

		beginTransformation();
		{
			// 춘식이 왼쪽 귀			
		    rotate(40.0f);
			translate(0.0f, 0.725f);
			rotate(1.0f);
			scale(1.5f, 1.4f);
			drawFilledCircle(Colors::babyyellow, 0.1f); // draw background object first
		}
		endTransformation();
        
		beginTransformation();
		{
			// 춘식이 오른쪽 귀			
			rotate(-40.0f);
			translate(0.0f, 0.725f);
			rotate(-1.0f);
			scale(1.5f, 1.4f);
			drawFilledCircle(Colors::babyyellow, 0.1f); // draw background object first
		}
		endTransformation();

	}
};
```

