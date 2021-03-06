---
title: 서버리스 기능 활용
description: 클라우드 네이티브 응용 프로그램에서 서버 리스 및 Azure Functions 활용
ms.date: 05/13/2020
ms.openlocfilehash: 8e5c60d29cd8d635f79f42c232b33f060949e2b5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155369"
---
# <a name="leveraging-serverless-functions"></a>서버리스 기능 활용

클라우드 기능을 활용 하기 위해 물리적 컴퓨터를 관리 하는 스펙트럼에서 서버를 사용 하지 않는 것은 매우 끝에 있습니다. 사용자의 유일한 책임은 코드를 실행 하는 경우에만 요금을 지불 하면 됩니다. Azure Functions는 클라우드 네이티브 응용 프로그램에 서버 리스 기능을 빌드하는 방법을 제공 합니다.

## <a name="what-is-serverless"></a>서버를 사용하지 않음은 무엇입니까?

서버를 사용 하지 않는 서비스는 클라우드 컴퓨팅의 비교적 새로운 서비스 모델입니다. 서버를 선택 하는 것은 아닙니다. 코드는 서버에서 계속 실행 됩니다. 응용 프로그램 팀은 더 이상 서버 인프라를 관리할 필요가 없다는 것을 구분 합니다. 대신, 클라우드 공급 업체는 이러한 업무를 담당 합니다. 개발 팀은 고객이 아니라 고객에 게 비즈니스 솔루션을 제공 하 여 생산성을 향상 시킵니다.

서버를 사용 하지 않는 컴퓨팅은 이벤트를 트리거한 상태 비저장 컨테이너를 사용 하 여 서비스를 호스팅합니다. 필요에 따라 수요를 충족 하도록 확장할 수 있습니다. Azure Functions와 같은 서버를 사용 하지 않는 플랫폼은 큐, 이벤트 및 저장소와 같은 다른 Azure 서비스와 긴밀 하 게 통합 됩니다.

## <a name="what-challenges-are-solved-by-serverless"></a>서버 리스에서 해결 되는 문제는 무엇 인가요?

서버를 사용 하지 않는 플랫폼은 시간이 많이 걸리고 비용이 많이 드는 문제를 해결 합니다.

- 컴퓨터 및 소프트웨어 라이선스 구매
- 컴퓨터와 네트워킹, 전원 및 A/C 요구 사항 하우징, 보안, 구성 및 유지 관리
- 운영 체제 및 소프트웨어 패치 및 업그레이드
- 응용 프로그램 소프트웨어를 호스팅하도록 웹 서버 또는 컴퓨터 서비스 구성
- 플랫폼 내에서 응용 프로그램 소프트웨어 구성

많은 회사에서 하드웨어 인프라 문제를 지원 하기 위해 다량의 예산을 할당 합니다. 클라우드로 전환 하면 이러한 비용을 줄일 수 있습니다. 응용 프로그램을 서버 리스로 이동 하면 제거 하는 데 도움이 될 수 있습니다.

## <a name="what-is-the-difference-between-a-microservice-and-a-serverless-function"></a>마이크로 서비스와 서버 리스 함수 간의 차이점은 무엇 인가요?

일반적으로 마이크로 서비스는 온라인 전자 상거래 사이트의 쇼핑 카트와 같은 비즈니스 기능을 캡슐화 합니다. 사용자가 쇼핑 환경을 관리할 수 있는 여러 작업을 노출 합니다. 그러나 함수는 이벤트에 대 한 응답으로 단일 용도의 작업을 실행 하는 작은 경량 코드 블록입니다.
일반적으로 마이크로 서비스는 일반적으로 인터페이스에서 요청에 응답 하도록 구성 됩니다. 요청은 HTTP Rest 또는 gRPC 기반 일 수 있습니다. 서버를 사용 하지 않는 서비스에서 이벤트에 응답 합니다. 이벤트 기반 아키텍처는 단기 실행 백그라운드 작업을 처리 하는 데 적합 합니다.

## <a name="what-scenarios-are-appropriate-for-serverless"></a>서버 리스에 적합 한 시나리오는 무엇입니까?

서버를 사용 하지 않는 경우 트리거에 대 한 응답으로 호출 되는 개별 단기 실행 함수를 노출 합니다. 이렇게 하면 백그라운드 작업을 처리 하는 데 적합 합니다.

응용 프로그램에서 워크플로의 단계로 전자 메일을 보내야 할 수 있습니다. 마이크로 서비스 요청의 일부로 알림을 보내는 대신 메시지 세부 정보를 큐에 저장 합니다. Azure 함수는 메시지를 큐에서 제거 하 고 비동기적으로 전자 메일을 보낼 수 있습니다. 이렇게 하면 마이크로 서비스의 성능 및 확장성을 향상 시킬 수 있습니다. 전자 메일 전송과 관련 된 병목 현상을 방지 하기 위해 [큐 기반 부하 평준화](/azure/architecture/patterns/queue-based-load-leveling) 를 구현할 수 있습니다. 또한이 독립 실행형 서비스는 여러 응용 프로그램에서 유틸리티로 재사용할 수 있습니다.

큐 및 항목 으로부터의 비동기 메시징은 서버 리스 함수를 트리거하는 일반적인 패턴입니다. 그러나 Azure Functions Azure Blob Storage 변경 같은 다른 이벤트에 의해 트리거될 수 있습니다. 이미지 업로드를 지 원하는 서비스에는 이미지 크기 최적화를 담당 하는 Azure 함수가 있을 수 있습니다. 함수는 Azure Blob Storage에 삽입 하 여 직접 트리거되어 마이크로 서비스 작업에서 복잡성을 유지할 수 있습니다.

많은 서비스에는 워크플로의 일부로 장기 실행 프로세스가 있습니다. 이러한 작업은 사용자가 응용 프로그램과 상호 작용 하는 과정의 일부로 수행 되는 경우가 많습니다. 이러한 작업을 통해 사용자는 자신의 환경에 부정적인 영향을 미칠 수 있습니다. 서버를 사용 하지 않는 컴퓨팅은 사용자 상호 작용 루프 외부에서 느린 작업을 이동할 수 있는 좋은 방법을 제공 합니다. 이러한 작업은 전체 응용 프로그램을 확장할 필요 없이 필요에 따라 확장할 수 있습니다.

## <a name="when-should-you-avoid-serverless"></a>서버를 사용 하지 않는 경우는 언제 인가요?

서버를 사용 하지 않는 솔루션은 주문형으로 프로 비전 하 고 확장 합니다. 새 인스턴스가 호출 될 때 콜드 시작은 일반적인 문제입니다. 콜드 시작은이 인스턴스를 프로 비전 하는 데 걸리는 시간입니다. 일반적으로이 지연은 몇 초 정도 걸릴 수 있지만 다양 한 요인에 따라 더 길어질 수 있습니다. 프로 비전 되 면 단일 인스턴스는 정기적으로 요청을 수신 하는 동안 활성 상태로 유지 됩니다. 그러나 서비스를 덜 자주 호출 하는 경우 Azure는 메모리에서이를 제거 하 고 다시 호출 될 때 콜드 시작이 필요할 수 있습니다. 콜드 시작은 함수를 새 인스턴스로 확장 하는 경우에도 필요 합니다.

그림 3-10에서는 콜드 시작 패턴을 보여 줍니다. 앱이 콜드 인 경우 추가 단계를 수행 해야 합니다.

![콜드 및 웜 시작 ](./media/cold-start-warm-start.png)
 **그림 3-10**. 콜드 시작과 웜 시작 비교

콜드 시작을 완전히 방지 하려면 [소비 계획에서 전용 요금제로](https://azure.microsoft.com/blog/understanding-serverless-cold-start/)전환할 수 있습니다. 프리미엄 계획 업그레이드를 사용 하 여 하나 이상의 [사전 준비 인스턴스](/azure/azure-functions/functions-premium-plan#pre-warmed-instances) 를 구성할 수도 있습니다. 이러한 경우 다른 인스턴스를 추가 해야 하는 경우 이미 실행 되 고 있습니다. 이러한 옵션은 서버를 사용 하지 않는 컴퓨팅과 관련 된 콜드 시작 문제를 완화 하는 데 도움이 됩니다.

클라우드 공급자는 계산 실행 시간 및 사용 된 메모리에 따라 서버 리스 서버를 청구 합니다. 장기 실행 작업 또는 높은 메모리 사용 워크 로드가 항상 서버를 사용 하기에 적합 한 것은 아닙니다. 서버를 사용 하지 않는 함수는 신속 하 게 완료할 수 있는 작은 작업 청크를 선호 합니다. 서버를 사용 하지 않는 대부분의 플랫폼에서는 몇 분 내에 개별 함수를 완료 해야 합니다. 기본값은 5 분의 시간 제한 기간으로, 최대 10 분으로 구성할 수 있습니다. Azure Functions Azure Functions 프리미엄 요금제를 사용 하면이 문제를 완화할 수 있으며, 구성할 수 있는 제한 없는 제한이 있는 30 분으로 기본 제한 시간을 설정할 수 있습니다. 계산 시간은 달력 시간이 아닙니다. [Azure Durable Functions 프레임 워크](/azure/azure-functions/durable/durable-functions-overview?tabs=csharp) 를 사용 하는 고급 함수는 며칠 동안 실행을 일시 중지할 수 있습니다. 요금은 실제 실행 시간을 기반으로 하며, 함수가 절전 모드를 해제 하 고 처리를 다시 시작 합니다.

마지막으로 응용 프로그램 작업에 대 한 Azure Functions 활용 하면 복잡성이 증가 합니다. 먼저 모듈화 된 느슨하게 연결 된 디자인을 사용 하 여 응용 프로그램을 설계 합니다. 그런 다음 서버를 사용 하지 않는 혜택이 추가 복잡성을 정당화 하는지 확인 합니다.

>[!div class="step-by-step"]
>[이전](leverage-containers-orchestrators.md)
>[다음](combine-containers-serverless-approaches.md)
