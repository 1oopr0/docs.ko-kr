---
title: 제네릭 메서드 - C# 프로그래밍 가이드
description: 제네릭 메서드라고 하는 형식 매개 변수를 사용하여 선언된 메서드에 대해 알아봅니다. 코드 예제를 살펴보고 사용 가능한 추가 리소스를 확인합니다.
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], methods
ms.assetid: 673eeea2-4b48-4faa-9c4e-2e89449221b9
ms.openlocfilehash: 195e3f11c73a17931fa6331750e2ae4ee8fd6f10
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151469"
---
# <a name="generic-methods-c-programming-guide"></a><span data-ttu-id="3f705-104">제네릭 메서드(C# 프로그래밍 가이드)</span><span class="sxs-lookup"><span data-stu-id="3f705-104">Generic Methods (C# Programming Guide)</span></span>

<span data-ttu-id="3f705-105">제네릭 메서드는 다음과 같은 형식 매개 변수를 사용하여 선언된 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="3f705-105">A generic method is a method that is declared with type parameters, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#22)]  
  
 <span data-ttu-id="3f705-106">다음 코드 예제는 형식 인수에 `int`를 사용하여 메서드를 호출하는 한 가지 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3f705-106">The following code example shows one way to call the method by using `int` for the type argument:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#23)]  
  
 <span data-ttu-id="3f705-107">형식 인수를 생략하고 컴파일러에서 이를 자동으로 유추하도록 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f705-107">You can also omit the type argument and the compiler will infer it.</span></span> <span data-ttu-id="3f705-108">`Swap`에 대한 다음 호출은 위 예제의 호출과 동일한 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="3f705-108">The following call to `Swap` is equivalent to the previous call:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#24)]  
  
 <span data-ttu-id="3f705-109">정적 메서드와 인스턴스 메서드에는 형식 유추와 동일한 규칙이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f705-109">The same rules for type inference apply to static methods and instance methods.</span></span> <span data-ttu-id="3f705-110">컴파일러는 전달한 메서드 인수에 따라 형식 매개 변수를 유추할 수 있지만, 제약 조건이나 반환 값만으로는 형식 매개 변수를 유추할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3f705-110">The compiler can infer the type parameters based on the method arguments you pass in; it cannot infer the type parameters only from a constraint or return value.</span></span> <span data-ttu-id="3f705-111">따라서 매개 변수가 없는 메서드에 대해서는 형식 유추가 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3f705-111">Therefore type inference does not work with methods that have no parameters.</span></span> <span data-ttu-id="3f705-112">형식 유추는 컴파일러에서 오버로드된 메서드 시그니처를 확인하려고 하기 전에 컴파일 시간에 진행됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f705-112">Type inference occurs at compile time before the compiler tries to resolve overloaded method signatures.</span></span> <span data-ttu-id="3f705-113">컴파일러는 동일한 이름을 공유하는 모든 제네릭 메서드에 형식 유추 논리를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="3f705-113">The compiler applies type inference logic to all generic methods that share the same name.</span></span> <span data-ttu-id="3f705-114">오버로드 확인 단계에서 컴파일러는 형식 유추에 성공한 제네릭 메서드만 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="3f705-114">In the overload resolution step, the compiler includes only those generic methods on which type inference succeeded.</span></span>  
  
 <span data-ttu-id="3f705-115">제네릭 클래스 내에서 제네릭이 아닌 메서드는 다음과 같은 클래스 수준의 형식 매개 변수에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f705-115">Within a generic class, non-generic methods can access the class-level type parameters, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#25)]  
  
 <span data-ttu-id="3f705-116">포함하는 클래스와 동일한 형식 매개 변수를 사용하는 제네릭 메서드를 정의하면 컴파일러에서 [CS0693](../../misc/cs0693.md) 경고가 발생합니다. 메서드 범위 내에서 내부 `T`에 제공된 인수가 외부 `T`에 제공된 인수를 숨기기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="3f705-116">If you define a generic method that takes the same type parameters as the containing class, the compiler generates warning [CS0693](../../misc/cs0693.md) because within the method scope, the argument supplied for the inner `T` hides the argument supplied for the outer `T`.</span></span> <span data-ttu-id="3f705-117">클래스를 인스턴스화할 때 제공한 형식 인수가 아닌 다른 형식 인수를 사용하여 제네릭 클래스 메서드를 호출할 수 있으려면 다음 예제의 `GenericList2<T>`에서와 같이 메서드의 형식 매개 변수에 다른 식별자를 제공해 보세요.</span><span class="sxs-lookup"><span data-stu-id="3f705-117">If you require the flexibility of calling a generic class method with type arguments other than the ones provided when the class was instantiated, consider providing another identifier for the type parameter of the method, as shown in `GenericList2<T>` in the following example.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#26)]  
  
 <span data-ttu-id="3f705-118">메서드에서 형식 매개 변수에 대한 더 구체적인 작업을 수행하려면 제약 조건을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3f705-118">Use constraints to enable more specialized operations on type parameters in methods.</span></span> <span data-ttu-id="3f705-119">`SwapIfGreater<T>`라는 이 버전의 `Swap<T>`은 <xref:System.IComparable%601>을 구현하는 형식 인수와만 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f705-119">This version of `Swap<T>`, now named `SwapIfGreater<T>`, can only be used with type arguments that implement <xref:System.IComparable%601>.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#27)]  
  
 <span data-ttu-id="3f705-120">제네릭 메서드는 몇몇 형식 매개 변수에 오버로드될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f705-120">Generic methods can be overloaded on several type parameters.</span></span> <span data-ttu-id="3f705-121">예를 들어 다음 메서드는 모두 동일한 클래스에 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f705-121">For example, the following methods can all be located in the same class:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#28)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="3f705-122">C# 언어 사양</span><span class="sxs-lookup"><span data-stu-id="3f705-122">C# Language Specification</span></span>  

 <span data-ttu-id="3f705-123">자세한 내용은 [C# 언어 사양](~/_csharplang/spec/classes.md#methods)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3f705-123">For more information, see the [C# Language Specification](~/_csharplang/spec/classes.md#methods).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f705-124">참조</span><span class="sxs-lookup"><span data-stu-id="3f705-124">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="3f705-125">C# 프로그래밍 가이드</span><span class="sxs-lookup"><span data-stu-id="3f705-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3f705-126">제네릭 소개</span><span class="sxs-lookup"><span data-stu-id="3f705-126">Introduction to Generics</span></span>](./index.md)
- [<span data-ttu-id="3f705-127">메서드</span><span class="sxs-lookup"><span data-stu-id="3f705-127">Methods</span></span>](../classes-and-structs/methods.md)
