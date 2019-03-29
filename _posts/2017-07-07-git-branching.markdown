---
layout: post
title:  "[git]git flow - git branching 전략"
subtitle:   "git branching 전략"
categories: devlog
tags: git devlog

---

Git을 이용한 협업은 이제 필수가 되었다. 많의 회사에서 협업능력을 강조하고, 협업을 위한 git의 사용여부를 묻기도한다.

git은 팀 내에서 공유되는 코드들의 체계적인 관리에 도움이 된다.

혼자서 모든 작업을 한다면 git의 branch를 따는 작업은 필요없을지도 모른다. 하지만 팀의 구성원들이 늘어나고 개발하는 피쳐가 늘어나면 그 복잡성과 충돌을 해결하기 위해 branching전략이 필요하게 된다.

다양한 branching 전략이 있지만, 오늘 소개할 전략은 git flow 방식의 전략이다.

## 전략

---

### 소스 중앙 저장소

- master : 최종 릴리즈한 안정된 버전

- develop : 개발중인 최신 빌드 버전

중앙 저장소에는 2개의 branch를 만든다. master와 develop이 바로 그것이다. master브랜치는 현재 배포되고 있는 버전을 담고있는 브랜치이다. develop 브랜치는 개발이 완료된 테스트 브랜치라고 생각하면 된다.

### 개발자의 PC

- feature : 특정 기능을 작성할 때의 브랜치

- release : develop 브랜치의 수정을 위한 브랜치

- hotfix : master 브랜치의 버그 수정을 위한 브랜치

feature 브랜치는 기능을 작성할 때 develop브랜치에서 가져와 만든다. develop브랜치에 머지하면 feature브랜치는 삭제한다.

release 브랜치는 develop 브랜치에서 가져온다. release-x.y.z의 형식으로 이름짓는다. 이 이름으로 master브랜치에 태깅한다. develop과 master브랜치에 머지된다. master브랜치에 머지되면 삭제한다.

hotfix 브랜치는 master브랜치에서 가져온다. 작업이 완료되면 master에 머지하고 삭제한다.

## 마치며

---

git flow를 기반으로 자신의 팀만의 branching전략을 세운다면 더 좋은 협업을 위한 시스템을 만들 수 있을 것이다.
