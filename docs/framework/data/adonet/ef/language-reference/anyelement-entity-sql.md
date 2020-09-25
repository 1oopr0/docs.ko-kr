---
title: ANYELEMENT(Entity SQL)
ms.date: 03/30/2017
ms.assetid: 475a9ad6-8c8d-4f49-9970-af273e5360f1
ms.openlocfilehash: e060956545ca924fa6fedb80b2f53ff312f307a2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201202"
---
# <a name="anyelement-entity-sql"></a><span data-ttu-id="c72a5-102">ANYELEMENT(Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="c72a5-102">ANYELEMENT (Entity SQL)</span></span>

<span data-ttu-id="c72a5-103">다중값 컬렉션에서 요소를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="c72a5-103">Extracts an element from a multivalued collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c72a5-104">구문</span><span class="sxs-lookup"><span data-stu-id="c72a5-104">Syntax</span></span>  
  
```csharp
ANYELEMENT ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="c72a5-105">인수</span><span class="sxs-lookup"><span data-stu-id="c72a5-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="c72a5-106">요소를 추출할 컬렉션을 반환하는 유효한 쿼리 식입니다.</span><span class="sxs-lookup"><span data-stu-id="c72a5-106">Any valid query expression that returns a collection to extract an element from.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c72a5-107">반환 값</span><span class="sxs-lookup"><span data-stu-id="c72a5-107">Return Value</span></span>  

 <span data-ttu-id="c72a5-108">컬렉션의 단일 요소 또는 임의 요소(컬렉션에 여러 요소가 있는 경우)를 반환하거나 컬렉션이 비어 있는 경우 `null`을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c72a5-108">A single element in the collection or an arbitrary element if the collection has more than one; if the collection is empty, returns `null`.</span></span> <span data-ttu-id="c72a5-109">`collection`가 형식의 컬렉션인 경우 `Collection<T>` `ANYELEMENT(collection)` 는 형식의 인스턴스를 생성 하는 유효한 식입니다 `T` .</span><span class="sxs-lookup"><span data-stu-id="c72a5-109">If `collection` is a collection of type `Collection<T>`, then `ANYELEMENT(collection)` is a valid expression that yields an instance of type `T`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c72a5-110">설명</span><span class="sxs-lookup"><span data-stu-id="c72a5-110">Remarks</span></span>  

 <span data-ttu-id="c72a5-111">ANYELEMENT는 다중값 컬렉션에서 임의의 요소를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="c72a5-111">ANYELEMENT extracts an arbitrary element from a multivalued collection.</span></span> <span data-ttu-id="c72a5-112">예를 들어, 다음 예제에서는 `Customers`집합에서 singleton 요소를 추출하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="c72a5-112">For example, the following example attempts to extract a singleton element from the set `Customers`.</span></span>  
  
```csharp
ANYELEMENT(Customers)  
```  
  
## <a name="example"></a><span data-ttu-id="c72a5-113">예제</span><span class="sxs-lookup"><span data-stu-id="c72a5-113">Example</span></span>  

 <span data-ttu-id="c72a5-114">다음 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 쿼리에서는 ANYELEMENT 연산자를 사용하여 다중값 컬렉션에서 요소를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="c72a5-114">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the ANYELEMENT operator to extract an element from a multivalued collection.</span></span> <span data-ttu-id="c72a5-115">쿼리는 AdventureWorks Sales 모델을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="c72a5-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="c72a5-116">이 쿼리를 컴파일하고 실행하려면 다음 단계를 수행하세요.</span><span class="sxs-lookup"><span data-stu-id="c72a5-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="c72a5-117">[How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)의 절차를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="c72a5-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="c72a5-118">다음 쿼리를 `ExecuteStructuralTypeQuery` 메서드에 인수로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="c72a5-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ANYELEMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#anyelement)]  
  
## <a name="see-also"></a><span data-ttu-id="c72a5-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c72a5-119">See also</span></span>

- [<span data-ttu-id="c72a5-120">엔터티 SQL 참조</span><span class="sxs-lookup"><span data-stu-id="c72a5-120">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="c72a5-121">nullable 구조적 형식</span><span class="sxs-lookup"><span data-stu-id="c72a5-121">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)
