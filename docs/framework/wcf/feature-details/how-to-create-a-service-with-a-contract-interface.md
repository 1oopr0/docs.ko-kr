---
title: '방법: Contract 인터페이스를 사용하여 서비스 만들기'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7b6803f6-d6f9-4cc2-9f1b-6f4c920475d5
ms.openlocfilehash: c7d4bce174790b97db6b95aa5d15af455f261f82
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597165"
---
# <a name="how-to-create-a-service-with-a-contract-interface"></a>방법: Contract 인터페이스를 사용하여 서비스 만들기
WCF (Windows Communication Foundation) 계약을 만드는 기본 방법은 인터페이스를 사용 하는 것입니다. 이 계약은 서비스에서 제공하는 작업에 액세스하는 데 필요한 메시지 컬렉션과 구조를 지정합니다. 이 인터페이스는 <xref:System.ServiceModel.ServiceContractAttribute> 클래스를 인터페이스에 적용하고 <xref:System.ServiceModel.OperationContractAttribute> 클래스를 노출할 메서드에 적용하여 입력 및 출력 형식을 정의합니다.  
  
 서비스 계약에 대 한 자세한 내용은 [서비스 계약 디자인](../designing-service-contracts.md)을 참조 하세요.  
  
### <a name="creating-a-wcf-contract-with-an-interface"></a>인터페이스로 WCF 계약 만들기  
  
1. Visual Basic, c # 또는 기타 공용 언어 런타임 언어를 사용 하 여 새 인터페이스를 만듭니다.  
  
2. 인터페이스에 <xref:System.ServiceModel.ServiceContractAttribute> 클래스를 적용합니다.  
  
3. 인터페이스에 메서드를 정의합니다.  
  
4. <xref:System.ServiceModel.OperationContractAttribute>공용 WCF 계약의 일부로 노출 되어야 하는 각 메서드에 클래스를 적용 합니다.  
  
## <a name="example"></a>예제  
 다음 코드 예제에서는 서비스 계약을 정의하는 인터페이스를 보여 줍니다.  
  
 [!code-csharp[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithinterface/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithinterface/vb/source.vb#1)]  
  
 <xref:System.ServiceModel.OperationContractAttribute> 클래스가 적용된 메서드는 기본적으로 요청-회신 메시지 패턴을 사용합니다. 이 메시지 패턴에 대 한 자세한 내용은 [방법: 요청-회신 계약 만들기](how-to-create-a-request-reply-contract.md)를 참조 하세요. 특성의 속성을 설정하여 다른 메시지 패턴을 만들고 사용할 수도 있습니다. 더 많은 예제 [는 방법: 단방향 계약 만들기](how-to-create-a-one-way-contract.md) 및 [방법: 이중 계약 만들기](how-to-create-a-duplex-contract.md)를 참조 하세요.  
  
## <a name="see-also"></a>참고 항목

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
