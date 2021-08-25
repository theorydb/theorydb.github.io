---
layout: post
title: "[GitHub] 깃헙 블로그 시작하기!"
subtitle: "Starting GitHub Blog with Jekyll"
categories: reference
tags: github
comments: true
---

>`Jekyll`를 활용한 `GitHub`블로그 개설 이후,
>
>블로그 운영에 있어서 필요한 기본적인 정보 및 레퍼런스에 관한 글.





### 시작하기에 앞서...

 "개발자라 하면 기술 블로그 정도는 하나씩 가져줘야 하지 않을까?" 😜

라는 생각으로 `HTML` , `JAVA` , `JSON` 에 관한 지식이 1도 없지만, 그냥 덤벼들어 보았다.

거의 깃허브 블로그는 반포기 상태였는데, 우연히 다른 레퍼런스를 찾다가 [TheoryDB](https://theorydb.github.io/)

님의 블로그를 알게 되었고, 천천히 따라해보다보니 성공하게 되었다!(오류도 물론 있었지만 서칭으로 해결했다.)

노력하면 된다는 걸 새삼 또 깨달았고, 이 시행착오들을 발판삼아 앞으로 더 알찬 글을 작성해 나가고 싶다.

누군가 내 블로그를 본다면! 위에 언급한 `TheoryDB` 님의 포스팅으로 한번 시도해보길!!!😉

---



> #### Ruby로 Jekyll bundle 사용하기

    ###### 기초적인 작업은 다 끝난 과정에서, 블로그를 운영할 때 필요한 정보들만 추렸다.

 



​    `Typora` 로 글을 작성하고 나서, 제대로 블로그에 올라가는지 오류는 없는지! 깃허브에 푸쉬하기 전에 미리 지킬번들로 가상의 주소를 부여받아서 `미리보기` 할 수 있다.



   1. **Start Command Promt with Ruby** 를 실행해준다.

   2. 심각한 오류폭탄 방지를 위해 아래와 같은 코드로 새 페이지로 넘어간다.

      

      ```ruby	
      chcp 65001
      ```

3. 순서는 상관 없지만, 깃헙파일 위치로 이동시켜준다. (2번 전에 해도 된다)

   ```ruby
   C:\User\UserName> cd C:\User\UserName\GithubBlogAdress
   ```

4. `Jekyll` 서버를 실행한다.

   ```ruby
   C:\User\UserName> bundle exec jekyll serve
   ```

5. 그러면 가상 주소가 나온다. 가상 주소를 따서 들어가보면 블로그를 미리 볼 수 있다.

   _ _config.yml 파일을 수정할 시에는 실시간으로 업데이트가 안되기 때문에 <span style="color:red">반드시</span>_

   *`Ctrl`+`C` -> `Y` 로 서버를 멈추고 재시작 해야한다.*

   

> #### GitHub에 Commit해서 실제로 저장하기

  ###### 커밋하고 나서 실 업데이트는 약간 시간이 걸린다.   



    ```Linux
    $ git add --all
    ```

추가된 문서들을 업데이트 한다.  



```Linux
$ git commit -m "update"
```

`Repository`에 `commit`하는데, `" " ` 따옴표 사이에 넣는 문장이 커밋되면서 추가되는 메모이다.  



``` Linux
$ git push -u origin master
```

`master`브랜치에 푸쉬한다는 의미이다!



---

#

> #### 두고두고 참고할 레퍼런스 URL

   

   1. 📘 <span style="color:blue">Markdown</span> 기본 문법들

      [[JekyllBlog]마크다운 사용법 및 예제](https://theorydb.github.io/envops/2019/05/22/envops-blog-how-to-use-md/)

      [[Github 블로그]마크다운 문법 총 정리](https://ansohxxn.github.io/blog/markdown/#%EA%B0%95%EC%A1%B0)

      [velog 마크다운 작성법](https://velog.io/@yuuuye/velog-%EB%A7%88%ED%81%AC%EB%8B%A4%EC%9A%B4MarkDown-%EC%9E%91%EC%84%B1%EB%B2%95)  _유일하게 글자색 바꾸는 내용 포함됨!_

      

2. 📙 <span style="color:pink">Pavicon</span> 변경하기

   [Pavicon_Converter](https://icoconvert.com/)

   

3. 📗 <span style="color:Green">iEmoji</span> 삽입하기 

   [iEmoji keyboard](http://www.iemoji.com/#?category=smileys-people&version=36&theme=appl&skintone=default)

   

앞으로 공부해야할게 산더미지만 차근차근 해보는 걸로!

다음에는 꼭 이미지 넣는 걸 성공하고 싶다!  😁









