---  
layout: post  
title: "Git bash command"  
subtitle: "Git bash command"  
categories: git
tags: 
comments: true  
header-img: img/post_img/git.png
---  

# Git을 사용해보자
git은 널리 알려진 VCS(Version Control System)중의 하나다.
- 사실 git을 사용한다기 보다 github를 사용한다는 표현이 옳다.
- git은 엄청나게 다양한 기능이 있다고 들었고, 사용하는 방법은 아직 다 알지 못한다.
- 내가 사용하는 방법은 아래 두가지
  - git bash, git CMD 같은 프롬프트 창을 이용하는 방법
  - IDE(Visual studio)와 연동하여 사용하는 방법

---
## 설치는?
git설치는 [git download](https://git-scm.com/downloads)페이지에서 운영체제에 맞는 파일을 다운받아 설치하면 된다.
세부적인 부분들은 따로 정리하는것으로 하자. (간단해 보일수도 있지만 해야 할 일들이 생각보다 양이 많다.)
## Gitbash
- 앞서 말한대로 프롬프트창을 사용하는 형식이다.
- 지금 필요한건 Gitbash를 사용하는데 필요한 명령어다.
- 명령어를 찾아보자.
- #### 아래 명령어들을 사용하기 전 github에 계정부터 만드는 것, 잊지말자.
    - 계정생성은 어렵지 않으니 금방 만들수 있다.
---
### Gitbash 명령어
- git 홈페이지에서 제공하는 Reference를 살펴봤더니
![Gitrefrence](https://D-Gun.github.io/assets/img/post_img/gitrefrence.png)
- 역시나 많다... 그러니 필요한 부분 몇개만 챙겨서 살펴보도록 하자. 허나,
  - 문서화된 부분을 읽어서는 기능을 이해하기 어려웠다. git의 구조를 어느정도 알고 있어야 이해가 가능할 것으로 보인다.
  - 구글링으로 간단하게 정리되어 있는 명령어들만 가져와서 메모해본다.
- 명령어
  - 명령어 작성 중 tab 두번 : 명령어 자동완성
  - Gitbash는 리눅스 프롬프트의 명령어를 사용하는 것으로 보인다.
  - `ls` : 해당 디렉토리 안의 파일과 디렉토리를 보여준다.
  - `cd` : 폴더 내부로 접근시 사용한다. 상위 폴더로 빠져나오고 싶으면 `..`을 사용하자.
  - 나머지 명령어들은 `git`으로 시작하는 명령어들이다.
  - 사용할 폴더를 생성 후 git initialize를 위해 처음 사용되는 명령어
    - `git init` : git과의 연결을 위한 명령어다. `.git`이라는 숨김폴더를 생성한다.
    - `git config --global user.name <github username>` : github에 생성된 계정의 username을 등록한다.
    - `git config --global user.email <github useremail>` : github에 생성된 계정의 email을 등록한다.
    - `git config --list` : git config의 list를 출력한다.
  - github repository 관련 명령어(clone, commit, pull, push)
    - `git clone <github 저장소 주소>` : github repository를 복사한다.
    - `git add --all` : 수정된 파일을 포함한 모든 파일 local 저장소에 업로드
    - `git add <파일/디렉토리 경로>` : 해당파일 스테이징
	- `git add .` : 현재 디렉토리의 모든 변경 내용을 스테이징
	- `git add -A` : 모든 변경 내용을 스테이징
	- `git add -p` : 변경사항을 터미널에서 확인 후 스테이징
    - `git commit -m "commit message"` : github로 commit. commit message는 꼭 작성도록 하자.
	- `git reset HEAD <파일명>` : 해당파일 스테이징 취소. 파일명이 없으면 add한 파일 전체 취소
	- `git reset --soft HEAD^` : 해당파일 커밋 취소, 파일들은 staged상태로 워킹 디렉토리에 보존
	- `git reset --mixed HEAD^` : 해당파일 커밋 취소, 파일들은 unstaged상태로 워킹 디렉토리에 보존
	- `git reset HEAD~2` : 마지막 2개 커밋 취소
	- `git reset --hard HEAD^` : 커밋 취소, 파일들은 unstaged상태로 워킹 디렉토리에서 삭제
    - `git log` : commit 내용 확인
    - ##### git의 branch를 local에서 생성 후 remote repository에 push하기 위해선 remote repository를 등록해주어야 한다.
    - `git remote` : remote repository 확인하기
    - `git remote -v` : remote repository의 단축이름과 URL보기
    - `git remote show <github remote repo name>` : remote repository의 상세정보 보기
    - `git remote rename <oldName> <newName>` : remote repository 의 이름 바꾸기
    - `git remote add <github remote repo name> <url>` : 워킹 디렉토리에 새 <github remote repo name>의 remote repository 추가
    - `git remote rm <github remote repo name>` : git remote repository 삭제
    - `git push <github remote repo name> --delete <github branch name>` : github remote branch 삭제
    - `git fetch <github remot repo name>` : <github remote repo name>의 remote repo fetch,로컬에는 없지만, remote repo에 있는 데이터를 모두 가져온다.
      - remote repo의 데이터를 모두 local로 가지오기는 하나, 자동으로 Merge하지 않는다. 따라서 수동으로 Merge해주어야 한다.
      - 그럴바엔 차라리 pull을 사용하는게 더 편할수도 있다.
    - `git branch` : branch목록 확인
    - `git branch -v` : banch 목록 및 마지막 커밋 메시지까지 확인
    - `git branch -merge` : branch merge여부 확인
    - `git branch -m <oldName> <newName>` : branch 이름 변경
    - `git branch -d <branchName>` : <branchName> branch 삭제
    - `git checkout <branchName>` : <branchName> branch로 switch.
    - `git checkout -b <branchName>` : branch확인 후 없으면 생성 
    - `git push -u origin master` : github master branch에 push
    - ##### 잊지말자, add-> commit-> pull-> push-> pull request
    - `git status` : 현재 폴더의 git 정보 확인
    - `git branch <github branch name>` : 등록된 저장소에 <github branch name>의 branch 생성
    - `git checkout <github branch name>` : <github branch name>의 branch로 이동
    - `git checkout -b <github branch name>` : <github branch name>의 branch를 생성하고 branch로 이동
    - `git --version` : git 버전 확인
- 추가로 새롭게 알게된 명령어는 찾는데로 업데이트 하도록 하겠다.