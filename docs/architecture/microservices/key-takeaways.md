---
title: 핵심 내용
description: 컨테이너화된 .NET 애플리케이션용 .NET 마이크로 서비스 아키텍처 가이드/전자책에서 핵심 요점을 가져와 혜택 및 단점, 디자인 및 개발에 대한 DDD 패턴, 복원력, 보안, 오케스트레이터 사용 등 마이크로 서비스 아키텍처 사용 시 관련된 상위 수준 문제를 빠르게 살펴볼 수 있습니다.
ms.date: 10/19/2018
ms.openlocfilehash: 3b8b7be9b3903c64221cba7c6abdb1e38f5d944f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68674460"
---
# <a name="key-takeaways"></a>핵심 내용

다음은 요약 및 핵심 내용으로, 이 가이드에서 가장 중요한 결론입니다.

**컨테이너 사용 시 이점.** 컨테이너 기반 솔루션은 프로덕션 환경의 종속성 오류로 인한 배포 문제 완화에 도움이 되기 때문에 중요한 비용 절감 효과가 있습니다. 컨테이너는 DevOps 및 프로덕션 운영을 획기적으로 개선합니다.

**컨테이너를 아주 흔히 보게 될 것입니다.** Docker 기반 컨테이너는 Microsoft, Amazon AWS, Google, IBM 등 Windows 및 Linux 에코시스템의 주요 공급업체에서 지원하는 업계의 사실상 표준이 되고 있습니다. 조만간 클라우드 및 온-프레미스 데이터 센터에서 Docker를 아주 흔히 볼 수 있게 될 것입니다.

**배포 단위로 컨테이너.** Docker 컨테이너는 서버 기반 애플리케이션 또는 서비스 배포의 표준 단위가 되고 있습니다.

**마이크로 서비스.** 마이크로 서비스 아키텍처는 자율 서비스 형태의 여러 독립적인 하위 시스템을 기반으로 하는 분산된 대규모 또는 복잡한 중요 업무용 애플리케이션에 선호되는 접근 방식이 되고 있습니다. 마이크로 서비스 기반 아키텍처에서 애플리케이션은 독립적으로 개발, 테스트, 버전 관리, 배포 및 크기 조정될 수 있는 서비스 컬렉션으로 빌드됩니다. 각 서비스에 관련된 자율 데이터베이스가 포함될 수 있습니다.

**도메인 기반 디자인 및 SOA.** 마이크로 서비스 아키텍처 패턴은 SOA(서비스 지향 아키텍처) 및 DDD(도메인 기반 디자인)에서 파생됩니다. 진화하는 비즈니스 요구 및 규칙이 있는 환경을 위해 마이크로 서비스를 디자인하고 개발할 때 DDD 접근 방식과 패턴을 고려하는 것이 중요합니다.

**마이크로 서비스 당면 과제.** 마이크로 서비스는 독립 배포, 강력한 하위 시스템 경계, 기술 다양성과 같은 많은 강력한 기능을 제공합니다. 그러나 조각화된 독립형 데이터 모델, 마이크로 서비스 간 복원력 있는 통신, 궁극적인 일관성 및 여러 마이크로 서비스의 로깅 및 모니터링 정보 집계로 인한 운영상의 복잡성과 같은 분산된 애플리케이션 개발과 관련된 많은 새로운 문제 역시 발생합니다. 이러한 측면은 기존의 모놀리식 애플리케이션보다 높은 수준의 복잡성을 야기합니다. 따라서 특정 시나리오만 마이크로 서비스 기반 애플리케이션에 적합합니다. 여기에는 여러 개의 진화하는 하위 시스템이 있는 크고 복잡한 애플리케이션이 포함됩니다. 이러한 경우 장기적인 민첩성 및 애플리케이션 유지 관리성이 향상될 것이므로 더 복잡한 소프트웨어 아키텍처에 투자할 가치가 있습니다.

**모든 애플리케이션을 위한 컨테이너.** 컨테이너는 마이크로 서비스에 편리하지만, Windows 컨테이너를 사용할 때 기존 .NET Framework를 기반으로 하는 모놀리식 애플리케이션에도 유용할 수 있습니다. 많은 프로덕션 배포 문제를 해결하고 최첨단 개발 및 테스트 환경을 제공하는 등 Docker 사용 시의 혜택은 다양한 유형의 애플리케이션에 적용됩니다.

**CLI 및 IDE.** Microsoft 도구를 사용하면 원하는 방식으로 컨테이너화된 .NET 애플리케이션을 개발할 수 있습니다. Docker CLI 및 Visual Studio Code를 사용하여 CLI 및 편집기 기반 환경으로 개발할 수 있습니다. 또는 Visual Studio와 Docker의 고유 기능(예: 다중 컨테이너 디버깅)을 통해 IDE 중심의 접근 방식을 사용할 수 있습니다.

**복원력 있는 클라우드 애플리케이션.** 일반적으로 클라우드 기반 시스템 및 분산된 시스템에서는 항상 부분 오류 위험이 있습니다. 클라이언트와 서비스는 별도의 프로세스(컨테이너)이기 때문에 서비스가 클라이언트의 요청에 시기 적절하게 응답하지 못할 수 있습니다. 예를 들어 부분 오류 또는 유지 관리로 인해 서비스가 다운될 수 있습니다. 서비스가 오버로드되어 요청에 느리게 응답하거나 네트워크 문제로 인해 단기간에 액세스할 수 없는 경우가 있습니다. 따라서 클라우드 기반 애플리케이션은 이러한 오류를 받아들여 해당 오류에 대응할 전략을 마련해야 합니다. 이러한 전략에는 다시 시도 정책(메시지 다시 전송 또는 요청 다시 시도)과 반복적인 요청의 기하급수적인 로드를 피하기 위한 회로 차단기 패턴 구현이 포함될 수 있습니다. 기본적으로 클라우드 기반 애플리케이션에는 오케스트레이터 또는 서비스 버스에서 제공하는 상위 수준 메커니즘과 같이 클라우드 인프라를 기반으로 하거나 사용자 지정의 복원력 있는 메커니즘이 있어야 합니다.

**보안.** 현대의 컨테이너 및 마이크로 서비스 영역은 새로운 취약성에 노출될 수 있습니다. 인증 및 권한 부여를 기반으로 하여 기본 애플리케이션 보안을 구현하는 여러 가지 방법이 있습니다. 그러나 컨테이너 보안은 본질적으로 더 안전한 애플리케이션을 만드는 추가 핵심 구성 요소를 고려해야 합니다. 더 안전한 앱을 빌드하는 데 중요한 요소는 다른 앱 및 시스템과 통신할 수 있는 안전한 방법을 구현하는 것으로, 자격 증명, 토큰, 암호 등 일반적으로 애플리케이션 비밀이라고 하는 것을 요구하는 방법이 필요합니다. 모든 보안 솔루션은 전송 중 및 미사용 시 비밀 암호화, 최종 애플리케이션에서 사용 시 비밀 유출 방지와 같은 보안 모범 사례를 따라야 합니다. 이러한 비밀은 Azure Key Vault를 사용할 때와 같이 안전하게 저장 및 유지되어야 합니다.

**오케스트레이터.** Azure Kubernetes Service 및 Azure Service Fabric과 같은 컨테이너 기반 오케스트레이터는 모든 중요한 마이크로 서비스 및 컨테이너 기반 애플리케이션의 핵심 부분입니다. 이러한 애플리케이션은 높은 복잡성과 확장성 요구를 수반하며 지속적으로 진화합니다. 이 가이드에서는 오케스트레이터와 마이크로 서비스 기반 및 컨테이너 기반 솔루션에서 이들의 역할에 대해 소개했습니다. 애플리케이션 요구 사항으로 인해 복잡한 컨테이너화된 앱으로 전환하려는 경우, 오케스트레이터에 대해 자세히 알아볼 수 있는 추가 리소스를 찾아보는 것이 좋습니다.

>[!div class="step-by-step"]
>[이전](secure-net-microservices-web-applications/azure-key-vault-protects-secrets.md)