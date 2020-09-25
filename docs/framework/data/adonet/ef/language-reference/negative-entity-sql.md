---
title: '- 양수 (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 208e54ef-4741-4ec5-89d6-6ff700863cb0
ms.openlocfilehash: 71749dab073fade854c2a494841e3f6b408ebd1d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204413"
---
# <a name="--negative-entity-sql"></a><span data-ttu-id="7ac8a-102">- (부정)(Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="7ac8a-102">- (Negative) (Entity SQL)</span></span>

<span data-ttu-id="7ac8a-103">숫자 식의 음수 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac8a-103">Returns the negative of the value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ac8a-104">구문</span><span class="sxs-lookup"><span data-stu-id="7ac8a-104">Syntax</span></span>  
  
```sql  
- expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="7ac8a-105">인수</span><span class="sxs-lookup"><span data-stu-id="7ac8a-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="7ac8a-106">숫자 데이터 형식의 유효한 식입니다.</span><span class="sxs-lookup"><span data-stu-id="7ac8a-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="7ac8a-107">결과 형식</span><span class="sxs-lookup"><span data-stu-id="7ac8a-107">Result Types</span></span>  

 <span data-ttu-id="7ac8a-108">`expression`의 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="7ac8a-108">The data type of `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ac8a-109">설명</span><span class="sxs-lookup"><span data-stu-id="7ac8a-109">Remarks</span></span>  

 <span data-ttu-id="7ac8a-110">`expression` 이 부호 없는 형식이면 결과 형식은 `expression`의 형식과 가장 밀접하게 관련된 부호 있는 형식이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ac8a-110">If `expression` is an unsigned type, the result type will be the signed type that most closely relates to the type of `expression`.</span></span> <span data-ttu-id="7ac8a-111">`expression` 이 Byte 형식이면 Int16 형식의 값이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ac8a-111">For example, if `expression` is of type Byte, a value of type Int16 will be returned.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ac8a-112">예제</span><span class="sxs-lookup"><span data-stu-id="7ac8a-112">Example</span></span>  

 <span data-ttu-id="7ac8a-113">다음 Entity SQL 쿼리에서는 - 산술 연산자를 사용하여 숫자 식의 음수 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac8a-113">The following Entity SQL query uses the - arithmetic operator to return the negative of the value of a numeric expression.</span></span> <span data-ttu-id="7ac8a-114">쿼리는 AdventureWorks Sales 모델을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac8a-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="7ac8a-115">이 쿼리를 컴파일하고 실행하려면 다음 단계를 수행하세요.</span><span class="sxs-lookup"><span data-stu-id="7ac8a-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="7ac8a-116">[How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)의 절차를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="7ac8a-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="7ac8a-117">다음 쿼리를 `ExecuteStructuralTypeQuery` 메서드에 인수로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac8a-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#NEGATIVE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#negative)]  
  
## <a name="see-also"></a><span data-ttu-id="7ac8a-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ac8a-118">See also</span></span>

- [<span data-ttu-id="7ac8a-119">엔터티 SQL 참조</span><span class="sxs-lookup"><span data-stu-id="7ac8a-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
