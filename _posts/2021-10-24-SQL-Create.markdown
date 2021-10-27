---  
layout: post  
title: "SQL Basic-Create"  
subtitle: "MSSQL_CREATE TABLE CLAUSE"  
categories: sql
tags: 
comments: true  
header-img: img/post_img/SQL.png
---  
### CREATE TABLE
- 아래 링크의 예제 중 하나를 통해 공부해 보자
  - [MSDN-CREATE TABLE예제](https://docs.microsoft.com/ko-kr/sql/t-sql/statements/create-table-transact-sql?view=sql-server-ver15)
- 간단한 구문 형식
	```SQL
	-- Simple CREATE TABLE Syntax (common if not using options)
	CREATE TABLE
		{ database_name.schema_name.table_name | schema_name.table_name | table_name }
		( { <column_definition> } [ ,...n ] )
	[ ; ]
	```

- 첫번째 예제를 보자
	```SQL
	CREATE TABLE TABLECREATE_1(
		COL1 INT PRIMARY KEY,
		COL2 VARCHAR(20),
		COL3 DATE NOT NULL
	);
	```


    - 이해를 돕기 위해 풀어쓰면 아래와 같다.


	```SQL
	CREATE TABLE [테이블 이름] (
		[컬럼명] [데이터 형식] [추가옵션],
		[컬럼명] [데이터 형식] [추가옵션],
		... 
	);
	```
  - 추가 옵션은 `NOT NULL`, `PRIMARY KEY`, `FOREIGN KEY`, `DEFAULT [기본값]` 등이 있다.
  - 생성된 테이블이 탐색기에서 보이지 않을 때는 해당 DB 하위폴더가 보이지 않는 상태에서 새로 고침하게 되면 반영된 테이블을 볼 수 있다.
  - 탐색기->테이블 우클릭->디자인 을 통해 데이터 형식과 기본값을 수정할 수 있지만, ALTER문 같은 쿼리를 사용하는데 더 익숙해져야 할 듯 하다. 

- 두번째 예제는 임시 테이블을 생성하기 위한 구문이다.
	```SQL
	--CREATE TEMP TABLE
	CREATE TABLE #TEMP_TABLECREATE_1(
		TEMP_COL1 INT PRIMARY KEY,
		TEMP_COL2 VARCHAR(20),
		TEMP_COL3 DATE NOT NULL
	);
	```
	- 임시 테이블은 말 그대로 SQL문이 실행되는 동안에만 임시로 생성되는 테이블이다.
	- 프로시저를 생성해 사용해야 할 때 유용하게 사용할 수 있을 듯 하다.