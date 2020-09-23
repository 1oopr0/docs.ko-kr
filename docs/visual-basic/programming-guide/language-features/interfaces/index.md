---
title: 인터페이스
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, interfaces
- interfaces [Visual Basic], Visual Basic
- interfaces
- interfaces [Visual Basic]
ms.assetid: 61b06674-12c9-430b-be68-cc67ecee1f5b
ms.openlocfilehash: ac5db62fec3548bfd4a99477958f4f29463267c0
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91057834"
---
# <a name="interfaces-visual-basic"></a><span data-ttu-id="4ba05-102">인터페이스(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4ba05-102">Interfaces (Visual Basic)</span></span>

<span data-ttu-id="4ba05-103">*인터페이스*는 클래스가 구현할 수 있는 속성, 메서드 및 이벤트를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-103">*Interfaces* define the properties, methods, and events that classes can implement.</span></span> <span data-ttu-id="4ba05-104">인터페이스를 사용하면 기능을 밀접한 관련이 있는 속성, 메서드, 이벤트 등의 작은 그룹으로 정의할 수 있습니다. 이렇게 하면 기존 코드를 그대로 사용하여 인터페이스에 대한 고급 구현을 개발할 수 있기 때문에 호환성 문제가 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-104">Interfaces allow you to define features as small groups of closely related properties, methods, and events; this reduces compatibility problems because you can develop enhanced implementations for your interfaces without jeopardizing existing code.</span></span> <span data-ttu-id="4ba05-105">추가적인 인터페이스와 구현을 개발하여 언제든지 새로운 기능을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-105">You can add new features at any time by developing additional interfaces and implementations.</span></span>  
  
 <span data-ttu-id="4ba05-106">클래스를 상속하는 대신 인터페이스를 사용해야 하는 몇 가지 다른 이유가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-106">There are several other reasons why you might want to use interfaces instead of class inheritance:</span></span>  
  
- <span data-ttu-id="4ba05-107">인터페이스는 특정 기능을 제공하기 위해 무관할 수 있는 다수의 개체 형식이 애플리케이션에서 요구되는 경우에 더 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-107">Interfaces are better suited to situations in which your applications require many possibly unrelated object types to provide certain functionality.</span></span>  
  
- <span data-ttu-id="4ba05-108">인터페이스는 다중 인터페이스를 구현하는 단일 구현을 정의할 수 있기 때문에 기본 클래스보다 더 유연합니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-108">Interfaces are more flexible than base classes because you can define a single implementation that can implement multiple interfaces.</span></span>  
  
- <span data-ttu-id="4ba05-109">인터페이스는 기본 클래스로부터 구현을 상속할 필요가 없는 경우에 더 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-109">Interfaces are better in situations in which you do not have to inherit implementation from a base class.</span></span>  
  
- <span data-ttu-id="4ba05-110">인터페이스는 클래스 상속을 사용할 수 없는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-110">Interfaces are useful when you cannot use class inheritance.</span></span> <span data-ttu-id="4ba05-111">예를 들어 구조체는 클래스에서 상속할 수 없지만 인터페이스를 구현할 수는 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-111">For example, structures cannot inherit from classes, but they can implement interfaces.</span></span>  
  
## <a name="declaring-interfaces"></a><span data-ttu-id="4ba05-112">인터페이스 선언</span><span class="sxs-lookup"><span data-stu-id="4ba05-112">Declaring Interfaces</span></span>  

 <span data-ttu-id="4ba05-113">인터페이스 정의는 `Interface` 및 `End Interface` 문 내에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-113">Interface definitions are enclosed within the `Interface` and `End Interface` statements.</span></span> <span data-ttu-id="4ba05-114">`Interface` 문 다음에, 하나 이상의 상속된 인터페이스를 나열하는 `Inherits` 문을 선택적으로 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-114">Following the `Interface` statement, you can add an optional `Inherits` statement that lists one or more inherited interfaces.</span></span> <span data-ttu-id="4ba05-115">`Inherits` 문은 선언에서 주석을 제외하고는 다른 모든 문 앞에 와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-115">The `Inherits` statements must precede all other statements in the declaration except comments.</span></span> <span data-ttu-id="4ba05-116">인터페이스 정의에 나오는 나머지 문은 `Event`, `Sub`, `Function`, `Property`, `Interface`, `Class`, `Structure` 및 `Enum` 문입니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-116">The remaining statements in the interface definition should be `Event`, `Sub`, `Function`, `Property`, `Interface`, `Class`, `Structure`, and `Enum` statements.</span></span> <span data-ttu-id="4ba05-117">인터페이스는 구현 코드 또는 구현 코드와 관련된 문(예: `End Sub` 또는 `End Property`)을 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-117">Interfaces cannot contain any implementation code or statements associated with implementation code, such as `End Sub` or `End Property`.</span></span>  
  
 <span data-ttu-id="4ba05-118">네임스페이스에서 인터페이스 문은 기본적으로 `Friend`이지만 `Public` 또는 `Friend`로 명시적으로 선언할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-118">In a namespace, interface statements are `Friend` by default, but they can also be explicitly declared as `Public` or `Friend`.</span></span> <span data-ttu-id="4ba05-119">클래스, 모듈, 인터페이스 및 구조체 내에서 정의되는 인터페이스는 기본적으로 `Public`이지만 `Public`, `Friend`, `Protected` 또는 `Private`으로 명시적으로 선언할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-119">Interfaces defined within classes, modules, interfaces, and structures are `Public` by default, but they can also be explicitly declared as `Public`, `Friend`, `Protected`, or `Private`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4ba05-120">`Shadows` 키워드는 모든 인터페이스 멤버에 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-120">The `Shadows` keyword can be applied to all interface members.</span></span> <span data-ttu-id="4ba05-121">`Overloads` 키워드는 인터페이스 정의에서 정의되는 `Sub`, `Function` 및 `Property` 문에 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-121">The `Overloads` keyword can be applied to `Sub`, `Function`, and `Property` statements declared in an interface definition.</span></span> <span data-ttu-id="4ba05-122">또한 `Property` 문은 `Default`, `ReadOnly` 또는 `WriteOnly` 한정자를 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-122">In addition, `Property` statements can have the `Default`, `ReadOnly`, or `WriteOnly` modifiers.</span></span> <span data-ttu-id="4ba05-123">`Public`, `Private`, `Friend`, `Protected`, `Shared`, `Overrides`, `MustOverride` 또는 `Overridable` 등의 다른 한정자는 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-123">None of the other modifiers—`Public`, `Private`, `Friend`, `Protected`, `Shared`, `Overrides`, `MustOverride`, or `Overridable`—are allowed.</span></span> <span data-ttu-id="4ba05-124">자세한 내용은 [선언 컨텍스트 및 기본 액세스 수준](../../../language-reference/statements/declaration-contexts-and-default-access-levels.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4ba05-124">For more information, see [Declaration Contexts and Default Access Levels](../../../language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="4ba05-125">예를 들어 다음 코드는 하나의 함수, 하나의 속성, 하나의 이벤트가 있는 인터페이스를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-125">For example, the following code defines an interface with one function, one property, and one event.</span></span>  
  
 [!code-vb[VbVbalrOOP#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#17)]  
  
## <a name="implementing-interfaces"></a><span data-ttu-id="4ba05-126">인터페이스 구현</span><span class="sxs-lookup"><span data-stu-id="4ba05-126">Implementing Interfaces</span></span>  

 <span data-ttu-id="4ba05-127">Visual Basic 예약어는 `Implements` 두 가지 방법으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-127">The Visual Basic reserved word `Implements` is used in two ways.</span></span> <span data-ttu-id="4ba05-128">`Implements` 문은 클래스 또는 구조체가 인터페이스를 구현한다는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-128">The `Implements` statement signifies that a class or structure implements an interface.</span></span> <span data-ttu-id="4ba05-129">`Implements` 키워드는 클래스 멤버 또는 구조체 멤버가 특정 인터페이스 멤버를 구현한다는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-129">The `Implements` keyword signifies that a class member or structure member implements a specific interface member.</span></span>  
  
### <a name="implements-statement"></a><span data-ttu-id="4ba05-130">Implements 문</span><span class="sxs-lookup"><span data-stu-id="4ba05-130">Implements Statement</span></span>  

 <span data-ttu-id="4ba05-131">하나 이상의 인터페이스를 구현하는 클래스 또는 구조체에는 `Class` 또는 `Structure` 문 바로 다음에 `Implements`문이 나와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-131">If a class or structure implements one or more interfaces, it must include the `Implements` statement immediately after the `Class` or `Structure` statement.</span></span> <span data-ttu-id="4ba05-132">`Implements` 문에는 클래스에 의해 구현될 인터페이스를 나열한, 쉼표로 구분된 목록이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-132">The `Implements` statement requires a comma-separated list of interfaces to be implemented by a class.</span></span> <span data-ttu-id="4ba05-133">클래스 또는 구조체는 `Implements` 키워드를 사용하여 모든 인터페이스 멤버를 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-133">The class or structure must implement all interface members using the `Implements` keyword.</span></span>  
  
### <a name="implements-keyword"></a><span data-ttu-id="4ba05-134">Implements 키워드</span><span class="sxs-lookup"><span data-stu-id="4ba05-134">Implements Keyword</span></span>  

 <span data-ttu-id="4ba05-135">`Implements` 키워드에는 구현될 인터페이스 멤버를 나열한, 쉼표로 구분된 목록이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-135">The `Implements` keyword requires a comma-separated list of interface members to be implemented.</span></span> <span data-ttu-id="4ba05-136">일반적으로 단일 인터페이스 멤버만 지정되지만 여러 멤버를 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-136">Generally, only a single interface member is specified, but you can specify multiple members.</span></span> <span data-ttu-id="4ba05-137">인터페이스 멤버의 사양은 인터페이스 이름(클래스 내의 implements 문에서 지정해야 함)과 기간 및 구현할 멤버 함수, 속성 또는 이벤트의 이름으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-137">The specification of an interface member consists of the interface name, which must be specified in an implements statement within the class; a period; and the name of the member function, property, or event to be implemented.</span></span> <span data-ttu-id="4ba05-138">인터페이스 멤버를 구현 하는 멤버의 이름에는 유효한 식별자를 사용할 수 있으며 `InterfaceName_MethodName` 이전 버전의 Visual Basic에 사용 되는 규칙으로 제한 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-138">The name of a member that implements an interface member can use any legal identifier, and it is not limited to the `InterfaceName_MethodName` convention used in earlier versions of Visual Basic.</span></span>  
  
 <span data-ttu-id="4ba05-139">예를 들어 다음 코드에서는 인터페이스의 메서드를 구현하는 `Sub1`이라는 서브루틴을 선언하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-139">For example, the following code shows how to declare a subroutine named `Sub1` that implements a method of an interface:</span></span>  
  
 [!code-vb[VbVbalrOOP#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#69)]  
  
 <span data-ttu-id="4ba05-140">구현 멤버의 매개 변수 형식 및 반환 형식은 인터페이스의 인터페이스 속성 또는 멤버 선언과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-140">The parameter types and return types of the implementing member must match the interface property or member declaration in the interface.</span></span> <span data-ttu-id="4ba05-141">인터페이스의 요소를 구현하는 가장 일반적인 방법은 이전 예제와 같이 인터페이스와 이름이 같은 멤버를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-141">The most common way to implement an element of an interface is with a member that has the same name as the interface, as shown in the previous example.</span></span>  
  
 <span data-ttu-id="4ba05-142">인터페이스 메서드의 구현을 선언하려면 인스턴스 메서드 선언에 `Overloads`, `Overrides`, `Overridable`, `Public`, `Private`, `Protected`, `Friend`, `Protected Friend`, `MustOverride`, `Default`, `Static` 등의 유효한 특성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-142">To declare the implementation of an interface method, you can use any attributes that are legal on instance method declarations, including `Overloads`, `Overrides`, `Overridable`, `Public`, `Private`, `Protected`, `Friend`, `Protected Friend`, `MustOverride`, `Default`, and `Static`.</span></span> <span data-ttu-id="4ba05-143">`Shared` 특성은 인스턴스 메서드가 아니라 클래스를 정의하므로 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-143">The `Shared` attribute is not legal since it defines a class rather than an instance method.</span></span>  
  
 <span data-ttu-id="4ba05-144">`Implements`를 사용하여 다음 예제와 같이 인터페이스에서 정의된 여러 메서드를 구현하는 단일 메서드를 작성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-144">Using `Implements`, you can also write a single method that implements multiple methods defined in an interface, as in the following example:</span></span>  
  
 [!code-vb[VbVbalrOOP#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#70)]  
  
 <span data-ttu-id="4ba05-145">전용 멤버를 사용하여 인터페이스 멤버를 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-145">You can use a private member to implement an interface member.</span></span> <span data-ttu-id="4ba05-146">전용 멤버가 인터페이스의 멤버를 구현하는 경우 이 멤버는 클래스에 대한 개체 변수에 대해 직접 사용할 수 없더라도 인터페이스를 통해 사용할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-146">When a private member implements a member of an interface, that member becomes available by way of the interface even though it is not available directly on object variables for the class.</span></span>  
  
### <a name="interface-implementation-examples"></a><span data-ttu-id="4ba05-147">인터페이스 구현 예제</span><span class="sxs-lookup"><span data-stu-id="4ba05-147">Interface Implementation Examples</span></span>  

 <span data-ttu-id="4ba05-148">인터페이스를 구현하는 클래스는 모든 속성, 메서드 및 이벤트를 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-148">Classes that implement an interface must implement all its properties, methods, and events.</span></span>  
  
 <span data-ttu-id="4ba05-149">다음 예제에서는 두 인터페이스를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-149">The following example defines two interfaces.</span></span> <span data-ttu-id="4ba05-150">두 번째 인터페이스인 `Interface2`는 `Interface1`을 상속하며 추가 속성 및 메서드를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-150">The second interface, `Interface2`, inherits `Interface1` and defines an additional property and method.</span></span>  
  
 [!code-vb[VbVbalrOOP#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#39)]  
  
 <span data-ttu-id="4ba05-151">다음 예제에서는 이전 예제에서 정의된 인터페이스인 `Interface1`을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-151">The next example implements `Interface1`, the interface defined in the previous example:</span></span>  
  
 [!code-vb[VbVbalrOOP#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#40)]  
  
 <span data-ttu-id="4ba05-152">마지막 예제에서는 `Interface1`에서 상속된 메서드를 포함하여 `Interface2`를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-152">The final example implements `Interface2`, including a method inherited from `Interface1`:</span></span>  
  
 [!code-vb[VbVbalrOOP#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#41)]  
  
 <span data-ttu-id="4ba05-153">읽기/쓰기 속성을 사용하여 읽기 전용 속성을 구현할 수 있습니다(즉, 구현 클래스에서 읽기 전용으로 선언할 필요가 없음).</span><span class="sxs-lookup"><span data-stu-id="4ba05-153">You can implement a readonly property with a readwrite property (that is, you do not have to declare it readonly in the implementing class).</span></span>  <span data-ttu-id="4ba05-154">인터페이스를 선언하면 최소한 이 인터페이스가 선언하는 멤버가 구현됩니다. 하지만 속성을 쓰기 가능하도록 허용하는 등, 더 많은 기능을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-154">Implementing an interface promises to implement at least the members that the interface declares, but you can offer more functionality, such as allowing your property to be writable.</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="4ba05-155">관련 항목</span><span class="sxs-lookup"><span data-stu-id="4ba05-155">Related Topics</span></span>  
  
|<span data-ttu-id="4ba05-156">제목</span><span class="sxs-lookup"><span data-stu-id="4ba05-156">Title</span></span>|<span data-ttu-id="4ba05-157">설명</span><span class="sxs-lookup"><span data-stu-id="4ba05-157">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="4ba05-158">연습: 인터페이스 만들기 및 구현</span><span class="sxs-lookup"><span data-stu-id="4ba05-158">Walkthrough: Creating and Implementing Interfaces</span></span>](walkthrough-creating-and-implementing-interfaces.md)|<span data-ttu-id="4ba05-159">고유한 인터페이스를 정의하고 구현하는 프로세스를 안내하는 자세한 절차를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-159">Provides a detailed procedure that takes you through the process of defining and implementing your own interface.</span></span>|  
|[<span data-ttu-id="4ba05-160">제네릭 인터페이스의 가변성</span><span class="sxs-lookup"><span data-stu-id="4ba05-160">Variance in Generic Interfaces</span></span>](../../concepts/covariance-contravariance/variance-in-generic-interfaces.md)|<span data-ttu-id="4ba05-161">제네릭 인터페이스의 공분산 및 반공분산에 대해 설명하고 .NET Framework의 Variant 제네릭 인터페이스의 목록을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4ba05-161">Discusses covariance and contravariance in generic interfaces and provides a list of variant generic interfaces in the .NET Framework.</span></span>|
