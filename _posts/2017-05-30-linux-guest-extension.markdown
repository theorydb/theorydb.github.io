---
layout: post
title:  "[리눅스]가상머신(virtualBox)에서 게스트 확장(드래그앤드롭, 클립보드 공유, 전체화면) 하기"
subtitle:   "가상머신(virtualBox)에서 게스트 확장(드래그앤드롭, 클립보드 공유, 전체화면) 하기"
categories:  devlog
tags: linux guest

---


이번 포스팅에서는 가상머신 oracle virtualBox에서 호스트pc와 드래그 앤 드롭, 클립보드 공유, 전체화면을 하는 방법을 알아보겠습니다.

### 0.개요

호스트pc와 가상머신간의 데이터를 편하게 이동할 수 있도록 하고 싶은데 보통 초기 설정만으로는 잘 되지 않습니다. 그럴 때 드래그 앤 드롭, 클립보드 공유, 전체화면 등을 할 수 있는 방법이 있습니다. 가상머신에 게스트 확장모드를 설치하면 가능하게 됩니다.

### 1.게스트확장 하기

[![](http://postfiles5.naver.net/20160323_196/zooqzqz_1458663975606uWlMX_PNG/1.PNG?type=w773)](#)

#### 가상머신의 장치에서 '게스트 확장 CD 이미지 삽입..'을 클릭합니다.

[![](http://postfiles6.naver.net/20160323_197/zooqzqz_1458663975891yt55u_PNG/2.PNG?type=w773)](#)

[![](http://postfiles5.naver.net/20160323_164/zooqzqz_1458663976075gve5y_PNG/3.PNG?type=w773)](#)

#### 확인을 누르면 게스트 확장 모드가 설치가 됩니다. 설치가 완료되면 전체화면, 드래그앤드롭, 클립보드 공유가 가능해집니다.

[![](http://postfiles8.naver.net/20160323_199/zooqzqz_1458664441576mewbB_PNG/3-1.PNG?type=w773)](#)

[![](http://postfiles9.naver.net/20160323_216/zooqzqz_1458664441843db9ew_PNG/3-2.PNG?type=w773)](#)

#### 설치가 되었다면 장치의 '클립보드 공유'->'양방향' ,'드래그 앤 드롭'->'양방향'을 선택해 줍니다.

### 2.마치며

virtualBox에서 드래그앤드롭, 클립보드 사용을 하려고 엄청 헤메었던 적이 있습니다. 저같은 분이 없으시길 바라며 이 포스팅을 올립니다.

[![스티커 이미지](http://gfmarket.phinf.naver.net/cony_special/original_31.png?type=p50_50)](#)
