---
title: 문자열이 숫자 값을 나타내는지 확인하는 방법 - C# 프로그래밍 가이드
ms.date: 07/20/2015
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
ms.openlocfilehash: 37437460ea4c6ca216f2844d63af3688ccc984c6
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241723"
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a>문자열이 숫자 값을 나타내는지 확인하는 방법(C# 프로그래밍 가이드)
문자열이 지정된 숫자 형식의 유효한 표현인지 확인하려면 모든 기본 숫자 형식 및 <xref:System.DateTime>, <xref:System.Net.IPAddress> 등의 형식에 의해서도 구현되는 정적 `TryParse` 메서드를 사용합니다. 다음 예제에서는 "108"이 유효한 [int](../../language-reference/builtin-types/integral-numeric-types.md)인지 확인하는 방법을 보여 줍니다.  
  
```csharp  
int i = 0;
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 문자열이 숫자가 아닌 문자를 포함하거나, 숫자 값이 지정한 특정 형식에 비해 너무 크거나 너무 작은 경우 `TryParse`는 false를 반환하고 out 매개 변수를 0으로 설정합니다. 그렇지 않으면 true를 반환하고 out 매개 변수를 문자열의 숫자 값으로 설정합니다.  
  
> [!NOTE]
> 문자열이 숫자만 포함해도 사용하는 `TryParse` 메서드의 형식에 유효하지 않을 수도 있습니다. 예를 들어 "256"은 `byte`에 유효한 값이 아니지만 `int`에는 유효합니다. "98.6"은 `int`에 유효한 값이 아니지만 유효한 `decimal`입니다.  
  
## <a name="example"></a>예제  
 다음 예제에서는`long`, `byte` 및 `decimal` 값의 문자열 표현과 함께 `TryParse`를 사용하는 방법을 보여 줍니다.  
  
 [!code-csharp[csProgGuideStrings#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#14)]  
  
## <a name="robust-programming"></a>강력한 프로그래밍  
 또한 기본 숫자 형식은 문자열이 유효한 숫자가 아닌 경우 예외를 throw하는 `Parse` 정적 메서드를 구현합니다. 일반적으로 숫자가 유효하지 않은 경우 단순히 false를 반환하는 `TryParse`가 더 효율적입니다.  
  
## <a name="net-security"></a>.NET 보안  
 항상 `TryParse` 또는 `Parse` 메서드를 사용하여 텍스트 상자, 콤보 상자 등의 컨트롤에서 들어오는 사용자 입력의 유효성을 검사합니다.  
  
## <a name="see-also"></a>참조

- [바이트 배열을 int로 변환하는 방법](../types/how-to-convert-a-byte-array-to-an-int.md)
- [문자열을 숫자로 변환하는 방법](../types/how-to-convert-a-string-to-a-number.md)
- [16진수 문자열과 숫자 형식 간에 변환하는 방법](../types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)
- [숫자 문자열 구문 분석](../../../standard/base-types/parsing-numeric.md)
- [형식 서식 지정](../../../standard/base-types/formatting-types.md)
