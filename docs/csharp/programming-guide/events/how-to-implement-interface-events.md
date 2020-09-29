---
title: 인터페이스 이벤트를 구현하는 방법 - C# 프로그래밍 가이드
description: 클래스에서 인터페이스 이벤트를 구현하는 방법을 알아봅니다. 코드 예제를 살펴보고 사용 가능한 추가 리소스를 확인합니다.
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], event implementation in classes
- events [C#], in interfaces
ms.assetid: 63527447-9535-4880-8e95-35e2075827df
ms.openlocfilehash: 153a2efa254bf2f2c81cec4b28a53207cdc4efe5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167550"
---
# <a name="how-to-implement-interface-events-c-programming-guide"></a><span data-ttu-id="2a31b-104">인터페이스 이벤트를 구현하는 방법(C# 프로그래밍 가이드)</span><span class="sxs-lookup"><span data-stu-id="2a31b-104">How to implement interface events (C# Programming Guide)</span></span>

<span data-ttu-id="2a31b-105">[인터페이스](../../language-reference/keywords/interface.md)는 [이벤트](../../language-reference/keywords/event.md)를 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a31b-105">An [interface](../../language-reference/keywords/interface.md) can declare an [event](../../language-reference/keywords/event.md).</span></span> <span data-ttu-id="2a31b-106">다음 예제에서는 클래스에서 인터페이스 이벤트를 구현하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2a31b-106">The following example shows how to implement interface events in a class.</span></span> <span data-ttu-id="2a31b-107">기본적인 규칙은 다른 모든 인터페이스 메서드나 속성을 구현할 때의 규칙과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2a31b-107">Basically the rules are the same as when you implement any interface method or property.</span></span>  
  
## <a name="to-implement-interface-events-in-a-class"></a><span data-ttu-id="2a31b-108">클래스에서 인터페이스 이벤트를 구현하려면</span><span class="sxs-lookup"><span data-stu-id="2a31b-108">To implement interface events in a class</span></span>  
  
<span data-ttu-id="2a31b-109">클래스에서 이벤트를 선언한 다음 적절한 영역에서 이벤트를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="2a31b-109">Declare the event in your class and then invoke it in the appropriate areas.</span></span>  
  
```csharp
namespace ImplementInterfaceEvents  
{  
    public interface IDrawingObject  
    {  
        event EventHandler ShapeChanged;  
    }  
    public class MyEventArgs : EventArgs
    {  
        // class members  
    }  
    public class Shape : IDrawingObject  
    {  
        public event EventHandler ShapeChanged;  
        void ChangeShape()  
        {  
            // Do something here before the event…  

            OnShapeChanged(new MyEventArgs(/*arguments*/));  

            // or do something here after the event.
        }  
        protected virtual void OnShapeChanged(MyEventArgs e)  
        {  
            ShapeChanged?.Invoke(this, e);  
        }  
    }  

}  
```  
  
## <a name="example"></a><span data-ttu-id="2a31b-110">예제</span><span class="sxs-lookup"><span data-stu-id="2a31b-110">Example</span></span>  

<span data-ttu-id="2a31b-111">다음 예제에서는 클래스가 둘 이상의 인터페이스에서 상속을 받으며 각 인터페이스에는 이름이 같은 이벤트가 있는 드문 상황을 처리하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2a31b-111">The following example shows how to handle the less-common situation in which your class inherits from two or more interfaces and each interface has an event with the same name.</span></span> <span data-ttu-id="2a31b-112">이러한 상황에서는 이벤트 하나 이상에 대해 명시적 인터페이스 구현을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a31b-112">In this situation, you must provide an explicit interface implementation for at least one of the events.</span></span> <span data-ttu-id="2a31b-113">이벤트에 대한 명시적 인터페이스 구현을 쓸 때는 `add` 및 `remove` 이벤트 접근자도 써야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a31b-113">When you write an explicit interface implementation for an event, you must also write the `add` and `remove` event accessors.</span></span> <span data-ttu-id="2a31b-114">일반적으로는 컴파일러가 이러한 접근자를 제공하지만 이 예제의 경우에는 컴파일러가 접근자를 제공할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2a31b-114">Normally these are provided by the compiler, but in this case the compiler cannot provide them.</span></span>  
  
<span data-ttu-id="2a31b-115">고유한 접근자를 제공하면 클래스에서 두 이벤트를 같은 이벤트로 표시할지 아니면 다른 이벤트로 표시할지를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a31b-115">By providing your own accessors, you can specify whether the two events are represented by the same event in your class, or by different events.</span></span> <span data-ttu-id="2a31b-116">예를 들어 인터페이스 사양에 따라 이벤트가 서로 다른 시간에 발생해야 하는 경우에는 각 이벤트를 클래스의 개별 구현과 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a31b-116">For example, if the events should be raised at different times according to the interface specifications, you can associate each event with a separate implementation in your class.</span></span> <span data-ttu-id="2a31b-117">다음 예제에서는 구독자가 `IShape` 또는 `IDrawingObject`에 셰이프 참조를 캐스팅하여 수신할 `OnDraw` 이벤트를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="2a31b-117">In the following example, subscribers determine which `OnDraw` event they will receive by casting the shape reference to either an `IShape` or an `IDrawingObject`.</span></span>  
  
 [!code-csharp[csProgGuideEvents#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#10)]
  
## <a name="see-also"></a><span data-ttu-id="2a31b-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2a31b-118">See also</span></span>

- [<span data-ttu-id="2a31b-119">C# 프로그래밍 가이드</span><span class="sxs-lookup"><span data-stu-id="2a31b-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2a31b-120">이벤트</span><span class="sxs-lookup"><span data-stu-id="2a31b-120">Events</span></span>](./index.md)
- [<span data-ttu-id="2a31b-121">대리자</span><span class="sxs-lookup"><span data-stu-id="2a31b-121">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="2a31b-122">명시적 인터페이스 구현</span><span class="sxs-lookup"><span data-stu-id="2a31b-122">Explicit Interface Implementation</span></span>](../interfaces/explicit-interface-implementation.md)
- [<span data-ttu-id="2a31b-123">파생 클래스에서 기본 클래스 이벤트를 발생하는 방법</span><span class="sxs-lookup"><span data-stu-id="2a31b-123">How to raise base class events in derived classes</span></span>](./how-to-raise-base-class-events-in-derived-classes.md)
