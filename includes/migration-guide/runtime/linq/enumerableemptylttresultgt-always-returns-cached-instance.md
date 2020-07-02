---
ms.openlocfilehash: 9131c91b34f4c24653dea37ea39af6be6e072287
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620336"
---
### <a name="enumerableemptylttresultgt-always-returns-cached-instance"></a><span data-ttu-id="6fc78-101">Enumerable.Empty&lt;TResult&gt;가 항상 캐시된 인스턴스를 반환</span><span class="sxs-lookup"><span data-stu-id="6fc78-101">Enumerable.Empty&lt;TResult&gt; always returns cached instance</span></span>

#### <a name="details"></a><span data-ttu-id="6fc78-102">설명</span><span class="sxs-lookup"><span data-stu-id="6fc78-102">Details</span></span>

<span data-ttu-id="6fc78-103">.NET Framework 4.5부터 <xref:System.Linq.Enumerable.Empty%60%601>는 항상 캐시된 내부 인스턴스 <xref:System.Collections.Generic.IEnumerable%601>를 반환합니다. 이전에는 <xref:System.Linq.Enumerable.Empty%60%601>이 API를 호출할 때 빈 <xref:System.Collections.Generic.IEnumerable%601>을 캐시했으며, 이 말은 즉 <xref:System.Linq.Enumerable.Empty%60%601>가 신속하게 동시에 호출된 일부 조건에서 다른 형식의 인스턴스가 다른 호출에 대해 API로 반환되었다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6fc78-103">Beginning in .NET Framework 4.5, <xref:System.Linq.Enumerable.Empty%60%601> always returns a cached internal instance <xref:System.Collections.Generic.IEnumerable%601>.Previously, <xref:System.Linq.Enumerable.Empty%60%601> would cache an empty <xref:System.Collections.Generic.IEnumerable%601> at the time the API was called, meaning that in some conditions in which <xref:System.Linq.Enumerable.Empty%60%601> was called rapidly and concurrently, different instances of the type could be returned for different calls to the API.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6fc78-104">제안 해결 방법</span><span class="sxs-lookup"><span data-stu-id="6fc78-104">Suggestion</span></span>

<span data-ttu-id="6fc78-105">이전 동작이 명확하지 않았으므로 코드가 종속될 가능성이 작습니다.</span><span class="sxs-lookup"><span data-stu-id="6fc78-105">Because the previous behavior was non-deterministic, code is unlikely to depend on it.</span></span> <span data-ttu-id="6fc78-106">그러나 빈 열거형은 비교되고 때로는 같지 않은 것으로 예상되는 드문 경우에는, <xref:System.Linq.Enumerable.Empty%60%601>를 사용하는 대신 명시적인 빈 배열을 만들어야 합니다(<code>new T[0]</code>).</span><span class="sxs-lookup"><span data-stu-id="6fc78-106">However, in the unlikely case that empty enumerables are being compared and expected to sometimes be unequal, explicit empty arrays should be created (<code>new T[0]</code>) instead of using <xref:System.Linq.Enumerable.Empty%60%601>.</span></span>

| <span data-ttu-id="6fc78-107">이름</span><span class="sxs-lookup"><span data-stu-id="6fc78-107">Name</span></span>    | <span data-ttu-id="6fc78-108">값</span><span class="sxs-lookup"><span data-stu-id="6fc78-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6fc78-109">Scope</span><span class="sxs-lookup"><span data-stu-id="6fc78-109">Scope</span></span>   |<span data-ttu-id="6fc78-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="6fc78-110">Edge</span></span>|
|<span data-ttu-id="6fc78-111">버전</span><span class="sxs-lookup"><span data-stu-id="6fc78-111">Version</span></span>|<span data-ttu-id="6fc78-112">4.5</span><span class="sxs-lookup"><span data-stu-id="6fc78-112">4.5</span></span>|
|<span data-ttu-id="6fc78-113">형식</span><span class="sxs-lookup"><span data-stu-id="6fc78-113">Type</span></span>|<span data-ttu-id="6fc78-114">런타임</span><span class="sxs-lookup"><span data-stu-id="6fc78-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6fc78-115">영향을 받는 API</span><span class="sxs-lookup"><span data-stu-id="6fc78-115">Affected APIs</span></span>

-<xref:System.Linq.Enumerable.Empty%60%601?displayProperty=nameWithType></li></ul>|
