---
title: "'<expression>'은(는) 형식 제약 조건으로 사용할 수 없습니다."
ms.date: 07/20/2015
f1_keywords:
- bc32061
- vbc32061
helpviewer_keywords:
- BC32061
ms.assetid: b17821b7-fa14-4397-a211-6e2a14079f09
ms.openlocfilehash: 4f1db6bdbe6f25d0362b55acd95e716fbc2417ed
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874274"
---
# <a name="expression-cannot-be-used-as-a-type-constraint"></a>'\<expression>'은(는) 형식 제약 조건으로 사용할 수 없습니다.

제약 조건 목록에 형식 매개 변수에 대한 유효한 제약 조건을 나타내지 않는 식이 포함되어 있습니다.  
  
 제약 조건 목록은 형식 매개 변수에 전달되는 형식 인수에 대해 요구 사항을 적용합니다. 다음 요구 사항을 임의로 조합해서 지정할 수 있습니다.  
  
- 형식 인수는 하나 이상의 인터페이스를 구현해야 합니다.  
  
- 형식 인수는 최대 하나의 클래스에서 상속해야 합니다.  
  
- 형식 인수는 만드는 코드가 액세스할 수 있는, 매개 변수 없는 생성자를 노출해야 합니다( `New` 제약 조건 포함).  
  
 제약 조건 목록에 특정 클래스 또는 인터페이스가 없는 경우 다음 중 하나를 지정하여 더 많은 일반 요구 사항을 적용할 수 있습니다.  
  
- 형식 인수는 값 형식이어야 합니다( `Structure` 제약 조건 포함).  
  
- 형식 인수는 참조 형식이어야 합니다( `Class` 제약 조건 포함).  
  
 동일한 형식 매개 변수에 `Structure` 와 `Class` 를 둘 다 지정할 수 없으며 두 번 이상 지정할 수도 없습니다.  
  
 **오류 ID:** BC32061  
  
## <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 식과 해당 요소의 철자가 맞는지 확인합니다.  
  
- 식이 앞의 요구 사항 목록에 맞지 않을 경우 제약 조건 목록에서 제거합니다.  
  
- 식이 인터페이스 또는 클래스를 참조하는 경우 컴파일러가 해당 인터페이스 또는 클래스에 액세스할 수 있는지 확인합니다. 해당 이름을 한정하거나 프로젝트에 대한 참조를 추가해야 할 수도 있습니다. 자세한 내용은 [선언 된 요소에](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)대 한 참조에서 "프로젝트에 대 한 참조"를 참조 하세요.  
  
## <a name="see-also"></a>참조

- [Visual Basic의 제네릭 형식](../../programming-guide/language-features/data-types/generic-types.md)
- [Value Types and Reference Types](../../programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
