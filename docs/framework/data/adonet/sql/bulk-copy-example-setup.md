---
title: 대량 복사 예제 설정
ms.date: 03/30/2017
ms.assetid: d4dde6ac-b8b6-4593-965a-635c8fb2dadb
ms.openlocfilehash: 562d36e0aee72fcc0619ec4ed7362622ba652337
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197484"
---
# <a name="bulk-copy-example-setup"></a><span data-ttu-id="deab7-102">대량 복사 예제 설정</span><span class="sxs-lookup"><span data-stu-id="deab7-102">Bulk Copy Example Setup</span></span>

<span data-ttu-id="deab7-103"><xref:System.Data.SqlClient.SqlBulkCopy> 클래스를 사용하면 SQL Server 테이블에만 데이터를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="deab7-103">The <xref:System.Data.SqlClient.SqlBulkCopy> class can be used to write data only to SQL Server tables.</span></span> <span data-ttu-id="deab7-104">이 항목에 표시된 코드 샘플에서는 SQL Server 샘플 데이터베이스 **AdventureWorks**를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="deab7-104">The code samples shown in this topic use the SQL Server sample database, **AdventureWorks**.</span></span> <span data-ttu-id="deab7-105">기존 테이블 코드 샘플이 변경되지 않도록 하려면 먼저 만들어야 하는 테이블에 데이터를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="deab7-105">To avoid altering the existing tables code samples write data to tables that you must create first.</span></span>  
  
 <span data-ttu-id="deab7-106">**BulkCopyDemoMatchingColumns** 및 **BulkCopyDemoDifferentColumns** 테이블은 모두 **AdventureWorks** **Production.Products** 테이블을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="deab7-106">The **BulkCopyDemoMatchingColumns** and **BulkCopyDemoDifferentColumns** tables are both based on the **AdventureWorks** **Production.Products** table.</span></span> <span data-ttu-id="deab7-107">이러한 테이블을 사용 하는 코드 샘플에서는 데이터를 **Production** 테이블에서 이러한 샘플 테이블 중 하나로 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="deab7-107">In code samples that use these tables, data is added from the **Production.Products** table to one of these sample tables.</span></span> <span data-ttu-id="deab7-108">**BulkCopyDemoDifferentColumns** 테이블은 샘플에서 원본 데이터의 열을 대상 테이블에 매핑하는 방법을 보여 주는 경우 사용 됩니다. **BulkCopyDemoMatchingColumns** 는 대부분의 다른 샘플에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="deab7-108">The **BulkCopyDemoDifferentColumns** table is used when the sample illustrates how to map columns from the source data to the destination table; **BulkCopyDemoMatchingColumns** is used for most other samples.</span></span>  
  
 <span data-ttu-id="deab7-109">일부 코드 샘플에서는 하나의 <xref:System.Data.SqlClient.SqlBulkCopy> 클래스를 사용하여 여러 테이블에 쓰는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="deab7-109">A few of the code samples demonstrate how to use one <xref:System.Data.SqlClient.SqlBulkCopy> class to write to multiple tables.</span></span> <span data-ttu-id="deab7-110">이러한 샘플의 경우 **대량 Copydemoorderheader** 및 **대량 Copydemoorderdetail** 테이블이 대상 테이블로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="deab7-110">For these samples, the **BulkCopyDemoOrderHeader** and **BulkCopyDemoOrderDetail** tables are used as the destination tables.</span></span> <span data-ttu-id="deab7-111">이러한 테이블은 **AdventureWorks**의 **SalesOrderHeader** 및 **SalesOrderDetail** 테이블을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="deab7-111">These tables are based on the **Sales.SalesOrderHeader** and **Sales.SalesOrderDetail** tables in **AdventureWorks**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="deab7-112">**SqlBulkCopy** 코드 샘플은 **SqlBulkCopy**를 사용하는 구문을 보여 주기 위한 용도로만 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="deab7-112">The **SqlBulkCopy** code samples are provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="deab7-113">원본 테이블과 대상 테이블이 동일한 SQL Server 인스턴스에 있으면 Transact-SQL `INSERT … SELECT` 문을 사용하여 데이터를 더 쉽고 빠르게 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="deab7-113">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>  
  
## <a name="table-setup"></a><span data-ttu-id="deab7-114">테이블 설정</span><span class="sxs-lookup"><span data-stu-id="deab7-114">Table Setup</span></span>  

 <span data-ttu-id="deab7-115">코드 샘플을 올바르게 실행하는 데 필요한 테이블을 만들려면 SQL Server 데이터베이스에서 다음 TRANSACT-SQL 문을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="deab7-115">To create the tables necessary for the code samples to run correctly, you must run the following Transact-SQL statements in a SQL Server database.</span></span>  
  
```sql
USE AdventureWorks  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoMatchingColumns]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoMatchingColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoMatchingColumns]([ProductID] [int] IDENTITY(1,1) NOT NULL,  
    [Name] [nvarchar](50) NOT NULL,  
    [ProductNumber] [nvarchar](25) NOT NULL,  
 CONSTRAINT [PK_ProductID] PRIMARY KEY CLUSTERED  
(  
    [ProductID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoDifferentColumns]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoDifferentColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoDifferentColumns]([ProdID] [int] IDENTITY(1,1) NOT NULL,  
    [ProdNum] [nvarchar](25) NOT NULL,  
    [ProdName] [nvarchar](50) NOT NULL,  
 CONSTRAINT [PK_ProdID] PRIMARY KEY CLUSTERED  
(  
    [ProdID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderHeader]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderHeader]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderHeader]([SalesOrderID] [int] IDENTITY(1,1) NOT NULL,  
    [OrderDate] [datetime] NOT NULL,  
    [AccountNumber] [nvarchar](15) NULL,  
 CONSTRAINT [PK_SalesOrderID] PRIMARY KEY CLUSTERED  
(  
    [SalesOrderID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderDetail]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderDetail]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderDetail]([SalesOrderID] [int] NOT NULL,  
    [SalesOrderDetailID] [int] NOT NULL,  
    [OrderQty] [smallint] NOT NULL,  
    [ProductID] [int] NOT NULL,  
    [UnitPrice] [money] NOT NULL,  
 CONSTRAINT [PK_LineNumber] PRIMARY KEY CLUSTERED  
(  
    [SalesOrderID] ASC,  
    [SalesOrderDetailID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
```  
  
## <a name="see-also"></a><span data-ttu-id="deab7-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="deab7-116">See also</span></span>

- [<span data-ttu-id="deab7-117">SQL Server에서 대량 복사 작업</span><span class="sxs-lookup"><span data-stu-id="deab7-117">Bulk Copy Operations in SQL Server</span></span>](bulk-copy-operations-in-sql-server.md)
- [<span data-ttu-id="deab7-118">ADO.NET 개요</span><span class="sxs-lookup"><span data-stu-id="deab7-118">ADO.NET Overview</span></span>](../ado-net-overview.md)
