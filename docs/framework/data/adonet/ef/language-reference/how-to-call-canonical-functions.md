---
title: '방법: 호출 정식 함수'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b3d84873-7403-4957-8e20-b4ae39f50214
ms.openlocfilehash: acfbdbaf21fe1d454b68dfef5bf4f88d8020ea65
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204452"
---
# <a name="how-to-call-canonical-functions"></a><span data-ttu-id="68ffb-102">방법: 호출 정식 함수</span><span class="sxs-lookup"><span data-stu-id="68ffb-102">How to: Call Canonical Functions</span></span>

<span data-ttu-id="68ffb-103"><xref:System.Data.Objects.EntityFunctions> 클래스에는 LINQ to Entities 쿼리에 사용할 정식 함수를 노출하는 메서드가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68ffb-103">The <xref:System.Data.Objects.EntityFunctions> class contains methods that expose canonical functions to use in LINQ to Entities queries.</span></span> <span data-ttu-id="68ffb-104">정식 함수에 대한 자세한 내용은 [정식 함수](canonical-functions.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="68ffb-104">For information about canonical functions, see [Canonical Functions](canonical-functions.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="68ffb-105"><xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> 클래스의 <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> 및 <xref:System.Data.Objects.EntityFunctions> 메서드에는 해당하는 정식 함수가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="68ffb-105">The <xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> and <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> methods in the <xref:System.Data.Objects.EntityFunctions> class do not have canonical function equivalents.</span></span>  
  
 <span data-ttu-id="68ffb-106">값 집합에 대한 계산을 수행하고 단일 값을 반환하는 정식 함수(집계 정식 함수라고도 함)는 직접 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68ffb-106">Canonical functions that perform a calculation on a set of values and return a single value (also known as aggregate canonical functions) can be directly invoked.</span></span> <span data-ttu-id="68ffb-107">기타 정식 함수는 LINQ to Entities 쿼리의 일부로만 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68ffb-107">Other canonical functions can only be called as part of a LINQ to Entities query.</span></span> <span data-ttu-id="68ffb-108">집계 함수를 직접 호출하려면 <xref:System.Data.Objects.ObjectQuery%601>를 함수로 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="68ffb-108">To call an aggregate function directly, you must pass an <xref:System.Data.Objects.ObjectQuery%601> to the function.</span></span> <span data-ttu-id="68ffb-109">자세한 내용은 아래 두 번째 예제를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="68ffb-109">For more information, see the second example below.</span></span>  
  
 <span data-ttu-id="68ffb-110">LINQ to Entities 쿼리에서 CLR(공용 언어 런타임) 메서드를 사용하여 일부 정식 함수를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68ffb-110">You can call some canonical functions by using common language runtime (CLR) methods in LINQ to Entities queries.</span></span> <span data-ttu-id="68ffb-111">정식 함수에 매핑되는 CLR 메서드 목록은 [정식 함수 매핑을 위한 Clr 메서드](clr-method-to-canonical-function-mapping.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="68ffb-111">For a list of CLR methods that map to canonical functions, see [CLR Method to Canonical Function Mapping](clr-method-to-canonical-function-mapping.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="68ffb-112">예제</span><span class="sxs-lookup"><span data-stu-id="68ffb-112">Example</span></span>  

 <span data-ttu-id="68ffb-113">다음 예에서는 [AdventureWorks Sales 모델](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="68ffb-113">The following example uses the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span> <span data-ttu-id="68ffb-114">이 예제에서는 <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> 메서드를 사용하여 `SellEndDate`와 `SellStartDate`의 차이가 365일 미만인 제품을 모두 반환하는 LINQ to Entities 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="68ffb-114">The example executes a LINQ to Entities query that uses the <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> method to return all products for which the difference between `SellEndDate` and `SellStartDate` is less than 365 days:</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#1)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="68ffb-115">예제</span><span class="sxs-lookup"><span data-stu-id="68ffb-115">Example</span></span>  

 <span data-ttu-id="68ffb-116">다음 예에서는 [AdventureWorks Sales 모델](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="68ffb-116">The following example uses the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span> <span data-ttu-id="68ffb-117">이 예제에서는 집계 <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> 메서드를 직접 호출하여 `SalesOrderHeader` 부분합의 표준 편차를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="68ffb-117">The example calls the aggregate <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> method directly to return the standard deviation of `SalesOrderHeader` subtotals.</span></span> <span data-ttu-id="68ffb-118"><xref:System.Data.Objects.ObjectQuery%601>는 LINQ to Entities 쿼리에 포함되지 않고 호출되도록 지정하는 함수로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="68ffb-118">Note that an <xref:System.Data.Objects.ObjectQuery%601> is passed to the function, which allows it to be called without being part of a LINQ to Entities query.</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#2)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="68ffb-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="68ffb-119">See also</span></span>

- [<span data-ttu-id="68ffb-120">LINQ to Entities 쿼리에서 함수 호출</span><span class="sxs-lookup"><span data-stu-id="68ffb-120">Calling Functions in LINQ to Entities Queries</span></span>](calling-functions-in-linq-to-entities-queries.md)
- [<span data-ttu-id="68ffb-121">LINQ to Entities에서 쿼리</span><span class="sxs-lookup"><span data-stu-id="68ffb-121">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
