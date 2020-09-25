---
title: 집계 함수(Entity Framework용 SqlClient)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: 1c32ccfe18c67c9baeb7df0f981c9129b3bbc8bb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204517"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a><span data-ttu-id="72212-102">집계 함수(Entity Framework용 SqlClient)</span><span class="sxs-lookup"><span data-stu-id="72212-102">Aggregate Functions (SqlClient for Entity Framework)</span></span>

<span data-ttu-id="72212-103">.NET Framework Data Provider for SQL Server(SqlClient)에서는 집계 함수를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="72212-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides aggregate functions.</span></span> <span data-ttu-id="72212-104">집계 함수는 입력 값 집합에 대해 계산을 수행하여 하나의 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="72212-104">Aggregate functions perform calculations on a set of input values and return a value.</span></span> <span data-ttu-id="72212-105">이 함수는 SqlClient를 사용할 때 사용 가능한 SqlServer 네임스페이스에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72212-105">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="72212-106">공급자의 네임스페이스 속성이 있으면 특정 구문(예: 형식 및 함수)에 대해 이 공급자가 사용하는 접두사를 Entity Framework에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72212-106">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span>  
  
 <span data-ttu-id="72212-107">다음은 SqlClient 집계 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="72212-107">The following are the SqlClient aggregate functions.</span></span>  

## <a name="avgexpression"></a><span data-ttu-id="72212-108">AVG (expression)</span><span class="sxs-lookup"><span data-stu-id="72212-108">AVG(expression)</span></span>

<span data-ttu-id="72212-109">컬렉션에 포함된 값의 평균을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="72212-109">Returns the average of the values in a collection.</span></span> <span data-ttu-id="72212-110">Null 값은 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="72212-110">Null values are ignored.</span></span>

<span data-ttu-id="72212-111">**인수**</span><span class="sxs-lookup"><span data-stu-id="72212-111">**Arguments**</span></span>

<span data-ttu-id="72212-112">`Int32`, `Int64`, `Double` 및 `Decimal`입니다.</span><span class="sxs-lookup"><span data-stu-id="72212-112">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="72212-113">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="72212-113">**Return Value**</span></span>

<span data-ttu-id="72212-114">`expression`의 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="72212-114">The type of `expression`.</span></span>

<span data-ttu-id="72212-115">**예제**</span><span class="sxs-lookup"><span data-stu-id="72212-115">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksum_aggcollection"></a><span data-ttu-id="72212-116">CHECKSUM_AGG (컬렉션)</span><span class="sxs-lookup"><span data-stu-id="72212-116">CHECKSUM_AGG(collection)</span></span>

 <span data-ttu-id="72212-117">컬렉션에 있는 값의 체크섬을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="72212-117">Returns the checksum of the values in a collection.</span></span> <span data-ttu-id="72212-118">Null 값은 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="72212-118">Null values are ignored.</span></span>

 <span data-ttu-id="72212-119">**인수**</span><span class="sxs-lookup"><span data-stu-id="72212-119">**Arguments**</span></span>

 <span data-ttu-id="72212-120">컬렉션 ( `Int32` )입니다.</span><span class="sxs-lookup"><span data-stu-id="72212-120">A Collection(`Int32`).</span></span>

 <span data-ttu-id="72212-121">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="72212-121">**Return Value**</span></span>

 <span data-ttu-id="72212-122">`Int32`입니다.</span><span class="sxs-lookup"><span data-stu-id="72212-122">An `Int32`.</span></span>

 <span data-ttu-id="72212-123">**예제**</span><span class="sxs-lookup"><span data-stu-id="72212-123">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]

## <a name="countexpression"></a><span data-ttu-id="72212-124">COUNT (식)</span><span class="sxs-lookup"><span data-stu-id="72212-124">COUNT(expression)</span></span>

<span data-ttu-id="72212-125">컬렉션의 항목 수를 `Int32`로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="72212-125">Returns the number of items in a collection as an `Int32`.</span></span>

<span data-ttu-id="72212-126">**인수**</span><span class="sxs-lookup"><span data-stu-id="72212-126">**Arguments**</span></span>

<span data-ttu-id="72212-127">컬렉션입니다 \<T> . 여기서 T는 다음 형식 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="72212-127">A Collection\<T>, where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="72212-128">`Guid` (SQL Server 2000에서 반환 되지 않음)</span><span class="sxs-lookup"><span data-stu-id="72212-128">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="72212-129">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="72212-129">**Return Value**</span></span>

<span data-ttu-id="72212-130">`Int32`입니다.</span><span class="sxs-lookup"><span data-stu-id="72212-130">An `Int32`.</span></span>

<span data-ttu-id="72212-131">**예제**</span><span class="sxs-lookup"><span data-stu-id="72212-131">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)]

## <a name="count_bigexpression"></a><span data-ttu-id="72212-132">COUNT_BIG (식)</span><span class="sxs-lookup"><span data-stu-id="72212-132">COUNT_BIG(expression)</span></span>

<span data-ttu-id="72212-133">컬렉션의 항목 수를 `bigint`로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="72212-133">Returns the number of items in a collection as a `bigint`.</span></span>

 <span data-ttu-id="72212-134">**인수**</span><span class="sxs-lookup"><span data-stu-id="72212-134">**Arguments**</span></span>

 <span data-ttu-id="72212-135">컬렉션 (T) 이며, 여기서 T는 다음 형식 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="72212-135">A Collection(T), where T is one of the following types:</span></span>

 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="72212-136">`Guid` (SQL Server 2000에서 반환 되지 않음)</span><span class="sxs-lookup"><span data-stu-id="72212-136">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="72212-137">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="72212-137">**Return Value**</span></span>

<span data-ttu-id="72212-138">`Int64`입니다.</span><span class="sxs-lookup"><span data-stu-id="72212-138">An `Int64`.</span></span>

<span data-ttu-id="72212-139">**예제**</span><span class="sxs-lookup"><span data-stu-id="72212-139">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a><span data-ttu-id="72212-140">MAX (expression)</span><span class="sxs-lookup"><span data-stu-id="72212-140">MAX(expression)</span></span>

<span data-ttu-id="72212-141">컬렉션의 최대값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="72212-141">Returns the maximum value the collection.</span></span>

<span data-ttu-id="72212-142">**인수**</span><span class="sxs-lookup"><span data-stu-id="72212-142">**Arguments**</span></span>

<span data-ttu-id="72212-143">컬렉션 (T) 이며, 여기서 T는 다음 형식 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="72212-143">A Collection(T), where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="72212-144">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="72212-144">**Return Value**</span></span>

<span data-ttu-id="72212-145">`expression`의 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="72212-145">The type of `expression`.</span></span>

<span data-ttu-id="72212-146">**예제**</span><span class="sxs-lookup"><span data-stu-id="72212-146">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a><span data-ttu-id="72212-147">MIN (expression)</span><span class="sxs-lookup"><span data-stu-id="72212-147">MIN(expression)</span></span>

<span data-ttu-id="72212-148">컬렉션의 최소값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="72212-148">Returns the minimum value in a collection.</span></span>

<span data-ttu-id="72212-149">**인수**</span><span class="sxs-lookup"><span data-stu-id="72212-149">**Arguments**</span></span>

<span data-ttu-id="72212-150">컬렉션 (T) 이며, 여기서 T는 다음 형식 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="72212-150">A Collection(T), where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="72212-151">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="72212-151">**Return Value**</span></span>

<span data-ttu-id="72212-152">`expression`의 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="72212-152">The type of `expression`.</span></span>

<span data-ttu-id="72212-153">**예제**</span><span class="sxs-lookup"><span data-stu-id="72212-153">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a><span data-ttu-id="72212-154">STDEV (식)</span><span class="sxs-lookup"><span data-stu-id="72212-154">STDEV(expression)</span></span>

<span data-ttu-id="72212-155">지정한 식의 모든 값에 대한 통계적 표준 편차를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="72212-155">Returns the statistical standard deviation of all values in the specified expression.</span></span>

<span data-ttu-id="72212-156">**인수**</span><span class="sxs-lookup"><span data-stu-id="72212-156">**Arguments**</span></span>

<span data-ttu-id="72212-157">컬렉션 ( `Double` )입니다.</span><span class="sxs-lookup"><span data-stu-id="72212-157">A Collection(`Double`).</span></span>

<span data-ttu-id="72212-158">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="72212-158">**Return Value**</span></span>

<span data-ttu-id="72212-159">`Double`</span><span class="sxs-lookup"><span data-stu-id="72212-159">A `Double`.</span></span>

<span data-ttu-id="72212-160">**예제**</span><span class="sxs-lookup"><span data-stu-id="72212-160">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a><span data-ttu-id="72212-161">STDEVP (식)</span><span class="sxs-lookup"><span data-stu-id="72212-161">STDEVP(expression)</span></span>

<span data-ttu-id="72212-162">지정한 식에 있는 모든 값의 모집단에 대한 통계적 표준 편차를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="72212-162">Returns the statistical standard deviation for the population for all values in the specified expression.</span></span>

<span data-ttu-id="72212-163">**인수**</span><span class="sxs-lookup"><span data-stu-id="72212-163">**Arguments**</span></span>

<span data-ttu-id="72212-164">컬렉션 ( `Double` )입니다.</span><span class="sxs-lookup"><span data-stu-id="72212-164">A Collection(`Double`).</span></span>

<span data-ttu-id="72212-165">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="72212-165">**Return Value**</span></span>

<span data-ttu-id="72212-166">`Double`</span><span class="sxs-lookup"><span data-stu-id="72212-166">A `Double`.</span></span>

<span data-ttu-id="72212-167">**예제**</span><span class="sxs-lookup"><span data-stu-id="72212-167">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a><span data-ttu-id="72212-168">합계 (식)</span><span class="sxs-lookup"><span data-stu-id="72212-168">SUM(expression)</span></span>

<span data-ttu-id="72212-169">컬렉션에 있는 모든 값의 합계를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="72212-169">Returns the sum of all the values in the collection.</span></span>

<span data-ttu-id="72212-170">**인수**</span><span class="sxs-lookup"><span data-stu-id="72212-170">**Arguments**</span></span>

<span data-ttu-id="72212-171">컬렉션 (T) 이며, 여기서 T는 `Int32` , `Int64` , `Double` , 형식 중 하나 `Decimal` 입니다.</span><span class="sxs-lookup"><span data-stu-id="72212-171">A Collection(T) where T is one of the following types: `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="72212-172">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="72212-172">**Return Value**</span></span>

<span data-ttu-id="72212-173">`expression`의 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="72212-173">The type of `expression`.</span></span>

<span data-ttu-id="72212-174">**예제**</span><span class="sxs-lookup"><span data-stu-id="72212-174">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a><span data-ttu-id="72212-175">VAR (expression)</span><span class="sxs-lookup"><span data-stu-id="72212-175">VAR(expression)</span></span>

<span data-ttu-id="72212-176">지정한 식에 있는 모든 값의 통계적 분산을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="72212-176">Returns the statistical variance of all values in the specified expression.</span></span>

<span data-ttu-id="72212-177">**인수**</span><span class="sxs-lookup"><span data-stu-id="72212-177">**Arguments**</span></span>

<span data-ttu-id="72212-178">컬렉션 ( `Double` )입니다.</span><span class="sxs-lookup"><span data-stu-id="72212-178">A Collection(`Double`).</span></span>

<span data-ttu-id="72212-179">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="72212-179">**Return Value**</span></span>

<span data-ttu-id="72212-180">`Double`</span><span class="sxs-lookup"><span data-stu-id="72212-180">A `Double`.</span></span>

<span data-ttu-id="72212-181">**예제**</span><span class="sxs-lookup"><span data-stu-id="72212-181">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a><span data-ttu-id="72212-182">VARP (식)</span><span class="sxs-lookup"><span data-stu-id="72212-182">VARP(expression)</span></span>

<span data-ttu-id="72212-183">지정한 식에 있는 모든 값의 모집단에 대한 통계적 분산을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="72212-183">Returns the statistical variance for the population for all values in the specified expression.</span></span>

<span data-ttu-id="72212-184">**인수**</span><span class="sxs-lookup"><span data-stu-id="72212-184">**Arguments**</span></span>

<span data-ttu-id="72212-185">컬렉션 ( `Double` )입니다.</span><span class="sxs-lookup"><span data-stu-id="72212-185">A Collection(`Double`).</span></span>

<span data-ttu-id="72212-186">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="72212-186">**Return Value**</span></span>

<span data-ttu-id="72212-187">`Double`</span><span class="sxs-lookup"><span data-stu-id="72212-187">A `Double`.</span></span>

<span data-ttu-id="72212-188">**예제**</span><span class="sxs-lookup"><span data-stu-id="72212-188">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)]
  
## <a name="see-also"></a><span data-ttu-id="72212-189">참고 항목</span><span class="sxs-lookup"><span data-stu-id="72212-189">See also</span></span>

- [<span data-ttu-id="72212-190">집계 함수(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="72212-190">Aggregate Functions (Transact-SQL)</span></span>](/sql/t-sql/functions/aggregate-functions-transact-sql)
- [<span data-ttu-id="72212-191">Entity SQL 언어</span><span class="sxs-lookup"><span data-stu-id="72212-191">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
- [<span data-ttu-id="72212-192">집계 정식 함수</span><span class="sxs-lookup"><span data-stu-id="72212-192">Aggregate Canonical Functions</span></span>](./language-reference/aggregate-canonical-functions.md)
