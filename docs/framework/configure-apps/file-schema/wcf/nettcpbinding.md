---
title: <netTcpBinding>
description: TCP를 사용 하는 WCF 시스템 간 통신에만 사용 되는 안전 하 고 신뢰할 수 있으며 최적화 된 바인딩을 나타냅니다. 안정적인 메시징은 기본적으로 해제 되어 있습니다.
ms.date: 03/30/2017
helpviewer_keywords:
- netTcpBinding Element
ms.assetid: 5c5104a7-8754-4335-8233-46a45322503e
ms.openlocfilehash: a366b26d87c8796822e4fbbb2001823c116f2629
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556130"
---
# \<netTcpBinding>

<span data-ttu-id="68a8c-103">시스템 간 통신에 적합한 안전하고, 신뢰할 수 있으며, 최적화된 바인딩을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-103">Specifies a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="68a8c-104">기본적으로 메시지 보안 및 인증을 위한 Windows 보안, 메시지 배달을 위한 TCP 및 이진 메시지 인코딩을 지원하는 런타임 통신 스택을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-104">By default, it generates a runtime communication stack with Windows Security for message security and authentication, TCP for message delivery, and binary message encoding.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netTcpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="68a8c-105">구문</span><span class="sxs-lookup"><span data-stu-id="68a8c-105">Syntax</span></span>  
  
```xml  
<netTcpBinding>
  <binding closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           listenBacklog="Integer"
           maxBufferPoolSize="integer"
           maxBufferSize="Integer"
           maxConnections="Integer"
           maxReceivedMessageSize="Integer"
           name="string"
           openTimeout="TimeSpan"
           portSharingEnabled="Boolean"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           transactionFlow="Boolean"
           transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <security mode="None/Transport/Message/Both">
      <message clientCredentialType="None/Windows/UserName/Certificate/CardSpace"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" />
      <transport clientCredentialType="None/Windows/Certificate"
                 protectionLevel="None/Sign/EncryptAndSign" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="68a8c-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="68a8c-106">Attributes and elements</span></span>

<span data-ttu-id="68a8c-107">다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="68a8c-108">특성</span><span class="sxs-lookup"><span data-stu-id="68a8c-108">Attributes</span></span>  
  
|<span data-ttu-id="68a8c-109">attribute</span><span class="sxs-lookup"><span data-stu-id="68a8c-109">Attribute</span></span>|<span data-ttu-id="68a8c-110">Description</span><span class="sxs-lookup"><span data-stu-id="68a8c-110">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="68a8c-111">닫기 작업을 완료하기 위해 제공된 시간 간격을 지정하는 <xref:System.TimeSpan> 값입니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-111">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="68a8c-112">이 값은 <xref:System.TimeSpan.Zero>보다 크거나 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-112">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="68a8c-113">기본값은 00:01:00입니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-113">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="68a8c-114">URI 구문 분석에 사용되는 HTTP 호스트 이름 비교 모드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-114">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="68a8c-115">이 특성은 <xref:System.ServiceModel.HostNameComparisonMode> 형식이며 URI에 대해 비교할 때 호스트 이름이 서비스에 연결하는 데 사용되는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-115">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="68a8c-116">기본값은 <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>이며 이 값은 비교 시 호스트 이름을 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-116">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`listenBacklog`|<span data-ttu-id="68a8c-117">수신기에서 수락하기까지 대기할 수 있는 최대 채널 수를 지정하는 양의 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-117">A positive integer that specifies the maximum number of channels waiting to be accepted on the listener.</span></span> <span data-ttu-id="68a8c-118">이 한도를 초과하는 연결은 채널 수가 한도 아래로 내려갈 때까지 큐에 대기됩니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-118">Connections in excess of this limit are queued until space below the limit becomes available.</span></span> <span data-ttu-id="68a8c-119">`connectionTimeout` 특성은 연결 예외가 throw되기 전에 클라이언트가 연결을 대기하는 시간을 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-119">The `connectionTimeout` attribute limits the time a client will wait to be connected before throwing a connection exception.</span></span> <span data-ttu-id="68a8c-120">기본값은 10입니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-120">The default is 10.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="68a8c-121">이 바인딩의 최대 버퍼 풀 크기를 지정하는 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-121">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="68a8c-122">기본값은 512 \* 1024바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-122">The default is 512 \* 1024 bytes.</span></span> <span data-ttu-id="68a8c-123">WCF(Windows Communication Foundation)의 많은 부분에서 버퍼를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-123">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="68a8c-124">버퍼를 사용할 때마다 만들고 삭제하면 비용이 많이 들며, 버퍼에 대한 가비지 수집 역시 비용이 많이 듭니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-124">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="68a8c-125">버퍼 풀이 있으면 이 풀로부터 버퍼를 가져와 사용한 다음 다시 풀로 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-125">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="68a8c-126">따라서 버퍼를 만들고 제거하는 데 오버헤드를 피할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-126">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="68a8c-127">메시지를 메모리에 저장하는 데 사용되는 버퍼의 최대 크기(바이트)를 지정하는 양의 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-127">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span><br /><br /> <span data-ttu-id="68a8c-128">`transferMode` 특성이 `Buffered`와 같은 경우 이 특성은 `maxReceivedMessageSize` 특성 값과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-128">If the `transferMode` attribute equals to `Buffered`, this attribute should be equal to the `maxReceivedMessageSize` attribute value.</span></span><br /><br /> <span data-ttu-id="68a8c-129">`transferMode` 특성이 `Streamed`와 같은 경우 이 특성은 `maxReceivedMessageSize` 특성 값보다 클 수 없으며 적어도 헤더 크기 이상이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-129">If the `transferMode` attribute equals to `Streamed`, this attribute cannot be more than the `maxReceivedMessageSize` attribute value, and should be at least the size of the headers.</span></span><br /><br /> <span data-ttu-id="68a8c-130">기본값은 65536입니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-130">The default is 65536.</span></span> <span data-ttu-id="68a8c-131">자세한 내용은 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="68a8c-131">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|`maxConnections`|<span data-ttu-id="68a8c-132">서비스에서 생성하고 수락하는 최대 아웃바운드 및 인바운드 연결 수를 지정하는 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-132">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="68a8c-133">들어오는 연결과 나가는 연결 수는 이 특성에서 지정한 별도의 제한에 따라 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-133">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="68a8c-134">이 제한을 초과하는 인바운드 연결은 연결 수가 제한 아래로 내려갈 때까지 큐에 대기됩니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-134">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="68a8c-135">이 한도를 초과하는 아웃바운드 연결은 연결 수가 한도 아래로 내려갈 때까지 큐에 대기됩니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-135">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="68a8c-136">기본값은 10입니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-136">The default is 10.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="68a8c-137">헤더를 비롯하여 이 바인딩으로 구성된 채널에서 받을 수 있는 최대 메시지 크기(바이트)를 지정하는 양의 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-137">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="68a8c-138">이 한도를 초과하는 메시지를 보낸 사람은 SOAP 오류를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-138">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="68a8c-139">수신자는 메시지를 삭제하고 추적 로그에 이벤트 항목을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-139">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="68a8c-140">기본값은 65536입니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-140">The default is 65536.</span></span>|  
|`name`|<span data-ttu-id="68a8c-141">바인딩의 구성 이름을 포함하는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-141">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="68a8c-142">이 값은 바인딩의 ID로 사용되므로 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-142">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="68a8c-143">.NET Framework 4부터 바인딩과 동작은 이름을 가질 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-143">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="68a8c-144">기본 구성 및 이름이 없는 바인딩 및 동작에 대 한 자세한 내용은 [WCF 서비스에 대 한](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [간소화 된 구성](../../../wcf/simplified-configuration.md) 및 단순화 된 구성을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="68a8c-144">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="68a8c-145">열기 작업을 완료하기 위해 제공된 시간 간격을 지정하는 <xref:System.TimeSpan> 값입니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="68a8c-146">이 값은 <xref:System.TimeSpan.Zero>보다 크거나 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="68a8c-147">기본값은 00:01:00입니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-147">The default is 00:01:00.</span></span>|  
|`portSharingEnabled`|<span data-ttu-id="68a8c-148">이 연결에서 TCP 포트 공유를 사용하는지 여부를 지정하는 부울 값입니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-148">A Boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span> <span data-ttu-id="68a8c-149">이 값이 `false`이면 바인딩마다 자체 단독 포트가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-149">If this is `false`, each binding uses its own exclusive port.</span></span> <span data-ttu-id="68a8c-150">클라이언트는 영향을 받지 않으므로 이 설정은 서비스에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-150">This setting is relevant only to services, because clients are not affected.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="68a8c-151">받기 작업을 완료하기 위해 제공된 시간 간격을 지정하는 <xref:System.TimeSpan> 값입니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-151">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="68a8c-152">이 값은 <xref:System.TimeSpan.Zero>보다 크거나 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-152">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="68a8c-153">기본값은 00:10:00입니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-153">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="68a8c-154">보내기 작업을 완료하기 위해 제공된 시간 간격을 지정하는 <xref:System.TimeSpan> 값입니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-154">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="68a8c-155">이 값은 <xref:System.TimeSpan.Zero>보다 크거나 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-155">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="68a8c-156">기본값은 00:01:00입니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-156">The default is 00:01:00.</span></span>|  
|`transactionFlow`|<span data-ttu-id="68a8c-157">바인딩에서 WS-Transactions 이동을 지원할지 여부를 지정하는 부울 값입니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-157">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="68a8c-158">기본값은 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-158">The default is `false`.</span></span>|  
|`transactionProtocol`|<span data-ttu-id="68a8c-159">이 바인딩과 함께 사용되는 트랜잭션 프로토콜을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-159">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="68a8c-160">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-160">Valid values are</span></span><br /><br /> <span data-ttu-id="68a8c-161">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="68a8c-161">-   OleTransactions</span></span><br /><span data-ttu-id="68a8c-162">-WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="68a8c-162">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="68a8c-163">기본값은 OleTransactions입니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-163">The default is OleTransactions.</span></span> <span data-ttu-id="68a8c-164">이 특성은 <xref:System.ServiceModel.TransactionProtocol> 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-164">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|`transferMode`|<span data-ttu-id="68a8c-165">메시지가 버퍼링되거나 스트리밍되는지 또는 요청이나 응답인지 지정하는 <xref:System.ServiceModel.TransferMode> 값입니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-165">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="68a8c-166">자식 요소</span><span class="sxs-lookup"><span data-stu-id="68a8c-166">Child elements</span></span>  
  
|<span data-ttu-id="68a8c-167">요소</span><span class="sxs-lookup"><span data-stu-id="68a8c-167">Element</span></span>|<span data-ttu-id="68a8c-168">Description</span><span class="sxs-lookup"><span data-stu-id="68a8c-168">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-nettcpbinding.md)|<span data-ttu-id="68a8c-169">바인딩에 대한 보안 설정을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-169">Defines the security settings for the binding.</span></span> <span data-ttu-id="68a8c-170">이 요소는 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement> 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-170">This element is of type <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>.</span></span>|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="68a8c-171">이 바인딩으로 구성된 엔드포인트에서 처리할 수 있는 SOAP 메시지의 복잡성에 대한 제약 조건을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-171">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="68a8c-172">이 요소는 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-172">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[\<reliableSession>](/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="68a8c-173">채널 엔드포인트 간에 신뢰할 수 있는 세션이 설정되는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-173">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="68a8c-174">부모 요소</span><span class="sxs-lookup"><span data-stu-id="68a8c-174">Parent elements</span></span>  
  
|<span data-ttu-id="68a8c-175">요소</span><span class="sxs-lookup"><span data-stu-id="68a8c-175">Element</span></span>|<span data-ttu-id="68a8c-176">Description</span><span class="sxs-lookup"><span data-stu-id="68a8c-176">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="68a8c-177">이 요소는 표준 및 사용자 지정 바인딩의 컬렉션을 보유합니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-177">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68a8c-178">설명</span><span class="sxs-lookup"><span data-stu-id="68a8c-178">Remarks</span></span>

<span data-ttu-id="68a8c-179">이 바인딩에서는 기본적으로 런타임 통신 스택을 생성하며, 이 스택은 전송 보안, 메시지 배달을 위한 TCP 및 이진 메시지 인코딩을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-179">This binding generates a run-time communication stack by default, which uses transport security, TCP for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="68a8c-180">이 바인딩은 인트라넷을 통해 통신 하는 데 적합 한 WCF (Windows Communication Foundation) 시스템 제공 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-180">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for communicating over an Intranet.</span></span>  
  
 <span data-ttu-id="68a8c-181">의 기본 구성은에서 제공 하는 `netTcpBinding` 구성 보다 빠르지만 `wsHttpBinding` WCF 통신에만 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-181">The default configuration for the `netTcpBinding` is faster than the configuration provided by the `wsHttpBinding`, but it is intended only for WCF communication.</span></span> <span data-ttu-id="68a8c-182">보안 동작은 선택적 `securityMode` 특성을 사용하여 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-182">The security behavior is configurable using the optional `securityMode` attribute.</span></span> <span data-ttu-id="68a8c-183">WS-ReliableMessaging 사용 시 선택적 `reliableSessionEnabled` 특성을 사용하여 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-183">The use of WS-ReliableMessaging is configurable using the optional `reliableSessionEnabled` attribute.</span></span> <span data-ttu-id="68a8c-184">그러나 신뢰할 수 있는 메시징은 기본적으로 해제 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-184">But reliable messaging is off by default.</span></span> <span data-ttu-id="68a8c-185">보다 일반적으로, 및와 같은 HTTP 시스템 제공 바인딩은 `wsHttpBinding` `basicHttpBinding` 기본적으로 기능을 설정 하도록 구성 되어 있습니다. 반면, `netTcpBinding` 바인딩은 WS-\* 사양 중 하나에 대 한 지원을 받기 위해 옵트인 (opt in) 할 수 있도록 기본적으로 기능을 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-185">More generally, the HTTP system-provided bindings such as `wsHttpBinding` and `basicHttpBinding` are configured to turn things on by default, whereas the `netTcpBinding` binding turns things off by default so that you have to opt-in to get support, for example, for one of the WS-\* specifications.</span></span> <span data-ttu-id="68a8c-186">따라서 엔드포인트 간에 메시지를 교환할 경우의 TCP 기본 구성이 HTTP 바인딩을 위한 기본 구성보다 더 빠릅니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-186">This means that the default configuration for TCP is faster at exchanging messages between endpoints than those configured for the HTTP bindings by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68a8c-187">예제</span><span class="sxs-lookup"><span data-stu-id="68a8c-187">Example</span></span>

<span data-ttu-id="68a8c-188">클라이언트 및 서비스 구성 파일에 바인딩이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-188">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="68a8c-189">바인딩 형식은 `binding` 요소의 `<endpoint>` 특성에서 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-189">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="68a8c-190">netTcpBinding 바인딩을 구성하고 일부 설정을 변경하려면 바인딩 구성을 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-190">If you want to configure the netTcpBinding binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="68a8c-191">엔드포인트는 `bindingConfiguration` 특성을 사용하여 바인딩 구성을 참조해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-191">The endpoint must reference the binding configuration with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="68a8c-192">다음 예제에서는 바인딩 구성을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="68a8c-192">In the following example, a binding configuration is defined.</span></span>  
  
```xml  
<services>
  <service name="Microsoft.ServiceModel.Samples.CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    ...
    <endpoint address=""
              binding="netTcpBinding"
              contract="Microsoft.ServiceModel.Samples.ICalculator" />
    ...
  </service>
</services>
<bindings>
  <netTcpBinding>
    <binding closeTimeout="00:01:00"
             openTimeout="00:01:00"
             receiveTimeout="00:10:00"
             sendTimeout="00:01:00"
             transactionFlow="false"
             transferMode="Buffered"
             transactionProtocol="OleTransactions"
             hostNameComparisonMode="StrongWildcard"
             listenBacklog="10"
             maxBufferPoolSize="524288"
             maxBufferSize="65536"
             maxConnections="10"
             maxReceivedMessageSize="65536">
      <readerQuotas maxDepth="32"
                    maxStringContentLength="8192"
                    maxArrayLength="16384"
                    maxBytesPerRead="4096"
                    maxNameTableCharCount="16384" />
      <reliableSession ordered="true"
                       inactivityTimeout="00:10:00"
                       enabled="false" />
      <security mode="Transport">
        <transport clientCredentialType="Windows" protectionLevel="EncryptAndSign" />
      </security>
    </binding>
  </netTcpBinding>
</bindings>
```  
  
## <a name="see-also"></a><span data-ttu-id="68a8c-193">참조</span><span class="sxs-lookup"><span data-stu-id="68a8c-193">See also</span></span>

- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement>
- [<span data-ttu-id="68a8c-194">바인딩</span><span class="sxs-lookup"><span data-stu-id="68a8c-194">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="68a8c-195">시스템 제공 바인딩 구성</span><span class="sxs-lookup"><span data-stu-id="68a8c-195">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="68a8c-196">바인딩을 사용하여 서비스 및 클라이언트 구성</span><span class="sxs-lookup"><span data-stu-id="68a8c-196">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
