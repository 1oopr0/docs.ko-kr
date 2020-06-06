---
title: <udpAnnouncementEndpoint>의 <udpTransportSettings>
ms.date: 03/30/2017
ms.assetid: a7ddff1a-5eed-4bbc-8580-b95ef8890e1f
ms.openlocfilehash: b67bdf825948dffe18aabe91b0de236eb929bccc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854853"
---
# <a name="udptransportsettings-of-udpannouncementendpoint"></a><span data-ttu-id="3bf9a-102">\<udpAnnouncementEndpoint>의 \<udpTransportSettings></span><span class="sxs-lookup"><span data-stu-id="3bf9a-102">\<udpTransportSettings> of \<udpAnnouncementEndpoint></span></span>
<span data-ttu-id="3bf9a-103">이 구성 요소는에 대 한 UDP 전송 설정을 노출 [\<udpAnnouncementEndpoint>](udpannouncementendpoint.md) 합니다.</span><span class="sxs-lookup"><span data-stu-id="3bf9a-103">This configuration element exposes UDP transport settings for [\<udpAnnouncementEndpoint>](udpannouncementendpoint.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<udpAnnouncementEndpoint>**](udpannouncementendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<updTransportSettings>**  

## <a name="syntax"></a><span data-ttu-id="3bf9a-104">구문</span><span class="sxs-lookup"><span data-stu-id="3bf9a-104">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <udpAnnouncementEndpoint>
      <standardEndpoint>
        <updTransportSettings duplicateMessageHistoryLength="Integer"
                              maxBufferPoolSize="Integer"
                              maxMulticastRetransmitCount="Integer"
                              maxPendingMessageCount="Integer"
                              maxReceivedMessageSize="Integer"
                              maxUnicastRetransmitCount="Integer"
                              multicastInterfaceId="String"
                              socketReceiveBufferSize="Integer"
                              timeToLive="Integer" />
      </standardEndpoint>
    </udpAnnouncementEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3bf9a-105">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="3bf9a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="3bf9a-106">다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3bf9a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3bf9a-107">특성</span><span class="sxs-lookup"><span data-stu-id="3bf9a-107">Attributes</span></span>  
  
|<span data-ttu-id="3bf9a-108">attribute</span><span class="sxs-lookup"><span data-stu-id="3bf9a-108">Attribute</span></span>|<span data-ttu-id="3bf9a-109">Description</span><span class="sxs-lookup"><span data-stu-id="3bf9a-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3bf9a-110">duplicateMessageHistoryLength</span><span class="sxs-lookup"><span data-stu-id="3bf9a-110">duplicateMessageHistoryLength</span></span>|<span data-ttu-id="3bf9a-111">중복 메시지를 식별하기 위해 전송에 사용되는 최대 메시지 해시 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3bf9a-111">An integer that specifies the maximum number of message hashes used by the transport for identifying duplicate messages.</span></span>  <span data-ttu-id="3bf9a-112">TransportManager 수준에서 중복 검색이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="3bf9a-112">Duplicate detection will be done at the TransportManager level.</span></span> <span data-ttu-id="3bf9a-113">이 속성을 0으로 설정하면 중복 검색이 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3bf9a-113">Setting this property to 0 disables duplicate detection.</span></span><br /><br /> <span data-ttu-id="3bf9a-114">시스템 관리자나 개발자는 이 특성을 사용하여 중복 메시지 검색 알고리즘을 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3bf9a-114">This attribute allows system administrators or developers to turn off duplicate message detection algorithms.</span></span> <span data-ttu-id="3bf9a-115">직접 작성한 중복 검색 알고리즘을 구현하려는 경우 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3bf9a-115">This may be desirable if you want to implement your own duplicate detection algorithm.</span></span><br /><br /> <span data-ttu-id="3bf9a-116">기본값은 4112입니다.</span><span class="sxs-lookup"><span data-stu-id="3bf9a-116">The default is 4112.</span></span>|  
|<span data-ttu-id="3bf9a-117">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="3bf9a-117">maxBufferPoolSize</span></span>|<span data-ttu-id="3bf9a-118">전송에 사용할 수 있는 버퍼 풀의 최대 크기를 지정하는 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="3bf9a-118">An integer that specifies the maximum size of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="3bf9a-119">maxMulticastRetransmitCount</span><span class="sxs-lookup"><span data-stu-id="3bf9a-119">maxMulticastRetransmitCount</span></span>|<span data-ttu-id="3bf9a-120">메시지를 처음 보낸 후 재전송해야 하는 최대 횟수를 지정하는 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="3bf9a-120">An integer that specifies the maximum number of times the message should be retransmitted (in addition to the first send).</span></span><br /><br /> <span data-ttu-id="3bf9a-121">기본값은 2입니다.</span><span class="sxs-lookup"><span data-stu-id="3bf9a-121">The default is 2.</span></span>|  
|<span data-ttu-id="3bf9a-122">maxPendingMessageCount</span><span class="sxs-lookup"><span data-stu-id="3bf9a-122">maxPendingMessageCount</span></span>|<span data-ttu-id="3bf9a-123">수신되었으나 개별 채널 인스턴스의 InputQueue에서 아직 제거되지 않은 최대 메시지 수를 지정하는 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="3bf9a-123">An integer that specifies the maximum number of messages that have been received but not yet removed from the InputQueue for an individual channel instance.</span></span>  <span data-ttu-id="3bf9a-124">InputQueue가 보류 중인 메시지 수 제한에 도달하는 경우 메시지가 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="3bf9a-124">If the InputQueue has hit its pending message count limit, the message will be dropped.</span></span><br /><br /> <span data-ttu-id="3bf9a-125">기본값은 32입니다.</span><span class="sxs-lookup"><span data-stu-id="3bf9a-125">The default is 32.</span></span>|  
|<span data-ttu-id="3bf9a-126">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="3bf9a-126">maxReceivedMessageSize</span></span>|<span data-ttu-id="3bf9a-127">바인딩에서 처리할 수 있는 메시지의 최대 크기를 지정하는 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="3bf9a-127">An integer that specifies the maximum size for a message that can be processed by the binding.</span></span><br /><br /> <span data-ttu-id="3bf9a-128">기본값은 65507입니다.</span><span class="sxs-lookup"><span data-stu-id="3bf9a-128">The default value is 65507.</span></span>|  
|<span data-ttu-id="3bf9a-129">maxUnicastRetransmitCount</span><span class="sxs-lookup"><span data-stu-id="3bf9a-129">maxUnicastRetransmitCount</span></span>|<span data-ttu-id="3bf9a-130">메시지를 처음 보낸 후 재전송해야 하는 최대 횟수를 지정하는 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="3bf9a-130">An integer that specifies the maximum number of times the message should be retransmitted (in addition to the first send).</span></span>  <span data-ttu-id="3bf9a-131">메시지를 유니캐스트 주소로 보내고 응답 메시지가 해당 RelatesTo 헤더에서 수신되면 구성된 횟수만큼 재전송하기 하기 전에 재전송이 일찍 종료될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3bf9a-131">If the message is sent to a unicast address and a response message is received with a corresponding RelatesTo header, then retransmission may terminate early (before retransmitting the configured number of times).</span></span><br /><br /> <span data-ttu-id="3bf9a-132">기본값은 1입니다.</span><span class="sxs-lookup"><span data-stu-id="3bf9a-132">The default value is 1.</span></span>|  
|<span data-ttu-id="3bf9a-133">multicastInterfaceId</span><span class="sxs-lookup"><span data-stu-id="3bf9a-133">multicastInterfaceId</span></span>|<span data-ttu-id="3bf9a-134">멀티홈 컴퓨터에서 멀티캐스트 트래픽을 보내고 받을 때 사용해야 하는 네트워크 어댑터를 고유하게 식별하는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="3bf9a-134">A string that uniquely identifies the network adapter that should be used when sending and receiving multicast traffic on multi-homed machines.</span></span> <span data-ttu-id="3bf9a-135">런타임에 전송에서 이 특성 값을 사용하여 인터페이스 인덱스를 조회합니다. 이 인덱스는 `IP_MULTICAST_IF` 및 `IPV6_MULTICAST_IF` 소켓 옵션을 설정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3bf9a-135">At runtime, the transport will use this attribute value to lookup the interface index, which is then used to set the `IP_MULTICAST_IF` and `IPV6_MULTICAST_IF` socket options.</span></span>  <span data-ttu-id="3bf9a-136">해당되는 경우 동일한 인터페이스 인덱스가 멀티캐스트 그룹을 조인할 때 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3bf9a-136">The same interface index will be used when joining a multicast group, if applicable.</span></span><br /><br /> <span data-ttu-id="3bf9a-137">기본값은 `null`입니다.</span><span class="sxs-lookup"><span data-stu-id="3bf9a-137">The default value is `null`.</span></span>|  
|<span data-ttu-id="3bf9a-138">socketReceiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="3bf9a-138">socketReceiveBufferSize</span></span>|<span data-ttu-id="3bf9a-139">기본 WinSock 소켓의 수신 버퍼 크기를 지정하는 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="3bf9a-139">An integer that specifies the receive buffer size on the underlying WinSock socket.</span></span><br /><br /> <span data-ttu-id="3bf9a-140">수신 채널의 사용자는 바인딩의 이 특성을 사용하여 데이터를 받을 때 시스템이 동작하는 방식을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3bf9a-140">A user of a receiving channel can use this attribute on the Binding to control how the system behaves when it receives data.</span></span>  <span data-ttu-id="3bf9a-141">예를 들어 최대 임계값으로 인바운드 WCF 메시지를 사용하는 특정 애플리케이션에서 이 특성에 더 큰 값을 사용하면 애플리케이션에서 메시지를 처리할 수 있을 때까지 대기하는 동안 메시지가 WinSock 버퍼에 쌓이게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3bf9a-141">For example, given an application that is consuming inbound WCF messages at the maximum threshold, using a higher value for this attribute would allow messages to stack up in the WinSock buffer while waiting for the application to be able to process them.</span></span>  <span data-ttu-id="3bf9a-142">같은 상황에서 더 작은 값을 사용하면 메시지가 삭제됩니다. 이 특성은 기본 WinSock `SO_RCVBUF` 소켓 옵션을 노출합니다. 이 특성의 값은 적어도 `maxReceivedMessageSize` 크기 이상이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3bf9a-142">Using a lower value in the same situation would result in messages getting dropped.This attribute exposes the underlying WinSock `SO_RCVBUF` socket option.This attribute value must be at least the size of `maxReceivedMessageSize`.</span></span>   <span data-ttu-id="3bf9a-143">이 값을 `maxReceivedMessageSize`보다 작은 값으로 설정하며 런타임 예외가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="3bf9a-143">Setting it to a value smaller than the `maxReceivedMessageSize` will result in runtime exception.</span></span><br /><br /> <span data-ttu-id="3bf9a-144">기본값은 65536입니다.</span><span class="sxs-lookup"><span data-stu-id="3bf9a-144">The default value is 65536.</span></span>|  
|<span data-ttu-id="3bf9a-145">timeToLive</span><span class="sxs-lookup"><span data-stu-id="3bf9a-145">timeToLive</span></span>|<span data-ttu-id="3bf9a-146">멀티캐스트 패킷이 이동할 수 있는 네트워크 세그먼트 홉의 수를 지정하는 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="3bf9a-146">An integer that specifies the number of network segment hops that a multicast packet can traverse.</span></span>  <span data-ttu-id="3bf9a-147">이 특성은 `IP_MULTICAST_TTL` 및 `IP_TTL` 소켓 옵션과 관련된 기능을 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="3bf9a-147">This attribute exposes the functionality associated with the `IP_MULTICAST_TTL` and `IP_TTL` socket options.</span></span><br /><br /> <span data-ttu-id="3bf9a-148">기본값은 1입니다.</span><span class="sxs-lookup"><span data-stu-id="3bf9a-148">The default value is 1.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3bf9a-149">자식 요소</span><span class="sxs-lookup"><span data-stu-id="3bf9a-149">Child Elements</span></span>  
 <span data-ttu-id="3bf9a-150">없음</span><span class="sxs-lookup"><span data-stu-id="3bf9a-150">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3bf9a-151">부모 요소</span><span class="sxs-lookup"><span data-stu-id="3bf9a-151">Parent Elements</span></span>  
  
|<span data-ttu-id="3bf9a-152">요소</span><span class="sxs-lookup"><span data-stu-id="3bf9a-152">Element</span></span>|<span data-ttu-id="3bf9a-153">Description</span><span class="sxs-lookup"><span data-stu-id="3bf9a-153">Description</span></span>|  
|-------------|-----------------|  
|[\<udpAnnouncementEndpoint>](udpannouncementendpoint.md)|<span data-ttu-id="3bf9a-154">고정 알림 계약 및 UDP 전송 바인딩이 있는 표준 엔드포인트입니다.</span><span class="sxs-lookup"><span data-stu-id="3bf9a-154">A standard endpoint that has fixed announcement contract and UDP transport binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3bf9a-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3bf9a-155">See also</span></span>

- <xref:System.ServiceModel.Discovery.UdpTransportSettings>
