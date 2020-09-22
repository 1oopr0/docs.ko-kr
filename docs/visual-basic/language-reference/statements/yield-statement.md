---
title: Yield 문
ms.date: 07/20/2015
f1_keywords:
- vb.Yield
helpviewer_keywords:
- iterators, Yield statement [Visual Basic]
- iterators [Visual Basic]
- Yield statement [Visual Basic]
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
ms.openlocfilehash: 783785f2a078b6ad8f975846c44ee4e716a12773
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866498"
---
# <a name="yield-statement-visual-basic"></a><span data-ttu-id="7aa2c-102">Yield 문(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7aa2c-102">Yield Statement (Visual Basic)</span></span>

<span data-ttu-id="7aa2c-103">컬렉션의 다음 요소를 `For Each...Next` 문으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="7aa2c-103">Sends the next element of a collection to a `For Each...Next` statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7aa2c-104">구문</span><span class="sxs-lookup"><span data-stu-id="7aa2c-104">Syntax</span></span>  
  
```vb  
Yield expression  
```  
  
## <a name="parameters"></a><span data-ttu-id="7aa2c-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7aa2c-105">Parameters</span></span>  
  
|<span data-ttu-id="7aa2c-106">용어</span><span class="sxs-lookup"><span data-stu-id="7aa2c-106">Term</span></span>|<span data-ttu-id="7aa2c-107">정의</span><span class="sxs-lookup"><span data-stu-id="7aa2c-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="7aa2c-108">필수 요소.</span><span class="sxs-lookup"><span data-stu-id="7aa2c-108">Required.</span></span> <span data-ttu-id="7aa2c-109">`Get`문을 포함 하는 반복기 함수 또는 접근자의 형식으로 암시적으로 변환할 수 있는 식입니다 `Yield` .</span><span class="sxs-lookup"><span data-stu-id="7aa2c-109">An expression that is implicitly convertible to the type of the iterator function or `Get` accessor that contains the `Yield` statement.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7aa2c-110">설명</span><span class="sxs-lookup"><span data-stu-id="7aa2c-110">Remarks</span></span>  

 <span data-ttu-id="7aa2c-111">`Yield`문은 한 번에 한 컬렉션의 요소를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="7aa2c-111">The `Yield` statement returns one element of a collection at a time.</span></span> <span data-ttu-id="7aa2c-112">`Yield`문은 `Get` 컬렉션에 대해 사용자 지정 반복을 수행 하는 반복기 함수 또는 접근자에 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7aa2c-112">The `Yield` statement is included in an iterator function or `Get` accessor, which perform custom iterations over a collection.</span></span>  
  
 <span data-ttu-id="7aa2c-113">For Each ...를 사용 하 여 반복기 함수를 사용 합니다. [ 다음 문](for-each-next-statement.md) 또는 LINQ 쿼리입니다.</span><span class="sxs-lookup"><span data-stu-id="7aa2c-113">You consume an iterator function by using a [For Each...Next Statement](for-each-next-statement.md) or a LINQ query.</span></span> <span data-ttu-id="7aa2c-114">루프의 각 반복 `For Each` 은 반복기 함수를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="7aa2c-114">Each iteration of the `For Each` loop calls the iterator function.</span></span> <span data-ttu-id="7aa2c-115">`Yield`반복기 함수에서 문이 도달 하면 `expression` 이 반환 되 고 코드에서 현재 위치는 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7aa2c-115">When a `Yield` statement is reached in the iterator function, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="7aa2c-116">다음에 반복기 함수가 호출되면 해당 위치에서 실행이 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="7aa2c-116">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="7aa2c-117">문의 형식에서 `expression` `Yield` 반복기의 반환 형식으로 암시적 변환이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7aa2c-117">An implicit conversion must exist from the type of `expression` in the `Yield` statement to the return type of the iterator.</span></span>  
  
 <span data-ttu-id="7aa2c-118">`Exit Function`또는 문을 사용 하 여 `Return` 반복을 종료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7aa2c-118">You can use an `Exit Function` or `Return` statement to end the iteration.</span></span>  
  
 <span data-ttu-id="7aa2c-119">"Yield"는 예약 된 단어가 아니므로 함수 또는 접근자에서 사용 되는 경우에만 특별 한 의미가 있습니다 `Iterator` `Get` .</span><span class="sxs-lookup"><span data-stu-id="7aa2c-119">"Yield" is not a reserved word and has special meaning only when it is used in an `Iterator` function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="7aa2c-120">반복기 함수 및 접근자에 대 한 자세한 내용은 `Get` [반복기](../../programming-guide/concepts/iterators.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7aa2c-120">For more information about iterator functions and `Get` accessors, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="iterator-functions-and-get-accessors"></a><span data-ttu-id="7aa2c-121">반복기 함수 및 Get 접근자</span><span class="sxs-lookup"><span data-stu-id="7aa2c-121">Iterator Functions and Get Accessors</span></span>  

 <span data-ttu-id="7aa2c-122">반복기 함수 또는 접근자의 선언은 `Get` 다음 요구 사항을 충족 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7aa2c-122">The declaration of an iterator function or `Get` accessor must meet the following requirements:</span></span>  
  
- <span data-ttu-id="7aa2c-123">[반복기](../modifiers/iterator.md) 한정자를 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7aa2c-123">It must include an [Iterator](../modifiers/iterator.md) modifier.</span></span>  
  
- <span data-ttu-id="7aa2c-124">반환 형식은 <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, 또는 <xref:System.Collections.Generic.IEnumerator%601>여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7aa2c-124">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
- <span data-ttu-id="7aa2c-125">`ByRef`매개 변수를 가질 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7aa2c-125">It cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="7aa2c-126">반복기 함수는 이벤트, 인스턴스 생성자, 정적 생성자 또는 정적 소멸자에서 발생할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7aa2c-126">An iterator function cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="7aa2c-127">반복기 함수는 익명 함수 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7aa2c-127">An iterator function can be an anonymous function.</span></span> <span data-ttu-id="7aa2c-128">자세한 내용은 [반복기](../../programming-guide/concepts/iterators.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7aa2c-128">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="7aa2c-129">예외 처리</span><span class="sxs-lookup"><span data-stu-id="7aa2c-129">Exception Handling</span></span>  

 <span data-ttu-id="7aa2c-130">`Yield`문은 `Try` Try ...의 블록 내부에 있을 수 있습니다. [ Catch ... Finally 문](try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7aa2c-130">A `Yield` statement can be inside a `Try` block of a [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span></span> <span data-ttu-id="7aa2c-131">`Try`문이 있는 블록은 블록 `Yield` 을 포함할 수 있으며 블록을 `Catch` 포함할 수 있습니다 `Finally` .</span><span class="sxs-lookup"><span data-stu-id="7aa2c-131">A `Try` block that has a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.</span></span>  
  
 <span data-ttu-id="7aa2c-132">`Yield`문은 `Catch` 블록이 나 블록 안에 있을 수 없습니다 `Finally` .</span><span class="sxs-lookup"><span data-stu-id="7aa2c-132">A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.</span></span>  
  
 <span data-ttu-id="7aa2c-133">`For Each`본문 (반복기 함수 외부)에서 예외를 throw 하는 경우 `Catch` 반복기 함수의 블록이 실행 되지 않지만 `Finally` 반복기 함수의 블록이 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7aa2c-133">If the `For Each` body (outside of the iterator function) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed.</span></span> <span data-ttu-id="7aa2c-134">`Catch`반복기 함수 내의 블록은 반복기 함수 내에서 발생 하는 예외만 catch 합니다.</span><span class="sxs-lookup"><span data-stu-id="7aa2c-134">A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.</span></span>  
  
## <a name="technical-implementation"></a><span data-ttu-id="7aa2c-135">기술 구현</span><span class="sxs-lookup"><span data-stu-id="7aa2c-135">Technical Implementation</span></span>  

 <span data-ttu-id="7aa2c-136">다음 코드는 `IEnumerable (Of String)` 반복기 함수에서을 반환 하 고의 요소를 반복 합니다 `IEnumerable (Of String)` .</span><span class="sxs-lookup"><span data-stu-id="7aa2c-136">The following code returns an `IEnumerable (Of String)` from an iterator function and then iterates through the elements of the `IEnumerable (Of String)`.</span></span>  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 <span data-ttu-id="7aa2c-137">에 대 한 호출은 `MyIteratorFunction` 함수 본문을 실행 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7aa2c-137">The call to `MyIteratorFunction` doesn't execute the body of the function.</span></span> <span data-ttu-id="7aa2c-138">대신에 `IEnumerable(Of String)` 변수에 `elements`을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7aa2c-138">Instead the call returns an `IEnumerable(Of String)` into the `elements` variable.</span></span>  
  
 <span data-ttu-id="7aa2c-139">`For Each` 루프 반복에서 <xref:System.Collections.IEnumerator.MoveNext%2A>에 대한 `elements` 메서드가 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="7aa2c-139">On an iteration of the `For Each` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="7aa2c-140">이 호출은 다음 `MyIteratorFunction` 문에 도달할 때까지 `Yield` 본문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7aa2c-140">This call executes the body of `MyIteratorFunction` until the next `Yield` statement is reached.</span></span> <span data-ttu-id="7aa2c-141">`Yield`문은 `element` 루프 본문에서 사용 하는 변수 값 뿐만 아니라 <xref:System.Collections.Generic.IEnumerator%601.Current%2A> 요소의 속성인를 결정 하는 식을 반환 합니다 `IEnumerable (Of String)` .</span><span class="sxs-lookup"><span data-stu-id="7aa2c-141">The `Yield` statement returns an expression that determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of elements, which is an `IEnumerable (Of String)`.</span></span>  
  
 <span data-ttu-id="7aa2c-142">이후에 `For Each` 루프가 반복될 때마다 중지되었던 위치에서 반복기 본문 실행이 계속되고 `Yield` 문에 도달하면 다시 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="7aa2c-142">On each subsequent iteration of the `For Each` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `Yield` statement.</span></span> <span data-ttu-id="7aa2c-143">`For Each`루프는 반복기 함수 또는 또는 문의 끝에 도달 하면 완료 `Return` 됩니다 `Exit Function` .</span><span class="sxs-lookup"><span data-stu-id="7aa2c-143">The `For Each` loop completes when the end of the iterator function or a `Return` or `Exit Function` statement is reached.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7aa2c-144">예제</span><span class="sxs-lookup"><span data-stu-id="7aa2c-144">Example</span></span>  

 <span data-ttu-id="7aa2c-145">다음 예제에는 `Yield` [에 대 한 내부 문이 있습니다. Next](for-next-statement.md) 루프.</span><span class="sxs-lookup"><span data-stu-id="7aa2c-145">The following example has a `Yield` statement that is inside a [For…Next](for-next-statement.md) loop.</span></span> <span data-ttu-id="7aa2c-146">의 각 문 본문 [에 대 한](for-each-next-statement.md) 각 반복은 `Main` 반복기 함수에 대 한 호출을 만듭니다 `Power` .</span><span class="sxs-lookup"><span data-stu-id="7aa2c-146">Each iteration of the [For Each](for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="7aa2c-147">반복기 함수를 호출할 때마다 다음에 `Yield` 루프를 반복하는 도중에 `For…Next` 문이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="7aa2c-147">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 <span data-ttu-id="7aa2c-148">반복기 메서드의 반환 형식은 <xref:System.Collections.Generic.IEnumerable%601> 반복기 인터페이스 형식인입니다.</span><span class="sxs-lookup"><span data-stu-id="7aa2c-148">The return type of the iterator method is <xref:System.Collections.Generic.IEnumerable%601>, an iterator interface type.</span></span> <span data-ttu-id="7aa2c-149">반복기 메서드가 호출되면 숫자의 거듭제곱이 들어 있는 열거형 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7aa2c-149">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a><span data-ttu-id="7aa2c-150">예제</span><span class="sxs-lookup"><span data-stu-id="7aa2c-150">Example</span></span>  

 <span data-ttu-id="7aa2c-151">다음 예제는 반복기인 `Get` 접근자에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7aa2c-151">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="7aa2c-152">속성 선언에 한정자가 포함 되어 있습니다 `Iterator` .</span><span class="sxs-lookup"><span data-stu-id="7aa2c-152">The property declaration includes an `Iterator` modifier.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 <span data-ttu-id="7aa2c-153">추가 예제는 [반복기](../../programming-guide/concepts/iterators.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7aa2c-153">For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7aa2c-154">참조</span><span class="sxs-lookup"><span data-stu-id="7aa2c-154">See also</span></span>

- [<span data-ttu-id="7aa2c-155">문</span><span class="sxs-lookup"><span data-stu-id="7aa2c-155">Statements</span></span>](index.md)
