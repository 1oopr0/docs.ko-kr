---
ms.openlocfilehash: 4a65e721e5639f12445a9a44f46baa0d26898a88
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615672"
---
### <a name="il-ret-not-allowed-in-a-try-region"></a>IL ret은 try 영역에서 허용되지 않음

#### <a name="details"></a>세부 정보

JIT64 Just-In-Time 컴파일러와 달리 RyuJIT(.NET Framework 4.6에서 사용됨)는 try 영역에서 IL ret 명령을 허용하지 않습니다. try 영역에서 반환은 ECMA-335 사양에서 허용되지 않으며 이러한 IL을 생성하는 알려진 관리 컴파일러는 없습니다. 그러나 이러한 IL이 리플렉션 내보내기를 사용하여 생성된 경우에는 JIT64 컴파일러에서 실행됩니다.

#### <a name="suggestion"></a>제안 해결 방법

앱이 try 영역에 ret opcode가 포함된 IL을 생성하는 경우 앱은 .NET Framework 4.5를 대상으로 이전 JIT를 사용하고 이 중단을 피할 수 있습니다. 또는 생성된 IL이 try 영역 이후로 돌아가도록 업데이트될 수 있습니다.

| 이름    | 값       |
|:--------|:------------|
| Scope   | Microsoft Edge        |
| 버전 | 4.6         |
| 형식    | 대상 변경 |
