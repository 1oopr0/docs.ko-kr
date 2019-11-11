---
title: 클라우드 네이티브 애플리케이션 소개
description: 클라우드 기본 컴퓨팅에 대해 알아보기
author: robvet
ms.date: 08/26/2019
ms.openlocfilehash: 1d3679c7f1ab940d7ab3e194c200483b63276883
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73841770"
---
# <a name="introduction-to-cloud-native-applications"></a>클라우드 네이티브 애플리케이션 소개

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

다른 날에는 "다음으로 큰 문제"에 대해 작업 하 고 있습니다.

휴대폰 링입니다. 새 작업에 대해 하루에 두 번 호출 하는 채용 담당자입니다.

그러나 이번에는 시작, 자본 및 많은 자금 등이 다릅니다.

클라우드 및 최첨단 기술을 언급 하면에 지가 표시 됩니다.

몇 주 후에는 이제 디자인 세션에서 주요 전자 상거래 응용 프로그램을 설계 하는 새 직원이 될 것입니다. 다른 선두 전자 상거래 사이트를 완료 하려고 합니다.

빌드하는 방법

지난 15 년 동안의 지침을 따르는 경우 그림 1.1에 표시 된 시스템을 빌드할 가능성이 가장 높습니다.

![기존 모놀리식 디자인](./media/monolithic-design.png)

**그림 1-1**. 기존 모놀리식 디자인

모든 도메인 논리를 포함 하는 매우 중요 한 응용 프로그램을 구성 합니다. 여기에는 Id, 카탈로그, 순서 지정 등의 모듈이 포함 됩니다. 핵심 앱은 많은 관계형 데이터베이스와 통신 합니다. 핵심은 HTML 인터페이스를 통해 기능을 노출 합니다.

지금까지  방금 모놀리식 응용 프로그램을 만들었습니다.

모두 잘못 된 것은 아닙니다. 거은 몇 가지 이점을 제공 합니다. 예를 들어, 다음은 간단 합니다.

- 빌드
- 테스트
- 배치할
- 문제점
- 소수 자릿수

오늘 존재 하는 많은 성공한 앱이 거로 생성 되었습니다. 앱이 적중 되며 계속 해 서 진화 하 고 반복 후 반복 해 서 더 많은 기능을 추가 합니다.

그러나 어느 시점에서 불편을 느낄 것입니다. 응용 프로그램에 대 한 제어 권한을 잃게 됩니다. 시간이 지남에 따라 느낌이 점점 더 유용 하 게 표시 되 고, 그에 따라 **걱정 주기**라는 상태를 입력 합니다.

- 응용 프로그램은 한 사람이 이해 하지 대다수 복잡해 집니다.
- 변경 해야 하는 경우-각 변경에 의도 하지 않으며 비용이 많이 드는 부작용이 있습니다.
- 새로운 기능/픽스는 복잡 하 고 시간이 많이 걸리고 구현 비용이 많이 듭니다.
- 각 릴리스는 전체 응용 프로그램을 완전히 배포 해야 할 수 있습니다.
- 불안정 한 구성 요소 하나는 전체 시스템의 작동이 중단 될 수 있습니다.
- 새 기술 및 프레임 워크는 옵션이 아닙니다.
- Agile 배달 방법론은 구현 하기 어렵습니다.
- 아키텍처 erosion은의를 코드 베이스 deteriorates로 설정 합니다. "특별 한 사례"는 그렇지 않습니다.
- 컨설턴트는 다시 작성 하는 것을 알려줍니다.

대부분의 조직에서는 시스템을 구축 하는 클라우드 기본 방법을 채택 하 여 모놀리식 우려 주기를 해결 했습니다. 그림 1-2은 클라우드 기본 기술 및 사례를 적용 하는 동일한 시스템을 보여 줍니다.

![클라우드 네이티브 디자인](./media/cloud-native-design.png)

**그림 1-2**. 클라우드 네이티브 디자인

응용 프로그램을 여러 개의 격리 된 소규모 마이크로 서비스 집합으로 분해 하는 방법을 확인 합니다. 각 서비스는 자체 포함 되며 자체 코드, 데이터 및 종속성을 캡슐화 합니다. 각는 소프트웨어 컨테이너에 배포 되 고 컨테이너 orchestrator에서 관리 됩니다. 각 서비스는 대량 관계형 데이터베이스 대신 데이터 요구 사항에 따라 다양 한 데이터 저장소를 소유 합니다. 일부 서비스가 관계형 데이터베이스에 종속 되는 방법에 대해 설명 하 고 NoSQL 데이터베이스에서 다른 서비스를 확인 합니다. 한 서비스는 분산 캐시에 상태를 저장 합니다. 모든 트래픽이 핵심 백엔드 서비스에 대 한 트래픽을 라우팅하는 역할을 담당 하는 API Gateway 서비스를 통해 경로를 결정 하 고 많은 교차 절삭 문제를 적용 하는 방법을 확인 합니다. 가장 중요 한 점은 응용 프로그램은 최신 클라우드 플랫폼에서 제공 하는 확장성 및 복원 력 기능을 완전히 활용 하는 것입니다.

### <a name="cloud-native-computing"></a>클라우드 네이티브 컴퓨팅

흠 ... "*클라우드 네이티브*" 라는 용어를 사용 했습니다. 처음에는 "무엇을 의미 하나요?" 라고 생각할 수 있습니다. 소프트웨어 공급 업체의 다른 업계 throw concocted

다행히이 책은 매우 다르며,이 책은 사용자의 권유를 도와줍니다.

짧은 시간 내에 클라우드 기본은 소프트웨어 업계에서 주행 추세를 얻게 됩니다. 최신 소프트웨어 개발 사례, 기술 및 클라우드 인프라를 최대한 활용 하는 방법인 크고 복잡 한 시스템을 구축 하는 것에 대해 생각 하는 새로운 방법입니다. 이 방법은 시스템을 디자인, 구현, 배포 및 운영 하는 방식을 변경 합니다.

업계를 구동 하는 지속적인 믿으세요와 달리 클라우드 기본은 "*실제*"입니다. 300이 넘는 주요 회사의 컨소시엄 인 cncf ( [Cloud Native 컴퓨팅 Foundation](https://www.cncf.io/) )를 사용 하 여 기술 및 클라우드 스택에서 클라우드 기본 컴퓨팅을 수행할 수 있도록 하는 기본 사항입니다. 가장 영향력 있는 오픈 소스 그룹 중 하나인 GitHub에서 가장 빠르게 성장 하는 오픈 소스 프로젝트를 많이 호스팅합니다. [Kubernetes](https://kubernetes.io/), [프로메테우스](https://prometheus.io/), [투구](https://helm.sh/), [엔보이](https://www.envoyproxy.io/)및 [grpc](https://grpc.io/)와 같은 프로젝트를 포함 합니다.

CNCF 발전시키는 오픈 소스 및 공급 업체 중립성의 에코 시스템을 제공 합니다. 그 후에는 클라우드 기본 원칙, 패턴 및 기술에 독립적인 모범 사례를 제공 합니다. 동시에 클라우드 네이티브 시스템을 구성 하기 위해 Microsoft Azure 클라우드에서 제공 되는 서비스 및 인프라에 대해 설명 합니다.

그렇다면 정확히 클라우드 기본 이란 무엇 인가요? 이 새로운 세계를 탐색 하는 데 도움을 주세요.

>[!div class="step-by-step"]
>[이전](index.md)
>[다음](definition.md)