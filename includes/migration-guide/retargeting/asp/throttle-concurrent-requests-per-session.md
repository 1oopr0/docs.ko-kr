---
ms.openlocfilehash: 9c3eedb7f7d4cd030a12c141b8630876c1ffdb4d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859081"
---
### <a name="throttle-concurrent-requests-per-session"></a><span data-ttu-id="15240-101">세션당 동시 요청 수 조절</span><span class="sxs-lookup"><span data-stu-id="15240-101">Throttle concurrent requests per session</span></span>

|   |   |
|---|---|
|<span data-ttu-id="15240-102">설명</span><span class="sxs-lookup"><span data-stu-id="15240-102">Details</span></span>|<span data-ttu-id="15240-103">.NET Framework 4.6.2 이전 버전에서 ASP.NET은 같은 Sessionid를 사용하여 요청을 순차적으로 실행하고, ASP.NET은 항상 기본적으로 쿠키를 통해 Sessionid를 발급합니다.</span><span class="sxs-lookup"><span data-stu-id="15240-103">In the .NET Framework 4.6.2 and earlier, ASP.NET executes requests with the same Sessionid sequentially, and ASP.NET always issues the Sessionid through cookies by default.</span></span> <span data-ttu-id="15240-104">페이지가 응답하는 데 시간이 오래 걸릴 때 브라우저에서 F5 키를 누르면 서버 성능이 크게 저하됩니다.</span><span class="sxs-lookup"><span data-stu-id="15240-104">If a page takes a long time to respond, it will significantly degrade server performance just by pressing F5 on the browser.</span></span> <span data-ttu-id="15240-105">수정 사항에서는 카운터를 추가하여 큐에 대기 중인 요청을 추적하고 지정된 한도를 초과할 때 요청을 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="15240-105">In the fix, we added a counter to track the queued requests and terminate the requests when they exceed a specified limit.</span></span> <span data-ttu-id="15240-106">기본값은 50입니다.</span><span class="sxs-lookup"><span data-stu-id="15240-106">The default value is 50.</span></span> <span data-ttu-id="15240-107">이 한도에 도달하면 이벤트 로그에 경고가 기록되고 HTTP 500 응답이 IIS 로그에 기록될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15240-107">If the limit is reached, a warning will be logged in the event log, and an HTTP 500 response may be recorded in the IIS log.</span></span>|
|<span data-ttu-id="15240-108">제안 해결 방법</span><span class="sxs-lookup"><span data-stu-id="15240-108">Suggestion</span></span>|<span data-ttu-id="15240-109">이전 동작을 복원하려면 web.config 파일에 다음 설정을 추가하여 새 동작을 옵트아웃(opt out)할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15240-109">To restore the old behavior, you can add the following setting to your web.config file to opt out of the new behavior.</span></span><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;aspnet:RequestQueueLimitPerSession&quot; value=&quot;2147483647&quot;/&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="15240-110">Scope</span><span class="sxs-lookup"><span data-stu-id="15240-110">Scope</span></span>|<span data-ttu-id="15240-111">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="15240-111">Edge</span></span>|
|<span data-ttu-id="15240-112">버전</span><span class="sxs-lookup"><span data-stu-id="15240-112">Version</span></span>|<span data-ttu-id="15240-113">4.7</span><span class="sxs-lookup"><span data-stu-id="15240-113">4.7</span></span>|
|<span data-ttu-id="15240-114">형식</span><span class="sxs-lookup"><span data-stu-id="15240-114">Type</span></span>|<span data-ttu-id="15240-115">대상 변경</span><span class="sxs-lookup"><span data-stu-id="15240-115">Retargeting</span></span>|
