---
layout: post
title:  "[리눅스]리눅스 시스템 콜(system call) 추가하기"
subtitle:   "리눅스 시스템 콜(system call) 추가하기"
categories:  devlog
tags: linux systemcall

---

오늘은 리눅스 페도라 운영체제에서 시스템콜을 추가해 보도록 하겠습니다. 시스템 콜이란 '사용자가 일반적으로 접근할 수 없는 커널 메모리, 커널 데이터 등을 사용자가 이용하기 위한 인터페이스' 라고 할 수 있습니다.

### 0.시스템 콜 추가 방법

시스템 콜을 추가하는 절차에 대해 미리 알고 시작하도록 하겠습니다.

> 과정 1. 시스템 콜 테이블 등록

> 과정 2. 시스템 콜 함수 원형 선언

> 과정 3. 시스템 콜 처리 함수 구현

> 과정 4. 커널 컴파일 및 재부팅

> 과정 5. 시스템 콜을 사용하는 프로그램 및 라이브러리 작성

### 1.시스템 콜 추가하기.

#### 과정 1. 시스템 콜 테이블 등록

[![](http://postfiles2.naver.net/20160320_273/zooqzqz_14584011511083BhNI_PNG/1.PNG?type=w773)](#)

1.컴파일된 리눅스 커널의 'arch/x86/syscalls/syscall_32.tbl'에 시스템 콜을 추가합니다. 64비트 운영체제라면 syscalls_64.tbl에 자신이 등록하고 싶은 시스템 콜을 추가합니다.

[![](http://postfiles10.naver.net/20160320_201/zooqzqz_14584011513464LLG0_PNG/2.PNG?type=w773)](#)

2.'시스템콜번호 시스템 시스템콜이름 sys_시스템콜이름'의 형식으로 시스템 콜을 추가합니다. 이 때 시스템 콜 번호를 메모해 놓으세요!

#### 과정2. 시스템 콜 함수 원형 선언

[![](http://postfiles7.naver.net/20160320_86/zooqzqz_1458401151505pEKib_PNG/3.PNG?type=w773)](#)

3.시스템 콜 처리 함수는 시스템 콜 테이블에 등록이 되어있어야 합니다. 등록을 위해 커널의 'include/linux/syscalls.h'를 편집합니다.

[![](http://postfiles14.naver.net/20160320_253/zooqzqz_1458401151657PfbaU_PNG/4.PNG?type=w773)](#)

4.#endif전에 'asmlinkage 리턴데이터형 sys_시스템콜이름(인자)'의 형식으로 시스템콜을 테이블에 등록합니다.

#### 과정3. 시스템 콜 처리 함수 구현

[![](http://postfiles3.naver.net/20160320_18/zooqzqz_1458401151762l4SN3_PNG/5.PNG?type=w773)](#)

5.이제 테이블에 등록한 시스템콜 처리 함수를 구현합니다. 그러기위해 컴파일된 커널 밑에 'kenel'에 c 파일을 생성합니다. 파일의 이름은 시스템콜이름과 달라도 되지만 함수는 'sys_시스템콜이름'으로 만들어주세요.


[![](http://postfiles15.naver.net/20160320_286/zooqzqz_1458401152047lBKvC_PNG/6.PNG?type=w773)](#)

5-1.저는 간단하게 이런식으로 구현했습니다.

[![](http://postfiles12.naver.net/20160320_219/zooqzqz_1458401152214VKNeA_PNG/7.PNG?type=w773)](#)

6.이제 시스템콜을 커널에 built-in 시키기 위해 'kernel'의 Makefile을 편집합니다. 'vi Makefile'

#### 과정4. 커널 이미지 재생성

[![](http://postfiles9.naver.net/20160320_8/zooqzqz_1458401152349dkoBT_PNG/8.PNG?type=w773)](#)

[![](http://postfiles16.naver.net/20160320_15/zooqzqz_1458401152708FX1su_PNG/9.PNG?type=w773)](#)

7.이미 커널 컴파일을 하셨다면 System.map과 initrd.img 파일이 이미 '/boot' 디렉토리에 있을 것입니다. 'make bzImage'로 커널 이미지만 새로만들겠습니다.

[![](http://postfiles14.naver.net/20160320_285/zooqzqz_14584011529345Xu9t_PNG/10.PNG?type=w773)](#)

8.만들어진 이미지는 'cp arch/x86/boot/bzImage /boot/vmlinuz'명령어로 커널이미지를 대체하도록 하겠습니다. 작업이 끝났으면 'reboot'으로 리부팅합니다.

#### 과정5. 사용자 프로그램 작성 및 라이브러리 작성

[![](http://postfiles15.naver.net/20160320_222/zooqzqz_14584011531778jUm3_PNG/11.PNG?type=w773)](#)

9.이제 마지막 과정입니다. 재부팅하였다면 '/root'로 이동해 테스트파일을 작성해보도록하겠습니다. test.c파일을 만듭니다.

[![](http://postfiles16.naver.net/20160320_255/zooqzqz_14584011533398BzKW_PNG/12.PNG?type=w773)](#)

9-1.컴파일 후 'dmesg'로 커널의 버퍼를 확인해보니 잘 작동하는 것 같습니다.

[![](http://postfiles6.naver.net/20160320_261/zooqzqz_1458401153681yVSKQ_PNG/13.PNG?type=w773)](#)

10.라이브러리 작성을 위해 c 파일을 생성하여 함수를 작성합니다.

[![](http://postfiles4.naver.net/20160320_67/zooqzqz_1458401153839R8PIL_PNG/14.PNG?type=w773)](#)

11.'-c'옵션으로 object file을 생성합니다.

[![](http://postfiles10.naver.net/20160320_217/zooqzqz_1458401153959iGRci_PNG/14-1.PNG?type=w773)](#)

12.'ar -r'로 라이브러리 아카이브에 오브젝트를 추가합니다.


[![](http://postfiles9.naver.net/20160320_72/zooqzqz_1458404524920R11xj_PNG/15-1.PNG?type=w773)](#)

13.라이브러리 테스트 파일을 작성합니다. 이제 syscall()함수를 쓰지 않고 직접 함수를 입력합니다.


[![](http://postfiles16.naver.net/20160320_175/zooqzqz_1458401154098PGTR0_PNG/15.PNG?type=w773)](#)

14.dmesg를 통해 버퍼를 확인하니 역시 잘작동합니다.

### 2.마치며

system call을 추가하며 사용자가 커널의 자원을 사용할 때 어떤 메커니즘을 가지게 되는지 어렴풋이 알 수 있는 시간이 된 것 같습니다.

좋은 하루 되세요!
