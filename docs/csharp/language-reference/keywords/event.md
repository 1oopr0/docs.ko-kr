---
description: event - C# 참조
title: event - C# 참조
ms.date: 07/20/2015
f1_keywords:
- event
- remove
- event_CSharpKeyword
- add
helpviewer_keywords:
- event keyword [C#]
ms.assetid: 7858fd85-153b-4259-85d0-6aa13c35f174
ms.openlocfilehash: 5e75fec12390cb694126c5bec684c40caa378915
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139101"
---
# <a name="event-c-reference"></a><span data-ttu-id="f8ed1-103">event(C# 참조)</span><span class="sxs-lookup"><span data-stu-id="f8ed1-103">event (C# reference)</span></span>

<span data-ttu-id="f8ed1-104">`event` 키워드는 게시자 클래스에서 이벤트를 선언하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8ed1-104">The `event` keyword is used to declare an event in a publisher class.</span></span>

## <a name="example"></a><span data-ttu-id="f8ed1-105">예제</span><span class="sxs-lookup"><span data-stu-id="f8ed1-105">Example</span></span>

<span data-ttu-id="f8ed1-106">다음 예제에서는 <xref:System.EventHandler>를 기본 대리자 형식으로 사용하는 이벤트를 선언하고 발생시키는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f8ed1-106">The following example shows how to declare and raise an event that uses <xref:System.EventHandler> as the underlying delegate type.</span></span> <span data-ttu-id="f8ed1-107">제네릭 <xref:System.EventHandler%601> 대리자 형식을 사용하는 방법 및 이벤트를 구독하고 이벤트 처리기 메서드를 만드는 방법을 보여 주는 전체 코드 예제는 [.NET Framework 지침을 따르는 이벤트를 게시하는 방법](../../programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f8ed1-107">For the complete code example that also shows how to use the generic <xref:System.EventHandler%601> delegate type and how to subscribe to an event and create an event handler method, see [How to publish events that conform to .NET Framework Guidelines](../../programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md).</span></span>

[!code-csharp[csrefKeywordsModifiers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#7)]

<span data-ttu-id="f8ed1-108">이벤트는 해당 이벤트가 선언되는 클래스(게시자 클래스) 또는 구조체 내에서만 호출할 수 있는 특수한 멀티캐스트 대리자입니다.</span><span class="sxs-lookup"><span data-stu-id="f8ed1-108">Events are a special kind of multicast delegate that can only be invoked from within the class or struct where they are declared (the publisher class).</span></span> <span data-ttu-id="f8ed1-109">다른 클래스 또는 구조체에서 이벤트를 구독하는 경우 해당 이벤트 처리기 메서드는 게시자 클래스에서 이벤트를 발생시킬 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8ed1-109">If other classes or structs subscribe to the event, their event handler methods will be called when the publisher class raises the event.</span></span> <span data-ttu-id="f8ed1-110">자세한 내용 및 코드 예제는 [이벤트](../../programming-guide/events/index.md) 및 [대리자](../../programming-guide/delegates/index.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f8ed1-110">For more information and code examples, see [Events](../../programming-guide/events/index.md) and [Delegates](../../programming-guide/delegates/index.md).</span></span>

<span data-ttu-id="f8ed1-111">이벤트는 [public](./public.md), [private](./private.md), [protected](./protected.md), [internal](./internal.md), [protected internal](./protected-internal.md) 또는 [private protected](./private-protected.md)로 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8ed1-111">Events can be marked as [public](./public.md), [private](./private.md), [protected](./protected.md), [internal](./internal.md), [protected internal](./protected-internal.md), or [private protected](./private-protected.md).</span></span> <span data-ttu-id="f8ed1-112">이러한 액세스 한정자는 클래스 사용자가 이벤트에 액세스하는 방법을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f8ed1-112">These access modifiers define how users of the class can access the event.</span></span> <span data-ttu-id="f8ed1-113">자세한 내용은 [액세스 한정자](../../programming-guide/classes-and-structs/access-modifiers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f8ed1-113">For more information, see [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>

## <a name="keywords-and-events"></a><span data-ttu-id="f8ed1-114">키워드 및 이벤트</span><span class="sxs-lookup"><span data-stu-id="f8ed1-114">Keywords and events</span></span>

<span data-ttu-id="f8ed1-115">이벤트에 적용되는 키워드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f8ed1-115">The following keywords apply to events.</span></span>

|<span data-ttu-id="f8ed1-116">키워드</span><span class="sxs-lookup"><span data-stu-id="f8ed1-116">Keyword</span></span>|<span data-ttu-id="f8ed1-117">Description</span><span class="sxs-lookup"><span data-stu-id="f8ed1-117">Description</span></span>|<span data-ttu-id="f8ed1-118">참조 항목</span><span class="sxs-lookup"><span data-stu-id="f8ed1-118">For more information</span></span>|
|-------------|-----------------|--------------------------|
|[<span data-ttu-id="f8ed1-119">static</span><span class="sxs-lookup"><span data-stu-id="f8ed1-119">static</span></span>](./static.md)|<span data-ttu-id="f8ed1-120">클래스의 인스턴스가 없는 경우에도 언제든지 호출자가 이벤트를 사용할 수 있도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f8ed1-120">Makes the event available to callers at any time, even if no instance of the class exists.</span></span>|[<span data-ttu-id="f8ed1-121">정적 클래스 및 정적 클래스 멤버</span><span class="sxs-lookup"><span data-stu-id="f8ed1-121">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)|
|[<span data-ttu-id="f8ed1-122">virtual</span><span class="sxs-lookup"><span data-stu-id="f8ed1-122">virtual</span></span>](./virtual.md)|<span data-ttu-id="f8ed1-123">파생 클래스에서 [override](./override.md) 키워드를 사용하여 이벤트 동작을 재정의할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8ed1-123">Allows derived classes to override the event behavior by using the [override](./override.md) keyword.</span></span>|[<span data-ttu-id="f8ed1-124">상속</span><span class="sxs-lookup"><span data-stu-id="f8ed1-124">Inheritance</span></span>](../../programming-guide/classes-and-structs/inheritance.md)|
|[<span data-ttu-id="f8ed1-125">sealed</span><span class="sxs-lookup"><span data-stu-id="f8ed1-125">sealed</span></span>](./sealed.md)|<span data-ttu-id="f8ed1-126">파생 클래스에 대해 더 이상 가상이 아니도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f8ed1-126">Specifies that for derived classes it is no longer virtual.</span></span>||
|[<span data-ttu-id="f8ed1-127">abstract</span><span class="sxs-lookup"><span data-stu-id="f8ed1-127">abstract</span></span>](./abstract.md)|<span data-ttu-id="f8ed1-128">컴파일러에서 `add` 및 `remove` 이벤트 접근자 블록을 생성하지 않으므로 파생 클래스는 자체 구현을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8ed1-128">The compiler will not generate the `add` and `remove` event accessor blocks and therefore derived classes must provide their own implementation.</span></span>||

<span data-ttu-id="f8ed1-129">이벤트는 [static](./static.md) 키워드를 사용하여 정적 이벤트로 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8ed1-129">An event may be declared as a static event by using the [static](./static.md) keyword.</span></span> <span data-ttu-id="f8ed1-130">그러면 클래스의 인스턴스가 없는 경우에도 언제든지 호출자가 이벤트를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8ed1-130">This makes the event available to callers at any time, even if no instance of the class exists.</span></span> <span data-ttu-id="f8ed1-131">자세한 내용은 [static 클래스 및 static 클래스 멤버](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f8ed1-131">For more information, see [Static Classes and Static Class Members](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>

<span data-ttu-id="f8ed1-132">이벤트는 [virtual](./virtual.md) 키워드를 사용하여 가상 이벤트로 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8ed1-132">An event can be marked as a virtual event by using the [virtual](./virtual.md) keyword.</span></span> <span data-ttu-id="f8ed1-133">그러면 파생 클래스에서 [override](./override.md) 키워드를 사용하여 이벤트 동작을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8ed1-133">This enables derived classes to override the event behavior by using the [override](./override.md) keyword.</span></span> <span data-ttu-id="f8ed1-134">자세한 내용은 [상속](../../programming-guide/classes-and-structs/inheritance.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f8ed1-134">For more information, see [Inheritance](../../programming-guide/classes-and-structs/inheritance.md).</span></span> <span data-ttu-id="f8ed1-135">또한 가상 이벤트를 재정의하는 이벤트는 [sealed](./sealed.md)일 수 있으며, 파생 클래스에 대해 더 이상 가상이 아니도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f8ed1-135">An event overriding a virtual event can also be [sealed](./sealed.md), which specifies that for derived classes it is no longer virtual.</span></span> <span data-ttu-id="f8ed1-136">마지막으로 이벤트를 [abstract](./abstract.md)로 선언할 수 있으며, 컴파일러에서 `add` 및 `remove` 이벤트 접근자 블록을 생성하지 않는다는 의미입니다.</span><span class="sxs-lookup"><span data-stu-id="f8ed1-136">Lastly, an event can be declared [abstract](./abstract.md), which means that the compiler will not generate the `add` and `remove` event accessor blocks.</span></span> <span data-ttu-id="f8ed1-137">따라서 파생 클래스는 자체 구현을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8ed1-137">Therefore derived classes must provide their own implementation.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f8ed1-138">C# 언어 사양</span><span class="sxs-lookup"><span data-stu-id="f8ed1-138">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="f8ed1-139">참조</span><span class="sxs-lookup"><span data-stu-id="f8ed1-139">See also</span></span>

- [<span data-ttu-id="f8ed1-140">C# 참조</span><span class="sxs-lookup"><span data-stu-id="f8ed1-140">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f8ed1-141">C# 프로그래밍 가이드</span><span class="sxs-lookup"><span data-stu-id="f8ed1-141">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f8ed1-142">C# 키워드</span><span class="sxs-lookup"><span data-stu-id="f8ed1-142">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="f8ed1-143">add</span><span class="sxs-lookup"><span data-stu-id="f8ed1-143">add</span></span>](./add.md)
- [<span data-ttu-id="f8ed1-144">remove</span><span class="sxs-lookup"><span data-stu-id="f8ed1-144">remove</span></span>](./remove.md)
- [<span data-ttu-id="f8ed1-145">한정자</span><span class="sxs-lookup"><span data-stu-id="f8ed1-145">Modifiers</span></span>](index.md)
- [<span data-ttu-id="f8ed1-146">대리자를 결합하는 방법(멀티캐스트 대리자)</span><span class="sxs-lookup"><span data-stu-id="f8ed1-146">How to combine delegates (Multicast Delegates)</span></span>](../../programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)
