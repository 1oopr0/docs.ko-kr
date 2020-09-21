---
title: 제네릭 형식(제네릭) 개요
description: 제네릭이 실제 데이터 형식에 커밋하지 않고 형식이 안전한 데이터 구조를 정의할 수 있게 해주는 코드 템플릿으로 사용되는 방법을 알아봅니다.
author: kuhlenh
ms.author: wiwagn
ms.date: 10/09/2018
ms.openlocfilehash: 5f6e84e23b5bcdcb3dcd742823d83728fb43d195
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557946"
---
# <a name="generic-types-overview"></a><span data-ttu-id="959a6-103">제네릭 형식 개요</span><span class="sxs-lookup"><span data-stu-id="959a6-103">Generic types overview</span></span>

<span data-ttu-id="959a6-104">개발자는 암시적이든 명시적이든 .NET에서 항상 제네릭을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="959a6-104">Developers use generics all the time in .NET, whether implicitly or explicitly.</span></span> <span data-ttu-id="959a6-105">.NET에서 LINQ를 사용할 때 <xref:System.Collections.Generic.IEnumerable%601>로 작업하고 있다는 것을 알아차리셨나요?</span><span class="sxs-lookup"><span data-stu-id="959a6-105">When you use LINQ in .NET, did you ever notice that you're working with <xref:System.Collections.Generic.IEnumerable%601>?</span></span> <span data-ttu-id="959a6-106">또는 Entity Framework를 사용하여 데이터베이스에 통신하기 위한 “제네릭 리포지토리”의 온라인 샘플을 본 적이 있다면 대부분의 메서드가 `IQueryable<T>`를 반환하는 것을 보셨습니까?</span><span class="sxs-lookup"><span data-stu-id="959a6-106">Or if you ever saw an online sample of a "generic repository" for talking to databases using Entity Framework, did you see that most methods return `IQueryable<T>`?</span></span> <span data-ttu-id="959a6-107">이러한 예제에서 **T**가 무엇이고 왜 사용되는지 궁금하게 여겼을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="959a6-107">You may have wondered what the **T** is in these examples and why it's in there.</span></span>

<span data-ttu-id="959a6-108">.NET Framework 2.0에서 처음 소개된 제네릭은 기본적으로 개발자가 실제 데이터 형식에 커밋하지 않고 [형식이 안전한](/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100)) 데이터 구조를 정의할 수 있게 해주는 “코드 템플릿”입니다.</span><span class="sxs-lookup"><span data-stu-id="959a6-108">First introduced in the .NET Framework 2.0, generics are essentially a "code template" that allows developers to define [type-safe](/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100)) data structures without committing to an actual data type.</span></span> <span data-ttu-id="959a6-109">예를 들어 <xref:System.Collections.Generic.List%601>는 `List<int>`, `List<string>` 또는 `List<Person>`과 같은 모든 형식으로 선언하고 사용할 수 있는 [제네릭 컬렉션](xref:System.Collections.Generic)입니다.</span><span class="sxs-lookup"><span data-stu-id="959a6-109">For example, <xref:System.Collections.Generic.List%601> is a [generic collection](xref:System.Collections.Generic) that can be declared and used with any type, such as `List<int>`, `List<string>`, or `List<Person>`.</span></span>

<span data-ttu-id="959a6-110">제네릭이 유용한 이유를 이해하려면 제네릭을 추가하기 전과 이후의 특정 클래스인 <xref:System.Collections.ArrayList>를 살펴보아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="959a6-110">To understand why generics are useful, let's take a look at a specific class before and after adding generics: <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="959a6-111">.NET Framework 1.0에서 `ArrayList` 요소는 <xref:System.Object> 형식이었습니다.</span><span class="sxs-lookup"><span data-stu-id="959a6-111">In .NET Framework 1.0, the `ArrayList` elements were of type <xref:System.Object>.</span></span> <span data-ttu-id="959a6-112">컬렉션에 추가된 모든 요소가 자동으로 `Object`로 변환되었습니다.</span><span class="sxs-lookup"><span data-stu-id="959a6-112">Any element added to the collection was silently converted into an `Object`.</span></span> <span data-ttu-id="959a6-113">목록에서 요소를 읽을 때 동일한 작업이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="959a6-113">The same would happen when reading elements from the list.</span></span> <span data-ttu-id="959a6-114">[boxing 및 unboxing](../csharp/programming-guide/types/boxing-and-unboxing.md)이라고 하는 이 프로세스는 성능에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="959a6-114">This process is known as [boxing and unboxing](../csharp/programming-guide/types/boxing-and-unboxing.md), and it impacts performance.</span></span> <span data-ttu-id="959a6-115">그러나 성능 외에도 컴파일 시간에 목록에 있는 데이터 형식을 결정하는 방법이 없으므로 손상되기 쉬운 일부 코드가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="959a6-115">Aside from performance, however, there's no way to determine the type of data in the list at compile time, which makes for some fragile code.</span></span> <span data-ttu-id="959a6-116">제네릭은 목록의 각 인스턴스에 포함될 데이터 형식을 정의하여 이 문제를 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="959a6-116">Generics solve this problem by defining the type of data each instance of list will contain.</span></span> <span data-ttu-id="959a6-117">예를 들어 `List<int>`에는 정수만 추가하고 `List<Person>`에는 사용자만 추가하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="959a6-117">For example, you can only add integers to `List<int>` and only add Persons to `List<Person>`.</span></span>

<span data-ttu-id="959a6-118">또한 제네릭은 런타임에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="959a6-118">Generics are also available at run time.</span></span> <span data-ttu-id="959a6-119">런타임에서 사용 중인 데이터 구조의 형식을 알고 메모리에 더욱 효율적으로 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="959a6-119">The runtime knows what type of data structure you're using and can store it in memory more efficiently.</span></span>

<span data-ttu-id="959a6-120">다음 예제에는 런타임에 데이터 구조 형식을 알고 있을 경우의 효율성을 보여 주는 작은 프로그램이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="959a6-120">The following example is a small program that illustrates the efficiency of knowing the data structure type at run time:</span></span>

```csharp
  using System;
  using System.Collections;
  using System.Collections.Generic;
  using System.Diagnostics;

  namespace GenericsExample {
    class Program {
      static void Main(string[] args) {
        //generic list
        List<int> ListGeneric = new List<int> { 5, 9, 1, 4 };
        //non-generic list
        ArrayList ListNonGeneric = new ArrayList { 5, 9, 1, 4 };
        // timer for generic list sort
        Stopwatch s = Stopwatch.StartNew();
        ListGeneric.Sort();
        s.Stop();
        Console.WriteLine($"Generic Sort: {ListGeneric}  \n Time taken: {s.Elapsed.TotalMilliseconds}ms");

        //timer for non-generic list sort
        Stopwatch s2 = Stopwatch.StartNew();
        ListNonGeneric.Sort();
        s2.Stop();
        Console.WriteLine($"Non-Generic Sort: {ListNonGeneric}  \n Time taken: {s2.Elapsed.TotalMilliseconds}ms");
        Console.ReadLine();
      }
    }
  }
```

<span data-ttu-id="959a6-121">이 프로그램은 다음과 비슷한 출력을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="959a6-121">This program produces output similar to the following:</span></span>

```console
Generic Sort: System.Collections.Generic.List`1[System.Int32]
 Time taken: 0.0034ms
Non-Generic Sort: System.Collections.ArrayList
 Time taken: 0.2592ms
```

<span data-ttu-id="959a6-122">여기서 알 수 있는 첫 번째 사항은 제네릭 목록의 정렬 속도가 제네릭이 아닌 목록보다 훨씬 빠르다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="959a6-122">The first thing you can notice here is that sorting the generic list is significantly faster than sorting the non-generic list.</span></span> <span data-ttu-id="959a6-123">제네릭 목록의 형식은 고유 형식([System.Int32])인 반면 제네릭이 아닌 목록의 형식은 일반 형식이라는 것도 발견했을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="959a6-123">You might also notice that the type for the generic list is distinct ([System.Int32]), whereas the type for the non-generic list is generalized.</span></span> <span data-ttu-id="959a6-124">제네릭 `List<int>`의 형식이 <xref:System.Int32>임을 런타임에서 알고 있으므로 메모리의 기본 정수 배열에 목록 요소를 저장할 수 있는 반면, 제네릭이 아닌 `ArrayList`는 각 목록 요소를 개체로 캐스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="959a6-124">Because the runtime knows the generic `List<int>` is of type <xref:System.Int32>, it can store the list elements in an underlying integer array in memory, while the non-generic `ArrayList` has to cast each list element to an object.</span></span> <span data-ttu-id="959a6-125">이 예제에 나와 있는 대로 추가 캐스트는 시간이 걸리며 목록 정렬 속도가 느려집니다.</span><span class="sxs-lookup"><span data-stu-id="959a6-125">As this example shows, the extra casts take up time and slow down the list sort.</span></span>

<span data-ttu-id="959a6-126">런타임에서 제네릭 형식을 알고 있을 경우의 추가적인 이점은 향상된 디버깅 환경입니다.</span><span class="sxs-lookup"><span data-stu-id="959a6-126">An additional advantage of the runtime knowing the type of your generic is a better debugging experience.</span></span> <span data-ttu-id="959a6-127">C#에서 제네릭을 디버그하는 경우 데이터 구조의 각 요소가 어떤 형식인지 알고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="959a6-127">When you're debugging a generic in C#, you know what type each element is in your data structure.</span></span> <span data-ttu-id="959a6-128">제네릭이 없었다면 각 요소의 형식을 알 수 없었을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="959a6-128">Without generics, you would have no idea what type each element was.</span></span>

## <a name="see-also"></a><span data-ttu-id="959a6-129">참조</span><span class="sxs-lookup"><span data-stu-id="959a6-129">See also</span></span>

- [<span data-ttu-id="959a6-130">C# 프로그래밍 가이드 - 제네릭</span><span class="sxs-lookup"><span data-stu-id="959a6-130">C# Programming Guide - Generics</span></span>](../csharp/programming-guide/generics/index.md)
