---
title: CREATEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 489828cf-a335-4449-9360-b0d92eec5481
ms.openlocfilehash: c2a57116f56abf4db3caabcfe3acd0d8afbcf4eb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201059"
---
# <a name="createref-entity-sql"></a><span data-ttu-id="3c740-102">CREATEREF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="3c740-102">CREATEREF (Entity SQL)</span></span>

<span data-ttu-id="3c740-103">entityset의 엔터티에 대한 참조를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="3c740-103">Fabricates references to an entity in an entityset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c740-104">구문</span><span class="sxs-lookup"><span data-stu-id="3c740-104">Syntax</span></span>  
  
```sql  
CreateRef(entityset_identifier, row_typed_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="3c740-105">인수</span><span class="sxs-lookup"><span data-stu-id="3c740-105">Arguments</span></span>  

 `entityset_identifier`  
 <span data-ttu-id="3c740-106">문자열 리터럴이 아니라 entityset 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="3c740-106">The entityset identifier, not a string literal.</span></span>  
  
 `row_typed_expression`  
 <span data-ttu-id="3c740-107">엔터티 형식의 키 속성에 해당하는 행 형식의 식입니다.</span><span class="sxs-lookup"><span data-stu-id="3c740-107">A row-typed expression that corresponds to the key properties of the entity type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c740-108">설명</span><span class="sxs-lookup"><span data-stu-id="3c740-108">Remarks</span></span>  

 <span data-ttu-id="3c740-109">`row_typed_expression` 은 엔터티의 키 유형과 구조적으로 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c740-109">`row_typed_expression` must be structurally equivalent to the key type for the entity.</span></span> <span data-ttu-id="3c740-110">다시 말해서, 필드의 개수와 형식 및 배열 순서가 엔터티 키와 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c740-110">That is, it must have the same number and types of fields in the same order as the entity keys.</span></span>  
  
 <span data-ttu-id="3c740-111">아래 예제에서 Order와 BadOrder는 모두 Order 형식의 entityset이며, Id는 Order의 단일 키 속성인 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c740-111">In the example below, Orders and BadOrders are both entitysets of type Order, and Id is assumed to be the single key property of Order.</span></span> <span data-ttu-id="3c740-112">예제에서는 BadOrder의 엔터티에 대한 참조를 생성하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3c740-112">The example illustrates how we may produce a reference to an entity in BadOrders.</span></span> <span data-ttu-id="3c740-113">이 참조는 현수 참조일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c740-113">Note that the reference may be dangling.</span></span>  <span data-ttu-id="3c740-114">다시 말해서, 참조가 특정 엔터티를 실제로 나타내지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c740-114">That is, the reference may not actually identify a specific entity.</span></span> <span data-ttu-id="3c740-115">이런 경우 해당 참조에 대해 `DEREF` 작업을 수행하면 null이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c740-115">In those cases, a `DEREF` operation on that reference returns a null.</span></span>  
  
```sql  
SELECT CreateRef(LOB.BadOrders, row(o.Id))
FROM LOB.Orders AS o
```  
  
## <a name="example"></a><span data-ttu-id="3c740-116">예제</span><span class="sxs-lookup"><span data-stu-id="3c740-116">Example</span></span>  

 <span data-ttu-id="3c740-117">다음 Entity SQL 쿼리는 CREATEREF 연산자를 사용하여 엔터티 집합 내의 엔터티에 대한 참조를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="3c740-117">The following Entity SQL query uses the CREATEREF operator to fabricate references to an entity in an entity set.</span></span> <span data-ttu-id="3c740-118">쿼리는 AdventureWorks Sales 모델을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c740-118">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="3c740-119">이 쿼리를 컴파일하고 실행하려면 다음 단계를 수행하세요.</span><span class="sxs-lookup"><span data-stu-id="3c740-119">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="3c740-120">[How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)의 절차를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="3c740-120">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="3c740-121">다음 쿼리를 `ExecuteStructuralTypeQuery` 메서드에 인수로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="3c740-121">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#CREATEREF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#createref)]  
  
## <a name="see-also"></a><span data-ttu-id="3c740-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3c740-122">See also</span></span>

- [<span data-ttu-id="3c740-123">엔터티 SQL 참조</span><span class="sxs-lookup"><span data-stu-id="3c740-123">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="3c740-124">DEREF</span><span class="sxs-lookup"><span data-stu-id="3c740-124">DEREF</span></span>](deref-entity-sql.md)
- [<span data-ttu-id="3c740-125">KEY</span><span class="sxs-lookup"><span data-stu-id="3c740-125">KEY</span></span>](key-entity-sql.md)
- [<span data-ttu-id="3c740-126">행위자</span><span class="sxs-lookup"><span data-stu-id="3c740-126">REF</span></span>](ref-entity-sql.md)
