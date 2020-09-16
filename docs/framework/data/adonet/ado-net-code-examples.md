---
title: 코드 예제
description: 이 예제에서는 ADO.NET 데이터 공급자 및 ADO.NET Entity Framework를 사용 하 여 데이터베이스에서 데이터를 검색 하는 방법을 .NET Framework 프로그래머에 게 보여 줍니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c119657a-9ce6-4940-91e4-ac1d5f0d9584
ms.openlocfilehash: 9d12c7c7dcbc3a24cf51ade5481f59715c4c4d88
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555109"
---
# <a name="adonet-code-examples"></a><span data-ttu-id="975b6-103">ADO.NET 코드 예제</span><span class="sxs-lookup"><span data-stu-id="975b6-103">ADO.NET code examples</span></span>

<span data-ttu-id="975b6-104">이 페이지의 코드 목록에서는 다음 ADO.NET 기술을 사용 하 여 데이터베이스에서 데이터를 검색 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="975b6-104">The code listings on this page demonstrate how to retrieve data from a database by using the following ADO.NET technologies:</span></span>

- <span data-ttu-id="975b6-105">ADO.NET 데이터 공급자</span><span class="sxs-lookup"><span data-stu-id="975b6-105">ADO.NET data providers:</span></span>

  - <span data-ttu-id="975b6-106">[SqlClient](#sqlclient) ( `System.Data.SqlClient` )</span><span class="sxs-lookup"><span data-stu-id="975b6-106">[SqlClient](#sqlclient) (`System.Data.SqlClient`)</span></span>

  - <span data-ttu-id="975b6-107">[OleDb](#oledb) ( `System.Data.OleDb` )</span><span class="sxs-lookup"><span data-stu-id="975b6-107">[OleDb](#oledb) (`System.Data.OleDb`)</span></span>

  - <span data-ttu-id="975b6-108">[Odbc](#odbc) ( `System.Data.Odbc` )</span><span class="sxs-lookup"><span data-stu-id="975b6-108">[Odbc](#odbc) (`System.Data.Odbc`)</span></span>

  - <span data-ttu-id="975b6-109">[OracleClient](#oracleclient) ( `System.Data.OracleClient` )</span><span class="sxs-lookup"><span data-stu-id="975b6-109">[OracleClient](#oracleclient) (`System.Data.OracleClient`)</span></span>

- <span data-ttu-id="975b6-110">ADO.NET Entity Framework:</span><span class="sxs-lookup"><span data-stu-id="975b6-110">ADO.NET Entity Framework:</span></span>

  - [<span data-ttu-id="975b6-111">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="975b6-111">LINQ to Entities</span></span>](#linq-to-entities)

  - [<span data-ttu-id="975b6-112">형식화된 ObjectQuery</span><span class="sxs-lookup"><span data-stu-id="975b6-112">Typed ObjectQuery</span></span>](#typed-objectquery)

  - <span data-ttu-id="975b6-113">[EntityClient](#entityclient) ( `System.Data.EntityClient` )</span><span class="sxs-lookup"><span data-stu-id="975b6-113">[EntityClient](#entityclient) (`System.Data.EntityClient`)</span></span>

- [<span data-ttu-id="975b6-114">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="975b6-114">LINQ to SQL</span></span>](#linq-to-sql)

## <a name="adonet-data-provider-examples"></a><span data-ttu-id="975b6-115">ADO.NET 데이터 공급자 예제</span><span class="sxs-lookup"><span data-stu-id="975b6-115">ADO.NET data provider examples</span></span>
<span data-ttu-id="975b6-116">다음에 나열된 코드에서는 ADO.NET 데이터 공급자를 사용하여 데이터베이스에서 데이터를 검색하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="975b6-116">The following code listings demonstrate how to retrieve data from a database using ADO.NET data providers.</span></span> <span data-ttu-id="975b6-117">데이터는 `DataReader`에서 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="975b6-117">The data is returned in a `DataReader`.</span></span> <span data-ttu-id="975b6-118">자세한 내용은 [DataReader를 사용 하 여 데이터 검색](retrieving-data-using-a-datareader.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="975b6-118">For more information, see [Retrieving Data Using a DataReader](retrieving-data-using-a-datareader.md).</span></span>

### <a name="sqlclient"></a><span data-ttu-id="975b6-119">SqlClient</span><span class="sxs-lookup"><span data-stu-id="975b6-119">SqlClient</span></span>
<span data-ttu-id="975b6-120">이 예제의 코드는 `Northwind` Microsoft SQL Server에서 예제 데이터베이스에 연결할 수 있다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="975b6-120">The code in this example assumes that you can connect to the `Northwind` sample database on Microsoft SQL Server.</span></span> <span data-ttu-id="975b6-121">이 코드에서는 Products 테이블에서 행을 선택하는 <xref:System.Data.SqlClient.SqlCommand>를 만들고 <xref:System.Data.SqlClient.SqlParameter>를 추가하여 UnitPrice가 지정한 매개 변수 값(이 경우 5)보다 큰 행만 반환되도록 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="975b6-121">The code creates a <xref:System.Data.SqlClient.SqlCommand> to select rows from the Products table, adding a <xref:System.Data.SqlClient.SqlParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="975b6-122">는 <xref:System.Data.SqlClient.SqlConnection> 블록 내에서 열리므로 `using` 코드가 종료 될 때 리소스가 닫히고 삭제 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="975b6-122">The <xref:System.Data.SqlClient.SqlConnection> is opened inside a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="975b6-123">이 코드에서는 <xref:System.Data.SqlClient.SqlDataReader>를 사용하여 명령을 실행하고 결과를 콘솔 창에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="975b6-123">The code executes the command by using a <xref:System.Data.SqlClient.SqlDataReader>, and displays the results in the console window.</span></span>

 [!code-csharp[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/VB/source.vb#1)]

### <a name="oledb"></a><span data-ttu-id="975b6-124">OleDb</span><span class="sxs-lookup"><span data-stu-id="975b6-124">OleDb</span></span>
<span data-ttu-id="975b6-125">이 예제 코드에서는 Microsoft Access Northwind 샘플 데이터베이스에 연결할 수 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="975b6-125">The code in this example assumes that you can connect to the Microsoft Access Northwind sample database.</span></span> <span data-ttu-id="975b6-126">이 코드에서는 Products 테이블에서 행을 선택하는 <xref:System.Data.OleDb.OleDbCommand>를 만들고 <xref:System.Data.OleDb.OleDbParameter>를 추가하여 UnitPrice가 지정한 매개 변수 값(이 경우 5)보다 큰 행만 반환되도록 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="975b6-126">The code creates a <xref:System.Data.OleDb.OleDbCommand> to select rows from the Products table, adding a <xref:System.Data.OleDb.OleDbParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="975b6-127">코드가 종료될 때 리소스가 닫히고 삭제되도록 <xref:System.Data.OleDb.OleDbConnection>이 `using` 블록 안에서 열립니다.</span><span class="sxs-lookup"><span data-stu-id="975b6-127">The <xref:System.Data.OleDb.OleDbConnection> is opened inside of a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="975b6-128">이 코드에서는 <xref:System.Data.OleDb.OleDbDataReader>를 사용하여 명령을 실행하고 결과를 콘솔 창에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="975b6-128">The code executes the command by using a <xref:System.Data.OleDb.OleDbDataReader>, and displays the results in the console window.</span></span>

 [!code-csharp[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/VB/source.vb#1)]

### <a name="odbc"></a><span data-ttu-id="975b6-129">Odbc</span><span class="sxs-lookup"><span data-stu-id="975b6-129">Odbc</span></span>
<span data-ttu-id="975b6-130">이 예제 코드에서는 Microsoft Access Northwind 샘플 데이터베이스에 연결할 수 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="975b6-130">The code in this example assumes that you can connect to the Microsoft Access Northwind sample database.</span></span> <span data-ttu-id="975b6-131">이 코드에서는 Products 테이블에서 행을 선택하는 <xref:System.Data.Odbc.OdbcCommand>를 만들고 <xref:System.Data.Odbc.OdbcParameter>를 추가하여 UnitPrice가 지정한 매개 변수 값(이 경우 5)보다 큰 행만 반환되도록 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="975b6-131">The code creates a <xref:System.Data.Odbc.OdbcCommand> to select rows from the Products table, adding a <xref:System.Data.Odbc.OdbcParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="975b6-132">는 <xref:System.Data.Odbc.OdbcConnection> 블록 내에서 열리므로 `using` 코드가 종료 될 때 리소스가 닫히고 삭제 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="975b6-132">The <xref:System.Data.Odbc.OdbcConnection> is opened inside a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="975b6-133">이 코드에서는 <xref:System.Data.Odbc.OdbcDataReader>를 사용하여 명령을 실행하고 결과를 콘솔 창에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="975b6-133">The code executes the command by using a <xref:System.Data.Odbc.OdbcDataReader>, and displays the results in the console window.</span></span>

[!code-csharp[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/CS/source.cs#1)]
[!code-vb[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/VB/source.vb#1)]

### <a name="oracleclient"></a><span data-ttu-id="975b6-134">OracleClient</span><span class="sxs-lookup"><span data-stu-id="975b6-134">OracleClient</span></span>
<span data-ttu-id="975b6-135">이 예제 코드에서는 Oracle 서버에서 DEMO.CUSTOMER에 연결할 수 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="975b6-135">The code in this example assumes a connection to DEMO.CUSTOMER on an Oracle server.</span></span> <span data-ttu-id="975b6-136">또한 System.Data.OracleClient.dll에 대한 참조를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="975b6-136">You must also add a reference to the System.Data.OracleClient.dll.</span></span> <span data-ttu-id="975b6-137">이 코드는 <xref:System.Data.OracleClient.OracleDataReader>에 데이터를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="975b6-137">The code returns the data in an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>

 [!code-csharp[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/VB/source.vb#1)]

## <a name="entity-framework-examples"></a><span data-ttu-id="975b6-138">Entity Framework 예제</span><span class="sxs-lookup"><span data-stu-id="975b6-138">Entity Framework examples</span></span>
<span data-ttu-id="975b6-139">다음에 나열된 코드에서는 EDM(엔터티 데이터 모델)의 엔터티를 쿼리하여 데이터 소스에서 데이터를 검색하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="975b6-139">The following code listings demonstrate how to retrieve data from a data source by querying entities in an Entity Data Model (EDM).</span></span> <span data-ttu-id="975b6-140">이 예에서는 Northwind 샘플 데이터베이스를 기반으로 하는 모델을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="975b6-140">These examples use a model based on the Northwind sample database.</span></span> <span data-ttu-id="975b6-141">Entity Framework에 대 한 자세한 내용은 [Entity Framework 개요](./ef/overview.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="975b6-141">For more information about Entity Framework, see [Entity Framework Overview](./ef/overview.md).</span></span>

### <a name="linq-to-entities"></a><span data-ttu-id="975b6-142">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="975b6-142">LINQ to Entities</span></span>
<span data-ttu-id="975b6-143">이 예제 코드에서는 LINQ 쿼리를 사용하여 CategoryID와 CategoryName 속성만 포함된 익명 형식으로 프로젝션된 Categories 개체로 데이터를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="975b6-143">The code in this example uses a LINQ query to return data as Categories objects, which are projected as an anonymous type that contains only the CategoryID and CategoryName properties.</span></span> <span data-ttu-id="975b6-144">자세한 내용은 [LINQ to Entities 개요](./ef/language-reference/linq-to-entities.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="975b6-144">For more information, see [LINQ to Entities Overview](./ef/language-reference/linq-to-entities.md).</span></span>

```csharp
using System;
using System.Linq;
using System.Data.Objects;
using NorthwindModel;

class LinqSample
{
    public static void ExecuteQuery()
    {
        using (NorthwindEntities context = new NorthwindEntities())
        {
            try
            {
                var query = from category in context.Categories
                            select new
                            {
                                categoryID = category.CategoryID,
                                categoryName = category.CategoryName
                            };

                foreach (var categoryInfo in query)
                {
                    Console.WriteLine("\t{0}\t{1}",
                        categoryInfo.categoryID, categoryInfo.categoryName);
                }
            }
            catch (Exception ex)
            {
                Console.WriteLine(ex.Message);
            }
        }
    }
}
```

```vb
Option Explicit On
Option Strict On

Imports System.Linq
Imports System.Data.Objects
Imports NorthwindModel

Class LinqSample
    Public Shared Sub ExecuteQuery()
        Using context As NorthwindEntities = New NorthwindEntities()
            Try
                Dim query = From category In context.Categories _
                            Select New With _
                            { _
                                .categoryID = category.CategoryID, _
                                .categoryName = category.CategoryName _
                            }

                For Each categoryInfo In query
                    Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _
                        categoryInfo.categoryID, categoryInfo.categoryName)
                Next
            Catch ex As Exception
                Console.WriteLine(ex.Message)
            End Try
        End Using
    End Sub
End Class
```

### <a name="typed-objectquery"></a><span data-ttu-id="975b6-145">형식화된 ObjectQuery</span><span class="sxs-lookup"><span data-stu-id="975b6-145">Typed ObjectQuery</span></span>
<span data-ttu-id="975b6-146">이 예제 코드에서는 <xref:System.Data.Objects.ObjectQuery%601>을 사용하여 데이터를 Categories 개체로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="975b6-146">The code in this example uses an <xref:System.Data.Objects.ObjectQuery%601> to return data as Categories objects.</span></span> <span data-ttu-id="975b6-147">자세한 내용은 [개체 쿼리](/previous-versions/dotnet/netframework-4.0/bb896241(v=vs.100))합니다.</span><span class="sxs-lookup"><span data-stu-id="975b6-147">For more information, see [Object Queries](/previous-versions/dotnet/netframework-4.0/bb896241(v=vs.100)).</span></span>

```csharp
using System;
using System.Data.Objects;
using NorthwindModel;

class ObjectQuerySample
{
    public static void ExecuteQuery()
    {
        using (NorthwindEntities context = new NorthwindEntities())
        {
            ObjectQuery<Categories> categoryQuery = context.Categories;

            foreach (Categories category in
                categoryQuery.Execute(MergeOption.AppendOnly))
            {
                Console.WriteLine("\t{0}\t{1}",
                    category.CategoryID, category.CategoryName);
            }
        }
    }
}
```

```vb
Option Explicit On
Option Strict On

Imports System.Data.Objects
Imports NorthwindModel

Class ObjectQuerySample
    Public Shared Sub ExecuteQuery()
        Using context As NorthwindEntities = New NorthwindEntities()
            Dim categoryQuery As ObjectQuery(Of Categories) = context.Categories

            For Each category As Categories In _
                categoryQuery.Execute(MergeOption.AppendOnly)
                Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _
                    category.CategoryID, category.CategoryName)
            Next
        End Using
    End Sub
End Class
```

### <a name="entityclient"></a><span data-ttu-id="975b6-148">EntityClient</span><span class="sxs-lookup"><span data-stu-id="975b6-148">EntityClient</span></span>
<span data-ttu-id="975b6-149">이 예제 코드에서는 <xref:System.Data.EntityClient.EntityCommand>를 사용하여 Entity SQL 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="975b6-149">The code in this example uses an <xref:System.Data.EntityClient.EntityCommand> to execute an Entity SQL query.</span></span> <span data-ttu-id="975b6-150">이 쿼리는 Categories 엔터티 형식의 인스턴스를 나타내는 레코드 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="975b6-150">This query returns a list of records that represent instances of the Categories entity type.</span></span> <span data-ttu-id="975b6-151"><xref:System.Data.EntityClient.EntityDataReader>를 사용하여 결과 집합의 데이터 레코드에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="975b6-151">An <xref:System.Data.EntityClient.EntityDataReader> is used to access data records in the result set.</span></span> <span data-ttu-id="975b6-152">자세한 내용은 [Entity Framework용 EntityClient 공급자](./ef/entityclient-provider-for-the-entity-framework.md)(영문)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="975b6-152">For more information, see [EntityClient Provider for the Entity Framework](./ef/entityclient-provider-for-the-entity-framework.md).</span></span>

```csharp
using System;
using System.Data;
using System.Data.Common;
using System.Data.EntityClient;
using NorthwindModel;

class EntityClientSample
{
    public static void ExecuteQuery()
    {
        string queryString =
            @"SELECT c.CategoryID, c.CategoryName
                FROM NorthwindEntities.Categories AS c";

        using (EntityConnection conn =
            new EntityConnection("name=NorthwindEntities"))
        {
            try
            {
                conn.Open();
                using (EntityCommand query = new EntityCommand(queryString, conn))
                {
                    using (DbDataReader rdr =
                        query.ExecuteReader(CommandBehavior.SequentialAccess))
                    {
                        while (rdr.Read())
                        {
                            Console.WriteLine("\t{0}\t{1}", rdr[0], rdr[1]);
                        }
                    }
                }
            }
            catch (Exception ex)
            {
                Console.WriteLine(ex.Message);
            }
        }
    }
}
```

```vb
Option Explicit On
Option Strict On

Imports System.Data
Imports System.Data.Common
Imports System.Data.EntityClient
Imports NorthwindModel

Class EntityClientSample
    Public Shared Sub ExecuteQuery()
        Dim queryString As String = _
            "SELECT c.CategoryID, c.CategoryName " & _
                "FROM NorthwindEntities.Categories AS c"

        Using conn As EntityConnection = _
            New EntityConnection("name=NorthwindEntities")

            Try
                conn.Open()
                Using query As EntityCommand = _
                New EntityCommand(queryString, conn)
                    Using rdr As DbDataReader = _
                        query.ExecuteReader(CommandBehavior.SequentialAccess)
                        While rdr.Read()
                            Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _
                                              rdr(0), rdr(1))
                        End While
                    End Using
                End Using
            Catch ex As Exception
                Console.WriteLine(ex.Message)
            End Try
        End Using
    End Sub
End Class
```

## <a name="linq-to-sql"></a><span data-ttu-id="975b6-153">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="975b6-153">LINQ to SQL</span></span>
<span data-ttu-id="975b6-154">이 예제 코드에서는 LINQ 쿼리를 사용하여 CategoryID와 CategoryName 속성만 포함된 익명 형식으로 프로젝션된 Categories 개체로 데이터를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="975b6-154">The code in this example uses a LINQ query to return data as Categories objects, which are projected as an anonymous type that contains only the CategoryID and CategoryName properties.</span></span> <span data-ttu-id="975b6-155">이 예제는 Northwind 데이터 컨텍스트를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="975b6-155">This example is based on the Northwind data context.</span></span> <span data-ttu-id="975b6-156">자세한 내용은 [시작](./sql/linq/getting-started.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="975b6-156">For more information, see [Getting Started](./sql/linq/getting-started.md).</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Northwind;

    class LinqSqlSample
    {
        public static void ExecuteQuery()
        {
            using (NorthwindDataContext db = new NorthwindDataContext())
            {
                try
                {
                    var query = from category in db.Categories
                                select new
                                {
                                    categoryID = category.CategoryID,
                                    categoryName = category.CategoryName
                                };

                    foreach (var categoryInfo in query)
                    {
                        Console.WriteLine("vbTab {0} vbTab {1}",
                            categoryInfo.categoryID, categoryInfo.categoryName);
                    }
                }
                catch (Exception ex)
                {
                    Console.WriteLine(ex.Message);
                }
            }
        }
    }
```

```vb
Option Explicit On
Option Strict On

Imports System.Collections.Generic
Imports System.Linq
Imports System.Text
Imports Northwind

Class LinqSqlSample
    Public Shared Sub ExecuteQuery()
        Using db As NorthwindDataContext = New NorthwindDataContext()
            Try
                Dim query = From category In db.Categories _
                                Select New With _
                                { _
                                    .categoryID = category.CategoryID, _
                                    .categoryName = category.CategoryName _
                                }

                For Each categoryInfo In query
                    Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _
                            categoryInfo.categoryID, categoryInfo.categoryName)
                Next
            Catch ex As Exception
                Console.WriteLine(ex.Message)
            End Try
            End Using
    End Sub
End Class
```

## <a name="see-also"></a><span data-ttu-id="975b6-157">참조</span><span class="sxs-lookup"><span data-stu-id="975b6-157">See also</span></span>

- [<span data-ttu-id="975b6-158">ADO.NET 개요</span><span class="sxs-lookup"><span data-stu-id="975b6-158">ADO.NET Overview</span></span>](ado-net-overview.md)
- [<span data-ttu-id="975b6-159">ADO.NET에서 데이터 검색 및 수정</span><span class="sxs-lookup"><span data-stu-id="975b6-159">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- <span data-ttu-id="975b6-160">[데이터 애플리케이션 만들기](/previous-versions/visualstudio/visual-studio-2013/h0y4a0f6(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="975b6-160">[Creating Data Applications](/previous-versions/visualstudio/visual-studio-2013/h0y4a0f6(v=vs.120))</span></span>
- <span data-ttu-id="975b6-161">[엔터티 데이터 모델 쿼리(Entity Framework 작업)](/previous-versions/bb738455(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="975b6-161">[Querying an Entity Data Model (Entity Framework Tasks)](/previous-versions/bb738455(v=vs.90))</span></span>
- <span data-ttu-id="975b6-162">[방법: 익명 형식 개체를 반환하는 쿼리 실행](/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="975b6-162">[How to: Execute a Query that Returns Anonymous Type Objects](/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))</span></span>
