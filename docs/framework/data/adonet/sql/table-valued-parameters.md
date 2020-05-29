---
title: 테이블 반환 매개 변수
ms.date: 10/12/2018
dev_langs:
- csharp
- vb
ms.assetid: 370c16d5-db7b-43e3-945b-ccaab35b739b
ms.openlocfilehash: b968c599cf061fbd03b7ba8fb19470f6ace11a55
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202168"
---
# <a name="table-valued-parameters"></a><span data-ttu-id="52ec5-102">테이블 반환 매개 변수</span><span class="sxs-lookup"><span data-stu-id="52ec5-102">Table-Valued Parameters</span></span>
<span data-ttu-id="52ec5-103">테이블 반환 매개 변수를 사용하면 데이터를 처리하는 데 여러 번 왕복하거나 서버 측 특수 논리를 설정하지 않고도 데이터의 여러 행을 클라이언트 애플리케이션에서 SQL Server로 쉽게 마샬링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-103">Table-valued parameters provide an easy way to marshal multiple rows of data from a client application to SQL Server without requiring multiple round trips or special server-side logic for processing the data.</span></span> <span data-ttu-id="52ec5-104">또한 테이블 반환 매개 변수를 사용하면 클라이언트 애플리케이션에서 데이터 행을 캡슐화하고 매개 변수가 있는 단일 명령으로 데이터를 서버에 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-104">You can use table-valued parameters to encapsulate rows of data in a client application and send the data to the server in a single parameterized command.</span></span> <span data-ttu-id="52ec5-105">들어오는 데이터 행을 테이블 변수에 저장한 다음 Transact-SQL을 사용하여 연산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-105">The incoming data rows are stored in a table variable that can then be operated on by using Transact-SQL.</span></span>  
  
 <span data-ttu-id="52ec5-106">테이블 반환 매개 변수의 열 값은 표준 Transact-SQL SELECT 문을 사용하여 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-106">Column values in table-valued parameters can be accessed using standard Transact-SQL SELECT statements.</span></span> <span data-ttu-id="52ec5-107">테이블 반환 매개 변수는 강력한 형식이며 해당 구조체의 유효성 검사가 자동으로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-107">Table-valued parameters are strongly typed and their structure is automatically validated.</span></span> <span data-ttu-id="52ec5-108">테이블 반환 매개 변수의 크기는 서버 메모리에 의해서만 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-108">The size of table-valued parameters is limited only by server memory.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="52ec5-109">테이블 반환 매개 변수에는 데이터를 반환할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-109">You cannot return data in a table-valued parameter.</span></span> <span data-ttu-id="52ec5-110">테이블 반환 매개 변수는 입력 전용입니다. OUTPUT 키워드는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-110">Table-valued parameters are input-only; the OUTPUT keyword is not supported.</span></span>  
  
 <span data-ttu-id="52ec5-111">테이블 반환 매개 변수에 대한 자세한 내용은 다음 리소스를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="52ec5-111">For more information about table-valued parameters, see the following resources.</span></span>  
  
|<span data-ttu-id="52ec5-112">리소스</span><span class="sxs-lookup"><span data-stu-id="52ec5-112">Resource</span></span>|<span data-ttu-id="52ec5-113">설명</span><span class="sxs-lookup"><span data-stu-id="52ec5-113">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="52ec5-114">테이블 반환 매개 변수 사용(데이터베이스 엔진)</span><span class="sxs-lookup"><span data-stu-id="52ec5-114">Use Table-Valued Parameters (Database Engine)</span></span>](/sql/relational-databases/tables/use-table-valued-parameters-database-engine)|<span data-ttu-id="52ec5-115">테이블 반환 매개 변수를 만들고 사용하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-115">Describes how to create and use table-valued parameters.</span></span>|  
|<span data-ttu-id="52ec5-116">[사용자 정의 테이블 형식](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="52ec5-116">[User-Defined Table Types](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100))</span></span>|<span data-ttu-id="52ec5-117">테이블 반환 매개 변수를 선언하는 데 사용되는 사용자 정의 테이블 형식에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-117">Describes user-defined table types that are used to declare table-valued parameters.</span></span>|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a><span data-ttu-id="52ec5-118">이전 버전의 SQL Server에서 여러 행 전달</span><span class="sxs-lookup"><span data-stu-id="52ec5-118">Passing Multiple Rows in Previous Versions of SQL Server</span></span>  
 <span data-ttu-id="52ec5-119">SQL Server 2008에 테이블 반환 매개 변수가 도입되기 전에는 여러 행의 데이터를 저장 프로시저나 매개 변수화된 SQL 명령에 전달하는 옵션이 제한적이었습니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-119">Before table-valued parameters were introduced to SQL Server 2008, the options for passing multiple rows of data to a stored procedure or a parameterized SQL command were limited.</span></span> <span data-ttu-id="52ec5-120">개발자는 서버에 여러 행을 전달하기 위해 다음 옵션 중에서 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-120">A developer could choose from the following options for passing multiple rows to the server:</span></span>  
  
- <span data-ttu-id="52ec5-121">일련의 개별 매개 변수를 사용하여 여러 열과 데이터 행의 값을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-121">Use a series of individual parameters to represent the values in multiple columns and rows of data.</span></span> <span data-ttu-id="52ec5-122">이 방법을 사용하여 전달할 수 있는 데이터의 양은 허용되는 매개 변수의 개수에 의해 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-122">The amount of data that can be passed by using this method is limited by the number of parameters allowed.</span></span> <span data-ttu-id="52ec5-123">SQL Server 프로시저에는 매개 변수를 2100개까지 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-123">SQL Server procedures can have, at most, 2100 parameters.</span></span> <span data-ttu-id="52ec5-124">이러한 개별 값을 테이블 변수 또는 처리를 위한 임시 테이블로 조합하는 데 서버 쪽 논리가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-124">Server-side logic is required to assemble these individual values into a table variable or a temporary table for processing.</span></span>  
  
- <span data-ttu-id="52ec5-125">여러 데이터 값을 구분된 문자열 또는 XML 문서로 번들로 묶은 다음 해당 텍스트 값을 프로시저 또는 문에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-125">Bundle multiple data values into delimited strings or XML documents and then pass those text values to a procedure or statement.</span></span> <span data-ttu-id="52ec5-126">이렇게 하려면 프로시저 또는 문이 데이터 구조의 유효성을 검사하고 값을 번들에서 해제하는 데 필요한 논리를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-126">This requires the procedure or statement to include the logic necessary for validating the data structures and unbundling the values.</span></span>  
  
- <span data-ttu-id="52ec5-127"><xref:System.Data.SqlClient.SqlDataAdapter>의 `Update` 메서드를 호출하여 만든 것과 같이 여러 행에 영향을 주는 데이터 수정을 위한 일련의 개별 SQL 문을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-127">Create a series of individual SQL statements for data modifications that affect multiple rows, such as those created by calling the `Update` method of a <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span> <span data-ttu-id="52ec5-128">변경 내용을 개별적으로 서버에 제출하거나 그룹으로 일괄 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-128">Changes can be submitted to the server individually or batched into groups.</span></span> <span data-ttu-id="52ec5-129">그러나 여러 문이 포함된 일괄 처리로 전송된 경우에도 각 문은 서버에서 개별적으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-129">However, even when submitted in batches that contain multiple statements, each statement is executed separately on the server.</span></span>  
  
- <span data-ttu-id="52ec5-130">`bcp` 유틸리티 프로그램 또는 <xref:System.Data.SqlClient.SqlBulkCopy> 개체를 사용하여 많은 데이터 행을 테이블에 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-130">Use the `bcp` utility program or the <xref:System.Data.SqlClient.SqlBulkCopy> object to load many rows of data into a table.</span></span> <span data-ttu-id="52ec5-131">이 기법은 매우 효율적이지만 데이터를 임시 테이블 또는 테이블 변수에 로드하지 않는 한 서버 쪽 처리를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-131">Although this technique is very efficient, it does not support server-side processing unless the data is loaded into a temporary table or table variable.</span></span>  
  
## <a name="creating-table-valued-parameter-types"></a><span data-ttu-id="52ec5-132">테이블 반환 매개 변수 형식 만들기</span><span class="sxs-lookup"><span data-stu-id="52ec5-132">Creating Table-Valued Parameter Types</span></span>  
 <span data-ttu-id="52ec5-133">테이블 반환 매개 변수는 Transact-sql CREATE TYPE 문을 사용 하 여 정의 된 강력한 형식의 테이블 구조를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-133">Table-valued parameters are based on strongly typed table structures that are defined by using Transact-SQL CREATE TYPE statements.</span></span> <span data-ttu-id="52ec5-134">클라이언트 애플리케이션에서 테이블 반환 매개 변수를 사용할 수 있으려면 먼저 SQL Server에서 테이블 형식을 만들고 구조를 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-134">You have to create a table type and define the structure in SQL Server before you can use table-valued parameters in your client applications.</span></span> <span data-ttu-id="52ec5-135">테이블 형식을 만드는 방법에 대 한 자세한 내용은 [사용자 정의 테이블 형식](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="52ec5-135">For more information about creating table types, see [User-Defined Table Types](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100)).</span></span>  
  
 <span data-ttu-id="52ec5-136">다음 문은 CategoryID 및 CategoryName 열로 구성된 CategoryTableType 라는 테이블 형식을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-136">The following statement creates a table type named CategoryTableType that consists of CategoryID and CategoryName columns:</span></span>  
  
```sql
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
 <span data-ttu-id="52ec5-137">테이블 형식을 만든 후에는 해당 형식을 기반으로 테이블 반환 매개 변수를 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-137">After you create a table type, you can declare table-valued parameters based on that type.</span></span> <span data-ttu-id="52ec5-138">다음 Transact-SQL 조각은 저장 프로시저 정의에 테이블 반환 매개 변수를 선언하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-138">The following Transact-SQL fragment demonstrates how to declare a table-valued parameter in a stored procedure definition.</span></span> <span data-ttu-id="52ec5-139">테이블 반환 매개 변수를 선언하려면 READONLY 키워드가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-139">Note that the READONLY keyword is required for declaring a table-valued parameter.</span></span>  
  
```sql
CREATE PROCEDURE usp_UpdateCategories
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a><span data-ttu-id="52ec5-140">테이블 반환 매개 변수를 사용하여 데이터 수정(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="52ec5-140">Modifying Data with Table-Valued Parameters (Transact-SQL)</span></span>  
 <span data-ttu-id="52ec5-141">단일 문을 실행하여 여러 행에 영향을 주는 집합 기반 데이터 수정에 테이블 반환 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-141">Table-valued parameters can be used in set-based data modifications that affect multiple rows by executing a single statement.</span></span> <span data-ttu-id="52ec5-142">예를 들어 테이블 반환 매개 변수에서 모든 행을 선택하여 데이터베이스 테이블에 삽입하거나 테이블 반환 매개 변수를 업데이트하려는 테이블에 조인하여 update 문을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-142">For example, you can select all the rows in a table-valued parameter and insert them into a database table, or you can create an update statement by joining a table-valued parameter to the table you want to update.</span></span>  
  
 <span data-ttu-id="52ec5-143">다음 Transact-SQL UPDATE 문은 테이블 반환 매개 변수를 Categories 테이블에 조인하여 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-143">The following Transact-SQL UPDATE statement demonstrates how to use a table-valued parameter by joining it to the Categories table.</span></span> <span data-ttu-id="52ec5-144">FROM 절에서 JOIN과 함께 테이블 반환 매개 변수를 사용하는 경우 별칭을 지정해야 합니다. 여기서는 테이블 반환 매개 변수에 대한 별칭을 "ec"로 지정했습니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-144">When you use a table-valued parameter with a JOIN in a FROM clause, you must also alias it, as shown here, where the table-valued parameter is aliased as "ec":</span></span>  
  
```sql
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```  
  
 <span data-ttu-id="52ec5-145">이 Transact-SQL 예제에서는 테이블 반환 매개 변수에서 행을 선택하여 단일 집합 기반 작업으로 INSERT를 수행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-145">This Transact-SQL example demonstrates how to select rows from a table-valued parameter to perform an INSERT in a single set-based operation.</span></span>  
  
```sql
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```  
  
## <a name="limitations-of-table-valued-parameters"></a><span data-ttu-id="52ec5-146">테이블 반환 매개 변수의 제한 사항</span><span class="sxs-lookup"><span data-stu-id="52ec5-146">Limitations of Table-Valued Parameters</span></span>  
 <span data-ttu-id="52ec5-147">테이블 반환 매개 변수에는 다음과 같은 몇 가지 제한 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-147">There are several limitations to table-valued parameters:</span></span>  
  
- <span data-ttu-id="52ec5-148">[CLR 사용자 정의 함수](/sql/relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions)에는 테이블 반환 매개 변수를 전달할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-148">You cannot pass table-valued parameters to [CLR user-defined functions](/sql/relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions).</span></span>  
  
- <span data-ttu-id="52ec5-149">테이블 반환 매개 변수는 UNIQUE 또는 PRIMARY KEY 제약 조건을 지원하기 위해서만 인덱싱할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-149">Table-valued parameters can only be indexed to support UNIQUE or PRIMARY KEY constraints.</span></span> <span data-ttu-id="52ec5-150">SQL Server는 테이블 반환 매개 변수에 대한 통계를 유지 관리하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-150">SQL Server does not maintain statistics on table-valued parameters.</span></span>  
  
- <span data-ttu-id="52ec5-151">테이블 반환 매개 변수는 Transact-SQL 코드에서 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-151">Table-valued parameters are read-only in Transact-SQL code.</span></span> <span data-ttu-id="52ec5-152">테이블 반환 매개 변수 행의 열 값은 업데이트할 수 없으며 행을 삽입하거나 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-152">You cannot update the column values in the rows of a table-valued parameter and you cannot insert or delete rows.</span></span> <span data-ttu-id="52ec5-153">테이블 반환 매개 변수에서 저장 프로시저 또는 매개 변수화된 문에 전달되는 데이터를 수정하려면 데이터를 임시 테이블 또는 테이블 변수에 삽입해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-153">To modify the data that is passed to a stored procedure or parameterized statement in table-valued parameter, you must insert the data into a temporary table or into a table variable.</span></span>  
  
- <span data-ttu-id="52ec5-154">ALTER TABLE 문을 사용하여 테이블 반환 매개 변수의 디자인을 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-154">You cannot use ALTER TABLE statements to modify the design of table-valued parameters.</span></span>  
  
## <a name="configuring-a-sqlparameter-example"></a><span data-ttu-id="52ec5-155">SqlParameter 예제 구성</span><span class="sxs-lookup"><span data-stu-id="52ec5-155">Configuring a SqlParameter Example</span></span>  
 <span data-ttu-id="52ec5-156"><xref:System.Data.SqlClient>에서는 <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> 또는 <xref:System.Collections.Generic.IEnumerable%601> \ <xref:Microsoft.SqlServer.Server.SqlDataRecord> 개체를 통한 테이블 반환 매개 변수 채우기를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-156"><xref:System.Data.SqlClient> supports populating table-valued parameters from <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> or <xref:System.Collections.Generic.IEnumerable%601> \ <xref:Microsoft.SqlServer.Server.SqlDataRecord> objects.</span></span> <span data-ttu-id="52ec5-157">이 경우 <xref:System.Data.SqlClient.SqlParameter>의 <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> 속성을 사용하여 테이블 반환 매개 변수에 대한 형식 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-157">You must specify a type name for the table-valued parameter by using the <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> property of a <xref:System.Data.SqlClient.SqlParameter>.</span></span> <span data-ttu-id="52ec5-158">`TypeName`은 이전에 서버에서 만든 호환 가능한 형식의 이름과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-158">The `TypeName` must match the name of a compatible type previously created on the server.</span></span> <span data-ttu-id="52ec5-159">다음 코드 조각에서는 <xref:System.Data.SqlClient.SqlParameter>를 구성하여 데이터를 삽입하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-159">The following code fragment demonstrates how to configure <xref:System.Data.SqlClient.SqlParameter> to insert data.</span></span>  

<span data-ttu-id="52ec5-160">다음 예에서 `addedCategories` 변수는 <xref:System.Data.DataTable>을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-160">In the following example, the `addedCategories` variable contains a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="52ec5-161">변수가 채워지는 방법을 확인하려면 다음 섹션 [저장 프로시저에 테이블 반환 매개 변수 전달](#passing)의 예제를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="52ec5-161">To see how the variable is populated, see the examples in the next section, [Passing a Table-Valued Parameter to a Stored Procedure](#passing).</span></span>

```csharp  
// Configure the command and parameter.  
SqlCommand insertCommand = new SqlCommand(sqlInsert, connection);  
SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
tvpParam.SqlDbType = SqlDbType.Structured;  
tvpParam.TypeName = "dbo.CategoryTableType";  
```  
  
```vb  
' Configure the command and parameter.  
Dim insertCommand As New SqlCommand(sqlInsert, connection)  
Dim tvpParam As SqlParameter = _  
   insertCommand.Parameters.AddWithValue( _  
  "@tvpNewCategories", addedCategories)  
tvpParam.SqlDbType = SqlDbType.Structured  
tvpParam.TypeName = "dbo.CategoryTableType"  
```  
  
 <span data-ttu-id="52ec5-162">다음 코드 조각에서 볼 수 있는 것처럼 <xref:System.Data.Common.DbDataReader>에서 파생된 개체를 사용하여 데이터 행을 테이블 반환 매개 변수로 스트림할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-162">You can also use any object derived from <xref:System.Data.Common.DbDataReader> to stream rows of data to a table-valued parameter, as shown in this fragment:</span></span>  
  
```csharp  
// Configure the SqlCommand and table-valued parameter.  
SqlCommand insertCommand = new SqlCommand("usp_InsertCategories", connection);  
insertCommand.CommandType = CommandType.StoredProcedure;  
SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", dataReader);  
tvpParam.SqlDbType = SqlDbType.Structured;  
```  
  
```vb  
' Configure the SqlCommand and table-valued parameter.  
Dim insertCommand As New SqlCommand("usp_InsertCategories", connection)  
insertCommand.CommandType = CommandType.StoredProcedure  
Dim tvpParam As SqlParameter = _  
  insertCommand.Parameters.AddWithValue("@tvpNewCategories", _  
  dataReader)  
tvpParam.SqlDbType = SqlDbType.Structured  
```  
  
## <a name="passing-a-table-valued-parameter-to-a-stored-procedure"></a><a name="passing"></a><span data-ttu-id="52ec5-163">저장 프로시저에 테이블 반환 매개 변수 전달</span><span class="sxs-lookup"><span data-stu-id="52ec5-163">Passing a Table-Valued Parameter to a Stored Procedure</span></span>  
 <span data-ttu-id="52ec5-164">이 예제에서는 테이블 반환 매개 변수 데이터를 저장 프로시저에 전달하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-164">This example demonstrates how to pass table-valued parameter data to a stored procedure.</span></span> <span data-ttu-id="52ec5-165">이 코드는 <xref:System.Data.DataTable.GetChanges%2A> 메서드를 사용하여 새 <xref:System.Data.DataTable>에 추가된 행을 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-165">The code extracts added rows into a new <xref:System.Data.DataTable> by using the <xref:System.Data.DataTable.GetChanges%2A> method.</span></span> <span data-ttu-id="52ec5-166">그런 다음 코드는 <xref:System.Data.SqlClient.SqlCommand>를 정의하여 <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> 속성을 <xref:System.Data.CommandType.StoredProcedure>로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-166">The code then defines a <xref:System.Data.SqlClient.SqlCommand>, setting the <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> property to <xref:System.Data.CommandType.StoredProcedure>.</span></span> <span data-ttu-id="52ec5-167"><xref:System.Data.SqlClient.SqlParameter>는 <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> 메서드를 사용하여 채워지고 <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A>는 `Structured`로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-167">The <xref:System.Data.SqlClient.SqlParameter> is populated by using the <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> method and the <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> is set to `Structured`.</span></span> <span data-ttu-id="52ec5-168">그런 다음 <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> 메서드를 사용하여 <xref:System.Data.SqlClient.SqlCommand>를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-168">The <xref:System.Data.SqlClient.SqlCommand> is then executed by using the <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> method.</span></span>  
  
```csharp  
// Assumes connection is an open SqlConnection object.  
using (connection)  
{  
  // Create a DataTable with the modified rows.  
  DataTable addedCategories = CategoriesDataTable.GetChanges(DataRowState.Added);  

  // Configure the SqlCommand and SqlParameter.  
  SqlCommand insertCommand = new SqlCommand("usp_InsertCategories", connection);  
  insertCommand.CommandType = CommandType.StoredProcedure;  
  SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
  tvpParam.SqlDbType = SqlDbType.Structured;  

  // Execute the command.  
  insertCommand.ExecuteNonQuery();  
}  
```  
  
```vb  
' Assumes connection is an open SqlConnection object.  
Using connection  
   '  Create a DataTable with the modified rows.  
   Dim addedCategories As DataTable = _  
     CategoriesDataTable.GetChanges(DataRowState.Added)  
  
  ' Configure the SqlCommand and SqlParameter.  
   Dim insertCommand As New SqlCommand( _  
     "usp_InsertCategories", connection)  
   insertCommand.CommandType = CommandType.StoredProcedure  
   Dim tvpParam As SqlParameter = _  
     insertCommand.Parameters.AddWithValue( _  
     "@tvpNewCategories", addedCategories)  
   tvpParam.SqlDbType = SqlDbType.Structured  
  
   '  Execute the command.  
   insertCommand.ExecuteNonQuery()  
End Using  
```  
  
### <a name="passing-a-table-valued-parameter-to-a-parameterized-sql-statement"></a><span data-ttu-id="52ec5-169">매개 변수화된 SQL 문에 테이블 반환 매개 변수 전달</span><span class="sxs-lookup"><span data-stu-id="52ec5-169">Passing a Table-Valued Parameter to a Parameterized SQL Statement</span></span>  
 <span data-ttu-id="52ec5-170">다음 예제에서는 테이블 반환 매개 변수를 데이터 원본으로 사용하는 SELECT 하위 쿼리와 함께 INSERT 문을 사용하여 dbo.Categories 테이블에 데이터를 삽입하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-170">The following example demonstrates how to insert data into the dbo.Categories table by using an INSERT statement with a SELECT subquery that has a table-valued parameter as the data source.</span></span> <span data-ttu-id="52ec5-171">테이블 반환 매개 변수를 매개 변수가 있는 SQL 문에 전달할 때 <xref:System.Data.SqlClient.SqlParameter>의 새 <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> 속성을 사용하여 테이블 반환 매개 변수의 형식 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-171">When passing a table-valued parameter to a parameterized SQL statement, you must specify a type name for the table-valued parameter by using the new <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> property of a <xref:System.Data.SqlClient.SqlParameter>.</span></span> <span data-ttu-id="52ec5-172">이 `TypeName`은 이전에 서버에서 만든 호환 가능한 형식의 이름과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-172">This `TypeName` must match the name of a compatible type previously created on the server.</span></span> <span data-ttu-id="52ec5-173">이 예제의 코드는 `TypeName` 속성을 사용하여 dbo.CategoryTableType에 정의된 형식 구조를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-173">The code in this example uses the `TypeName` property to reference the type structure defined in dbo.CategoryTableType.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="52ec5-174">테이블 반환 매개 변수에서 ID 열에 대한 값을 제공하는 경우 세션에 SET IDENTITY_INSERT 문을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-174">If you supply a value for an identity column in a table-valued parameter, you must issue the SET IDENTITY_INSERT statement for the session.</span></span>  
  
```csharp  
// Assumes connection is an open SqlConnection.  
using (connection)  
{  
  // Create a DataTable with the modified rows.  
  DataTable addedCategories = CategoriesDataTable.GetChanges(DataRowState.Added);  

  // Define the INSERT-SELECT statement.  
  string sqlInsert =
      "INSERT INTO dbo.Categories (CategoryID, CategoryName)"  
      + " SELECT nc.CategoryID, nc.CategoryName"  
      + " FROM @tvpNewCategories AS nc;"  

  // Configure the command and parameter.  
  SqlCommand insertCommand = new SqlCommand(sqlInsert, connection);  
  SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
  tvpParam.SqlDbType = SqlDbType.Structured;  
  tvpParam.TypeName = "dbo.CategoryTableType";  

  // Execute the command.  
  insertCommand.ExecuteNonQuery();  
}  
```  
  
```vb  
' Assumes connection is an open SqlConnection.  
Using connection  
  ' Create a DataTable with the modified rows.  
  Dim addedCategories As DataTable = _  
    CategoriesDataTable.GetChanges(DataRowState.Added)  
  
  ' Define the INSERT-SELECT statement.  
  Dim sqlInsert As String = _  
  "INSERT INTO dbo.Categories (CategoryID, CategoryName)" _  
  & " SELECT nc.CategoryID, nc.CategoryName" _  
  & " FROM @tvpNewCategories AS nc;"  
  
  ' Configure the command and parameter.  
  Dim insertCommand As New SqlCommand(sqlInsert, connection)  
  Dim tvpParam As SqlParameter = _  
     insertCommand.Parameters.AddWithValue( _  
    "@tvpNewCategories", addedCategories)  
  tvpParam.SqlDbType = SqlDbType.Structured  
  tvpParam.TypeName = "dbo.CategoryTableType"  
  
  ' Execute the query  
  insertCommand.ExecuteNonQuery()  
End Using  
```  
  
## <a name="streaming-rows-with-a-datareader"></a><span data-ttu-id="52ec5-175">DataReader를 사용하여 행 스트리밍</span><span class="sxs-lookup"><span data-stu-id="52ec5-175">Streaming Rows with a DataReader</span></span>  
 <span data-ttu-id="52ec5-176"><xref:System.Data.Common.DbDataReader>에서 파생된 개체를 사용하여 데이터 행을 테이블 반환 매개 변수로 스트림할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-176">You can also use any object derived from <xref:System.Data.Common.DbDataReader> to stream rows of data to a table-valued parameter.</span></span> <span data-ttu-id="52ec5-177">다음 코드 조각에서는 <xref:System.Data.OracleClient.OracleCommand> 및 <xref:System.Data.OracleClient.OracleDataReader>를 사용하여 Oracle 데이터베이스에서 데이터를 검색하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-177">The following code fragment demonstrates retrieving data from an Oracle database by using an <xref:System.Data.OracleClient.OracleCommand> and an <xref:System.Data.OracleClient.OracleDataReader>.</span></span> <span data-ttu-id="52ec5-178">그런 다음 코드에서는 단일 입력 매개 변수를 사용하여 저장 프로시저를 호출하도록 <xref:System.Data.SqlClient.SqlCommand>를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-178">The code then configures a <xref:System.Data.SqlClient.SqlCommand> to invoke a stored procedure with a single input parameter.</span></span> <span data-ttu-id="52ec5-179"><xref:System.Data.SqlClient.SqlParameter>의 <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> 속성이 `Structured`로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-179">The <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> property of the <xref:System.Data.SqlClient.SqlParameter> is set to `Structured`.</span></span> <span data-ttu-id="52ec5-180"><xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A>는 `OracleDataReader` 결과 집합을 저장 프로시저에 테이블 반환 매개 변수로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="52ec5-180">The <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> passes the `OracleDataReader` result set to the stored procedure as a table-valued parameter.</span></span>  
  
```csharp  
// Assumes connection is an open SqlConnection.  
// Retrieve data from Oracle.  
OracleCommand selectCommand = new OracleCommand(  
   "Select CategoryID, CategoryName FROM Categories;",  
   oracleConnection);  
OracleDataReader oracleReader = selectCommand.ExecuteReader(  
   CommandBehavior.CloseConnection);  
  
 // Configure the SqlCommand and table-valued parameter.  
 SqlCommand insertCommand = new SqlCommand(  
   "usp_InsertCategories", connection);  
 insertCommand.CommandType = CommandType.StoredProcedure;  
 SqlParameter tvpParam =  
    insertCommand.Parameters.AddWithValue(  
    "@tvpNewCategories", oracleReader);  
 tvpParam.SqlDbType = SqlDbType.Structured;  
  
 // Execute the command.  
 insertCommand.ExecuteNonQuery();  
```  
  
```vb  
' Assumes connection is an open SqlConnection.  
' Retrieve data from Oracle.  
Dim selectCommand As New OracleCommand( _  
  "Select CategoryID, CategoryName FROM Categories;", _  
  oracleConnection)  
Dim oracleReader As OracleDataReader = _  
  selectCommand.ExecuteReader(CommandBehavior.CloseConnection)  
  
' Configure SqlCommand and table-valued parameter.  
Dim insertCommand As New SqlCommand("usp_InsertCategories", connection)  
insertCommand.CommandType = CommandType.StoredProcedure  
Dim tvpParam As SqlParameter = _  
  insertCommand.Parameters.AddWithValue("@tvpNewCategories", _  
  oracleReader)  
tvpParam.SqlDbType = SqlDbType.Structured  
  
' Execute the command.  
insertCommand.ExecuteNonQuery()  
```  
  
## <a name="see-also"></a><span data-ttu-id="52ec5-181">참고 항목</span><span class="sxs-lookup"><span data-stu-id="52ec5-181">See also</span></span>

- [<span data-ttu-id="52ec5-182">매개 변수 및 매개 변수 데이터 형식 구성</span><span class="sxs-lookup"><span data-stu-id="52ec5-182">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="52ec5-183">명령 및 매개 변수</span><span class="sxs-lookup"><span data-stu-id="52ec5-183">Commands and Parameters</span></span>](../commands-and-parameters.md)
- [<span data-ttu-id="52ec5-184">DataAdapter 매개 변수</span><span class="sxs-lookup"><span data-stu-id="52ec5-184">DataAdapter Parameters</span></span>](../dataadapter-parameters.md)
- [<span data-ttu-id="52ec5-185">ADO.NET의 SQL Server 데이터 작업</span><span class="sxs-lookup"><span data-stu-id="52ec5-185">SQL Server Data Operations in ADO.NET</span></span>](sql-server-data-operations.md)
- [<span data-ttu-id="52ec5-186">ADO.NET 개요</span><span class="sxs-lookup"><span data-stu-id="52ec5-186">ADO.NET Overview</span></span>](../ado-net-overview.md)
