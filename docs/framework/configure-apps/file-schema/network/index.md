---
title: 네트워크 설정 스키마
ms.date: 03/30/2017
helpviewer_keywords:
- elements [.NET Framework], network configuration elements
- sending data, network configuration elements
- receiving data, network configuration elements
- configuration settings [.NET Framework], networks
- Internet, network configuration elements
- network configuration elements
- network settings
- connections [.NET Framework], network configuration elements
- network resources, network configuration elements
ms.assetid: f1de5a0f-76c5-4833-819f-5222b8146340
ms.openlocfilehash: 5e3bd1b1734fc7fba50b72785531a8b001d6d741
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/06/2020
ms.locfileid: "71698159"
---
# <a name="network-settings-schema"></a><span data-ttu-id="3745a-102">네트워크 설정 스키마</span><span class="sxs-lookup"><span data-stu-id="3745a-102">Network Settings Schema</span></span>
<span data-ttu-id="3745a-103">네트워크 설정으로 .NET Framework의 인터넷 연결 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3745a-103">Network settings specify how the .NET Framework connects to the Internet.</span></span>

<span data-ttu-id="3745a-104">\<system.net>설정은 .NET Framework 네트워크에 연결 하는 방법을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3745a-104">The \<system.net> settings specify how the .NET Framework connects to the network.</span></span> <span data-ttu-id="3745a-105">다음 표에서는 [ \<system.Net> 요소 (네트워크 설정)](system-net-element-network-settings.md)아래에 있는 각 자식 구성 요소의 기능을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="3745a-105">The following table describes the function of each child configuration element under the [\<system.Net> Element (Network Settings)](system-net-element-network-settings.md).</span></span>  
  
|<span data-ttu-id="3745a-106">요소</span><span class="sxs-lookup"><span data-stu-id="3745a-106">Element</span></span>|<span data-ttu-id="3745a-107">Description</span><span class="sxs-lookup"><span data-stu-id="3745a-107">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3745a-108">\<authenticationModules>요소 (네트워크 설정)</span><span class="sxs-lookup"><span data-stu-id="3745a-108">\<authenticationModules> Element (Network Settings)</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="3745a-109">인터넷 요청을 인증하는 데 사용되는 모듈을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3745a-109">Specifies the modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="3745a-110">\<connectionManagement>요소 (네트워크 설정)</span><span class="sxs-lookup"><span data-stu-id="3745a-110">\<connectionManagement> Element (Network Settings)</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="3745a-111">인터넷 호스트에 대한 최대 연결 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3745a-111">Specifies the maximum number of connections to Internet hosts.</span></span>|  
|[<span data-ttu-id="3745a-112">\<defaultProxy>요소 (네트워크 설정)</span><span class="sxs-lookup"><span data-stu-id="3745a-112">\<defaultProxy> Element (Network Settings)</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="3745a-113">인터넷에 대한 HTTP 요청에 사용할 프록시 서버를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3745a-113">Specifies the proxy server used for HTTP requests to the Internet.</span></span>|  
|[<span data-ttu-id="3745a-114">\<mailSettings>요소 (네트워크 설정)</span><span class="sxs-lookup"><span data-stu-id="3745a-114">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="3745a-115">메일 보내기 옵션에 대한 설정을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="3745a-115">Contains settings for mail sending options.</span></span>|  
|[<span data-ttu-id="3745a-116">\<requestCaching>요소 (네트워크 설정)</span><span class="sxs-lookup"><span data-stu-id="3745a-116">\<requestCaching> Element (Network Settings)</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="3745a-117">네트워크 요청에 대 한 캐싱 메커니즘을 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="3745a-117">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="3745a-118">\<webRequestModules>요소 (네트워크 설정)</span><span class="sxs-lookup"><span data-stu-id="3745a-118">\<webRequestModules> Element (Network Settings)</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="3745a-119">인터넷 호스트 정보를 요청하는 데 사용되는 모듈을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3745a-119">Specifies the modules used to request information from Internet hosts.</span></span>|  
  
<span data-ttu-id="3745a-120">\<uri>설정은 .NET Framework uri (uniform resource identifier)를 사용 하 여 표현 된 웹 주소를 처리 하는 방법을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3745a-120">The \<uri> settings specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span> <span data-ttu-id="3745a-121">다음 표에서는 요소의 각 자식 구성 요소 [ \<uri> (Uri 설정)](uri-element-uri-settings.md)에 대 한 함수에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="3745a-121">The following table describes the function of each child configuration element under the [\<uri> Element (Uri Settings)](uri-element-uri-settings.md).</span></span>  
  
|<span data-ttu-id="3745a-122">요소</span><span class="sxs-lookup"><span data-stu-id="3745a-122">Element</span></span>|<span data-ttu-id="3745a-123">Description</span><span class="sxs-lookup"><span data-stu-id="3745a-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3745a-124">\<idn>요소 (Uri 설정)</span><span class="sxs-lookup"><span data-stu-id="3745a-124">\<idn> Element (Uri Settings)</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="3745a-125">IDN(Internationalized Domain Name) 구문 분석이 도메인 이름에 적용되는지 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3745a-125">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="3745a-126">\<iriParsing>요소 (Uri 설정)</span><span class="sxs-lookup"><span data-stu-id="3745a-126">\<iriParsing> Element (Uri Settings)</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="3745a-127">IRI(International Resource Identifier) 구문 분석이 <xref:System.Uri>에 적용되는지와 IRI 구문 분석 규칙을 적용해야 하는지 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3745a-127">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="3745a-128">\<schemeSettings>요소 (Uri 설정)</span><span class="sxs-lookup"><span data-stu-id="3745a-128">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="3745a-129">특정 체계에 대해 <xref:System.Uri>가 구문 분석되는 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3745a-129">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3745a-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3745a-130">See also</span></span>

- [<span data-ttu-id="3745a-131">인터넷 애플리케이션 구성</span><span class="sxs-lookup"><span data-stu-id="3745a-131">Configuring Internet Applications</span></span>](../../../network-programming/configuring-internet-applications.md)
- [<span data-ttu-id="3745a-132">구성 파일 스키마</span><span class="sxs-lookup"><span data-stu-id="3745a-132">Configuration File Schema</span></span>](../index.md)
