---
description: in(제네릭 한정자) - C# 참조
title: in(제네릭 한정자) - C# 참조
ms.date: 07/20/2015
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.openlocfilehash: feae17be7bdf29f6bc90e8c85b3878d4714699f4
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89118457"
---
# <a name="in-generic-modifier-c-reference"></a><span data-ttu-id="40940-103">in(제네릭 한정자)(C# 참조)</span><span class="sxs-lookup"><span data-stu-id="40940-103">in (Generic Modifier) (C# Reference)</span></span>

<span data-ttu-id="40940-104">제네릭 형식 매개 변수에서 `in` 키워드는 형식 매개 변수를 반공변(contravariant)으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="40940-104">For generic type parameters, the `in` keyword specifies that the type parameter is contravariant.</span></span> <span data-ttu-id="40940-105">제네릭 인터페이스 및 대리자에서 `in` 키워드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40940-105">You can use the `in` keyword in generic interfaces and delegates.</span></span>

<span data-ttu-id="40940-106">반공변성(Contravariance)을 통해 제네릭 매개 변수에 지정된 것보다 적은 파생 형식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40940-106">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="40940-107">따라서 공변(contravariant) 인터페이스를 구현하는 클래스의 암시적 변환과 대리자 형식의 암시적 변환이 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="40940-107">This allows for implicit conversion of classes that implement contravariant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="40940-108">제네릭 형식 매개 변수의 공변성(Covariance) 및 반공변성(Contravariance)은 참조 형식에 대해 지원되고 값 형식에 대해서는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="40940-108">Covariance and contravariance in generic type parameters are supported for reference types, but they are not supported for value types.</span></span>

<span data-ttu-id="40940-109">메서드 매개 변수의 형식을 정의하고 메서드의 반환 형식을 정의하지 않는 경우에만 형식을 제네릭 인터페이스 또는 대리자에서 반공변(contravariant)으로 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40940-109">A type can be declared contravariant in a generic interface or delegate only if it defines the type of a method's parameters and not of a method's return type.</span></span> <span data-ttu-id="40940-110">`In`, `ref` 및 `out` 매개 변수는 고정이어야 합니다. 즉 공변(covariant) 또는 반공변(contravariant)입니다.</span><span class="sxs-lookup"><span data-stu-id="40940-110">`In`, `ref`, and `out` parameters must be invariant, meaning they are neither covariant or contravariant.</span></span>

<span data-ttu-id="40940-111">반공변(contravariant) 형식 매개 변수가 있는 인터페이스는 해당 메서드가 인터페이스 형식 매개 변수에 지정된 형식보다 덜 파생된 형식의 인수를 사용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="40940-111">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="40940-112">예를 들어 <xref:System.Collections.Generic.IComparer%601> 인터페이스에서 T 형식은 반공변(contravariant)이므로 `Employee`가 `Person`을 상속하는 경우 특수 변환 메서드를 사용하지 않고 `IComparer<Person>` 형식의 개체를 `IComparer<Employee>` 형식의 개체에 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40940-112">For example, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer<Person>` type to an object of the `IComparer<Employee>` type without using any special conversion methods if `Employee` inherits `Person`.</span></span>

<span data-ttu-id="40940-113">반공변(contravariant) 대리자에 동일한 형식의 다른 대리자를 할당할 수 있지만 덜 파생된 제네릭 형식 매개 변수가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="40940-113">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>

<span data-ttu-id="40940-114">자세한 내용은 [공변성(Covariance) 및 반공변성(Contravariance)](../../programming-guide/concepts/covariance-contravariance/index.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="40940-114">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

## <a name="contravariant-generic-interface"></a><span data-ttu-id="40940-115">반공변(contravariant) 제네릭 인터페이스</span><span class="sxs-lookup"><span data-stu-id="40940-115">Contravariant generic interface</span></span>

<span data-ttu-id="40940-116">다음 예제에서는 반공변(contravariant) 제네릭 인터페이스를 선언, 확장 및 구현하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="40940-116">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="40940-117">또한 이 인터페이스를 구현하는 클래스에 대해 암시적 변환을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="40940-117">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>

[!code-csharp[csVarianceKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#1)]

## <a name="contravariant-generic-delegate"></a><span data-ttu-id="40940-118">반공변(contravariant) 제네릭 대리자</span><span class="sxs-lookup"><span data-stu-id="40940-118">Contravariant generic delegate</span></span>

<span data-ttu-id="40940-119">다음 예제에서는 반공변(contravariant) 제네릭 대리자를 선언, 인스턴스화 및 호출하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="40940-119">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="40940-120">또한 대리자 형식을 암시적으로 변환하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="40940-120">It also shows how you can implicitly convert a delegate type.</span></span>

[!code-csharp[csVarianceKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="40940-121">C# 언어 사양</span><span class="sxs-lookup"><span data-stu-id="40940-121">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="40940-122">참조</span><span class="sxs-lookup"><span data-stu-id="40940-122">See also</span></span>

- [<span data-ttu-id="40940-123">out</span><span class="sxs-lookup"><span data-stu-id="40940-123">out</span></span>](out-generic-modifier.md)
- [<span data-ttu-id="40940-124">공 분산 및 반공 분산</span><span class="sxs-lookup"><span data-stu-id="40940-124">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)
- [<span data-ttu-id="40940-125">한정자</span><span class="sxs-lookup"><span data-stu-id="40940-125">Modifiers</span></span>](index.md)
