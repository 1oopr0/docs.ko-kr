---
title: System.Delegate 및 `delegate` 키워드
description: .NET에서 대리자를 지원하는 클래스와 해당 클래스가 ‘delegate’ 키워드에 매핑되는 방법을 설명합니다.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: f3742fda-13c2-4283-8966-9e21c2674393
ms.openlocfilehash: 9df8ad68f6bfa62863ee047875b6419fc81ad779
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062467"
---
# <a name="systemdelegate-and-the-delegate-keyword"></a><span data-ttu-id="63c0c-103">System.Delegate 및 `delegate` 키워드</span><span class="sxs-lookup"><span data-stu-id="63c0c-103">System.Delegate and the `delegate` keyword</span></span>

[<span data-ttu-id="63c0c-104">이전</span><span class="sxs-lookup"><span data-stu-id="63c0c-104">Previous</span></span>](delegates-overview.md)

<span data-ttu-id="63c0c-105">이 문서에서는 .NET에서 대리자를 지원하는 클래스와 해당 클래스가 `delegate` 키워드에 매핑되는 방법을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-105">This article covers the classes in .NET that support delegates, and how those map to the `delegate` keyword.</span></span>

## <a name="define-delegate-types"></a><span data-ttu-id="63c0c-106">대리자 유형 정의</span><span class="sxs-lookup"><span data-stu-id="63c0c-106">Define delegate types</span></span>

<span data-ttu-id="63c0c-107">먼저 'delegate' 키워드를 살펴보겠습니다. 대리자 작업을 수행할 때 기본적으로 이 키워드를 사용하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-107">Let's start with the 'delegate' keyword, because that's primarily what you will use as you work with delegates.</span></span> <span data-ttu-id="63c0c-108">`delegate` 키워드를 사용할 때 컴파일러가 생성하는 코드는 <xref:System.Delegate> 및 <xref:System.MulticastDelegate> 클래스의 멤버를 호출하는 메서드 호출에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-108">The code that the compiler generates when you use the `delegate` keyword will map to method calls that invoke members of the <xref:System.Delegate> and <xref:System.MulticastDelegate> classes.</span></span>

<span data-ttu-id="63c0c-109">메서드 시그니처를 정의하는 것과 비슷한 구문을 사용하여 대리자 형식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-109">You define a delegate type using syntax that is similar to defining a method signature.</span></span> <span data-ttu-id="63c0c-110">`delegate` 키워드를 정의에 추가하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-110">You just add the `delegate` keyword to the definition.</span></span>

<span data-ttu-id="63c0c-111">계속해서 List.Sort() 메서드를 예제로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-111">Let's continue to use the List.Sort() method as our example.</span></span> <span data-ttu-id="63c0c-112">첫 번째 단계는 비교 대리자에 대한 형식을 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-112">The first step is to create a type for the comparison delegate:</span></span>

```csharp
// From the .NET Core library

// Define the delegate type:
public delegate int Comparison<in T>(T left, T right);
```

<span data-ttu-id="63c0c-113">컴파일러에서는 사용된 시그니처와 일치하는 `System.Delegate`에서 파생된 클래스를 생성합니다(이 경우 정수를 반환하고 두 개의 인수가 포함된 메서드).</span><span class="sxs-lookup"><span data-stu-id="63c0c-113">The compiler generates a class, derived from `System.Delegate` that matches the signature used (in this case, a method that returns an integer, and has two arguments).</span></span> <span data-ttu-id="63c0c-114">해당 대리자의 형식은 `Comparison`입니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-114">The type of that delegate is `Comparison`.</span></span> <span data-ttu-id="63c0c-115">`Comparison` 대리자 형식은 제네릭 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-115">The `Comparison` delegate type is a generic type.</span></span> <span data-ttu-id="63c0c-116">제네릭에 대한 자세한 내용은 [여기](programming-guide/generics/index.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="63c0c-116">For details on generics see [here](programming-guide/generics/index.md).</span></span>

<span data-ttu-id="63c0c-117">구문이 변수를 선언하는 것처럼 보일 수 있지만 실제로는 *형식*을 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-117">Notice that the syntax may appear as though it is declaring a variable, but it is actually declaring a *type*.</span></span> <span data-ttu-id="63c0c-118">클래스 내부, 직접 네임스페이스 내부 또는 전역 네임스페이스에 대리자 형식을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-118">You can define delegate types inside classes, directly inside namespaces, or even in the global namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="63c0c-119">전역 네임스페이스에 직접 대리자 형식(또는 기타 형식)을 선언하는 것은 권장하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-119">Declaring delegate types (or other types) directly in the global namespace is not recommended.</span></span>

<span data-ttu-id="63c0c-120">이 클래스의 클라이언트가 인스턴스의 호출 목록에서 메서드를 추가 및 제거할 수 있도록 컴파일러에서는 이 새로운 형식에 대한 추가 및 제거 처리기를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-120">The compiler also generates add and remove handlers for this new type so that clients of this class can add and remove methods from an instance's invocation list.</span></span> <span data-ttu-id="63c0c-121">컴파일러는 추가되거나 제거되는 메서드의 시그니처가 메서드를 선언할 대 사용된 시그니처와 일치하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-121">The compiler will enforce that the signature of the method being added or removed matches the signature used when declaring the method.</span></span>

## <a name="declare-instances-of-delegates"></a><span data-ttu-id="63c0c-122">대리자 인스턴스 선언</span><span class="sxs-lookup"><span data-stu-id="63c0c-122">Declare instances of delegates</span></span>

<span data-ttu-id="63c0c-123">대리자를 정의한 후 해당 형식의 인스턴스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-123">After defining the delegate, you can create an instance of that type.</span></span>
<span data-ttu-id="63c0c-124">C#의 모든 변수처럼 네임스페이스에서 직접 또는 전역 네임스페이스에서 대리자 인스턴스를 선언할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-124">Like all variables in C#, you cannot declare delegate instances directly in a namespace, or in the global namespace.</span></span>

```csharp
// inside a class definition:

// Declare an instance of that type:
public Comparison<T> comparator;
```

<span data-ttu-id="63c0c-125">변수 형식은 앞에서 정의한 대리자 형식인 `Comparison<T>`입니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-125">The type of the variable is `Comparison<T>`, the delegate type defined earlier.</span></span> <span data-ttu-id="63c0c-126">변수 이름은 `comparator`입니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-126">The name of the variable is `comparator`.</span></span>

 <span data-ttu-id="63c0c-127">위의 코드 조각에서는 클래스 내부에 멤버 변수를 선언했습니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-127">That code snippet above declared a member variable inside a class.</span></span> <span data-ttu-id="63c0c-128">메서드에 대한 인수 또는 지역 변수인 대리자 변수를 선언할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-128">You can also declare delegate variables that are local variables, or arguments to methods.</span></span>

## <a name="invoke-delegates"></a><span data-ttu-id="63c0c-129">대리자 호출</span><span class="sxs-lookup"><span data-stu-id="63c0c-129">Invoke delegates</span></span>

<span data-ttu-id="63c0c-130">대리자를 호출하여 대리자 호출 목록에 있는 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-130">You invoke the methods that are in the invocation list of a delegate by calling that delegate.</span></span> <span data-ttu-id="63c0c-131">`Sort()` 메서드 내부에서 코드는 비교 메서드를 호출하여 개체를 배치할 순서를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-131">Inside the `Sort()` method, the code will call the comparison method to determine which order to place objects:</span></span>

```csharp
int result = comparator(left, right);
```

<span data-ttu-id="63c0c-132">위 줄에서 코드는 대리자에 연결된 메서드를 *호출*합니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-132">In the line above, the code *invokes* the method attached to the delegate.</span></span>
<span data-ttu-id="63c0c-133">변수를 메서드 이름으로 처리하고 일반 메서드 호출 구문을 사용하여 변수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-133">You treat the variable as a method name, and invoke it using normal method call syntax.</span></span>

<span data-ttu-id="63c0c-134">해당 코드 줄은 안전하지 않은 가정을 생성합니다. 대상이 대리자에 추가되었다는 보장이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-134">That line of code makes an unsafe assumption: There's no guarantee that a target has been added to the delegate.</span></span> <span data-ttu-id="63c0c-135">대상이 연결되지 않은 경우 위 줄은 `NullReferenceException`을 throw합니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-135">If no targets have been attached, the line above would cause a `NullReferenceException` to be thrown.</span></span> <span data-ttu-id="63c0c-136">이 문제를 해결하는 데 사용된 관용구는 간단한 null 검사보다 더 복잡하고 이 [시리즈](delegates-patterns.md)의 뒷부분에서 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-136">The idioms used to address this problem are more complicated than a simple null-check, and are covered later in this [series](delegates-patterns.md).</span></span>

## <a name="assign-add-and-remove-invocation-targets"></a><span data-ttu-id="63c0c-137">호출 대상 할당, 추가 및 제거</span><span class="sxs-lookup"><span data-stu-id="63c0c-137">Assign, add, and remove invocation targets</span></span>

<span data-ttu-id="63c0c-138">이 방법으로 대리자 형식을 정의하고 대리자 인스턴스를 선언 및 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-138">That's how a delegate type is defined, and how delegate instances are declared and invoked.</span></span>

<span data-ttu-id="63c0c-139">`List.Sort()` 메서드를 사용하려는 개발자는 시그니처가 대리자 형식 정의와 일치하는 메서드를 정의하고 정렬 메서드에서 사용된 대리자에 할당해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-139">Developers that want to use the `List.Sort()` method need to define a method whose signature matches the delegate type definition, and assign it to the delegate used by the sort method.</span></span> <span data-ttu-id="63c0c-140">이 할당으로 해당 대리자 개체의 호출 목록에 메서드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-140">This assignment adds the method to the invocation list of that delegate object.</span></span>

<span data-ttu-id="63c0c-141">길이별로 문자열 목록을 정렬한다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-141">Suppose you wanted to sort a list of strings by their length.</span></span> <span data-ttu-id="63c0c-142">비교 함수는 다음과 같을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-142">Your comparison function might be the following:</span></span>

```csharp
private static int CompareLength(string left, string right) =>
    left.Length.CompareTo(right.Length);
```

<span data-ttu-id="63c0c-143">메서드는 private 메서드로 선언됩니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-143">The method is declared as a private method.</span></span> <span data-ttu-id="63c0c-144">괜찮습니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-144">That's fine.</span></span> <span data-ttu-id="63c0c-145">이 메서드를 public 인터페이스에 포함하지 않으려고 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-145">You may not want this method to be part of your public interface.</span></span> <span data-ttu-id="63c0c-146">대리자에 연결될 경우 비교 메서드로 계속 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-146">It can still be used as the comparison method when attached to a delegate.</span></span> <span data-ttu-id="63c0c-147">호출 코드에서는 이 메서드를 대리자 개체의 대상 목록에 연결하고 해당 대리자를 통해 메서드에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-147">The calling code will have this method attached to the target list of the delegate object, and can access it through that delegate.</span></span>

<span data-ttu-id="63c0c-148">해당 메서드를 `List.Sort()` 메서드에 전달하여 관계를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-148">You create that relationship by passing that method to the `List.Sort()` method:</span></span>

```csharp
phrases.Sort(CompareLength);
```

<span data-ttu-id="63c0c-149">메서드 이름은 괄호 없이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-149">Notice that the method name is used, without parentheses.</span></span> <span data-ttu-id="63c0c-150">메서드를 인수로 사용하면 메서드 참조를 대리자 호출 대상으로 사용될 수 있는 참조로 변환하고 해당 메서드를 호출 대상으로 연결하도록 컴파일러에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-150">Using the method as an argument tells the compiler to convert the method reference into a reference that can be used as a delegate invocation target, and attach that method as an invocation target.</span></span>

<span data-ttu-id="63c0c-151">`Comparison<string>` 형식의 변수를 선언하고 할당을 수행하여 명시적 상태일 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-151">You could also have been explicit by declaring a variable of type `Comparison<string>` and doing an assignment:</span></span>

```csharp
Comparison<string> comparer = CompareLength;
phrases.Sort(comparer);
```

<span data-ttu-id="63c0c-152">대리자 대상으로 사용되는 메서드가 작은 메서드인 경우에는 일반적으로 [람다 식](language-reference/operators/lambda-expressions.md) 구문을 사용하여 할당을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-152">In uses where the method being used as a delegate target is a small method, it's common to use [lambda expression](language-reference/operators/lambda-expressions.md) syntax to perform the assignment:</span></span>

```csharp
Comparison<string> comparer = (left, right) => left.Length.CompareTo(right.Length);
phrases.Sort(comparer);
```

<span data-ttu-id="63c0c-153">대리자 대상에 람다 식을 사용하는 방법은 [이후 섹션](delegates-patterns.md)에서 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-153">Using lambda expressions for delegate targets is covered more in a [later section](delegates-patterns.md).</span></span>

<span data-ttu-id="63c0c-154">Sort() 예제에서는 일반적으로 단일 대상 메서드를 대리자에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-154">The Sort() example typically attaches a single target method to the delegate.</span></span> <span data-ttu-id="63c0c-155">그러나 대리자 개체는 여러 대상 메서드가 대리자 개체에 연결되어 있는 호출 목록을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-155">However, delegate objects do support invocation lists that have multiple target methods attached to a delegate object.</span></span>

## <a name="delegate-and-multicastdelegate-classes"></a><span data-ttu-id="63c0c-156">Delegate 및 MulticastDelegate 클래스</span><span class="sxs-lookup"><span data-stu-id="63c0c-156">Delegate and MulticastDelegate classes</span></span>

<span data-ttu-id="63c0c-157">위에 설명된 언어 지원은 일반적으로 대리자를 사용할 때 필요한 기능과 지원을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-157">The language support described above provides the features and support you'll typically need to work with delegates.</span></span> <span data-ttu-id="63c0c-158">이러한 기능은 .NET Core Framework의 두 가지 클래스 <xref:System.Delegate> 및 <xref:System.MulticastDelegate>를 기반으로 빌드됩니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-158">These features are built on two classes in the .NET Core framework: <xref:System.Delegate> and <xref:System.MulticastDelegate>.</span></span>

<span data-ttu-id="63c0c-159">`System.Delegate` 클래스와 단일 직접 하위 클래스 `System.MulticastDelegate`는 대리자를 만들고, 메서드를 대리자 대상으로 등록하고, 대리자 대상으로 등록된 모든 메서드를 호출하기 위한 프레임워크 지원을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-159">The `System.Delegate` class and its single direct subclass, `System.MulticastDelegate`, provide the framework support for creating delegates, registering methods as delegate targets, and invoking all methods that are registered as a delegate target.</span></span>

<span data-ttu-id="63c0c-160">흥미롭게도 `System.Delegate` 및 `System.MulticastDelegate` 클래스는 자체가 대리자 형식이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-160">Interestingly, the `System.Delegate` and `System.MulticastDelegate` classes are not themselves delegate types.</span></span> <span data-ttu-id="63c0c-161">모든 특정 대리자 형식에 대한 기초를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-161">They do provide the basis for all specific delegate types.</span></span> <span data-ttu-id="63c0c-162">동일한 언어 디자인 프로세스에서는 `Delegate` 또는 `MulticastDelegate`에서 파생되는 클래스를 선언할 수 없도록 요구했습니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-162">That same language design process mandated that you cannot declare a class that derives from `Delegate` or `MulticastDelegate`.</span></span> <span data-ttu-id="63c0c-163">C# 언어 규칙은 이러한 선언을 금지합니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-163">The C# language rules prohibit it.</span></span>

<span data-ttu-id="63c0c-164">대신에 C# 컴파일러는 C# 언어 키워드를 사용하여 대리자 형식을 선언할 경우 `MulticastDelegate`에서 파생된 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-164">Instead, the C# compiler creates instances of a class derived from `MulticastDelegate` when you use the C# language keyword to declare delegate types.</span></span>

<span data-ttu-id="63c0c-165">이 디자인은 C# 및 .NET의 첫 번째 릴리스를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-165">This design has its roots in the first release of C# and .NET.</span></span> <span data-ttu-id="63c0c-166">디자인 팀의 한 가지 목적은 언어에서 대리자를 사용할 때 형식 안전성을 적용하는지 확인하는 것이었습니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-166">One goal for the design team was to ensure that the language enforced type safety when using delegates.</span></span> <span data-ttu-id="63c0c-167">이는 대리자가 인수의 올바른 형식 및 개수를 사용하여 호출되는지 확인함을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-167">That meant ensuring that delegates were invoked with the right type and number of arguments.</span></span> <span data-ttu-id="63c0c-168">또한 컴파일 시간에 반환 형식이 제대로 표시되었는지 확인함을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-168">And, that any return type was correctly indicated at compile time.</span></span> <span data-ttu-id="63c0c-169">대리자는 이전에 제네릭이었던 1.0 .NET 릴리스의 일부였습니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-169">Delegates were part of the 1.0 .NET release, which was before generics.</span></span>

<span data-ttu-id="63c0c-170">이 형식 안전성을 적용하는 가장 좋은 방법은 컴파일러에서 사용되는 메서드 시그니처를 표현한 구체적인 대리자 클래스를 만드는 것이었습니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-170">The best way to enforce this type safety was for the compiler to create the concrete delegate classes that represented the method signature being used.</span></span>

<span data-ttu-id="63c0c-171">파생 클래스를 만들 수 없더라도 이러한 클래스에서 정의된 메서드를 사용하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-171">Even though you cannot create derived classes directly, you will use the methods defined on these classes.</span></span> <span data-ttu-id="63c0c-172">대리자 관련 작업을 수행할 때 사용할 가장 일반적인 메서드를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-172">Let's go through the most common methods that you will use when you work with delegates.</span></span>

<span data-ttu-id="63c0c-173">기억해야 하는 가장 중요한 첫 번째 사실은 사용하는 모든 대리자는 `MulticastDelegate`에서 파생된다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-173">The first, most important fact to remember is that every delegate you work with is derived from `MulticastDelegate`.</span></span> <span data-ttu-id="63c0c-174">멀티캐스트 대리자는 대리자를 통해 호출할 경우 두 개 이상의 메서드 대상이 호출될 수 있음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-174">A multicast delegate means that more than one method target can be invoked when invoking through a delegate.</span></span> <span data-ttu-id="63c0c-175">원래 디자인에서는 하나의 대상 메서드만 연결 및 호출할 수 대리자와 여러 대상 메서드를 연결 및 호출할 수 있는 대리자를 구분하도록 고려했습니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-175">The original design considered making a distinction between delegates where only one target method could be attached and invoked, and delegates where multiple target methods could be attached and invoked.</span></span> <span data-ttu-id="63c0c-176">이 구분은 원래 고려한 것보다 실제로 그다지 유용하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-176">That distinction proved to be less useful in practice than originally thought.</span></span> <span data-ttu-id="63c0c-177">두 가지 클래스가 이미 만들어졌고 초기 공식 릴리스 이후 프레임워크에 포함되었습니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-177">The two different classes were already created, and have been in the framework since its initial public release.</span></span>

<span data-ttu-id="63c0c-178">대리자와 함께 가장 많이 사용할 메서드는 `Invoke()` 및 `BeginInvoke()` / `EndInvoke()`입니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-178">The methods that you will use the most with delegates are `Invoke()` and `BeginInvoke()` / `EndInvoke()`.</span></span> <span data-ttu-id="63c0c-179">`Invoke()`는 특정 대리자 인스턴스에 연결된 모든 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-179">`Invoke()` will invoke all the methods that have been attached to a particular delegate instance.</span></span> <span data-ttu-id="63c0c-180">위에서 확인한 대로, 일반적으로 대리자 변수에서 메서드 호출 스택을 사용하여 대리자를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-180">As you saw above, you typically invoke delegates using the method call syntax on the delegate variable.</span></span> <span data-ttu-id="63c0c-181">[이 시리즈의 뒷부분](delegates-patterns.md)에서 살펴보겠지만 이러한 메서드에서 직접 사용되는 패턴이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-181">As you'll see [later in this series](delegates-patterns.md), there are patterns that work directly with these methods.</span></span>

<span data-ttu-id="63c0c-182">이제 언어 구문 및 대리자 지원 클래스를 확인했으므로 강력한 형식의 대리자를 사용하고, 만들고, 호출하는 방법을 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="63c0c-182">Now that you've seen the language syntax and the classes that support delegates, let's examine how strongly typed delegates are used, created, and invoked.</span></span>

[<span data-ttu-id="63c0c-183">다음</span><span class="sxs-lookup"><span data-stu-id="63c0c-183">Next</span></span>](delegates-strongly-typed.md)
