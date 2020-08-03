---
title: 데이터 필터링(C#)
description: 선택이라고도 하는 필터링은 조건에 따라 결과를 제한합니다. C#에서 필터링을 수행하는 LINQ의 표준 쿼리 연산자 메서드에 대해 알아봅니다.
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: f9f6d691da73b566e5135f6692c87ba3a8978005
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103933"
---
# <a name="filtering-data-c"></a><span data-ttu-id="07c6c-104">데이터 필터링(C#)</span><span class="sxs-lookup"><span data-stu-id="07c6c-104">Filtering Data (C#)</span></span>
<span data-ttu-id="07c6c-105">필터링은 지정된 조건을 충족하는 요소만 포함하도록 결과 집합을 제한하는 작업을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="07c6c-105">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="07c6c-106">필터링은 선택이라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="07c6c-106">It is also known as selection.</span></span>  
  
 <span data-ttu-id="07c6c-107">다음 그림에서는 문자 시퀀스를 필터링한 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="07c6c-107">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="07c6c-108">필터링 작업에 대한 조건자는 문자가 'A'가 되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="07c6c-108">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 ![LINQ 필터링 작업을 보여주는 다이어그램](./media/filtering-data/linq-filter-operation.png)  
  
 <span data-ttu-id="07c6c-110">선택을 수행하는 표준 쿼리 연산자 메서드는 다음 섹션에 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="07c6c-110">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="07c6c-111">메서드</span><span class="sxs-lookup"><span data-stu-id="07c6c-111">Methods</span></span>  
  
|<span data-ttu-id="07c6c-112">메서드 이름</span><span class="sxs-lookup"><span data-stu-id="07c6c-112">Method Name</span></span>|<span data-ttu-id="07c6c-113">설명</span><span class="sxs-lookup"><span data-stu-id="07c6c-113">Description</span></span>|<span data-ttu-id="07c6c-114">C# 쿼리 식 구문</span><span class="sxs-lookup"><span data-stu-id="07c6c-114">C# Query Expression Syntax</span></span>|<span data-ttu-id="07c6c-115">추가 정보</span><span class="sxs-lookup"><span data-stu-id="07c6c-115">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="07c6c-116">OfType</span><span class="sxs-lookup"><span data-stu-id="07c6c-116">OfType</span></span>|<span data-ttu-id="07c6c-117">지정된 형식으로 캐스트할 수 있는지 여부에 따라 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="07c6c-117">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="07c6c-118">해당 사항 없음.</span><span class="sxs-lookup"><span data-stu-id="07c6c-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="07c6c-119">Where</span><span class="sxs-lookup"><span data-stu-id="07c6c-119">Where</span></span>|<span data-ttu-id="07c6c-120">조건자 함수를 기반으로 하는 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="07c6c-120">Selects values that are based on a predicate function.</span></span>|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="07c6c-121">쿼리 식 구문 예제</span><span class="sxs-lookup"><span data-stu-id="07c6c-121">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="07c6c-122">다음 예제에서는 `where` 절을 사용하여 배열에서 특정 길이의 문자열을 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="07c6c-122">The following example uses the `where` clause to filter from an array those strings that have a specific length.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            where word.Length == 3  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="07c6c-123">참조</span><span class="sxs-lookup"><span data-stu-id="07c6c-123">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="07c6c-124">표준 쿼리 연산자 개요(C#)</span><span class="sxs-lookup"><span data-stu-id="07c6c-124">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="07c6c-125">where 절</span><span class="sxs-lookup"><span data-stu-id="07c6c-125">where clause</span></span>](../../../language-reference/keywords/where-clause.md)
- [<span data-ttu-id="07c6c-126">런타임에 동적으로 조건자 필터 지정</span><span class="sxs-lookup"><span data-stu-id="07c6c-126">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="07c6c-127">리플렉션을 사용하여 어셈블리의 메타데이터를 쿼리하는 방법(LINQ)(C#)</span><span class="sxs-lookup"><span data-stu-id="07c6c-127">How to query an assembly's metadata with Reflection (LINQ) (C#)</span></span>](./how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [<span data-ttu-id="07c6c-128">지정된 특성 또는 이름을 사용하여 파일을 쿼리하는 방법(C#)</span><span class="sxs-lookup"><span data-stu-id="07c6c-128">How to query for files with a specified attribute or name (C#)</span></span>](./how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [<span data-ttu-id="07c6c-129">단어 또는 필드에 따라 텍스트 데이터를 정렬하거나 필터링하는 방법(LINQ)(C#)</span><span class="sxs-lookup"><span data-stu-id="07c6c-129">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
