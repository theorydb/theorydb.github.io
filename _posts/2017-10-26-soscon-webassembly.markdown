---
layout: post
title:  "[SOSCON 2017] WebAssembly & Developer Toolkit"
subtitle:   "SOSCON"
categories: review
tags: event
comments: true
---

github.com/Samsung/WATT

## WebAssembly

### asm.js

자바스크립트 섭셋

단점 여전히 자바스크립트

### pNaCl 포터블 네이티브 클라이언트

네이티브코드의 안전한 구동

단점 크로미움만 지원

### WebAssembly

W3C에 워킹 그룹을 결성하여 asm.js 와 PNaCl에 영감을 받아 모든 벤더에 적용가능하게

실행속도가 빠르다. 크기가 작다.

쓰기가 어렵지 않다. 하드웨어 디펜던시가 없다.

하이퍼포먼스 게임, 피직스, 멀티미디어쪽에서 효과적임.

C/C++/Rust 등을 이용해 코딩하고 컴파일하면 WASM bytecode가 나옴. 

JS에서 WASM을 로드해서 사용해야함.


## Performance Enhancement

WASM을 네트워크로 받아오는 시간

디코드 컴파일 실행하는 시간

WebGL로 그리는 것 부스트

---

코드 캐시 - 와즘 컴파일된 코드를 캐시하는 법. 물론 처음 한번은 컴파일해야함. 재방문시 유리.

WASM Compactization - 와즘 파일을 컴팩하게 익스포트해서 받아옴

V8 Features

- Parallel Compilation

펑션단위로 컴파일

- WASM Optimization

AST파일을 최적화 함.

---

Direct Canvas


## WebAssembly Translation Toolkit

WATT

웹어셈블리 라이브러리와 웹앱을 작성할 수 있는 IDE

Unity와 Unreal로 만들어진걸 WASM으로 컴파일하면 사용 할 수 있음.

Emscripten - LLVM 기반의 컴파일러






