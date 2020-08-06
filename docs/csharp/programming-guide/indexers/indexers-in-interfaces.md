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
# <a name="indexers-in-interfaces-c-programming-guide"></a>인터페이스의 인덱서(C# 프로그래밍 가이드)

[interface](../../language-reference/keywords/interface.md)에 인덱서를 선언할 수 있습니다. 인터페이스 인덱서 접근자와 [class](../../language-reference/keywords/class.md) 인덱서 접근자 간에는 다음과 같은 차이점이 있습니다.

- 인터페이스 접근자는 한정자를 사용하지 않습니다.
- 일반적으로 인터페이스 접근자에는 본문이 없습니다.

접근자의 목적은 인덱서가 읽기/쓰기인지, 읽기 전용인지, 쓰기 전용인지를 나타내는 것입니다. 인터페이스에 정의된 인덱서에 대해 구현을 정의할 수 있긴 하나, 이는 드문 경우입니다. 인덱서는 일반적으로 API를 정의하여 데이터 필드에 액세스하는데, 데이터 필드는 인터페이스에서 정의할 수 없기 때문입니다.

다음은 인터페이스 인덱서 접근자의 예입니다.

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#DefineIndexer)]

인덱서의 시그니처는 동일한 인터페이스에 선언된 다른 모든 인덱서의 시그니처와 달라야 합니다.

## <a name="example"></a>예제

다음 예제에서는 인터페이스 인덱서를 구현하는 방법을 보여 줍니다.

[!code-csharp[Implement](~/samples/snippets/csharp/interfaces/indexers.cs#ImplementInterface)]

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#ExampleCode)]

앞의 예제에서는 인터페이스 멤버의 정규화된 이름을 사용하여 명시적 인터페이스 멤버 구현을 사용할 수 있습니다. 예

```csharp
string IIndexInterface.this[int index]
{
}
```

그러나 정규화된 이름은 클래스가 동일한 인덱서 시그니처로 둘 이상의 인터페이스를 구현할 때 모호성을 피하기 위해서만 필요합니다. 예를 들어 `Employee` 클래스가 두 인터페이스 `ICitizen` 및 `IEmployee`를 구현하고 두 인터페이스의 인덱서 시그니처가 같으면 명시적 인터페이스 멤버 구현이 필요합니다. 즉, 다음과 같은 인덱서 선언이 있다고 가정합니다.

```csharp
string IEmployee.this[int index]
{
}
```

이 선언은 `IEmployee` 인터페이스의 인덱서를 구현합니다. 또한 다음과 같은 선언이 있다고 가정합니다.

```csharp
string ICitizen.this[int index]
{
}
```

이 선언은 `ICitizen` 인터페이스의 인덱서를 구현합니다.

## <a name="see-also"></a>참조

- [C# 프로그래밍 가이드](../index.md)
- [인덱서](./index.md)
- [속성](../classes-and-structs/properties.md)
- [인터페이스](../interfaces/index.md)
