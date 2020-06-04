---
title: 속성 또는 메서드 호출에 인수 또는 반환 값으로서 private 개체에 대한 참조를 포함할 수 없습니다.
ms.date: 07/20/2015
f1_keywords:
- vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
ms.openlocfilehash: 36c71cdb345d0fdc0da2b58865a1f11956bcb944
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409974"
---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a>속성 또는 메서드 호출에 인수 또는 반환 값으로서 private 개체에 대한 참조를 포함할 수 없습니다.

이 오류의 가능한 원인:  
  
- 클라이언트가 Out of Process 구성 요소의 속성 또는 메서드를 호출했으며 private 개체에 대한 참조를 인수 중 하나로 전달하려고 했습니다.  
  
- Out of Process 구성 요소가 해당 클라이언트에 대해 콜백 메서드를 호출했으며 private 개체에 대한 참조를 전달하려고 했습니다.  
  
- Out of Process 구성 요소가 private 개체에 대한 참조를 발생 이벤트의 인수로 전달하려고 했습니다.  
  
- 클라이언트가 처리 중인 이벤트의 `ByRef` 인수에 private 개체 참조를 할당하려고 했습니다.  
  
## <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
1. 참조를 제거합니다.  
  
## <a name="see-also"></a>참고 항목

- [프라이빗](../modifiers/private.md)
