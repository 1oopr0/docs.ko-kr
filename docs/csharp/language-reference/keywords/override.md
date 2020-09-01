---
description: override 한정자 - C# 참조
title: override 한정자 - C# 참조
ms.date: 07/20/2015
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: 51ca806310214981b7ff24a796fe078d902dca4d
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134461"
---
# <a name="override-c-reference"></a><span data-ttu-id="9ef06-103">override(C# 참조)</span><span class="sxs-lookup"><span data-stu-id="9ef06-103">override (C# Reference)</span></span>

<span data-ttu-id="9ef06-104">`override` 한정자는 상속된 메서드, 속성, 인덱서 또는 이벤트의 추상 또는 가상 구현을 확장하거나 수정하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="9ef06-104">The `override` modifier is required to extend or modify the abstract or virtual implementation of an inherited method, property, indexer, or event.</span></span>

## <a name="example"></a><span data-ttu-id="9ef06-105">예제</span><span class="sxs-lookup"><span data-stu-id="9ef06-105">Example</span></span>

<span data-ttu-id="9ef06-106">이 예에서 `Square` 클래스는 `GetArea`가 추상 `Shape` 클래스에서 상속되기 때문에 `GetArea`의 재정의된 구현을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ef06-106">In this example, the `Square` class must provide an overridden implementation of `GetArea` because `GetArea` is inherited from the abstract `Shape` class:</span></span>

[!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]

<span data-ttu-id="9ef06-107">`override` 메서드는 기본 클래스에서 상속된 멤버의 새 구현을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9ef06-107">An `override` method provides a new implementation of a member that is inherited from a base class.</span></span> <span data-ttu-id="9ef06-108">`override` 선언에서 재정의된 메서드를 재정의된 기본 메서드라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ef06-108">The method that is overridden by an `override` declaration is known as the overridden base method.</span></span> <span data-ttu-id="9ef06-109">재정의된 기본 메서드에는 `override` 메서드와 동일한 시그니처가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ef06-109">The overridden base method must have the same signature as the `override` method.</span></span> <span data-ttu-id="9ef06-110">상속에 대한 자세한 내용은 [상속](../../programming-guide/classes-and-structs/inheritance.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9ef06-110">For information about inheritance, see [Inheritance](../../programming-guide/classes-and-structs/inheritance.md).</span></span>

<span data-ttu-id="9ef06-111">비가상 또는 정적 메서드는 재정의할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9ef06-111">You cannot override a non-virtual or static method.</span></span> <span data-ttu-id="9ef06-112">재정의된 기본 메서드는 `virtual`, `abstract` 또는 `override`여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ef06-112">The overridden base method must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="9ef06-113">`override` 선언에서는 `virtual` 메서드의 액세스 가능성을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9ef06-113">An `override` declaration cannot change the accessibility of the `virtual` method.</span></span> <span data-ttu-id="9ef06-114">`override` 메서드 및 `virtual` 메서드 둘 다에 동일한 [액세스 수준 한정자](access-modifiers.md)가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ef06-114">Both the `override` method and the `virtual` method must have the same [access level modifier](access-modifiers.md).</span></span>

<span data-ttu-id="9ef06-115">`new`, `static` 또는 `virtual` 한정자를 사용하여 `override` 메서드를 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9ef06-115">You cannot use the `new`, `static`, or `virtual` modifiers to modify an `override` method.</span></span>

<span data-ttu-id="9ef06-116">재정의 속성 선언은 상속된 속성과 동일한 액세스 한정자, 형식 및 이름을 지정해야 하고, 재정의된 속성은 `virtual`, `abstract` 또는 `override`여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ef06-116">An overriding property declaration must specify exactly the same access modifier, type, and name as the inherited property, and the overridden property must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="9ef06-117">`override` 키워드 사용 방법에 대한 자세한 내용은 [Override 및 New 키워드를 사용하여 버전 관리](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) 및 [Override 및 New 키워드를 사용해야 하는 경우](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9ef06-117">For more information about how to use the `override` keyword, see [Versioning with the Override and New Keywords](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing when to use Override and New Keywords](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>

## <a name="example"></a><span data-ttu-id="9ef06-118">예제</span><span class="sxs-lookup"><span data-stu-id="9ef06-118">Example</span></span>

<span data-ttu-id="9ef06-119">이 예제에서는 `Employee`라는 기본 클래스와 `SalesEmployee`라는 파생 클래스를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="9ef06-119">This example defines a base class named `Employee`, and a derived class named `SalesEmployee`.</span></span> <span data-ttu-id="9ef06-120">`SalesEmployee` 클래스에는 추가 필드 `salesbonus`가 포함되어 있고, 이를 고려하기 위해 `CalculatePay` 메서드를 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="9ef06-120">The `SalesEmployee` class includes an extra field, `salesbonus`, and overrides the method `CalculatePay` in order to take it into account.</span></span>

[!code-csharp[csrefKeywordsModifiers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="9ef06-121">C# 언어 사양</span><span class="sxs-lookup"><span data-stu-id="9ef06-121">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="9ef06-122">참조</span><span class="sxs-lookup"><span data-stu-id="9ef06-122">See also</span></span>

- [<span data-ttu-id="9ef06-123">C# 참조</span><span class="sxs-lookup"><span data-stu-id="9ef06-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9ef06-124">C# 프로그래밍 가이드</span><span class="sxs-lookup"><span data-stu-id="9ef06-124">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9ef06-125">상속</span><span class="sxs-lookup"><span data-stu-id="9ef06-125">Inheritance</span></span>](../../programming-guide/classes-and-structs/inheritance.md)
- [<span data-ttu-id="9ef06-126">C# 키워드</span><span class="sxs-lookup"><span data-stu-id="9ef06-126">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="9ef06-127">한정자</span><span class="sxs-lookup"><span data-stu-id="9ef06-127">Modifiers</span></span>](index.md)
- [<span data-ttu-id="9ef06-128">abstract</span><span class="sxs-lookup"><span data-stu-id="9ef06-128">abstract</span></span>](abstract.md)
- [<span data-ttu-id="9ef06-129">virtual</span><span class="sxs-lookup"><span data-stu-id="9ef06-129">virtual</span></span>](virtual.md)
- [<span data-ttu-id="9ef06-130">new(한정자)</span><span class="sxs-lookup"><span data-stu-id="9ef06-130">new (modifier)</span></span>](new-modifier.md)
- [<span data-ttu-id="9ef06-131">다형성</span><span class="sxs-lookup"><span data-stu-id="9ef06-131">Polymorphism</span></span>](../../programming-guide/classes-and-structs/polymorphism.md)
