---
title: 선언이 필요합니다.
ms.date: 07/20/2015
f1_keywords:
- vbc30188
- bc30188
helpviewer_keywords:
- BC30188
ms.assetid: da6b1df3-fe6b-4415-88e6-0977e5189e0b
ms.openlocfilehash: 2755f5afcb96ca7a6c4d140908649390dd66d571
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162702"
---
# <a name="bc30188-declaration-expected"></a>BC30188: 선언이 필요 합니다.

대입 또는 loop 문과 같은 비 선언적 문은 프로시저 외부에서 발생 합니다. 프로시저 외부에는 선언만 사용할 수 있습니다.

 또는와 같은 선언 키워드 없이 프로그래밍 요소가 선언 되었습니다 `Dim` `Const` .

 **오류 ID:** BC30188

## <a name="to-correct-this-error"></a>이 오류를 해결하려면

- 비 선언적 문을 프로시저 본문으로 이동 합니다.

- 적절 한 선언 키워드를 사용 하 여 선언을 시작 합니다.

- 선언 키워드의 철자가 잘못 되었는지 확인 합니다.

## <a name="see-also"></a>참고 항목

- [절차](../../programming-guide/language-features/procedures/index.md)
- [Dim 문](../statements/dim-statement.md)
