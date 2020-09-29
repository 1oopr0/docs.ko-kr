---
title: C++ 템플릿과 C# 제네릭의 차이점 - C# 프로그래밍 가이드
description: C++ 템플릿과 C# 제네릭의 차이점을 알아봅니다. 둘 다 매개 변수가 있는 형식에 대한 지원을 제공하는 언어 기능입니다.
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], vs. C++ templates
ms.assetid: 1da6beeb-d4a4-4da0-87b7-0cfbe04920b7
ms.openlocfilehash: 58b424e4dacd8b691c353f4eda1950f9710ef081
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167368"
---
# <a name="differences-between-c-templates-and-c-generics-c-programming-guide"></a><span data-ttu-id="42a20-104">C++ 템플릿과 C# 제네릭의 차이점(C# 프로그래밍 가이드)</span><span class="sxs-lookup"><span data-stu-id="42a20-104">Differences Between C++ Templates and C# Generics (C# Programming Guide)</span></span>

<span data-ttu-id="42a20-105">C# 제네릭 및 C++ 템플릿은 둘 다 매개 변수가 있는 형식을 지원하는 언어 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="42a20-105">C# Generics and C++ templates are both language features that provide support for parameterized types.</span></span> <span data-ttu-id="42a20-106">그러나 둘 사이에는 많은 차이가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42a20-106">However, there are many differences between the two.</span></span> <span data-ttu-id="42a20-107">구문 수준에서 C# 제네릭은 매개 변수가 있는 형식에 대한 더 간단한 접근 방식으로, C++ 템플릿의 복잡함이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="42a20-107">At the syntax level, C# generics are a simpler approach to parameterized types without the complexity of C++ templates.</span></span> <span data-ttu-id="42a20-108">또한 C#은 C++ 템플릿에서 제공하는 기능 중 일부를 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="42a20-108">In addition, C# does not attempt to provide all of the functionality that C++ templates provide.</span></span> <span data-ttu-id="42a20-109">구현 수준에서 주요 차이점은 런타임에 C# 제네릭 형식 대체가 수행되어 인스턴스화된 개체에 대해 제네릭 형식 정보가 유지된다는 점입니다.</span><span class="sxs-lookup"><span data-stu-id="42a20-109">At the implementation level, the primary difference is that C# generic type substitutions are performed at runtime and generic type information is thereby preserved for instantiated objects.</span></span> <span data-ttu-id="42a20-110">자세한 내용은 [런타임의 제네릭](./generics-in-the-run-time.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="42a20-110">For more information, see [Generics in the Run Time](./generics-in-the-run-time.md).</span></span>  
  
 <span data-ttu-id="42a20-111">다음은 C# 제네릭 및 C++ 템플릿 사이의 주요 차이점입니다.</span><span class="sxs-lookup"><span data-stu-id="42a20-111">The following are the key differences between C# Generics and C++ templates:</span></span>  
  
- <span data-ttu-id="42a20-112">C# 제네릭은 C++ 템플릿과 동일한 수준의 유연성을 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="42a20-112">C# generics do not provide the same amount of flexibility as C++ templates.</span></span> <span data-ttu-id="42a20-113">예를 들어 C# 제네릭 클래스에서 산술 연산자는 호출할 수 없지만 사용자 정의 연산자는 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42a20-113">For example, it is not possible to call arithmetic operators in a C# generic class, although it is possible to call user defined operators.</span></span>  
  
- <span data-ttu-id="42a20-114">C#에서는 `template C<int i> {}` 같은 비형식 템플릿 매개 변수를 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="42a20-114">C# does not allow non-type template parameters, such as `template C<int i> {}`.</span></span>  
  
- <span data-ttu-id="42a20-115">C#은 명시적 특수화 즉, 특정 형식에 대한 템플릿의 사용자 지정 구현을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="42a20-115">C# does not support explicit specialization; that is, a custom implementation of a template for a specific type.</span></span>  
  
- <span data-ttu-id="42a20-116">C#은 부분 특수화 즉, 형식 인수의 하위 집합에 대한 사용자 지정 구현을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="42a20-116">C# does not support partial specialization: a custom implementation for a subset of the type arguments.</span></span>  
  
- <span data-ttu-id="42a20-117">C#에서는 형식 매개 변수를 제네릭 형식에 대한 기본 클래스로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="42a20-117">C# does not allow the type parameter to be used as the base class for the generic type.</span></span>  
  
- <span data-ttu-id="42a20-118">C#에서는 형식 매개 변수가 기본 형식을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="42a20-118">C# does not allow type parameters to have default types.</span></span>  
  
- <span data-ttu-id="42a20-119">C#에서 제네릭 형식 매개 변수 자체는 제네릭이 될 수 없지만 생성된 형식은 제네릭으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42a20-119">In C#, a generic type parameter cannot itself be a generic, although constructed types can be used as generics.</span></span> <span data-ttu-id="42a20-120">C++에서는 템플릿 매개 변수를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="42a20-120">C++ does allow template parameters.</span></span>  
  
- <span data-ttu-id="42a20-121">C++에서는 템플릿의 일부 형식 매개 변수에 적합하지 않아 형식 매개 변수로 사용되는 특정 형식을 확인하는 코드를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="42a20-121">C++ allows code that might not be valid for all type parameters in the template, which is then checked for the specific type used as the type parameter.</span></span> <span data-ttu-id="42a20-122">C#에서는 제약 조건을 충족하는 모든 형식에서 작동하는 방식으로 작성할 코드가 클래스에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="42a20-122">C# requires code in a class to be written in such a way that it will work with any type that satisfies the constraints.</span></span> <span data-ttu-id="42a20-123">예를 들어 C++에서는 산술 연산자 `+` 및 `-`를 사용하는 함수를 형식 매개 변수의 개체에서 작성하여 이러한 연산자를 지원하지 않는 형식으로 템플릿을 인스턴스화할 때 오류를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42a20-123">For example, in C++ it is possible to write a function that uses the arithmetic operators `+` and `-` on objects of the type parameter, which will produce an error at the time of instantiation of the template with a type that does not support these operators.</span></span> <span data-ttu-id="42a20-124">C#에서는 이를 허용하지 않습니다. 허용되는 유일한 언어 구문은 제약 조건에서 추론할 수 있는 구문입니다.</span><span class="sxs-lookup"><span data-stu-id="42a20-124">C# disallows this; the only language constructs allowed are those that can be deduced from the constraints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42a20-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="42a20-125">See also</span></span>

- [<span data-ttu-id="42a20-126">C# 프로그래밍 가이드</span><span class="sxs-lookup"><span data-stu-id="42a20-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="42a20-127">제네릭 소개</span><span class="sxs-lookup"><span data-stu-id="42a20-127">Introduction to Generics</span></span>](./index.md)
- [<span data-ttu-id="42a20-128">템플릿</span><span class="sxs-lookup"><span data-stu-id="42a20-128">Templates</span></span>](/cpp/cpp/templates-cpp)
