---
title: 함수
description: F#의 함수 및 F#에서 일반적인 함수 프로그래밍 구문을 지원하는 방법에 대해 알아보세요.
ms.date: 05/16/2016
ms.openlocfilehash: e49183e0634dee1750757abadbfe9e9c824f51a8
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596476"
---
# <a name="functions"></a><span data-ttu-id="dd544-103">함수</span><span class="sxs-lookup"><span data-stu-id="dd544-103">Functions</span></span>

<span data-ttu-id="dd544-104">함수는 모든 프로그래밍 언어에서 프로그램 실행의 기본 단위입니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-104">Functions are the fundamental unit of program execution in any programming language.</span></span> <span data-ttu-id="dd544-105">다른 언어와 마찬가지로 F# 함수는 이름을 가지며, 매개 변수 및 인수를 사용할 수 있고, 본문을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-105">As in other languages, an F# function has a name, can have parameters and take arguments, and has a body.</span></span> <span data-ttu-id="dd544-106">또한 F#은 함수를 값으로 처리, 식에 명명되지 않은 함수 사용, 함수를 합성하여 새로운 함수 생성, 커리된 함수, 함수 인수를 부분적으로 적용하는 방식의 암시적 함수 정의 등 함수형 프로그래밍 구문도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-106">F# also supports functional programming constructs such as treating functions as values, using unnamed functions in expressions, composition of functions to form new functions, curried functions, and the implicit definition of functions by way of the partial application of function arguments.</span></span>

<span data-ttu-id="dd544-107">`let` 키워드 또는 `let rec` 키워드 조합(함수가 재귀적인 경우)을 사용하여 함수를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-107">You define functions by using the `let` keyword, or, if the function is recursive, the `let rec` keyword combination.</span></span>

## <a name="syntax"></a><span data-ttu-id="dd544-108">구문</span><span class="sxs-lookup"><span data-stu-id="dd544-108">Syntax</span></span>

```fsharp
// Non-recursive function definition.
let [inline] function-name parameter-list [ : return-type ] = function-body
// Recursive function definition.
let rec function-name parameter-list = recursive-function-body
```

## <a name="remarks"></a><span data-ttu-id="dd544-109">설명</span><span class="sxs-lookup"><span data-stu-id="dd544-109">Remarks</span></span>

<span data-ttu-id="dd544-110">*function-name*은 함수를 나타내는 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-110">The *function-name* is an identifier that represents the function.</span></span> <span data-ttu-id="dd544-111">*parameter-list*는 공백으로 구분되는 연속 매개 변수로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-111">The *parameter-list* consists of successive parameters that are separated by spaces.</span></span> <span data-ttu-id="dd544-112">매개 변수 섹션에 설명된 대로 각 매개 변수에 대해 명시적 형식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-112">You can specify an explicit type for each parameter, as described in the Parameters section.</span></span> <span data-ttu-id="dd544-113">특정 인수 형식을 지정하지 않으면 컴파일러가 함수 본문에서 형식을 유추하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-113">If you do not specify a specific argument type, the compiler attempts to infer the type from the function body.</span></span> <span data-ttu-id="dd544-114">*함수 본문*은 식으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-114">The *function-body* consists of an expression.</span></span> <span data-ttu-id="dd544-115">함수 본문을 구성하는 식은 일반적으로 여러 식으로 구성된 복합 식이며, 복합 식은 반환 값이 되는 최종 식으로 수렴됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-115">The expression that makes up the function body is typically a compound expression consisting of a number of expressions that culminate in a final expression that is the return value.</span></span> <span data-ttu-id="dd544-116">*반환 형식*은 그 뒤에 콜론이 나오며 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-116">The *return-type* is a colon followed by a type and is optional.</span></span> <span data-ttu-id="dd544-117">반환 값의 형식을 명시적으로 지정하지 않으면 컴파일러가 최종 식에서 반환 형식을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-117">If you do not specify the type of the return value explicitly, the compiler determines the return type from the final expression.</span></span>

<span data-ttu-id="dd544-118">간단한 함수 정의는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-118">A simple function definition resembles the following:</span></span>

```fsharp
let f x = x + 1
```

<span data-ttu-id="dd544-119">앞의 예제에서 함수 이름은 `f`이고, 인수는 `x`이고 그 형식은 `int`이며, 함수 본문은 `x + 1`이고, 반환 값의 형식은 `int`입니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-119">In the previous example, the function name is `f`, the argument is `x`, which has type `int`, the function body is `x + 1`, and the return value is of type `int`.</span></span>

<span data-ttu-id="dd544-120">함수를 `inline`으로 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-120">Functions can be marked `inline`.</span></span> <span data-ttu-id="dd544-121">`inline`에 대한 내용은 [인라인 함수](inline-functions.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dd544-121">For information about `inline`, see [Inline Functions](inline-functions.md).</span></span>

## <a name="scope"></a><span data-ttu-id="dd544-122">Scope</span><span class="sxs-lookup"><span data-stu-id="dd544-122">Scope</span></span>

<span data-ttu-id="dd544-123">모듈 범위 이외의 모든 범위 수준에서 값 또는 함수 이름을 다시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-123">At any level of scope other than module scope, it is not an error to reuse a value or function name.</span></span> <span data-ttu-id="dd544-124">이름을 다시 사용하는 경우 나중에 선언된 이름이 이전에 선언된 이름을 섀도 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-124">If you reuse a name, the name declared later shadows the name declared earlier.</span></span> <span data-ttu-id="dd544-125">그러나 모듈의 최상위 수준 범위에서는 이름이 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-125">However, at the top level scope in a module, names must be unique.</span></span> <span data-ttu-id="dd544-126">예를 들어 다음 코드가 모듈 범위에 표시되는 경우에는 오류가 발생하지만 함수 내에 표시되는 경우에는 오류가 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-126">For example, the following code produces an error when it appears at module scope, but not when it appears inside a function:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet101.fs)]

<span data-ttu-id="dd544-127">하지만 다음 코드는 범위의 모든 수준에서 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-127">But the following code is acceptable at any level of scope:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet102.fs)]

### <a name="parameters"></a><span data-ttu-id="dd544-128">매개 변수</span><span class="sxs-lookup"><span data-stu-id="dd544-128">Parameters</span></span>

<span data-ttu-id="dd544-129">매개 변수 이름은 함수 이름 뒤에 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-129">Names of parameters are listed after the function name.</span></span> <span data-ttu-id="dd544-130">다음 예제와 같이 매개 변수의 형식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-130">You can specify a type for a parameter, as shown in the following example:</span></span>

```fsharp
let f (x : int) = x + 1
```

<span data-ttu-id="dd544-131">형식을 지정하는 경우 매개 변수의 이름 다음에 나오며 콜론으로 이름과 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-131">If you specify a type, it follows the name of the parameter and is separated from the name by a colon.</span></span> <span data-ttu-id="dd544-132">매개 변수의 형식을 생략하면 컴파일러에서 매개 변수 형식을 유추합니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-132">If you omit the type for the parameter, the parameter type is inferred by the compiler.</span></span> <span data-ttu-id="dd544-133">예를 들어 다음 함수 정의에서 1이 `int` 형식이므로`x` 인수는 `int` 형식으로 유추됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-133">For example, in the following function definition, the argument `x` is inferred to be of type `int` because 1 is of type `int`.</span></span>

```fsharp
let f x = x + 1
```

<span data-ttu-id="dd544-134">그러나 컴파일러는 함수를 가능한 한 일반적인 형식으로 설정하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-134">However, the compiler will attempt to make the function as generic as possible.</span></span> <span data-ttu-id="dd544-135">예를 들어 다음 코드를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-135">For example, note the following code:</span></span>

```fsharp
let f x = (x, x)
```

<span data-ttu-id="dd544-136">이 함수는 임의 형식의 한 가지 인수에서 튜플을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-136">The function creates a tuple from one argument of any type.</span></span> <span data-ttu-id="dd544-137">형식이 지정되어 있지 않으므로 함수를 임의의 인수 형식과 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-137">Because the type is not specified, the function can be used with any argument type.</span></span> <span data-ttu-id="dd544-138">자세한 내용은 [자동 일반화](../generics/automatic-generalization.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dd544-138">For more information, see [Automatic Generalization](../generics/automatic-generalization.md).</span></span>

## <a name="function-bodies"></a><span data-ttu-id="dd544-139">함수 본문</span><span class="sxs-lookup"><span data-stu-id="dd544-139">Function Bodies</span></span>

<span data-ttu-id="dd544-140">함수 본문에는 로컬 변수 및 함수에 대한 정의를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-140">A function body can contain definitions of local variables and functions.</span></span> <span data-ttu-id="dd544-141">이러한 변수 및 함수는 현재 함수 본문 외부가 아닌 본문 내부에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-141">Such variables and functions are in scope in the body of the current function but not outside it.</span></span> <span data-ttu-id="dd544-142">간단한 구문 옵션을 사용하는 경우 다음 예제와 같이 들여쓰기를 사용하여 정의가 함수 본문 내에 있음을 나타내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-142">When you have the lightweight syntax option enabled, you must use indentation to indicate that a definition is in a function body, as shown in the following example:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet103.fs)]

<span data-ttu-id="dd544-143">자세한 내용은 [코드 서식 지정 지침](../../style-guide/formatting.md) 및 [자세한 구문](../verbose-syntax.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dd544-143">For more information, see [Code Formatting Guidelines](../../style-guide/formatting.md) and [Verbose Syntax](../verbose-syntax.md).</span></span>

## <a name="return-values"></a><span data-ttu-id="dd544-144">반환 값</span><span class="sxs-lookup"><span data-stu-id="dd544-144">Return Values</span></span>

<span data-ttu-id="dd544-145">컴파일러는 함수 본문의 최종 식을 사용하여 반환 값과 형식을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-145">The compiler uses the final expression in a function body to determine the return value and type.</span></span> <span data-ttu-id="dd544-146">컴파일러는 이전 식에서 최종 식의 형식을 유추할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-146">The compiler might infer the type of the final expression from previous expressions.</span></span> <span data-ttu-id="dd544-147">`cylinderVolume` 함수에서, 이전 섹션과 같이 `pi`의 형식이 `3.14159` 리터럴 형식에서 `float`으로 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-147">In the function `cylinderVolume`, shown in the previous section, the type of `pi` is determined from the type of the literal `3.14159` to be `float`.</span></span> <span data-ttu-id="dd544-148">컴파일러는 `pi`의 형식을 사용하여 `h * pi * r * r` 식의 형식을 `float`으로 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-148">The compiler uses the type of `pi` to determine the type of the expression `h * pi * r * r` to be `float`.</span></span> <span data-ttu-id="dd544-149">따라서 함수의 전체 반환 형식은 `float`입니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-149">Therefore, the overall return type of the function is `float`.</span></span>

<span data-ttu-id="dd544-150">반환 값을 명시적으로 지정하려면 다음과 같이 코드를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-150">To specify the return value explicitly, write the code as follows:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet105.fs)]

<span data-ttu-id="dd544-151">코드가 위와 같이 작성되면 컴파일러에서 전체 함수에 **float**을 적용합니다. 매개 변수 형식에도 이를 적용하려는 경우 다음 코드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-151">As the code is written above, the compiler applies **float** to the entire function; if you mean to apply it to the parameter types as well, use the following code:</span></span>

```fsharp
let cylinderVolume (radius : float) (length : float) : float
```

## <a name="calling-a-function"></a><span data-ttu-id="dd544-152">함수 호출</span><span class="sxs-lookup"><span data-stu-id="dd544-152">Calling a Function</span></span>

<span data-ttu-id="dd544-153">함수 이름 뒤에 공백을 지정한 후 공백으로 구분된 인수를 지정하여 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-153">You call functions by specifying the function name followed by a space and then any arguments separated by spaces.</span></span> <span data-ttu-id="dd544-154">예를 들어, **cylinderVolume** 함수를 호출하여 **vol** 값에 결과를 할당하려면 다음 코드를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-154">For example, to call the function **cylinderVolume** and assign the result to the value **vol**, you write the following code:</span></span>

```fsharp
let vol = cylinderVolume 2.0 3.0
```

## <a name="partial-application-of-arguments"></a><span data-ttu-id="dd544-155">인수의 부분 적용</span><span class="sxs-lookup"><span data-stu-id="dd544-155">Partial Application of Arguments</span></span>

<span data-ttu-id="dd544-156">지정된 수보다 적은 인수를 지정하는 경우 나머지 인수를 요구하는 새 함수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-156">If you supply fewer than the specified number of arguments, you create a new function that expects the remaining arguments.</span></span> <span data-ttu-id="dd544-157">인수를 처리하는 이 메서드를 *커링*(currying)이라고 하며 F#과 같은 함수형 프로그래밍 언어의 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-157">This method of handling arguments is referred to as *currying* and is a characteristic of functional programming languages like F#.</span></span> <span data-ttu-id="dd544-158">예를 들어, 두 가지 크기의 파이프(**2.0**의 반지름 및 **3.0**의 반지름)에 대해 작업하고 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-158">For example, suppose you are working with two sizes of pipe: one has a radius of **2.0** and the other has a radius of **3.0**.</span></span> <span data-ttu-id="dd544-159">다음과 같이 파이프의 볼륨을 결정하는 함수를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-159">You could create functions that determine the volume of pipe as follows:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet106.fs)]

<span data-ttu-id="dd544-160">다양한 길이의 두 가지 크기 파이프에 필요한 추가 인수를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-160">You would then supply the additional argument as needed for various lengths of pipe of the two different sizes:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet107.fs)]

## <a name="recursive-functions"></a><span data-ttu-id="dd544-161">재귀 함수</span><span class="sxs-lookup"><span data-stu-id="dd544-161">Recursive Functions</span></span>

<span data-ttu-id="dd544-162">*재귀 함수*는 자신을 호출하는 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-162">*Recursive functions* are functions that call themselves.</span></span> <span data-ttu-id="dd544-163">이러한 함수에는 **rec** 키워드 다음에 **let** 키워드를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-163">They require that you specify the **rec** keyword following the **let** keyword.</span></span> <span data-ttu-id="dd544-164">임의의 함수를 호출하는 경우와 마찬가지로 함수 본문 내에서 재귀 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-164">Invoke the recursive function from within the body of the function just as you would invoke any function call.</span></span> <span data-ttu-id="dd544-165">다음 재귀 함수는 *n*<sup>번째</sup> 피보나치 수를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-165">The following recursive function computes the *n*<sup>th</sup> Fibonacci number.</span></span> <span data-ttu-id="dd544-166">피보나치 수열은 아주 오래 전부터 알려져 왔으며, 연속되는 각 숫자는 수열에서 이전 두 숫자의 합이 되는 수열입니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-166">The Fibonacci number sequence has been known since antiquity and is a sequence in which each successive number is the sum of the previous two numbers in the sequence.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet108.fs)]

<span data-ttu-id="dd544-167">주의를 기울이고 누적기 및 연속의 사용과 같은 특별 기법을 인식하여 재귀 함수를 작성하지 않으면 일부 재귀 함수는 프로그램 스택을 오버플로하거나 비효율적으로 작동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-167">Some recursive functions might overflow the program stack or perform inefficiently if you do not write them with care and with awareness of special techniques, such as the use of accumulators and continuations.</span></span>

## <a name="function-values"></a><span data-ttu-id="dd544-168">함수 값</span><span class="sxs-lookup"><span data-stu-id="dd544-168">Function Values</span></span>

<span data-ttu-id="dd544-169">F#에서 모든 함수는 값으로 간주됩니다. 사실 이들을 *함수 값*이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-169">In F#, all functions are considered values; in fact, they are known as *function values*.</span></span> <span data-ttu-id="dd544-170">함수가 값이기 때문에 이러한 함수를 값이 사용되는 다른 컨텍스트에서 또는 다른 함수의 인수로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-170">Because functions are values, they can be used as arguments to other functions or in other contexts where values are used.</span></span> <span data-ttu-id="dd544-171">다음은 함수 값을 인수로 사용하는 함수의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-171">Following is an example of a function that takes a function value as an argument:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet109.fs)]

<span data-ttu-id="dd544-172">`->` 토큰을 사용하여 함수 값의 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-172">You specify the type of a function value by using the `->` token.</span></span> <span data-ttu-id="dd544-173">이 토큰의 왼쪽에는 인수의 형식이 있고 오른쪽에는 반환 값이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-173">On the left side of this token is the type of the argument, and on the right side is the return value.</span></span> <span data-ttu-id="dd544-174">앞의 예제에서 `apply1`은 `transform` 함수를 인수로 사용합니다. 여기서 `transform`은 인수를 사용하고 다른 정수를 반환하는 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-174">In the previous example, `apply1` is a function that takes a function `transform` as an argument, where `transform` is a function that takes an integer and returns another integer.</span></span> <span data-ttu-id="dd544-175">다음 코드에서는 `apply1`을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-175">The following code shows how to use `apply1`:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet110.fs)]

<span data-ttu-id="dd544-176">`result`의 값은 앞의 코드가 실행된 후 101이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-176">The value of `result` will be 101 after the previous code runs.</span></span>

<span data-ttu-id="dd544-177">다음 예와 같이 여러 인수는 연속적인 `->` 토큰으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-177">Multiple arguments are separated by successive `->` tokens, as shown in the following example:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet111.fs)]

<span data-ttu-id="dd544-178">해당 결과는 200입니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-178">The result is 200.</span></span>

## <a name="lambda-expressions"></a><span data-ttu-id="dd544-179">람다 식</span><span class="sxs-lookup"><span data-stu-id="dd544-179">Lambda Expressions</span></span>

<span data-ttu-id="dd544-180">*람다 식*은 명명되지 않은 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-180">A *lambda expression* is an unnamed function.</span></span> <span data-ttu-id="dd544-181">이전 예제에서, 명명된 함수인 **increment** 및 **mul**을 정의하는 대신 다음과 같이 람다 식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-181">In the previous examples, instead of defining named functions **increment** and **mul**, you could use lambda expressions as follows:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet112.fs)]

<span data-ttu-id="dd544-182">`fun` 키워드를 사용하여 람다 식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-182">You define lambda expressions by using the `fun` keyword.</span></span> <span data-ttu-id="dd544-183">람다 식은 함수 정의와 유사합니다. 단, `=` 토큰 대신 `->` 토큰이 함수 본문에서 인수 목록을 구분하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-183">A lambda expression resembles a function definition, except that instead of the `=` token, the `->` token is used to separate the argument list from the function body.</span></span> <span data-ttu-id="dd544-184">일반 함수 정의에서와 같이, 인수 형식이 명시적으로 유추되거나 지정될 수 있으며 람다 식의 반환 형식은 본문의 마지막 식 형식에서 유추됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-184">As in a regular function definition, the argument types can be inferred or specified explicitly, and the return type of the lambda expression is inferred from the type of the last expression in the body.</span></span> <span data-ttu-id="dd544-185">자세한 내용은 [람다 식: `fun` 키워드](lambda-expressions-the-fun-keyword.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dd544-185">For more information, see [Lambda Expressions: The `fun` Keyword](lambda-expressions-the-fun-keyword.md).</span></span>

## <a name="function-composition-and-pipelining"></a><span data-ttu-id="dd544-186">함수 컴퍼지션 및 파이프라인</span><span class="sxs-lookup"><span data-stu-id="dd544-186">Function Composition and Pipelining</span></span>

<span data-ttu-id="dd544-187">F#의 함수는 다른 함수에서 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-187">Functions in F# can be composed from other functions.</span></span> <span data-ttu-id="dd544-188">두 함수**function1** 및 **function2**의 컴퍼지션은 **function1**을 적용한 후 **function2**를 적용한다는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-188">The composition of two functions **function1** and **function2** is another function that represents the application of **function1** followed the application of **function2**:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet113.fs)]

<span data-ttu-id="dd544-189">결과는 202입니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-189">The result is 202.</span></span>

<span data-ttu-id="dd544-190">파이프라인을 통해 함수 호출을 연속 작업으로 함께 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-190">Pipelining enables function calls to be chained together as successive operations.</span></span> <span data-ttu-id="dd544-191">파이프라인은 다음과 같이 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-191">Pipelining works as follows:</span></span>

```fsharp
let result = 100 |> function1 |> function2
```

<span data-ttu-id="dd544-192">결과는 다시 202입니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-192">The result is again 202.</span></span>

<span data-ttu-id="dd544-193">컴퍼지션 연산자는 두 개의 함수를 사용하고 한 함수를 반환합니다. 반대로 파이프라인 연산자는 함수 및 인수를 사용하고 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-193">The composition operators take two functions and return a function; by contrast, the pipeline operators take a function and an argument and return a value.</span></span> <span data-ttu-id="dd544-194">다음 코드 예제에서는 함수 시그니처 및 사용 방식의 차이를 나타내어 파이프라인 및 컴퍼지션 연산자 간의 차이를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-194">The following code example shows the difference between the pipeline and composition operators by showing the differences in the function signatures and usage.</span></span>

```fsharp
// Function composition and pipeline operators compared.

let addOne x = x + 1
let timesTwo x = 2 * x

// Composition operator
// ( >> ) : ('T1 -> 'T2) -> ('T2 -> 'T3) -> 'T1 -> 'T3
let Compose2 = addOne >> timesTwo

// Backward composition operator
// ( << ) : ('T2 -> 'T3) -> ('T1 -> 'T2) -> 'T1 -> 'T3
let Compose1 = addOne << timesTwo

// Result is 5
let result1 = Compose1 2

// Result is 6
let result2 = Compose2 2

// Pipelining
// Pipeline operator
// ( |> ) : 'T1 -> ('T1 -> 'U) -> 'U
let Pipeline2 x = addOne x |> timesTwo

// Backward pipeline operator
// ( <| ) : ('T -> 'U) -> 'T -> 'U
let Pipeline1 x = addOne <| timesTwo x

// Result is 5
let result3 = Pipeline1 2

// Result is 6
let result4 = Pipeline2 2
```

## <a name="overloading-functions"></a><span data-ttu-id="dd544-195">함수 오버로드</span><span class="sxs-lookup"><span data-stu-id="dd544-195">Overloading Functions</span></span>

<span data-ttu-id="dd544-196">특정 형식의 메서드는 오버로드할 수 있지만 함수를 오버로드할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dd544-196">You can overload methods of a type but not functions.</span></span> <span data-ttu-id="dd544-197">자세한 내용은 [메서드](../members/methods.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dd544-197">For more information, see [Methods](../members/methods.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dd544-198">참조</span><span class="sxs-lookup"><span data-stu-id="dd544-198">See also</span></span>

- [<span data-ttu-id="dd544-199">값</span><span class="sxs-lookup"><span data-stu-id="dd544-199">Values</span></span>](../values/index.md)
- [<span data-ttu-id="dd544-200">F# 언어 참조</span><span class="sxs-lookup"><span data-stu-id="dd544-200">F# Language Reference</span></span>](../index.md)
