---
ms.openlocfilehash: ae557ce57557d027dba35b7da213c08aee85f2c7
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622077"
---
### <a name="aspnet-fix-handling-of-inputattributes-and-labelattributes-for-webforms-checkbox-control"></a><span data-ttu-id="2dded-101">WebForms CheckBox 컨트롤에 대한 InputAttributes 및 LabelAttributes의 ASP.NET Fix 처리</span><span class="sxs-lookup"><span data-stu-id="2dded-101">ASP.NET Fix handling of InputAttributes and LabelAttributes for WebForms CheckBox control</span></span>

#### <a name="details"></a><span data-ttu-id="2dded-102">설명</span><span class="sxs-lookup"><span data-stu-id="2dded-102">Details</span></span>

<span data-ttu-id="2dded-103">.NET Framework 4.7.2 이하 버전을 대상으로 하는 애플리케이션의 경우, WebForms <xref:System.Web.UI.WebControls.CheckBox> 컨트롤에 프로그래밍 방식으로 추가된 <xref:System.Web.UI.WebControls.CheckBox.InputAttributes?displayProperty=nameWithType> 및 <xref:System.Web.UI.WebControls.CheckBox.LabelAttributes?displayProperty=nameWithType>는 포스트백 후에 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="2dded-103">For applications that target .NET Framework 4.7.2 and earlier versions, <xref:System.Web.UI.WebControls.CheckBox.InputAttributes?displayProperty=nameWithType> and <xref:System.Web.UI.WebControls.CheckBox.LabelAttributes?displayProperty=nameWithType> that are programmatically added to a WebForms <xref:System.Web.UI.WebControls.CheckBox> control are lost after postback.</span></span> <span data-ttu-id="2dded-104">.NET Framework 4.8 이상 버전을 대상으로 하는 애플리케이션의 경우, 포스트백 후 그대로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="2dded-104">For applications that target .NET Framework 4.8 or later versions, they are preserved after postback.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2dded-105">제안 해결 방법</span><span class="sxs-lookup"><span data-stu-id="2dded-105">Suggestion</span></span>

<span data-ttu-id="2dded-106">포스트백에서 특성을 복원하는 올바른 동작을 위해 <code>targetFrameworkVersion</code>를 4.8 이상으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2dded-106">For the correct behavior for restoring attributes on postback, set the <code>targetFrameworkVersion</code> to 4.8 or higher.</span></span> <span data-ttu-id="2dded-107">예를 들어:</span><span class="sxs-lookup"><span data-stu-id="2dded-107">For example:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;system.web&gt;&#13;&#10;&lt;httpRuntime targetFramework=&quot;4.8&quot;/&gt;&#13;&#10;&lt;/system.web&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre><span data-ttu-id="2dded-108">더 낮게 설정하거나 전혀 설정되지 않으면 이전의 잘못된 동작이 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="2dded-108">Setting it lower, or not at all, preserves the old incorrect behavior.</span></span>

| <span data-ttu-id="2dded-109">이름</span><span class="sxs-lookup"><span data-stu-id="2dded-109">Name</span></span>    | <span data-ttu-id="2dded-110">값</span><span class="sxs-lookup"><span data-stu-id="2dded-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2dded-111">Scope</span><span class="sxs-lookup"><span data-stu-id="2dded-111">Scope</span></span>   |<span data-ttu-id="2dded-112">알 수 없음</span><span class="sxs-lookup"><span data-stu-id="2dded-112">Unknown</span></span>|
|<span data-ttu-id="2dded-113">버전</span><span class="sxs-lookup"><span data-stu-id="2dded-113">Version</span></span>|<span data-ttu-id="2dded-114">4.8</span><span class="sxs-lookup"><span data-stu-id="2dded-114">4.8</span></span>|
|<span data-ttu-id="2dded-115">형식</span><span class="sxs-lookup"><span data-stu-id="2dded-115">Type</span></span>|<span data-ttu-id="2dded-116">런타임</span><span class="sxs-lookup"><span data-stu-id="2dded-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2dded-117">영향을 받는 API</span><span class="sxs-lookup"><span data-stu-id="2dded-117">Affected APIs</span></span>

-<xref:System.Web.UI.WebControls.CheckBox?displayProperty=nameWithType></li></ul>|
