---
title: using 문 - C# 참조
ms.date: 05/29/2020
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: b889d2fcbdf854dbe8948744810f9b74e9f0dac2
ms.sourcegitcommit: 5280b2aef60a1ed99002dba44e4b9e7f6c830604
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/03/2020
ms.locfileid: "84307048"
---
# <a name="using-statement-c-reference"></a><span data-ttu-id="46332-102">using 문(C# 참조)</span><span class="sxs-lookup"><span data-stu-id="46332-102">using statement (C# Reference)</span></span>

<span data-ttu-id="46332-103"><xref:System.IDisposable> 개체의 올바른 사용을 보장하는 편리한 구문을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="46332-103">Provides a convenient syntax that ensures the correct use of <xref:System.IDisposable> objects.</span></span> <span data-ttu-id="46332-104">C# 8.0부터 `using` 문은 <xref:System.IAsyncDisposable> 개체의 올바른 사용을 보장합니다.</span><span class="sxs-lookup"><span data-stu-id="46332-104">Beginning in C# 8.0, the `using` statement ensures the correct use of <xref:System.IAsyncDisposable> objects.</span></span>

## <a name="example"></a><span data-ttu-id="46332-105">예제</span><span class="sxs-lookup"><span data-stu-id="46332-105">Example</span></span>

<span data-ttu-id="46332-106">다음 예제에서는 `using` 문을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="46332-106">The following example shows how to use the `using` statement.</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetFirstExample":::

<span data-ttu-id="46332-107">C# 8.0부터는 중괄호가 필요하지 않은 `using` 문에 다음 대체 구문을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46332-107">Beginning with C# 8.0, you can use the following alternative syntax for the `using` statement that doesn't require braces:</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetModernUsing":::

## <a name="remarks"></a><span data-ttu-id="46332-108">설명</span><span class="sxs-lookup"><span data-stu-id="46332-108">Remarks</span></span>

<span data-ttu-id="46332-109"><xref:System.IO.File> 및 <xref:System.Drawing.Font>는 관리되지 않는 리소스에 액세스하는 관리되는 형식의 예입니다(이 경우 파일 핸들 및 디바이스 컨텍스트).</span><span class="sxs-lookup"><span data-stu-id="46332-109"><xref:System.IO.File> and <xref:System.Drawing.Font> are examples of managed types that access unmanaged resources (in this case file handles and device contexts).</span></span> <span data-ttu-id="46332-110">다른 많은 종류의 관리되지 않는 리소스 및 이를 캡슐화하는 클래스 라이브러리 형식이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46332-110">There are many other kinds of unmanaged resources and class library types that encapsulate them.</span></span> <span data-ttu-id="46332-111">해당 형식은 모두 <xref:System.IDisposable> 인터페이스 또는 <xref:System.IAsyncDisposable> 인터페이스를 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46332-111">All such types must implement the <xref:System.IDisposable> interface, or the <xref:System.IAsyncDisposable> interface.</span></span>

<span data-ttu-id="46332-112">`IDisposable` 개체의 수명이 단일 메서드로 제한된 경우 `using` 문에서 선언하고 인스턴스화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46332-112">When the lifetime of an `IDisposable` object is limited to a single method, you should declare and instantiate it in the `using` statement.</span></span> <span data-ttu-id="46332-113">`using` 문은 올바른 방법으로 개체에서 <xref:System.IDisposable.Dispose%2A> 메서드를 호출하며, (앞서 설명한 대로 사용하는 경우) <xref:System.IDisposable.Dispose%2A>가 호출되자마자 개체 자체가 범위를 벗어나도록 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="46332-113">The `using` statement calls the <xref:System.IDisposable.Dispose%2A> method on the object in the correct way, and (when you use it as shown earlier) it also causes the object itself to go out of scope as soon as <xref:System.IDisposable.Dispose%2A> is called.</span></span> <span data-ttu-id="46332-114">`using` 블록 내에서 개체는 읽기 전용이며 수정하거나 다시 할당할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="46332-114">Within the `using` block, the object is read-only and can't be modified or reassigned.</span></span> <span data-ttu-id="46332-115">개체가 `IDisposable` 대신 `IAsyncDisposable`을 구현하는 경우 `using` 문은 <xref:System.IAsyncDisposable.DisposeAsync%2A>를 호출하고 반환된 <xref:System.Threading.Tasks.ValueTask>를 `awaits`합니다.</span><span class="sxs-lookup"><span data-stu-id="46332-115">If the object implements `IAsyncDisposable` instead of `IDisposable`, the `using` statement calls the <xref:System.IAsyncDisposable.DisposeAsync%2A> and `awaits` the returned <xref:System.Threading.Tasks.ValueTask>.</span></span> <span data-ttu-id="46332-116"><xref:System.IAsyncDisposable>에 대한 자세한 내용은 [DisposeAsync 메서드 구현](../../../standard/garbage-collection/implementing-disposeasync.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="46332-116">For more information on <xref:System.IAsyncDisposable>, see [Implement a DisposeAsync method](../../../standard/garbage-collection/implementing-disposeasync.md).</span></span>

<span data-ttu-id="46332-117">`using` 문은 `using` 블록 내에서 예외가 발생하더라도 <xref:System.IDisposable.Dispose%2A>(또는 <xref:System.IAsyncDisposable.DisposeAsync%2A>)가 호출되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="46332-117">The `using` statement ensures that <xref:System.IDisposable.Dispose%2A> (or <xref:System.IAsyncDisposable.DisposeAsync%2A>) is called even if an exception occurs within the `using` block.</span></span> <span data-ttu-id="46332-118">`try` 블록 내부에 개체를 배치한 다음, `finally` 블록에서 <xref:System.IDisposable.Dispose%2A>(또는 <xref:System.IAsyncDisposable.DisposeAsync%2A>)를 호출해도 동일한 결과를 얻을 수 있습니다. 실제로 컴파일러는 이 방법으로 `using` 문을 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="46332-118">You can achieve the same result by putting the object inside a `try` block and then calling <xref:System.IDisposable.Dispose%2A> (or <xref:System.IAsyncDisposable.DisposeAsync%2A>) in a `finally` block; in fact, this is how the `using` statement is translated by the compiler.</span></span> <span data-ttu-id="46332-119">이전의 코드 예제는 컴파일 시 다음 코드로 확장됩니다(개체의 제한된 범위를 만드는 여분의 중괄호 참고).</span><span class="sxs-lookup"><span data-stu-id="46332-119">The code example earlier expands to the following code at compile time (note the extra curly braces to create the limited scope for the object):</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetTryFinallyExample":::

<span data-ttu-id="46332-120">최신 `using` 문 구문은 유사한 코드로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="46332-120">The newer `using` statement syntax translates to similar code.</span></span> <span data-ttu-id="46332-121">변수가 선언된 위치에서 `try` 블록이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="46332-121">The `try` block opens where the variable is declared.</span></span> <span data-ttu-id="46332-122">`finally` 블록은 일반적으로 메서드의 끝에 있는 바깥쪽 블록의 가까이에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="46332-122">The `finally` block is added at the close of the enclosing block, typically at the end of a method.</span></span>

<span data-ttu-id="46332-123">`try`-`finally` 문에 대한 자세한 내용은 [try-finally](try-finally.md) 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="46332-123">For more information about the `try`-`finally` statement, see the [try-finally](try-finally.md) article.</span></span>

<span data-ttu-id="46332-124">다음 예제와 같이 단일 `using` 문에서 한 형식의 여러 인스턴스를 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46332-124">Multiple instances of a type can be declared in a single `using` statement, as shown in the following example.</span></span> <span data-ttu-id="46332-125">단일 문에서 여러 변수를 선언하는 경우에는 암시적으로 형식화된 변수(`var`)를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="46332-125">Notice that you can't use implicitly typed variables (`var`) when you declare multiple variables in a single statement:</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetDeclareMultipleVariables":::

<span data-ttu-id="46332-126">다음 예제와 같이 C# 8에 도입된 새로운 구문을 사용하여 동일한 형식의 여러 선언을 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46332-126">You can combine multiple declarations of the same type using the new syntax introduced with C# 8 as well, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetModernMultipleVariables":::

<span data-ttu-id="46332-127">리소스 개체를 인스턴스화한 후 `using` 문에 변수를 전달할 수 있지만, 이 방법이 최선은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="46332-127">You can instantiate the resource object and then pass the variable to the `using` statement, but this isn't a best practice.</span></span> <span data-ttu-id="46332-128">이 경우 컨트롤이 `using` 블록을 벗어난 후에도 개체가 범위 내에 있지만, 관리되지 않는 리소스에 액세스하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46332-128">In this case, after control leaves the `using` block, the object remains in scope but probably has no access to its unmanaged resources.</span></span> <span data-ttu-id="46332-129">즉, 더 이상 완전히 초기화되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="46332-129">In other words, it's not fully initialized anymore.</span></span> <span data-ttu-id="46332-130">`using` 블록 외부에서 개체를 사용하려고 하면 예외가 throw될 위험이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46332-130">If you try to use the object outside the `using` block, you risk causing an exception to be thrown.</span></span> <span data-ttu-id="46332-131">따라서 `using` 문에서 개체를 인스턴스화하고 `using` 블록에서 범위를 제한하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="46332-131">For this reason, it's better to instantiate the object in the `using` statement and limit its scope to the `using` block.</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetDeclareBeforeUsing":::

<span data-ttu-id="46332-132">`IDisposable` 개체를 삭제하는 방법에 대한 자세한 내용은 [IDisposable을 구현하는 개체 사용](../../../standard/garbage-collection/using-objects.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="46332-132">For more information about disposing of `IDisposable` objects, see [Using objects that implement IDisposable](../../../standard/garbage-collection/using-objects.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="46332-133">C# 언어 사양</span><span class="sxs-lookup"><span data-stu-id="46332-133">C# language specification</span></span>

<span data-ttu-id="46332-134">자세한 내용은 [C# 언어 사양](/dotnet/csharp/language-reference/language-specification/introduction)의 [using 문](~/_csharplang/spec/statements.md#the-using-statement)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="46332-134">For more information, see [The using statement](~/_csharplang/spec/statements.md#the-using-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="46332-135">언어 사양은 C# 구문 및 사용법에 대 한 신뢰할 수 있는 소스 됩니다.</span><span class="sxs-lookup"><span data-stu-id="46332-135">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="46332-136">참조</span><span class="sxs-lookup"><span data-stu-id="46332-136">See also</span></span>

- [<span data-ttu-id="46332-137">C# 참조</span><span class="sxs-lookup"><span data-stu-id="46332-137">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="46332-138">C# 프로그래밍 가이드</span><span class="sxs-lookup"><span data-stu-id="46332-138">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="46332-139">C# 키워드</span><span class="sxs-lookup"><span data-stu-id="46332-139">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="46332-140">using 지시문</span><span class="sxs-lookup"><span data-stu-id="46332-140">using Directive</span></span>](using-directive.md)
- [<span data-ttu-id="46332-141">가비지 수집</span><span class="sxs-lookup"><span data-stu-id="46332-141">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="46332-142">IDisposable을 구현하는 개체 사용</span><span class="sxs-lookup"><span data-stu-id="46332-142">Using objects that implement IDisposable</span></span>](../../../standard/garbage-collection/using-objects.md)
- [<span data-ttu-id="46332-143">IDisposable 인터페이스</span><span class="sxs-lookup"><span data-stu-id="46332-143">IDisposable interface</span></span>](xref:System.IDisposable)
- [<span data-ttu-id="46332-144">C# 8.0의 using 문</span><span class="sxs-lookup"><span data-stu-id="46332-144">using statement in C# 8.0</span></span>](~/_csharplang/proposals/csharp-8.0/using.md)
