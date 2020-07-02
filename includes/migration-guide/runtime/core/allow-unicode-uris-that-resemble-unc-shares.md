---
ms.openlocfilehash: 3e8601ba76dfb05e3d70b3af7440bd7e228768d0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621170"
---
### <a name="allow-unicode-in-uris-that-resemble-unc-shares"></a><span data-ttu-id="66508-101">UNC 공유와 비슷한 URI에서 유니코드 허용</span><span class="sxs-lookup"><span data-stu-id="66508-101">Allow Unicode in URIs that resemble UNC shares</span></span>

#### <a name="details"></a><span data-ttu-id="66508-102">설명</span><span class="sxs-lookup"><span data-stu-id="66508-102">Details</span></span>

<span data-ttu-id="66508-103"><xref:System.Uri?displayProperty=fullName>에서 UNC 공유 이름 및 유니코드 문자 모두를 포함하는 파일 URI를 생성하면 더 이상 잘못된 내부 상태의 URI를 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="66508-103">In <xref:System.Uri?displayProperty=fullName>, constructing a file URI containing both a UNC share name and Unicode characters will no longer result in a URI with invalid internal state.</span></span> <span data-ttu-id="66508-104">이 동작은 다음의 모든 것이 True인 경우에만 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="66508-104">The behavior will change only when all of the following are true:</span></span><ul><li><span data-ttu-id="66508-105">URI는 구성표 <code>file:</code>을 보유하며 4개 이상의 슬래시가 뒤따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="66508-105">The URI has the scheme <code>file:</code> and is followed by four or more slashes.</span></span></li><li><span data-ttu-id="66508-106">호스트 이름은 밑줄 또는 기타 예약되지 않은 기호로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="66508-106">The host name begins with an underscore or other non-reserved symbol.</span></span></li><li><span data-ttu-id="66508-107">URI에 유니코드 문자가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66508-107">The URI contains Unicode characters.</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="66508-108">제안 해결 방법</span><span class="sxs-lookup"><span data-stu-id="66508-108">Suggestion</span></span>

<span data-ttu-id="66508-109">지속적으로 유니코드를 포함하는 URI를 사용하여 작동하는 애플리케이션은 UNC 공유에 대한 참조를 허용하지 않기 위해 이 동작을 사용했습니다.</span><span class="sxs-lookup"><span data-stu-id="66508-109">Applications working with URIs consistently containing Unicode could have conceivably used this behavior to disallow references to UNC shares.</span></span> <span data-ttu-id="66508-110">이러한 애플리케이션은 대신 <xref:System.Uri.IsUnc>을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="66508-110">Those applications should use <xref:System.Uri.IsUnc> instead.</span></span>

| <span data-ttu-id="66508-111">이름</span><span class="sxs-lookup"><span data-stu-id="66508-111">Name</span></span>    | <span data-ttu-id="66508-112">값</span><span class="sxs-lookup"><span data-stu-id="66508-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="66508-113">Scope</span><span class="sxs-lookup"><span data-stu-id="66508-113">Scope</span></span>   |<span data-ttu-id="66508-114">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="66508-114">Edge</span></span>|
|<span data-ttu-id="66508-115">버전</span><span class="sxs-lookup"><span data-stu-id="66508-115">Version</span></span>|<span data-ttu-id="66508-116">4.7.2</span><span class="sxs-lookup"><span data-stu-id="66508-116">4.7.2</span></span>|
|<span data-ttu-id="66508-117">형식</span><span class="sxs-lookup"><span data-stu-id="66508-117">Type</span></span>|<span data-ttu-id="66508-118">런타임</span><span class="sxs-lookup"><span data-stu-id="66508-118">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="66508-119">영향을 받는 API</span><span class="sxs-lookup"><span data-stu-id="66508-119">Affected APIs</span></span>

-<xref:System.Uri?displayProperty=nameWithType></li></ul>|
