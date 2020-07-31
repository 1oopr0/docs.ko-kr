---
title: '완화: 포인터 기반 터치 및 스타일러스 지원'
description: .NET Framework 4.7을 대상으로 하는 WPF 앱에 대한 선택적 WPF 터치/스타일러스 스택을 사용하도록 설정하는 효과에 대해 알아봅니다.
ms.date: 04/07/2017
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
ms.openlocfilehash: d0c0effeaa727c615dddc3b92cdd34aafde65705
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475426"
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a>완화: 포인터 기반 터치 및 스타일러스 지원

.NET Framework 4.7을 대상으로 하고 Windows 10 크리에이터 업데이트 버전 이상의 Windows에서 실행되는 WPF 애플리케이션은 선택적 `WM_POINTER` 기반 WPF 터치/스타일러스 스택을 사용하도록 설정할 수 있습니다.

## <a name="impact"></a>영향

포인터 기반 터치/스타일러스 지원을 명시적으로 사용하지 않도록 하는 개발자는 WPF 터치/스타일러스 동작이 달라지지 않는 것을 알 수 있습니다.

다음은 현재 선택적 `WM_POINTER` 기반 터치/스타일러스 스택의 알려진 문제입니다.

- 실시간 잉크 기능을 지원하지 않습니다.

   잉크 입력 및 스타일러스 플러그 인은 계속 작동하지만 UI 스레드에서 처리되므로 성능이 저하될 수 있습니다.

- 터치/스타일러스 이벤트에서 마우스 이벤트로 전환하는 방식의 변경으로 인해 동작이 변경됩니다.

  - 조작이 다르게 동작할 수 있습니다.

  - 끌어서 놓기 작업이 터치 입력에 대해 적절한 피드백을 표시하지 않습니다. (이러한 문제가 스타일러스 입력에는 영향을 주지 않습니다.)

  - 끌어서 놓기가 더 이상 터치/스타일러스 이벤트에서 시작될 수 없습니다.

      이로 인해 마우스 입력이 감지될 때까지 애플리케이션이 응답하지 않을 수 있습니다. 대신, 개발자는 마우스 이벤트에서 끌어서 놓기를 시작하는 것이 좋습니다.

## <a name="opting-in-to-wm_pointer-based-touchstylus-support"></a>WM_POINTER 기반 터치/스타일러스 지원 옵트인(opt in)

이 스택을 사용하도록 설정하려는 개발자는 애플리케이션의 ‘app.config’ 파일에 다음을 추가할 수 있습니다.

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

이 항목을 제거하거나 해당 값을 `false`로 설정하면 이 선택적 스택이 해제됩니다.

## <a name="see-also"></a>참조

- [애플리케이션 호환성](application-compatibility.md)
