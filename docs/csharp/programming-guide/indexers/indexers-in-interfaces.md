---
title: 인터페이스의 인덱서 - C# 프로그래밍 가이드
description: C#의 인터페이스에 인덱서를 선언할 수 있습니다. 인터페이스 인덱서의 접근자와 클래스 인덱서의 접근자가 어떻게 다른지 알아봅니다.
ms.date: 02/08/2020
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: ec77843bdf3181a543bd6c02cfb034b21ded1ae7
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303103"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a><span data-ttu-id="8f494-104">인터페이스의 인덱서(C# 프로그래밍 가이드)</span><span class="sxs-lookup"><span data-stu-id="8f494-104">Indexers in Interfaces (C# Programming Guide)</span></span>

<span data-ttu-id="8f494-105">[interface](../../language-reference/keywords/interface.md)에 인덱서를 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f494-105">Indexers can be declared on an [interface](../../language-reference/keywords/interface.md).</span></span> <span data-ttu-id="8f494-106">인터페이스 인덱서 접근자와 [class](../../language-reference/keywords/class.md) 인덱서 접근자 간에는 다음과 같은 차이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f494-106">Accessors of interface indexers differ from the accessors of [class](../../language-reference/keywords/class.md) indexers in the following ways:</span></span>

- <span data-ttu-id="8f494-107">인터페이스 접근자는 한정자를 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8f494-107">Interface accessors do not use modifiers.</span></span>
- <span data-ttu-id="8f494-108">일반적으로 인터페이스 접근자에는 본문이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8f494-108">An interface accessor typically does not have a body.</span></span>

<span data-ttu-id="8f494-109">접근자의 목적은 인덱서가 읽기/쓰기인지, 읽기 전용인지, 쓰기 전용인지를 나타내는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8f494-109">The purpose of the accessor is to indicate whether the indexer is read-write, read-only, or write-only.</span></span> <span data-ttu-id="8f494-110">인터페이스에 정의된 인덱서에 대해 구현을 정의할 수 있긴 하나, 이는 드문 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="8f494-110">You may provide an implementation for an indexer defined in an interface, but this is rare.</span></span> <span data-ttu-id="8f494-111">인덱서는 일반적으로 API를 정의하여 데이터 필드에 액세스하는데, 데이터 필드는 인터페이스에서 정의할 수 없기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="8f494-111">Indexers typically define an API to access data fields, and data fields cannot be defined in an interface.</span></span>

<span data-ttu-id="8f494-112">다음은 인터페이스 인덱서 접근자의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="8f494-112">The following is an example of an interface indexer accessor:</span></span>

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#DefineIndexer)]

<span data-ttu-id="8f494-113">인덱서의 시그니처는 동일한 인터페이스에 선언된 다른 모든 인덱서의 시그니처와 달라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f494-113">The signature of an indexer must differ from the signatures of all other indexers declared in the same interface.</span></span>

## <a name="example"></a><span data-ttu-id="8f494-114">예제</span><span class="sxs-lookup"><span data-stu-id="8f494-114">Example</span></span>

<span data-ttu-id="8f494-115">다음 예제에서는 인터페이스 인덱서를 구현하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8f494-115">The following example shows how to implement interface indexers.</span></span>

[!code-csharp[Implement](~/samples/snippets/csharp/interfaces/indexers.cs#ImplementInterface)]

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#ExampleCode)]

<span data-ttu-id="8f494-116">앞의 예제에서는 인터페이스 멤버의 정규화된 이름을 사용하여 명시적 인터페이스 멤버 구현을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f494-116">In the preceding example, you could use the explicit interface member implementation by using the fully qualified name of the interface member.</span></span> <span data-ttu-id="8f494-117">예</span><span class="sxs-lookup"><span data-stu-id="8f494-117">For example</span></span>

```csharp
string IIndexInterface.this[int index]
{
}
```

<span data-ttu-id="8f494-118">그러나 정규화된 이름은 클래스가 동일한 인덱서 시그니처로 둘 이상의 인터페이스를 구현할 때 모호성을 피하기 위해서만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="8f494-118">However, the fully qualified name is only needed to avoid ambiguity when the class is implementing more than one interface with the same indexer signature.</span></span> <span data-ttu-id="8f494-119">예를 들어 `Employee` 클래스가 두 인터페이스 `ICitizen` 및 `IEmployee`를 구현하고 두 인터페이스의 인덱서 시그니처가 같으면 명시적 인터페이스 멤버 구현이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="8f494-119">For example, if an `Employee` class is implementing two interfaces, `ICitizen` and `IEmployee`, and both interfaces have the same indexer signature, the explicit interface member implementation is necessary.</span></span> <span data-ttu-id="8f494-120">즉, 다음과 같은 인덱서 선언이 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f494-120">That is, the following indexer declaration:</span></span>

```csharp
string IEmployee.this[int index]
{
}
```

<span data-ttu-id="8f494-121">이 선언은 `IEmployee` 인터페이스의 인덱서를 구현합니다. 또한 다음과 같은 선언이 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f494-121">implements the indexer on the `IEmployee` interface, while the following declaration:</span></span>

```csharp
string ICitizen.this[int index]
{
}
```

<span data-ttu-id="8f494-122">이 선언은 `ICitizen` 인터페이스의 인덱서를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="8f494-122">implements the indexer on the `ICitizen` interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="8f494-123">참조</span><span class="sxs-lookup"><span data-stu-id="8f494-123">See also</span></span>

- [<span data-ttu-id="8f494-124">C# 프로그래밍 가이드</span><span class="sxs-lookup"><span data-stu-id="8f494-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8f494-125">인덱서</span><span class="sxs-lookup"><span data-stu-id="8f494-125">Indexers</span></span>](./index.md)
- [<span data-ttu-id="8f494-126">속성</span><span class="sxs-lookup"><span data-stu-id="8f494-126">Properties</span></span>](../classes-and-structs/properties.md)
- [<span data-ttu-id="8f494-127">인터페이스</span><span class="sxs-lookup"><span data-stu-id="8f494-127">Interfaces</span></span>](../interfaces/index.md)
