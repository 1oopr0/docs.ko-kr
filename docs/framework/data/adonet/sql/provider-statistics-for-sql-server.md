---
title: SQL Server용 공급자 통계
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 429c9d09-92ac-46ec-829a-fbff0a9575a2
ms.openlocfilehash: 21bf7662094d5bc8948a1ce6378c454713cacc62
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183119"
---
# <a name="provider-statistics-for-sql-server"></a><span data-ttu-id="b25e6-102">SQL Server용 공급자 통계</span><span class="sxs-lookup"><span data-stu-id="b25e6-102">Provider Statistics for SQL Server</span></span>

<span data-ttu-id="b25e6-103">.NET Framework 버전 2.0부터는 .NET Framework Data Provider for SQL Server에 런타임 통계가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-103">Starting with the .NET Framework version 2.0, the .NET Framework Data Provider for SQL Server supports run-time statistics.</span></span> <span data-ttu-id="b25e6-104">유효한 연결 개체를 만든 후 <xref:System.Data.SqlClient.SqlConnection> 개체의 <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> 속성을 `True`로 설정하여 통계를 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-104">You must enable statistics by setting the <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> property of the <xref:System.Data.SqlClient.SqlConnection> object to `True` after you have a valid connection object created.</span></span> <span data-ttu-id="b25e6-105">통계를 사용하도록 설정한 후에는 <xref:System.Data.SqlClient.SqlConnection> 개체의 <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> 메서드를 통해 <xref:System.Collections.IDictionary> 참조를 검색하여 "특정 시점 스냅샷"으로 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-105">After statistics are enabled, you can review them as a "snapshot in time" by retrieving an <xref:System.Collections.IDictionary> reference via the <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="b25e6-106">목록 전체를 이름/값 쌍 사전 항목 집합으로 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-106">You enumerate through the list as a set of name/value pair dictionary entries.</span></span> <span data-ttu-id="b25e6-107">이러한 이름/값 쌍은 순서가 지정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-107">These name/value pairs are unordered.</span></span> <span data-ttu-id="b25e6-108">언제든지 <xref:System.Data.SqlClient.SqlConnection> 개체의 <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> 메서드를 호출하여 카운터를 초기화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-108">At any time, you can call the <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object to reset the counters.</span></span> <span data-ttu-id="b25e6-109">통계 수집을 사용하도록 설정하지 않은 경우 예외가 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-109">If statistic gathering has not been enabled, an exception is not generated.</span></span> <span data-ttu-id="b25e6-110">또한 <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A>를 먼저 호출하지 않고 <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>를 호출하는 경우 검색된 값은 각 항목의 초기 값입니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-110">In addition, if <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> is called without <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> having been called first, the values retrieved are the initial values for each entry.</span></span> <span data-ttu-id="b25e6-111">통계를 사용하도록 설정하고 잠시 동안 애플리케이션을 실행한 다음 통계를 사용하지 않도록 설정하면 검색된 값에 통계를 사용하지 않도록 설정한 지점까지 수집된 값이 반영됩니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-111">If you enable statistics, run your application for a while, and then disable statistics, the values retrieved will reflect the values collected up to the point where statistics were disabled.</span></span> <span data-ttu-id="b25e6-112">모든 통계 값은 연결 단위로 수집됩니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-112">All statistical values gathered are on a per-connection basis.</span></span>  
  
## <a name="statistical-values-available"></a><span data-ttu-id="b25e6-113">사용 가능한 통계 값</span><span class="sxs-lookup"><span data-stu-id="b25e6-113">Statistical Values Available</span></span>  

 <span data-ttu-id="b25e6-114">현재 Microsoft SQL Server 공급자에서 사용할 수 있는 항목은 18개입니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-114">Currently there are 18 different items available from the Microsoft SQL Server provider.</span></span> <span data-ttu-id="b25e6-115">사용 가능한 항목의 수는 <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>에서 반환한 <xref:System.Collections.IDictionary> 인터페이스 참조의 **Count** 속성을 통해 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-115">The number of items available can be accessed via the **Count** property of the <xref:System.Collections.IDictionary> interface reference returned by <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>.</span></span> <span data-ttu-id="b25e6-116">공급자 통계의 모든 카운터는 64비트 수준의 공용 언어 런타임 <xref:System.Int64> 형식(C#과 Visual Basic의 **long**)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-116">All of the counters for provider statistics use the common language runtime <xref:System.Int64> type (**long** in C# and Visual Basic), which is 64 bits wide.</span></span> <span data-ttu-id="b25e6-117">**int64.MaxValue** 필드에서 정의한 **int64** 데이터 형식의 최댓값은 ((2^63)-1))입니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-117">The maximum value of the **int64** data type, as defined by the **int64.MaxValue** field, is ((2^63)-1)).</span></span> <span data-ttu-id="b25e6-118">카운터 값이 최댓값에 도달하면 더 이상 정확한 것으로 간주하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-118">When the values for the counters reach this maximum value, they should no longer be considered accurate.</span></span> <span data-ttu-id="b25e6-119">즉, **int64.MaxValue**-1((2^63)-2)는 사실상 모든 통계의 최대 유효 값입니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-119">This means that **int64.MaxValue**-1((2^63)-2) is effectively the greatest valid value for any statistic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b25e6-120">반환된 통계의 번호, 이름 및 순서가 나중에 변경될 수 있으므로 사전을 사용하여 공급자 통계를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-120">A dictionary is used for returning provider statistics because the number, names and order of the returned statistics may change in the future.</span></span> <span data-ttu-id="b25e6-121">애플리케이션이 사전에 있는 특정 값을 사용하면 안 되며, 값이 있는지 여부를 확인하고 적절하게 분기해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-121">Applications should not rely on a specific value being found in the dictionary, but should instead check whether the value is there and branch accordingly.</span></span>  
  
 <span data-ttu-id="b25e6-122">다음 표에서는 현재 사용 가능한 통계 값에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-122">The following table describes the current statistical values available.</span></span> <span data-ttu-id="b25e6-123">개별 값의 키 이름은 Microsoft .NET Framework의 국가별 버전에서 지역화되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-123">Note that the key names for the individual values are not localized across regional versions of the Microsoft .NET Framework.</span></span>  
  
|<span data-ttu-id="b25e6-124">키 이름</span><span class="sxs-lookup"><span data-stu-id="b25e6-124">Key Name</span></span>|<span data-ttu-id="b25e6-125">설명</span><span class="sxs-lookup"><span data-stu-id="b25e6-125">Description</span></span>|  
|--------------|-----------------|  
|`BuffersReceived`|<span data-ttu-id="b25e6-126">애플리케이션에서 공급자 사용을 시작하고 통계를 사용하도록 설정한 후 공급자가 SQL Server에서 받은 TDS(Tabular Data Stream) 패킷의 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-126">Returns the number of tabular data stream (TDS) packets received by the provider from SQL Server after the application has started using the provider and has enabled statistics.</span></span>|  
|`BuffersSent`|<span data-ttu-id="b25e6-127">통계를 사용하도록 설정한 후 공급자가 SQL Server에 보낸 TDS 패킷 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-127">Returns the number of TDS packets sent to SQL Server by the provider after statistics have been enabled.</span></span> <span data-ttu-id="b25e6-128">긴 명령에는 여러 버퍼가 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-128">Large commands can require multiple buffers.</span></span> <span data-ttu-id="b25e6-129">예를 들어 서버에 긴 명령이 전송되고 6개의 패킷이 필요한 경우 `ServerRoundtrips`가 1씩 증가하고 `BuffersSent`가 6씩 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-129">For example, if a large command is sent to the server and it requires six packets, `ServerRoundtrips` is incremented by one and `BuffersSent` is incremented by six.</span></span>|  
|`BytesReceived`|<span data-ttu-id="b25e6-130">애플리케이션에서 공급자 사용을 시작하고 통계를 사용하도록 설정한 후 공급자가 SQL Server에서 받은 TDS 패킷의 데이터 바이트 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-130">Returns the number of bytes of data in the TDS packets received by the provider from SQL Server once the application has started using the provider and has enabled statistics.</span></span>|  
|`BytesSent`|<span data-ttu-id="b25e6-131">애플리케이션에서 공급자 사용을 시작하고 통계를 사용하도록 설정한 후 SQL Server로 보낸 TDS 패킷의 데이터 바이트 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-131">Returns the number of bytes of data sent to SQL Server in TDS packets after the application has started using the provider and has enabled statistics.</span></span>|  
|`ConnectionTime`|<span data-ttu-id="b25e6-132">통계가 활성화된 후 연결이 열려 있던 시간(밀리초 단위)입니다(연결을 열기 전에 통계를 활성화한 경우에는 총 연결 시간).</span><span class="sxs-lookup"><span data-stu-id="b25e6-132">The amount of time (in milliseconds) that the connection has been opened after statistics have been enabled (total connection time if statistics were enabled before opening the connection).</span></span>|  
|`CursorOpens`|<span data-ttu-id="b25e6-133">애플리케이션에서 공급자 사용을 시작하고 통계를 사용하도록 설정한 후 연결을 통해 커서를 연 횟수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-133">Returns the number of times a cursor was open through the connection once the application has started using the provider and has enabled statistics.</span></span><br /><br /> <span data-ttu-id="b25e6-134">SELECT 문이 반환하는 읽기 전용/전달 전용 결과는 커서로 간주되지 않으므로 이 카운터에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-134">Note that read-only/forward-only results returned by SELECT statements are not considered cursors and thus do not affect this counter.</span></span>|  
|`ExecutionTime`|<span data-ttu-id="b25e6-135">통계가 활성화된 후 서버의 응답을 기다린 시간과 공급자 자체에서 코드를 실행하는 데 걸린 시간을 포함하여 공급자에서 처리에 소요된 누적 시간(밀리초 단위)을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-135">Returns the cumulative amount of time (in milliseconds) that the provider has spent processing once statistics have been enabled, including the time spent waiting for replies from the server as well as the time spent executing code in the provider itself.</span></span><br /><br /> <span data-ttu-id="b25e6-136">타이밍 코드를 포함하는 클래스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-136">The classes that include timing code are:</span></span><br /><br /> <span data-ttu-id="b25e6-137">SqlConnection</span><span class="sxs-lookup"><span data-stu-id="b25e6-137">SqlConnection</span></span><br /><br /> <span data-ttu-id="b25e6-138">SqlCommand</span><span class="sxs-lookup"><span data-stu-id="b25e6-138">SqlCommand</span></span><br /><br /> <span data-ttu-id="b25e6-139">SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="b25e6-139">SqlDataReader</span></span><br /><br /> <span data-ttu-id="b25e6-140">SqlDataAdapter</span><span class="sxs-lookup"><span data-stu-id="b25e6-140">SqlDataAdapter</span></span><br /><br /> <span data-ttu-id="b25e6-141">SqlTransaction</span><span class="sxs-lookup"><span data-stu-id="b25e6-141">SqlTransaction</span></span><br /><br /> <span data-ttu-id="b25e6-142">SqlCommandBuilder</span><span class="sxs-lookup"><span data-stu-id="b25e6-142">SqlCommandBuilder</span></span><br /><br /> <span data-ttu-id="b25e6-143">성능이 중요한 멤버를 가능한 한 작게 유지하기 위해 다음 멤버는 시간이 제한되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-143">To keep performance-critical members as small as possible, the following members are not timed:</span></span><br /><br /> <span data-ttu-id="b25e6-144">SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="b25e6-144">SqlDataReader</span></span><br /><br /> <span data-ttu-id="b25e6-145">this[] 연산자(모두 오버로드)</span><span class="sxs-lookup"><span data-stu-id="b25e6-145">this[] operator (all overloads)</span></span><br /><br /> <span data-ttu-id="b25e6-146">GetBoolean</span><span class="sxs-lookup"><span data-stu-id="b25e6-146">GetBoolean</span></span><br /><br /> <span data-ttu-id="b25e6-147">GetChar</span><span class="sxs-lookup"><span data-stu-id="b25e6-147">GetChar</span></span><br /><br /> <span data-ttu-id="b25e6-148">GetDateTime</span><span class="sxs-lookup"><span data-stu-id="b25e6-148">GetDateTime</span></span><br /><br /> <span data-ttu-id="b25e6-149">GetDecimal</span><span class="sxs-lookup"><span data-stu-id="b25e6-149">GetDecimal</span></span><br /><br /> <span data-ttu-id="b25e6-150">GetDouble</span><span class="sxs-lookup"><span data-stu-id="b25e6-150">GetDouble</span></span><br /><br /> <span data-ttu-id="b25e6-151">GetFloat</span><span class="sxs-lookup"><span data-stu-id="b25e6-151">GetFloat</span></span><br /><br /> <span data-ttu-id="b25e6-152">GetGuid</span><span class="sxs-lookup"><span data-stu-id="b25e6-152">GetGuid</span></span><br /><br /> <span data-ttu-id="b25e6-153">GetInt16</span><span class="sxs-lookup"><span data-stu-id="b25e6-153">GetInt16</span></span><br /><br /> <span data-ttu-id="b25e6-154">GetInt32</span><span class="sxs-lookup"><span data-stu-id="b25e6-154">GetInt32</span></span><br /><br /> <span data-ttu-id="b25e6-155">GetInt64</span><span class="sxs-lookup"><span data-stu-id="b25e6-155">GetInt64</span></span><br /><br /> <span data-ttu-id="b25e6-156">GetName</span><span class="sxs-lookup"><span data-stu-id="b25e6-156">GetName</span></span><br /><br /> <span data-ttu-id="b25e6-157">GetOrdinal</span><span class="sxs-lookup"><span data-stu-id="b25e6-157">GetOrdinal</span></span><br /><br /> <span data-ttu-id="b25e6-158">GetSqlBinary</span><span class="sxs-lookup"><span data-stu-id="b25e6-158">GetSqlBinary</span></span><br /><br /> <span data-ttu-id="b25e6-159">GetSqlBoolean</span><span class="sxs-lookup"><span data-stu-id="b25e6-159">GetSqlBoolean</span></span><br /><br /> <span data-ttu-id="b25e6-160">GetSqlByte</span><span class="sxs-lookup"><span data-stu-id="b25e6-160">GetSqlByte</span></span><br /><br /> <span data-ttu-id="b25e6-161">GetSqlDateTime</span><span class="sxs-lookup"><span data-stu-id="b25e6-161">GetSqlDateTime</span></span><br /><br /> <span data-ttu-id="b25e6-162">GetSqlDecimal</span><span class="sxs-lookup"><span data-stu-id="b25e6-162">GetSqlDecimal</span></span><br /><br /> <span data-ttu-id="b25e6-163">GetSqlDouble</span><span class="sxs-lookup"><span data-stu-id="b25e6-163">GetSqlDouble</span></span><br /><br /> <span data-ttu-id="b25e6-164">GetSqlGuid</span><span class="sxs-lookup"><span data-stu-id="b25e6-164">GetSqlGuid</span></span><br /><br /> <span data-ttu-id="b25e6-165">GetSqlInt16</span><span class="sxs-lookup"><span data-stu-id="b25e6-165">GetSqlInt16</span></span><br /><br /> <span data-ttu-id="b25e6-166">GetSqlInt32</span><span class="sxs-lookup"><span data-stu-id="b25e6-166">GetSqlInt32</span></span><br /><br /> <span data-ttu-id="b25e6-167">GetSqlInt64</span><span class="sxs-lookup"><span data-stu-id="b25e6-167">GetSqlInt64</span></span><br /><br /> <span data-ttu-id="b25e6-168">GetSqlMoney</span><span class="sxs-lookup"><span data-stu-id="b25e6-168">GetSqlMoney</span></span><br /><br /> <span data-ttu-id="b25e6-169">GetSqlSingle</span><span class="sxs-lookup"><span data-stu-id="b25e6-169">GetSqlSingle</span></span><br /><br /> <span data-ttu-id="b25e6-170">GetSqlString</span><span class="sxs-lookup"><span data-stu-id="b25e6-170">GetSqlString</span></span><br /><br /> <span data-ttu-id="b25e6-171">GetString</span><span class="sxs-lookup"><span data-stu-id="b25e6-171">GetString</span></span><br /><br /> <span data-ttu-id="b25e6-172">IsDBNull</span><span class="sxs-lookup"><span data-stu-id="b25e6-172">IsDBNull</span></span>|  
|`IduCount`|<span data-ttu-id="b25e6-173">애플리케이션에서 공급자 사용을 시작하고 통계를 사용하도록 설정한 후 연결을 통해 실행된 INSERT, DELETE 및 UPDATE 문의 총 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-173">Returns the total number of INSERT, DELETE, and UPDATE statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`IduRows`|<span data-ttu-id="b25e6-174">애플리케이션에서 공급자 사용을 시작하고 통계를 사용하도록 설정한 후 연결을 통해 실행된 INSERT, DELETE 및 UPDATE 문의 영향을 받은 행의 총 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-174">Returns the total number of rows affected by INSERT, DELETE, and UPDATE statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`NetworkServerTime`|<span data-ttu-id="b25e6-175">애플리케이션에서 공급자 사용을 시작하고 통계를 활성화한 후 공급자에서 서버의 응답을 기다리는 데 소요된 누적 시간(밀리초 단위)의 양을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-175">Returns the cumulative amount of time (in milliseconds) that the provider spent waiting for replies from the server once the application has started using the provider and has enabled statistics.</span></span>|  
|`PreparedExecs`|<span data-ttu-id="b25e6-176">애플리케이션에서 공급자 사용을 시작하고 통계를 사용하도록 설정한 후 연결을 통해 실행된 준비된 명령의 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-176">Returns the number of prepared commands executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`Prepares`|<span data-ttu-id="b25e6-177">애플리케이션에서 공급자 사용을 시작하고 통계를 사용하도록 설정한 후 연결을 통해 준비된 문의 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-177">Returns the number of statements prepared through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`SelectCount`|<span data-ttu-id="b25e6-178">애플리케이션에서 공급자 사용을 시작하고 통계를 사용하도록 설정한 후 연결을 통해 실행된 SELECT 문의 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-178">Returns the number of SELECT statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="b25e6-179">여기에는 커서에서 행을 검색하는 FETCH 문이 포함되며 <xref:System.Data.SqlClient.SqlDataReader>의 끝에 도달하면 SELECT 문 수가 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-179">This includes FETCH statements to retrieve rows from cursors, and the count for SELECT statements is updated when the end of a <xref:System.Data.SqlClient.SqlDataReader> is reached.</span></span>|  
|`SelectRows`|<span data-ttu-id="b25e6-180">애플리케이션에서 공급자 사용을 시작하고 통계를 사용하도록 설정한 후에 선택된 행 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-180">Returns the number of rows selected once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="b25e6-181">이 카운터는 호출자가 실제로 사용하지 않은 행을 포함하여 SQL 문에서 생성된 모든 행을 반영합니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-181">This counter reflects all the rows generated by SQL statements, even those that were not actually consumed by the caller.</span></span> <span data-ttu-id="b25e6-182">예를 들어 전체 결과 집합을 읽기 전에 데이터 판독기를 닫으면 개수에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-182">For example, closing a data reader before reading the entire result set would not affect the count.</span></span> <span data-ttu-id="b25e6-183">여기에는 FETCH 문을 통해 커서에서 검색된 행이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-183">This includes the rows retrieved from cursors through FETCH statements.</span></span>|  
|`ServerRoundtrips`|<span data-ttu-id="b25e6-184">애플리케이션에서 공급자 사용을 시작하고 통계를 사용하도록 설정한 후 연결이 서버에 명령을 보내고 응답을 받은 횟수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-184">Returns the number of times the connection sent commands to the server and got a reply back once the application has started using the provider and has enabled statistics.</span></span>|  
|`SumResultSets`|<span data-ttu-id="b25e6-185">애플리케이션에서 공급자 사용을 시작하고 통계를 사용하도록 설정한 후 사용된 결과 집합의 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-185">Returns the number of result sets that have been used once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="b25e6-186">예를 들어 클라이언트에 반환되는 모든 결과 집합이 여기에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-186">For example this would include any result set returned to the client.</span></span> <span data-ttu-id="b25e6-187">커서의 경우 각 페치 또는 블록 페치 작업은 독립적인 결과 집합으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-187">For cursors, each fetch or block-fetch operation is considered an independent result set.</span></span>|  
|`Transactions`|<span data-ttu-id="b25e6-188">애플리케이션에서 공급자 사용을 시작하고 통계를 사용하도록 설정한 후 시작된 사용자 트랜잭션의 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-188">Returns the number of user transactions started once the application has started using the provider and has enabled statistics, including rollbacks.</span></span> <span data-ttu-id="b25e6-189">자동 커밋을 사용하여 연결을 실행하는 경우 각 명령은 트랜잭션으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-189">If a connection is running with auto commit on, each command is considered a transaction.</span></span><br /><br /> <span data-ttu-id="b25e6-190">이 카운터는 나중에 트랜잭션이 커밋되거나 롤백되는지 여부에 관계없이 BEGIN TRAN 문이 실행되는 즉시 트랜잭션 수를 증가시킵니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-190">This counter increments the transaction count as soon as a BEGIN TRAN statement is executed, regardless of whether the transaction is committed or rolled back later.</span></span>|  
|`UnpreparedExecs`|<span data-ttu-id="b25e6-191">애플리케이션에서 공급자 사용을 시작하고 통계를 사용하도록 설정한 후 연결을 통해 실행된 준비되지 않은 문의 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-191">Returns the number of unprepared statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
  
### <a name="retrieving-a-value"></a><span data-ttu-id="b25e6-192">값 검색</span><span class="sxs-lookup"><span data-stu-id="b25e6-192">Retrieving a Value</span></span>  

 <span data-ttu-id="b25e6-193">다음 콘솔 애플리케이션에서는 연결에서 통계를 사용하도록 설정하고, 4개의 개별 통계 값을 검색하고, 콘솔 창에 기록하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-193">The following console application shows how to enable statistics on a connection, retrieve four individual statistic values, and write them out to the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b25e6-194">다음 예제에서는 SQL Server에 포함된 샘플 **AdventureWorks** 데이터베이스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-194">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="b25e6-195">샘플 코드에 제공된 연결 문자열은 데이터베이스가 로컬 컴퓨터에 설치되어 있고 사용 가능한 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-195">The connection string provided in the sample code assumes the database is installed and available on the local computer.</span></span> <span data-ttu-id="b25e6-196">사용자 환경에 필요한 경우 연결 문자열을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-196">Modify the connection string as necessary for your environment.</span></span>  
  
```vb  
Option Strict On  
  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  
  Sub Main()  
    Dim connectionString As String = GetConnectionString()  
  
    Using awConnection As New SqlConnection(connectionString)  
      ' StatisticsEnabled is False by default.  
      ' It must be set to True to start the
      ' statistic collection process.  
      awConnection.StatisticsEnabled = True  
  
      Dim productSQL As String = "SELECT * FROM Production.Product"  
      Dim productAdapter As _  
          New SqlDataAdapter(productSQL, awConnection)  
  
      Dim awDataSet As New DataSet()  
  
      awConnection.Open()  
  
      productAdapter.Fill(awDataSet, "ProductTable")  
  
      ' Retrieve the current statistics as  
      ' a collection of values at this point  
      ' and time.  
      Dim currentStatistics As IDictionary = _  
          awConnection.RetrieveStatistics()  
  
      Console.WriteLine("Total Counters: " & _  
          currentStatistics.Count.ToString())  
      Console.WriteLine()  
  
      ' Retrieve a few individual values  
      ' related to the previous command.  
      Dim bytesReceived As Long = _  
          CLng(currentStatistics.Item("BytesReceived"))  
      Dim bytesSent As Long = _  
          CLng(currentStatistics.Item("BytesSent"))  
      Dim selectCount As Long = _  
          CLng(currentStatistics.Item("SelectCount"))  
      Dim selectRows As Long = _  
          CLng(currentStatistics.Item("SelectRows"))  
  
      Console.WriteLine("BytesReceived: " & bytesReceived.ToString())  
      Console.WriteLine("BytesSent: " & bytesSent.ToString())  
      Console.WriteLine("SelectCount: " & selectCount.ToString())  
      Console.WriteLine("SelectRows: " & selectRows.ToString())  
  
      Console.WriteLine()  
      Console.WriteLine("Press any key to continue")  
      Console.ReadLine()  
    End Using  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrieve it from a configuration file.  
    Return "Data Source=localhost;Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace CS_Stats_Console_GetValue  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =
          new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
          awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
          currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        // Retrieve a few individual values  
        // related to the previous command.  
        long bytesReceived =  
            (long) currentStatistics["BytesReceived"];  
        long bytesSent =  
            (long) currentStatistics["BytesSent"];  
        long selectCount =  
            (long) currentStatistics["SelectCount"];  
        long selectRows =  
            (long) currentStatistics["SelectRows"];  
  
        Console.WriteLine("BytesReceived: " +  
            bytesReceived.ToString());  
        Console.WriteLine("BytesSent: " +  
            bytesSent.ToString());  
        Console.WriteLine("SelectCount: " +  
            selectCount.ToString());  
        Console.WriteLine("SelectRows: " +  
            selectRows.ToString());  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrieve it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
### <a name="retrieving-all-values"></a><span data-ttu-id="b25e6-197">모든 값 검색</span><span class="sxs-lookup"><span data-stu-id="b25e6-197">Retrieving All Values</span></span>  

 <span data-ttu-id="b25e6-198">다음 콘솔 애플리케이션에서는 연결에서 통계를 사용하도록 설정하고, 열거자를 사용하여 사용 가능한 모든 통계 값을 검색하고, 콘솔 창에 쓰는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-198">The following console application shows how to enable statistics on a connection, retrieve all available statistic values using the enumerator, and write them to the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b25e6-199">다음 예제에서는 SQL Server에 포함된 샘플 **AdventureWorks** 데이터베이스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-199">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="b25e6-200">샘플 코드에 제공된 연결 문자열은 데이터베이스가 로컬 컴퓨터에 설치되어 있고 사용 가능한 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-200">The connection string provided in the sample code assumes the database is installed and available on the local computer.</span></span> <span data-ttu-id="b25e6-201">사용자 환경에 필요한 경우 연결 문자열을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="b25e6-201">Modify the connection string as necessary for your environment.</span></span>  
  
```vb  
Option Strict On  
  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  Sub Main()  
    Dim connectionString As String = GetConnectionString()  
  
    Using awConnection As New SqlConnection(connectionString)  
      ' StatisticsEnabled is False by default.  
      ' It must be set to True to start the
      ' statistic collection process.  
      awConnection.StatisticsEnabled = True  
  
      Dim productSQL As String = "SELECT * FROM Production.Product"  
      Dim productAdapter As _  
          New SqlDataAdapter(productSQL, awConnection)  
  
      Dim awDataSet As New DataSet()  
  
      awConnection.Open()  
  
      productAdapter.Fill(awDataSet, "ProductTable")  
  
      ' Retrieve the current statistics as  
      ' a collection of values at this point  
      ' and time.  
      Dim currentStatistics As IDictionary = _  
          awConnection.RetrieveStatistics()  
  
      Console.WriteLine("Total Counters: " & _  
          currentStatistics.Count.ToString())  
      Console.WriteLine()  
  
      Console.WriteLine("Key Name and Value")  
  
      ' Note the entries are unsorted.  
      For Each entry As DictionaryEntry In currentStatistics  
        Console.WriteLine(entry.Key.ToString() & _  
            ": " & entry.Value.ToString())  
      Next  
  
      Console.WriteLine()  
      Console.WriteLine("Press any key to continue")  
      Console.ReadLine()  
    End Using  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrieve it from a configuration file.  
    Return "Data Source=localhost;Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Text;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace CS_Stats_Console_GetAll  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =  
            new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
            awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
            currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        Console.WriteLine("Key Name and Value");  
  
        // Note the entries are unsorted.  
        foreach (DictionaryEntry entry in currentStatistics)  
        {  
          Console.WriteLine(entry.Key.ToString() +  
              ": " + entry.Value.ToString());  
        }  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrieve it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="b25e6-202">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b25e6-202">See also</span></span>

- [<span data-ttu-id="b25e6-203">SQL Server 및 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b25e6-203">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="b25e6-204">ADO.NET 개요</span><span class="sxs-lookup"><span data-stu-id="b25e6-204">ADO.NET Overview</span></span>](../ado-net-overview.md)
