---
title: LINQ 및 제네릭 형식(C#)
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], generic types
- generic types [LINQ]
- generics [LINQ]
ms.assetid: 660e3799-25ca-462c-8c4a-8bce04fbb031
ms.openlocfilehash: 2cbff0b31cac091a57ea35cbd01535b7d0c4b78a
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241762"
---
# <a name="linq-and-generic-types-c"></a><span data-ttu-id="1c52c-102">LINQ 및 제네릭 형식(C#)</span><span class="sxs-lookup"><span data-stu-id="1c52c-102">LINQ and Generic Types (C#)</span></span>
<span data-ttu-id="1c52c-103">LINQ 쿼리는 .NET Framework 버전 2.0에서 도입된 제네릭 형식을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c52c-103">LINQ queries are based on generic types, which were introduced in version 2.0 of .NET Framework.</span></span> <span data-ttu-id="1c52c-104">제네릭에 대한 세부 지식이 없어도 쿼리 작성을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c52c-104">You do not need an in-depth knowledge of generics before you can start writing queries.</span></span> <span data-ttu-id="1c52c-105">그러나 다음 두 가지 기본 개념은 이해하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1c52c-105">However, you may want to understand two basic concepts:</span></span>  
  
1. <span data-ttu-id="1c52c-106"><xref:System.Collections.Generic.List%601> 같은 제네릭 컬렉션 클래스의 인스턴스를 만들 때 “T”를 목록에 포함할 개체 형식으로 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="1c52c-106">When you create an instance of a generic collection class such as <xref:System.Collections.Generic.List%601>, you replace the "T" with the type of objects that the list will hold.</span></span> <span data-ttu-id="1c52c-107">예를 들어 문자열 목록은 `List<string>`으로 표현되고, `Customer` 개체 목록은 `List<Customer>`로 표현됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c52c-107">For example, a list of strings is expressed as `List<string>`, and a list of `Customer` objects is expressed as `List<Customer>`.</span></span> <span data-ttu-id="1c52c-108">제네릭 목록은 강력한 형식이어야 하며 해당 요소를 <xref:System.Object>로 저장하는 컬렉션에 비해 많은 장점을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1c52c-108">A generic list is strongly typed and provides many benefits over collections that store their elements as <xref:System.Object>.</span></span> <span data-ttu-id="1c52c-109">`List<string>`에 `Customer`를 추가하려고 하면 컴파일 시간에 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="1c52c-109">If you try to add a `Customer` to a `List<string>`, you will get an error at compile time.</span></span> <span data-ttu-id="1c52c-110">런타임 형식 캐스팅을 수행할 필요가 없기 때문에 제네릭 컬렉션을 사용하기가 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="1c52c-110">It is easy to use generic collections because you do not have to perform run-time type-casting.</span></span>  
  
2. <span data-ttu-id="1c52c-111"><xref:System.Collections.Generic.IEnumerable%601>은 `foreach` 문을 사용하여 제네릭 컬렉션 클래스를 열거할 수 있는 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="1c52c-111"><xref:System.Collections.Generic.IEnumerable%601> is the interface that enables generic collection classes to be enumerated by using the `foreach` statement.</span></span> <span data-ttu-id="1c52c-112">제네릭 컬렉션 클래스는 <xref:System.Collections.ArrayList> 등의 제네릭이 아닌 컬렉션이 <xref:System.Collections.IEnumerable>을 지원하는 것처럼 <xref:System.Collections.Generic.IEnumerable%601>을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="1c52c-112">Generic collection classes support <xref:System.Collections.Generic.IEnumerable%601> just as non-generic collection classes such as <xref:System.Collections.ArrayList> support <xref:System.Collections.IEnumerable>.</span></span>  
  
 <span data-ttu-id="1c52c-113">제네릭에 대한 자세한 내용은 [제네릭](../../generics/index.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1c52c-113">For more information about generics, see [Generics](../../generics/index.md).</span></span>  
  
## <a name="ienumerablet-variables-in-linq-queries"></a><span data-ttu-id="1c52c-114">LINQ 쿼리의 IEnumerable<T\> 변수</span><span class="sxs-lookup"><span data-stu-id="1c52c-114">IEnumerable<T\> variables in LINQ Queries</span></span>  
 <span data-ttu-id="1c52c-115">LINQ 쿼리 변수는 <xref:System.Collections.Generic.IEnumerable%601> 또는 파생 형식(예: <xref:System.Linq.IQueryable%601>)으로 형식화됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c52c-115">LINQ query variables are typed as <xref:System.Collections.Generic.IEnumerable%601> or a derived type such as <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="1c52c-116">형식이 `IEnumerable<Customer>`인 쿼리 변수가 표시되면 쿼리가 실행될 때 0개 이상의 `Customer` 개체 시퀀스를 생성한다는 의미입니다.</span><span class="sxs-lookup"><span data-stu-id="1c52c-116">When you see a query variable that is typed as `IEnumerable<Customer>`, it just means that the query, when it is executed, will produce a sequence of zero or more `Customer` objects.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#34)]  
  
 <span data-ttu-id="1c52c-117">자세한 내용은 [LINQ 쿼리 작업의 형식 관계](./type-relationships-in-linq-query-operations.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1c52c-117">For more information, see [Type Relationships in LINQ Query Operations](./type-relationships-in-linq-query-operations.md).</span></span>  
  
## <a name="letting-the-compiler-handle-generic-type-declarations"></a><span data-ttu-id="1c52c-118">컴파일러에서 제네릭 형식 선언을 처리하도록 허용</span><span class="sxs-lookup"><span data-stu-id="1c52c-118">Letting the Compiler Handle Generic Type Declarations</span></span>  
 <span data-ttu-id="1c52c-119">원하는 경우 [var](../../../language-reference/keywords/var.md) 키워드를 사용하여 제네릭 구문을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c52c-119">If you prefer, you can avoid generic syntax by using the [var](../../../language-reference/keywords/var.md) keyword.</span></span> <span data-ttu-id="1c52c-120">`var` 키워드는 `from` 절에 지정된 데이터 소스를 확인하여 쿼리 변수의 형식을 유추하도록 컴파일러에 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="1c52c-120">The `var` keyword instructs the compiler to infer the type of a query variable by looking at the data source specified in the `from` clause.</span></span> <span data-ttu-id="1c52c-121">다음 예제에서는 이전 예제와 동일하게 컴파일된 코드를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="1c52c-121">The following example produces the same compiled code as the previous example:</span></span>  
  
 [!code-csharp[csLINQGettingStarted#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#35)]  
  
 <span data-ttu-id="1c52c-122">`var` 키워드는 변수의 형식이 명확하거나 그룹 쿼리에 의해 생성되는 형식과 같이 중첩된 제네릭 형식을 명시적으로 지정하는 것이 중요하지 않은 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="1c52c-122">The `var` keyword is useful when the type of the variable is obvious or when it is not that important to explicitly specify nested generic types such as those that are produced by group queries.</span></span> <span data-ttu-id="1c52c-123">일반적으로 `var`을 사용하는 경우 다른 사용자가 코드를 읽기가 더 어려워질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c52c-123">In general, we recommend that if you use `var`, realize that it can make your code more difficult for others to read.</span></span> <span data-ttu-id="1c52c-124">자세한 내용은 [암시적으로 형식화된 지역 변수](../../classes-and-structs/implicitly-typed-local-variables.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1c52c-124">For more information, see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c52c-125">참조</span><span class="sxs-lookup"><span data-stu-id="1c52c-125">See also</span></span>

- [<span data-ttu-id="1c52c-126">제네릭</span><span class="sxs-lookup"><span data-stu-id="1c52c-126">Generics</span></span>](../../generics/index.md)
