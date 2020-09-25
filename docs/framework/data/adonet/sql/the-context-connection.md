---
title: 컨텍스트 연결
ms.date: 03/30/2017
ms.assetid: e443ca86-9243-4234-a822-ed10a53a9de0
ms.openlocfilehash: 85b303d62b619a8139ca56b23cacd3411cebc17b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91188852"
---
# <a name="the-context-connection"></a><span data-ttu-id="2f6a8-102">컨텍스트 연결</span><span class="sxs-lookup"><span data-stu-id="2f6a8-102">The Context Connection</span></span>

<span data-ttu-id="2f6a8-103">내부 데이터 액세스 문제는 상당히 일반적인 시나리오입니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a8-103">The problem of internal data access is a fairly common scenario.</span></span> <span data-ttu-id="2f6a8-104">즉, CLR(공용 언어 런타임) 저장 프로시저 또는 함수가 실행 중인 서버에 액세스하려는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a8-104">That is, you wish to access the same server on which your common language runtime (CLR) stored procedure or function is executing.</span></span> <span data-ttu-id="2f6a8-105">한 가지 방법은 <xref:System.Data.SqlClient.SqlConnection>을 사용하여 연결을 만들고, 로컬 서버를 가리키는 연결 문자열을 지정하고, 연결을 여는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a8-105">One option is to create a connection using <xref:System.Data.SqlClient.SqlConnection>, specify a connection string that points to the local server, and open the connection.</span></span> <span data-ttu-id="2f6a8-106">이렇게 하려면 로그인에 사용할 자격 증명을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a8-106">This requires specifying credentials for logging in.</span></span> <span data-ttu-id="2f6a8-107">연결은 저장 프로시저 또는 함수와 다른 데이터베이스 세션에 있거나, 다른 `SET` 옵션을 가지거나, 별도의 트랜잭션에 있거나, 사용자의 임시 테이블을 볼 수 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a8-107">The connection is in a different database session than the stored procedure or function, it may have different `SET` options, it is in a separate transaction, it does not see your temporary tables, and so on.</span></span> <span data-ttu-id="2f6a8-108">사용자의 관리 저장 프로시저 또는 함수 코드가 SQL Server 서버 프로세스에서 실행되는 경우 다른 사용자가 해당 서버에 연결하고 SQL 문을 실행하여 이를 호출했기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a8-108">If your managed stored procedure or function code is executing in the SQL Server process, it is because someone connected to that server and executed a SQL statement to invoke it.</span></span> <span data-ttu-id="2f6a8-109">저장 프로시저 또는 함수를 이 연결의 트랜잭션, `SET` 옵션 등과 함께 이 연결의 컨텍스트에서 실행하려는 경우가 있는데</span><span class="sxs-lookup"><span data-stu-id="2f6a8-109">You probably want the stored procedure or function to execute in the context of that connection, along with its transaction, `SET` options, and so on.</span></span> <span data-ttu-id="2f6a8-110">이를 컨텍스트 연결이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a8-110">This is called the context connection.</span></span>  
  
 <span data-ttu-id="2f6a8-111">컨텍스트 연결을 사용하여 코드를 처음 호출한 컨텍스트에서 Transact-SQL 문을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a8-111">The context connection lets you execute Transact-SQL statements in the same context that your code was invoked in the first place.</span></span> <span data-ttu-id="2f6a8-112">자세한 내용을 보려면 현재 사용하고 있는 SQL Server 버전에 해당하는 SQL Server 온라인 설명서 버전을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2f6a8-112">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="2f6a8-113">**SQL Server 설명서**</span><span class="sxs-lookup"><span data-stu-id="2f6a8-113">**SQL Server documentation**</span></span>  
  
1. [<span data-ttu-id="2f6a8-114">컨텍스트 연결</span><span class="sxs-lookup"><span data-stu-id="2f6a8-114">The Context Connection</span></span>](/sql/relational-databases/clr-integration/data-access/context-connection)  
  
## <a name="see-also"></a><span data-ttu-id="2f6a8-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2f6a8-115">See also</span></span>

- [<span data-ttu-id="2f6a8-116">ADO.NET 개요</span><span class="sxs-lookup"><span data-stu-id="2f6a8-116">ADO.NET Overview</span></span>](../ado-net-overview.md)
