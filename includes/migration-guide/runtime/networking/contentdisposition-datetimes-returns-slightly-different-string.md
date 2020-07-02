---
ms.openlocfilehash: c103dff320ae30d02c12ea5c585a47b589da8237
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621309"
---
### <a name="contentdisposition-datetimes-returns-slightly-different-string"></a><span data-ttu-id="190e1-101">ContentDisposition DateTimes는 약간 다른 문자열을 반환합니다</span><span class="sxs-lookup"><span data-stu-id="190e1-101">ContentDisposition DateTimes returns slightly different string</span></span>

#### <a name="details"></a><span data-ttu-id="190e1-102">세부 정보</span><span class="sxs-lookup"><span data-stu-id="190e1-102">Details</span></span>

<span data-ttu-id="190e1-103">4\.6부터 <xref:System.Net.Mime.ContentDisposition?displayProperty=fullName>의 문자열 표현이 항상 <xref:System.DateTime?displayProperty=fullName>의 시간 구성 요소를 두 자리로 표시하도록 업데이트되었습니다.</span><span class="sxs-lookup"><span data-stu-id="190e1-103">String representations of <xref:System.Net.Mime.ContentDisposition?displayProperty=fullName>'s have been updated, beginning in 4.6, to always represent the hour component of a <xref:System.DateTime?displayProperty=fullName> with two digits.</span></span> <span data-ttu-id="190e1-104">이것은 [RFC822](https://www.ietf.org/rfc/rfc0822.txt) 및 [RFC2822](https://www.ietf.org/rfc/rfc2822.txt)를 준수하기 위함입니다.</span><span class="sxs-lookup"><span data-stu-id="190e1-104">This is to comply with [RFC822](https://www.ietf.org/rfc/rfc0822.txt) and [RFC2822](https://www.ietf.org/rfc/rfc2822.txt).</span></span> <span data-ttu-id="190e1-105">이로 인해 4.6에서 <xref:System.Net.Mime.ContentDisposition.ToString>은 처리 시간 요소 중 하나가 오전 10시 전인 시나리오에서 약간 다른 문자열을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="190e1-105">This causes <xref:System.Net.Mime.ContentDisposition.ToString> to return a slightly different string in 4.6 in scenarios where one of the disposition's time elements was before 10:00 AM.</span></span> <span data-ttu-id="190e1-106">ContentDispositions는 가끔 문자열로 변환하여 직렬화되므로 모든 <xref:System.Net.Mime.ContentDisposition.ToString> 작업, 직렬화 또는 GetHashCode 호출이 검토되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="190e1-106">Note that ContentDispositions are sometimes serialized via converting them to strings, so any <xref:System.Net.Mime.ContentDisposition.ToString> operations, serialization, or GetHashCode calls should be reviewed.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="190e1-107">제안 해결 방법</span><span class="sxs-lookup"><span data-stu-id="190e1-107">Suggestion</span></span>

<span data-ttu-id="190e1-108">다른 .NET Framework 버전에서 ContentDispositions의 문자열 표현이 서로 올바르게 비교할 것으로 기대하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="190e1-108">Do not expect that string representations of ContentDispositions from different .NET Framework versions will correctly compare to one another.</span></span> <span data-ttu-id="190e1-109">가능하면 비교를 수행하기 전에 문자열을 다시 ContentDispositions로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="190e1-109">Convert the strings back to ContentDispositions, if possible, before conducting a comparison.</span></span>

| <span data-ttu-id="190e1-110">이름</span><span class="sxs-lookup"><span data-stu-id="190e1-110">Name</span></span>    | <span data-ttu-id="190e1-111">값</span><span class="sxs-lookup"><span data-stu-id="190e1-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="190e1-112">Scope</span><span class="sxs-lookup"><span data-stu-id="190e1-112">Scope</span></span>   |<span data-ttu-id="190e1-113">부</span><span class="sxs-lookup"><span data-stu-id="190e1-113">Minor</span></span>|
|<span data-ttu-id="190e1-114">버전</span><span class="sxs-lookup"><span data-stu-id="190e1-114">Version</span></span>|<span data-ttu-id="190e1-115">4.6</span><span class="sxs-lookup"><span data-stu-id="190e1-115">4.6</span></span>|
|<span data-ttu-id="190e1-116">형식</span><span class="sxs-lookup"><span data-stu-id="190e1-116">Type</span></span>|<span data-ttu-id="190e1-117">런타임</span><span class="sxs-lookup"><span data-stu-id="190e1-117">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="190e1-118">영향을 받는 API</span><span class="sxs-lookup"><span data-stu-id="190e1-118">Affected APIs</span></span>

-<xref:System.Net.Mime.ContentDisposition.ToString?displayProperty=nameWithType></li><li><xref:System.Net.Mime.ContentDisposition.GetHashCode?displayProperty=nameWithType></li></ul>|
