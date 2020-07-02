---
title: 애플리케이션 도메인에서 설치 정보 검색
description: System.AppDomain 클래스 또는 AppDomainSetup 개체를 사용하여 .NET의 애플리케이션 도메인에서 설치 정보를 검색합니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- AppDomainSetup object
- retrieving setup information
- application domains, retrieving setup information
ms.assetid: 5cdb12ae-1e37-4a62-8ec7-93d6dcc6e8d9
ms.openlocfilehash: 3b7fdd302ac11caa423815483a4add38264f0910
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325662"
---
# <a name="retrieve-setup-information-from-an-application-domain"></a>애플리케이션 도메인에서 설치 정보 검색

애플리케이션 도메인의 각 인스턴스는 두 속성과 <xref:System.AppDomainSetup> 정보로 구성됩니다. <xref:System.AppDomain?displayProperty=nameWithType> 클래스를 사용하여 애플리케이션 도메인에서 설치 정보를 검색할 수 있습니다. 이 클래스는 애플리케이션 도메인에 대한 구성 정보를 검색하는 여러 멤버를 제공합니다.  
  
 애플리케이션 도메인에 대한 **AppDomainSetup** 개체를 쿼리하여 만들 때 도메인에 전달된 설치 정보를 가져올 수도 있습니다.  
  
 다음 예제에서는 새 애플리케이션 도메인을 만들고 여러 멤버 값을 콘솔에 출력합니다.  
  
 [!code-cpp[AppDomain_Setup#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source2.cpp#2)]
 [!code-csharp[AppDomain_Setup#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source2.cs#2)]
 [!code-vb[AppDomain_Setup#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source2.vb#2)]  
  
 다음 예제에서는 애플리케이션 도메인에 대한 설치 정보를 설정한 후 검색합니다. `AppDomain.SetupInformation.ApplicationBase`는 구성 정보를 가져옵니다.  
  
 [!code-cpp[AppDomain_Setup#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source3.cpp#3)]
 [!code-csharp[AppDomain_Setup#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source3.cs#3)]
 [!code-vb[AppDomain_Setup#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source3.vb#3)]  
  
## <a name="see-also"></a>참조

- [애플리케이션 도메인으로 프로그래밍](application-domains.md#programming-with-application-domains)
- [애플리케이션 도메인 사용](use.md)
