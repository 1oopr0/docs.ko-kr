---
title: new 한정자 - C# 참조
ms.date: 07/20/2015
helpviewer_keywords:
- new modifier keyword [C#]
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
ms.openlocfilehash: 529d77b0a66a8a3cedfe7a400af0fb34dd653322
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795172"
---
# <a name="new-modifier-c-reference"></a><span data-ttu-id="4a3aa-102">new 한정자(C# 참조)</span><span class="sxs-lookup"><span data-stu-id="4a3aa-102">new modifier (C# Reference)</span></span>

<span data-ttu-id="4a3aa-103">선언 한정자로 사용되는 `new` 키워드는 기본 클래스에서 상속된 멤버를 명시적으로 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="4a3aa-103">When used as a declaration modifier, the `new` keyword explicitly hides a member that is inherited from a base class.</span></span> <span data-ttu-id="4a3aa-104">상속된 멤버를 숨기면 파생 버전의 멤버로 기본 클래스 버전의 멤버를 대신하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a3aa-104">When you hide an inherited member, the derived version of the member replaces the base class version.</span></span> <span data-ttu-id="4a3aa-105">`new` 한정자를 사용하지 않고 멤버를 숨길 수도 있지만 컴파일러 경고가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="4a3aa-105">Although you can hide members without using the `new` modifier, you get a compiler warning.</span></span> <span data-ttu-id="4a3aa-106">`new`를 사용하여 멤버를 명시적으로 숨기면 이 경고가 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4a3aa-106">If you use `new` to explicitly hide a member, it suppresses this warning.</span></span>

<span data-ttu-id="4a3aa-107">`new` 키워드를 사용하여 [형식의 인스턴스를 만들](../operators/new-operator.md)거나 [제네릭 형식 제약 조건](./new-constraint.md)으로 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a3aa-107">You can also use the `new` keyword to [create an instance of a type](../operators/new-operator.md) or as a [generic type constraint](./new-constraint.md).</span></span>

<span data-ttu-id="4a3aa-108">상속된 멤버를 숨기려면 동일한 멤버 이름을 사용하여 파생된 클래스에 해당 멤버를 선언한 다음 `new` 키워드를 사용하여 이를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="4a3aa-108">To hide an inherited member, declare it in the derived class by using the same member name, and modify it with the `new` keyword.</span></span> <span data-ttu-id="4a3aa-109">예를 들어:</span><span class="sxs-lookup"><span data-stu-id="4a3aa-109">For example:</span></span>

[!code-csharp[csrefKeywordsOperator#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#8)]

<span data-ttu-id="4a3aa-110">이 예제에서 `BaseC.Invoke`는 `DerivedC.Invoke`에 의해 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="4a3aa-110">In this example, `BaseC.Invoke` is hidden by `DerivedC.Invoke`.</span></span> <span data-ttu-id="4a3aa-111">`x` 필드는 비슷한 이름으로 숨겨져 있지 않기 때문에 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4a3aa-111">The field `x` is not affected because it is not hidden by a similar name.</span></span>

<span data-ttu-id="4a3aa-112">상속을 사용한 이름 숨기기는 다음 중 한 가지 형식을 취합니다.</span><span class="sxs-lookup"><span data-stu-id="4a3aa-112">Name hiding through inheritance takes one of the following forms:</span></span>

- <span data-ttu-id="4a3aa-113">일반적으로 클래스 또는 구조체에 파생된 상수, 필드, 속성 또는 형식은 동일한 이름의 모든 기본 클래스 멤버를 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="4a3aa-113">Generally, a constant, field, property, or type that is introduced in a class or struct hides all base class members that share its name.</span></span> <span data-ttu-id="4a3aa-114">이 사항이 적용되지 않는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a3aa-114">There are special cases.</span></span> <span data-ttu-id="4a3aa-115">예를 들어 호출할 수 없는 형식이 포함된 `N`이라는 이름의 새 필드를 선언하고 기본 형식에서 `N`을 메서드로 선언하면 새 필드가 호출 구문에서 기본 선언을 숨기지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4a3aa-115">For example, if you declare a new field with name `N` to have a type that is not invocable, and a base type declares `N` to be a method, the new field does not hide the base declaration in invocation syntax.</span></span> <span data-ttu-id="4a3aa-116">자세한 내용은 [C# 언어 사양](~/_csharplang/spec/introduction.md)의 [멤버 조회](~/_csharplang/spec/expressions.md#member-lookup) 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4a3aa-116">For more information, see the [Member lookup](~/_csharplang/spec/expressions.md#member-lookup) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

- <span data-ttu-id="4a3aa-117">클래스 또는 구조체에 파생된 메서드는 기본 클래스에서 동일한 이름의 속성, 필드 및 형식을 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="4a3aa-117">A method introduced in a class or struct hides properties, fields, and types that share that name in the base class.</span></span> <span data-ttu-id="4a3aa-118">또한 시그니처가 동일한 기본 클래스 메서드도 모두 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="4a3aa-118">It also hides all base class methods that have the same signature.</span></span>

- <span data-ttu-id="4a3aa-119">클래스 또는 구조체에 파생된 인덱서는 시그니처가 동일한 기본 클래스 인덱서를 모두 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="4a3aa-119">An indexer introduced in a class or struct hides all base class indexers that have the same signature.</span></span>

<span data-ttu-id="4a3aa-120">동일한 멤버에 대해 `new`와 [override](override.md)를 모두 사용하면 오류가 발생합니다. 두 한정자는 함께 사용할 수 없는 의미를 지니고 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="4a3aa-120">It is an error to use both `new` and [override](override.md) on the same member, because the two modifiers have mutually exclusive meanings.</span></span> <span data-ttu-id="4a3aa-121">`new` 한정자는 동일한 이름의 새 멤버를 만들고 원래 멤버를 숨기도록 하는 반면,</span><span class="sxs-lookup"><span data-stu-id="4a3aa-121">The `new` modifier creates a new member with the same name and causes the original member to become hidden.</span></span> <span data-ttu-id="4a3aa-122">`override` 한정자는 상속된 멤버에 대한 구현을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="4a3aa-122">The `override` modifier extends the implementation for an inherited member.</span></span>

<span data-ttu-id="4a3aa-123">상속된 멤버를 숨기지 않는 선언에 `new` 한정자를 사용하면 경고가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="4a3aa-123">Using the `new` modifier in a declaration that does not hide an inherited member generates a warning.</span></span>

## <a name="example"></a><span data-ttu-id="4a3aa-124">예제</span><span class="sxs-lookup"><span data-stu-id="4a3aa-124">Example</span></span>

<span data-ttu-id="4a3aa-125">이 예제에서 기본 클래스 `BaseC` 및 파생 클래스 `DerivedC`는 동일한 필드 이름 `x`를 사용하므로 상속된 필드의 값이 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="4a3aa-125">In this example, a base class, `BaseC`, and a derived class, `DerivedC`, use the same field name `x`, which hides the value of the inherited field.</span></span> <span data-ttu-id="4a3aa-126">이 예제에서는 `new` 한정자의 사용법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4a3aa-126">The example demonstrates the use of the `new` modifier.</span></span> <span data-ttu-id="4a3aa-127">또한 정규화된 이름을 사용하여 기본 클래스의 숨겨진 멤버에 액세스하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4a3aa-127">It also demonstrates how to access the hidden members of the base class by using their fully qualified names.</span></span>

[!code-csharp[csrefKeywordsOperator#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#9)]

## <a name="example"></a><span data-ttu-id="4a3aa-128">예제</span><span class="sxs-lookup"><span data-stu-id="4a3aa-128">Example</span></span>

<span data-ttu-id="4a3aa-129">이 예제에서 중첩 클래스는 기본 클래스에서 이름이 동일한 클래스를 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="4a3aa-129">In this example, a nested class hides a class that has the same name in the base class.</span></span> <span data-ttu-id="4a3aa-130">이 예제에서는 `new` 한정자를 사용하여 경고 메시지를 제거하는 방법과 정규화된 이름을 사용하여 숨겨진 클래스 멤버에 액세스하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4a3aa-130">The example demonstrates how to use the `new` modifier to eliminate the warning message and how to access the hidden class members by using their fully qualified names.</span></span>

[!code-csharp[csrefKeywordsOperator#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#10)]

<span data-ttu-id="4a3aa-131">`new` 한정자를 제거해도 프로그램은 컴파일되고 실행되지만 다음과 같은 경고가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="4a3aa-131">If you remove the `new` modifier, the program will still compile and run, but you will get the following warning:</span></span>

```text
The keyword new is required on 'MyDerivedC.x' because it hides inherited member 'MyBaseC.x'.
```

## <a name="c-language-specification"></a><span data-ttu-id="4a3aa-132">C# 언어 사양</span><span class="sxs-lookup"><span data-stu-id="4a3aa-132">C# language specification</span></span>

<span data-ttu-id="4a3aa-133">자세한 내용은 [C# 언어 사양](~/_csharplang/spec/introduction.md)의 [새 한정자](~/_csharplang/spec/classes.md#the-new-modifier) 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4a3aa-133">For more information, see [The new modifier](~/_csharplang/spec/classes.md#the-new-modifier) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4a3aa-134">참조</span><span class="sxs-lookup"><span data-stu-id="4a3aa-134">See also</span></span>

- [<span data-ttu-id="4a3aa-135">C# 참조</span><span class="sxs-lookup"><span data-stu-id="4a3aa-135">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4a3aa-136">C# 프로그래밍 가이드</span><span class="sxs-lookup"><span data-stu-id="4a3aa-136">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4a3aa-137">C# 키워드</span><span class="sxs-lookup"><span data-stu-id="4a3aa-137">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="4a3aa-138">한정자</span><span class="sxs-lookup"><span data-stu-id="4a3aa-138">Modifiers</span></span>](index.md)
- [<span data-ttu-id="4a3aa-139">Override 및 New 키워드를 사용하여 버전 관리</span><span class="sxs-lookup"><span data-stu-id="4a3aa-139">Versioning with the Override and New Keywords</span></span>](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)
- [<span data-ttu-id="4a3aa-140">Override 및 New 키워드를 사용해야 하는 경우</span><span class="sxs-lookup"><span data-stu-id="4a3aa-140">Knowing When to Use Override and New Keywords</span></span>](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)
