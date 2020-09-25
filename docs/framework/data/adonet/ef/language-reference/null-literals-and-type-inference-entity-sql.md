---
title: Null 리터럴 및 형식 유추(Entity SQL)
ms.date: 03/30/2017
ms.assetid: edd56afb-af1b-4e7d-b210-cb8998143426
ms.openlocfilehash: 5797c9f55b1a1c89cc27787af6f9ad7bfffc5767
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185069"
---
# <a name="null-literals-and-type-inference-entity-sql"></a><span data-ttu-id="83a00-102">Null 리터럴 및 형식 유추(Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="83a00-102">Null Literals and Type Inference (Entity SQL)</span></span>

<span data-ttu-id="83a00-103">null 리터럴은 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 형식 시스템의 모든 형식과 호환됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a00-103">Null literals are compatible with any type in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] type system.</span></span> <span data-ttu-id="83a00-104">하지만 null 리터럴의 형식을 올바르게 유추할 수 있도록 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]에서는 null 리터럴을 사용할 수 있는 위치에 대한 특정 제약 조건을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="83a00-104">However, for the type of a null literal to be inferred correctly, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] imposes certain constraints on where a null literal can be used.</span></span>  
  
## <a name="typed-nulls"></a><span data-ttu-id="83a00-105">형식화된 null</span><span class="sxs-lookup"><span data-stu-id="83a00-105">Typed Nulls</span></span>  

 <span data-ttu-id="83a00-106">형식화된 null은 어디서나 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a00-106">Typed nulls can be used anywhere.</span></span> <span data-ttu-id="83a00-107">형식이 알려져 있으므로 형식화된 null에는 형식 유추가 필요 없습니다.</span><span class="sxs-lookup"><span data-stu-id="83a00-107">Type inference is not required for typed nulls because the type is known.</span></span> <span data-ttu-id="83a00-108">예를 들어, 다음 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 생성자를 사용하여 Int16 형식의 null을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a00-108">For example, you can construct a null of type Int16 with the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] construct:</span></span>  
  
 `(cast(null as Int16))`  
  
## <a name="free-floating-null-literals"></a><span data-ttu-id="83a00-109">자유 부동 null 리터럴</span><span class="sxs-lookup"><span data-stu-id="83a00-109">Free-Floating Null Literals</span></span>  

 <span data-ttu-id="83a00-110">다음 컨텍스트에서 자유 부동 null 리터럴을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a00-110">Free-floating null literals can be used in the following contexts:</span></span>  
  
- <span data-ttu-id="83a00-111">CAST 또는 TREAT 식의 인수로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="83a00-111">As an argument to a CAST or TREAT expression.</span></span> <span data-ttu-id="83a00-112">형식화된 null 식을 생성하기 위한 권장 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="83a00-112">This is the recommended way to produce a typed null expression.</span></span>  
  
- <span data-ttu-id="83a00-113">메서드 또는 함수의 인수로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="83a00-113">As an argument to a method or a function.</span></span> <span data-ttu-id="83a00-114">표준 오버로드 규칙이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a00-114">Standard overload rules apply.</span></span>  
  
- <span data-ttu-id="83a00-115">+, -, / 등과 같은 산술 식 인수 중 하나로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="83a00-115">As one of the arguments to an arithmetic expression such as +, -, or /.</span></span> <span data-ttu-id="83a00-116">이외의 인수는 null 리터럴일 수 없습니다. 그렇지 않으면 형식을 유추할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="83a00-116">The other arguments cannot be null literals, otherwise type inference is not possible.</span></span>  
  
- <span data-ttu-id="83a00-117">AND, OR, NOT 등과 같이 논리 식 인수 중 하나로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="83a00-117">As any of the arguments to a logical expression (AND, OR, or NOT).</span></span> <span data-ttu-id="83a00-118">모든 인수는 부울 형식으로 알려져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a00-118">All the arguments are known to be of type Boolean.</span></span>  
  
- <span data-ttu-id="83a00-119">IS NULL 또는 IS NOT NULL 식의 인수로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="83a00-119">As the argument to an IS NULL or IS NOT NULL expression.</span></span>  
  
- <span data-ttu-id="83a00-120">LIKE 식의 인수 중 하나 이상으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="83a00-120">As one or more of the arguments to a LIKE expression.</span></span> <span data-ttu-id="83a00-121">모든 인수는 문자열이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a00-121">All arguments are expected to be strings.</span></span>  
  
- <span data-ttu-id="83a00-122">명명된 형식 생성자의 인수 중 하나 이상으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="83a00-122">As one or more of the arguments to a named-type constructor.</span></span>  
  
- <span data-ttu-id="83a00-123">multiset 생성자의 인수 중 하나 이상으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="83a00-123">As one or more of the arguments to a multiset constructor.</span></span> <span data-ttu-id="83a00-124">multiset 생성자의 인수 중 하나 이상은 null 리터럴이 아닌 식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a00-124">At least one argument to the multiset constructor must be an expression that is not a null literal.</span></span>  
  
- <span data-ttu-id="83a00-125">CASE 식에서 THEN 또는 ELSE 식 중 하나 이상으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="83a00-125">As one or more of the THEN or ELSE expressions in a CASE expression.</span></span> <span data-ttu-id="83a00-126">CASE 식에서 THEN 또는 ELSE 식 중 하나 이상은 null 리터럴이 아닌 다른 식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a00-126">At least one of the THEN or ELSE expressions in the CASE expression must be an expression other than a null literal.</span></span>  
  
 <span data-ttu-id="83a00-127">다른 시나리오에서는 자유 부동 null 리터럴을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="83a00-127">Free-floating null literals cannot be used in other scenarios.</span></span> <span data-ttu-id="83a00-128">예를 들어, 자유 부동 null 리터럴을 행 생성자의 인수로서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="83a00-128">For example,  they cannot be used as arguments to a row constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83a00-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="83a00-129">See also</span></span>

- [<span data-ttu-id="83a00-130">Entity SQL 개요</span><span class="sxs-lookup"><span data-stu-id="83a00-130">Entity SQL Overview</span></span>](entity-sql-overview.md)
