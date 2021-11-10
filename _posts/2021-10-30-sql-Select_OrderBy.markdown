---  
layout: post  
title: "SQL Basic-Select_OrderBy_"  
subtitle: "MSSQL_SELECT_ORDERBY_CLAUSE"  
categories: sql
tags: 
comments: true  
header-img: img/post_img/SQL.png
---  
## SELECT-ORDER BY CLAUSE
- SELECT 문에서 결과를 정렬하기 위해 사용되는 절이다.
	- 오름차순(ASC) 내림차순(DESC)의 옵션이 있다.  기본 정렬은 오름차순 정렬이다.
	- 정렬 시 Null값은 가장 작은 값으로 취급한다. 
- 기본 구성
```sql
SELECT SCHEMA_NAME(schema_id) AS Sch FROM sys.objects
ORDER BY SchemaName;
```
- 구문 작성시 주의할 점은 아래와 같다.
	- 열 이름은 FROM절에서 지정한 테이블에 정의된 열과 같아야 한다.
	- ORDER BY절에서 사용되는 열 이름은 그 일부분이 식으로 사용되어져서는 안된다.
		- 잘못 사용한 예
		```sql
		SELECT SCHEMA_NAME(schema_id) AS Sch FROM sys.objects
		ORDER BY SchemaName + ''; -- 이 부분이 잘못된 예시
		```
- WHERE 로 조건에 맞는 열을 추스린 후, ORDER BY 이후에 CASE WHEN 절을 추가하여 지정된 열 값에 따라 행의 정렬 순서를 조건부로 지정할 수 있다.
	- 예시
	```sql
	SELECT BusinessEntityID, SalariedFlag
	FROM HumanResources.Employee
	ORDER BY CASE SalariedFlag WHEN 1 THEN BusinessEntityID END DESC,
	CASE WHEN SalariedFlag = 0 THEN BusinessEntityID END;
	```
	- HumanResources.Employee 테이블의 SalariedFlag열의 값이 1일때 내림차순, 0일때 오름차순으로 정렬한다.

위의 구문에서
```sql
CASE WHEN SalariedFlag = 0 THEN BusinessEntityID END
```
을 
```sql
CASE SalariedFlag WHEN 0 THEN BusinessEntityID END
``` 

으로 사용해도 된다.