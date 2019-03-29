---
layout: post
title:  "MongoDB Backup restore 하기"
subtitle:   "DB만큼 소중한게 또 있을까."
categories: devlog
tags: mongodb backup restore devlog
---

DB만큼 소중한게 또 있을까.

DB이전이라던지 사고라던지에 대비해 백업은 숙명이다.

요즘엔 Meteor를 써서 작업하기 때문에 mongoDB를 사용하는데, 백업과 리스토어에 관해 알아보자.

### 몽고DB 백업

---

```
mongodump -h 127.0.0.1:3001 –db meteor  –out  backups
```

localhost의 meteor DB를 backups로 내보내는 라인이다.

backups/meteor라는 경로로 저장되어있다.

### 몽고DB 리스토어

---

```
mongorestore -h 127.0.0.1:3001 --db meteor backups/meteor/
```

이 라인으로 깔끔하게 복원된다.

### 끝으로

---

DB관리를 소중히하자.
