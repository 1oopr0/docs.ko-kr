---
title: 이벤트 구독 및 구독 취소 방법 - C# 프로그래밍 가이드
ms.date: 07/20/2015
helpviewer_keywords:
- event handlers [C#], creating
- Code Editor, event handlers
- events [C#], creating using the IDE
ms.assetid: 6319f39f-282c-4173-8a62-6c4657cf51cd
ms.openlocfilehash: d917ea097cf9253a65c1907efdca71a640df9497
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84240670"
---
# <a name="how-to-subscribe-to-and-unsubscribe-from-events-c-programming-guide"></a><span data-ttu-id="9b520-102">이벤트 구독 및 구독 취소 방법(C# 프로그래밍 가이드)</span><span class="sxs-lookup"><span data-stu-id="9b520-102">How to subscribe to and unsubscribe from events (C# Programming Guide)</span></span>
<span data-ttu-id="9b520-103">해당 이벤트가 발생할 때 호출되는 사용자 지정 코드를 작성하려는 경우 다른 클래스에 의해 게시되는 이벤트를 구독합니다.</span><span class="sxs-lookup"><span data-stu-id="9b520-103">You subscribe to an event that is published by another class when you want to write custom code that is called when that event is raised.</span></span> <span data-ttu-id="9b520-104">예를 들어 사용자가 단추를 클릭할 때 애플리케이션에서 유용한 작업을 수행하도록 하려면 단추의 `click` 이벤트를 구독할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b520-104">For example, you might subscribe to a button's `click` event in order to make your application do something useful when the user clicks the button.</span></span>  
  
### <a name="to-subscribe-to-events-by-using-the-visual-studio-ide"></a><span data-ttu-id="9b520-105">Visual Studio IDE를 사용하여 이벤트를 구독하려면</span><span class="sxs-lookup"><span data-stu-id="9b520-105">To subscribe to events by using the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="9b520-106">**속성** 창이 표시되지 않는 경우 **디자인** 보기에서 이벤트 처리기를 만들려는 양식 또는 컨트롤을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9b520-106">If you cannot see the **Properties** window, in **Design** view, right-click the form or control for which you want to create an event handler, and select **Properties**.</span></span>  
  
2. <span data-ttu-id="9b520-107">**속성** 창의 맨 위에서 **이벤트** 아이콘을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9b520-107">On top of the **Properties** window, click the **Events** icon.</span></span>  
  
3. <span data-ttu-id="9b520-108">만들려는 이벤트(예: `Load` 이벤트)를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9b520-108">Double-click the event that you want to create, for example the `Load` event.</span></span>  
  
     <span data-ttu-id="9b520-109">Visual C#에서 빈 이벤트 처리기 메서드를 만들고 코드에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9b520-109">Visual C# creates an empty event handler method and adds it to your code.</span></span> <span data-ttu-id="9b520-110">또는 **코드** 보기에서 수동으로 코드를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b520-110">Alternatively you can add the code manually in **Code** view.</span></span> <span data-ttu-id="9b520-111">예를 들어 다음 코드 줄은 `Form` 클래스에서 `Load` 이벤트가 발생할 때 호출되는 이벤트 처리기 메서드를 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="9b520-111">For example, the following lines of code declare an event handler method that will be called when the `Form` class raises the `Load` event.</span></span>  
  
     [!code-csharp[csProgGuideEvents#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#11)]  
  
     <span data-ttu-id="9b520-112">이벤트를 구독하는 데 필요한 코드 줄도 프로젝트의 Form1.Designer.cs 파일에 있는 `InitializeComponent` 메서드에 자동으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b520-112">The line of code that is required to subscribe to the event is also automatically generated in the `InitializeComponent` method in the Form1.Designer.cs file in your project.</span></span> <span data-ttu-id="9b520-113">해당 코드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9b520-113">It resembles this:</span></span>  
  
    ```csharp
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
### <a name="to-subscribe-to-events-programmatically"></a><span data-ttu-id="9b520-114">프로그래밍 방식으로 이벤트를 구독하려면</span><span class="sxs-lookup"><span data-stu-id="9b520-114">To subscribe to events programmatically</span></span>  
  
1. <span data-ttu-id="9b520-115">이벤트의 대리자 시그니처와 일치하는 시그니처를 가진 이벤트 처리기 메서드를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="9b520-115">Define an event handler method whose signature matches the delegate signature for the event.</span></span> <span data-ttu-id="9b520-116">예를 들어 이벤트가 <xref:System.EventHandler> 대리자 형식을 기반으로 하는 경우 다음 코드는 메서드 스텁을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9b520-116">For example, if the event is based on the <xref:System.EventHandler> delegate type, the following code represents the method stub:</span></span>  
  
    ```csharp
    void HandleCustomEvent(object sender, CustomEventArgs a)  
    {  
       // Do something useful here.  
    }  
    ```  
  
2. <span data-ttu-id="9b520-117">더하기 대입 연산자(`+=`)를 사용하여 이벤트에 이벤트 처리기를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="9b520-117">Use the addition assignment operator (`+=`) to attach an event handler to the event.</span></span> <span data-ttu-id="9b520-118">다음 예제에서는 `publisher` 개체에 `RaiseCustomEvent`라는 이벤트가 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="9b520-118">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent`.</span></span> <span data-ttu-id="9b520-119">구독자 클래스가 해당 이벤트를 구독하려면 게시자 클래스에 대한 참조가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="9b520-119">Note that the subscriber class needs a reference to the publisher class in order to subscribe to its events.</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="9b520-120">앞의 구문은 C# 2.0의 새로운 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="9b520-120">Note that the previous syntax is new in C# 2.0.</span></span> <span data-ttu-id="9b520-121">`new` 키워드를 사용하여 명시적으로 캡슐화 대리자를 만들어야 한다는 점에서 C# 1.0 구문과 정확히 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="9b520-121">It is exactly equivalent to the C# 1.0 syntax in which the encapsulating delegate must be explicitly created by using the `new` keyword:</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += new CustomEventHandler(HandleCustomEvent);  
    ```  
  
     <span data-ttu-id="9b520-122">[람다 식](../statements-expressions-operators/lambda-expressions.md)을 사용하여 이벤트 처리기를 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b520-122">You can also use a [lambda expression](../statements-expressions-operators/lambda-expressions.md) to specify an event handler:</span></span>
  
    ```csharp
    public Form1()  
    {  
        InitializeComponent();  
        this.Click += (s,e) =>
            {
                MessageBox.Show(((MouseEventArgs)e).Location.ToString());
            };
    }  
    ```  
  
### <a name="to-subscribe-to-events-by-using-an-anonymous-method"></a><span data-ttu-id="9b520-123">무명 메서드를 사용하여 이벤트를 구독하려면</span><span class="sxs-lookup"><span data-stu-id="9b520-123">To subscribe to events by using an anonymous method</span></span>  
  
- <span data-ttu-id="9b520-124">나중에 이벤트 구독을 취소할 필요가 없는 경우 더하기 대입 연산자(`+=`)를 사용하여 이벤트에 무명 메서드를 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b520-124">If you will not have to unsubscribe to an event later, you can use the addition assignment operator (`+=`) to attach an anonymous method to the event.</span></span> <span data-ttu-id="9b520-125">다음 예제에서는 `publisher` 개체에 `RaiseCustomEvent`라는 이벤트가 있고 일종의 특수 이벤트 정보를 전달하도록 `CustomEventArgs` 클래스도 정의되었다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="9b520-125">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent` and that a `CustomEventArgs` class has also been defined to carry some kind of specialized event information.</span></span> <span data-ttu-id="9b520-126">구독자 클래스가 해당 이벤트를 구독하려면 `publisher`에 대한 참조가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="9b520-126">Note that the subscriber class needs a reference to `publisher` in order to subscribe to its events.</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += delegate(object o, CustomEventArgs e)  
    {  
      string s = o.ToString() + " " + e.ToString();  
      Console.WriteLine(s);  
    };  
    ```  
  
     <span data-ttu-id="9b520-127">익명 함수를 사용하여 이벤트를 구독한 경우 쉽게 이벤트 구독을 취소할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9b520-127">It is important to notice that you cannot easily unsubscribe from an event if you used an anonymous function to subscribe to it.</span></span> <span data-ttu-id="9b520-128">이 시나리오에서 구독을 취소하려면 이벤트를 구독하고, 대리자 변수에 무명 메서드를 저장한 다음 이벤트에 대리자를 추가하는 코드로 돌아가야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b520-128">To unsubscribe in this scenario, it is necessary to go back to the code where you subscribe to the event, store the anonymous method in a delegate variable, and then add the delegate to the event.</span></span> <span data-ttu-id="9b520-129">일반적으로 코드의 뒷부분에서 이벤트 구독을 취소해야 하는 경우 익명 함수를 사용하여 이벤트를 구독하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9b520-129">In general, we recommend that you do not use anonymous functions to subscribe to events if you will have to unsubscribe from the event at some later point in your code.</span></span> <span data-ttu-id="9b520-130">익명 함수에 대한 자세한 내용은 [익명 함수](../statements-expressions-operators/anonymous-functions.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9b520-130">For more information about anonymous functions, see [Anonymous Functions](../statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="unsubscribing"></a><span data-ttu-id="9b520-131">구독 해제</span><span class="sxs-lookup"><span data-stu-id="9b520-131">Unsubscribing</span></span>  
 <span data-ttu-id="9b520-132">이벤트가 발생할 때 이벤트 처리기가 호출되지 않도록 하려면 이벤트 구독을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="9b520-132">To prevent your event handler from being invoked when the event is raised, unsubscribe from the event.</span></span> <span data-ttu-id="9b520-133">리소스 누수를 방지하려면 구독자 개체를 삭제하기 전에 이벤트 구독을 취소해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b520-133">In order to prevent resource leaks, you should unsubscribe from events before you dispose of a subscriber object.</span></span> <span data-ttu-id="9b520-134">이벤트 구독을 취소할 때까지 게시 개체에서 이벤트의 기반이 되는 멀티캐스트 대리자에 구독자의 이벤트 처리기를 캡슐화하는 대리자에 대한 참조가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b520-134">Until you unsubscribe from an event, the multicast delegate that underlies the event in the publishing object has a reference to the delegate that encapsulates the subscriber's event handler.</span></span> <span data-ttu-id="9b520-135">게시 개체에 해당 참조가 있기만 하면 가비지 수집 시 구독자 개체가 삭제되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9b520-135">As long as the publishing object holds that reference, garbage collection will not delete your subscriber object.</span></span>  
  
#### <a name="to-unsubscribe-from-an-event"></a><span data-ttu-id="9b520-136">이벤트 구독을 취소하려면</span><span class="sxs-lookup"><span data-stu-id="9b520-136">To unsubscribe from an event</span></span>  
  
- <span data-ttu-id="9b520-137">빼기 대입 연산자(`-=`)를 사용하여 이벤트 구독을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="9b520-137">Use the subtraction assignment operator (`-=`) to unsubscribe from an event:</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent -= HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="9b520-138">모든 구독자가 이벤트 구독을 취소하면 게시자 클래스의 이벤트 인스턴스가 `null`로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b520-138">When all subscribers have unsubscribed from an event, the event instance in the publisher class is set to `null`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b520-139">참조</span><span class="sxs-lookup"><span data-stu-id="9b520-139">See also</span></span>

- [<span data-ttu-id="9b520-140">이벤트</span><span class="sxs-lookup"><span data-stu-id="9b520-140">Events</span></span>](./index.md)
- [<span data-ttu-id="9b520-141">event</span><span class="sxs-lookup"><span data-stu-id="9b520-141">event</span></span>](../../language-reference/keywords/event.md)
- [<span data-ttu-id="9b520-142">.NET 지침을 따르는 이벤트를 게시하는 방법</span><span class="sxs-lookup"><span data-stu-id="9b520-142">How to publish events that conform to .NET Guidelines</span></span>](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)
- [<span data-ttu-id="9b520-143">- 및 -= 연산자</span><span class="sxs-lookup"><span data-stu-id="9b520-143">- and -= operators</span></span>](../../language-reference/operators/subtraction-operator.md)
- [<span data-ttu-id="9b520-144">+ 및 += 연산자</span><span class="sxs-lookup"><span data-stu-id="9b520-144">+ and += operators</span></span>](../../language-reference/operators/addition-operator.md)
