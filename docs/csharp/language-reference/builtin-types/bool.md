---
description: C#의 기본 제공 부울 형식에 관한 자세한 정보
title: char 형식 - C# 참조
ms.date: 11/26/2019
f1_keywords:
- bool
- bool_CSharpKeyword
- "true"
- "false"
- true_CSharpKeyword
- false_CSharpKeyword
helpviewer_keywords:
- bool data type [C#]
- Boolean [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: e74fd76fcb19faa5860e48140da0fbd3db4afa47
ms.sourcegitcommit: 870bc4b4087510f6fba3c7b1c0d391f02bcc1f3e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2020
ms.locfileid: "92471891"
---
# <a name="bool-c-reference"></a><span data-ttu-id="5d5cd-103">bool(C# 참조)</span><span class="sxs-lookup"><span data-stu-id="5d5cd-103">bool (C# reference)</span></span>

<span data-ttu-id="5d5cd-104">`bool` 형식 키워드는 부울 값(`true` 또는 `false`)을 나타내는 .NET <xref:System.Boolean?displayProperty=nameWithType> 구조체 형식의 별칭입니다.</span><span class="sxs-lookup"><span data-stu-id="5d5cd-104">The `bool` type keyword is an alias for the .NET <xref:System.Boolean?displayProperty=nameWithType> structure type that represents a Boolean value, which can be either `true` or `false`.</span></span>

<span data-ttu-id="5d5cd-105">`bool` 형식의 값을 사용하여 논리 연산을 수행하려면 [부울 논리](../operators/boolean-logical-operators.md) 연산자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5d5cd-105">To perform logical operations with values of the `bool` type, use [Boolean logical](../operators/boolean-logical-operators.md) operators.</span></span> <span data-ttu-id="5d5cd-106">`bool` 형식은 [비교](../operators/comparison-operators.md) 및 [같음](../operators/equality-operators.md) 연산자의 결과 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="5d5cd-106">The `bool` type is the result type of [comparison](../operators/comparison-operators.md) and [equality](../operators/equality-operators.md) operators.</span></span> <span data-ttu-id="5d5cd-107">`bool` 식은 [if](../keywords/if-else.md), [do](../keywords/do.md), [while](../keywords/while.md) 및 [for](../keywords/for.md) 문과 [조건부 연산자`?:`](../operators/conditional-operator.md)에서 제어하는 조건식입니다.</span><span class="sxs-lookup"><span data-stu-id="5d5cd-107">A `bool` expression can be a controlling conditional expression in the [if](../keywords/if-else.md), [do](../keywords/do.md), [while](../keywords/while.md), and [for](../keywords/for.md) statements and in the [conditional operator `?:`](../operators/conditional-operator.md).</span></span>

<span data-ttu-id="5d5cd-108">`bool` 형식의 기본값은 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="5d5cd-108">The default value of the `bool` type is `false`.</span></span>

## <a name="literals"></a><span data-ttu-id="5d5cd-109">리터럴</span><span class="sxs-lookup"><span data-stu-id="5d5cd-109">Literals</span></span>

<span data-ttu-id="5d5cd-110">`true` 및 `false` 리터럴을 사용하여 `bool` 변수를 초기화하거나 `bool` 값을 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d5cd-110">You can use the `true` and `false` literals to initialize a `bool` variable or to pass a `bool` value:</span></span>

[!code-csharp-interactive[bool literals](snippets/shared/BoolType.cs#Literals)]

## <a name="three-valued-boolean-logic"></a><span data-ttu-id="5d5cd-111">값이 세 개인 부울 논리</span><span class="sxs-lookup"><span data-stu-id="5d5cd-111">Three-valued Boolean logic</span></span>

<span data-ttu-id="5d5cd-112">예를 들어 값이 세 개인 논리를 지원해야 하는 경우(예: 값이 세 개인 부울 형식을 지원하는 데이터베이스에서 작업하는 경우) nullable `bool?` 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5d5cd-112">Use the nullable `bool?` type, if you need to support the three-valued logic, for example, when you work with databases that support a three-valued Boolean type.</span></span> <span data-ttu-id="5d5cd-113">`bool?` 피연산자의 경우 미리 정의된 `&` 및 `|` 연산자는 값이 세 개인 논리를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="5d5cd-113">For the `bool?` operands, the predefined `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="5d5cd-114">자세한 내용은 [부울 논리 연산자](../operators/boolean-logical-operators.md) 문서의 [Nullable 부울 논리 연산자](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5d5cd-114">For more information, see the [Nullable Boolean logical operators](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../operators/boolean-logical-operators.md) article.</span></span>

<span data-ttu-id="5d5cd-115">nullable 값 형식에 대한 자세한 내용은 [Nullable 값 형식](nullable-value-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5d5cd-115">For more information about nullable value types, see [Nullable value types](nullable-value-types.md).</span></span>

## <a name="conversions"></a><span data-ttu-id="5d5cd-116">변환</span><span class="sxs-lookup"><span data-stu-id="5d5cd-116">Conversions</span></span>

<span data-ttu-id="5d5cd-117">C#는 `bool` 형식을 포함하는 두 개의 변환만 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5d5cd-117">C# provides only two conversions that involve the `bool` type.</span></span> <span data-ttu-id="5d5cd-118">여기에는 해당하는 nullable `bool?` 형식으로의 암시적 변환과 `bool?` 형식에서의 명시적 변환이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d5cd-118">Those are an implicit conversion to the corresponding nullable `bool?` type and an explicit conversion from the `bool?` type.</span></span> <span data-ttu-id="5d5cd-119">그러나 .NET에서는 `bool` 형식으로 변환하거나 해당 형식에서 변환하는 데 사용할 수 있는 추가 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5d5cd-119">However, .NET provides additional methods that you can use to convert to or from the `bool` type.</span></span> <span data-ttu-id="5d5cd-120">자세한 내용은 <xref:System.Boolean?displayProperty=nameWithType> API 참조 페이지의 [부울 값 사이의 변환](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5d5cd-120">For more information, see the [Converting to and from Boolean values](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) section of the <xref:System.Boolean?displayProperty=nameWithType> API reference page.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="5d5cd-121">C# 언어 사양</span><span class="sxs-lookup"><span data-stu-id="5d5cd-121">C# language specification</span></span>

<span data-ttu-id="5d5cd-122">자세한 내용은 [C# 언어 사양](~/_csharplang/spec/introduction.md)의 [bool 형식](~/_csharplang/spec/types.md#the-bool-type) 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5d5cd-122">For more information, see [The bool type](~/_csharplang/spec/types.md#the-bool-type) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5d5cd-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5d5cd-123">See also</span></span>

- [<span data-ttu-id="5d5cd-124">C# 참조</span><span class="sxs-lookup"><span data-stu-id="5d5cd-124">C# reference</span></span>](../index.md)
- [<span data-ttu-id="5d5cd-125">값 형식</span><span class="sxs-lookup"><span data-stu-id="5d5cd-125">Value types</span></span>](value-types.md)
- [<span data-ttu-id="5d5cd-126">true 및 false 연산자</span><span class="sxs-lookup"><span data-stu-id="5d5cd-126">true and false operators</span></span>](../operators/true-false-operators.md)
