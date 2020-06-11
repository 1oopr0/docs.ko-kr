---
title: 파생 클래스에서 기본 클래스 이벤트를 발생하는 방법 - C# 프로그래밍 가이드
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
ms.openlocfilehash: e2d2dfc2809a4de1756bfc362880eebc79076b94
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84240630"
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a><span data-ttu-id="c4a8d-102">파생 클래스에서 기본 클래스 이벤트를 발생하는 방법(C# 프로그래밍 가이드)</span><span class="sxs-lookup"><span data-stu-id="c4a8d-102">How to raise base class events in derived classes (C# Programming Guide)</span></span>
<span data-ttu-id="c4a8d-103">다음 간단한 예제에서는 파생 클래스에서도 발생할 수 있도록 기본 클래스에서 이벤트를 선언하는 표준 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c4a8d-103">The following simple example shows the standard way to declare events in a base class so that they can also be raised from derived classes.</span></span> <span data-ttu-id="c4a8d-104">이 패턴은 .NET 클래스 라이브러리의 Windows Forms 클래스에서 광범위하게 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4a8d-104">This pattern is used extensively in Windows Forms classes in the .NET class libraries.</span></span>  
  
 <span data-ttu-id="c4a8d-105">다른 클래스의 기본 클래스로 사용할 수 있는 클래스를 만드는 경우 이벤트가 해당 이벤트를 선언한 클래스 내에서만 호출할 수 있는 특수 유형의 대리자라는 사실을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4a8d-105">When you create a class that can be used as a base class for other classes, you should consider the fact that events are a special type of delegate that can only be invoked from within the class that declared them.</span></span> <span data-ttu-id="c4a8d-106">파생 클래스는 기본 클래스 내에서 선언된 이벤트를 직접 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c4a8d-106">Derived classes cannot directly invoke events that are declared within the base class.</span></span> <span data-ttu-id="c4a8d-107">기본 클래스에서만 발생할 수 있는 이벤트를 원하는 경우도 있지만 대부분의 경우 파생 클래스가 기본 클래스 이벤트를 호출할 수 있도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4a8d-107">Although sometimes you may want an event that can only be raised by the base class, most of the time, you should enable the derived class to invoke base class events.</span></span> <span data-ttu-id="c4a8d-108">이렇게 하려면 이벤트를 래핑하는 기본 클래스에서 보호된 호출 메서드를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c4a8d-108">To do this, you can create a protected invoking method in the base class that wraps the event.</span></span> <span data-ttu-id="c4a8d-109">이 호출 메서드를 호출하거나 재정의하면 파생 클래스에서 간접적으로 이벤트를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4a8d-109">By calling or overriding this invoking method, derived classes can invoke the event indirectly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c4a8d-110">기본 클래스에서 가상 이벤트를 선언하지 말고 파생 클래스에서 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="c4a8d-110">Do not declare virtual events in a base class and override them in a derived class.</span></span> <span data-ttu-id="c4a8d-111">C# 컴파일러는 이러한 이벤트를 올바르게 처리하지 않으며, 파생 이벤트의 구독자가 실제로 기본 클래스 이벤트를 구독할지 여부를 예측할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c4a8d-111">The C# compiler does not handle these correctly and it is unpredictable whether a subscriber to the derived event will actually be subscribing to the base class event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4a8d-112">예제</span><span class="sxs-lookup"><span data-stu-id="c4a8d-112">Example</span></span>  
 [!code-csharp[csProgGuideEvents#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c4a8d-113">참조</span><span class="sxs-lookup"><span data-stu-id="c4a8d-113">See also</span></span>

- [<span data-ttu-id="c4a8d-114">C# 프로그래밍 가이드</span><span class="sxs-lookup"><span data-stu-id="c4a8d-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c4a8d-115">이벤트</span><span class="sxs-lookup"><span data-stu-id="c4a8d-115">Events</span></span>](./index.md)
- [<span data-ttu-id="c4a8d-116">대리자</span><span class="sxs-lookup"><span data-stu-id="c4a8d-116">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="c4a8d-117">액세스 한정자</span><span class="sxs-lookup"><span data-stu-id="c4a8d-117">Access Modifiers</span></span>](../classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="c4a8d-118">Windows Forms에서 이벤트 처리기 만들기</span><span class="sxs-lookup"><span data-stu-id="c4a8d-118">Creating Event Handlers in Windows Forms</span></span>](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
