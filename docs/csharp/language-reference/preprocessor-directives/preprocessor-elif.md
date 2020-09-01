---
description: '#elif - C# 참조'
title: '#elif - C# 참조'
ms.date: 07/20/2015
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
ms.openlocfilehash: 3aa9082b392b352091b9fde74a85f9dd155ad7b1
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89132289"
---
# <a name="elif-c-reference"></a>#elif(C# 참조)
`#elif`를 사용하면 복합 조건부 지시문을 만들 수 있습니다. `#elif` 식이 계산되는 경우는 [#if](./preprocessor-if.md)와 앞의 선택적 `#elif` 지시문 식이 모두 `true`로 계산되지 않는 경우입니다. `#elif` 식이 `true`이면 컴파일러는 `#elif`와 다음 조건부 지시문 사이에 있는 모든 코드를 평가합니다. 예:  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.WriteLine("Debug build");  
#elif VC7  
    Console.WriteLine("Visual Studio 7");  
#endif  
```  
  
 `==`(같음), `!=`(같지 않음), `&&`(AND), `||`(OR) 연산자를 사용하여 여러 기호를 평가할 수 있습니다. 기호와 연산자를 괄호로 묶을 수도 있습니다.  
  
## <a name="remarks"></a>설명  
 `#elif`는 다음 코드를 사용하는 것과 같습니다.  
  
```csharp
#else  
#if  
```  
  
 `#elif`를 사용하는 것이 더 간단합니다. 각 `#if`에는 [#endif](./preprocessor-endif.md)가 필요한 반면, `#elif`는 짝이 되는 `#endif` 없이 사용할 수 있기 때문입니다.  
  
 `#elif`를 사용하는 방법에 대한 예제는 [#if](./preprocessor-if.md)를 참조하세요.  
  
## <a name="see-also"></a>참고 항목

- [C# 참조](../index.md)
- [C# 프로그래밍 가이드](../../programming-guide/index.md)
- [C# 전처리기 지시문](./index.md)
