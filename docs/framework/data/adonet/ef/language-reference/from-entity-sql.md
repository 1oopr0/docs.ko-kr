---
title: FROM(Entity SQL)
ms.date: 03/30/2017
ms.assetid: ff3e3048-0d5d-4502-ae5c-9187fcbd0514
ms.openlocfilehash: 8affac82fb1813aa0282540b5dc2f47d42234a1b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148059"
---
# <a name="from-entity-sql"></a><span data-ttu-id="ce499-102">FROM(Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ce499-102">FROM (Entity SQL)</span></span>

<span data-ttu-id="ce499-103">[SELECT](select-entity-sql.md) 문에 사용 되는 컬렉션을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-103">Specifies the collection used in [SELECT](select-entity-sql.md) statements.</span></span>

## <a name="syntax"></a><span data-ttu-id="ce499-104">구문</span><span class="sxs-lookup"><span data-stu-id="ce499-104">Syntax</span></span>

```sql
FROM expression [ ,...n ] AS C
```

## <a name="arguments"></a><span data-ttu-id="ce499-105">인수</span><span class="sxs-lookup"><span data-stu-id="ce499-105">Arguments</span></span>

`expression` \
<span data-ttu-id="ce499-106">`SELECT` 문에서 소스로 사용할 컬렉션을 생성하는 모든 유효한 쿼리 식입니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-106">Any valid query expression that yields a collection to use as a source in a `SELECT` statement.</span></span>

## <a name="remarks"></a><span data-ttu-id="ce499-107">설명</span><span class="sxs-lookup"><span data-stu-id="ce499-107">Remarks</span></span>

<span data-ttu-id="ce499-108">`FROM` 절은 하나 이상의 `FROM` 절 항목이 쉼표로 구분된 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-108">A `FROM` clause is a comma-separated list of one or more `FROM` clause items.</span></span> <span data-ttu-id="ce499-109">`FROM` 절을 사용하여 `SELECT` 문의 소스를 하나 이상 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-109">The `FROM` clause can be used to specify one or more sources for a `SELECT` statement.</span></span> <span data-ttu-id="ce499-110">가장 단순한 형태의 `FROM` 절은 다음 예제와 같이 `SELECT` 문에서 소스로 사용되는 컬렉션 및 별칭을 식별하는 단일 쿼리 식입니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-110">The simplest form of a `FROM` clause is a single query expression that identifies a collection and an alias used as the source in a `SELECT` statement, as illustrated in the following example:</span></span>

`FROM C as c`

## <a name="from-clause-items"></a><span data-ttu-id="ce499-111">FROM 절 항목</span><span class="sxs-lookup"><span data-stu-id="ce499-111">FROM Clause Items</span></span>

<span data-ttu-id="ce499-112">각 `FROM` 절 항목은 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 쿼리의 소스 컬렉션을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-112">Each `FROM` clause item refers to a source collection in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="ce499-113">에서는 단순 `FROM` 절 항목, `FROM` 절 항목 및 `JOIN FROM` 절 항목과 같은 `APPLY FROM` 절 항목의 클래스를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-113">supports the following classes of `FROM` clause items: simple `FROM` clause items, `JOIN FROM` clause items, and `APPLY FROM` clause items.</span></span> <span data-ttu-id="ce499-114">각 `FROM` 절 항목에 대해서는 다음 단원에서 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-114">Each of these `FROM` clause items is described in more detail in the following sections.</span></span>

### <a name="simple-from-clause-item"></a><span data-ttu-id="ce499-115">단순 FROM 절 항목</span><span class="sxs-lookup"><span data-stu-id="ce499-115">Simple FROM Clause Item</span></span>

<span data-ttu-id="ce499-116">가장 단순한 `FROM` 절 항목은 컬렉션 및 별칭을 식별하는 단일 식입니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-116">The simplest `FROM` clause item is a single expression that identifies a collection and an alias.</span></span> <span data-ttu-id="ce499-117">식은 단순히 엔터티 집합이거나 하위 쿼리 또는 컬렉션 형식인 다른 모든 식일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-117">The expression can simply be an entity set, or a subquery, or any other expression that is a collection type.</span></span> <span data-ttu-id="ce499-118">다음은 이에 대한 예입니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-118">The following is an example:</span></span>

```sql
LOB.Customers as c
```

<span data-ttu-id="ce499-119">별칭 지정은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-119">The alias specification is optional.</span></span> <span data-ttu-id="ce499-120">위에서 설명한 FROM 절 항목의 대체 지정은 다음과 같을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-120">An alternate specification of the above from clause item could be the following:</span></span>

```sql
LOB.Customers
```

<span data-ttu-id="ce499-121">별칭이 지정되지 않은 경우 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]에서는 컬렉션 식을 기반으로 별칭을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-121">If no alias is specified, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] attempts to generate an alias based on the collection expression.</span></span>

### <a name="join-from-clause-item"></a><span data-ttu-id="ce499-122">JOIN FROM 절 항목</span><span class="sxs-lookup"><span data-stu-id="ce499-122">JOIN FROM Clause Item</span></span>

<span data-ttu-id="ce499-123">`JOIN FROM` 절 항목은 두 `FROM` 절 항목 간의 조인을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-123">A `JOIN FROM` clause item represents a join between two `FROM` clause items.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="ce499-124">에서는 Cross Join, Inner Join, Left Outer Join, Right Outer Join 및 Full Outer Join을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-124">supports cross joins, inner joins, left and right outer joins, and full outer joins.</span></span> <span data-ttu-id="ce499-125">이러한 모든 조인은 Transact-sql에서 지원 되는 방식과 유사 하 게 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-125">All these joins are supported similar to the way that they are supported in Transact-SQL.</span></span> <span data-ttu-id="ce499-126">Transact-sql에서와 같이에 관련 된 두 `FROM` 절 항목은 `JOIN` 독립적 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-126">As in Transact-SQL, the two `FROM` clause items involved in the `JOIN` must be independent.</span></span> <span data-ttu-id="ce499-127">즉, 상호 관련될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-127">That is, they cannot be correlated.</span></span> <span data-ttu-id="ce499-128">이러한 경우 `CROSS APPLY` 또는 `OUTER APPLY`를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-128">A `CROSS APPLY` or `OUTER APPLY` can be used for these cases.</span></span>

#### <a name="cross-joins"></a><span data-ttu-id="ce499-129">Cross Join</span><span class="sxs-lookup"><span data-stu-id="ce499-129">Cross Joins</span></span>

<span data-ttu-id="ce499-130">`CROSS JOIN` 쿼리 식에서는 다음 예제와 같이 두 컬렉션의 Cartesian 곱을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-130">A `CROSS JOIN` query expression produces the Cartesian product of the two collections, as illustrated in the following example:</span></span>

`FROM C AS c CROSS JOIN D as d`

#### <a name="inner-joins"></a><span data-ttu-id="ce499-131">Inner Join</span><span class="sxs-lookup"><span data-stu-id="ce499-131">Inner Joins</span></span>

<span data-ttu-id="ce499-132">`INNER JOIN`에서는 다음 예제와 같이 두 컬렉션의 제한된 Cartesian 곱을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-132">An `INNER JOIN` produces a constrained Cartesian product of the two collections, as illustrated in the following example:</span></span>

`FROM C AS c [INNER] JOIN D AS d ON e`

<span data-ttu-id="ce499-133">위의 쿼리 식에서는 `ON` 조건이 true인 오른쪽 컬렉션의 모든 요소와 왼쪽 컬렉션의 모든 요소 쌍으로 이루어진 조합을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-133">The previous query expression processes a combination of every element of the collection on the left paired against every element of the collection on the right, where the `ON` condition is true.</span></span> <span data-ttu-id="ce499-134">`ON` 조건이 지정되지 않은 경우 `INNER JOIN`은 `CROSS JOIN`이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-134">If no `ON` condition is specified, an `INNER JOIN` degenerates to a `CROSS JOIN`.</span></span>

#### <a name="left-outer-joins-and-right-outer-joins"></a><span data-ttu-id="ce499-135">Left Outer Join 및 Right Outer Join</span><span class="sxs-lookup"><span data-stu-id="ce499-135">Left Outer Joins and Right Outer Joins</span></span>

<span data-ttu-id="ce499-136">`OUTER JOIN` 쿼리 식에서는 다음 예제와 같이 두 컬렉션의 제한된 Cartesian 곱을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-136">An `OUTER JOIN` query expression produces a constrained Cartesian product of the two collections, as illustrated in the following example:</span></span>

`FROM C AS c LEFT OUTER JOIN D AS d ON e`

<span data-ttu-id="ce499-137">위의 쿼리 식에서는 `ON` 조건이 true인 오른쪽 컬렉션의 모든 요소와 왼쪽 컬렉션의 모든 요소 쌍으로 이루어진 조합을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-137">The previous query expression processes a combination of every element of the collection on the left paired against every element of the collection on the right, where the `ON` condition is true.</span></span> <span data-ttu-id="ce499-138">`ON` 조건이 false이면 식에서 값이 Null인 오른쪽 요소와 쌍을 이루는 왼쪽 요소의 단일 인스턴스를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-138">If the `ON` condition is false, the expression still processes a single instance of the element on the left paired against the element on the right, with the value null.</span></span>

<span data-ttu-id="ce499-139">`RIGHT OUTER JOIN`은 유사한 방식으로 표현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-139">A `RIGHT OUTER JOIN` may be expressed in a similar manner.</span></span>

#### <a name="full-outer-joins"></a><span data-ttu-id="ce499-140">Full Outer Join</span><span class="sxs-lookup"><span data-stu-id="ce499-140">Full Outer Joins</span></span>

<span data-ttu-id="ce499-141">명시적 `FULL OUTER JOIN`에서는 다음 예제와 같이 두 컬렉션의 제한된 Cartesian 곱을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-141">An explicit `FULL OUTER JOIN` produces a constrained Cartesian product of the two collections as illustrated in the following example:</span></span>

`FROM C AS c FULL OUTER JOIN D AS d ON e`

<span data-ttu-id="ce499-142">위의 쿼리 식에서는 `ON` 조건이 true인 오른쪽 컬렉션의 모든 요소와 왼쪽 컬렉션의 모든 요소 쌍으로 이루어진 조합을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-142">The previous query expression processes a combination of every element of the collection on the left paired against every element of the collection on the right, where the `ON` condition is true.</span></span> <span data-ttu-id="ce499-143">`ON` 조건이 false이면 식에서 값이 Null인 오른쪽 요소와 쌍을 이루는 왼쪽 요소의 단일 인스턴스를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-143">If the `ON` condition is false, the expression still processes one instance of the element on the left paired against the element on the right, with the value null.</span></span> <span data-ttu-id="ce499-144">또한 값이 Null인 왼쪽 요소와 쌍을 이루는 오른쪽 요소의 단일 인스턴스를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-144">It also processes one instance of the element on the right paired against the element on the left, with the value null.</span></span>

> [!NOTE]
> <span data-ttu-id="ce499-145">Transact-sql에서 SQL-92과의 호환성을 유지 하기 위해 외부 키워드는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-145">To preserve compatibility with SQL-92, in Transact-SQL the OUTER keyword is optional.</span></span> <span data-ttu-id="ce499-146">따라서 `LEFT JOIN`, `RIGHT JOIN` 및 `FULL JOIN`은 `LEFT OUTER JOIN`, `RIGHT OUTER JOIN` 및 `FULL OUTER JOIN`과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-146">Therefore, `LEFT JOIN`, `RIGHT JOIN`, and `FULL JOIN` are synonyms for `LEFT OUTER JOIN`, `RIGHT OUTER JOIN`, and `FULL OUTER JOIN`.</span></span>

### <a name="apply-clause-item"></a><span data-ttu-id="ce499-147">APPLY 절 항목</span><span class="sxs-lookup"><span data-stu-id="ce499-147">APPLY Clause Item</span></span>

[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="ce499-148">에서는 두 가지 종류의 `APPLY`인 `CROSS APPLY`와 `OUTER APPLY`를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-148">supports two kinds of `APPLY`: `CROSS APPLY` and `OUTER APPLY`.</span></span>

<span data-ttu-id="ce499-149">`CROSS APPLY`에서는 오른쪽 요소를 계산하여 구한 컬렉션 요소와 왼쪽 컬렉션의 각 요소로 이루어진 고유한 쌍을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-149">A `CROSS APPLY` produces a unique pairing of each element of the collection on the left with an element of the collection produced by evaluating the expression on the right.</span></span> <span data-ttu-id="ce499-150">`CROSS APPLY`를 사용하면 다음의 연관된 컬렉션 예제와 같이 오른쪽 식의 기능이 왼쪽의 요소에 종속됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-150">With a `CROSS APPLY`, the expression on the right is functionally dependent on the element on the left, as illustrated in the following associated collection example:</span></span>

`SELECT c, f FROM C AS c CROSS APPLY c.Assoc AS f`

<span data-ttu-id="ce499-151">`CROSS APPLY`의 동작은 조인 목록과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-151">The behavior of `CROSS APPLY` is similar to the join list.</span></span> <span data-ttu-id="ce499-152">오른쪽의 식이 빈 컬렉션으로 계산되면 `CROSS APPLY`에서 왼쪽 요소의 해당 인스턴스에 대해 쌍을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-152">If the expression on the right evaluates to an empty collection, the `CROSS APPLY` produces no pairings for that instance of the element on the left.</span></span>

<span data-ttu-id="ce499-153">`OUTER APPLY`는 오른쪽의 식이 빈 컬렉션으로 계산되는 경우에도 쌍이 생성된다는 점을 제외하고 `CROSS APPLY`와 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-153">An `OUTER APPLY` resembles a `CROSS APPLY`, except a pairing is still produced even when the expression on the right evaluates to an empty collection.</span></span> <span data-ttu-id="ce499-154">다음은 `OUTER APPLY`의 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-154">The following is an example of an `OUTER APPLY`:</span></span>

`SELECT c, f FROM C AS c OUTER APPLY c.Assoc AS f`

> [!NOTE]
> <span data-ttu-id="ce499-155">Transact-sql과는 달리에서 명시적인 unnest 단계가 필요 하지 않습니다 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ce499-155">Unlike in Transact-SQL, there is no need for an explicit unnest step in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>

> [!NOTE]
> <span data-ttu-id="ce499-156">`CROSS` 및 `OUTER APPLY` 연산자는 SQL Server 2005에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-156">`CROSS` and `OUTER APPLY` operators were introduced in SQL Server 2005.</span></span> <span data-ttu-id="ce499-157">경우에 따라 쿼리 파이프라인에서 `CROSS APPLY` 및/또는 `OUTER APPLY` 연산자가 포함된 Transact-SQL을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-157">In some cases, the query pipeline might produce Transact-SQL that contains `CROSS APPLY` and/or `OUTER APPLY` operators.</span></span> <span data-ttu-id="ce499-158">SQL Server 2005 이전 SQL Server 버전을 비롯 한 일부 백엔드 공급자는 이러한 연산자를 지원 하지 않으므로 이러한 백 엔드 공급자에서는 이러한 쿼리를 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-158">Because some backend providers, including versions of SQL Server earlier than SQL Server 2005, do not support these operators, such queries cannot be executed on these backend providers.</span></span>
>
> <span data-ttu-id="ce499-159">출력 쿼리에 `CROSS APPLY` 및/또는 `OUTER APPLY` 연산자가 포함될 수 있는 일부 일반적인 시나리오는 페이징이 포함된 상호 관련된 하위 쿼리, 상호 관련된 하위 쿼리 또는 탐색으로 생성된 컬렉션에 대한 AnyElement, 요소 선택기를 허용하는 그룹화 메서드를 사용하는 LINQ 쿼리, `CROSS APPLY` 또는 `OUTER APPLY`가 명시적으로 지정된 쿼리, `DEREF` 구문에 대한 `REF` 구문이 있는 쿼리 등입니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-159">Some typical scenarios that might lead to the presence of `CROSS APPLY` and/or `OUTER APPLY` operators in the output query are the following: a correlated subquery with paging; AnyElement over a correlated subquery or over a collection produced by navigation; LINQ queries that use grouping methods that accept an element selector; a query in which a `CROSS APPLY` or an `OUTER APPLY` are explicitly specified; a query that has a `DEREF` construct over a `REF` construct.</span></span>

## <a name="multiple-collections-in-the-from-clause"></a><span data-ttu-id="ce499-160">FROM 절의 여러 컬렉션</span><span class="sxs-lookup"><span data-stu-id="ce499-160">Multiple Collections in the FROM Clause</span></span>

<span data-ttu-id="ce499-161">`FROM` 절에는 둘 이상의 컬렉션이 쉼표로 구분되어 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-161">The `FROM` clause can contain more than one collection separated by commas.</span></span> <span data-ttu-id="ce499-162">이 경우 컬렉션은 함께 조인되는 것으로 가정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-162">In these cases, the collections are assumed to be joined together.</span></span> <span data-ttu-id="ce499-163">이러한 조인을 N-Way CROSS JOIN으로 간주하세요.</span><span class="sxs-lookup"><span data-stu-id="ce499-163">Think of these as an n-way CROSS JOIN.</span></span>

<span data-ttu-id="ce499-164">다음 예제에서 및는 `C` `D` 독립 된 컬렉션 이지만 `c.Names` 는에 종속 됩니다 `C` .</span><span class="sxs-lookup"><span data-stu-id="ce499-164">In the following example, `C` and `D` are independent collections, but `c.Names` is dependent on `C`.</span></span>

```sql
FROM C AS c, D AS d, c.Names AS e
```

<span data-ttu-id="ce499-165">위의 예제는 다음 예제와 논리적으로 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-165">The previous example is logically equivalent to the following example:</span></span>

`FROM (C AS c JOIN D AS d) CROSS APPLY c.Names AS e`

## <a name="left-correlation"></a><span data-ttu-id="ce499-166">왼쪽 상관 관계</span><span class="sxs-lookup"><span data-stu-id="ce499-166">Left Correlation</span></span>

 <span data-ttu-id="ce499-167">`FROM` 절의 항목은 위의 절에서 지정된 항목을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-167">Items in the `FROM` clause can refer to items specified in earlier clauses.</span></span> <span data-ttu-id="ce499-168">다음 예제에서 `C` 및 `D`는 독립된 컬렉션이지만 `c.Names`는 `C`에 종속됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-168">In the following example, `C` and `D` are independent collections, but `c.Names` is dependent on `C`:</span></span>

```sql
from C as c, D as d, c.Names as e
```

<span data-ttu-id="ce499-169">위의 구문은 다음 구문과 논리적으로 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-169">This is logically equivalent to:</span></span>

```sql
from (C as c join D as d) cross apply c.Names as e
```

## <a name="semantics"></a><span data-ttu-id="ce499-170">의미 체계</span><span class="sxs-lookup"><span data-stu-id="ce499-170">Semantics</span></span>

<span data-ttu-id="ce499-171">논리적으로, `FROM` 절의 컬렉션은 1-way Cross Join의 경우를 제외하고 `n`-way Cross Join의 일부인 것으로 가정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-171">Logically, the collections in the `FROM` clause are assumed to be part of an `n`-way cross join (except in the case of a 1-way cross join).</span></span> <span data-ttu-id="ce499-172">`FROM` 절의 별칭은 왼쪽에서 오른쪽으로 처리되고 나중에 참조하기 위해 현재 범위에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-172">Aliases in the `FROM` clause are processed left to right, and are added to the current scope for later reference.</span></span> <span data-ttu-id="ce499-173">`FROM` 절은 행의 multiset을 생성하는 것으로 가정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-173">The `FROM` clause is assumed to produce a multiset of rows.</span></span> <span data-ttu-id="ce499-174">해당 컬렉션 항목의 단일 요소를 나타내는 `FROM` 절의 각 항목에 대해 하나의 필드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-174">There will be one field for each item in the `FROM` clause that represents a single element from that collection item.</span></span>

<span data-ttu-id="ce499-175">`FROM` 절은 논리적으로 Row(c, d, e) 형식의 행 multiset을 생성합니다. 여기서 c, d, e 필드는 `C`, `D` 및 `c.Names`의 요소 형식인 것으로 가정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-175">The `FROM` clause logically produces a multiset of rows of type Row(c, d, e) where fields c, d, and e are assumed to be of the element type of `C`, `D`, and `c.Names`.</span></span>

[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="ce499-176">에서는 범위에 있는 각 단순 `FROM` 절 항목에 대해 별칭을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-176">introduces an alias for each simple `FROM` clause item in scope.</span></span> <span data-ttu-id="ce499-177">예를 들어, 다음 FROM 절 조각에서 범위에 생성된 이름은 c, d, e입니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-177">For example, in the following FROM clause snippet, The names introduced into scope are c, d, and e.</span></span>

```sql
from (C as c join D as d) cross apply c.Names as e
```

<span data-ttu-id="ce499-178">에서 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 절은 transact-sql과 달리 `FROM` 범위에 별칭을 도입 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-178">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (unlike Transact-SQL), the `FROM` clause only introduces the aliases into scope.</span></span> <span data-ttu-id="ce499-179">이러한 컬렉션의 열(속성)에 대한 모든 참조는 해당 별칭으로 정규화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-179">Any references to columns (properties) of these collections must be qualified with the alias.</span></span>

## <a name="pulling-up-keys-from-nested-queries"></a><span data-ttu-id="ce499-180">중첩 쿼리에서 키 끌어오기</span><span class="sxs-lookup"><span data-stu-id="ce499-180">Pulling Up Keys from Nested Queries</span></span>

<span data-ttu-id="ce499-181">중첩 쿼리에서 키를 끌어와야 하는 특정 쿼리 유형은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-181">Certain types of queries that require pulling up keys from a nested query are not supported.</span></span> <span data-ttu-id="ce499-182">예를 들어, 다음 쿼리는 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-182">For example, the following query is valid:</span></span>

```sql
select c.Orders from Customers as c
```

<span data-ttu-id="ce499-183">그러나 다음 쿼리는 중첩 쿼리에 키가 없으므로 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ce499-183">However, the following query is not valid, because the nested query does not have any keys:</span></span>

```sql
select {1} from {2, 3}
```

## <a name="see-also"></a><span data-ttu-id="ce499-184">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ce499-184">See also</span></span>

- [<span data-ttu-id="ce499-185">엔터티 SQL 참조</span><span class="sxs-lookup"><span data-stu-id="ce499-185">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="ce499-186">쿼리 식</span><span class="sxs-lookup"><span data-stu-id="ce499-186">Query Expressions</span></span>](query-expressions-entity-sql.md)
- [<span data-ttu-id="ce499-187">nullable 구조적 형식</span><span class="sxs-lookup"><span data-stu-id="ce499-187">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)
