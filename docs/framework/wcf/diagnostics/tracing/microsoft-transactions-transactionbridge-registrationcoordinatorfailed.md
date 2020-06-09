---
title: Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFailed
ms.date: 03/30/2017
ms.assetid: 96474056-0418-41e4-8c75-bbc0a853eaba
ms.openlocfilehash: faab1927f75a33b6a6950f8f4baf758e7418547a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599700"
---
# <a name="microsofttransactionstransactionbridgeregistrationcoordinatorfailed"></a><span data-ttu-id="6d537-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFailed</span><span class="sxs-lookup"><span data-stu-id="6d537-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFailed</span></span>
<span data-ttu-id="6d537-103">WS-AT 프로토콜 서비스가 코디네이터에게 Register 메시지를 보내지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="6d537-103">The WS-AT protocol service failed to send a Register message to its coordinator</span></span>  
  
## <a name="description"></a><span data-ttu-id="6d537-104">Description</span><span class="sxs-lookup"><span data-stu-id="6d537-104">Description</span></span>  
 <span data-ttu-id="6d537-105">로컬 TransactionManager가 메시지를 보낼 수 없기 때문에 상위 TransactionManager를 등록할 수 없는 경우 추적됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d537-105">Traced if the local TransactionManager is not able to Register with its superior TransactionManager due to the inability to send a message.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="6d537-106">문제 해결</span><span class="sxs-lookup"><span data-stu-id="6d537-106">Troubleshooting</span></span>  
 <span data-ttu-id="6d537-107">메시지 보내기 오류의 원인인 예외에 대한 추적 메시지를 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="6d537-107">Inspect the trace message for the exception causing the message send failure</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d537-108">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6d537-108">See also</span></span>

- [<span data-ttu-id="6d537-109">추적</span><span class="sxs-lookup"><span data-stu-id="6d537-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="6d537-110">추적을 사용하여 애플리케이션 문제 해결</span><span class="sxs-lookup"><span data-stu-id="6d537-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="6d537-111">관리 및 진단</span><span class="sxs-lookup"><span data-stu-id="6d537-111">Administration and Diagnostics</span></span>](../index.md)
