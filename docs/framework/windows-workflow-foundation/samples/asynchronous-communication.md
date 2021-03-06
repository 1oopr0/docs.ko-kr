---
title: Asynchronous Communication
ms.date: 03/30/2017
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
ms.openlocfilehash: e1bc63b5d3178b8e98350dedd8eb0791e0e35589
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142878"
---
# <a name="asynchronous-communication"></a>Asynchronous Communication
이 샘플에서는 WF(두 개의 서로 다른 WF) 서비스 간의 통신이 기본적으로 비동기적으로 수행되는 방법을 보여 줍니다.  
  
## <a name="demonstrates"></a>데모  
 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 서비스 간의 비동기 통신  
  
## <a name="discussion"></a>토론  
 이 샘플에서는 .NET Framework에서 제공되는 메시징 활동을 통해 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 애플리케이션 간의 통신이 비동기적으로 이루어지는 방식을 보여 줍니다.  
  
 이 샘플은 다음 세 개의 프로젝트로 구성되어 있습니다.  
  
 CreditCheckService  
 이 서비스는 특정 개인의 신용 점수나 승인할 품목의 가치를 받은 다음 해당 개인에게 신용을 부여할지 여부를 결정합니다.  
  
 RentalApprovalService  
 이 서비스는 신용 거래를 필요로 하는 개인으로부터 신청을 받습니다. 이 서비스는 `CreditCheckService`와 비동기적으로 통신하여 신용 거래 신청이 유효한지 여부를 결정합니다.  
  
 Client  
 클라이언트는 `RentalApprovalService`와 동기적으로 통신하여 신용 거래가 승인되었는지 여부를 확인합니다.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>샘플을 설치, 빌드 및 실행하려면  
  
1. **비동기통신** 솔루션을 마우스 오른쪽 단추로 클릭하고 **속성을**선택합니다.  
  
2. **공통 속성에서** **시작 프로젝트를**선택하고 여러 시작 **프로젝트를**선택합니다.  
  
3. **RentalApprovalService를** 목록의 첫 번째 위치로 이동한 다음 **CreditCheckService**다음에 **클라이언트가**표시됩니다. 세 프로젝트 모두에 **대해 시작** 작업을 설정합니다.  
  
4. **확인을**클릭하고 F5를 눌러 샘플을 실행합니다.  
  
> [!IMPORTANT]
> 컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다. 계속하기 전에 다음(기본) 디렉터리를 확인하세요.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> 이 디렉터리가 없는 경우 [.NET Framework 4에 대한 WCF(Windows 통신 재단) 및 WF(Windows 워크플로우 재단) 샘플로](https://www.microsoft.com/download/details.aspx?id=21459) 이동하여 모든 WCF(Windows 통신 재단) 및 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 샘플을 다운로드합니다. 이 샘플은 다음 디렉터리에 있습니다.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`
