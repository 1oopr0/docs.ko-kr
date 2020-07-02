---
ms.openlocfilehash: ccdf232d743c9e270b6ed21f698998eb95a97399
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621218"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a><span data-ttu-id="3b33b-101">WCF MsmqSecureHashAlgorithm 기본값은 이제 SHA256입니다.</span><span class="sxs-lookup"><span data-stu-id="3b33b-101">WCF MsmqSecureHashAlgorithm default value is now SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="3b33b-102">설명</span><span class="sxs-lookup"><span data-stu-id="3b33b-102">Details</span></span>

<span data-ttu-id="3b33b-103">.NET Framework 4.7.1부터 Msmq 메시지에 대한 WCF의 기본 메시지 서명 알고리즘은 SHA256입니다.</span><span class="sxs-lookup"><span data-stu-id="3b33b-103">Starting with the .NET Framework 4.7.1, the default message signing algorithm in WCF for Msmq messages is SHA256.</span></span> <span data-ttu-id="3b33b-104">.NET Framework 4.7 및 이전 버전에서 기본 메시지 서명 알고리즘은 SHA1입니다.</span><span class="sxs-lookup"><span data-stu-id="3b33b-104">In the .NET Framework 4.7 and earlier versions, the default message signing algorithm is SHA1.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3b33b-105">제안 해결 방법</span><span class="sxs-lookup"><span data-stu-id="3b33b-105">Suggestion</span></span>

<span data-ttu-id="3b33b-106">.NET Framework 4.7.1 이상에서 이러한 변경 내용과의 호환성 문제가 발생하면 app.config 파일의 <code>&lt;runtime&gt;</code> 섹션에 다음 줄을 추가하여 변경 내용을 옵트아웃할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b33b-106">If you run into compatibility issues with this change on the .NET Framework 4.7.1 or later, you can opt-out the change by adding the following line to the <code>&lt;runtime&gt;</code>section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="3b33b-107">이름</span><span class="sxs-lookup"><span data-stu-id="3b33b-107">Name</span></span>    | <span data-ttu-id="3b33b-108">값</span><span class="sxs-lookup"><span data-stu-id="3b33b-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3b33b-109">Scope</span><span class="sxs-lookup"><span data-stu-id="3b33b-109">Scope</span></span>   |<span data-ttu-id="3b33b-110">부</span><span class="sxs-lookup"><span data-stu-id="3b33b-110">Minor</span></span>|
|<span data-ttu-id="3b33b-111">버전</span><span class="sxs-lookup"><span data-stu-id="3b33b-111">Version</span></span>|<span data-ttu-id="3b33b-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="3b33b-112">4.7.1</span></span>|
|<span data-ttu-id="3b33b-113">형식</span><span class="sxs-lookup"><span data-stu-id="3b33b-113">Type</span></span>|<span data-ttu-id="3b33b-114">런타임</span><span class="sxs-lookup"><span data-stu-id="3b33b-114">Runtime</span></span>|
