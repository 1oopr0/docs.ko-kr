---
title: 포인터 변환 - C# 프로그래밍 가이드
description: 포인터 변환에 대해 알아봅니다. 암시적 및 명시적 포인터 변환 표, 코드 예제 및 사용 가능한 추가 리소스를 확인합니다.
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: c39be5cb52964abbea5bc5636c6fa74d8411a331
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87382089"
---
# <a name="pointer-conversions-c-programming-guide"></a>포인터 변환(C# 프로그래밍 가이드)
다음 표에서는 미리 정의된 암시적 포인터 변환을 보여 줍니다. 암시적 변환은 메서드 호출, 할당 문을 비롯한 대부분의 경우에서 발생할 수 있습니다.  
  
## <a name="implicit-pointer-conversions"></a>암시적 포인터 변환  
  
|시작|대상|  
|----------|--------|  
|임의의 포인터 형식|void*|  
|null|임의의 포인터 형식|  
  
 명시적 포인터 변환은 캐스트 식을 통해 암시적 변환이 없는 변환을 수행하는 데 사용됩니다. 다음 표에는 이러한 변환이 나와 있습니다.  
  
## <a name="explicit-pointer-conversions"></a>명시적 포인터 변환  
  
|시작|대상|  
|----------|--------|  
|임의의 포인터 형식|다른 포인터 형식|  
|sbyte, byte, short, ushort, int, uint, long 또는 ulong|임의의 포인터 형식|  
|임의의 포인터 형식|sbyte, byte, short, ushort, int, uint, long 또는 ulong|  
  
## <a name="example"></a>예제  
 다음 예제에서 `int`에 대한 포인터는 `byte`에 대한 포인터로 변환됩니다. 포인터는 변수의 최하위 주소 지정 바이트를 가리킵니다. `int` 크기(4바이트)까지 결과를 연속적으로 증가할 경우 변수의 나머지 바이트를 표시할 수 있습니다.  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a>참고 항목

- [C# 프로그래밍 가이드](../index.md)
- [포인터 형식](pointer-types.md)
- [참조 형식](../../language-reference/keywords/reference-types.md)
- [값 형식](../../language-reference/builtin-types/value-types.md)
- [unsafe](../../language-reference/keywords/unsafe.md)
- [fixed 문](../../language-reference/keywords/fixed-statement.md)
- [stackalloc](../../language-reference/operators/stackalloc.md)
