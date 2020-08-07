---
title: 시퀀스
description: '데이터의 순서가 지정 된 컬렉션이 크고 모든 요소를 사용할 필요가 없는 경우 F # 시퀀스를 사용 하는 방법에 대해 알아봅니다.'
ms.date: 11/04/2019
ms.openlocfilehash: fa5073f33b9dae52371c249bfb257a2446b4d26a
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855324"
---
# <a name="sequences"></a><span data-ttu-id="d0863-103">시퀀스</span><span class="sxs-lookup"><span data-stu-id="d0863-103">Sequences</span></span>

<span data-ttu-id="d0863-104">*시퀀스* 는 단일 형식의 논리적 일련의 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-104">A *sequence* is a logical series of elements all of one type.</span></span> <span data-ttu-id="d0863-105">시퀀스는 광범위 하 고 정렬 된 데이터 컬렉션이 있지만 모든 요소를 반드시 사용할 필요는 없는 경우에 특히 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-105">Sequences are particularly useful when you have a large, ordered collection of data but do not necessarily expect to use all of the elements.</span></span> <span data-ttu-id="d0863-106">개별 시퀀스 요소는 필요에 따라 계산 되므로 모든 요소가 사용 되지 않는 상황에서 시퀀스는 목록 보다 더 나은 성능을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-106">Individual sequence elements are computed only as required, so a sequence can provide better performance than a list in situations in which not all the elements are used.</span></span> <span data-ttu-id="d0863-107">시퀀스는 `seq<'T>` 의 별칭인 형식으로 표현 됩니다 <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="d0863-107">Sequences are represented by the `seq<'T>` type, which is an alias for <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="d0863-108">따라서 인터페이스를 구현 하는 모든 .NET 형식을 <xref:System.Collections.Generic.IEnumerable%601> 시퀀스로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-108">Therefore, any .NET type that implements <xref:System.Collections.Generic.IEnumerable%601> interface can be used as a sequence.</span></span> <span data-ttu-id="d0863-109">[Seq 모듈](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684) 은 시퀀스와 관련 된 조작을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-109">The [Seq module](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684) provides support for manipulations involving sequences.</span></span>

> [!NOTE]
> <span data-ttu-id="d0863-110">F #에 대 한 docs.microsoft.com API 참조가 완전 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-110">The docs.microsoft.com API reference for F# is not complete.</span></span> <span data-ttu-id="d0863-111">끊어진 링크가 있는 경우 대신 [F # 핵심 라이브러리 설명서](https://fsharp.github.io/fsharp-core-docs/) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d0863-111">If you encounter any broken links, reference [F# Core Library Documentation](https://fsharp.github.io/fsharp-core-docs/) instead.</span></span>

## <a name="sequence-expressions"></a><span data-ttu-id="d0863-112">시퀀스 식</span><span class="sxs-lookup"><span data-stu-id="d0863-112">Sequence Expressions</span></span>

<span data-ttu-id="d0863-113">*시퀀스 식은* 시퀀스로 계산 되는 식입니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-113">A *sequence expression* is an expression that evaluates to a sequence.</span></span> <span data-ttu-id="d0863-114">시퀀스 식은 많은 폼을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-114">Sequence expressions can take a number of forms.</span></span> <span data-ttu-id="d0863-115">가장 간단한 형태는 범위를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-115">The simplest form specifies a range.</span></span> <span data-ttu-id="d0863-116">예를 `seq { 1 .. 5 }` 들어는 끝점 1과 5를 포함 하 여 다섯 개의 요소를 포함 하는 시퀀스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-116">For example, `seq { 1 .. 5 }` creates a sequence that contains five elements, including the endpoints 1 and 5.</span></span> <span data-ttu-id="d0863-117">두 개의 double 기간 사이에 증가 (또는 감소)를 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-117">You can also specify an increment (or decrement) between two double periods.</span></span> <span data-ttu-id="d0863-118">예를 들어 다음 코드는 10의 배수로 이루어진 시퀀스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-118">For example, the following code creates the sequence of multiples of 10.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1502.fs)]

<span data-ttu-id="d0863-119">시퀀스 식은 시퀀스의 값을 생성 하는 F # 식으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-119">Sequence expressions are made up of F# expressions that produce values of the sequence.</span></span> <span data-ttu-id="d0863-120">값을 프로그래밍 방식으로 생성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-120">You can also generate values programmatically:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1503.fs)]

<span data-ttu-id="d0863-121">이전 예제에서는 연산자를 사용 하 여 해당 `->` 값이 시퀀스의 일부가 될 식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-121">The previous sample uses the `->` operator, which allows you to specify an expression whose value will become a part of the sequence.</span></span> <span data-ttu-id="d0863-122">`->`뒤에 오는 코드의 모든 부분에서 값을 반환 하는 경우에만를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-122">You can only use `->` if every part of the code that follows it returns a value.</span></span>

<span data-ttu-id="d0863-123">또는 키워드를 지정 하 고 다음과 같은 옵션을 지정할 수 있습니다 `do` `yield` .</span><span class="sxs-lookup"><span data-stu-id="d0863-123">Alternatively, you can specify the `do` keyword, with an optional `yield` that follows:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1504.fs)]

<span data-ttu-id="d0863-124">다음 코드에서는 표를 나타내는 배열에 대 한 인덱스와 함께 좌표 쌍의 목록을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-124">The following code generates a list of coordinate pairs along with an index into an array that represents the grid.</span></span> <span data-ttu-id="d0863-125">첫 번째 식에는를 `for` `do` 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-125">Note that the first `for` expression requires a `do` to be specified.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1505.fs)]

<span data-ttu-id="d0863-126">`if`시퀀스에 사용 되는 식은 필터입니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-126">An `if` expression used in a sequence is a filter.</span></span> <span data-ttu-id="d0863-127">예를 들어, 형식이 인 함수를 포함 하 고 있다고 가정 하 고 소수 숫자만 포함 하는 시퀀스를 생성 하려면 `isprime` `int -> bool` 다음과 같이 시퀀스를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-127">For example, to generate a sequence of only prime numbers, assuming that you have a function `isprime` of type `int -> bool`, construct the sequence as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1506.fs)]

<span data-ttu-id="d0863-128">앞에서 설명한 것 처럼 `do` `else` 와 함께 이동 하는 분기가 없기 때문에이 필요 `if` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-128">As mentioned previously, `do` is required here because there is no `else` branch that goes with the `if`.</span></span> <span data-ttu-id="d0863-129">를 사용 하려고 하면 `->` 모든 분기에서 값을 반환 하지 않는다는 오류가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-129">If you try to use `->`, you'll get an error saying that not all branches return a value.</span></span>

## <a name="the-yield-keyword"></a><span data-ttu-id="d0863-130">`yield!` 키워드</span><span class="sxs-lookup"><span data-stu-id="d0863-130">The `yield!` keyword</span></span>

<span data-ttu-id="d0863-131">경우에 따라 요소의 시퀀스를 다른 시퀀스에 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-131">Sometimes, you may wish to include a sequence of elements into another sequence.</span></span> <span data-ttu-id="d0863-132">시퀀스를 다른 시퀀스 내에 포함 하려면 키워드를 사용 해야 합니다 `yield!` .</span><span class="sxs-lookup"><span data-stu-id="d0863-132">To include a sequence within another sequence, you'll need to use the `yield!` keyword:</span></span>

```fsharp
// Repeats '1 2 3 4 5' ten times
seq {
    for _ in 1..10 do
        yield! seq { 1; 2; 3; 4; 5}
}
```

<span data-ttu-id="d0863-133">를 고려 하는 또 다른 방법은 `yield!` 내부 시퀀스를 평면화 한 다음 포함 하는 시퀀스에이를 포함 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-133">Another way of thinking of `yield!` is that it flattens an inner sequence and then includes that in the containing sequence.</span></span>

<span data-ttu-id="d0863-134">`yield!`식에를 사용 하는 경우 다른 모든 단일 값은 키워드를 사용 해야 합니다 `yield` .</span><span class="sxs-lookup"><span data-stu-id="d0863-134">When `yield!` is used in an expression, all other single values must use the `yield` keyword:</span></span>

```fsharp
// Combine repeated values with their values
seq {
    for x in 1..10 do
        yield x
        yield! seq { for i in 1..x -> i}
}
```

<span data-ttu-id="d0863-135">이전 예제 에서만를 지정 `x` 하면 시퀀스에서 값을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-135">Specifying only `x` in the previous example will result in the sequence generating no values.</span></span>

## <a name="examples"></a><span data-ttu-id="d0863-136">예</span><span class="sxs-lookup"><span data-stu-id="d0863-136">Examples</span></span>

<span data-ttu-id="d0863-137">첫 번째 예에서는 반복, 필터 및 양보를 포함 하는 시퀀스 식을 사용 하 여 배열을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-137">The first example uses a sequence expression that contains an iteration, a filter, and a yield to generate an array.</span></span> <span data-ttu-id="d0863-138">이 코드는 1에서 100 사이의 일련 번호 시퀀스를 콘솔에 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-138">This code prints a sequence of prime numbers between 1 and 100 to the console.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1507.fs)]

<span data-ttu-id="d0863-139">다음 예에서는 두 개의 요소로 구성 된 튜플로 구성 된 곱하기 테이블을 만듭니다. 각 요소는 두 개의 요소와 제품으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-139">The following example creates a multiplication table that consists of tuples of three elements, each consisting of two factors and the product:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1508.fs)]

<span data-ttu-id="d0863-140">다음 예제에서는를 사용 하 여 `yield!` 개별 시퀀스를 단일 최종 시퀀스로 결합 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-140">The following example demonstrates the use of `yield!` to combine individual sequences into a single final sequence.</span></span> <span data-ttu-id="d0863-141">이 경우 이진 트리의 각 하위 트리에 대 한 시퀀스는 재귀적 함수에서 연결 되어 최종 시퀀스를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-141">In this case, the sequences for each subtree in a binary tree are concatenated in a recursive function to produce the final sequence.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1509.fs)]

## <a name="using-sequences"></a><span data-ttu-id="d0863-142">시퀀스 사용</span><span class="sxs-lookup"><span data-stu-id="d0863-142">Using Sequences</span></span>

<span data-ttu-id="d0863-143">시퀀스는 [목록과](lists.md)동일한 많은 기능을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-143">Sequences support many of the same functions as [lists](lists.md).</span></span> <span data-ttu-id="d0863-144">시퀀스는 키 생성 함수를 사용 하 여 그룹화 및 계산 등의 작업도 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-144">Sequences also support operations such as grouping and counting by using key-generating functions.</span></span> <span data-ttu-id="d0863-145">시퀀스는 버킷이라고을 추출 하는 더 다양 한 함수도 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-145">Sequences also support more diverse functions for extracting subsequences.</span></span>

<span data-ttu-id="d0863-146">목록, 배열, 집합 및 맵과 같은 많은 데이터 형식은 열거 가능한 컬렉션 이므로 암시적으로 시퀀스 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-146">Many data types, such as lists, arrays, sets, and maps are implicitly sequences because they are enumerable collections.</span></span> <span data-ttu-id="d0863-147">시퀀스를 인수로 사용 하는 함수는을 구현 하는 .NET 데이터 형식 외에도 일반적인 F # 데이터 형식과 함께 사용할 수 `System.Collections.Generic.IEnumerable<'T>` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-147">A function that takes a sequence as an argument works with any of the common F# data types, in addition to any .NET data type that implements `System.Collections.Generic.IEnumerable<'T>`.</span></span> <span data-ttu-id="d0863-148">목록을 인수로 사용 하는 함수와 대조 하 여 목록만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-148">Contrast this to a function that takes a list as an argument, which can only take lists.</span></span> <span data-ttu-id="d0863-149">형식은 `seq<'T>` 에 대 한 형식 약어입니다 `IEnumerable<'T>` .</span><span class="sxs-lookup"><span data-stu-id="d0863-149">The type `seq<'T>` is a type abbreviation for `IEnumerable<'T>`.</span></span> <span data-ttu-id="d0863-150">즉, `System.Collections.Generic.IEnumerable<'T>` F #의 배열, 목록, 집합 및 맵을 포함 하는 제네릭을 구현 하는 모든 형식 및 대부분의 .net 컬렉션 형식은 형식과 호환 되며 `seq` 시퀀스가 필요한 모든 곳에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-150">This means that any type that implements the generic `System.Collections.Generic.IEnumerable<'T>`, which includes arrays, lists, sets, and maps in F#, and also most .NET collection types, is compatible with the `seq` type and can be used wherever a sequence is expected.</span></span>

## <a name="module-functions"></a><span data-ttu-id="d0863-151">모듈 함수</span><span class="sxs-lookup"><span data-stu-id="d0863-151">Module Functions</span></span>

<span data-ttu-id="d0863-152">[Fsharp.core 네임 스페이스](https://msdn.microsoft.com/library/24f64e5f-5030-47d0-9759-8d3e398ed13f) 의 [Seq 모듈](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684) 에는 시퀀스 작업을 위한 함수가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-152">The [Seq module](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684) in the [Microsoft.FSharp.Collections namespace](https://msdn.microsoft.com/library/24f64e5f-5030-47d0-9759-8d3e398ed13f) contains functions for working with sequences.</span></span> <span data-ttu-id="d0863-153">이러한 함수는 모두 열거 가능 하므로 시퀀스로 처리 될 수 있기 때문에 목록, 배열, 맵 및 집합 에서도 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-153">These functions work with lists, arrays, maps, and sets as well, because all of those types are enumerable, and therefore can be treated as sequences.</span></span>

## <a name="creating-sequences"></a><span data-ttu-id="d0863-154">시퀀스 만들기</span><span class="sxs-lookup"><span data-stu-id="d0863-154">Creating Sequences</span></span>

<span data-ttu-id="d0863-155">앞에서 설명한 대로 시퀀스 식을 사용 하거나 특정 함수를 사용 하 여 시퀀스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-155">You can create sequences by using sequence expressions, as described previously, or by using certain functions.</span></span>

<span data-ttu-id="d0863-156">[Seq](https://msdn.microsoft.com/library/3c7f1c69-6117-4782-b2da-0e04d6854f59)를 사용 하 여 빈 시퀀스를 만들거나 [seq. singleton](https://msdn.microsoft.com/library/9b8cc460-a282-4ec5-b29a-630ab17e9de7)을 사용 하 여 지정 된 요소의 시퀀스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-156">You can create an empty sequence by using [Seq.empty](https://msdn.microsoft.com/library/3c7f1c69-6117-4782-b2da-0e04d6854f59), or you can create a sequence of just one specified element by using [Seq.singleton](https://msdn.microsoft.com/library/9b8cc460-a282-4ec5-b29a-630ab17e9de7).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet9.fs)]

<span data-ttu-id="d0863-157">[Seq.init](https://msdn.microsoft.com/library/059de69d-812c-4f8e-be86-88aa72101576) 를 사용 하 여 사용자가 제공 하는 함수를 사용 하 여 요소가 생성 되는 시퀀스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-157">You can use [Seq.init](https://msdn.microsoft.com/library/059de69d-812c-4f8e-be86-88aa72101576) to create a sequence for which the elements are created by using a function that you provide.</span></span> <span data-ttu-id="d0863-158">또한 시퀀스의 크기를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-158">You also provide a size for the sequence.</span></span> <span data-ttu-id="d0863-159">이 함수는 시퀀스를 반복할 때까지 요소가 생성 되지 않는다는 점을 제외 하 고는 [List.init](https://msdn.microsoft.com/library/dd38c096-0ea8-4858-be6b-794b90418b83)와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-159">This function is just like [List.init](https://msdn.microsoft.com/library/dd38c096-0ea8-4858-be6b-794b90418b83), except that the elements are not created until you iterate through the sequence.</span></span> <span data-ttu-id="d0863-160">다음 코드에서는를 사용 하는 방법을 보여 줍니다 `Seq.init` .</span><span class="sxs-lookup"><span data-stu-id="d0863-160">The following code illustrates the use of `Seq.init`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet10.fs)]

<span data-ttu-id="d0863-161">출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-161">The output is</span></span>

```console
0 10 20 30 40
```

<span data-ttu-id="d0863-162">[Seq.](https://msdn.microsoft.com/library/299cd4d9-be72-4511-aac8-089e1ddaac99) [&#60;&#62; 함수](https://msdn.microsoft.com/visualfsharpdocs/conceptual/seq.oflist%5b%27t%5d-function-%5bfsharp%5d)를 사용 하 여 배열 및 목록에서 시퀀스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-162">By using [Seq.ofArray](https://msdn.microsoft.com/library/299cd4d9-be72-4511-aac8-089e1ddaac99) and [Seq.ofList&#60;'T&#62; Function](https://msdn.microsoft.com/visualfsharpdocs/conceptual/seq.oflist%5b%27t%5d-function-%5bfsharp%5d), you can create sequences from arrays and lists.</span></span> <span data-ttu-id="d0863-163">그러나 캐스트 연산자를 사용 하 여 배열 및 목록을 시퀀스로 변환할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-163">However, you can also convert arrays and lists to sequences by using a cast operator.</span></span> <span data-ttu-id="d0863-164">다음 코드에서는 두 가지 방법을 모두 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-164">Both techniques are shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet11.fs)]

<span data-ttu-id="d0863-165">[Seq. 캐스트](https://msdn.microsoft.com/library/1d087db3-a8b2-41dd-8ddc-227544529334)를 사용 하 여에 정의 된 것과 같은 약하게 형식화 된 컬렉션에서 시퀀스를 만들 수 있습니다 `System.Collections` .</span><span class="sxs-lookup"><span data-stu-id="d0863-165">By using [Seq.cast](https://msdn.microsoft.com/library/1d087db3-a8b2-41dd-8ddc-227544529334), you can create a sequence from a weakly typed collection, such as those defined in `System.Collections`.</span></span> <span data-ttu-id="d0863-166">이러한 약하게 형식화 된 컬렉션은 요소 형식을 가지 `System.Object` 며 제네릭이 아닌 형식을 사용 하 여 열거 됩니다 `System.Collections.Generic.IEnumerable&#96;1` .</span><span class="sxs-lookup"><span data-stu-id="d0863-166">Such weakly typed collections have the element type `System.Object` and are enumerated by using the non-generic `System.Collections.Generic.IEnumerable&#96;1` type.</span></span> <span data-ttu-id="d0863-167">다음 코드에서는를 사용 하 여를 `Seq.cast` 시퀀스로 변환 하는 방법을 보여 줍니다 `System.Collections.ArrayList` .</span><span class="sxs-lookup"><span data-stu-id="d0863-167">The following code illustrates the use of `Seq.cast` to convert an `System.Collections.ArrayList` into a sequence.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet12.fs)]

<span data-ttu-id="d0863-168">[Seq.initInfinite](https://msdn.microsoft.com/library/d1804e53-da92-48ec-8d6e-57eaf4c62bef) 함수를 사용 하 여 무한 시퀀스를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-168">You can define infinite sequences by using the [Seq.initInfinite](https://msdn.microsoft.com/library/d1804e53-da92-48ec-8d6e-57eaf4c62bef) function.</span></span> <span data-ttu-id="d0863-169">이러한 시퀀스의 경우 요소의 인덱스에서 각 요소를 생성 하는 함수를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-169">For such a sequence, you provide a function that generates each element from the index of the element.</span></span> <span data-ttu-id="d0863-170">지연 계산으로 인해 무한 시퀀스를 사용할 수 있습니다. 요소는 지정 된 함수를 호출 하 여 필요에 따라 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-170">Infinite sequences are possible because of lazy evaluation; elements are created as needed by calling the function that you specify.</span></span> <span data-ttu-id="d0863-171">다음 코드 예제에서는 부동 소수점 숫자의 무한 시퀀스를 생성 합니다 .이 경우 연속 되는 정수의 사각형 reciprocals 교대로 반복 되는 연속 된 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-171">The following code example produces an infinite sequence of floating point numbers, in this case the alternating series of reciprocals of squares of successive integers.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet13.fs)]

<span data-ttu-id="d0863-172">[펼침](https://msdn.microsoft.com/library/7d9232fc-742e-42bc-bdf7-6f130f0eff21) 는 상태를 사용 하는 계산 함수에서 시퀀스를 생성 하 고 시퀀스의 각 후속 요소를 생성 하도록 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-172">[Seq.unfold](https://msdn.microsoft.com/library/7d9232fc-742e-42bc-bdf7-6f130f0eff21) generates a sequence from a computation function that takes a state and transforms it to produce each subsequent element in the sequence.</span></span> <span data-ttu-id="d0863-173">상태는 각 요소를 계산 하는 데 사용 되는 값 이며 각 요소가 계산 될 때 변경 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-173">The state is just a value that is used to compute each element, and can change as each element is computed.</span></span> <span data-ttu-id="d0863-174">에 대 한 두 번째 인수는 `Seq.unfold` 시퀀스를 시작 하는 데 사용 되는 초기 값입니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-174">The second argument to `Seq.unfold` is the initial value that is used to start the sequence.</span></span> <span data-ttu-id="d0863-175">`Seq.unfold`는 상태에 대해 옵션 유형을 사용 합니다 .이를 통해 값을 반환 하 여 시퀀스를 종료할 수 있습니다 `None` .</span><span class="sxs-lookup"><span data-stu-id="d0863-175">`Seq.unfold` uses an option type for the state, which enables you to terminate the sequence by returning the `None` value.</span></span> <span data-ttu-id="d0863-176">다음 코드에서는 `seq1` 작업에 의해 생성 되는 및 시퀀스의 두 가지 예를 보여 줍니다 `fib` `unfold` .</span><span class="sxs-lookup"><span data-stu-id="d0863-176">The following code shows two examples of sequences, `seq1` and `fib`, that are generated by an `unfold` operation.</span></span> <span data-ttu-id="d0863-177">첫 번째는 `seq1` 숫자를 20 개까지 포함 하는 간단한 시퀀스 일 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-177">The first, `seq1`, is just a simple sequence with numbers up to 20.</span></span> <span data-ttu-id="d0863-178">두 번째는를 사용 하 여 `fib` `unfold` 피보나치 시퀀스를 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-178">The second, `fib`, uses `unfold` to compute the Fibonacci sequence.</span></span> <span data-ttu-id="d0863-179">피보나치 시퀀스의 각 요소는 이전의 두 피보나치 번호의 합계 이므로 상태 값은 시퀀스의 이전 두 숫자로 구성 된 튜플입니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-179">Because each element in the Fibonacci sequence is the sum of the previous two Fibonacci numbers, the state value is a tuple that consists of the previous two numbers in the sequence.</span></span> <span data-ttu-id="d0863-180">초기 값은 `(1,1)` 시퀀스에서 처음 두 개의 숫자입니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-180">The initial value is `(1,1)`, the first two numbers in the sequence.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet14.fs)]

<span data-ttu-id="d0863-181">출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-181">The output is as follows:</span></span>

```console
The sequence seq1 contains numbers from 0 to 20.

0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20

The sequence fib contains Fibonacci numbers.

2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597
```

<span data-ttu-id="d0863-182">다음 코드는 무한 시퀀스의 값을 생성 하 고 계산 하기 위해 여기에 설명 된 다양 한 시퀀스 모듈 함수를 사용 하는 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-182">The following code is an example that uses many of the sequence module functions described here to generate and compute the values of infinite sequences.</span></span> <span data-ttu-id="d0863-183">코드를 실행 하는 데 몇 분 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-183">The code might take a few minutes to run.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet15.fs)]

## <a name="searching-and-finding-elements"></a><span data-ttu-id="d0863-184">요소 검색 및 찾기</span><span class="sxs-lookup"><span data-stu-id="d0863-184">Searching and Finding Elements</span></span>

<span data-ttu-id="d0863-185">시퀀스는 다음과 같은 목록에서 사용할 수 있는 기능을 지원 합니다. [seq. exists](https://msdn.microsoft.com/library/428c97bf-599d-4c39-a5b9-f8717c198ad1), [array.exists2](https://msdn.microsoft.com/library/efdf14a4-27f7-4dc1-9281-52639e66d565), seq. [Find](https://msdn.microsoft.com/library/02c21ecd-97e5-4e99-a4c1-b4d0b730b7d8), [seq. findindex](https://msdn.microsoft.com/library/96dfe86b-df15-4d92-8316-7cd6055e09f3), [Seq. pick](https://msdn.microsoft.com/library/a87bc771-55f7-43f9-94f9-33d8f9bf325d), [seq. trfind](https://msdn.microsoft.com/library/ac43c6f5-4dc7-4e9a-a222-00b5736aee47)및 [seq.](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a)</span><span class="sxs-lookup"><span data-stu-id="d0863-185">Sequences support functionality available with lists: [Seq.exists](https://msdn.microsoft.com/library/428c97bf-599d-4c39-a5b9-f8717c198ad1), [Seq.exists2](https://msdn.microsoft.com/library/efdf14a4-27f7-4dc1-9281-52639e66d565), [Seq.find](https://msdn.microsoft.com/library/02c21ecd-97e5-4e99-a4c1-b4d0b730b7d8), [Seq.findIndex](https://msdn.microsoft.com/library/96dfe86b-df15-4d92-8316-7cd6055e09f3), [Seq.pick](https://msdn.microsoft.com/library/a87bc771-55f7-43f9-94f9-33d8f9bf325d), [Seq.tryFind](https://msdn.microsoft.com/library/ac43c6f5-4dc7-4e9a-a222-00b5736aee47), and [Seq.tryFindIndex](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a).</span></span> <span data-ttu-id="d0863-186">시퀀스에 사용할 수 있는 이러한 함수 버전은 검색 되는 요소 까지만 시퀀스를 평가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-186">The versions of these functions that are available for sequences evaluate the sequence only up to the element that is being searched for.</span></span> <span data-ttu-id="d0863-187">예제는 [목록](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d0863-187">For examples, see [Lists](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d).</span></span>

## <a name="obtaining-subsequences"></a><span data-ttu-id="d0863-188">버킷이라고 가져오기</span><span class="sxs-lookup"><span data-stu-id="d0863-188">Obtaining Subsequences</span></span>

<span data-ttu-id="d0863-189">[Seq. 필터](https://msdn.microsoft.com/library/7f2e9850-a660-460c-9831-3bbff5613770) 및 [seq. 선택](https://msdn.microsoft.com/library/63b83b06-4b24-4239-bf69-a2c12d891395) 은 시퀀스 요소가 평가 될 때까지 필터링 및 선택이 발생 하지 않는다는 점을 제외 하면 목록에 사용할 수 있는 해당 함수와 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-189">[Seq.filter](https://msdn.microsoft.com/library/7f2e9850-a660-460c-9831-3bbff5613770) and [Seq.choose](https://msdn.microsoft.com/library/63b83b06-4b24-4239-bf69-a2c12d891395) are like the corresponding functions that are available for lists, except that the filtering and choosing does not occur until the sequence elements are evaluated.</span></span>

<span data-ttu-id="d0863-190">[Seq. truncate](https://msdn.microsoft.com/library/1892dfeb-308e-45e2-857a-3c3405d02244) 은 다른 시퀀스에서 시퀀스를 만들지만 시퀀스를 지정 된 수의 요소로 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-190">[Seq.truncate](https://msdn.microsoft.com/library/1892dfeb-308e-45e2-857a-3c3405d02244) creates a sequence from another sequence, but limits the sequence to a specified number of elements.</span></span> <span data-ttu-id="d0863-191">[Seq](https://msdn.microsoft.com/library/6e75f701-640b-4c4a-9d63-4313fc090596) 는 시퀀스의 시작 부분부터 지정 된 수의 요소만 포함 하는 새 시퀀스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-191">[Seq.take](https://msdn.microsoft.com/library/6e75f701-640b-4c4a-9d63-4313fc090596) creates a new sequence that contains only a specified number of elements from the start of a sequence.</span></span> <span data-ttu-id="d0863-192">시퀀스에 지정 된 것 보다 더 많은 요소가 있으면에서을 `Seq.take` throw `System.InvalidOperationException` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-192">If there are fewer elements in the sequence than you specify to take, `Seq.take` throws a `System.InvalidOperationException`.</span></span> <span data-ttu-id="d0863-193">와의 차이 `Seq.take` 는 `Seq.truncate` `Seq.truncate` 요소 수가 지정한 수보다 적으면에서 오류를 생성 하지 않는다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-193">The difference between `Seq.take` and `Seq.truncate` is that `Seq.truncate` does not produce an error if the number of elements is fewer than the number you specify.</span></span>

<span data-ttu-id="d0863-194">다음 코드에서는 및의 동작과의 차이점을 보여 `Seq.truncate` 줍니다 `Seq.take` .</span><span class="sxs-lookup"><span data-stu-id="d0863-194">The following code shows the behavior of and differences between `Seq.truncate` and `Seq.take`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet16.fs)]

<span data-ttu-id="d0863-195">오류가 발생 하기 전의 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-195">The output, before the error occurs, is as follows.</span></span>

```console
1 4 9 16 25
1 4 9 16 25 36 49 64 81 100
1 4 9 16 25
1 4 9 16 25 36 49 64 81 100
```

<span data-ttu-id="d0863-196">[TakeWhile](https://msdn.microsoft.com/library/19eea4ce-66e0-4353-b015-72eb03421d92)를 사용 하 여 조건자 함수 (부울 함수)를 지정 하 고 조건자가 인 원래 시퀀스의 요소로 구성 된 다른 시퀀스에서 시퀀스를 만든 다음 조건자가 반환 하는 `true` 첫 번째 요소 앞에서 중지할 수 있습니다 `false` .</span><span class="sxs-lookup"><span data-stu-id="d0863-196">By using [Seq.takeWhile](https://msdn.microsoft.com/library/19eea4ce-66e0-4353-b015-72eb03421d92), you can specify a predicate function (a Boolean function) and create a sequence from another sequence made up of those elements of the original sequence for which the predicate is `true`, but stop before the first element for which the predicate returns `false`.</span></span> <span data-ttu-id="d0863-197">[Seq. skip](https://msdn.microsoft.com/library/b4eb3f08-8594-4d17-8180-852c6c688bf1) 은 다른 시퀀스의 지정 된 수의 첫 번째 요소를 건너뛰고 나머지 요소를 반환 하는 시퀀스를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-197">[Seq.skip](https://msdn.microsoft.com/library/b4eb3f08-8594-4d17-8180-852c6c688bf1) returns a sequence that skips a specified number of the first elements of another sequence and returns the remaining elements.</span></span> <span data-ttu-id="d0863-198">[SkipWhile](https://msdn.microsoft.com/library/fb729021-2a3c-430f-83c3-0b37526f1a16) 는 조건자가 반환 되는 한 다른 시퀀스의 첫 번째 요소를 건너뛴 `true` 다음 조건자가 반환 하는 첫 번째 요소부터 시작 하 여 나머지 요소를 반환 하는 시퀀스를 반환 `false` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-198">[Seq.skipWhile](https://msdn.microsoft.com/library/fb729021-2a3c-430f-83c3-0b37526f1a16) returns a sequence that skips the first elements of another sequence as long as the predicate returns `true`, and then returns the remaining elements, starting with the first element for which the predicate returns `false`.</span></span>

<span data-ttu-id="d0863-199">다음 코드 예제에서는, 및의 차이점을 보여 줍니다 `Seq.takeWhile` `Seq.skip` `Seq.skipWhile` .</span><span class="sxs-lookup"><span data-stu-id="d0863-199">The following code example illustrates the behavior of and differences between `Seq.takeWhile`, `Seq.skip`, and `Seq.skipWhile`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet17.fs)]

<span data-ttu-id="d0863-200">출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-200">The output is as follows.</span></span>

```console
1 4 9
36 49 64 81 100
16 25 36 49 64 81 100
```

## <a name="transforming-sequences"></a><span data-ttu-id="d0863-201">시퀀스 변환</span><span class="sxs-lookup"><span data-stu-id="d0863-201">Transforming Sequences</span></span>

<span data-ttu-id="d0863-202">[Seq. 쌍](https://msdn.microsoft.com/library/210dcf26-4e24-4d83-af6d-a8288b2ae4b1) 은 입력 시퀀스의 연속 요소가 튜플로 그룹화 되는 새 시퀀스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-202">[Seq.pairwise](https://msdn.microsoft.com/library/210dcf26-4e24-4d83-af6d-a8288b2ae4b1) creates a new sequence in which successive elements of the input sequence are grouped into tuples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet18.fs)]

<span data-ttu-id="d0863-203">[Seq](https://msdn.microsoft.com/library/8b565b8f-d645-4dba-be22-099075fe4744) 는와 유사 합니다. `Seq.pairwise` 단, 튜플 시퀀스를 생성 하는 대신 시퀀스에서 인접 한 요소 ( *창*)의 복사본을 포함 하는 배열 시퀀스를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-203">[Seq.windowed](https://msdn.microsoft.com/library/8b565b8f-d645-4dba-be22-099075fe4744) is like `Seq.pairwise`, except that instead of producing a sequence of tuples, it produces a sequence of arrays that contain copies of adjacent elements (a *window*) from the sequence.</span></span> <span data-ttu-id="d0863-204">각 배열에 원하는 인접 요소 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-204">You specify the number of adjacent elements you want in each array.</span></span>

<span data-ttu-id="d0863-205">다음 코드 예제에서는 `Seq.windowed`의 사용법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-205">The following code example demonstrates the use of `Seq.windowed`.</span></span> <span data-ttu-id="d0863-206">이 경우 창의 요소 수는 3입니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-206">In this case the number of elements in the window is 3.</span></span> <span data-ttu-id="d0863-207">이 예제에서는 `printSeq` 앞의 코드 예제에서 정의 된를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-207">The example uses `printSeq`, which is defined in the previous code example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet180.fs)]

<span data-ttu-id="d0863-208">출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-208">The output is as follows.</span></span>

<span data-ttu-id="d0863-209">초기 시퀀스:</span><span class="sxs-lookup"><span data-stu-id="d0863-209">Initial sequence:</span></span>

```console
1.0 1.5 2.0 1.5 1.0 1.5

Windows of length 3:
[|1.0; 1.5; 2.0|] [|1.5; 2.0; 1.5|] [|2.0; 1.5; 1.0|] [|1.5; 1.0; 1.5|]

Moving average:
1.5 1.666666667 1.5 1.333333333
```

## <a name="operations-with-multiple-sequences"></a><span data-ttu-id="d0863-210">여러 시퀀스를 사용 하는 작업</span><span class="sxs-lookup"><span data-stu-id="d0863-210">Operations with Multiple Sequences</span></span>

<span data-ttu-id="d0863-211">[Seq.zip](https://msdn.microsoft.com/library/0a5df8bf-0d48-44ce-bff4-e8ef1df5bca4) 및 [Seq.zip3](https://msdn.microsoft.com/library/ef13bebb-22ae-4eb9-873b-87dd29154d16) 은 두 개 또는 세 개의 시퀀스를 사용 하 고 튜플 시퀀스를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-211">[Seq.zip](https://msdn.microsoft.com/library/0a5df8bf-0d48-44ce-bff4-e8ef1df5bca4) and [Seq.zip3](https://msdn.microsoft.com/library/ef13bebb-22ae-4eb9-873b-87dd29154d16) take two or three sequences and produce a sequence of tuples.</span></span> <span data-ttu-id="d0863-212">이러한 함수는 [목록](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d)에 사용할 수 있는 해당 함수와 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-212">These functions are like the corresponding functions available for [lists](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d).</span></span> <span data-ttu-id="d0863-213">한 시퀀스를 두 개 이상의 시퀀스로 분리 하는 기능이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-213">There is no corresponding functionality to separate one sequence into two or more sequences.</span></span> <span data-ttu-id="d0863-214">시퀀스에이 기능이 필요한 경우 시퀀스를 목록으로 변환 하 고 [list. 압축 풀기](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21)를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-214">If you need this functionality for a sequence, convert the sequence to a list and use [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).</span></span>

## <a name="sorting-comparing-and-grouping"></a><span data-ttu-id="d0863-215">정렬, 비교 및 그룹화</span><span class="sxs-lookup"><span data-stu-id="d0863-215">Sorting, Comparing, and Grouping</span></span>

<span data-ttu-id="d0863-216">목록에 대해 지원 되는 정렬 함수도 시퀀스와 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-216">The sorting functions supported for lists also work with sequences.</span></span> <span data-ttu-id="d0863-217">여기에는 [seq. sort](https://msdn.microsoft.com/library/327ea595-e77c-4529-b61e-8c6cbf5ec92e) 및 [sortBy](https://msdn.microsoft.com/library/4f8b4fb9-bf20-49d9-b4ee-dcc906c8208f)가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-217">This includes [Seq.sort](https://msdn.microsoft.com/library/327ea595-e77c-4529-b61e-8c6cbf5ec92e) and [Seq.sortBy](https://msdn.microsoft.com/library/4f8b4fb9-bf20-49d9-b4ee-dcc906c8208f).</span></span> <span data-ttu-id="d0863-218">이러한 함수는 전체 시퀀스를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-218">These functions iterate through the whole sequence.</span></span>

<span data-ttu-id="d0863-219">[Seq. compareWith](https://msdn.microsoft.com/library/5a740135-0b3a-4545-816f-8f91cc31290f) 함수를 사용 하 여 두 시퀀스를 비교 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-219">You compare two sequences by using the [Seq.compareWith](https://msdn.microsoft.com/library/5a740135-0b3a-4545-816f-8f91cc31290f) function.</span></span> <span data-ttu-id="d0863-220">함수는 연속 된 요소를 차례로 비교 하 고, 첫 번째 같지 않은 쌍을 발견할 경우 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-220">The function compares successive elements in turn, and stops when it encounters the first unequal pair.</span></span> <span data-ttu-id="d0863-221">추가 요소는 비교에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-221">Any additional elements do not contribute to the comparison.</span></span>

<span data-ttu-id="d0863-222">다음 코드는 `Seq.compareWith`의 사용법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-222">The following code shows the use of `Seq.compareWith`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet19.fs)]

<span data-ttu-id="d0863-223">위의 코드에서는 첫 번째 요소만 계산 및 검사 되 고 결과는-1입니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-223">In the previous code, only the first element is computed and examined, and the result is -1.</span></span>

<span data-ttu-id="d0863-224">[Seq.countby](https://msdn.microsoft.com/library/721702a5-150e-4fe8-81cd-ffbf8476cc1f) 는 각 요소에 대 한 *키* 라는 값을 생성 하는 함수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-224">[Seq.countBy](https://msdn.microsoft.com/library/721702a5-150e-4fe8-81cd-ffbf8476cc1f) takes a function that generates a value called a *key* for each element.</span></span> <span data-ttu-id="d0863-225">각 요소에 대해이 함수를 호출 하 여 각 요소에 대 한 키를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-225">A key is generated for each element by calling this function on each element.</span></span> <span data-ttu-id="d0863-226">`Seq.countBy`그런 다음는 키 값을 포함 하는 시퀀스와 키의 각 값을 생성 한 요소 수의 개수를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-226">`Seq.countBy` then returns a sequence that contains the key values, and a count of the number of elements that generated each value of the key.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet201.fs)]

<span data-ttu-id="d0863-227">출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-227">The output is as follows.</span></span>

```console
(1, 34) (2, 33) (0, 33)
```

<span data-ttu-id="d0863-228">위의 출력은 키 1, 키 2를 생성 한 33 값 및 키 0을 생성 한 33 값을 생성 한 원래 시퀀스의 요소가 34 개 있음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-228">The previous output shows that there were 34 elements of the original sequence that produced the key 1, 33 values that produced the key 2, and 33 values that produced the key 0.</span></span>

<span data-ttu-id="d0863-229">[Seq. groupBy](https://msdn.microsoft.com/library/d46a04df-1a42-40cc-a368-058c9c5806fd)를 호출 하 여 시퀀스의 요소를 그룹화 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-229">You can group elements of a sequence by calling [Seq.groupBy](https://msdn.microsoft.com/library/d46a04df-1a42-40cc-a368-058c9c5806fd).</span></span> <span data-ttu-id="d0863-230">`Seq.groupBy`요소에서 키를 생성 하는 시퀀스 및 함수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-230">`Seq.groupBy` takes a sequence and a function that generates a key from an element.</span></span> <span data-ttu-id="d0863-231">함수는 시퀀스의 각 요소에 대해 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-231">The function is executed on each element of the sequence.</span></span> <span data-ttu-id="d0863-232">`Seq.groupBy`각 튜플의 첫 번째 요소가 키이 고 두 번째 요소가 해당 키를 생성 하는 요소의 시퀀스인 경우 튜플 시퀀스를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-232">`Seq.groupBy` returns a sequence of tuples, where the first element of each tuple is the key and the second is a sequence of elements that produce that key.</span></span>

<span data-ttu-id="d0863-233">다음 코드 예제에서는를 사용 하 여 `Seq.groupBy` 1에서 100 사이의 숫자 시퀀스를 고유 키 값이 0, 1, 2 인 세 개의 그룹으로 분할 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-233">The following code example shows the use of `Seq.groupBy` to partition the sequence of numbers from 1 to 100 into three groups that have the distinct key values 0, 1, and 2.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet202.fs)]

<span data-ttu-id="d0863-234">출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-234">The output is as follows.</span></span>

```console
(1, seq [1; 4; 7; 10; ...]) (2, seq [2; 5; 8; 11; ...]) (0, seq [3; 6; 9; 12; ...])
```

<span data-ttu-id="d0863-235">[Seq](https://msdn.microsoft.com/library/99d01014-7e0e-4e7b-9d0a-41a61d93f401)를 호출 하 여 중복 요소를 제거 하는 시퀀스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-235">You can create a sequence that eliminates duplicate elements by calling [Seq.distinct](https://msdn.microsoft.com/library/99d01014-7e0e-4e7b-9d0a-41a61d93f401).</span></span> <span data-ttu-id="d0863-236">또는 각 요소에서 키 생성 함수를 호출 하는 [seq.distinctby](https://msdn.microsoft.com/library/9293293b-9420-49c8-848f-401a9cd49b75)를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-236">Or you can use [Seq.distinctBy](https://msdn.microsoft.com/library/9293293b-9420-49c8-848f-401a9cd49b75), which takes a key-generating function to be called on each element.</span></span> <span data-ttu-id="d0863-237">결과 시퀀스에는 고유 키가 있는 원래 시퀀스의 요소가 포함 됩니다. 이전 요소에 대 한 중복 키를 생성 하는 이후 요소는 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-237">The resulting sequence contains elements of the original sequence that have unique keys; later elements that produce a duplicate key to an earlier element are discarded.</span></span>

<span data-ttu-id="d0863-238">다음 코드 예제에서는를 사용 하는 방법을 보여 줍니다 `Seq.distinct` .</span><span class="sxs-lookup"><span data-stu-id="d0863-238">The following code example illustrates the use of `Seq.distinct`.</span></span> <span data-ttu-id="d0863-239">`Seq.distinct`이진 숫자를 나타내는 시퀀스를 생성 한 다음 유일한 고유 요소만 0과 1 임을 보여 주는 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-239">`Seq.distinct` is demonstrated by generating sequences that represent binary numbers, and then showing that the only distinct elements are 0 and 1.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet22.fs)]

<span data-ttu-id="d0863-240">다음 코드에서는 `Seq.distinctBy` 음수 및 양수가 포함 된 시퀀스를 시작 하 고 절대 값 함수를 키 생성 함수로 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-240">The following code demonstrates `Seq.distinctBy` by starting with a sequence that contains negative and positive numbers and using the absolute value function as the key-generating function.</span></span> <span data-ttu-id="d0863-241">음수는 시퀀스에서 앞에 표시 되 고 동일한 절대값 또는 키를 갖는 양수 대신 선택 되므로 시퀀스의 음수에 해당 하는 모든 양수가 결과 시퀀스에 누락 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-241">The resulting sequence is missing all the positive numbers that correspond to the negative numbers in the sequence, because the negative numbers appear earlier in the sequence and therefore are selected instead of the positive numbers that have the same absolute value, or key.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet23.fs)]

## <a name="readonly-and-cached-sequences"></a><span data-ttu-id="d0863-242">읽기 전용 및 캐시 된 시퀀스</span><span class="sxs-lookup"><span data-stu-id="d0863-242">Readonly and Cached Sequences</span></span>

<span data-ttu-id="d0863-243">[Seq. readonly](https://msdn.microsoft.com/library/88059cb4-3bb0-4126-9448-fbcd48fe13a7) 는 시퀀스의 읽기 전용 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-243">[Seq.readonly](https://msdn.microsoft.com/library/88059cb4-3bb0-4126-9448-fbcd48fe13a7) creates a read-only copy of a sequence.</span></span> <span data-ttu-id="d0863-244">`Seq.readonly`는 배열과 같은 읽기/쓰기 컬렉션이 있고 원래 컬렉션을 수정 하지 않으려는 경우에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-244">`Seq.readonly` is useful when you have a read-write collection, such as an array, and you do not want to modify the original collection.</span></span> <span data-ttu-id="d0863-245">이 함수는 데이터 캡슐화를 유지 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-245">This function can be used to preserve data encapsulation.</span></span> <span data-ttu-id="d0863-246">다음 코드 예제에서는 배열을 포함 하는 형식이 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-246">In the following code example, a type that contains an array is created.</span></span> <span data-ttu-id="d0863-247">속성은 배열을 노출 하지만 배열을 반환 하는 대신를 사용 하 여 배열에서 만든 시퀀스를 반환 합니다 `Seq.readonly` .</span><span class="sxs-lookup"><span data-stu-id="d0863-247">A property exposes the array, but instead of returning an array, it returns a sequence that is created from the array by using `Seq.readonly`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet24.fs)]

<span data-ttu-id="d0863-248">[Seq. cache](https://msdn.microsoft.com/library/d197f9cc-08bf-4986-9869-246e72ca73f0) 는 시퀀스의 저장 된 버전을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-248">[Seq.cache](https://msdn.microsoft.com/library/d197f9cc-08bf-4986-9869-246e72ca73f0) creates a stored version of a sequence.</span></span> <span data-ttu-id="d0863-249">를 사용 `Seq.cache` 하 여 시퀀스의 재평가를 방지 하거나 시퀀스를 사용 하는 스레드가 여러 개 있는 경우 각 요소가 한 번만 처리 되도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-249">Use `Seq.cache` to avoid reevaluation of a sequence, or when you have multiple threads that use a sequence, but you must make sure that each element is acted upon only one time.</span></span> <span data-ttu-id="d0863-250">여러 스레드에서 사용 되는 시퀀스를 사용 하는 경우 원래 시퀀스에 대 한 값을 열거 하 고 계산 하는 하나의 스레드를 사용 하 고 나머지 스레드는 캐시 된 시퀀스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-250">When you have a sequence that is being used by multiple threads, you can have one thread that enumerates and computes the values for the original sequence, and remaining threads can use the cached sequence.</span></span>

## <a name="performing-computations-on-sequences"></a><span data-ttu-id="d0863-251">시퀀스에 대 한 계산 수행</span><span class="sxs-lookup"><span data-stu-id="d0863-251">Performing Computations on Sequences</span></span>

<span data-ttu-id="d0863-252">간단한 산술 연산은 [seq. average](https://msdn.microsoft.com/library/609d793b-c70f-4e36-9ab4-d928056d65b8), [seq. sum](https://msdn.microsoft.com/library/01208515-4880-4358-91f5-af34f66dc77a), [Array.averageby](https://msdn.microsoft.com/library/47c855c1-2dbd-415a-885e-b909d9d3e4f8), [seq. sumby](https://msdn.microsoft.com/library/68cca78c-94ed-4a45-9b8d-34d2c5f2b1b1)등의 목록에서와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-252">Simple arithmetic operations are like those of lists, such as [Seq.average](https://msdn.microsoft.com/library/609d793b-c70f-4e36-9ab4-d928056d65b8), [Seq.sum](https://msdn.microsoft.com/library/01208515-4880-4358-91f5-af34f66dc77a), [Seq.averageBy](https://msdn.microsoft.com/library/47c855c1-2dbd-415a-885e-b909d9d3e4f8), [Seq.sumBy](https://msdn.microsoft.com/library/68cca78c-94ed-4a45-9b8d-34d2c5f2b1b1), and so on.</span></span>

<span data-ttu-id="d0863-253">[Seq. 접기](https://msdn.microsoft.com/library/30c4c95a-9563-4c96-bbe1-f7aacfd026e3), [seq. 감소](https://msdn.microsoft.com/library/a2ad4f64-ac69-47d2-92f0-7173d9dfeae9)및 [seq. scan](https://msdn.microsoft.com/library/7e2d23e9-f153-4411-a884-b6d415ff627e) 은 목록에 사용할 수 있는 해당 함수와 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-253">[Seq.fold](https://msdn.microsoft.com/library/30c4c95a-9563-4c96-bbe1-f7aacfd026e3), [Seq.reduce](https://msdn.microsoft.com/library/a2ad4f64-ac69-47d2-92f0-7173d9dfeae9), and [Seq.scan](https://msdn.microsoft.com/library/7e2d23e9-f153-4411-a884-b6d415ff627e) are like the corresponding functions that are available for lists.</span></span> <span data-ttu-id="d0863-254">시퀀스는 지원을 나열 하는 이러한 함수의 전체 변형 하위 집합을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0863-254">Sequences support a subset of the full variations of these functions that lists support.</span></span> <span data-ttu-id="d0863-255">자세한 내용 및 예제는 [목록](lists.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="d0863-255">For more information and examples, see [Lists](lists.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d0863-256">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d0863-256">See also</span></span>

- [<span data-ttu-id="d0863-257">F# 언어 참조</span><span class="sxs-lookup"><span data-stu-id="d0863-257">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="d0863-258">F# 형식</span><span class="sxs-lookup"><span data-stu-id="d0863-258">F# Types</span></span>](fsharp-types.md)
