---
title: '방법: 이중 계약 만들기'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 500a75b6-998a-47d5-8e3b-24e3aba2a434
ms.openlocfilehash: e5b6c7eecce08a23490b6ab1991e4561d9462469
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598985"
---
# <a name="how-to-create-a-duplex-contract"></a><span data-ttu-id="438c0-102">방법: 이중 계약 만들기</span><span class="sxs-lookup"><span data-stu-id="438c0-102">How to: Create a Duplex Contract</span></span>
<span data-ttu-id="438c0-103">이 항목에서는 이중(양방향) 계약을 사용하는 메서드를 만드는 기본 단계를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="438c0-103">This topic shows the basic steps to create methods that use a duplex (two-way) contract.</span></span> <span data-ttu-id="438c0-104">이중 계약을 사용하면 클라이언트와 서버가 각각 독립적으로 통신하므로 서로 호출을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="438c0-104">A duplex contract allows clients and servers to communicate with each other independently so that either can initiate calls to the other.</span></span> <span data-ttu-id="438c0-105">이중 계약은 WCF (Windows Communication Foundation) 서비스에서 사용할 수 있는 세 가지 메시지 패턴 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="438c0-105">The duplex contract is one of three message patterns available to Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="438c0-106">다른 두 메시지 패턴은 단방향 및 요청-회신입니다.</span><span class="sxs-lookup"><span data-stu-id="438c0-106">The other two message patterns are one-way and request-reply.</span></span> <span data-ttu-id="438c0-107">이중 계약은 클라이언트와 서버 간 두 개의 단방향 계약으로 구성되며, 메서드 호출을 상호 관련시키지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="438c0-107">A duplex contract consists of two one-way contracts between the client and the server and does not require that the method calls be correlated.</span></span> <span data-ttu-id="438c0-108">서비스가 클라이언트에 세부 정보를 쿼리하거나 클라이언트에서 이벤트를 명시적으로 발생시킬 때 이러한 종류의 계약을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="438c0-108">Use this kind of contract when your service must query the client for more information or explicitly raise events on the client.</span></span> <span data-ttu-id="438c0-109">이중 계약에 대 한 클라이언트 응용 프로그램을 만드는 방법에 대 한 자세한 내용은 [방법: 이중 계약을 사용 하 여 서비스 액세스](how-to-access-services-with-a-duplex-contract.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="438c0-109">For more information about creating a client application for a duplex contract, see [How to: Access Services with a Duplex Contract](how-to-access-services-with-a-duplex-contract.md).</span></span> <span data-ttu-id="438c0-110">작업 샘플은 [이중](../samples/duplex.md) 샘플을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="438c0-110">For a working sample, see the [Duplex](../samples/duplex.md) sample.</span></span>  
  
### <a name="to-create-a-duplex-contract"></a><span data-ttu-id="438c0-111">이중 계약을 만들려면</span><span class="sxs-lookup"><span data-stu-id="438c0-111">To create a duplex contract</span></span>  
  
1. <span data-ttu-id="438c0-112">이중 계약의 서버 측을 구성하는 인터페이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="438c0-112">Create the interface that makes up the server side of the duplex contract.</span></span>  
  
2. <span data-ttu-id="438c0-113">인터페이스에 <xref:System.ServiceModel.ServiceContractAttribute> 클래스를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="438c0-113">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface.</span></span>  
  
     [!code-csharp[S_WS_DualHttp#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#3)]
     [!code-vb[S_WS_DualHttp#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#3)]  
  
3. <span data-ttu-id="438c0-114">인터페이스에 메서드 서명을 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="438c0-114">Declare the method signatures in the interface.</span></span>  
  
4. <span data-ttu-id="438c0-115">공용 계약의 일부여야 하는 각 메서드 서명에 <xref:System.ServiceModel.OperationContractAttribute> 클래스를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="438c0-115">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method signature that must be part of the public contract.</span></span>  
  
5. <span data-ttu-id="438c0-116">서비스가 클라이언트에서 호출할 수 있는 작업 집합을 정의하는 콜백 인터페이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="438c0-116">Create the callback interface that defines the set of operations that the service can invoke on the client.</span></span>  
  
     [!code-csharp[S_WS_DualHttp#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#4)]
     [!code-vb[S_WS_DualHttp#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#4)]  
  
6. <span data-ttu-id="438c0-117">콜백 인터페이스에 메서드 서명을 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="438c0-117">Declare the method signatures in the callback interface.</span></span>  
  
7. <span data-ttu-id="438c0-118">공용 계약의 일부여야 하는 각 메서드 서명에 <xref:System.ServiceModel.OperationContractAttribute> 클래스를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="438c0-118">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method signature that must be part of the public contract.</span></span>  
  
8. <span data-ttu-id="438c0-119">기본 인터페이스의 <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> 속성을 콜백 인터페이스의 형식으로 설정하여 이중 계약에 두 개의 인터페이스를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="438c0-119">Link the two interfaces into a duplex contract by setting the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> property in the primary interface to the type of the callback interface.</span></span>  
  
### <a name="to-call-methods-on-the-client"></a><span data-ttu-id="438c0-120">클라이언트에서 메서드를 호출하려면</span><span class="sxs-lookup"><span data-stu-id="438c0-120">To call methods on the client</span></span>  
  
1. <span data-ttu-id="438c0-121">기본 계약의 서비스 구현에서 콜백 인터페이스에 대한 변수를 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="438c0-121">In the service's implementation of the primary contract, declare a variable for the callback interface.</span></span>  
  
2. <span data-ttu-id="438c0-122">변수를 <xref:System.ServiceModel.OperationContext.GetCallbackChannel%2A> 클래스의 <xref:System.ServiceModel.OperationContext> 메서드에서 반환한 개체 참조로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="438c0-122">Set the variable to the object reference returned by the <xref:System.ServiceModel.OperationContext.GetCallbackChannel%2A> method of the <xref:System.ServiceModel.OperationContext> class.</span></span>  
  
     [!code-csharp[S_WS_DualHttp#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#1)]
     [!code-vb[S_WS_DualHttp#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#1)]  
  
     [!code-csharp[S_WS_DualHttp#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#2)]
     [!code-vb[S_WS_DualHttp#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#2)]  
  
3. <span data-ttu-id="438c0-123">콜백 인터페이스에서 정의한 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="438c0-123">Call the methods defined by the callback interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="438c0-124">예제</span><span class="sxs-lookup"><span data-stu-id="438c0-124">Example</span></span>  
 <span data-ttu-id="438c0-125">다음 코드 예제에서는 이중 통신을 수행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="438c0-125">The following code example demonstrates duplex communication.</span></span> <span data-ttu-id="438c0-126">서비스의 계약에는 앞뒤로 이동하기 위한 서비스 작업이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="438c0-126">The service’s contract contains service operations for moving forward and backward.</span></span> <span data-ttu-id="438c0-127">클라이언트의 계약에는 해당 위치를 보고하는 서비스 작업이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="438c0-127">The client’s contract contains a service operation for reporting its position.</span></span>  
  
 [!code-csharp[S_WS_DualHttp#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#5)]
 [!code-vb[S_WS_DualHttp#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#5)]  
  
- <span data-ttu-id="438c0-128"><xref:System.ServiceModel.ServiceContractAttribute> 및 <xref:System.ServiceModel.OperationContractAttribute> 특성을 적용하면 WSDL(웹 서비스 기술 언어)에서 서비스 계약 정의를 자동으로 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="438c0-128">Applying the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes allows the automatic generation of service contract definitions in the Web Services Description Language (WSDL).</span></span>  
  
- <span data-ttu-id="438c0-129">[ServiceModel Metadata 유틸리티 도구 (svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) 를 사용 하 여 WSDL 문서를 검색 하 고 (선택 사항) 클라이언트에 대 한 코드 및 구성을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="438c0-129">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to retrieve the WSDL document and (optional) code and configuration for a client.</span></span>  
  
- <span data-ttu-id="438c0-130">이중 서비스를 노출하는 엔드포인트를 보호해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="438c0-130">Endpoints exposing duplex services must be secured.</span></span> <span data-ttu-id="438c0-131">서비스가 이중 메시지를 받으면 들어오는 해당 메시지에서 ReplyTo를 확인하여 회신을 보낼 위치를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="438c0-131">When a service receives a duplex message, it looks at the ReplyTo in that incoming message to determine where to send the reply.</span></span> <span data-ttu-id="438c0-132">채널이 보안되지 않으면 신뢰할 수 없는 클라이언트가 대상 컴퓨터의 ReplyTo를 사용하여 악의적인 메시지를 보낼 수 있으므로 해당 대상 컴퓨터의 서비스 거부가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="438c0-132">If the channel is not secured, then an untrusted client could send a malicious message with a target machine's ReplyTo, leading to a denial of service of the target machine.</span></span> <span data-ttu-id="438c0-133">정규 요청-회신 메시지를 사용하는 경우에는 ReplyTo가 무시되고 원래 메시지가 들어온 채널에서 응답이 보내지므로 이러한 문제가 생기지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="438c0-133">With regular request-reply messages, this is not an issue, because the ReplyTo is ignored and the response is sent on the channel the original message came in on.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="438c0-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="438c0-134">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [<span data-ttu-id="438c0-135">방법: 이중 계약을 사용하여 서비스 액세스</span><span class="sxs-lookup"><span data-stu-id="438c0-135">How to: Access Services with a Duplex Contract</span></span>](how-to-access-services-with-a-duplex-contract.md)
- [<span data-ttu-id="438c0-136">이중</span><span class="sxs-lookup"><span data-stu-id="438c0-136">Duplex</span></span>](../samples/duplex.md)
- [<span data-ttu-id="438c0-137">서비스 디자인 및 구현</span><span class="sxs-lookup"><span data-stu-id="438c0-137">Designing and Implementing Services</span></span>](../designing-and-implementing-services.md)
- [<span data-ttu-id="438c0-138">방법: 서비스 계약 정의</span><span class="sxs-lookup"><span data-stu-id="438c0-138">How to: Define a Service Contract</span></span>](../how-to-define-a-wcf-service-contract.md)
- [<span data-ttu-id="438c0-139">세션</span><span class="sxs-lookup"><span data-stu-id="438c0-139">Session</span></span>](../samples/session.md)
