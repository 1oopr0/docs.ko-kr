---
title: MARS(Multiple Active Result Sets) 사용
description: 연결 문자열에서 MARS를 사용 하거나 사용 하지 않도록 설정 하는 방법에 대해 알아봅니다. ADO.NET에서 단일 연결을 사용 하 여 여러 일괄 처리를 실행할 수 있도록 SQL Server와 함께 작동 합니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 576079e4-debe-4ab5-9204-fcbe2ca7a5e2
ms.openlocfilehash: 43bdfebce291c3c1d6c90104c5fef440b295934b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286483"
---
# <a name="enabling-multiple-active-result-sets"></a><span data-ttu-id="b3cff-103">MARS(Multiple Active Result Sets) 사용</span><span class="sxs-lookup"><span data-stu-id="b3cff-103">Enabling Multiple Active Result Sets</span></span>
<span data-ttu-id="b3cff-104">MARS(Multiple Active Result Sets)는 단일 연결에서 여러 배치를 실행할 수 있도록 하는 SQL Server의 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-104">Multiple Active Result Sets (MARS) is a feature that works with SQL Server to allow the execution of multiple batches on a single connection.</span></span> <span data-ttu-id="b3cff-105">SQL Server에 MARS가 활성화되어 있으면 명령 개체를 사용할 때마다 연결에 세션이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-105">When MARS is enabled for use with SQL Server, each command object used adds a session to the connection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b3cff-106">단일 MARS 세션에서 MARS가 사용할 논리적 연결을 1개 열고 각 활성 명령에 대해 논리적 연결을 1개씩 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-106">A single MARS session opens one logical connection for MARS to use and then one logical connection for each active command.</span></span>  
  
## <a name="enabling-and-disabling-mars-in-the-connection-string"></a><span data-ttu-id="b3cff-107">연결 문자열에서 MARS 활성화 및 비활성화</span><span class="sxs-lookup"><span data-stu-id="b3cff-107">Enabling and Disabling MARS in the Connection String</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b3cff-108">다음 연결 문자열에서는 SQL Server에 포함된 샘플 **AdventureWorks** 데이터베이스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-108">The following connection strings use the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="b3cff-109">제공된 연결 문자열은 데이터베이스가 MSSQL1이라는 서버에 설치되어 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-109">The connection strings provided assume that the database is installed on a server named MSSQL1.</span></span> <span data-ttu-id="b3cff-110">사용자 환경에 필요한 경우 연결 문자열을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-110">Modify the connection string as necessary for your environment.</span></span>  
  
 <span data-ttu-id="b3cff-111">MARS 기능은 기본적으로 해제되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-111">The MARS feature is disabled by default.</span></span> <span data-ttu-id="b3cff-112">연결 문자열에 "MultipleActiveResultSets=True" 키워드 쌍을 추가하여 사용하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-112">It can be enabled by adding the "MultipleActiveResultSets=True" keyword pair to your connection string.</span></span> <span data-ttu-id="b3cff-113">MARS를 활성화하는 유일한 유효 값은 "True"입니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-113">"True" is the only valid value for enabling MARS.</span></span> <span data-ttu-id="b3cff-114">다음 예제에서는 SQL Server 인스턴스에 연결하고 MARS를 사용하도록 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-114">The following example demonstrates how to connect to an instance of SQL Server and how to specify that MARS should be enabled.</span></span>  
  
```vb  
Dim connectionString As String = "Data Source=MSSQL1;" & _  
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" & _  
    "MultipleActiveResultSets=True"  
```  
  
```csharp  
string connectionString = "Data Source=MSSQL1;" +
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" +  
    "MultipleActiveResultSets=True";  
```  
  
 <span data-ttu-id="b3cff-115">연결 문자열에 "MultipleActiveResultSets=False" 키워드 쌍을 추가하여 MARS를 사용하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-115">You can disable MARS by adding the "MultipleActiveResultSets=False" keyword pair to your connection string.</span></span> <span data-ttu-id="b3cff-116">MARS를 비활성화하는 유일한 유효 값은 "False"입니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-116">"False" is the only valid value for disabling MARS.</span></span> <span data-ttu-id="b3cff-117">다음 연결 문자열에서는 MARS를 사용하지 않도록 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-117">The following connection string demonstrates how to disable MARS.</span></span>  
  
```vb  
Dim connectionString As String = "Data Source=MSSQL1;" & _  
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" & _  
    "MultipleActiveResultSets=False"  
```  
  
```csharp  
string connectionString = "Data Source=MSSQL1;" +
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" +  
    "MultipleActiveResultSets=False";  
```  
  
## <a name="special-considerations-when-using-mars"></a><span data-ttu-id="b3cff-118">MARS를 사용할 때 특별히 고려할 사항</span><span class="sxs-lookup"><span data-stu-id="b3cff-118">Special Considerations When Using MARS</span></span>  
 <span data-ttu-id="b3cff-119">일반적으로 기존 애플리케이션은 MARS 사용 연결을 사용하기 위해 수정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-119">In general, existing applications should not need modification to use a MARS-enabled connection.</span></span> <span data-ttu-id="b3cff-120">그러나 애플리케이션에서 MARS 기능을 사용하려는 경우 다음과 같은 특별한 고려 사항을 이해해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-120">However, if you wish to use MARS features in your applications, you should understand the following special considerations.</span></span>  
  
### <a name="statement-interleaving"></a><span data-ttu-id="b3cff-121">문 인터리빙</span><span class="sxs-lookup"><span data-stu-id="b3cff-121">Statement Interleaving</span></span>  
 <span data-ttu-id="b3cff-122">MARS 작업은 서버에서 동기식으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-122">MARS operations execute synchronously on the server.</span></span> <span data-ttu-id="b3cff-123">SELECT 및 BULK INSERT 문의 문 인터리빙이 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-123">Statement interleaving of SELECT and BULK INSERT statements is allowed.</span></span> <span data-ttu-id="b3cff-124">그러나 DML(데이터 조작 언어) 및 DDL(데이터 정의 언어) 문은 원자성으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-124">However, data manipulation language (DML) and data definition language (DDL) statements execute atomically.</span></span> <span data-ttu-id="b3cff-125">원자성 일괄 처리가 실행되는 동안 실행하려는 모든 문은 차단됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-125">Any statements attempting to execute while an atomic batch is executing are blocked.</span></span> <span data-ttu-id="b3cff-126">서버에서의 병렬 실행은 MARS 기능이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-126">Parallel execution at the server is not a MARS feature.</span></span>  
  
 <span data-ttu-id="b3cff-127">MARS 연결에서 하나는 SELECT 문을 포함하고 다른 하나는 DML 문을 포함하는 두 개의 일괄 처리를 제출하는 경우 SELECT 문이 실행되는 동안 DML이 실행을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-127">If two batches are submitted under a MARS connection, one of them containing a SELECT statement, the other containing a DML statement, the DML can begin execution within execution of the SELECT statement.</span></span> <span data-ttu-id="b3cff-128">그러나 SELECT 문 실행이 진행되려면 DML 문이 실행을 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-128">However, the DML statement must run to completion before the SELECT statement can make progress.</span></span> <span data-ttu-id="b3cff-129">두 문이 동일한 트랜잭션에서 실행되는 경우 SELECT 문 실행이 시작된 후 DML 문에 의한 변경 내용은 읽기 작업에 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-129">If both statements are running under the same transaction, any changes made by a DML statement after the SELECT statement has started execution are not visible to the read operation.</span></span>  
  
 <span data-ttu-id="b3cff-130">SELECT 문 내부의 WAITFOR 문은 첫 번째 행이 생성될 때까지 대기하는 동안 트랜잭션을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-130">A WAITFOR statement inside a SELECT statement does not yield the transaction while it is waiting, that is, until the first row is produced.</span></span> <span data-ttu-id="b3cff-131">이는 WAITFOR 문이 대기하는 동안 동일한 연결 내에서 다른 일괄 처리를 실행할 수 없음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-131">This implies that no other batches can execute within the same connection while a WAITFOR statement is waiting.</span></span>  
  
### <a name="mars-session-cache"></a><span data-ttu-id="b3cff-132">MARS 세션 캐시</span><span class="sxs-lookup"><span data-stu-id="b3cff-132">MARS Session Cache</span></span>  
 <span data-ttu-id="b3cff-133">MARS가 활성화된 상태에서 연결이 열리면 논리 세션이 만들어지고 오버헤드가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-133">When a connection is opened with MARS enabled, a logical session is created, which adds additional overhead.</span></span> <span data-ttu-id="b3cff-134">오버헤드를 최소화하고 성능을 높이기 위해 **SqlClient**가 연결 내에서 MARS 세션을 캐시합니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-134">To minimize overhead and enhance performance, **SqlClient** caches the MARS session within a connection.</span></span> <span data-ttu-id="b3cff-135">캐시에는 최대 10개의 MARS 세션이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-135">The cache contains at most 10 MARS sessions.</span></span> <span data-ttu-id="b3cff-136">이 값은 사용자가 조정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-136">This value is not user adjustable.</span></span> <span data-ttu-id="b3cff-137">세션 제한에 도달하면 새 세션이 만들어지며, 이때 오류는 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-137">If the session limit is reached, a new session is created—an error is not generated.</span></span> <span data-ttu-id="b3cff-138">캐시와 여기에 포함된 세션은 연결 기준입니다. 연결 간에 공유되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-138">The cache and sessions contained in it are per-connection; they are not shared across connections.</span></span> <span data-ttu-id="b3cff-139">세션을 해제하면 풀 상한에 도달하지 않은 한 풀로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-139">When a session is released, it is returned to the pool unless the pool's upper limit has been reached.</span></span> <span data-ttu-id="b3cff-140">캐시 풀이 꽉 차면 세션이 닫힙니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-140">If the cache pool is full, the session is closed.</span></span> <span data-ttu-id="b3cff-141">MARS 세션은 만료되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-141">MARS sessions do not expire.</span></span> <span data-ttu-id="b3cff-142">연결 개체가 삭제될 때만 정리됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-142">They are only cleaned up when the connection object is disposed.</span></span> <span data-ttu-id="b3cff-143">MARS 세션 캐시는 미리 로드되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-143">The MARS session cache is not preloaded.</span></span> <span data-ttu-id="b3cff-144">애플리케이션에 더 많은 세션이 필요할 때 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-144">It is loaded as the application requires more sessions.</span></span>  
  
### <a name="thread-safety"></a><span data-ttu-id="b3cff-145">스레드 보안</span><span class="sxs-lookup"><span data-stu-id="b3cff-145">Thread Safety</span></span>  
 <span data-ttu-id="b3cff-146">MARS 작업은 스레드로부터 안전하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-146">MARS operations are not thread-safe.</span></span>  
  
### <a name="connection-pooling"></a><span data-ttu-id="b3cff-147">연결 풀링</span><span class="sxs-lookup"><span data-stu-id="b3cff-147">Connection Pooling</span></span>  
 <span data-ttu-id="b3cff-148">MARS 사용 연결은 다른 연결과 마찬가지로 풀링됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-148">MARS-enabled connections are pooled like any other connection.</span></span> <span data-ttu-id="b3cff-149">애플리케이션에서 MARS를 사용하도록 설정한 연결 1개와 MARS를 사용하지 않도록 설정한 연결 1개를 여는 경우 두 연결은 서로 다른 풀에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-149">If an application opens two connections, one with MARS enabled and one with MARS disabled, the two connections are in separate pools.</span></span> <span data-ttu-id="b3cff-150">자세한 내용은 [SQL Server 연결 풀링(ADO.NET)](../sql-server-connection-pooling.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b3cff-150">For more information, see [SQL Server Connection Pooling (ADO.NET)](../sql-server-connection-pooling.md).</span></span>  
  
### <a name="sql-server-batch-execution-environment"></a><span data-ttu-id="b3cff-151">SQL Server 배치 실행 환경</span><span class="sxs-lookup"><span data-stu-id="b3cff-151">SQL Server Batch Execution Environment</span></span>  
 <span data-ttu-id="b3cff-152">연결이 열리면 기본 환경이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-152">When a connection is opened, a default environment is defined.</span></span> <span data-ttu-id="b3cff-153">그런 다음 이 환경은 논리적 MARS 세션에 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-153">This environment is then copied into a logical MARS session.</span></span>  
  
 <span data-ttu-id="b3cff-154">일괄 처리 실행 환경에는 다음 구성 요소가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-154">The batch execution environment includes the following components:</span></span>  
  
- <span data-ttu-id="b3cff-155">설정된 옵션(예: ANSI_NULLS, DATE_FORMAT, LANGUAGE, TEXTSIZE)</span><span class="sxs-lookup"><span data-stu-id="b3cff-155">Set options (for example, ANSI_NULLS, DATE_FORMAT, LANGUAGE, TEXTSIZE)</span></span>  
  
- <span data-ttu-id="b3cff-156">보안 컨텍스트(사용자/애플리케이션 역할)</span><span class="sxs-lookup"><span data-stu-id="b3cff-156">Security context (user/application role)</span></span>  
  
- <span data-ttu-id="b3cff-157">데이터베이스 컨텍스트(현재 데이터베이스)</span><span class="sxs-lookup"><span data-stu-id="b3cff-157">Database context (current database)</span></span>  
  
- <span data-ttu-id="b3cff-158">실행 상태 변수(예: @@ERROR, @@ROWCOUNT, @@FETCH_STATUS @@IDENTITY)</span><span class="sxs-lookup"><span data-stu-id="b3cff-158">Execution state variables (for example, @@ERROR, @@ROWCOUNT, @@FETCH_STATUS @@IDENTITY)</span></span>  
  
- <span data-ttu-id="b3cff-159">최상위 임시 테이블</span><span class="sxs-lookup"><span data-stu-id="b3cff-159">Top-level temporary tables</span></span>  
  
 <span data-ttu-id="b3cff-160">MARS를 사용하면 기본 실행 환경이 연결과 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-160">With MARS, a default execution environment is associated to a connection.</span></span> <span data-ttu-id="b3cff-161">특정 연결에서 실행을 시작하는 각각의 새 일괄 처리는 기본 환경의 복사본을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-161">Every new batch that starts executing under a given connection receives a copy of the default environment.</span></span> <span data-ttu-id="b3cff-162">지정된 일괄 처리에서 코드가 실행될 때마다 해당 환경에 대한 모든 변경 사항은 특정 일괄 처리로 범위가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-162">Whenever code is executed under a given batch, all changes made to the environment are scoped to the specific batch.</span></span> <span data-ttu-id="b3cff-163">실행이 완료되면 실행 설정이 기본 환경에 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-163">Once execution finishes, the execution settings are copied into the default environment.</span></span> <span data-ttu-id="b3cff-164">동일한 트랜잭션에서 순차적으로 여러 명령을 실행하는 단일 일괄 처리의 경우 의미 체계는 이전 클라이언트 또는 서버와 관련된 연결에서 노출하는 것과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-164">In the case of a single batch issuing several commands to be executed sequentially under the same transaction, semantics are the same as those exposed by connections involving earlier clients or servers.</span></span>  
  
### <a name="parallel-execution"></a><span data-ttu-id="b3cff-165">병렬 실행</span><span class="sxs-lookup"><span data-stu-id="b3cff-165">Parallel Execution</span></span>  
 <span data-ttu-id="b3cff-166">MARS는 애플리케이션의 다중 연결에 대한 모든 요구 사항을 제거하도록 설계되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-166">MARS is not designed to remove all requirements for multiple connections in an application.</span></span> <span data-ttu-id="b3cff-167">애플리케이션은 반드시 서버에서 명령을 병렬 실행해야 하는 경우 여러 연결을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-167">If an application needs true parallel execution of commands against a server, multiple connections should be used.</span></span>  
  
 <span data-ttu-id="b3cff-168">예를 들어 다음 시나리오를 고려해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-168">For example, consider the following scenario.</span></span> <span data-ttu-id="b3cff-169">두 개의 명령 개체를 만듭니다. 한 개체는 결과 집합을 처리하고 다른 개체는 데이터를 업데이트합니다. 이들은 MARS를 통해 한 연결을 공유합니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-169">Two command objects are created, one for processing a result set and another for updating data; they share a common connection via MARS.</span></span> <span data-ttu-id="b3cff-170">시나리오 내용: `Transaction``Commit`</span><span class="sxs-lookup"><span data-stu-id="b3cff-170">In this scenario, the `Transaction`.`Commit`</span></span> <span data-ttu-id="b3cff-171">첫 번째 명령 개체에서 모든 결과를 읽을 때까지 업데이트를 수행하지 못하므로 다음과 같은 예외가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-171">fails on the update until all the results have been read on the first command object, yielding the following exception:</span></span>  
  
 <span data-ttu-id="b3cff-172">메시지: 다른 세션에서 트랜잭션 컨텍스트를 사용 중입니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-172">Message: Transaction context in use by another session.</span></span>  
  
 <span data-ttu-id="b3cff-173">소스: .NET SqlClient Data Provider</span><span class="sxs-lookup"><span data-stu-id="b3cff-173">Source: .NET SqlClient Data Provider</span></span>  
  
 <span data-ttu-id="b3cff-174">예상: (null)</span><span class="sxs-lookup"><span data-stu-id="b3cff-174">Expected: (null)</span></span>  
  
 <span data-ttu-id="b3cff-175">수신: System.Data.SqlClient.SqlException</span><span class="sxs-lookup"><span data-stu-id="b3cff-175">Received: System.Data.SqlClient.SqlException</span></span>  
  
 <span data-ttu-id="b3cff-176">이 시나리오를 처리하기 위한 세 가지 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-176">There are three options for handling this scenario:</span></span>  
  
1. <span data-ttu-id="b3cff-177">트랜잭션이 포함되지 않도록 판독기를 만든 후 트랜잭션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-177">Start the transaction after the reader is created, so that it is not part of the transaction.</span></span> <span data-ttu-id="b3cff-178">그러면 모든 업데이트가 자체 트랜잭션이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-178">Every update then becomes its own transaction.</span></span>  
  
2. <span data-ttu-id="b3cff-179">판독기를 닫은 후 모든 작업을 커밋합니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-179">Commit all work after the reader is closed.</span></span> <span data-ttu-id="b3cff-180">이렇게 하면 대량의 업데이트를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-180">This has the potential for a substantial batch of updates.</span></span>  
  
3. <span data-ttu-id="b3cff-181">MARS를 사용하지 않습니다. MARS가 없을 때처럼 각 명령 개체에 대해 별도의 연결을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-181">Don't use MARS; instead use a separate connection for each command object as you would have before MARS.</span></span>  
  
### <a name="detecting-mars-support"></a><span data-ttu-id="b3cff-182">MARS 지원 검색</span><span class="sxs-lookup"><span data-stu-id="b3cff-182">Detecting MARS Support</span></span>  
 <span data-ttu-id="b3cff-183">애플리케이션은 `SqlConnection.ServerVersion` 값을 읽어 MARS 지원을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-183">An application can check for MARS support by reading the `SqlConnection.ServerVersion` value.</span></span> <span data-ttu-id="b3cff-184">주 번호는 SQL Server 2005의 경우 9, SQL Server 2008의 경우 10입니다.</span><span class="sxs-lookup"><span data-stu-id="b3cff-184">The major number should be 9 for SQL Server 2005 and 10 for SQL Server 2008.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3cff-185">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b3cff-185">See also</span></span>

- [<span data-ttu-id="b3cff-186">MARS(Multiple Active Result Sets)</span><span class="sxs-lookup"><span data-stu-id="b3cff-186">Multiple Active Result Sets (MARS)</span></span>](multiple-active-result-sets-mars.md)
- [<span data-ttu-id="b3cff-187">ADO.NET 개요</span><span class="sxs-lookup"><span data-stu-id="b3cff-187">ADO.NET Overview</span></span>](../ado-net-overview.md)
