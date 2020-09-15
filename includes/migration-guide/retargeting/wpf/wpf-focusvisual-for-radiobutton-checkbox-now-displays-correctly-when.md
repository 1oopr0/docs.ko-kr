---
ms.openlocfilehash: 9e70bcd95393a7ff24de43577d26869ce674067b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614963"
---
### <a name="wpf-focusvisual-for-radiobutton-and-checkbox-now-displays-correctly-when-the-controls-have-no-content"></a><span data-ttu-id="e954d-101">RadioButton 및 CheckBox용 WPF FocusVisual은 컨트롤이 콘텐츠가 없을 경우 올바르게 표시됨</span><span class="sxs-lookup"><span data-stu-id="e954d-101">WPF FocusVisual for RadioButton and CheckBox Now Displays Correctly When The Controls Have No Content</span></span>

#### <a name="details"></a><span data-ttu-id="e954d-102">설명</span><span class="sxs-lookup"><span data-stu-id="e954d-102">Details</span></span>

<span data-ttu-id="e954d-103">.NET Framework 4.7.1 및 이전 버전에서 WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWithType> 및 <xref:System.Windows.Controls.RadioButton?displayProperty=nameWithType>에는 일치하지 않는, 그리고 기본 및 고대비 테마에서는 잘못된 포커스 시각적 개체가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e954d-103">In the .NET Framework 4.7.1 and earlier versions, WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWithType> and <xref:System.Windows.Controls.RadioButton?displayProperty=nameWithType> have inconsistent and, in Classic and High Contrast themes, incorrect focus visuals.</span></span>  <span data-ttu-id="e954d-104">이러한 문제는 컨트롤에 아무 콘텐츠 집합도 없는 경우 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="e954d-104">These issues occur in cases where the controls do not have any content set.</span></span>  <span data-ttu-id="e954d-105">이렇게 하면 테마 혼동 및 포커스 시각적 개체 간 전환을 보기 어렵게 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e954d-105">This can make the transition between themes confusing and the focus visual hard to see.</span></span> <span data-ttu-id="e954d-106">NET Framework 4.7.2에서 이러한 시각적 개체는 이제 테마에서 더욱 일관적이고 기본 및 고대비 테마에서 더욱 쉽게 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e954d-106">In the .NET Framework 4.7.2, these visuals are now more consistent across themes and more easily visible in Classic and High Contrast themes.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e954d-107">제안 해결 방법</span><span class="sxs-lookup"><span data-stu-id="e954d-107">Suggestion</span></span>

<span data-ttu-id="e954d-108">.NET 4.7.1에서 동작을 되돌리려는 .NET Framework 4.7.2를 대상으로 하는 개발자는 다음 AppContext 플래그를 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e954d-108">A developer targeting .NET Framework 4.7.2 that wants to revert to the behavior in .NET 4.7.1 will need to set the following AppContext flag.</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures.2=true;&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

<span data-ttu-id="e954d-109">.NET 4.7.2 미만 프레임워크 버전을 대상으로 하면서 이 변경을 활용하려는 개발자는 다음 AppContext 플래그를 설정해야 합니다. 모든 플래그를 적절하게 설정해야 하며 설치된 .NET Framework 버전은 4.7.2 이상이어야 합니다. WPF 애플리케이션이 최신 기능 향상을 가져오려면 모든 이전 접근성 향상을 옵트인할 것을 요구합니다.</span><span class="sxs-lookup"><span data-stu-id="e954d-109">A developer who wants to utilize this change while targeting a framework version below .NET 4.7.2 must set the following AppContext flags.Note that all the flags must be set appropriately and the installed version of the .NET Framework must be 4.7.2 or greater.WPF applications are required to opt in to all earlier accessibility improvements to get the latest improvements.</span></span> <span data-ttu-id="e954d-110">이러려면 AppContext 스위치 'Switch.UseLegacyAccessibilityFeatures' 및 'Switch.UseLegacyAccessibilityFeatures.2' 모두가 False로 설정됐는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e954d-110">To do this, ensure that both the AppContext switches 'Switch.UseLegacyAccessibilityFeatures' and 'Switch.UseLegacyAccessibilityFeatures.2' are set to false.</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="e954d-111">이름</span><span class="sxs-lookup"><span data-stu-id="e954d-111">Name</span></span>    | <span data-ttu-id="e954d-112">값</span><span class="sxs-lookup"><span data-stu-id="e954d-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e954d-113">Scope</span><span class="sxs-lookup"><span data-stu-id="e954d-113">Scope</span></span>   | <span data-ttu-id="e954d-114">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="e954d-114">Edge</span></span>        |
| <span data-ttu-id="e954d-115">버전</span><span class="sxs-lookup"><span data-stu-id="e954d-115">Version</span></span> | <span data-ttu-id="e954d-116">4.7.2</span><span class="sxs-lookup"><span data-stu-id="e954d-116">4.7.2</span></span>       |
| <span data-ttu-id="e954d-117">형식</span><span class="sxs-lookup"><span data-stu-id="e954d-117">Type</span></span>    | <span data-ttu-id="e954d-118">대상 변경</span><span class="sxs-lookup"><span data-stu-id="e954d-118">Retargeting</span></span> |
