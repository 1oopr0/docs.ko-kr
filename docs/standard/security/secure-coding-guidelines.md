---
title: .NET에 대 한 보안 코딩 지침
description: 사용할 코드를 디자인 합니다. 악의적인 코드가 데이터에 액세스 하거나 다른 작업을 수행 하지 못하도록 하는 데 도움이 되는 순 적용 권한 및 기타 적용.
ms.date: 07/15/2020
helpviewer_keywords:
- managed wrapper to native code implementation
- secure coding
- reusable components
- library code that exposes protected resources
- code, security
- code security
- secure coding, options
- components [.NET], security
- code security, options
- security-neutral code
- security [.NET], coding guidelines
ms.assetid: 4f882d94-262b-4494-b0a6-ba9ba1f5f177
ms.openlocfilehash: a05e0cec2814be88ac835d05601d5cf5f66383c3
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555958"
---
# <a name="secure-coding-guidelines"></a>보안 코딩 지침

대부분의 응용 프로그램 코드는 .NET에서 구현 된 인프라를 간단히 사용할 수 있습니다. 경우에 따라, 보안 시스템을 확장하거나 새로운 임시 메서드를 사용하여 빌드되는 추가적인 애플리케이션 관련 보안이 필요합니다.

.NET에서 적용 한 권한 및 기타 적용을 코드에 사용 하 여 악의적인 코드가 원치 않는 다른 작업을 수행 하지 않으려는 정보에 액세스 하는 것을 방지 하기 위해 장벽을 방어 해야 합니다. 또한 신뢰할 수 있는 코드를 사용하여 예상되는 모든 시나리오에서 보안과 유용성 간의 균형을 맞춰야 합니다.

이 개요에서는 보안 시스템에서 사용하기 위해 코드를 설계하는 여러 가지 방법에 대해 설명합니다.

## <a name="securing-resource-access"></a>리소스 액세스 보안

코드를 설계하고 작성하는 경우, 특히 출처를 알 수 없는 코드를 사용하거나 호출하는 경우 코드에 부여된 리소스 액세스 권한을 보호하고 제한해야 합니다. 따라서 코드의 보안을 유지하도록 다음과 같은 기술을 염두에 둡니다.

- CAS(코드 액세스 보안) 사용 안 함

- 부분적으로 신뢰할 수 있는 코드 사용 안 함

- [AllowPartiallyTrustedCaller](xref:System.Security.AllowPartiallyTrustedCallersAttribute) 특성 (APTCA)을 사용 하지 마십시오.

- .NET Remoting 사용 안 함

- DCOM(분산 구성 요소 개체 모델) 사용 안 함

- 이진 포맷터 사용 안 함

코드 액세스 보안 및 보안 투명 코드는 부분적으로 신뢰할 수 있는 코드의 보안 경계로 지원 되지 않습니다. 대체 보안 조치를 적용하지 않고 출처를 알 수 없는 코드를 로드 및 실행하지 않는 것이 좋습니다. 대체 보안 조치는 다음과 같습니다.

- 가상화

- AppContainers

- OS(운영 체제) 사용자 및 사용 권한

- Hyper-V 컨테이너

## <a name="security-neutral-code"></a>보안 중립 코드

보안 중립 코드는 보안 시스템에서 명시적인 작업을 수행하는 것이 없습니다. 단순히 코드에 부여되는 권한을 실행합니다. 보호 된 작업 (예: 파일, 네트워킹 등)과 관련 된 보안 예외를 catch 하지 못하는 응용 프로그램은 처리 되지 않은 예외를 발생 시킬 수 있지만, 보안 중립 코드는 여전히 .NET의 보안 기술을 활용 합니다.

보안 중립 라이브러리에는 사용자가 파악해야 하는 특징이 있습니다. 라이브러리가 파일을 사용 하거나 비관리 코드를 호출 하는 API 요소를 제공 한다고 가정 합니다. 코드에 해당 권한이 없으면 설명 된 대로 실행 되지 않습니다. 하지만 코드에 권한이 있더라도 이 코드를 호출하는 모든 애플리케이션이 작동하려면 동일한 권한이 있어야 합니다. 호출 코드에 올바른 권한이 없으면 <xref:System.Security.SecurityException> 코드 액세스 보안 스택 워크의 결과로이 표시 됩니다.

## <a name="application-code-that-isnt-a-reusable-component"></a>재사용 가능한 구성 요소가 아닌 응용 프로그램 코드

코드가 다른 코드에서 호출 되지 않는 응용 프로그램의 일부인 경우 보안은 단순 하며 특수 코딩이 필요 하지 않을 수 있습니다. 하지만 악성 코드는 해당 코드를 호출할 수 있습니다. 코드 액세스 보안으로 악성 코드가 리소스에 액세스하는 것을 방지할 수 있지만, 이러한 코드는 중요한 정보가 들어 있을 수 있는 필드 또는 속성의 값을 판독할 수 있습니다.

또한 해당 코드가 인터넷 또는 기타 신뢰할 수 없는 소스로부터의 사용자 입력을 허용하는 경우에는 악의적인 입력에 주의해야 합니다.

## <a name="managed-wrapper-to-native-code-implementation"></a>네이티브 코드 구현에 대 한 관리 되는 래퍼

일반적으로 이 시나리오에서는 네이티브 코드에서 관리 코드에 사용 가능하게 하려는 몇 가지 유용한 기능을 구현합니다. 관리되는 래퍼는 플랫폼 호출 또는 COM interop를 사용하여 쉽게 작성할 수 있습니다. 하지만 이 작업을 성공적으로 수행하려면 래퍼 호출자에게 비관리 코드 권한이 있어야 합니다. 기본 정책에서이는 인트라넷 또는 인터넷에서 다운로드 된 코드가 래퍼와 작동 하지 않음을 의미 합니다.

이러한 래퍼를 사용 하는 모든 응용 프로그램에 비관리 코드 권한을 부여 하는 대신, 래퍼 코드에만 이러한 권한을 부여 하는 것이 좋습니다. 기본 기능이 리소스를 노출하지 않으며 구현도 안전할 경우에는, 래퍼는 모든 코드가 이를 통해 호출할 수 있도록 해당 권한을 어셜션하기만 하면 됩니다. 리소스가 포함되어 있으면, 보안 코딩은 다음 섹션에 설명된 라이브러리 코드의 경우와 동일해야 합니다. 래퍼는 호출자를 이러한 리소스에 노출할 가능성이 있기 때문에, 네이티브 코드가 안전한지 신중하게 확인해야 하며 이는 래퍼의 책임입니다.

## <a name="library-code-that-exposes-protected-resources"></a>보호 된 리소스를 노출 하는 라이브러리 코드

다음 접근 방식은 보안 코딩을 위해 가장 강력 하 고 위험할 수 있는 (잘못 된 경우)입니다. 즉, 라이브러리는 .NET 클래스에서 사용 하는 리소스에 대 한 사용 권한을 적용 하는 것 처럼 다른 방법으로는 사용할 수 없는 특정 리소스에 액세스 하기 위해 다른 코드의 인터페이스 역할을 수행 합니다. 리소스를 노출할 경우, 먼저 코드는 리소스에 적절한 권한을 요구해야 합니다(즉, 보안 검사를 수행해야 함). 그런 다음 실제 작업을 수행할 수 있도록 해당 권한을 어설션합니다.

## <a name="see-also"></a>참고 항목

- [상태 데이터 보안](securing-state-data.md)
- [보안 및 사용자 입력](security-and-user-input.md)
- [보안 및 경합 상태](security-and-race-conditions.md)
- [보안 및 빠른 코드 생성](security-and-on-the-fly-code-generation.md)
- [역할 기반 보안](role-based-security.md)
- [ASP.NET Core 보안](/aspnet/core/security/)
