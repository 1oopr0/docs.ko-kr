---
title: Mac용 Visual Studio를 사용하여 .NET Core 콘솔 애플리케이션 디버그
description: Mac용 Visual Studio를 사용하여 .NET Core 콘솔 앱을 디버그하는 방법을 알아봅니다.
ms.date: 06/08/2020
ms.openlocfilehash: 011647a6e3e676909880befa3b770205eb9616d6
ms.sourcegitcommit: 60dc0a11ebdd77f969f41891d5cca06335cda6a7
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88957527"
---
# <a name="tutorial-debug-a-net-core-console-application-using-visual-studio-for-mac"></a>자습서: Mac용 Visual Studio를 사용하여 .NET Core 콘솔 애플리케이션 디버그

이 자습서에서는 Mac용 Visual Studio에서 사용할 수 있는 디버깅 도구를 소개합니다.

## <a name="prerequisites"></a>사전 요구 사항

- 이 자습서는 [Mac용 Visual Studio를 사용하여 .NET Core 콘솔 애플리케이션 만들기](with-visual-studio-mac.md)에서 만든 콘솔 앱을 사용합니다.

## <a name="use-debug-build-configuration"></a>디버그 빌드 구성 사용

디버그 및 릴리스는 Visual Studio의 기본 빌드 구성입니다. 디버그 빌드 구성은 디버깅에 사용하고, 릴리스 구성은 최종 릴리스 배포에 사용합니다.

디버그 구성에서 프로그램은 완전히 기호화된 디버그 정보를 사용하여 컴파일되며 최적화되지 않습니다. 최적화하면 소스 코드와 생성된 명령 간의 관계가 복잡해지므로 디버깅이 복잡해집니다. 프로그램의 릴리스 구성은 완전히 최적화되고, 기호화된 디버그 정보를 포함하지 않습니다.

기본적으로 Mac용 Visual Studio는 디버그 빌드 구성을 사용하므로 디버그하기 전에 변경할 필요가 없습니다.

1. Mac용 Visual Studio를 시작합니다.

1. [Mac용 Visual Studio를 사용하여 .NET Core 콘솔 애플리케이션 만들기](with-visual-studio-mac.md)에서 만든 프로젝트를 엽니다.

   현재 빌드 구성은 도구 모음에 표시됩니다. 다음 도구 모음 그림은 Visual Studio가 앱의 디버그 버전을 컴파일하도록 구성되어 있음을 보여줍니다.

   :::image type="content" source="media/debugging-with-visual-studio-mac/visual-studio-toolbar-debug.png" alt-text="디버그가 강조 표시된 Visual Studio 도구 모음":::

## <a name="set-a-breakpoint"></a>중단점 설정

중단점은 중단점이 설정된 줄이 실행되기 전에 애플리케이션 실행을 일시적으로 중단합니다.

1. 이름, 날짜, 시간을 표시하는 줄에 중단점을 설정합니다. 이렇게 하려면 코드 줄에 커서를 올려 놓고 <kbd>⌘</kbd><kbd>\\</kbd>(<kbd>command</kbd>+<kbd>\\</kbd>)를 누릅니다. 메뉴에서 **실행** > **중단점 설정/해제**를 선택해도 중단점을 설정할 수 있습니다.

   Visual Studio는 중단점이 설정된 줄을 강조 표시하고 왼쪽 여백에 빨간 점을 표시합니다.

   :::image type="content" source="media/debugging-with-visual-studio-mac/set-breakpoint-in-editor.png" alt-text="중단점이 설정된 Visual Studio 프로그램 창":::

1. <kbd>⌘</kbd><kbd>↵</kbd>(<kbd>command</kbd>+<kbd>enter</kbd>)를 눌러 디버깅 모드에서 프로그램을 시작합니다. 메뉴에서 **실행** > **디버깅 시작**을 선택해도 디버깅을 시작할 수 있습니다.

1. 프로그램 이름을 입력하라는 메시지가 표시되면 터미널 창에 문자열을 입력하고 <kbd>Enter</kbd> 키를 누릅니다.

1. 중단점에 도달할 때와 `Console.WriteLine` 메서드가 실행되기 전에 프로그램 실행이 중지됩니다.

   :::image type="content" source="media/debugging-with-visual-studio-mac/breakpoint-hit.png" alt-text="Visual Studio의 중단점 스크린샷":::

## <a name="use-the-immediate-window"></a>즉시 실행 창 사용

**직접 실행 창**에서는 디버그하는 애플리케이션을 조작할 수 있습니다. 대화형으로 변수 값을 변경하여 프로그램에 미치는 영향을 확인할 수 있습니다.

1. **직접 실행 창**이 표시되지 않는 경우 **보기** > **디버그 패드** > **직접 실행**을 선택하여 표시합니다.

1. **직접 실행 창**에 `name = "Gracie"`를 입력하고 <kbd>Enter</kbd> 키를 누릅니다.

1. **직접 실행 창**에 `date = date.AddDays(1)`를 입력하고 <kbd>Enter</kbd> 키를 누릅니다.

   **직접 실행 창**에는 문자열 변수의 새로운 값과 <xref:System.DateTime> 값의 속성이 표시됩니다.

   :::image type="content" source="media/debugging-with-visual-studio-mac/immediate-window.png" alt-text="Visual Studio의 직접 실행 창":::

   **지역** 창에는 현재 실행 중인 메서드에 정의된 변수 값이 표시됩니다. 방금 변경한 변수 값이 **로컬** 창에서 업데이트됩니다.

   :::image type="content" source="media/debugging-with-visual-studio-mac/locals-window.png" alt-text="Visual Studio의 로컬 창":::

1. <kbd>⌘</kbd><kbd>↵</kbd>(<kbd>command</kbd>+<kbd>enter</kbd>)를 눌러 디버깅을 계속합니다.

   터미널에 표시되는 값은 **직접 실행 창**에서 변경한 값과 일치합니다.

   터미널이 표시되지 않을 경우 하단의 탐색 막대에서 **Terminal - HelloWorld**를 선택합니다.

   :::image type="content" source="media/debugging-with-visual-studio-mac/terminal-hello-world.png" alt-text="하단 탐색 막대의 Terminal - Hello World":::

1. 아무 키나 눌러 프로그램을 종료합니다.

1. 터미널 창을 닫습니다.

## <a name="set-a-conditional-breakpoint"></a>조건부 중단점 설정

프로그램은 사용자가 입력하는 문자열을 표시합니다. 사용자가 아무 값도 입력하지 않으면 어떻게 되나요? *조건부 중단점*이라는 유용한 디버깅 기능을 사용하여 이를 테스트할 수 있습니다.

1. <kbd>ctrl</kbd> 키를 누른 상태에서 중단점을 나타내는 빨간색 점을 클릭합니다. 상황에 맞는 메뉴에서 **중단점 편집**을 선택합니다.

1. **중단점 편집** 대화 상자에서 **그리고 다음 조건이 true임** 아래에 있는 필드에 다음과 같은 코드를 입력한 후 **적용**을 선택합니다.

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   :::image type="content" source="media/debugging-with-visual-studio-mac/breakpoint-settings.png" alt-text="중단점 설정 패널을 보여 주는 편집기":::

   디버거는 중단점이 적중될 때마다 `String.IsNullOrEmpty(name)` 메서드를 호출하고, 메서드 호출이 `true`를 반환하는 경우에만 이 줄에서 중단합니다.

   조건식 대신 문이 지정된 횟수만큼 실행되기 전에 프로그램 실행을 중단하는 적중 횟수를 지정할 수 있습니다.

1. <kbd>⌘</kbd><kbd>↵</kbd>(<kbd>command</kbd>+<kbd>enter</kbd>)를 눌러 디버깅을 시작합니다.

1. 이름을 입력하라는 메시지가 나타나면 터미널 창에서 <kbd>Enter</kbd> 키를 누릅니다.

   `name`이 `null` 또는 <xref:System.String.Empty?displayProperty=nameWithType>이라는 지정한 조건이 충족되었으므로 중단점에 도달하면 프로그램 실행이 중지됩니다.

1. **지역** 창을 선택합니다. 이 창에는 현재 실행 중인 메서드에 로컬인 변수 값이 표시됩니다. 이 경우 `Main`은 현재 실행 중인 메서드입니다. `name` 변수의 값은 `""`, 즉 <xref:System.String.Empty?displayProperty=nameWithType>입니다.

1. **직접 실행 창**에 `name` 변수 이름을 입력하고 <kbd>Enter</kbd> 키를 눌러 값이 빈 문자열인지 확인할 수도 있습니다.

   :::image type="content" source="media/debugging-with-visual-studio-mac/immediate-window-output.png" alt-text="이름이 빈 문자열임을 보여주는 직접 실행 창":::

1. <kbd>⌘</kbd><kbd>↵</kbd>(<kbd>command</kbd>+<kbd>enter</kbd>)를 눌러 디버깅을 계속합니다.

1. 터미널 창에서 아무 키나 눌러서 프로그램을 종료합니다.

1. 터미널 창을 닫습니다.

1. 코드 창 왼쪽 여백에 있는 빨간 점을 클릭하여 중단점을 지웁니다. 중단점을 지우는 또 다른 방법은 코드 줄이 선택되어 있는 동안 **실행 > 중단점 설정/해제**를 선택하는 것입니다.

## <a name="step-through-a-program"></a>단계별 프로그램 실행

Visual Studio에서 프로그램을 한 줄씩 단계별로 실행하고 해당 실행을 모니터링할 수도 있습니다. 일반적으로 중단점을 설정하고 프로그램 코드 일부의 프로그램 흐름을 따라가면서 확인할 수 있습니다. 이 프로그램은 작으므로 전체 프로그램을 단계별로 실행할 수 있습니다.

1. `Main` 메서드의 시작을 표시하는 중괄호에서 중단점을 설정합니다(<kbd>command</kbd>+<kbd>\\</kbd> 누르기).

1. <kbd>⌘</kbd><kbd>↵</kbd>(<kbd>command</kbd>+<kbd>enter</kbd>)를 눌러 디버깅을 시작합니다.

   Visual Studio는 중단점이 있는 줄에서 중지됩니다.

1. <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd>(<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>)를 누르거나 **실행** > **한 단계씩 코드 실행**을 선택하여 한 줄씩 진행합니다.

   Visual Studio에서 다음에 실행될 줄을 강조 표시하고 옆에 화살표를 표시합니다.

   :::image type="content" source="media/debugging-with-visual-studio-mac/step-into-method.png" alt-text="Visual Studio 한 단계씩 코드 실행 메서드":::

   이 시점에서 **지역** 창에는 `args` 배열이 비어 있다고 표시되고, `name` 및 `date`에는 기본값이 있습니다. 또한 Visual Studio에서는 빈 터미널이 열려 있습니다.

1. <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd>(<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>)를 누릅니다.

   Visual Studio는 `name` 변수 할당을 포함하는 문을 강조 표시합니다. **로컬** 창에서는 `name`이 `null`로 표시되고 터미널에서는 문자열 "What is your name?"이 표시됩니다.

1. 콘솔 창에 문자열을 입력하고 <kbd>Enter</kbd> 키를 눌러 프롬프트에 응답합니다.

1. <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd>(<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>)를 누릅니다.

   Visual Studio는 `date` 변수 할당을 포함하는 문을 강조 표시합니다. **지역** 창에는 <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> 메서드 호출에 의해 반환된 값이 표시됩니다. 터미널에는 프롬프트에 입력한 문자열이 표시됩니다.

1. <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd>(<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>)를 누릅니다.

   **지역** 창에는 <xref:System.DateTime.Now?displayProperty=nameWithType> 속성에 따라 할당된 이후의 `date` 변수 값이 표시됩니다. 터미널은 변경되지 않습니다.

1. <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd>(<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>)를 누릅니다.

   Visual Studio에서 <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> 메서드를 호출합니다. 터미널에는 서식이 지정된 문자열이 표시됩니다.

1. <kbd>⇧</kbd><kbd>⌘</kbd><kbd>U</kbd>(<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>U</kbd>)를 누르거나 **실행** > **프로시저 나가기**를 선택합니다.

   터미널은 메시지를 표시하고 사용자가 키를 누르기를 기다립니다.

1. 아무 키나 눌러 프로그램을 종료합니다.

## <a name="use-release-build-configuration"></a>릴리스 빌드 구성 사용

애플리케이션의 디버그 버전을 테스트한 후에는 릴리스 버전을 컴파일하고 테스트해야 합니다. 릴리스 버전에는 애플리케이션의 동작에 부정적인 영향을 줄 수 있는 컴파일러 최적화가 통합됩니다. 예를 들어 성능 향상을 위해 설계된 컴파일러 최적화는 다중 스레드 애플리케이션에서 경합 상태를 만들 수 있습니다.

콘솔 애플리케이션의 릴리스 버전을 빌드하고 테스트하려면 다음 단계를 수행합니다.

1. 도구 모음의 빌드 구성을 **디버그**에서 **릴리스**로 변경합니다.

   :::image type="content" source="media/debugging-with-visual-studio-mac/visual-studio-toolbar-release.png" alt-text="디버그가 강조 표시된 기본 Visual Studio 도구 모음":::

1. <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd>+<kbd>command</kbd>+<kbd>enter</kbd>)를 눌러 디버그 없이 실행합니다.

## <a name="next-steps"></a>다음 단계

이 자습서에서는 Visual Studio 디버깅 도구를 사용했습니다. 다음 자습서에서는 앱의 배포 가능 버전을 게시합니다.

> [!div class="nextstepaction"]
> [Mac용 Visual Studio를 사용하여 .NET Core 콘솔 애플리케이션 게시](publishing-with-visual-studio-mac.md)
