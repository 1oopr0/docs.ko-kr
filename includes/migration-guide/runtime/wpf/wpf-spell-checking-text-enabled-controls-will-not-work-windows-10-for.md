---
ms.openlocfilehash: 1d2e4a058008676c6ea85becebd4bb9220569ef3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621362"
---
### <a name="wpf-spell-checking-in-text-enabled-controls-will-not-work-in-windows-10-for-languages-not-in-the-oss-input-language-list"></a>텍스트 지원 컨트롤의 WPF 맞춤법 검사는 Windows 10에서 OS의 입력된 언어 목록에 없는 언어에 대해서는 작동하지 않습니다.

#### <a name="details"></a>세부 정보

Windows 10에서 실행하는 경우 플랫폼 맞춤법 검사 기능은 입력된 언어 목록에 있는 언어에 대해서만 사용할 수 있으므로 맞춤법 검사기가 WPF 텍스트 지원 컨트롤에서 작동하지 않을 수 있습니다. Windows 10에서 사용 가능한 키보드 목록에 언어가 추가되면 Windows는 맞춤법 검사 기능을 제공하는 해당 FOD(Feature on Demand) 패키지를 자동으로 다운로드하여 설치합니다. 입력 언어 목록에 언어를 추가하면 맞춤법 검사기가 지원됩니다.

#### <a name="suggestion"></a>제안 해결 방법

Windows 10에서 맞춤법 검사가 작동하려면 맞춤법을 검사할 언어 또는 텍스트를 입력 언어로 추가해야 합니다.

| 이름    | 값       |
|:--------|:------------|
| Scope   |Microsoft Edge|
|버전|4.6|
|형식|런타임|
