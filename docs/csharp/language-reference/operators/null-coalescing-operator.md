---
title: ?? 및 ??= 연산자 - C# 참조
ms.date: 09/10/2019
f1_keywords:
- ??_CSharpKeyword
- ??=_CSharpKeyword
helpviewer_keywords:
- null-coalescing operator [C#]
- ?? operator [C#]
- null-coalescing assignment [C#]
- ??= operator [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: 58c60dad3badc62f850f737a3d210ec486809272
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916734"
---
# <a name="-and--operators-c-reference"></a><span data-ttu-id="d356c-103">??</span><span class="sxs-lookup"><span data-stu-id="d356c-103">??</span></span> <span data-ttu-id="d356c-104">및 ??= 연산자(C# 참조)</span><span class="sxs-lookup"><span data-stu-id="d356c-104">and ??= operators (C# reference)</span></span>

<span data-ttu-id="d356c-105">null 병합 연산자 `??`는 `null`이 아닌 경우 왼쪽 피연산자의 값을 반환합니다. 그렇지 않으면 오른쪽 피연자를 평가하고 그 결과를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d356c-105">The null-coalescing operator `??` returns the value of its left-hand operand if it isn't `null`; otherwise, it evaluates the right-hand operand and returns its result.</span></span> <span data-ttu-id="d356c-106">왼쪽 피연산자가 null이 아닌 것으로 평가되면 `??` 연산자는 오른쪽 피연산자를 평가하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d356c-106">The `??` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

<span data-ttu-id="d356c-107">C# 8.0 이상에서 사용할 수 있는 null 병합 할당 연산자 `??=`는 왼쪽 피연산자가 `null`로 계산되는 경우에만 오른쪽 피연산자의 값을 왼쪽 피연산자에 대입합니다.</span><span class="sxs-lookup"><span data-stu-id="d356c-107">Available in C# 8.0 and later, the null-coalescing assignment operator `??=` assigns the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span> <span data-ttu-id="d356c-108">왼쪽 피연산자가 null이 아닌 것으로 평가되면 `??=` 연산자는 오른쪽 피연산자를 평가하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d356c-108">The `??=` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

[!code-csharp[null-coalescing assignment](snippets/shared/NullCoalescingOperator.cs#Assignment)]

<span data-ttu-id="d356c-109">`??=` 연산자의 왼쪽 피연산자는 변수, [속성](../../programming-guide/classes-and-structs/properties.md) 또는 [인덱서](../../programming-guide/indexers/index.md) 요소여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d356c-109">The left-hand operand of the `??=` operator must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../programming-guide/indexers/index.md) element.</span></span>

<span data-ttu-id="d356c-110">C# 7.3 이전 버전에서 `??` 연산자의 왼쪽 피연산자 형식은 [참조 형식](../keywords/reference-types.md) 또는 [Nullable 값 형식](../builtin-types/nullable-value-types.md)이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d356c-110">In C# 7.3 and earlier, the type of the left-hand operand of the `??` operator must be either a [reference type](../keywords/reference-types.md) or a [nullable value type](../builtin-types/nullable-value-types.md).</span></span> <span data-ttu-id="d356c-111">C# 8.0부터 이 요구 사항이 다음과 같이 바뀝니다. `??` 및 `??=` 연산자의 왼쪽 피연산자 형식은 null을 허용하지 않는 값 형식일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d356c-111">Beginning with C# 8.0, that requirement is replaced with the following: the type of the left-hand operand of the `??` and `??=` operators cannot be a non-nullable value type.</span></span> <span data-ttu-id="d356c-112">특히 C# 8.0부터 비제한 형식 매개 변수와 함께 null 병합 연산자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d356c-112">In particular, beginning with C# 8.0, you can use the null-coalescing operators with unconstrained type parameters:</span></span>

[!code-csharp[unconstrained type parameter](snippets/shared/NullCoalescingOperator.cs#UnconstrainedType)]

<span data-ttu-id="d356c-113">null 병합 연산자는 오른쪽 결합입니다.</span><span class="sxs-lookup"><span data-stu-id="d356c-113">The null-coalescing operators are right-associative.</span></span> <span data-ttu-id="d356c-114">즉, 양식의 식이</span><span class="sxs-lookup"><span data-stu-id="d356c-114">That is, expressions of the form</span></span>

```csharp
a ?? b ?? c
d ??= e ??= f
```

<span data-ttu-id="d356c-115">다음과 같이 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="d356c-115">are evaluated as</span></span>

```csharp
a ?? (b ?? c)
d ??= (e ??= f)
```

## <a name="examples"></a><span data-ttu-id="d356c-116">예</span><span class="sxs-lookup"><span data-stu-id="d356c-116">Examples</span></span>

<span data-ttu-id="d356c-117">`??` 및 `??=` 연산자는 다음과 같은 시나리오에서 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d356c-117">The `??` and `??=` operators can be useful in the following scenarios:</span></span>

- <span data-ttu-id="d356c-118">[null 병합 연산자 ?. 및 ?[]](member-access-operators.md#null-conditional-operators--and-)가 있는 식에서 `??` 연산자를 사용하여 null 조건부 연산을 사용한 식의 결과가 `null`인 경우 평가하는 대체 식을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d356c-118">In expressions with the [null-conditional operators ?. and ?[]](member-access-operators.md#null-conditional-operators--and-), you can use the `??` operator to provide an alternative expression to evaluate in case the result of the expression with null-conditional operations is `null`:</span></span>

  [!code-csharp-interactive[with null-conditional](snippets/shared/NullCoalescingOperator.cs#WithNullConditional)]

- <span data-ttu-id="d356c-119">[nullable 값 형식](../builtin-types/nullable-value-types.md)을 사용하고 기본값 유형의 값을 제공해야 할 때 `??` 연산자를 사용하여 nullable 값이 `null`인 경우 제공할 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d356c-119">When you work with [nullable value types](../builtin-types/nullable-value-types.md) and need to provide a value of an underlying value type, use the `??` operator to specify the value to provide in case a nullable type value is `null`:</span></span>

  [!code-csharp-interactive[with nullable types](snippets/shared/NullCoalescingOperator.cs#WithNullableTypes)]

  <span data-ttu-id="d356c-120">nullable 형식 값이 `null`일 때 사용될 값이 기본 값 형식의 기본 값이어야 하는 경우 <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d356c-120">Use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method if the value to be used when a nullable type value is `null` should be the default value of the underlying value type.</span></span>

- <span data-ttu-id="d356c-121">C# 7.0부터 `??` 연산자의 오른쪽 피연산자로 [`throw` 식](../keywords/throw.md#the-throw-expression)을 사용하여 인수 확인 코드를 보다 간결하게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d356c-121">Beginning with C# 7.0, you can use a [`throw` expression](../keywords/throw.md#the-throw-expression) as the right-hand operand of the `??` operator to make the argument-checking code more concise:</span></span>

  [!code-csharp[with throw expression](snippets/shared/NullCoalescingOperator.cs#WithThrowExpression)]

  <span data-ttu-id="d356c-122">앞의 예제에서는 [식 본문 멤버](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)를 사용하여 속성을 정의하는 방법도 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="d356c-122">The preceding example also demonstrates how to use [expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) to define a property.</span></span>

- <span data-ttu-id="d356c-123">C# 8.0부터 `??=` 연산자를 사용하여 다음 양식의 코드를</span><span class="sxs-lookup"><span data-stu-id="d356c-123">Beginning with C# 8.0, you can use the `??=` operator to replace the code of the form</span></span>

  ```csharp
  if (variable is null)
  {
      variable = expression;
  }
  ```

  <span data-ttu-id="d356c-124">다음 코드와 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="d356c-124">with the following code:</span></span>

  ```csharp
  variable ??= expression;
  ```

## <a name="operator-overloadability"></a><span data-ttu-id="d356c-125">연산자 오버로드 가능성</span><span class="sxs-lookup"><span data-stu-id="d356c-125">Operator overloadability</span></span>

<span data-ttu-id="d356c-126">`??` 및 `??=` 연산자는 오버로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d356c-126">The operators `??` and `??=` cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d356c-127">C# 언어 사양</span><span class="sxs-lookup"><span data-stu-id="d356c-127">C# language specification</span></span>

<span data-ttu-id="d356c-128">`??` 연산자에 대한 자세한 내용은 [C# 언어 사양](~/_csharplang/spec/introduction.md)의 [null 병합 연산자](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d356c-128">For more information about the `??` operator, see [The null coalescing operator](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="d356c-129">`??=` 연산자에 대한 자세한 내용은 [기능 제안 노트](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d356c-129">For more information about the `??=` operator, see the [feature proposal note](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d356c-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d356c-130">See also</span></span>

- [<span data-ttu-id="d356c-131">C# 참조</span><span class="sxs-lookup"><span data-stu-id="d356c-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="d356c-132">C# 연산자 및 식</span><span class="sxs-lookup"><span data-stu-id="d356c-132">C# operators and expressions</span></span>](index.md)
- <span data-ttu-id="d356c-133">[?. 및 ?[] 연산자](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="d356c-133">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="d356c-134">?: 연산자</span><span class="sxs-lookup"><span data-stu-id="d356c-134">?: operator</span></span>](conditional-operator.md)
