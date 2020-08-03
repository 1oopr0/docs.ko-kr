---
title: Join 작업(C#)
description: 두 데이터 원본의 조인은 개체와 데이터 원본 간에 특성을 공유하는 개체를 연결합니다. C#의 LINQ 프레임 워크에서의 조인 메서드에 대해 알아봅니다.
ms.date: 07/20/2015
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
no-loc:
- Join
- GroupJoin
ms.openlocfilehash: 1b453f1752edf0cc126f8e27dbdd9e91ad9143f3
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165693"
---
# <a name="no-locjoin-operations-c"></a><span data-ttu-id="4b8c0-104">Join 작업(C#)</span><span class="sxs-lookup"><span data-stu-id="4b8c0-104">Join Operations (C#)</span></span>

<span data-ttu-id="4b8c0-105">두 데이터 소스를 *조인*하는 것은 한 데이터 소스의 개체를 공통 특성을 공유하는 다른 데이터 소스의 개체와 연결하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4b8c0-105">A *join* of two data sources is the association of objects in one data source with objects that share a common attribute in another data source.</span></span>  
  
 <span data-ttu-id="4b8c0-106">서로 간의 관계를 직접 적용할 수 없는 데이터 원본을 대상으로 하는 쿼리에서는 Join이 중요한 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="4b8c0-106">Joining is an important operation in queries that target data sources whose relationships to each other cannot be followed directly.</span></span> <span data-ttu-id="4b8c0-107">개체 지향 프로그래밍에서 데이터 소스 간의 관계를 직접 적용할 수 없다는 것은 모델링되지 않은 개체 간에 상관 관계가 있음을 의미할 수 있습니다(예: 단방향 관계에서 반대 방향을 사용).</span><span class="sxs-lookup"><span data-stu-id="4b8c0-107">In object-oriented programming, this could mean a correlation between objects that is not modeled, such as the backwards direction of a one-way relationship.</span></span> <span data-ttu-id="4b8c0-108">단방향 관계의 예로는 Customer 클래스가 City 형식 속성을 포함하는데 City 클래스는 Customer 개체의 컬렉션인 속성을 포함하지 않는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b8c0-108">An example of a one-way relationship is a Customer class that has a property of type City, but the City class does not have a property that is a collection of Customer objects.</span></span> <span data-ttu-id="4b8c0-109">City 개체 목록이 있는 경우 각 구/군/시의 모든 고객을 찾으려면 조인 작업을 사용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b8c0-109">If you have a list of City objects and you want to find all the customers in each city, you could use a join operation to find them.</span></span>  
  
 <span data-ttu-id="4b8c0-110">LINQ 프레임워크에 제공되는 조인 메서드는 <xref:System.Linq.Enumerable.Join%2A> 및 <xref:System.Linq.Enumerable.GroupJoin%2A>입니다.</span><span class="sxs-lookup"><span data-stu-id="4b8c0-110">The join methods provided in the LINQ framework are <xref:System.Linq.Enumerable.Join%2A> and <xref:System.Linq.Enumerable.GroupJoin%2A>.</span></span> <span data-ttu-id="4b8c0-111">이러한 메서드는 키가 같은지 여부에 따라 두 데이터 소스의 일치 여부를 확인하는 조인인 동등 조인을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="4b8c0-111">These methods perform equijoins, or joins that match two data sources based on equality of their keys.</span></span> <span data-ttu-id="4b8c0-112">비교를 위해 Transact-SQL에서는 '같음'이 아닌 '보다 작음' 연산자와 같은 조인 연산자를 지원합니다. 관계형 데이터베이스 용어에서 <xref:System.Linq.Enumerable.Join%2A>은 내부 조인을 구현합니다. 내부 조인은 다른 데이터 집합에 일치하는 항목이 있는 개체만 반환하는 유형의 조인입니다.</span><span class="sxs-lookup"><span data-stu-id="4b8c0-112">(For comparison, Transact-SQL supports join operators other than 'equals', for example the 'less than' operator.) In relational database terms, <xref:System.Linq.Enumerable.Join%2A> implements an inner join, a type of join in which only those objects that have a match in the other data set are returned.</span></span> <span data-ttu-id="4b8c0-113"><xref:System.Linq.Enumerable.GroupJoin%2A> 메서드에는 관계형 데이터베이스 측면에 직접 상응하는 기능이 없지만 내부 조인 및 왼쪽 우선 외부 조인의 상위 집합을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="4b8c0-113">The <xref:System.Linq.Enumerable.GroupJoin%2A> method has no direct equivalent in relational database terms, but it implements a superset of inner joins and left outer joins.</span></span> <span data-ttu-id="4b8c0-114">왼쪽 우선 외부 조인은 다른 데이터 소스에 서로 관련된 요소가 없더라도 첫 번째(왼쪽) 데이터 소스의 각 요소를 반환하는 조인입니다.</span><span class="sxs-lookup"><span data-stu-id="4b8c0-114">A left outer join is a join that returns each element of the first (left) data source, even if it has no correlated elements in the other data source.</span></span>  
  
 <span data-ttu-id="4b8c0-115">다음 그림에서는 내부 조인 또는 왼쪽 우선 외부 조인에 포함된 두 집합 및 해당 집합 내의 요소를 개념적으로 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="4b8c0-115">The following illustration shows a conceptual view of two sets and the elements within those sets that are included in either an inner join or a left outer join.</span></span>  
  
 ![내부/외부를 보여주는 두 개의 겹치는 원](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a><span data-ttu-id="4b8c0-117">메서드</span><span class="sxs-lookup"><span data-stu-id="4b8c0-117">Methods</span></span>  
  
|<span data-ttu-id="4b8c0-118">메서드 이름</span><span class="sxs-lookup"><span data-stu-id="4b8c0-118">Method Name</span></span>|<span data-ttu-id="4b8c0-119">설명</span><span class="sxs-lookup"><span data-stu-id="4b8c0-119">Description</span></span>|<span data-ttu-id="4b8c0-120">C# 쿼리 식 구문</span><span class="sxs-lookup"><span data-stu-id="4b8c0-120">C# Query Expression Syntax</span></span>|<span data-ttu-id="4b8c0-121">추가 정보</span><span class="sxs-lookup"><span data-stu-id="4b8c0-121">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Join|<span data-ttu-id="4b8c0-122">키 선택기 함수를 기준으로 두 시퀀스를 Join한 다음 값 쌍을 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="4b8c0-122">Joins two sequences based on key selector functions and extracts pairs of values.</span></span>|`join … in … on … equals …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin|<span data-ttu-id="4b8c0-123">키 선택기 함수를 기준으로 두 시퀀스를 Join한 다음 결과로 생성된 일치 항목을 요소마다 그룹화합니다.</span><span class="sxs-lookup"><span data-stu-id="4b8c0-123">Joins two sequences based on key selector functions and groups the resulting matches for each element.</span></span>|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="4b8c0-124">쿼리 식 구문 예제</span><span class="sxs-lookup"><span data-stu-id="4b8c0-124">Query expression syntax examples</span></span>
  
### Join  
  
<span data-ttu-id="4b8c0-125">다음 예제에서는 `join … in … on … equals …` 절을 사용하여 특정 값을 기준으로 두 시퀀스를 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="4b8c0-125">The following example uses the `join … in … on … equals …` clause to join two sequences based on specific value:</span></span>
  
[!code-csharp[Join](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQJoinOperation/CS/JoinOperation.cs#Join)]  

### GroupJoin  

<span data-ttu-id="4b8c0-126">다음 예제에서는 `join … in … on … equals … into …` 절을 사용하여 특정 값을 기준으로 두 시퀀스를 조인하고 각 요소에 대해 결과 일치 항목을 그룹화합니다.</span><span class="sxs-lookup"><span data-stu-id="4b8c0-126">The following example uses the `join … in … on … equals … into …` clause to join two sequences based on specific value and groups the resulting matches for each element:</span></span>
  
[!code-csharp[GroupJoin](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQJoinOperation/CS/JoinOperation.cs#GroupJoin)]  
  
## <a name="see-also"></a><span data-ttu-id="4b8c0-127">참조</span><span class="sxs-lookup"><span data-stu-id="4b8c0-127">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="4b8c0-128">표준 쿼리 연산자 개요(C#)</span><span class="sxs-lookup"><span data-stu-id="4b8c0-128">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="4b8c0-129">익명 형식</span><span class="sxs-lookup"><span data-stu-id="4b8c0-129">Anonymous Types</span></span>](../../classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="4b8c0-130">Join 및 교차곱 쿼리 작성</span><span class="sxs-lookup"><span data-stu-id="4b8c0-130">Formulate Joins and Cross-Product Queries</span></span>](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [<span data-ttu-id="4b8c0-131">join 절</span><span class="sxs-lookup"><span data-stu-id="4b8c0-131">join clause</span></span>](../../../language-reference/keywords/join-clause.md)
- [<span data-ttu-id="4b8c0-132">Join 복합 키를 사용하여</span><span class="sxs-lookup"><span data-stu-id="4b8c0-132">Join by using composite keys</span></span>](../../../linq/join-by-using-composite-keys.md)
- [<span data-ttu-id="4b8c0-133">서로 다른 파일의 콘텐츠를 조인하는 방법(LINQ)(C#)</span><span class="sxs-lookup"><span data-stu-id="4b8c0-133">How to join content from dissimilar files (LINQ) (C#)</span></span>](./how-to-join-content-from-dissimilar-files-linq.md)
- [<span data-ttu-id="4b8c0-134">Join 절 결과를 서순대로 정렬</span><span class="sxs-lookup"><span data-stu-id="4b8c0-134">Order the results of a join clause</span></span>](../../../linq/order-the-results-of-a-join-clause.md)
- [<span data-ttu-id="4b8c0-135">사용자 지정 조인 작업 수행</span><span class="sxs-lookup"><span data-stu-id="4b8c0-135">Perform custom join operations</span></span>](../../../linq/perform-custom-join-operations.md)
- [<span data-ttu-id="4b8c0-136">그룹화 조인 수행</span><span class="sxs-lookup"><span data-stu-id="4b8c0-136">Perform grouped joins</span></span>](../../../linq/perform-grouped-joins.md)
- [<span data-ttu-id="4b8c0-137">내부 조인 수행</span><span class="sxs-lookup"><span data-stu-id="4b8c0-137">Perform inner joins</span></span>](../../../linq/perform-inner-joins.md)
- [<span data-ttu-id="4b8c0-138">왼쪽 우선 외부 조인 수행</span><span class="sxs-lookup"><span data-stu-id="4b8c0-138">Perform left outer joins</span></span>](../../../linq/perform-left-outer-joins.md)
- [<span data-ttu-id="4b8c0-139">여러 소스로 개체 컬렉션을 채우는 방법(LINQ)(C#)</span><span class="sxs-lookup"><span data-stu-id="4b8c0-139">How to populate object collections from multiple sources (LINQ) (C#)</span></span>](./how-to-populate-object-collections-from-multiple-sources-linq.md)
