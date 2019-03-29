---
layout: post
title:  "[리눅스]가상머신(virtualBox)에 리눅스(Fedora18) 설치하기"
subtitle:   "가상머신(virtualBox)에 리눅스(Fedora18) 설치하기"
categories:  devlog
tags: linux install

---


오늘은 오라클 버츄얼박스(Oracle virtualBox)에 페도라(fedora) 리눅스를 설치해보도록 하겠습니다.

저는 사정이 있어 페도라 18버전을 설치하고자 합니다. 각자 가지고 계신 버전에 맞게 설치하시면 됩니다. 버전이 다르다고 다른점이 몇가지 없고 어느 부분을 고려해야 하는지도 살펴볼테니 천천히 따라하면서 보시면 문제 없이 잘 설치 될 것입니다.

### 0.사전준비

#### virtualBox 또는 vmWare같은 가상머신 프로그램을 설치합니다.

저는 virtualBox를 선택했습니다. 버츄얼 박스는 [이 곳](https://www.virtualbox.org/)에서 다운로드 하실 수 있습니다.

#### Fedora 운영체제의 이미지파일(.iso)를 구하시면 됩니다.

무료운영체제이기때문에 최신판은 https://getfedora.org/ 에서 배급하고 있습니다.

### 1.FEDORA 설치하기

[![](http://postfiles1.naver.net/20160315_144/zooqzqz_1458028834481NPfte_PNG/1.PNG?type=w773)](#)

[![](http://postfiles6.naver.net/20160315_197/zooqzqz_14580288389764E4Oq_PNG/%C4%B8%C3%B3.PNG?type=w773)](#)

1.첫 째로 virtualBox를 실행하고 새로만들기를 클릭합니다. 제가 가지고있는 이미지 파일은 32bit fedora이기 때문에 Fedora(32-bit)를 선택하였습니다. 저는 포스팅전에 미리 몇번 깔아보았기 때문에 두개의 가상머신이 이미 있네요.

[![](http://postfiles3.naver.net/20160315_226/zooqzqz_1458028834676vFp6V_PNG/2.PNG?type=w773)](#)

2.새로만들기를 누르시면 가상머신이 할당받을 메모리를 설정하는 창이 나옵니다. 자신의 메모리의 양을 고려하여 알뜰하게 나누어 주시기 바랍니다. (저같은 경우는 가상머신을 사용할 땐 다른 것을 잘 안하기 때문에 좀 많이 주었습니다. )

[![](http://postfiles3.naver.net/20160315_258/zooqzqz_1458028834976eS3F0_PNG/3.PNG?type=w773)](#)

[![](http://postfiles5.naver.net/20160315_196/zooqzqz_1458028835196FOPWE_PNG/4.PNG?type=w773)](#)

[![](http://postfiles10.naver.net/20160315_217/zooqzqz_1458028835396ahHfg_PNG/5.PNG?type=w773)](#)

3.가상머신이 사용할 디스크 크기를 할당해 줍니다. 동적할당을 해주면 속도가 조금 느려서 저는 고정할당을 하도록 하겠습니다.

[![](http://postfiles3.naver.net/20160315_114/zooqzqz_1458028835612laSto_PNG/6.PNG?type=w773)](#)

[![](http://postfiles15.naver.net/20160315_14/zooqzqz_1458028835820fTesQ_PNG/7.PNG?type=w773)](#)


4.가상머신의 이름과 디스크 크기를 정해줍니다. 저는 이름은 fedora-18-basic으로 정하고 커널컴파일등 여러가지 행동을 할 예정이라 넉넉하게 디스크를 주었습니다. 만들기를 클릭하고 잠시 기다리면 가상머신이 생성됩니다.

[![](http://postfiles4.naver.net/20160315_99/zooqzqz_1458028835984wNwrj_PNG/8.PNG?type=w773)](#)

5, 자, 이제 가상머신에 페도라를 설치합니다. 페도라 운영체제 이미지를 삽입하기 위해 저장소를 클릭합니다.

[![](http://postfiles6.naver.net/20160315_37/zooqzqz_1458028836151O6W4c_PNG/9.PNG?type=w773)](#)


[![](http://postfiles4.naver.net/20160315_35/zooqzqz_14580288363452dIPE_PNG/10.PNG?type=w773)](#)

6.컨트롤러:IDE의 비어있음을 클릭하고 광학 드라이브 오른쪽 CD버튼을 클릭하여 자신이 가진 운영체제 이미지 파일을 삽입합니다.

[![](http://postfiles10.naver.net/20160315_137/zooqzqz_1458028836484v8rv5_PNG/11.PNG?type=w773)](#)

[![](http://postfiles6.naver.net/20160315_5/zooqzqz_1458028836737qe1gu_PNG/12.PNG?type=w773)](#)

7.이미지를 삽입하고 가상머신을 실행하면 이런 화면이 나옵니다. Test this media & install Fedora에 포커스를 두고 엔터를 눌르면 간단한 검사 후 페도라를 설치합니다.

[![](http://postfiles13.naver.net/20160315_204/zooqzqz_1458028836894FWiSf_PNG/13.PNG?type=w773)](#)

8.언어 설정입니다. 저는 한국인이기 때문에 한국어로 설정하고 키보드 레이아웃도 동일하게 설정하겠습니다.

[![](http://postfiles6.naver.net/20160315_229/zooqzqz_1458028837064558JM_PNG/14.PNG?type=w773)](#)

9.이부분에선 '!'가 떠있는 것들을 설정해 주어야합니다. 그 전에 저는 기본적으로 설치 될 소프트웨어 설정을 해보겠습니다.

[![](http://postfiles10.naver.net/20160315_41/zooqzqz_1458028837448AjF9L_PNG/15.PNG?type=w773)](#)

10.저는 페도라 운영체제를 개발용으로 사용할 것이기 때문에 환경을 'Develop...'으로 설정하고 제게 필요할 것 같은 도구들을 설치하겠습니다. 그냥 GNOME이나 다른 어떤것으로 설치하셔도 무방합니다.


[![](http://postfiles12.naver.net/20160315_75/zooqzqz_1458028837647UQRJy_PNG/16.PNG?type=w773)](#)

11.그 다음 느낌표가 떠있는 '설치 목적지'를 설정해보겠습니다.

[![](http://postfiles7.naver.net/20160315_6/zooqzqz_1458028837824e6YxI_PNG/17.PNG?type=w773)](#)

[![](http://postfiles12.naver.net/20160315_91/zooqzqz_1458028838062vcgUq_PNG/18.PNG?type=w773)](#)

12.그냥 들어가서 완료를 누르면 됩니다. 오른쪽아래 설치버튼을 누르면 다음 스탭으로 진행됩니다.

[![](http://postfiles2.naver.net/20160315_49/zooqzqz_1458028838175w9Alt_PNG/19.PNG?type=w773)](#)

[![](http://postfiles4.naver.net/20160315_19/zooqzqz_1458028838352EF4GE_PNG/20.PNG?type=w773)](#)

13.루트 계정을 설정하라고합니다. 길고 복잡한 암호가 아니면 경고가 나오는데 무시하고 완료를 두번누르면 설정됩니다.

[![](http://postfiles11.naver.net/20160315_58/zooqzqz_1458028838473me3pT_PNG/21.PNG?type=w773)](#)

14.루트를 설정하고 설치가 완료되었다면 재부팅을 누릅니다.

[![](http://postfiles15.naver.net/20160315_254/zooqzqz_1458028838644GnGOH_PNG/22.PNG?type=w773)](#)

15.광학드라이브에 설치디스크가 들어있으면 다시 설치하는 창으로 가므로 오른쪽 Cd모양을 눌러 '광학드라이브를 꺼내기' 해줍니다.

[![](http://postfiles3.naver.net/20160315_130/zooqzqz_1458028838768hyxY1_PNG/23.PNG?type=w773)](#)

16.짠! 페도라가 설치되었습니다! 이제 여러분은 가상머신에서 페도라 운영체제를 사용할 수 있게되었습니다.

### 2.설치 완료

가상머신에 페도라를 설치하는 방법은 어렵지 않습니다. 자신이 가진 운영체제 이미지 파일에 맞춰 32비트 또는 64비트 머신을 만들고 보통의 운영체제 설치방법처럼 설치하게 됩니다. 이제 여러분은 다양한 가상운영체제를 설치하실 수 있게 되었습니다.

다음에는 가상머신의 간단한 설정과 게스트모드 확장에대해 알아보겠습니다.

감사합니다.
