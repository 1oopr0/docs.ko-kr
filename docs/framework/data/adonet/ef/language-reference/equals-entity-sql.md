---
title: = (같음) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
ms.openlocfilehash: 31299670d9f47ed7672b980a3415b8d214463b8e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148089"
---
# <a name="-equals-entity-sql"></a><span data-ttu-id="a8a5d-102">= (같음) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="a8a5d-102">= (Equals) (Entity SQL)</span></span>

<span data-ttu-id="a8a5d-103">두 식이 같은지 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="a8a5d-103">Compares the equality of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8a5d-104">구문</span><span class="sxs-lookup"><span data-stu-id="a8a5d-104">Syntax</span></span>  
  
```sql  
expression = expression  
-- or
expression == expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="a8a5d-105">인수</span><span class="sxs-lookup"><span data-stu-id="a8a5d-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="a8a5d-106">모든 유효한 식입니다.</span><span class="sxs-lookup"><span data-stu-id="a8a5d-106">Any valid expression.</span></span> <span data-ttu-id="a8a5d-107">두 식은 모두 암시적으로 변환 가능한 데이터 형식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8a5d-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="a8a5d-108">결과 형식</span><span class="sxs-lookup"><span data-stu-id="a8a5d-108">Result Types</span></span>  

 <span data-ttu-id="a8a5d-109">왼쪽 식의 값이 오른쪽 식의 값과 같으면`true` 이고, 그렇지 않으면 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="a8a5d-109">`true` if the left expression is equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8a5d-110">설명</span><span class="sxs-lookup"><span data-stu-id="a8a5d-110">Remarks</span></span>  

 <span data-ttu-id="a8a5d-111">== 연산자는 = 연산자와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="a8a5d-111">The == operator is equivalent to =.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8a5d-112">예제</span><span class="sxs-lookup"><span data-stu-id="a8a5d-112">Example</span></span>  

 <span data-ttu-id="a8a5d-113">다음 Entity SQL 쿼리에서는 = 비교 연산자를 사용하여 두 식이 같은지 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="a8a5d-113">The following Entity SQL query uses = comparison operator to compare the equality of two expressions.</span></span> <span data-ttu-id="a8a5d-114">쿼리는 AdventureWorks Sales 모델을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8a5d-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="a8a5d-115">이 쿼리를 컴파일하고 실행하려면 다음 단계를 수행하세요.</span><span class="sxs-lookup"><span data-stu-id="a8a5d-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="a8a5d-116">[How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)의 절차를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="a8a5d-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="a8a5d-117">다음 쿼리를 `ExecuteStructuralTypeQuery` 메서드에 인수로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="a8a5d-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#equals)]  
  
## <a name="see-also"></a><span data-ttu-id="a8a5d-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a8a5d-118">See also</span></span>

- [<span data-ttu-id="a8a5d-119">엔터티 SQL 참조</span><span class="sxs-lookup"><span data-stu-id="a8a5d-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
