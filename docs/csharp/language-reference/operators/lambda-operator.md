---
title: '>= 연산자 - C# 참조'
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: 30e1a3546f83a0a1ba5b1363238878868e94ab93
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063135"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="74152-102">=> 연산자(C# 참조)</span><span class="sxs-lookup"><span data-stu-id="74152-102">=> operator (C# reference)</span></span>

<span data-ttu-id="74152-103">`=>` 토큰은 [람다 연산자](#lambda-operator)와 [식 본문 정의](#expression-body-definition)의 멤버 이름과 멤버 구현의 구분자라는 두 가지 형식으로 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="74152-103">The `=>` token is supported in two forms: as the [lambda operator](#lambda-operator) and as a separator of a member name and the member implementation in an [expression body definition](#expression-body-definition).</span></span>

## <a name="lambda-operator"></a><span data-ttu-id="74152-104">람다 연산자</span><span class="sxs-lookup"><span data-stu-id="74152-104">Lambda operator</span></span>

<span data-ttu-id="74152-105">[람다 식](lambda-expressions.md)에서 람다 연산자 `=>`은 왼쪽의 입력 매개 변수를 오른쪽의 람다 본문과 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="74152-105">In [lambda expressions](lambda-expressions.md), the lambda operator `=>` separates the input parameters on the left side from the lambda body on the right side.</span></span>

<span data-ttu-id="74152-106">다음 예제에서는 메서드 구문이 포함된 [LINQ](../../programming-guide/concepts/linq/index.md) 기능을 사용하여 람다 식의 사용법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="74152-106">The following example uses the [LINQ](../../programming-guide/concepts/linq/index.md) feature with method syntax to demonstrate the usage of lambda expressions:</span></span>

[!code-csharp-interactive[infer types of input variables](snippets/shared/LambdaOperator.cs#InferredTypes)]

<span data-ttu-id="74152-107">람다 식의 입력 매개 변수는 컴파일 시 강력한 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="74152-107">Input parameters of a lambda expression are strongly typed at compile time.</span></span> <span data-ttu-id="74152-108">위의 예제와 같이 컴파일러가 입력 매개 변수의 형식을 추론하는 경우, 형식 선언을 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74152-108">When the compiler can infer the types of input parameters, like in the preceding example, you may omit type declarations.</span></span> <span data-ttu-id="74152-109">입력 매개 변수의 형식을 지정해야 하는 경우 다음 예제와 같이 각 매개 변수에 대해 입력매개 변수를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74152-109">If you need to specify the type of input parameters, you must do that for each parameter, as the following example shows:</span></span>

[!code-csharp-interactive[specify types of input variables](snippets/shared/LambdaOperator.cs#ExplicitTypes)]

<span data-ttu-id="74152-110">다음 예제에서는 입력 매개 변수 없이 람다 식을 정의하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="74152-110">The following example shows how to define a lambda expression without input parameters:</span></span>

[!code-csharp-interactive[without input variables](snippets/shared/LambdaOperator.cs#WithoutInput)]

<span data-ttu-id="74152-111">자세한 내용은 [람다 식](lambda-expressions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="74152-111">For more information, see [Lambda expressions](lambda-expressions.md).</span></span>

## <a name="expression-body-definition"></a><span data-ttu-id="74152-112">식 본문 정의</span><span class="sxs-lookup"><span data-stu-id="74152-112">Expression body definition</span></span>

<span data-ttu-id="74152-113">식 본문 정의의 일반 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="74152-113">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="74152-114">여기서 `expression`은(는) 유효한 식입니다.</span><span class="sxs-lookup"><span data-stu-id="74152-114">where `expression` is a valid expression.</span></span> <span data-ttu-id="74152-115">`expression`의 반환 형식은 구성원의 반환 형식으로 암시적으로 변환할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74152-115">The return type of `expression` must be implicitly convertible to the member's return type.</span></span> <span data-ttu-id="74152-116">멤버의 반환 형식이 `void`거나 구성원이 생성자, 종료자, 속성 또는 인덱서 `set` 접근자인 경우 `expression`은 [‘식 문’](~/_csharplang/spec/statements.md#expression-statements)이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74152-116">If the member's return type is `void` or if the member is a constructor, a finalizer, or a property or indexer `set` accessor, `expression` must be a [*statement expression*](~/_csharplang/spec/statements.md#expression-statements).</span></span> <span data-ttu-id="74152-117">식의 결과는 삭제되므로 해당 식의 반환 형식은 어떤 형식도 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74152-117">Because the expression's result is discarded, the return type of that expression can be any type.</span></span>

<span data-ttu-id="74152-118">다음 예제에서는 `Person.ToString` 메서드에 대한 식 본문 정의를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="74152-118">The following example shows an expression body definition for a `Person.ToString` method:</span></span>

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

<span data-ttu-id="74152-119">다음과 같은 메서드 정의의 약식 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="74152-119">It's a shorthand version of the following method definition:</span></span>

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```

<span data-ttu-id="74152-120">메서드, 연산자 및 읽기 전용 속성에 대한 식 본문 정의는 C# 6부터 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="74152-120">Expression body definitions for methods, operators, and read-only properties are supported beginning with C# 6.</span></span> <span data-ttu-id="74152-121">생성자, 종료자, 속성 및 인덱서 접근자에 대한 식 본문 정의는 C# 7.0부터 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="74152-121">Expression body definitions for constructors, finalizers, and property and indexer accessors are supported beginning with C# 7.0.</span></span>

<span data-ttu-id="74152-122">자세한 내용은 [식 본문 멤버](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="74152-122">For more information, see [Expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="74152-123">연산자 오버로드 가능성</span><span class="sxs-lookup"><span data-stu-id="74152-123">Operator overloadability</span></span>

<span data-ttu-id="74152-124">`=>` 연산자를 오버로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="74152-124">The `=>` operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="74152-125">C# 언어 사양</span><span class="sxs-lookup"><span data-stu-id="74152-125">C# language specification</span></span>

<span data-ttu-id="74152-126">람다 연산자에 대한 자세한 내용은 [C# 언어 사양](~/_csharplang/spec/introduction.md)의 [익명 함수 식](~/_csharplang/spec/expressions.md#anonymous-function-expressions) 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="74152-126">For more information about the lambda operator, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="74152-127">참조</span><span class="sxs-lookup"><span data-stu-id="74152-127">See also</span></span>

- [<span data-ttu-id="74152-128">C# 참조</span><span class="sxs-lookup"><span data-stu-id="74152-128">C# reference</span></span>](../index.md)
- [<span data-ttu-id="74152-129">C# 연산자 및 식</span><span class="sxs-lookup"><span data-stu-id="74152-129">C# operators and expressions</span></span>](index.md)
