---
title: LINQ 쿼리 작업의 형식 관계(C#)
description: LINQ 쿼리의 변수 형식이 서로 관련되는 방식에 대해 알아봅니다. LINQ 쿼리 작업은 데이터 원본, 쿼리 및 실행에서 강력하게 형식화됩니다.
ms.date: 07/20/2015
helpviewer_keywords:
- inferring type information [LINQ in C#]
- data sources [LINQ in C#], type relationships
- queries [LINQ in C#], type relationships
- relationships [LINQ in C#]
- type relationships [LINQ in C#]
- variable relationships [LINQ in C#]
- type information inferred [LINQ in C#]
- data transformations [LINQ in C#]
- LINQ [C#], type relationships
ms.assetid: 99118938-d47c-4d7e-bb22-2657a9f95268
ms.openlocfilehash: 20f0b37a156e3b3f9c63f14cb83d678d26f685ee
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302284"
---
# <a name="type-relationships-in-linq-query-operations-c"></a><span data-ttu-id="52636-104">LINQ 쿼리 작업의 형식 관계(C#)</span><span class="sxs-lookup"><span data-stu-id="52636-104">Type Relationships in LINQ Query Operations (C#)</span></span>
<span data-ttu-id="52636-105">쿼리를 효과적으로 작성하려면 전체 쿼리 작업의 변수 형식이 모두 어떻게 서로 관련되는지를 이해해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52636-105">To write queries effectively, you should understand how types of the variables in a complete query operation all relate to each other.</span></span> <span data-ttu-id="52636-106">이러한 관계를 이해하면 설명서의 LINQ 샘플 및 코드 예제를 더 쉽게 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52636-106">If you understand these relationships you will more easily comprehend the LINQ samples and code examples in the documentation.</span></span> <span data-ttu-id="52636-107">또한 `var`을 사용하여 변수를 암시적으로 형식화하는 경우 백그라운드에서 발생하는 상황을 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52636-107">Furthermore, you will understand what occurs behind the scenes when variables are implicitly typed by using `var`.</span></span>  
  
 <span data-ttu-id="52636-108">LINQ 쿼리 작업은 데이터 소스, 쿼리 자체 및 쿼리 실행에서 강력하게 형식화됩니다.</span><span class="sxs-lookup"><span data-stu-id="52636-108">LINQ query operations are strongly typed in the data source, in the query itself, and in the query execution.</span></span> <span data-ttu-id="52636-109">쿼리의 변수 형식은 데이터 소스의 요소 형식 및 `foreach` 문의 반복 변수 형식과 호환되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52636-109">The type of the variables in the query must be compatible with the type of the elements in the data source and with the type of the iteration variable in the `foreach` statement.</span></span> <span data-ttu-id="52636-110">이 강력한 형식화는 사용자가 발견하기 전에 수정될 수 있도록 컴파일 시간에 형식 오류가 catch되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="52636-110">This strong typing guarantees that type errors are caught at compile time when they can be corrected before users encounter them.</span></span>  
  
 <span data-ttu-id="52636-111">이러한 형식 관계를 보여 주기 위해 뒤에 나오는 대부분의 예제에서는 모든 변수에 명시적 형식화를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="52636-111">In order to demonstrate these type relationships, most of the examples that follow use explicit typing for all variables.</span></span> <span data-ttu-id="52636-112">마지막 예제에서는 [var](../../../language-reference/keywords/var.md)을 통해 암시적 형식화를 사용하는 경우에도 어떻게 동일한 원칙이 적용되는지를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="52636-112">The last example shows how the same principles apply even when you use implicit typing by using [var](../../../language-reference/keywords/var.md).</span></span>  
  
## <a name="queries-that-do-not-transform-the-source-data"></a><span data-ttu-id="52636-113">소스 데이터를 변환하지 않는 쿼리</span><span class="sxs-lookup"><span data-stu-id="52636-113">Queries that do not Transform the Source Data</span></span>  
 <span data-ttu-id="52636-114">다음 그림에서는 데이터 변환을 수행하지 않는 LINQ to Objects 쿼리 작업을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="52636-114">The following illustration shows a LINQ to Objects query operation that performs no transformations on the data.</span></span> <span data-ttu-id="52636-115">소스에는 문자열 시퀀스가 포함되어 있고, 쿼리 출력도 문자열 시퀀스입니다.</span><span class="sxs-lookup"><span data-stu-id="52636-115">The source contains a sequence of strings and the query output is also a sequence of strings.</span></span>  
  
 ![LINQ 쿼리에서 데이터 형식의 관계를 보여 주는 다이어그램](./media/type-relationships-in-linq-query-operations/linq-query-data-type-relation.png)  
  
1. <span data-ttu-id="52636-117">데이터 소스의 형식 인수에 따라 범위 변수의 형식이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="52636-117">The type argument of the data source determines the type of the range variable.</span></span>  
  
2. <span data-ttu-id="52636-118">선택된 개체의 형식에 따라 쿼리 변수의 형식이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="52636-118">The type of the object that is selected determines the type of the query variable.</span></span> <span data-ttu-id="52636-119">여기서 `name`은 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="52636-119">Here `name` is a string.</span></span> <span data-ttu-id="52636-120">따라서 쿼리 변수는 `IEnumerable<string>`입니다.</span><span class="sxs-lookup"><span data-stu-id="52636-120">Therefore, the query variable is an `IEnumerable<string>`.</span></span>  
  
3. <span data-ttu-id="52636-121">쿼리 변수는 `foreach` 문에서 반복됩니다.</span><span class="sxs-lookup"><span data-stu-id="52636-121">The query variable is iterated over in the `foreach` statement.</span></span> <span data-ttu-id="52636-122">쿼리 변수가 문자열 시퀀스이기 때문에 반복 변수도 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="52636-122">Because the query variable is a sequence of strings, the iteration variable is also a string.</span></span>  
  
## <a name="queries-that-transform-the-source-data"></a><span data-ttu-id="52636-123">소스 데이터를 변환하는 쿼리</span><span class="sxs-lookup"><span data-stu-id="52636-123">Queries that Transform the Source Data</span></span>  
 <span data-ttu-id="52636-124">다음 그림에서는 간단한 데이터 변환을 수행하는 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 쿼리 작업을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="52636-124">The following illustration shows a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] query operation that performs a simple transformation on the data.</span></span> <span data-ttu-id="52636-125">쿼리는 `Customer` 개체 시퀀스를 입력으로 사용하고 결과에서 `Name` 속성만 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="52636-125">The query takes a sequence of `Customer` objects as input, and selects only the `Name` property in the result.</span></span> <span data-ttu-id="52636-126">`Name`이 문자열이기 때문에 쿼리에서 출력으로 문자열 시퀀스를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="52636-126">Because `Name` is a string, the query produces a sequence of strings as output.</span></span>  
  
 ![데이터 형식을 변환하는 쿼리를 보여 주는 다이어그램](./media/type-relationships-in-linq-query-operations/linq-query-transform-data-type.png)  
  
1. <span data-ttu-id="52636-128">데이터 소스의 형식 인수에 따라 범위 변수의 형식이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="52636-128">The type argument of the data source determines the type of the range variable.</span></span>  
  
2. <span data-ttu-id="52636-129">`select` 문은 전체 `Customer` 개체가 아니라 `Name` 속성을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="52636-129">The `select` statement returns the `Name` property instead of the complete `Customer` object.</span></span> <span data-ttu-id="52636-130">`Name`이 문자열이므로 `custNameQuery`의 형식 인수는 `Customer`가 아니라 `string`입니다.</span><span class="sxs-lookup"><span data-stu-id="52636-130">Because `Name` is a string, the type argument of `custNameQuery` is `string`, not `Customer`.</span></span>  
  
3. <span data-ttu-id="52636-131">`custNameQuery`가 문자열 시퀀스이므로 `foreach` 루프의 반복 변수도 `string`이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52636-131">Because `custNameQuery` is a sequence of strings, the `foreach` loop's iteration variable must also be a `string`.</span></span>  
  
 <span data-ttu-id="52636-132">다음 그림에서는 약간 더 복잡한 변환을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="52636-132">The following illustration shows a slightly more complex transformation.</span></span> <span data-ttu-id="52636-133">`select` 문은 원래 `Customer` 개체의 두 멤버만 캡처하는 무명 형식을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="52636-133">The `select` statement returns an anonymous type that captures just two members of the original `Customer` object.</span></span>  
  
 ![데이터 형식을 변환하는 더 복잡한 쿼리를 보여 주는 다이어그램](./media/type-relationships-in-linq-query-operations/linq-complex-query-transform-data-type.png)  
  
1. <span data-ttu-id="52636-135">데이터 소스의 형식 인수는 항상 쿼리의 범위 변수 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="52636-135">The type argument of the data source is always the type of the range variable in the query.</span></span>  
  
2. <span data-ttu-id="52636-136">`select` 문이 무명 형식을 생성하기 때문에 `var`을 사용하여 쿼리 변수를 암시적으로 형식화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52636-136">Because the `select` statement produces an anonymous type, the query variable must be implicitly typed by using `var`.</span></span>  
  
3. <span data-ttu-id="52636-137">쿼리 변수의 형식이 암시적이기 때문에 `foreach` 루프의 반복 변수도 암시적이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52636-137">Because the type of the query variable is implicit, the iteration variable in the `foreach` loop must also be implicit.</span></span>  
  
## <a name="letting-the-compiler-infer-type-information"></a><span data-ttu-id="52636-138">컴파일러에서 형식 정보를 유추하도록 허용</span><span class="sxs-lookup"><span data-stu-id="52636-138">Letting the compiler infer type information</span></span>  
 <span data-ttu-id="52636-139">쿼리 작업의 형식 관계를 이해해야 하지만 컴파일러가 모든 작업을 대신 수행하도록 하는 옵션도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52636-139">Although you should understand the type relationships in a query operation, you have the option to let the compiler do all the work for you.</span></span> <span data-ttu-id="52636-140">[var](../../../language-reference/keywords/var.md) 키워드를 쿼리 작업의 모든 지역 변수에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52636-140">The keyword [var](../../../language-reference/keywords/var.md) can be used for any local variable in a query operation.</span></span> <span data-ttu-id="52636-141">다음 그림은 앞에서 설명한 예제 번호 2와 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="52636-141">The following illustration is similar to example number 2 that was discussed earlier.</span></span> <span data-ttu-id="52636-142">그러나 컴파일러는 쿼리 작업의 각 변수에 대해 강력한 형식을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="52636-142">However, the compiler supplies the strong type for each variable in the query operation.</span></span>  
  
 ![암시적 형식의 형식 흐름을 보여 주는 다이어그램](./media/type-relationships-in-linq-query-operations/linq-type-flow-implicit-typing.png)  
  
 <span data-ttu-id="52636-144">`var`에 대한 자세한 내용은 [암시적 형식 지역 변수](../../classes-and-structs/implicitly-typed-local-variables.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="52636-144">For more information about `var`, see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
