---
title: 원격 및 로컬 실행
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ee50e943-9349-4c84-ab1c-c35d3ada1a9c
ms.openlocfilehash: c99e726902192fc8324e77441b80aa4519c55ddc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91196951"
---
# <a name="remote-vs-local-execution"></a><span data-ttu-id="4cf3e-102">원격 및 로컬 실행</span><span class="sxs-lookup"><span data-stu-id="4cf3e-102">Remote vs. Local Execution</span></span>

<span data-ttu-id="4cf3e-103">쿼리를 원격으로 실행할지(즉, 데이터베이스 엔진이 데이터베이스에 대해 쿼리 실행) 아니면 로컬로 실행할지(즉, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]이 로컬 캐시에 대해 쿼리 실행) 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4cf3e-103">You can decide to execute your queries either remotely (that is, the database engine executes the query against the database) or locally ([!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] executes the query against a local cache).</span></span>  
  
## <a name="remote-execution"></a><span data-ttu-id="4cf3e-104">원격 실행</span><span class="sxs-lookup"><span data-stu-id="4cf3e-104">Remote Execution</span></span>  

 <span data-ttu-id="4cf3e-105">다음과 같은 쿼리를 고려해 보세요.</span><span class="sxs-lookup"><span data-stu-id="4cf3e-105">Consider the following query:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#7)]
 [!code-vb[DLinqQueryConcepts#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#7)]  
  
 <span data-ttu-id="4cf3e-106">데이터베이스에 수천 개의 주문 행이 있는 경우 작은 하위 집합을 처리하기 위해 이러한 행을 모두 검색하고 싶지 않을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4cf3e-106">If your database has thousands of rows of orders, you do not want to retrieve them all to process a small subset.</span></span> <span data-ttu-id="4cf3e-107">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]에서 <xref:System.Data.Linq.EntitySet%601> 클래스는 <xref:System.Linq.IQueryable> 인터페이스를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="4cf3e-107">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Data.Linq.EntitySet%601> class implements the <xref:System.Linq.IQueryable> interface.</span></span> <span data-ttu-id="4cf3e-108">이 방법을 사용하면 이러한 쿼리를 원격으로 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4cf3e-108">This approach makes sure that such queries can be executed remotely.</span></span> <span data-ttu-id="4cf3e-109">이 기술의 두 가지 주요 이점은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4cf3e-109">Two major benefits flow from this technique:</span></span>  
  
- <span data-ttu-id="4cf3e-110">불필요한 데이터가 검색되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4cf3e-110">Unnecessary data is not retrieved.</span></span>  
  
- <span data-ttu-id="4cf3e-111">데이터베이스 엔진이 실행하는 쿼리는 일반적으로 데이터베이스 인덱스로 인해 더 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="4cf3e-111">A query executed by the database engine is often more efficient because of the database indexes.</span></span>  
  
## <a name="local-execution"></a><span data-ttu-id="4cf3e-112">로컬 실행</span><span class="sxs-lookup"><span data-stu-id="4cf3e-112">Local Execution</span></span>  

 <span data-ttu-id="4cf3e-113">다른 상황에서는 관련 엔터티의 전체 집합을 로컬 캐시에 포함하려고 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4cf3e-113">In other situations, you might want to have the complete set of related entities in the local cache.</span></span> <span data-ttu-id="4cf3e-114">이를 위해 <xref:System.Data.Linq.EntitySet%601>은 <xref:System.Data.Linq.EntitySet%601.Load%2A>의 모든 멤버를 명시적으로 로드하기 위한 <xref:System.Data.Linq.EntitySet%601> 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4cf3e-114">For this purpose, <xref:System.Data.Linq.EntitySet%601> provides the <xref:System.Data.Linq.EntitySet%601.Load%2A> method to explicitly load all the members of the <xref:System.Data.Linq.EntitySet%601>.</span></span>  
  
 <span data-ttu-id="4cf3e-115"><xref:System.Data.Linq.EntitySet%601>이 이미 로드된 경우 후속 쿼리는 로컬로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="4cf3e-115">If an <xref:System.Data.Linq.EntitySet%601> is already loaded, subsequent queries are executed locally.</span></span> <span data-ttu-id="4cf3e-116">이 방법은 다음과 같은 두 가지 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4cf3e-116">This approach helps in two ways:</span></span>  
  
- <span data-ttu-id="4cf3e-117">전체 집합을 로컬로 사용하거나 여러 번 사용해야 할 경우 원격 쿼리 및 연관된 대기 시간을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4cf3e-117">If the complete set must be used locally or multiple times, you can avoid remote queries and associated latencies.</span></span>  
  
- <span data-ttu-id="4cf3e-118">엔터티를 완전한 엔터티로 serialize할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4cf3e-118">The entity can be serialized as a complete entity.</span></span>  
  
 <span data-ttu-id="4cf3e-119">다음 코드 조각에서는 로컬 실행을 수행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4cf3e-119">The following code fragment illustrates how local execution can be obtained:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#8)]
 [!code-vb[DLinqQueryConcepts#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#8)]  
  
## <a name="comparison"></a><span data-ttu-id="4cf3e-120">비교</span><span class="sxs-lookup"><span data-stu-id="4cf3e-120">Comparison</span></span>  

 <span data-ttu-id="4cf3e-121">이러한 두 기능은 대규모 컬렉션을 위한 원격 실행과 소규모 컬렉션 또는 완전한 컬렉션이 필요한 상황을 위한 로컬 실행이라는 옵션이 결합된 강력한 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4cf3e-121">These two capabilities provide a powerful combination of options: remote execution for large collections and local execution for small collections or where the complete collection is needed.</span></span> <span data-ttu-id="4cf3e-122"><xref:System.Linq.IQueryable>을 통해 원격 실행을 구현하고 메모리 내 <xref:System.Collections.Generic.IEnumerable%601> 컬렉션에 대해 로컬 실행을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="4cf3e-122">You implement remote execution through <xref:System.Linq.IQueryable>, and local execution against an in-memory <xref:System.Collections.Generic.IEnumerable%601> collection.</span></span> <span data-ttu-id="4cf3e-123">로컬 실행을 강제로 적용 하려면 (즉, <xref:System.Collections.Generic.IEnumerable%601> ) [제네릭 IEnumerable로 형식 변환](convert-a-type-to-a-generic-ienumerable.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4cf3e-123">To force local execution (that is, <xref:System.Collections.Generic.IEnumerable%601>), see [Convert a Type to a Generic IEnumerable](convert-a-type-to-a-generic-ienumerable.md).</span></span>  
  
### <a name="queries-against-unordered-sets"></a><span data-ttu-id="4cf3e-124">정렬되지 않은 집합에 대한 쿼리</span><span class="sxs-lookup"><span data-stu-id="4cf3e-124">Queries Against Unordered Sets</span></span>  

 <span data-ttu-id="4cf3e-125">을 구현 하는 로컬 컬렉션과 <xref:System.Collections.Generic.List%601> 관계형 데이터베이스의 *순서가* 지정 되지 않은 집합에 대해 실행 되는 원격 쿼리를 제공 하는 컬렉션 간의 중요 한 차이점을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="4cf3e-125">Note the important difference between a local collection that implements <xref:System.Collections.Generic.List%601> and a collection that provides remote queries executed against *unordered sets* in a relational database.</span></span> <span data-ttu-id="4cf3e-126">인덱스 값을 사용하는 메서드와 같은 <xref:System.Collections.Generic.List%601> 메서드에는 목록 의미 체계가 필요한데 이는 일반적으로 정렬되지 않은 집합에 대한 원격 쿼리를 통해 얻을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4cf3e-126"><xref:System.Collections.Generic.List%601> methods such as those that use index values require list semantics, which typically cannot be obtained through a remote query against an unordered set.</span></span> <span data-ttu-id="4cf3e-127">이와 같은 이유 때문에 이러한 메서드는 로컬 실행을 허용하기 위해 <xref:System.Data.Linq.EntitySet%601>을 암시적으로 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="4cf3e-127">For this reason, such methods implicitly load the <xref:System.Data.Linq.EntitySet%601> to allow local execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cf3e-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4cf3e-128">See also</span></span>

- [<span data-ttu-id="4cf3e-129">쿼리 개념</span><span class="sxs-lookup"><span data-stu-id="4cf3e-129">Query Concepts</span></span>](query-concepts.md)
