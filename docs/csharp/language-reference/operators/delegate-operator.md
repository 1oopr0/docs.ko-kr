---
description: delegate 연산자 - C# 참조
title: delegate 연산자 - C# 참조
ms.date: 09/25/2020
helpviewer_keywords:
- delegate [C#]
- anonymous method [C#]
ms.openlocfilehash: db2bf673db12e4a10741a26112820726a4b8aaee
ms.sourcegitcommit: c04535ad05e374fb269fcfc6509217755fbc0d54
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91247659"
---
# <a name="delegate-operator-c-reference"></a>delegate 연산자(C# 참조)

`delegate` 연산자는 대리자 형식으로 변환될 수 있는 무명 메서드를 만듭니다.

[!code-csharp-interactive[anonymous method](snippets/shared/DelegateOperator.cs#AnonymousMethod)]

> [!NOTE]
> C# 3으로 시작하는 람다 식은 익명 함수를 만드는 더 간결하고 이해하기 쉬운 방법을 제공합니다. [=> 연산자](lambda-operator.md)를 사용하여 람다 식을 구성합니다.
>
> [!code-csharp-interactive[lambda expression](snippets/shared/DelegateOperator.cs#Lambda)]
>
> 람다 식의 기능(예: 외부 변수 캡처)에 대한 자세한 내용은 [람다 식](lambda-expressions.md)을 참조하세요.

`delegate` 연산자를 사용하는 경우 매개 변수 목록을 생략할 수 있습니다. 이렇게 하면 다음 예제와 같이 매개 변수 목록을 사용하여 생성된 무명 메서드를 대리자 형식으로 변환할 수 있습니다.

[!code-csharp-interactive[no parameter list](snippets/shared/DelegateOperator.cs#WithoutParameterList)]

이 기능은 람다 식에서 지원되지 않는 무명 메서드의 유일한 기능입니다. 다른 모든 경우 인라인 코드를 작성하는 데 람다 식이 선호됩니다.

C# 9.0부터 [무시 항목](../../discards.md)을 사용하여 무명 메서드에서 사용하지 않는 입력 매개 변수를 두 개 이상 지정할 수 있습니다.

:::code language="csharp" source="snippets/shared/DelegateOperator.cs" id="SnippetDiscards" :::

이전 버전과의 호환성을 위해, 단일 매개 변수만 `_`로 명명된 경우 `_`가 무명 메서드 내에서 해당 매개 변수의 이름으로 처리됩니다.

또한 C# 9.0부터 무명 메서드 선언에 `static` 한정자를 사용할 수 있습니다.

:::code language="csharp" source="snippets/shared/DelegateOperator.cs" id="SnippetStatic" :::

정적 무명 메서드는 바깥쪽 범위에서 지역 변수 또는 인스턴스 상태를 캡처할 수 없습니다.

`delegate` 키워드를 사용하여 [대리자 형식](../builtin-types/reference-types.md#the-delegate-type)을 선언할 수도 있습니다.

## <a name="c-language-specification"></a>C# 언어 사양

자세한 내용은 [C# 언어 사양](~/_csharplang/spec/introduction.md)의 [익명 함수 식](~/_csharplang/spec/expressions.md#anonymous-function-expressions) 섹션을 참조하세요.

## <a name="see-also"></a>참고 항목

- [C# 참조](../index.md)
- [C# 연산자 및 식](index.md)
- [=> 연산자](lambda-operator.md)
