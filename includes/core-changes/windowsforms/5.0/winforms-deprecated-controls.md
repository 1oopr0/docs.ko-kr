---
ms.openlocfilehash: c9720f51e40ada4cd2cf6997ba7006a232893553
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702490"
---
### <a name="removed-status-bar-controls"></a><span data-ttu-id="8796d-101">상태 표시줄 컨트롤 제거</span><span class="sxs-lookup"><span data-stu-id="8796d-101">Removed status bar controls</span></span>

<span data-ttu-id="8796d-102">.NET 5.0 미리 보기 1부터 일부 Windows Forms 컨트롤을 더 이상 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8796d-102">Starting in .NET 5.0 Preview 1, some Windows Forms controls are no longer available.</span></span>

#### <a name="change-description"></a><span data-ttu-id="8796d-103">변경 내용 설명</span><span class="sxs-lookup"><span data-stu-id="8796d-103">Change description</span></span>

<span data-ttu-id="8796d-104">.NET 5.0 미리 보기 1부터 상태 표시줄 관련 Windows Forms 컨트롤 중 일부를 더 이상 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8796d-104">Starting with .NET 5.0 Preview 1, some of the status bar-related Windows Forms controls are no longer available.</span></span> <span data-ttu-id="8796d-105">향상된 디자인 및 지원을 제공하는 대체 컨트롤이 .NET Framework 2.0에 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8796d-105">Replacement controls that have better design and support were introduced in .NET Framework 2.0.</span></span> <span data-ttu-id="8796d-106">사용되지 않는 컨트롤은 이전에 디자이너 도구 상자에서 제거되었지만, 여전히 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8796d-106">The deprecated controls were previously removed from designer toolboxes but were still available to be used.</span></span> <span data-ttu-id="8796d-107">이제 완전히 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8796d-107">Now, they have been completely removed.</span></span>

<span data-ttu-id="8796d-108">다음 형식은 더 이상 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8796d-108">The following types are no longer available:</span></span>

* `StatusBar`
* `StatusBarDrawItemEventArgs`
* `StatusBarDrawItemEventHandler`
* `StatusBarPanel`
* `StatusBarPanelAutoSize`
* `StatusBarPanelBorderStyle`
* `StatusBarPanelClickEventArgs`
* `StatusBarPanelClickEventHandler`
* `StatusBarPanelStyle`

#### <a name="version-introduced"></a><span data-ttu-id="8796d-109">도입된 버전</span><span class="sxs-lookup"><span data-stu-id="8796d-109">Version introduced</span></span>

<span data-ttu-id="8796d-110">5.0 미리 보기 1</span><span class="sxs-lookup"><span data-stu-id="8796d-110">5.0 Preview 1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8796d-111">권장 조치</span><span class="sxs-lookup"><span data-stu-id="8796d-111">Recommended action</span></span>

<span data-ttu-id="8796d-112">이러한 컨트롤 및 해당 시나리오에 대한 대체 API로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="8796d-112">Move to the replacement APIs for these controls and their scenarios:</span></span>

| <span data-ttu-id="8796d-113">이전 컨트롤(API)</span><span class="sxs-lookup"><span data-stu-id="8796d-113">Old Control (API)</span></span> | <span data-ttu-id="8796d-114">권장 대체</span><span class="sxs-lookup"><span data-stu-id="8796d-114">Recommended Replacement</span></span>                          |
|-------------------|--------------------------------------------------|
| <span data-ttu-id="8796d-115">StatusBar</span><span class="sxs-lookup"><span data-stu-id="8796d-115">StatusBar</span></span>         | <xref:System.Windows.Forms.StatusStrip>          |
| <span data-ttu-id="8796d-116">StatusBarPanel</span><span class="sxs-lookup"><span data-stu-id="8796d-116">StatusBarPanel</span></span>    | <xref:System.Windows.Forms.ToolStripStatusLabel> |

#### <a name="category"></a><span data-ttu-id="8796d-117">범주</span><span class="sxs-lookup"><span data-stu-id="8796d-117">Category</span></span>

<span data-ttu-id="8796d-118">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8796d-118">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8796d-119">영향을 받는 API</span><span class="sxs-lookup"><span data-stu-id="8796d-119">Affected APIs</span></span>

- <xref:System.Windows.Forms.StatusBar?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarDrawItemEventArgs?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarDrawItemEventHandler?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanel?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelAutoSize?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelBorderStyle?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelClickEventArgs?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelClickEventHandler?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelStyle?displayProperty=fullName>

<!-- 

#### Affected APIs

- `T:System.Windows.Forms.StatusBar`
- `T:System.Windows.Forms.StatusBarDrawItemEventArgs`
- `T:System.Windows.Forms.StatusBarDrawItemEventHandler`
- `T:System.Windows.Forms.StatusBarPanel`
- `T:System.Windows.Forms.StatusBarPanelAutoSize`
- `T:System.Windows.Forms.StatusBarPanelBorderStyle`
- `T:System.Windows.Forms.StatusBarPanelClickEventArgs`
- `T:System.Windows.Forms.StatusBarPanelClickEventHandler`
- `T:System.Windows.Forms.StatusBarPanelStyle` 

-->
