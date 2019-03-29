---
layout: post
title:  "[리눅스] 라즈베리파이 무선랜 연결하기"
subtitle:   "라즈베리파이에 무선랜을 설정해보자."
categories:  devlog
tags: linux raspberrypi wlan
---

라즈베리파이 무선랜을 설정해보겠습니다.

저도 여러블로그를 통해 시도해보았는데 안되더라구요. 겨우 방법을 찾아서 방법을 공유합니다.

p.s.이 포스트는 씨리얼을 통해 통신합니다. gui를 통해 다루시는 분들은 과정2번부터 확인하시면 됩니다.

### 0.라즈베리파이 무선랜 설정과정

> 과정1. 씨리얼 통신하기.

> 과정2. 무선랜 연결하기.

### 1.라즈베리파이 무선랜 설정하기

#### 과정1. 씨리얼 통신하기

[![](http://postfiles11.naver.net/20160405_10/zooqzqz_1459835799041BEoP7_PNG/1-1.PNG?type=w773)](#)

1.씨리얼이 연결된 USB포트 검색

[![](http://postfiles9.naver.net/20160405_200/zooqzqz_1459835799182EnnCT_PNG/1-2.PNG?type=w773)](#)

[![](http://postfiles2.naver.net/20160405_209/zooqzqz_1459835799527qYApk_PNG/1-3.PNG?type=w773)](#)

2.다운받은 라즈비언 이미지를 Win32 Disk Imager로 sd카드의 부트 이미지로 만듭니다.

[![](http://postfiles3.naver.net/20160405_98/zooqzqz_1459835799838f1tSH_PNG/2-1.PNG?type=w773)](#)

3.$minicom -s 명령으로 미니컴 설정으로 진입합니다.

[![](http://postfiles15.naver.net/20160405_62/zooqzqz_145983579999219jVg_PNG/2-2.PNG?type=w773)](#)

4.sereal port setup을 선책하여 디바이스를 미리 검색해둔 디바이스로 설정합니다.

[![](http://postfiles5.naver.net/20160405_4/zooqzqz_1459835800352kNGek_PNG/2-3.PNG?type=w773)](#)

5.미니컴에 진입하고 씨리얼로 연결된 라즈베리파이에 전원을 넣으면

[![](http://postfiles4.naver.net/20160405_291/zooqzqz_1459835800582QvERK_PNG/2-4.PNG?type=w773)](#)

5-1.라즈베리파이와 씨리얼 통신이 됩니다.

#### 과정2. 무선랜 연결하기

[![](http://postfiles1.naver.net/20160405_128/zooqzqz_1459835801162awOxq_PNG/3-1.PNG?type=w773)](#)

6.사용자 pi로 접속하고 라즈베리파이에 삽입된 랜카드가 잡혔는지 $lsusb 명령으로 확인합니다.

리얼텍 WLAN adapter라고 잡힙니다.

[![](http://postfiles4.naver.net/20160405_275/zooqzqz_1459835801499npMJs_PNG/3-2.PNG?type=w773)](#)

7.$ifconfig로 네트워크 상태를 확인해 보니 wlan0에 inet주소가 배정되어 있지 않습니다.

무선인터넷에 연결되지 않았기 때문입니다.

[![](http://postfiles3.naver.net/20160405_210/zooqzqz_14598358022749puxS_PNG/3-5.PNG?type=w773)](#)

8.무선랜 연결에 참조하는 wpa_supplicant.conf 파일에 무선랜 정보를 입력합니다. 제 설정을 개방형 ap의 경우 설정입니다.

일반적인 경우는 아래와 같이 하시면 되실겁니다.

```

network={

    ssid="와이파이 이름"

    psk="패스워드"

    key_mgmt=WPA-PSK

}

```

[![](http://postfiles16.naver.net/20160405_159/zooqzqz_1459835802804fKu4k_PNG/4-3.PNG?type=w773)](#)

8-1. wlan0이 연결될때 dhcp방식으로 연결될 수 있도록 네트워크 interfaces파일도 수정해주었습니다.

[![](http://postfiles8.naver.net/20160405_279/zooqzqz_1459835802417ATcvV_PNG/4-1.PNG?type=w773)](#)

9.wlan0를 다시 셋업해주고 $ifconfig로 네트워크 상태를 확인해보면

[![](http://postfiles5.naver.net/20160405_36/zooqzqz_1459835802575wSB6J_PNG/4-2.PNG?type=w773)](#)

10.wlan0에 inet주소가 할당되었습니다.

[![](http://postfiles3.naver.net/20160405_34/zooqzqz_1459835802965a2tGN_PNG/4-4.PNG?type=w773)](#)

10-1.연결된 ap도 알맞게 나옵니다.

[![](http://postfiles11.naver.net/20160405_42/zooqzqz_1459835803255lUisU_PNG/4-5.PNG?type=w773)](#)

10-2.핑을 보내보니 잘 전달되는게 무선랜이 제대로 연결이 되었습니다.

[![](http://postfiles16.naver.net/20160405_95/zooqzqz_14598358036217qCuR_PNG/4-7.PNG?type=w773)](#)

11.무선랜을 잡았으니 라즈베리파이를 업데이트 해줍니다. $sudo apt-get update

[![](http://postfiles6.naver.net/20160405_117/zooqzqz_1459835803832R7wPE_PNG/4-8.PNG?type=w773)](#)

12.업데이트가 완료되었습니다.

### 2.마치며

라즈베리파이 무선랜 설정을 했습니다. 보통은 다른 여러 블로그들의 일반적인 방법으로 되실텐데 안되시는 분들은 제 방법을 따라해보시는것도 좋을것 같습니다. 몇시간 동안 헤메서 저도 겨우 해냈네요.

좋은하루 되세요!
