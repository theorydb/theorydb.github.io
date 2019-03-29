---
layout: post
title:  "[리눅스] 라즈베리파이 시스템 콜 추가하기"
subtitle:   "라즈베리파이에 시스템 콜을 추가해보자."
categories:  devlog
tags: linux raspberrypi systemcall
---

라즈베리 파이에 시스템 콜을 추가해보도록 하겠습니다.

### 순서

> 과정1.크로스 컴파일 설정


> 과정2.시스템 콜 추가

## 1.라즈베리파이 시스템 콜 추가
---

### 과정1.크로스 컴파일 설정

[![](http://postfiles2.naver.net/20160424_177/zooqzqz_1461481203041N6a5T_PNG/1.PNG?type=w773)](#)

1.작업을 진행할 디렉토리를 생성합니다.

[![](http://postfiles14.naver.net/20160424_45/zooqzqz_1461481203354OjTb3_PNG/2.PNG?type=w773)](#)
2.git 및 개발도구를 다운로드합니다.

[![](http://postfiles12.naver.net/20160424_283/zooqzqz_1461481203516pIWyB_PNG/3.PNG?type=w773)](#)

[![](http://postfiles15.naver.net/20160424_158/zooqzqz_1461481203722pjJ1g_PNG/4.PNG?type=w773)](#)
3.커널 소스를 다운로드 하고 다운로드한 커널 버전을 확입합니다.

[![](http://postfiles11.naver.net/20160424_122/zooqzqz_1461481203948hzGu6_PNG/5.PNG?type=w773)](#)

4.디렉토리를 옮겨 크로스 툴체인을 다운로드합니다.


[![](http://postfiles2.naver.net/20160424_273/zooqzqz_1461481204286F0PAo_PNG/6.PNG?type=w773)](#)

5.크로스 컴파일러를 실행해봅니다.

[![](http://postfiles7.naver.net/20160424_198/zooqzqz_1461481204527mgTjo_PNG/6-1.PNG?type=w773)](#)

6.환경변수 PATH에 실행 경로 추가한 뒤 실행경로 테스트해 봅니다.

[![](http://postfiles6.naver.net/20160424_101/zooqzqz_1461481204688i0AqG_PNG/7.PNG?type=w773)](#)

7.크로스 컴파일 prefix를 설정하고 설정파일을 만듭니다.

   [![](http://postfiles12.naver.net/20160424_251/zooqzqz_1461481205062IamwI_PNG/8-1.PNG?type=w773)](#)

   [![](http://postfiles8.naver.net/20160424_135/zooqzqz_1461481205231PNUbh_PNG/9.PNG?type=w773)](#)

8.#make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- zImage modules dtbs -j5 명령어로 zImage를 만들고 확인해봅니다.

[![](http://postfiles13.naver.net/20160424_108/zooqzqz_1461481205687SnzYj_PNG/11.PNG?type=w773)](#)

9.#lsblk로 연결 된 블록 디바이스 목록을 보고 sd카드 연결을 확인합니다..

[![](http://postfiles3.naver.net/20160424_18/zooqzqz_1461481205935JBbXc_PNG/12-1.PNG?type=w773)](#)

10.마운트 시킬 디렉토리를 만들고 sd카드와 마운트 시킵니다.

[![](http://postfiles9.naver.net/20160424_296/zooqzqz_1461481206141KMaWs_PNG/13.PNG?type=w773)](#)

11.모듈을 sd카드에 복사합니다.

[![](http://postfiles16.naver.net/20160424_63/zooqzqz_1461481206307e12IA_PNG/14.PNG?type=w773)](#)

12.커널 이미지를 백업하고 복사합니다. Device Tree blobs도 복사하고 마운트를 해재하고 미니컴으로 라즈베리파이를 연결합니다.

[![](http://postfiles13.naver.net/20160424_252/zooqzqz_1461481206777ohw1A_PNG/15.PNG?type=w773)](#)

13.(minicom)커널 버전을 확인합니다.

### 과정2. 시스템 콜 추가하기

[![](http://postfiles2.naver.net/20160424_1/zooqzqz_1461481206972CKqWT_PNG/16.PNG?type=w773)](#)

1.시스템 콜 번호를 arch/arm/include/uapi/asm/unistd.h에 추가합니다.

[![](http://postfiles11.naver.net/20160424_42/zooqzqz_1461481207284dIdzh_PNG/17.PNG?type=w773)](#)

1-1.총 시스템 콜의 갯수를 확인합니다. 392개라고 적혀있습니다.

[![](http://postfiles13.naver.net/20160424_236/zooqzqz_1461481207449601CR_PNG/18.PNG?type=w773)](#)

2.arch/arm/kernel/calls./s에 시스템 콜 처리함수를 등록합니다.

[![](http://postfiles5.naver.net/20160424_180/zooqzqz_1461481207647DL2IK_PNG/19.PNG?type=w773)](#)

3.include/linux/syscalls.h에 시스템 콜 함수 원형을 선언합니다.

[![](http://postfiles11.naver.net/20160424_266/zooqzqz_14614812078913n0w1_PNG/20.PNG?type=w773)](#)

4.커널에 포함되어 컴파일 해야하므로 kernel아래에 mysyscall.c함수를 작성합니다.

[![](http://postfiles2.naver.net/20160424_273/zooqzqz_1461481208105Klayn_PNG/21.PNG?type=w773)](#)

5.Makefile을 수정합니다.

[![](http://postfiles4.naver.net/20160424_131/zooqzqz_1461481208278Vm2qJ_PNG/22.PNG?type=w773)](#)

6.커널 컴파일을 진행합니다.

[![](http://postfiles1.naver.net/20160424_192/zooqzqz_1461481208490LjByh_PNG/23.PNG?type=w773)](#)

7.sd카드와 연결을 확인합니다.

[![](http://postfiles11.naver.net/20160424_202/zooqzqz_1461481208775lnkoC_PNG/24.PNG?type=w773)](#)

8.디렉토리를 마운트하고 커널 이미지 백업, 복사, dtb복사를 합니다.

[![](http://postfiles4.naver.net/20160424_291/zooqzqz_1461481209102fusw7_PNG/24-1.PNG?type=w773)](#)

9.마운트를 해제합니다.

[![](http://postfiles12.naver.net/20160424_139/zooqzqz_1461481209313vKaTo_PNG/25-1.PNG?type=w773)](#)

10.(minicom)미니컴에서 응용프로그램을 작성합니다.

[![](http://postfiles5.naver.net/20160424_260/zooqzqz_1461481209721cFRr0_PNG/26-1.PNG?type=w773)](#)

11.(minicom)컴파일하고 결과물을 실행합니다.

[![](http://postfiles2.naver.net/20160424_1/zooqzqz_1461481209605g3te0_PNG/26.PNG?type=w773)](#)

12.(minicom)커널 메세지를 확인해보니 정상적으로 작동합니다.

## 2.마치며
---

라즈베리파이에도 시스템콜을 추가해보았습니다. 시스템 콜 추가라는게 사실은 리눅스 기반의 OS에서는 대동소이 합니다. 크로스 컴파일이라는 기능은 쉽게 말해 다른 시스템의 기계에서 실행될수 있도록 컴파일 하는 것을 말합니다. 크로스컴파일을 통하면 여러가지 기계에서 쓸 수 있는 프로그램을 만들 수 있겠지요.

좋은하루되세요!
