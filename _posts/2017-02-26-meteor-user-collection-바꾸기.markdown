---
layout: post
title:  "Meteor default users 콜렉션 바꾸기"
subtitle:   "Meteor는 기본적으로 유저컬렉션을 users로 fix해 놨다."
categories: devlog
tags: meteor devlog

---

Meteor는 기본적으로 유저컬렉션을 users로 fix해 놨다.

개인 프로젝트를 할때는 상관없을지 모르지만 다른사람들과 협업을 위한다면, 컬렉션의 이름을 커스텀해야 할 필요가있다.

이럴때 컬렉션의 이름을 바꾸는 방법을 찾아보았다.

미티어는 /lib폴더가 먼저 실행되기 때문에 /lib폴더에 아래와 같은 코드를 넣는다.

```javascript

import { Meteor } from 'meteor/meteor'
import { Accounts } from 'meteor/accounts-base'

Accounts.users = new Mongo.Collection("custom_users");

Meteor.users = Accounts.users;

```

강제로 Accounts와 Meteor의 user를 배당해주는 방법을 택했다.
