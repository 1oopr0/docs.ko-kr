---
description: fixed 문 - C# 참조
title: fixed 문 - C# 참조
ms.date: 05/10/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: 05505916ab3837d2c433ec420d7928a8ee883fa8
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139725"
---
# <a name="fixed-statement-c-reference"></a><span data-ttu-id="83ca2-103">fixed 문(C# 참조)</span><span class="sxs-lookup"><span data-stu-id="83ca2-103">fixed Statement (C# Reference)</span></span>

<span data-ttu-id="83ca2-104">`fixed` 문은 가비지 수집기에서 이동 가능한 변수를 재배치할 수 없도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="83ca2-104">The `fixed` statement prevents the garbage collector from relocating a movable variable.</span></span> <span data-ttu-id="83ca2-105">`fixed` 문은 [unsafe](unsafe.md) 컨텍스트에서만 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="83ca2-105">The `fixed` statement is only permitted in an [unsafe](unsafe.md) context.</span></span> <span data-ttu-id="83ca2-106">`fixed` 키워드를 사용하여 [고정 크기 버퍼](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)를 만들수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83ca2-106">You can also use the `fixed` keyword to create [fixed size buffers](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>

<span data-ttu-id="83ca2-107">`fixed` 문은 관리되는 변수에 대한 포인터를 설정하고 문을 실행하는 동안 해당 변수를 "고정"합니다.</span><span class="sxs-lookup"><span data-stu-id="83ca2-107">The `fixed` statement sets a pointer to a managed variable and "pins" that variable during the execution of the statement.</span></span> <span data-ttu-id="83ca2-108">이동 가능한 관리되는 변수에 대한 포인터는 `fixed` 컨텍스트에만 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="83ca2-108">Pointers to movable managed variables are useful only in a `fixed` context.</span></span> <span data-ttu-id="83ca2-109">`fixed` 컨텍스트 없는 가비지 수집은 예기치 않게 변수를 재배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83ca2-109">Without a `fixed` context, garbage collection could relocate the variables unpredictably.</span></span> <span data-ttu-id="83ca2-110">C# 컴파일러만 `fixed` 문에서 관리되는 변수에 대한 포인터를 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83ca2-110">The C# compiler only lets you assign a pointer to a managed variable in a `fixed` statement.</span></span>

[!code-csharp[Accessing fixed memory](snippets/FixedKeywordExamples.cs#1)]

<span data-ttu-id="83ca2-111">배열, 문자열, 고정 크기 버퍼 또는 변수의 주소를 사용하여 포인터를 초기화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83ca2-111">You can initialize a pointer by using an array, a string, a fixed-size buffer, or the address of a variable.</span></span> <span data-ttu-id="83ca2-112">다음 예제에서는 변수 주소, 배열 및 문자열의 사용을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="83ca2-112">The following example illustrates the use of variable addresses, arrays, and strings:</span></span>

[!code-csharp[Initializing fixed size buffers](snippets/FixedKeywordExamples.cs#2)]

<span data-ttu-id="83ca2-113">C# 7.3부터 `fixed` 문은 배열, 문자열, 고정 크기 버퍼 또는 비관리형 변수 외의 추가 형식에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="83ca2-113">Starting with C# 7.3, the `fixed` statement operates on additional types beyond arrays, strings, fixed size buffers, or unmanaged variables.</span></span> <span data-ttu-id="83ca2-114">`GetPinnableReference` 메서드를 구현하는 모든 형식을 고정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83ca2-114">Any type that implements a method named `GetPinnableReference` can be pinned.</span></span> <span data-ttu-id="83ca2-115">`GetPinnableReference`는 `ref` 변수를 [비관리형 형식](../builtin-types/unmanaged-types.md)으로 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83ca2-115">The `GetPinnableReference` must return a `ref` variable of an [unmanaged type](../builtin-types/unmanaged-types.md).</span></span> <span data-ttu-id="83ca2-116">.NET Core 2.0에 도입된 .NET 형식 <xref:System.Span%601?displayProperty=nameWithType> 및 <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>은 이 패턴을 사용하며 고정될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83ca2-116">The .NET types <xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> introduced in .NET Core 2.0 make use of this pattern and can be pinned.</span></span> <span data-ttu-id="83ca2-117">이는 다음 예제에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83ca2-117">This is shown in the following example:</span></span>

[!code-csharp[Accessing fixed memory](snippets/FixedKeywordExamples.cs#FixedSpan)]

<span data-ttu-id="83ca2-118">이 패턴에 참여해야 하는 형식을 만드는 경우 패턴을 구현하는 예제는 <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="83ca2-118">If you are creating types that should participate in this pattern, see <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> for an example of implementing the pattern.</span></span>

<span data-ttu-id="83ca2-119">여러 개의 포인터가 모두 동일한 형식인 경우 하나의 명령문에서 초기화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83ca2-119">Multiple pointers can be initialized in one statement if they are all the same type:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

<span data-ttu-id="83ca2-120">형식이 다른 포인터를 초기화하려면 다음 예제와 같이 `fixed` 문을 중첩하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83ca2-120">To initialize pointers of different types, simply nest `fixed` statements, as shown in the following example.</span></span>

[!code-csharp[Initializing multiple pointers](snippets/FixedKeywordExamples.cs#3)]

<span data-ttu-id="83ca2-121">이 문의 코드를 실행하면 고정된 모든 변수가 고정 해제되고 가비지 수집됩니다.</span><span class="sxs-lookup"><span data-stu-id="83ca2-121">After the code in the statement is executed, any pinned variables are unpinned and subject to garbage collection.</span></span> <span data-ttu-id="83ca2-122">따라서 `fixed` 문 외부에서 해당 변수를 가리키지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="83ca2-122">Therefore, do not point to those variables outside the `fixed` statement.</span></span> <span data-ttu-id="83ca2-123">`fixed` 명령문 내에서 선언된 변수는 해당 명령문에 범위가 지정되어 다음을 더 쉽게 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="83ca2-123">The variables declared in the `fixed` statement are scoped to that statement, making this easier:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

<span data-ttu-id="83ca2-124">`fixed` 명령문에서 초기화된 포인터는 읽기 전용 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="83ca2-124">Pointers initialized in `fixed` statements are readonly variables.</span></span> <span data-ttu-id="83ca2-125">포인터 값을 수정하려는 경우 두 번째 포인터 변수를 선언하고 수정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83ca2-125">If you want to modify the pointer value, you must declare a second pointer variable, and modify that.</span></span> <span data-ttu-id="83ca2-126">`fixed` 명령문에서 선언된 변수는 을 수정될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="83ca2-126">The variable declared in the `fixed` statement cannot be modified:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```

<span data-ttu-id="83ca2-127">가비지 수집의 대상이 아니므로 고정할 필요가 없는 스택에서 메모리를 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83ca2-127">You can allocate memory on the stack, where it is not subject to garbage collection and therefore does not need to be pinned.</span></span> <span data-ttu-id="83ca2-128">이렇게 하려면 [`stackalloc` 식](../operators/stackalloc.md)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="83ca2-128">To do that, use a [`stackalloc` expression](../operators/stackalloc.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="83ca2-129">C# 언어 사양</span><span class="sxs-lookup"><span data-stu-id="83ca2-129">C# language specification</span></span>

<span data-ttu-id="83ca2-130">자세한 내용은 [C# 언어 사양](~/_csharplang/spec/introduction.md)의 [fixed 문](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="83ca2-130">For more information, see [The fixed statement](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="83ca2-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="83ca2-131">See also</span></span>

- [<span data-ttu-id="83ca2-132">C# 참조</span><span class="sxs-lookup"><span data-stu-id="83ca2-132">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="83ca2-133">C# 프로그래밍 가이드</span><span class="sxs-lookup"><span data-stu-id="83ca2-133">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="83ca2-134">C# 키워드</span><span class="sxs-lookup"><span data-stu-id="83ca2-134">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="83ca2-135">unsafe</span><span class="sxs-lookup"><span data-stu-id="83ca2-135">unsafe</span></span>](unsafe.md)
- [<span data-ttu-id="83ca2-136">포인터 형식</span><span class="sxs-lookup"><span data-stu-id="83ca2-136">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="83ca2-137">고정 크기 버퍼</span><span class="sxs-lookup"><span data-stu-id="83ca2-137">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
