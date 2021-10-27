---  
layout: post  
title: "SQL Basic-Update"  
subtitle: "MSSQL_UPDATE CLAUSE"  
categories: sql
tags: 
comments: true  
header-img: img/post_img/SQL.png
---  
## UPDATE
- 참고할 MSDN 문서는 아래와 같다.
	- [UPDATE-MSDN](https://docs.microsoft.com/ko-kr/sql/t-sql/queries/update-transact-sql?view=sql-server-ver15)
- 아래 예제를 보면서 사용법을 알아보자.(예제 역시 MSDN에서 발췌했다.)
- 기본 구문
	```SQL
	UPDATE Person.Address SET ModifiedDate = GETDATE();
	```

	- ```UPDATE [테이블이름] SET [UPDATE작업구문]``` 의 구성이다.
	- Person.Address테이블의 ModifieDate 컬럼에 오늘 날짜를 입력하는 구문이다.

- 여러 열 업데이트 하기
	```SQL
	UPDATE Sales.SalesPerson SET
	Bonus = 6000, CommisionPct = 10, SaleQuota = NULL;
	```
	- 위의 예시처럼 SET 구정에 쉼표와 함께 컬럼을 지정하면 지정된 컬럼만 UPDATE 작업이 가능하다. 
	- 여기에 WHERE절을 이용하면 조건까지 부여된 UPDATE를 진행할 수 있다.
	- 아래 예시를 보자

	```SQL
	UPDATE Production.Product
	SET Color = N'Metallic Red'
	WHERE Name LIKE N'Road-250%' AND Color = N'Red';
	```	

	- Production.Product 테이블의 Color 컬럼의 내용을 N'Metallic Red' 로 변경한다.
	- 단, Name이 Road-250으로 시작하고
	- Color이 N'Red' 로 되어있는 행만 UPDATE한다.
	- N'Red' 에서 앞의 N은 유니코드를 의미한다.
- TOP 사용하여 UPDATE
	- TOP(n)을 사용해 n행만큼의 내용만 UPDATE하는것도 가능하다.
	- 아래 예시를 보자

	```SQL
	UPDATE TOP(10) HumanResources.Employee
	SET VacationHours = VacationHours*1.25;
	```
	- HumanResources.Employee테이블의 상위 10개 행에서 VacationHours 컬럼의 값을 25%증가시켜 UPDATE를 진행한다.