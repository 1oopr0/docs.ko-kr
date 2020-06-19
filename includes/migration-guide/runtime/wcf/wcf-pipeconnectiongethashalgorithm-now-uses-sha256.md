---
ms.openlocfilehash: 318609c15d2e0b9a7ee59b38463735b33ef87974
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857243"
---
### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a><span data-ttu-id="53d0e-101">WCF PipeConnection.GetHashAlgorithm은 이제 SHA256을 사용</span><span class="sxs-lookup"><span data-stu-id="53d0e-101">WCF PipeConnection.GetHashAlgorithm now uses SHA256</span></span>

|   |   |
|---|---|
|<span data-ttu-id="53d0e-102">설명</span><span class="sxs-lookup"><span data-stu-id="53d0e-102">Details</span></span>|<span data-ttu-id="53d0e-103">.NET Framework 4.7.1부터 Windows Communication Foundation은 명명 된 파이프에 대한 임의 이름을 생성하기 위해 SHA256 해시를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="53d0e-103">Starting with the .NET Framework 4.7.1, Windows Communication Foundation uses a SHA256 hash to generate random names for named pipes.</span></span> <span data-ttu-id="53d0e-104">.NET Framework 4.7 및 이전 버전에서는 SHA1 해시를 사용했습니다.</span><span class="sxs-lookup"><span data-stu-id="53d0e-104">In the .NET Framework 4.7 and earlier versions, it used a SHA1 hash.</span></span>|
|<span data-ttu-id="53d0e-105">제안 해결 방법</span><span class="sxs-lookup"><span data-stu-id="53d0e-105">Suggestion</span></span>|<span data-ttu-id="53d0e-106">.NET Framework 4.7.1 이상에서 이러한 변경 내용과의 호환성 문제가 발생하면 app.config 파일의 <code>&lt;runtime&gt;</code> 섹션에 다음 줄을 추가하여 옵트아웃할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53d0e-106">If you run into compatibility issue with this change on the .NET Framework 4.7.1 or later, you can opt-out it by adding the following line to the <code>&lt;runtime&gt;</code> section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="53d0e-107">Scope</span><span class="sxs-lookup"><span data-stu-id="53d0e-107">Scope</span></span>|<span data-ttu-id="53d0e-108">부</span><span class="sxs-lookup"><span data-stu-id="53d0e-108">Minor</span></span>|
|<span data-ttu-id="53d0e-109">버전</span><span class="sxs-lookup"><span data-stu-id="53d0e-109">Version</span></span>|<span data-ttu-id="53d0e-110">4.7.1</span><span class="sxs-lookup"><span data-stu-id="53d0e-110">4.7.1</span></span>|
|<span data-ttu-id="53d0e-111">형식</span><span class="sxs-lookup"><span data-stu-id="53d0e-111">Type</span></span>|<span data-ttu-id="53d0e-112">런타임</span><span class="sxs-lookup"><span data-stu-id="53d0e-112">Runtime</span></span>|
