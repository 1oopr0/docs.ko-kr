---
description: switch(C# 참조)
title: C# switch 문
ms.date: 04/09/2019
f1_keywords:
- switch_CSharpKeyword
- switch
- case
- case_CSharpKeyword
- defaultcase_CSharpKeyword
helpviewer_keywords:
- switch statement [C#]
- switch keyword [C#]
- case statement [C#]
- default keyword [C#]
ms.assetid: 44bae8b8-8841-4d85-826b-8a94277daecb
ms.openlocfilehash: 2d12091f3c3f10048a98f5f0ecf6a381087faf41
ms.sourcegitcommit: e078b7540a8293ca1b604c9c0da1ff1506f0170b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "91997688"
---
# <a name="switch-c-reference"></a><span data-ttu-id="7c45e-103">switch(C# 참조)</span><span class="sxs-lookup"><span data-stu-id="7c45e-103">switch (C# reference)</span></span>

<span data-ttu-id="7c45e-104">이 문서에서는 `switch` 문에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-104">This article covers the `switch` statement.</span></span> <span data-ttu-id="7c45e-105">C# 8.0에 도입된 `switch` 식에 대한 자세한 내용은 [식 및 연산자](../operators/index.md) 섹션에서 [`switch` 식](../operators/switch-expression.md) 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7c45e-105">For information on the `switch` expression (introduced in C# 8.0), see the article on [`switch` expressions](../operators/switch-expression.md) in the [expressions and operators](../operators/index.md) section.</span></span>

<span data-ttu-id="7c45e-106">`switch`는 *일치 식*을 사용한 패턴 일치를 기반으로 하여 후보 목록에서 실행할 *switch 섹션* 하나를 선택하는 선택 문입니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-106">`switch` is a selection statement that chooses a single *switch section* to execute from a list of candidates based on a pattern match with the *match expression*.</span></span>

[!code-csharp[switch#1](~/samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]

<span data-ttu-id="7c45e-107">단일 식을 3개 이상의 조건에 대해 테스트하는 경우 `switch` 문이 [if-else](if-else.md) 구문 대신 사용되는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-107">The `switch` statement is often used as an alternative to an [if-else](if-else.md) construct if a single expression is tested against three or more conditions.</span></span> <span data-ttu-id="7c45e-108">예를 들어 다음 `switch` 문은 `Color` 형식의 변수에 다음 세 가지 값 중 하나가 있는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-108">For example, the following `switch` statement determines whether a variable of type `Color` has one of three values:</span></span>

[!code-csharp[switch#3](~/samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)]

<span data-ttu-id="7c45e-109">이 문은 `if`-`else` 구문을 사용하는 다음 예제와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-109">It's equivalent to the following example that uses an `if`-`else` construct.</span></span>

[!code-csharp[switch#3a](~/samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)]

## <a name="the-match-expression"></a><span data-ttu-id="7c45e-110">일치 식</span><span class="sxs-lookup"><span data-stu-id="7c45e-110">The match expression</span></span>

<span data-ttu-id="7c45e-111">일치 식은 `case` 레이블의 패턴과 일치시킬 값을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-111">The match expression provides the value to match against the patterns in `case` labels.</span></span> <span data-ttu-id="7c45e-112">구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-112">Its syntax is:</span></span>

```csharp
   switch (expr)
```

<span data-ttu-id="7c45e-113">C# 6 이하에서 일치 식은 다음 형식의 값을 반환하는 식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-113">In C# 6 and earlier, the match expression must be an expression that returns a value of the following types:</span></span>

- <span data-ttu-id="7c45e-114">[char](../builtin-types/char.md)</span><span class="sxs-lookup"><span data-stu-id="7c45e-114">a [char](../builtin-types/char.md).</span></span>
- <span data-ttu-id="7c45e-115">[string](../builtin-types/reference-types.md)</span><span class="sxs-lookup"><span data-stu-id="7c45e-115">a [string](../builtin-types/reference-types.md).</span></span>
- <span data-ttu-id="7c45e-116">[bool](../builtin-types/bool.md)</span><span class="sxs-lookup"><span data-stu-id="7c45e-116">a [bool](../builtin-types/bool.md).</span></span>
- <span data-ttu-id="7c45e-117">[정수](../builtin-types/integral-numeric-types.md) 값(예: `int` 또는 `long`)입니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-117">an [integral](../builtin-types/integral-numeric-types.md) value, such as an `int` or a `long`.</span></span>
- <span data-ttu-id="7c45e-118">[enum](../builtin-types/enum.md) 값</span><span class="sxs-lookup"><span data-stu-id="7c45e-118">an [enum](../builtin-types/enum.md) value.</span></span>

<span data-ttu-id="7c45e-119">C# 7.0부터 일치 식은 null이 아닌 모든 식일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-119">Starting with C# 7.0, the match expression can be any non-null expression.</span></span>

## <a name="the-switch-section"></a><span data-ttu-id="7c45e-120">switch 섹션</span><span class="sxs-lookup"><span data-stu-id="7c45e-120">The switch section</span></span>

<span data-ttu-id="7c45e-121">`switch` 문에는 스위치 섹션이 하나 이상 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-121">A `switch` statement includes one or more switch sections.</span></span> <span data-ttu-id="7c45e-122">각 switch 섹션에는 하나 이상의 *case 레이블*(사례 또는 기본 레이블) 및 하나 이상의 명령문이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-122">Each switch section contains one or more *case labels* (either a case or default label) followed by one or more statements.</span></span> <span data-ttu-id="7c45e-123">`switch` 문은 switch 섹션에 있는 기본 레이블이 하나만 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-123">The `switch` statement may include at most one default label placed in any switch section.</span></span> <span data-ttu-id="7c45e-124">다음 예제에서는 각각 두 개의 명령문을 포함하는 세 개의 switch 섹션이 있는 간단한 `switch` 문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-124">The following example shows a simple `switch` statement that has three switch sections, each containing two statements.</span></span> <span data-ttu-id="7c45e-125">두 번째 switch 섹션에는 `case 2:` 및 `case 3:` 레이블이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-125">The second switch section contains the `case 2:` and `case 3:` labels.</span></span>

<span data-ttu-id="7c45e-126">`switch` 문에 포함할 수 있는 switch 섹션 수에는 제한이 없으며 각 섹션에 하나 이상의 case 레이블을 포함할 수 있습니다(다음 예제 참조).</span><span class="sxs-lookup"><span data-stu-id="7c45e-126">A `switch` statement can include any number of switch sections, and each section can have one or more case labels, as shown in the following example.</span></span> <span data-ttu-id="7c45e-127">하지만 두 case 레이블에 동일한 식을 포함할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-127">However, no two case labels may contain the same expression.</span></span>

[!code-csharp[switch#2](~/samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]

<span data-ttu-id="7c45e-128">switch 문에서 하나의 switch 섹션만 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-128">Only one switch section in a switch statement executes.</span></span> <span data-ttu-id="7c45e-129">C#은 한 switch 섹션에서 다음 switch 섹션으로 계속 실행하도록 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-129">C# doesn't allow execution to continue from one switch section to the next.</span></span> <span data-ttu-id="7c45e-130">이로 인해 다음 코드는 다음과 같은 컴파일러 오류를 생성합니다. CS0163: "한 case 레이블에서 다른 case 레이블(\<case label>)로 제어를 이동할 수 없습니다."</span><span class="sxs-lookup"><span data-stu-id="7c45e-130">Because of this, the following code generates a compiler error, CS0163: "Control cannot fall through from one case label (\<case label>) to another."</span></span>

```csharp
switch (caseSwitch)
{
    // The following switch section causes an error.
    case 1:
        Console.WriteLine("Case 1...");
        // Add a break or other jump statement here.
    case 2:
        Console.WriteLine("... and/or Case 2");
        break;
}
```

<span data-ttu-id="7c45e-131">이 요구 사항은 일반적으로 [break](break.md), [goto](goto.md) 또는 [return](return.md) 문을 통해 switch 섹션을 명시적으로 종료하여 충족됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-131">This requirement is usually met by explicitly exiting the switch section by using a [break](break.md), [goto](goto.md), or [return](return.md) statement.</span></span> <span data-ttu-id="7c45e-132">그러나 다음 코드는 프로그램 제어가 `default` switch 섹션으로 이동할 수 없도록 하기 때문에 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-132">However, the following code is also valid, because it ensures that program control can't fall through to the `default` switch section.</span></span>

[!code-csharp[switch#4](~/samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]

<span data-ttu-id="7c45e-133">case 레이블이 일치 식과 일치하는 switch 섹션에서 문 목록의 실행은 첫 번째 문으로 시작하고 일반적으로 `break`, `goto case`, `goto label`, `return` 또는 `throw` 같은 점프 문에 도달할 때까지 문 목록 전체를 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-133">Execution of the statement list in the switch section with a case label that matches the match expression begins with the first statement and proceeds through the statement list, typically until a jump statement, such as a `break`, `goto case`, `goto label`, `return`, or `throw`, is reached.</span></span> <span data-ttu-id="7c45e-134">이 경우 `switch` 문 외부 또는 다른 case 레이블로 제어를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-134">At that point, control is transferred outside the `switch` statement or to another case label.</span></span> <span data-ttu-id="7c45e-135">사용되는 경우 `goto` 문은 constant 레이블에 컨트롤을 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-135">A `goto` statement, if it's used, must transfer control to a constant label.</span></span> <span data-ttu-id="7c45e-136">이 제한 사항이 필요합니다. constant가 아닌 레이블에 컨트롤을 전달하려고 하면 코드의 의도치 않은 위치에 컨트롤을 전달하거나 무한 루프를 만드는 것과 같은 원치 않는 부작용이 발생할 수 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-136">This restriction is necessary, since attempting to transfer control to a non-constant label can have undesirable side-effects, such transferring control to an unintended location in code or creating an endless loop.</span></span>

## <a name="case-labels"></a><span data-ttu-id="7c45e-137">case 레이블</span><span class="sxs-lookup"><span data-stu-id="7c45e-137">Case labels</span></span>

<span data-ttu-id="7c45e-138">각 case 레이블은 일치 식과 비교할 패턴(이전 예제의 `caseSwitch` 변수)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-138">Each case label specifies a pattern to compare to the match expression (the `caseSwitch` variable in the previous examples).</span></span> <span data-ttu-id="7c45e-139">일치하는 경우 제어가 일치하는 **첫 번째** case 레이블을 포함하는 switch 섹션으로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-139">If they match, control is transferred to the switch section that contains the **first** matching case label.</span></span> <span data-ttu-id="7c45e-140">일치 식과 일치하는 case 레이블 패턴이 없는 경우 제어가 `default` case 레이블을 포함하는 섹션으로 전송됩니다(있는 경우).</span><span class="sxs-lookup"><span data-stu-id="7c45e-140">If no case label pattern matches the match expression, control is transferred to the section with the `default` case label, if there's one.</span></span> <span data-ttu-id="7c45e-141">`default` case가 없는 경우 switch 섹션의 문이 실행되지 않으며, 제어가 `switch` 문 외부로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-141">If there's no `default` case, no statements in any switch section are executed, and control is transferred outside the `switch` statement.</span></span>

<span data-ttu-id="7c45e-142">`switch` 문과 패턴 일치에 대한 자세한 내용은 [`switch` 문을 사용한 패턴 일치](#pattern-matching-with-the-switch-statement) 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7c45e-142">For information on the `switch` statement and pattern matching, see the [Pattern matching with the `switch` statement](#pattern-matching-with-the-switch-statement) section.</span></span>

<span data-ttu-id="7c45e-143">C# 6에서 상수 패턴만 지원하고 상수 값의 반복을 허용하지 않는 경우 case 레이블은 상호 배타적인 값을 정의하며 하나의 패턴만 일치 식과 일치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-143">Because C# 6 supports only the constant pattern and doesn't allow the repetition of constant values, case labels define mutually exclusive values, and only one pattern can match the match expression.</span></span> <span data-ttu-id="7c45e-144">따라서 `case` 문이 표시되는 순서는 중요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-144">As a result, the order in which `case` statements appear is unimportant.</span></span>

<span data-ttu-id="7c45e-145">그러나 C# 7.0에서는 다른 패턴도 지원되므로 case 레이블에서 상호 배타적인 값을 정의할 필요가 없으며 여러 패턴이 일치 식과 일치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-145">In C# 7.0, however, because other patterns are supported, case labels need not define mutually exclusive values, and multiple patterns can match the match expression.</span></span> <span data-ttu-id="7c45e-146">일치 패턴을 포함하는 첫 번째 switch 섹션의 문만 실행되기 때문에 이제 `case` 문이 나타나는 순서가 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-146">Because only the statements in the first switch section that contains the matching pattern are executed, the order in which `case` statements appear is now important.</span></span> <span data-ttu-id="7c45e-147">C#에서 case 문이 이전 문과 같거나 이전 문의 하위 집합인 switch 섹션을 검색할 경우 컴파일러 오류, CS8120, "Switch case가 이전 case에서 이미 처리되었습니다."를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-147">If C# detects a switch section whose case statement or statements are equivalent to or are subsets of previous statements, it generates a compiler error, CS8120, "The switch case has already been handled by a previous case."</span></span>

<span data-ttu-id="7c45e-148">다음 예제에서는 상호 배타적이 아닌 다양한 패턴을 사용하는 `switch` 문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-148">The following example illustrates a `switch` statement that uses a variety of non-mutually exclusive patterns.</span></span> <span data-ttu-id="7c45e-149">더 이상 `switch` 문의 첫 번째 섹션이 아니도록 `case 0:` switch 섹션을 이동하는 경우 해당 값이 0인 정수는 `case int val` 문에 정의된 패턴인 모든 정수의 하위 집합이므로 C#에서 컴파일러 오류를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-149">If you move the `case 0:` switch section so that it's no longer the first section in the `switch` statement, C# generates a compiler error because an integer whose value is zero is a subset of all integers, which is the pattern defined by the `case int val` statement.</span></span>

[!code-csharp[switch#5](~/samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]

<span data-ttu-id="7c45e-150">이 문제를 해결하고 다음 두 가지 방법 중 하나로 컴파일러 경고를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-150">You can correct this issue and eliminate the compiler warning in one of two ways:</span></span>

- <span data-ttu-id="7c45e-151">switch 섹션의 순서 변경</span><span class="sxs-lookup"><span data-stu-id="7c45e-151">By changing the order of the switch sections.</span></span>

- <span data-ttu-id="7c45e-152">`case` 레이블에서 [when 절](#the-case-statement-and-the-when-clause) 사용</span><span class="sxs-lookup"><span data-stu-id="7c45e-152">By using a [when clause](#the-case-statement-and-the-when-clause) in the `case` label.</span></span>

## <a name="the-default-case"></a><span data-ttu-id="7c45e-153">`default` case</span><span class="sxs-lookup"><span data-stu-id="7c45e-153">The `default` case</span></span>

<span data-ttu-id="7c45e-154">`default` case는 일치 식이 다른 `case` 레이블과 일치하지 않는 경우 실행할 switch 섹션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-154">The `default` case specifies the switch section to execute if the match expression doesn't match any other `case` label.</span></span> <span data-ttu-id="7c45e-155">`default` case가 없고 일치 식이 다른 `case` 레이블과 일치하지 않는 경우 프로그램 흐름이 `switch` 문으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-155">If a `default` case is not present and the match expression doesn't match any other `case` label, program flow falls through the `switch` statement.</span></span>

<span data-ttu-id="7c45e-156">`default` case는 `switch` 문에 임의 순서로 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-156">The `default` case can appear in any order in the `switch` statement.</span></span> <span data-ttu-id="7c45e-157">소스 코드에서 해당 순서와 관계없이 항상 모든 `case` 레이블이 평가된 후 마지막에 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-157">Regardless of its order in the source code, it's always evaluated last, after all `case` labels have been evaluated.</span></span>

## <a name="pattern-matching-with-the-switch-statement"></a><span data-ttu-id="7c45e-158">`switch` 문과 일치하는 패턴</span><span class="sxs-lookup"><span data-stu-id="7c45e-158">Pattern matching with the `switch` statement</span></span>

<span data-ttu-id="7c45e-159">각 `case` 문은 일치 식과 일치할 경우 포함하는 switch 섹션이 실행되는 패턴을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-159">Each `case` statement defines a pattern that, if it matches the match expression, causes its  containing switch section to be executed.</span></span> <span data-ttu-id="7c45e-160">상수 패턴은 모든 버전의 C#에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-160">All versions of C# support the constant pattern.</span></span> <span data-ttu-id="7c45e-161">나머지 패턴은 C# 7.0부터 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-161">The remaining patterns are supported beginning with C# 7.0.</span></span>

### <a name="constant-pattern"></a><span data-ttu-id="7c45e-162">상수 패턴</span><span class="sxs-lookup"><span data-stu-id="7c45e-162">Constant pattern</span></span>

<span data-ttu-id="7c45e-163">상수 패턴은 일치 식이 지정된 상수와 같은지 여부를 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-163">The constant pattern tests whether the match expression equals a specified constant.</span></span> <span data-ttu-id="7c45e-164">구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-164">Its syntax is:</span></span>

```csharp
   case constant:
```

<span data-ttu-id="7c45e-165">여기서 *constant*는 테스트할 값입니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-165">where *constant* is the value to test for.</span></span> <span data-ttu-id="7c45e-166">*constant*는 다음 상수 식 중 하나가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-166">*constant* can be any of the following constant expressions:</span></span>

- <span data-ttu-id="7c45e-167">[bool](../builtin-types/bool.md) 리터럴(`true` 또는 `false`).</span><span class="sxs-lookup"><span data-stu-id="7c45e-167">A [bool](../builtin-types/bool.md) literal: either `true` or `false`.</span></span>
- <span data-ttu-id="7c45e-168">[정수](../builtin-types/integral-numeric-types.md) 상수(예: `int`, `long` 또는 `byte`)입니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-168">Any [integral](../builtin-types/integral-numeric-types.md) constant, such as an `int`, a `long`, or a `byte`.</span></span>
- <span data-ttu-id="7c45e-169">선언된 `const` 변수의 이름</span><span class="sxs-lookup"><span data-stu-id="7c45e-169">The name of a declared `const` variable.</span></span>
- <span data-ttu-id="7c45e-170">열거형 상수</span><span class="sxs-lookup"><span data-stu-id="7c45e-170">An enumeration constant.</span></span>
- <span data-ttu-id="7c45e-171">[char](../builtin-types/char.md) 리터럴</span><span class="sxs-lookup"><span data-stu-id="7c45e-171">A [char](../builtin-types/char.md) literal.</span></span>
- <span data-ttu-id="7c45e-172">[string](../builtin-types/reference-types.md) 리터럴</span><span class="sxs-lookup"><span data-stu-id="7c45e-172">A [string](../builtin-types/reference-types.md) literal.</span></span>

<span data-ttu-id="7c45e-173">상수 식은 다음과 같이 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-173">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="7c45e-174">*expr* 및 *constant*가 정수 형식인 경우 C# 같음 연산자는 식에서 `true`를 반환하는지 여부 즉, `expr == constant`인지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-174">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="7c45e-175">정수 형식이 아니면 static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) 메서드 호출을 통해 식의 값이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-175">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>

<span data-ttu-id="7c45e-176">다음 예제에서는 상수 패턴을 사용하여 특정 날짜가 주말인지, 작업 주의 첫째 날인지, 작업 주의 마지막 날인지 또는 작업 주의 중간인지를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-176">The following example uses the constant pattern to determine whether a particular date is a weekend, the first day of the work week, the last day of the work week, or the middle of the work week.</span></span> <span data-ttu-id="7c45e-177">현재 날짜의 <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> 속성을 <xref:System.DayOfWeek> 열거형의 멤버와 비교해서 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-177">It evaluates the <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> property of the current day against the members of the <xref:System.DayOfWeek> enumeration.</span></span>

[!code-csharp[switch#7](~/samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

<span data-ttu-id="7c45e-178">다음 예제에서는 상수 패턴을 사용하여 자동 커피 머신을 시뮬레이트하는 콘솔 애플리케이션의 사용자 입력을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-178">The following example uses the constant pattern to handle user input in a console application that simulates an automatic coffee machine.</span></span>

[!code-csharp[switch#6](~/samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]

### <a name="type-pattern"></a><span data-ttu-id="7c45e-179">형식 패턴</span><span class="sxs-lookup"><span data-stu-id="7c45e-179">Type pattern</span></span>

<span data-ttu-id="7c45e-180">형식 패턴은 간결한 형식 평가 및 변환을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-180">The type pattern enables concise type evaluation and conversion.</span></span> <span data-ttu-id="7c45e-181">`switch` 문과 함께 사용하여 패턴 일치를 수행하는 경우 식을 지정된 형식으로 변환할 수 있는지 여부를 테스트하고, 변환할 수 있으면 해당 형식의 변수로 캐스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-181">When used with the `switch` statement to perform pattern matching, it tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="7c45e-182">구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-182">Its syntax is:</span></span>

```csharp
   case type varname
```

<span data-ttu-id="7c45e-183">여기서 *type*은 *expr*의 결과가 변환되는 형식의 이름이고, *varname*은 일치에 성공할 경우 *expr*의 결과가 변환되는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-183">where *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the match succeeds.</span></span> <span data-ttu-id="7c45e-184">*expr*의 컴파일 시간 형식은 C# 7.1부터 제네릭 형식 매개 변수일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-184">The compile-time type of *expr* may be a generic type parameter, starting with C# 7.1.</span></span>

<span data-ttu-id="7c45e-185">다음 중 하나가 true일 경우 `case` 식은 `true`입니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-185">The `case` expression is `true` if any of the following is true:</span></span>

- <span data-ttu-id="7c45e-186">*expr*이 *type*과 동일한 형식의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-186">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="7c45e-187">*expr*이 *type*에서 파생된 형식의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-187">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="7c45e-188">즉, *expr*의 결과를 *type*의 인스턴스로 업캐스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-188">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="7c45e-189">*expr*의 컴파일 시간 형식은 *type*의 기본 클래스이고 *expr*의 런타임 형식은 *type*이거나 *type*에서 파생됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-189">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="7c45e-190">변수의 *컴파일 시간 형식*은 해당 형식 선언에 정의된 변수의 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-190">The *compile-time type* of a variable is the variable's type as defined in its type declaration.</span></span> <span data-ttu-id="7c45e-191">변수의 *런타임 형식*은 해당 변수에 할당된 인스턴스의 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-191">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="7c45e-192">*expr*이 *type* 인터페이스를 구현하는 형식의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-192">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="7c45e-193">case 식이 true이면 *varname*이 한정적으로 할당되고 switch 섹션 내의 로컬 범위만 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-193">If the case expression is true, *varname* is definitely assigned and has local scope within the switch section only.</span></span>

<span data-ttu-id="7c45e-194">`null`은 형식과 일치하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-194">Note that `null` doesn't match a type.</span></span> <span data-ttu-id="7c45e-195">`null`과 일치하려면 다음 `case` 레이블을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-195">To match a `null`, you use the following `case` label:</span></span>

```csharp
case null:
```

<span data-ttu-id="7c45e-196">다음 예제에서는 형식 패턴을 사용하여 다양한 종류의 컬렉션 형식에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-196">The following example uses the type pattern to provide information about various kinds of collection types.</span></span>

[!code-csharp[type-pattern#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

<span data-ttu-id="7c45e-197">`object` 대신, 다음 코드와 같이 컬렉션 형식을 형식 매개 변수로 사용하여 제네릭 메서드를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-197">Instead of `object`, you could make a generic method, using the type of the collection as the type parameter, as shown in the following code:</span></span>

[!code-csharp[type-pattern#3](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern3.cs#1)]

<span data-ttu-id="7c45e-198">제네릭 버전은 두 가지 측면에서 첫 번째 샘플과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-198">The generic version is different than the first sample in two ways.</span></span> <span data-ttu-id="7c45e-199">먼저 `null` case를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-199">First, you can't use the `null` case.</span></span> <span data-ttu-id="7c45e-200">컴파일러가 임의 형식 `T`를 `object` 이외의 형식으로 변환할 수 없으므로 constant case를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-200">You can't use any constant case because the compiler can't convert any arbitrary type `T` to any type other than `object`.</span></span> <span data-ttu-id="7c45e-201">`default` case였던 항목이 이제 Null이 아닌 `object`에 대해 테스트됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-201">What had been the `default` case now tests for a non-null `object`.</span></span> <span data-ttu-id="7c45e-202">즉, `default` case는 `null`에 대해서만 테스트됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-202">That means the `default` case tests only for `null`.</span></span>

<span data-ttu-id="7c45e-203">패턴 일치를 사용하지 않을 경우 이 코드를 다음과 같이 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-203">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="7c45e-204">형식 패턴 일치를 사용하면 변환 결과가 `null`인지 여부를 테스트하거나 반복된 캐스트를 수행할 필요가 없으므로 더욱 단순하고 읽기 쉬운 코드가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-204">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null` or to perform repeated casts.</span></span>

[!code-csharp[type-pattern2#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="the-case-statement-and-the-when-clause"></a><span data-ttu-id="7c45e-205">`case` 문과 `when` 절</span><span class="sxs-lookup"><span data-stu-id="7c45e-205">The `case` statement and the `when` clause</span></span>

<span data-ttu-id="7c45e-206">C# 7.0부터 case 문이 상호 배타적일 필요가 없으므로 `when` 절을 추가하여 case 문이 true로 평가되기 위해 충족해야 하는 추가 조건을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-206">Starting with C# 7.0, because case statements need not be mutually exclusive, you can add a `when` clause to specify an additional condition that must be satisfied for the case statement to evaluate to true.</span></span> <span data-ttu-id="7c45e-207">`when` 절은 부울 값을 반환하는 모든 식일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-207">The `when` clause can be any expression that returns a Boolean value.</span></span>

<span data-ttu-id="7c45e-208">다음 예제에서는 기본 `Shape` 클래스, `Shape`에서 파생된 `Rectangle` 클래스 및 `Rectangle`에서 파생된 `Square` 클래스를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-208">The following example defines a base `Shape` class, a `Rectangle` class that derives from `Shape`, and a `Square` class that derives from `Rectangle`.</span></span> <span data-ttu-id="7c45e-209">`when` 절을 사용하여 `ShowShapeInfo`에서 `Square` 개체로 인스턴스화되지 않은 경우에도 동일한 길이 및 너비가 할당된 `Rectangle` 개체를 `Square`로 처리하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-209">It uses the `when` clause to ensure that the `ShowShapeInfo` treats a `Rectangle` object that has been assigned equal lengths and widths as a `Square` even if it hasn't been instantiated as a `Square` object.</span></span> <span data-ttu-id="7c45e-210">이 메서드는 `null`인 개체나 면적이 0인 도형에 대한 정보를 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-210">The method doesn't attempt to display information either about an object that is `null` or a shape whose area is zero.</span></span>

[!code-csharp[when-clause#1](~/samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]

<span data-ttu-id="7c45e-211">`Shape` 개체가 `null`인지 여부를 테스트하는 예제의 `when` 절은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-211">Note that the `when` clause in the example that attempts to test whether a `Shape` object is `null` doesn't execute.</span></span> <span data-ttu-id="7c45e-212">`null`인지 테스트하는 올바른 형식 패턴은 `case null:`입니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-212">The correct type pattern to test for a `null` is `case null:`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7c45e-213">C# 언어 사양</span><span class="sxs-lookup"><span data-stu-id="7c45e-213">C# language specification</span></span>

<span data-ttu-id="7c45e-214">자세한 내용은 [C# 언어 사양](/dotnet/csharp/language-reference/language-specification/introduction)의 [switch 문](~/_csharplang/spec/statements.md#the-switch-statement)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7c45e-214">For more information, see [The switch statement](~/_csharplang/spec/statements.md#the-switch-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="7c45e-215">언어 사양은 C# 구문 및 사용법에 대 한 신뢰할 수 있는 소스 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c45e-215">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="7c45e-216">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7c45e-216">See also</span></span>

- [<span data-ttu-id="7c45e-217">C# 참조</span><span class="sxs-lookup"><span data-stu-id="7c45e-217">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7c45e-218">C# 프로그래밍 가이드</span><span class="sxs-lookup"><span data-stu-id="7c45e-218">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7c45e-219">C# 키워드</span><span class="sxs-lookup"><span data-stu-id="7c45e-219">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="7c45e-220">if-else</span><span class="sxs-lookup"><span data-stu-id="7c45e-220">if-else</span></span>](if-else.md)
- [<span data-ttu-id="7c45e-221">패턴 일치</span><span class="sxs-lookup"><span data-stu-id="7c45e-221">Pattern Matching</span></span>](../../pattern-matching.md)
