---
description: C#에서 add 키워드를 사용하여 사용자 지정 이벤트 접근자를 만드는 방법 알아보기
title: add - C# 참조
ms.date: 07/20/2015
f1_keywords:
- add_CSharpKeyword
helpviewer_keywords:
- add event accessor [C#]
ms.assetid: faf30b99-10e8-45cd-ab9a-57585d4d1d8d
ms.openlocfilehash: 9daf635206ff9727a4bf333c123f68be812723cd
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91168766"
---
# <a name="add-c-reference"></a>add(C# 참조)

`add` 상황별 키워드는 클라이언트 코드가 [event](./event.md)를 구독할 때 호출되는 사용자 지정 이벤트 접근자를 정의하는 데 사용됩니다. 사용자 지정 `add` 접근자를 제공하는 경우 [remove](./remove.md) 접근자도 제공해야 합니다.  
  
## <a name="example"></a>예제  

다음 예제에서는 사용자 지정 `add` 및 [remove](./remove.md) 접근자가 있는 이벤트를 보여 줍니다. 전체 예제를 보려면 [인터페이스 이벤트를 구현하는 방법](../../programming-guide/events/how-to-implement-interface-events.md)을 참조하세요.
  
[!code-csharp[csrefKeywordsContextual#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#15)]
  
 일반적으로 고유한 사용자 지정 이벤트 접근자를 제공할 필요가 없습니다. 이벤트를 선언할 때 컴파일러에서 자동으로 생성되는 접근자만으로도 대부분의 시나리오에 충분합니다.  
  
## <a name="see-also"></a>참조

- [이벤트](../../programming-guide/events/index.md)
