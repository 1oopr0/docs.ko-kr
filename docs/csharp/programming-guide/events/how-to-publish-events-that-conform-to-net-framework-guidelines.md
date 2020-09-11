---
title: .NET 지침을 따르는 이벤트 게시(C# 프로그래밍 가이드)
description: .NET 지침을 따르는 이벤트를 게시하는 방법을 알아봅니다. .NET 클래스 라이브러리의 모든 이벤트는 EventHandler 대리자를 기반으로 합니다.
ms.date: 05/26/2020
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
ms.openlocfilehash: 8cc8b0a9fdaeeb6ab6290630c5d78044c2696b9a
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89466172"
---
# <a name="how-to-publish-events-that-conform-to-net-guidelines-c-programming-guide"></a><span data-ttu-id="59c02-104">.NET 지침을 따르는 이벤트를 게시하는 방법(C# 프로그래밍 가이드)</span><span class="sxs-lookup"><span data-stu-id="59c02-104">How to publish events that conform to .NET Guidelines (C# Programming Guide)</span></span>

<span data-ttu-id="59c02-105">다음 절차에서는 표준 .NET 패턴을 따르는 이벤트를 클래스와 구조체에 추가하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="59c02-105">The following procedure demonstrates how to add events that follow the standard .NET pattern to your classes and structs.</span></span> <span data-ttu-id="59c02-106">.NET 클래스 라이브러리의 모든 이벤트는 다음과 같이 정의된 <xref:System.EventHandler> 대리자를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="59c02-106">All events in the .NET class library are based on the <xref:System.EventHandler> delegate, which is defined as follows:</span></span>

```csharp
public delegate void EventHandler(object sender, EventArgs e);
```

> [!NOTE]
> <span data-ttu-id="59c02-107">.NET Framework 2.0에서는 이 대리자의 제네릭 버전인 <xref:System.EventHandler%601>가 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="59c02-107">.NET Framework 2.0 introduces a generic version of this delegate, <xref:System.EventHandler%601>.</span></span> <span data-ttu-id="59c02-108">다음 예제에서는 두 버전을 사용하는 방법을 모두 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="59c02-108">The following examples show how to use both versions.</span></span>

<span data-ttu-id="59c02-109">정의하는 클래스의 이벤트는 값을 반환하는 대리자를 포함하여 유효한 모든 대리자 형식을 기반으로 할 수 있지만, 다음 예제와 같이 <xref:System.EventHandler>를 사용하여 .NET 패턴에 따라 이벤트를 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="59c02-109">Although events in classes that you define can be based on any valid delegate type, even delegates that return a value, it is generally recommended that you base your events on the .NET pattern by using <xref:System.EventHandler>, as shown in the following example.</span></span>

<span data-ttu-id="59c02-110">이름 `EventHandler`는 이벤트를 실제로 처리하지는 않으므로 약간의 혼동을 일으킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59c02-110">The name `EventHandler` can lead to a bit of confusion as it doesn't actually handle the event.</span></span> <span data-ttu-id="59c02-111"><xref:System.EventHandler> 및 제네릭 <xref:System.EventHandler%601>는 대리자 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="59c02-111">The <xref:System.EventHandler>, and generic <xref:System.EventHandler%601> are delegate types.</span></span> <span data-ttu-id="59c02-112">시그니처가 대리자 정의와 일치하는 메서드 또는 람다 식은 이벤트 처리기이며, 이벤트가 발생할 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="59c02-112">A method or lambda expression whose signature matches the delegate definition is the *event handler* and will be invoked when the event is raised.</span></span>

## <a name="publish-events-based-on-the-eventhandler-pattern"></a><span data-ttu-id="59c02-113">EventHandler 패턴에 따라 이벤트 게시</span><span class="sxs-lookup"><span data-stu-id="59c02-113">Publish events based on the EventHandler pattern</span></span>

1. <span data-ttu-id="59c02-114">이벤트와 함께 사용자 지정 데이터를 보낼 필요가 없는 경우 이 단계를 건너뛰고 3a 단계로 이동합니다. 게시자 및 구독자 클래스 둘 다에 표시되는 범위에서 사용자 지정 데이터에 대한 클래스를 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="59c02-114">(Skip this step and go to Step 3a if you do not have to send custom data with your event.) Declare the class for your custom data at a scope that is visible to both your publisher and subscriber classes.</span></span> <span data-ttu-id="59c02-115">그런 다음 사용자 지정 이벤트 데이터를 저장하는 데 필요한 멤버를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="59c02-115">Then add the required members to hold your custom event data.</span></span> <span data-ttu-id="59c02-116">이 예제에서는 간단한 문자열이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="59c02-116">In this example, a simple string is returned.</span></span>

    ```csharp
    public class CustomEventArgs : EventArgs
    {
        public CustomEventArgs(string message)
        {
            Message = message;
        }

        public string Message { get; set; }
    }
    ```

2. <span data-ttu-id="59c02-117"><xref:System.EventHandler%601>의 제네릭 버전을 사용하는 경우 이 단계를 건너뜁니다. 게시 클래스에서 대리자를 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="59c02-117">(Skip this step if you are using the generic version of <xref:System.EventHandler%601>.) Declare a delegate in your publishing class.</span></span> <span data-ttu-id="59c02-118">`EventHandler`로 끝나는 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="59c02-118">Give it a name that ends with `EventHandler`.</span></span> <span data-ttu-id="59c02-119">두 번째 매개 변수는 사용자 지정 `EventArgs` 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="59c02-119">The second parameter specifies your custom `EventArgs` type.</span></span>

    ```csharp
    public delegate void CustomEventHandler(object sender, CustomEventArgs args);
    ```

3. <span data-ttu-id="59c02-120">다음 단계 중 하나를 사용하여 게시 클래스에서 이벤트를 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="59c02-120">Declare the event in your publishing class by using one of the following steps.</span></span>

    1. <span data-ttu-id="59c02-121">사용자 지정 EventArgs 클래스가 없는 경우 이벤트 유형은 제네릭이 아닌 EventHandler 대리자가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="59c02-121">If you have no custom EventArgs class, your Event type will be the non-generic EventHandler delegate.</span></span> <span data-ttu-id="59c02-122">C# 프로젝트를 만들 때 포함된 <xref:System> 네임스페이스에서 이미 선언되었기 때문에 대리자를 선언할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="59c02-122">You do not have to declare the delegate because it is already declared in the <xref:System> namespace that is included when you create your C# project.</span></span> <span data-ttu-id="59c02-123">게시자 클래스에 다음 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="59c02-123">Add the following code to your publisher class.</span></span>

        ```csharp
        public event EventHandler RaiseCustomEvent;
        ```

    2. <span data-ttu-id="59c02-124">제네릭이 아닌 버전의 <xref:System.EventHandler>를 사용 중이고 <xref:System.EventArgs>에서 파생된 사용자 지정 클래스가 있는 경우 게시 클래스 내에서 이벤트를 선언하고 2단계의 대리자를 형식으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="59c02-124">If you are using the non-generic version of <xref:System.EventHandler> and you have a custom class derived from <xref:System.EventArgs>, declare your event inside your publishing class and use your delegate from step 2 as the type.</span></span>

        ```csharp
        public event CustomEventHandler RaiseCustomEvent;
        ```

    3. <span data-ttu-id="59c02-125">제네릭 버전을 사용하는 경우에는 사용자 지정 대리자가 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="59c02-125">If you are using the generic version, you do not need a custom delegate.</span></span> <span data-ttu-id="59c02-126">대신, 게시 클래스에서 이벤트 유형을 `EventHandler<CustomEventArgs>`로 지정하고 고유한 클래스 이름을 꺾쇠 괄호로 묶어 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="59c02-126">Instead, in your publishing class, you specify your event type as `EventHandler<CustomEventArgs>`, substituting the name of your own class between the angle brackets.</span></span>

        ```csharp
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;
        ```

## <a name="example"></a><span data-ttu-id="59c02-127">예제</span><span class="sxs-lookup"><span data-stu-id="59c02-127">Example</span></span>

<span data-ttu-id="59c02-128">다음 예제에서는 사용자 지정 EventArgs 클래스와 <xref:System.EventHandler%601>를 이벤트 유형으로 사용하여 이전 단계를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="59c02-128">The following example demonstrates the previous steps by using a custom EventArgs class and <xref:System.EventHandler%601> as the event type.</span></span>

[!code-csharp[csProgGuideEvents#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#2)]

## <a name="see-also"></a><span data-ttu-id="59c02-129">참조</span><span class="sxs-lookup"><span data-stu-id="59c02-129">See also</span></span>

- <xref:System.Delegate>
- [<span data-ttu-id="59c02-130">C# 프로그래밍 가이드</span><span class="sxs-lookup"><span data-stu-id="59c02-130">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="59c02-131">이벤트</span><span class="sxs-lookup"><span data-stu-id="59c02-131">Events</span></span>](index.md)
- [<span data-ttu-id="59c02-132">대리자</span><span class="sxs-lookup"><span data-stu-id="59c02-132">Delegates</span></span>](../delegates/index.md)
