---
description: sealed 한정자 - C# 참조
title: sealed 한정자 - C# 참조
ms.date: 07/20/2015
f1_keywords:
- sealed
- sealed_CSharpKeyword
helpviewer_keywords:
- sealed keyword [C#]
ms.assetid: 8e4ed5d3-10be-47db-9488-0da2008e6f3f
ms.openlocfilehash: 5b945503c6f6546f571a2422ae77760da0363b08
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89136969"
---
# <a name="sealed-c-reference"></a><span data-ttu-id="8f0c1-103">sealed(C# 참조)</span><span class="sxs-lookup"><span data-stu-id="8f0c1-103">sealed (C# Reference)</span></span>

<span data-ttu-id="8f0c1-104">클래스에 적용된 경우 `sealed` 한정자는 다른 클래스가 해당 클래스에서 상속하지 못하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0c1-104">When applied to a class, the `sealed` modifier prevents other classes from inheriting from it.</span></span> <span data-ttu-id="8f0c1-105">다음 예제에서 `B` 클래스는 `A` 클래스에서 상속하지만 `B` 클래스에서 상속할 수 있는 클래스는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8f0c1-105">In the following example, class `B` inherits from class `A`, but no class can inherit from class `B`.</span></span>

```csharp
class A {}
sealed class B : A {}
```

<span data-ttu-id="8f0c1-106">기본 클래스의 가상 메서드 또는 속성을 재정의하는 메서드 또는 속성에 `sealed` 한정자를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f0c1-106">You can also use the `sealed` modifier on a method or property that overrides a virtual method or property in a base class.</span></span> <span data-ttu-id="8f0c1-107">이렇게 하면 사용자 클래스에서 클래스가 파생되고 특정 가상 메서드 또는 속성을 재정의하지 못하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f0c1-107">This enables you to allow classes to derive from your class and prevent them from overriding specific virtual methods or properties.</span></span>

## <a name="example"></a><span data-ttu-id="8f0c1-108">예제</span><span class="sxs-lookup"><span data-stu-id="8f0c1-108">Example</span></span>

<span data-ttu-id="8f0c1-109">다음 예제에서 `Z`는 `Y`에서 상속하지만 `Z`는 `X`에서 선언되고 `Y`에서 봉인된 가상 함수 `F`를 재정의할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8f0c1-109">In the following example, `Z` inherits from `Y` but `Z` cannot override the virtual function `F` that is declared in `X` and sealed in `Y`.</span></span>

[!code-csharp[csrefKeywordsModifiers#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#16)]

<span data-ttu-id="8f0c1-110">클래스에서 새 메서드 또는 속성을 정의할 때 [virtual](virtual.md)로 선언하지 않으면 파생 클래스가 재정의하지 못하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f0c1-110">When you define new methods or properties in a class, you can prevent deriving classes from overriding them by not declaring them as [virtual](virtual.md).</span></span>

<span data-ttu-id="8f0c1-111">추상 클래스는 추상 메서드 또는 속성 구현을 제공하는 클래스에 상속되어야 하므로 봉인 클래스에 [abstract](abstract.md) 한정자를 사용하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0c1-111">It is an error to use the [abstract](abstract.md) modifier with a sealed class, because an abstract class must be inherited by a class that provides an implementation of the abstract methods or properties.</span></span>

<span data-ttu-id="8f0c1-112">메서드 또는 속성에 적용된 경우 `sealed` 한정자는 항상 [override](override.md)와 함께 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0c1-112">When applied to a method or property, the `sealed` modifier must always be used with [override](override.md).</span></span>

<span data-ttu-id="8f0c1-113">구조체는 암시적으로 봉인되므로 상속할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8f0c1-113">Because structs are implicitly sealed, they cannot be inherited.</span></span>

<span data-ttu-id="8f0c1-114">자세한 내용은 [상속](../../programming-guide/classes-and-structs/inheritance.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8f0c1-114">For more information, see [Inheritance](../../programming-guide/classes-and-structs/inheritance.md).</span></span>

<span data-ttu-id="8f0c1-115">더 많은 예제를 보려면 [추상 및 봉인 클래스와 클래스 멤버](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8f0c1-115">For more examples, see [Abstract and Sealed Classes and Class Members](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>

## <a name="example"></a><span data-ttu-id="8f0c1-116">예제</span><span class="sxs-lookup"><span data-stu-id="8f0c1-116">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#17)]

<span data-ttu-id="8f0c1-117">앞의 예제에서 다음 문을 사용하여 봉인된 클래스에서 상속을 시도할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f0c1-117">In the previous example, you might try to inherit from the sealed class by using the following statement:</span></span>

`class MyDerivedC: SealedClass {}   // Error`

<span data-ttu-id="8f0c1-118">그 결과 다음 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f0c1-118">The result is an error message:</span></span>

`'MyDerivedC': cannot derive from sealed type 'SealedClass'`

## <a name="remarks"></a><span data-ttu-id="8f0c1-119">설명</span><span class="sxs-lookup"><span data-stu-id="8f0c1-119">Remarks</span></span>

<span data-ttu-id="8f0c1-120">클래스, 메서드 또는 속성을 봉인할지 여부를 결정하려면 일반적으로 다음 두 가지 사항을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f0c1-120">To determine whether to seal a class, method, or property, you should generally consider the following two points:</span></span>

- <span data-ttu-id="8f0c1-121">파생 클래스가 사용자 클래스의 사용자 지정을 통해 얻을 수 있는 잠재적인 이점</span><span class="sxs-lookup"><span data-stu-id="8f0c1-121">The potential benefits that deriving classes might gain through the ability to customize your class.</span></span>

- <span data-ttu-id="8f0c1-122">파생 클래스가 사용자 클래스를 수정하여 더 이상 올바르게 또는 예상대로 작동하지 않을 가능성</span><span class="sxs-lookup"><span data-stu-id="8f0c1-122">The potential that deriving classes could modify your classes in such a way that they would no longer work correctly or as expected.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8f0c1-123">C# 언어 사양</span><span class="sxs-lookup"><span data-stu-id="8f0c1-123">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="8f0c1-124">참조</span><span class="sxs-lookup"><span data-stu-id="8f0c1-124">See also</span></span>

- [<span data-ttu-id="8f0c1-125">C# 참조</span><span class="sxs-lookup"><span data-stu-id="8f0c1-125">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8f0c1-126">C# 프로그래밍 가이드</span><span class="sxs-lookup"><span data-stu-id="8f0c1-126">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8f0c1-127">C# 키워드</span><span class="sxs-lookup"><span data-stu-id="8f0c1-127">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="8f0c1-128">정적 클래스 및 정적 클래스 멤버</span><span class="sxs-lookup"><span data-stu-id="8f0c1-128">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [<span data-ttu-id="8f0c1-129">추상/봉인된 클래스 및 클래스 멤버</span><span class="sxs-lookup"><span data-stu-id="8f0c1-129">Abstract and Sealed Classes and Class Members</span></span>](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="8f0c1-130">액세스 한정자</span><span class="sxs-lookup"><span data-stu-id="8f0c1-130">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="8f0c1-131">한정자</span><span class="sxs-lookup"><span data-stu-id="8f0c1-131">Modifiers</span></span>](index.md)
- [<span data-ttu-id="8f0c1-132">override</span><span class="sxs-lookup"><span data-stu-id="8f0c1-132">override</span></span>](override.md)
- [<span data-ttu-id="8f0c1-133">virtual</span><span class="sxs-lookup"><span data-stu-id="8f0c1-133">virtual</span></span>](virtual.md)
