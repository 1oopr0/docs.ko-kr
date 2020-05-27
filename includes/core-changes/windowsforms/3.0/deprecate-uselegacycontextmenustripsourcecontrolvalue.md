---
ms.openlocfilehash: 3ada05a13ec7acde1d8374ed733d0d51cdfb408c
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721463"
---
### <a name="uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a><span data-ttu-id="12d1d-101">UseLegacyContextMenuStripSourceControlValue 호환성 스위치가 지원되지 않음</span><span class="sxs-lookup"><span data-stu-id="12d1d-101">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>

<span data-ttu-id="12d1d-102">.NET Framework 4.7.2에서 도입된 `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` 호환성 스위치는 .NET Core 3.0의 Windows Forms에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="12d1d-102">The `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch, which was introduced in .NET Framework 4.7.2, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="12d1d-103">변경 내용 설명</span><span class="sxs-lookup"><span data-stu-id="12d1d-103">Change description</span></span>

<span data-ttu-id="12d1d-104">.NET Framework 4.7.2부터는 개발자가 `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` 호환성 스위치를 통해 소스 제어에 대한 참조를 반환하는 <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> 속성의 새 동작을 옵트아웃할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12d1d-104">Starting with the .NET Framework 4.7.2, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch allows the developer to opt out of the new behavior of the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> property, which now returns a reference to the source control.</span></span> <span data-ttu-id="12d1d-105">이 속성의 이전 동작은 `null`을 반환하는 것이었습니다.</span><span class="sxs-lookup"><span data-stu-id="12d1d-105">The previous behavior of the property was to return `null`.</span></span> <span data-ttu-id="12d1d-106">자세한 내용은 [\<AppContextSwitchOverrides> 요소](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="12d1d-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="12d1d-107">.NET Core에서는 `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` 스위치가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="12d1d-107">In .NET Core, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="12d1d-108">도입된 버전</span><span class="sxs-lookup"><span data-stu-id="12d1d-108">Version introduced</span></span>

<span data-ttu-id="12d1d-109">3.0 미리 보기 9</span><span class="sxs-lookup"><span data-stu-id="12d1d-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="12d1d-110">권장 조치</span><span class="sxs-lookup"><span data-stu-id="12d1d-110">Recommended action</span></span>

<span data-ttu-id="12d1d-111">스위치를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="12d1d-111">Remove the switch.</span></span> <span data-ttu-id="12d1d-112">이 스위치는 지원되지 않으며, 사용 가능한 대체 기능이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="12d1d-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="12d1d-113">범주</span><span class="sxs-lookup"><span data-stu-id="12d1d-113">Category</span></span>

<span data-ttu-id="12d1d-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="12d1d-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="12d1d-115">영향을 받는 API</span><span class="sxs-lookup"><span data-stu-id="12d1d-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->
