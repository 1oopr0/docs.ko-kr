---
title: 네임스페이스 - C# 프로그래밍 가이드
description: C# 프로그래밍에서 네임스페이스에 대해 알아봅니다. 네임스페이스 속성의 개요를 확인하고 추가 리소스를 봅니다.
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: fca2c641520bd9cd19a48bff2119a6f09c3713ea
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87382102"
---
# <a name="namespaces-c-programming-guide"></a>네임스페이스(C# 프로그래밍 가이드)

네임스페이스는 C# 프로그래밍에서 두 가지 방법으로 많이 사용됩니다. 먼저 .NET은 다음과 같이 네임스페이스를 사용하여 여러 클래스를 구성합니다.  

[!code-csharp[csProgGuide#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#22)]

<xref:System>은 네임스페이스이고 <xref:System.Console>은 해당 네임스페이스의 클래스입니다. 전체 키워드가 필요하지 않으므로 다음 예처럼 `using` 키워드를 사용할 수 있습니다.

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#25)]

자세한 내용은 [using 지시문](../../language-reference/keywords/using-directive.md)을 참조하세요.

둘째, 고유한 네임스페이스를 선언하면 대규모 프로그래밍 프로젝트에서 클래스 및 메서드 이름의 범위를 제어할 수 있습니다. 다음 예와 같이 [네임스페이스](../../language-reference/keywords/namespace.md) 키워드를 사용하여 네임스페이스를 선언합니다.

[!code-csharp[csProgGuideNamespaces#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#6)]

네임스페이스 이름은 유효한 C# [식별자 이름](../inside-a-program/identifier-names.md)이어야 합니다.

## <a name="namespaces-overview"></a>네임스페이스 개요

네임스페이스에는 다음과 같은 속성이 있습니다.

- 대규모 코드 프로젝트를 구성합니다.
- `.` 연산자를 사용하여 구분됩니다.
- `using` 지시문은 모든 클래스에 대해 네임스페이스 이름을 지정할 필요가 없습니다.
- `global` 네임스페이스는 “루트” 네임스페이스입니다. `global::System`은 항상 .NET <xref:System> 네임스페이스를 가리킵니다.

## <a name="c-language-specification"></a>C# 언어 사양

자세한 내용은 [C# 언어 사양](~/_csharplang/spec/introduction.md)의 [네임스페이스](~/_csharplang/spec/namespaces.md) 섹션을 참조하세요.

## <a name="see-also"></a>참고 항목

- [C# 프로그래밍 가이드](../index.md)
- [네임스페이스 사용](using-namespaces.md)
- [My 네임스페이스를 사용하는 방법](how-to-use-the-my-namespace.md)
- [식별자 이름](../inside-a-program/identifier-names.md)
- [using 지시문](../../language-reference/keywords/using-directive.md)
- [:: 연산자](../../language-reference/operators/namespace-alias-qualifier.md)
