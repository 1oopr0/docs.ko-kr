---
title: 집합 작업
ms.date: 07/20/2015
ms.assetid: 2b06e822-e030-438f-9db7-ee402bd3a706
ms.openlocfilehash: b6ff14794343ae7623ee38894cef02cfc0a2a597
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406822"
---
# <a name="set-operations-visual-basic"></a><span data-ttu-id="ae639-102">Set 작업 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae639-102">Set Operations (Visual Basic)</span></span>

<span data-ttu-id="ae639-103">LINQ의 집합 작업은 동일 컬렉션이나 별개 컬렉션(또는 집합)에 동등한 요소가 있는지 여부에 따라 결과 집합을 생성하는 쿼리 작업을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="ae639-103">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>

<span data-ttu-id="ae639-104">다음 섹션에는 집합 작업을 수행하는 표준 쿼리 연산자 메서드가 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae639-104">The standard query operator methods that perform set operations are listed in the following section.</span></span>

## <a name="methods"></a><span data-ttu-id="ae639-105">메서드</span><span class="sxs-lookup"><span data-stu-id="ae639-105">Methods</span></span>

|<span data-ttu-id="ae639-106">메서드 이름</span><span class="sxs-lookup"><span data-stu-id="ae639-106">Method Name</span></span>|<span data-ttu-id="ae639-107">설명</span><span class="sxs-lookup"><span data-stu-id="ae639-107">Description</span></span>|<span data-ttu-id="ae639-108">Visual Basic 쿼리 식 구문</span><span class="sxs-lookup"><span data-stu-id="ae639-108">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="ae639-109">추가 정보</span><span class="sxs-lookup"><span data-stu-id="ae639-109">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="ae639-110">Distinct</span><span class="sxs-lookup"><span data-stu-id="ae639-110">Distinct</span></span>|<span data-ttu-id="ae639-111">컬렉션에서 중복 값을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="ae639-111">Removes duplicate values from a collection.</span></span>|`Distinct`|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|
|<span data-ttu-id="ae639-112">Except</span><span class="sxs-lookup"><span data-stu-id="ae639-112">Except</span></span>|<span data-ttu-id="ae639-113">두 번째 컬렉션에 표시되지 않는 한 컬렉션의 요소를 의미하는 차집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ae639-113">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="ae639-114">해당 사항 없음</span><span class="sxs-lookup"><span data-stu-id="ae639-114">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|
|<span data-ttu-id="ae639-115">Intersect</span><span class="sxs-lookup"><span data-stu-id="ae639-115">Intersect</span></span>|<span data-ttu-id="ae639-116">두 컬렉션에 각각 표시되는 요소를 의미하는 교집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ae639-116">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="ae639-117">해당 사항 없음</span><span class="sxs-lookup"><span data-stu-id="ae639-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|
|<span data-ttu-id="ae639-118">Union</span><span class="sxs-lookup"><span data-stu-id="ae639-118">Union</span></span>|<span data-ttu-id="ae639-119">두 컬렉션 중 하나에 표시되는 고유한 요소를 의미하는 합집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ae639-119">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="ae639-120">해당 사항 없음</span><span class="sxs-lookup"><span data-stu-id="ae639-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|

## <a name="comparison-of-set-operations"></a><span data-ttu-id="ae639-121">집합 작업 비교</span><span class="sxs-lookup"><span data-stu-id="ae639-121">Comparison of Set Operations</span></span>

### <a name="distinct"></a><span data-ttu-id="ae639-122">Distinct</span><span class="sxs-lookup"><span data-stu-id="ae639-122">Distinct</span></span>

<span data-ttu-id="ae639-123">다음 그림에서는 문자 시퀀스에 대한 <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> 메서드의 동작을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ae639-123">The following illustration depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> method on a sequence of characters.</span></span> <span data-ttu-id="ae639-124">반환된 시퀀스에는 입력 시퀀스의 고유한 요소가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae639-124">The returned sequence contains the unique elements from the input sequence.</span></span>

![Distinct()의 동작을 보여주는 그래픽](./media/set-operations/distinct-method-behavior.png)

### <a name="except"></a><span data-ttu-id="ae639-126">Except</span><span class="sxs-lookup"><span data-stu-id="ae639-126">Except</span></span>

<span data-ttu-id="ae639-127">다음 그림에서는 <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>의 동작을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ae639-127">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ae639-128">반환된 시퀀스에는 두 번째 입력 시퀀스에 없는 첫 번째 입력 시퀀스의 요소만 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae639-128">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>

<span data-ttu-id="ae639-129">![Except&#40;&#41;의 동작을 보여 주는 그래픽.](./media/set-operations/except-behavior-graphic.png "Except의 동작을 보여 줍니다.")</span><span class="sxs-lookup"><span data-stu-id="ae639-129">![Graphic showing the action of Except&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Shows the behavior of Except.")</span></span>

### <a name="intersect"></a><span data-ttu-id="ae639-130">Intersect</span><span class="sxs-lookup"><span data-stu-id="ae639-130">Intersect</span></span>

<span data-ttu-id="ae639-131">다음 그림에서는 <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>의 동작을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ae639-131">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ae639-132">반환된 시퀀스에는 입력 시퀀스 둘 다에 공통적으로 있는 요소가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae639-132">The returned sequence contains the elements that are common to both of the input sequences.</span></span>

![두 시퀀스의 교집합을 보여주는 그래픽](./media/set-operations/intersection-two-sequences.png)

### <a name="union"></a><span data-ttu-id="ae639-134">Union</span><span class="sxs-lookup"><span data-stu-id="ae639-134">Union</span></span>

<span data-ttu-id="ae639-135">다음 그림은 두 개의 문자 시퀀스에 대한 합집합을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ae639-135">The following illustration depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="ae639-136">반환된 시퀀스에는 두 입력 시퀀스의 고유한 요소가 모두 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae639-136">The returned sequence contains the unique elements from both input sequences.</span></span>

![두 시퀀스의 결합을 보여주는 그래픽](./media/set-operations/union-operation-two-sequences.png)

## <a name="query-expression-syntax-example"></a><span data-ttu-id="ae639-138">쿼리 식 구문 예제</span><span class="sxs-lookup"><span data-stu-id="ae639-138">Query Expression Syntax Example</span></span>

<span data-ttu-id="ae639-139">다음 예제에서는 LINQ 쿼리에 절을 사용 하 여 `Distinct` 정수 목록에서 고유 번호를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae639-139">The following example uses the `Distinct` clause in a LINQ query to return the unique numbers from a list of integers.</span></span>

[!code-vb[CsLINQSetOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQSetOps/VB/setops.vb#1)]

## <a name="see-also"></a><span data-ttu-id="ae639-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ae639-140">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="ae639-141">표준 쿼리 연산자 개요(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae639-141">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="ae639-142">Distinct 절</span><span class="sxs-lookup"><span data-stu-id="ae639-142">Distinct Clause</span></span>](../../../language-reference/queries/distinct-clause.md)
- [<span data-ttu-id="ae639-143">방법: 문자열 컬렉션 결합 및 비교 (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae639-143">How to: Combine and Compare String Collections (LINQ) (Visual Basic)</span></span>](how-to-combine-and-compare-string-collections-linq.md)
- [<span data-ttu-id="ae639-144">방법: 두 목록 간의 차집합을 설정 찾기 (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae639-144">How to: Find the Set Difference Between Two Lists (LINQ) (Visual Basic)</span></span>](how-to-find-the-set-difference-between-two-lists-linq.md)
