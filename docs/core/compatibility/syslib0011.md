---
title: SYSLIB0011 경고
description: 컴파일 시간 경고 SYSLIB0011을 생성하는 사용되지 않음에 대해 알아봅니다.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 1b4f4c24c64148319f659b78573a4d80fd5b98a7
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440017"
---
# <a name="syslib0011-binaryformatter-serialization-is-obsolete"></a>SYSLIB0011: BinaryFormatter serialization이 사용되지 않음

<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>의 [보안 취약성](../../standard/serialization/binaryformatter-security-guide.md#binaryformatter-security-vulnerabilities)으로 인해 다음 API는 .NET 5.0부터 사용되지 않는 것으로 표시됩니다. 코드에서 이러한 API를 사용하면 컴파일 시간에 `SYSLIB0011` 경고가 생성됩니다.

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>

## <a name="workarounds"></a>해결 방법

<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 대신 <xref:System.Text.Json.JsonSerializer>나 <xref:System.Xml.Serialization.XmlSerializer>를 사용하는 것이 좋습니다.

권장 작업에 대한 자세한 내용은 [BinaryFormatter 사용 중지 및 비활성화 오류 해결](https://aka.ms/binaryformatter)을 참조하세요.

[!INCLUDE [suppress-syslib-warning](../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a>추가 정보

- [BinaryFormatter 사용되지 않음 및 비활성화 오류 해결](https://aka.ms/binaryformatter)
- [ASP.NET 앱에서 BinaryFormatter serialization 메서드가 사용되지 않고 금지됨](corefx.md#binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps)
