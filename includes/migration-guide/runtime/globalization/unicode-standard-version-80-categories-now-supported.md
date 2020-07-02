---
ms.openlocfilehash: a20fad5f9c95e59c14ffd91f4921cf8bfab443cd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621189"
---
### <a name="unicode-standard-version-80-categories-now-supported"></a><span data-ttu-id="90190-101">유니코드 표준 버전 8.0 범주가 이제 지원됨</span><span class="sxs-lookup"><span data-stu-id="90190-101">Unicode standard version 8.0 categories now supported</span></span>

#### <a name="details"></a><span data-ttu-id="90190-102">세부 정보</span><span class="sxs-lookup"><span data-stu-id="90190-102">Details</span></span>

<span data-ttu-id="90190-103">.NET Framework 4.6.2에서 유니코드 데이터가 유니코드 표준 버전 6.3에서 8.0으로 업그레이드되었습니다.</span><span class="sxs-lookup"><span data-stu-id="90190-103">In .NET Framework 4.6.2, Unicode data has been upgraded from Unicode Standard version 6.3 to version 8.0.</span></span>  <span data-ttu-id="90190-104">.NET Framework 4.6.2에서 유니코드 문자 범주를 요청할 때 일부 결과가 이전 .NET Framework 버전의 결과와 일치하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90190-104">When requesting Unicode character categories in .NET Framework 4.6.2, some results might not match the results in previous .NET Framework versions.</span></span>  <span data-ttu-id="90190-105">이러한 변경은 주로 체로키어 음절 및 New Tai Lue 모음 기호 및 성조 표시에 영향을 미칩니다.</span><span class="sxs-lookup"><span data-stu-id="90190-105">This change mostly affects Cherokee syllables and New Tai Lue vowels signs and tone marks.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="90190-106">제안 해결 방법</span><span class="sxs-lookup"><span data-stu-id="90190-106">Suggestion</span></span>

<span data-ttu-id="90190-107">코드를 검토하고 하드 코드된 유니코드 문자 범주에 종속된 논리를 제거/변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90190-107">Review code and remove/change logic that depends on hard-coded Unicode character categories.</span></span>

| <span data-ttu-id="90190-108">이름</span><span class="sxs-lookup"><span data-stu-id="90190-108">Name</span></span>    | <span data-ttu-id="90190-109">값</span><span class="sxs-lookup"><span data-stu-id="90190-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="90190-110">Scope</span><span class="sxs-lookup"><span data-stu-id="90190-110">Scope</span></span>   |<span data-ttu-id="90190-111">부</span><span class="sxs-lookup"><span data-stu-id="90190-111">Minor</span></span>|
|<span data-ttu-id="90190-112">버전</span><span class="sxs-lookup"><span data-stu-id="90190-112">Version</span></span>|<span data-ttu-id="90190-113">4.6.2</span><span class="sxs-lookup"><span data-stu-id="90190-113">4.6.2</span></span>|
|<span data-ttu-id="90190-114">형식</span><span class="sxs-lookup"><span data-stu-id="90190-114">Type</span></span>|<span data-ttu-id="90190-115">런타임</span><span class="sxs-lookup"><span data-stu-id="90190-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="90190-116">영향을 받는 API</span><span class="sxs-lookup"><span data-stu-id="90190-116">Affected APIs</span></span>

-<xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType></li></ul>|
