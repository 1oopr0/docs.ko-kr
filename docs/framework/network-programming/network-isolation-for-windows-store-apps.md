---
title: Windows 스토어 앱에 대한 네트워크 격리
ms.date: 03/30/2017
ms.assetid: b064497c-d956-46b8-838d-7a0223c7e200
ms.openlocfilehash: 0f9288b53b969838cac64c24d3c9861a0f841aca
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558461"
---
# <a name="network-isolation-for-windows-store-apps"></a><span data-ttu-id="67508-102">Windows 스토어 앱에 대한 네트워크 격리</span><span class="sxs-lookup"><span data-stu-id="67508-102">Network Isolation for Windows Store Apps</span></span>

<span data-ttu-id="67508-103"><xref:System.Net>, <xref:System.Net.Http> 및 <xref:System.Net.Http.Headers> 네임스페이스의 클래스는 Windows 스토어 앱 또는 데스크톱 앱을 개발하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67508-103">Classes in the <xref:System.Net>, <xref:System.Net.Http>, and <xref:System.Net.Http.Headers> namespaces can be used to develop Windows Store  apps  or desktop apps.</span></span> <span data-ttu-id="67508-104">Windows 스토어 앱에서 사용할 때 이러한 네임스페이스의 클래스는 Windows 8에서 사용한 애플리케이션 보안 모델의 일부인 네트워크 격리의 영향을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="67508-104">When used in a Windows Store app, classes in these namespaces are affected by network isolation, part of the application security model used by Windows 8.</span></span> <span data-ttu-id="67508-105">시스템의 Windows 스토어 앱에서 네트워크에 액세스할 수 있도록 앱 매니페스트에서 적절한 네트워크 기능을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67508-105">The appropriate network capabilities must be enabled in the app manifest for a Windows Store app for the system to allow network access.</span></span>  
  
## <a name="checklist-for-network-isolation"></a><span data-ttu-id="67508-106">네트워크 격리 검사 목록</span><span class="sxs-lookup"><span data-stu-id="67508-106">Checklist for Network Isolation</span></span>  

<span data-ttu-id="67508-107">이 검사 목록을 사용하여 Windows 스토어 앱에 대해 네트워크 격리가 구성되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="67508-107">Use this checklist to be sure that network isolation is configured for your Windows Store app.</span></span>  
  
1. <span data-ttu-id="67508-108">앱에 필요한 네트워크 액세스 요청의 방향을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="67508-108">Determine the direction of network access requests needed by the app.</span></span> <span data-ttu-id="67508-109">이 방향은 아웃바운드 클라이언트에서 시작된 요청 또는 원치 않는 인바운드 요청이거나, 이러한 두 네트워크 요청 유형을 조합한 것일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67508-109">This can be either outbound client-initiated requests or inbound unsolicited requests or it could be a combination of both of these network request types.</span></span>  
  
2. <span data-ttu-id="67508-110">앱과 통신하는 네트워크 리소스의 유형을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="67508-110">Determine the type of network resources that the app will communicate with.</span></span> <span data-ttu-id="67508-111">앱이 홈 또는 회사 네트워크에서 신뢰할 수 있는 리소스와 통신해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67508-111">An app may need to communicate with trusted resources on a Home or Work network.</span></span> <span data-ttu-id="67508-112">앱에서 인터넷에 있는 리소스와 통신해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67508-112">An app might need to communicate with resources on the Internet.</span></span> <span data-ttu-id="67508-113">앱에서 두 가지 유형의 네트워크 리소스 모두에 액세스해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67508-113">An app might need access to both types of network resources.</span></span>  
  
3. <span data-ttu-id="67508-114">앱 매니페스트에서 필요한 최소 네트워킹 격리 기능을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="67508-114">Configure the minimum-required networking isolation capabilities in the app manifest.</span></span>  
  
4. <span data-ttu-id="67508-115">문제 해결을 위해 제공된 네트워크 격리 도구를 사용하여 테스트하도록 앱을 배포하고 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="67508-115">Deploy and run your app to test it using the network isolation tools provided for troubleshooting.</span></span>  
  
<span data-ttu-id="67508-116">네트워크 격리 문제를 해결하는 데 사용한 네트워크 기능과 격리 도구를 구성하는 방법에 대한 자세한 내용은 Windows 8.x 스토어 개발자 문서의 [네트워크 격리 기능 구성 방법](/previous-versions/windows/apps/hh770532(v=win.10))을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="67508-116">For more detailed information on how to configure network capabilities and isolation tools used for troubleshooting network isolation, see [How to configure network isolation capabilities](/previous-versions/windows/apps/hh770532(v=win.10)) in the Windows 8.x Store developer documentation.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="67508-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="67508-117">See also</span></span>

- <span data-ttu-id="67508-118">[웹 서비스에 연결](/previous-versions/windows/apps/hh761504(v=win.10))</span><span class="sxs-lookup"><span data-stu-id="67508-118">[Connecting to a web service](/previous-versions/windows/apps/hh761504(v=win.10))</span></span>
- <span data-ttu-id="67508-119">[네트워크 격리 지침 및 검사 목록](/previous-versions/windows/apps/hh770532(v=win.10))</span><span class="sxs-lookup"><span data-stu-id="67508-119">[Guidelines and checklist for network isolation](/previous-versions/windows/apps/hh770532(v=win.10))</span></span>
- <span data-ttu-id="67508-120">[빠른 시작: HttpClient를 사용하여 연결](/previous-versions/windows/apps/hh781239(v=win.10))</span><span class="sxs-lookup"><span data-stu-id="67508-120">[Quickstart: Connecting using HttpClient](/previous-versions/windows/apps/hh781239(v=win.10))</span></span>
- <span data-ttu-id="67508-121">[HttpClient 처리기 사용 방법](/previous-versions/windows/apps/hh781241(v=win.10))</span><span class="sxs-lookup"><span data-stu-id="67508-121">[How to use HttpClient handlers](/previous-versions/windows/apps/hh781241(v=win.10))</span></span>
- <span data-ttu-id="67508-122">[HttpClient 연결 보호 방법](/previous-versions/windows/apps/hh781240(v=win.10))</span><span class="sxs-lookup"><span data-stu-id="67508-122">[How to secure HttpClient connections](/previous-versions/windows/apps/hh781240(v=win.10))</span></span>
- [<span data-ttu-id="67508-123">HttpClient 샘플</span><span class="sxs-lookup"><span data-stu-id="67508-123">HttpClient Sample</span></span>](https://code.msdn.microsoft.com/windowsapps/HttpClient-sample-55700664)
