---
title: 사용자 정의 전환 연산자 - C# 참조
description: C#에서 사용자 지정 암시적 및 명시적 형식 변환을 정의하는 방법을 알아봅니다.
ms.date: 07/09/2019
f1_keywords:
- explicit_CSharpKeyword
- implicit_CSharpKeyword
- explicit
- implicit
helpviewer_keywords:
- explicit keyword [C#]
- implicit keyword [C#]
- conversion operator [C#]
- user-defined conversion [C#]
ms.openlocfilehash: a0eb11d55ad9e9cccde1704ba4c5ae8acb609989
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916634"
---
# <a name="user-defined-conversion-operators-c-reference"></a>사용자 정의 전환 연산자(C# 참조)

사용자 정의 형식은 다른 형식에서 또는 다른 형식으로 사용자 지정 암시적 또는 명시적 변환을 정의할 수 있습니다.

암시적 변환은 특별한 구문을 호출할 필요가 없으며, 할당과 메서드 호출과 같은 다양한 상황에서 발생할 수 있습니다. 미리 정의된 C# 암시적 변환은 항상 성공하며 예외를 throw하지 않습니다. 사용자 정의 암시적 변화도 이러한 방식으로 작동해야 합니다. 사용자 지정 변환이 예외를 throw하거나 정보가 손실될 수 있는 경우 이를 명시적 변환으로 정의합니다.

사용자 정의 변환은 [is](type-testing-and-cast.md#is-operator) 및 [as](type-testing-and-cast.md#as-operator) 연산자로 간주되지 않습니다. [캐스트 식](type-testing-and-cast.md#cast-expression)을 사용하여 사용자 정의 명시적 변환을 호출합니다.

`operator` 및 `implicit` 또는 `explicit` 키워드를 사용하여 각각 암시적 또는 명시적 변환을 정의합니다. 변환을 정의하는 유형은 해당 변환의 소스 유형 또는 대상 유형이어야 합니다. 두 형식 중 하나에서 두 개의 사용자 정의 형식 간의 변환을 정의할 수 있습니다.

다음 예제에서는 암시적 및 명시적 변환을 정의하는 방법을 보여줍니다.

[!code-csharp[implicit an explicit conversions](snippets/shared/UserDefinedConversions.cs)]

또한 `operator` 키워드를 사용하여 미리 정의된 C# 연산자를 오버로드합니다. 자세한 내용은 [연산자 오버로드](operator-overloading.md)를 참조하세요.

## <a name="c-language-specification"></a>C# 언어 사양

자세한 내용은 [C# 언어 사양](~/_csharplang/spec/introduction.md)의 다음 섹션을 참조하세요.

- [변환 연산자](~/_csharplang/spec/classes.md#conversion-operators)
- [사용자 정의 변환](~/_csharplang/spec/conversions.md#user-defined-conversions)
- [암시적 변환](~/_csharplang/spec/conversions.md#implicit-conversions)
- [명시적 변환](~/_csharplang/spec/conversions.md#explicit-conversions)

## <a name="see-also"></a>참조

- [C# 참조](../index.md)
- [C# 연산자 및 식](index.md)
- [연산자 오버로드](operator-overloading.md)
- [형식 테스트 및 캐스트 연산자](type-testing-and-cast.md)
- [캐스팅 및 형식 변환](../../programming-guide/types/casting-and-type-conversions.md)
- [디자인 지침 - 변환 연산자](../../../standard/design-guidelines/operator-overloads.md#conversion-operators)
- [Chained user-defined explicit conversions in C#](https://docs.microsoft.com/archive/blogs/ericlippert/chained-user-defined-explicit-conversions-in-c)(C#의 연결된 사용자 정의 명시적 변환)
