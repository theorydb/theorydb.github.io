---  
layout: post  
title: "C#-SqlConnection Class"  
subtitle: "SqlConnection사용해보기"  
categories: C#
tags: 
comments: true  
header-img: 
---  
## SqlConnection class
#### MSDN - [SqlConnection](https://docs.microsoft.com/ko-kr/dotnet/api/system.data.sqlclient.sqlconnection?view=dotnet-plat-ext-5.0)
C#에서 MSSQL의 데이터를 연동하여 사용할때 필요한 SqlConnection Class에 대해 알아보자.
- SqlConnection class는 .NET Framework 에서 SQL Sever 데이터베이스에 대한 연결을 위한 기능을 제공한다.
- 상속관계는 아래와 같다.
   > Object -> MarshalByRefObject -> Component -> DbConnection -> SqlConnection
   > 
   > 구현은 Icloneable
- DB에 관련된 클래스 답게 DbConnection클래스를 상속받는다.
- 정의를 보면 아래와 같다.
```csharp
public sealed class SqlConnection : System.Data.Common.DbConnection, ICloneable
```
- 정의를 보면 알겠지만, 사용하기 위해선 ```using.System.Data;```를 추가해줘야 한다.
- using.System.Data;와 더불어 SQL DB와의 연결을 위해 ConnectionString을 사용해야 한다.
- ConnectionString에 대해선 아래를 참고하자.
  - MSDN - [ConnectionString](https://docs.microsoft.com/ko-kr/dotnet/api/system.data.sqlclient.sqlconnection.connectionstring?view=dotnet-plat-ext-5.0)
- 아래 예제를 보면서 ConnectionString과 SqlConnection이 어떻게 쓰이는지 조금은 알수 있을 것이다.

<br/>

```csharp
//using.System.Data; 전처리기는 미리 선언해준다.
private static void OpenSqlConnection()
{
    string connectionString = GetConnectionString(); //ConncetionString을 담기 위한 인스턴스 생성

    using (SqlConnection connection = new SqlConnection())
    {
        connection.ConnectionString = connectionString;

        connection.Open();

        Console.WriteLine("State: {0}", connection.State);
        Console.WriteLine("ConnectionString: {0}",
            connection.ConnectionString);
    }
}

static private string GetConnectionString()
{
    // To avoid storing the connection string in your code,
    // you can retrieve it from a configuration file.
    // 아래 ConnectionString은 App.config파일을 이용해서 setting가능하다.
    return "Data Source=MSSQL1;Initial Catalog=AdventureWorks;"
        + "Integrated Security=true;";
}
``` 

- GetConnectionString() method의 주석에서 보이는 configuration file은 App.config파일의 ```<connectionString>``` 태그를 이용하여 구현할 수 있다.
- App.config파일을 다루는 내용은 차후 따로 다뤄보기로 한다.