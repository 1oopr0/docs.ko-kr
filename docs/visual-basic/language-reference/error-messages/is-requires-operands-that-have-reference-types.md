---
title: "'Is'의 피연산자는 참조 형식이어야 하는데 이 피연산자의 값 형식은 '<typename>'입니다."
ms.date: 07/20/2015
f1_keywords:
- bc30020
- vbc30020
helpviewer_keywords:
- BC30020
ms.assetid: 228afebd-1203-4bd3-8d7a-c5c56f3cedc4
ms.openlocfilehash: 5c9f156272cd0c3cbaeadbc0e162129f41619cc6
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163352"
---
# <a name="bc30020-is-requires-operands-that-have-reference-types-but-this-operand-has-the-value-type-typename"></a>BC30020: ' i s '에는 참조 형식이 있는 피연산자가 필요 하지만이 피연산자의 값 형식은 ' '입니다. \<typename>

`Is`비교 연산자는 두 개체 변수가 같은 인스턴스를 참조 하는지 여부를 확인 합니다. 이 비교는 값 형식에 대해 정의 되지 않습니다.

 **오류 ID:** BC30020

## <a name="to-correct-this-error"></a>이 오류를 해결하려면

- 적절 한 산술 비교 연산자 또는 연산자를 사용 `Like` 하 여 두 개의 값 형식을 비교 합니다.

## <a name="see-also"></a>참고 항목

- [Is 연산자](../operators/is-operator.md)
- [Like 연산자](../operators/like-operator.md)
- [비교 연산자](../operators/comparison-operators.md)
