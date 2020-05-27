---
ms.openlocfilehash: cb8c0532bb2bcfbcd619cd382f3d236b431c3480
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721154"
---
### <a name="donotloadlatestricheditcontrol-compatibility-switch-not-supported"></a><span data-ttu-id="faf5c-101">DoNotLoadLatestRichEditControl 호환성 스위치가 지원되지 않음</span><span class="sxs-lookup"><span data-stu-id="faf5c-101">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>

<span data-ttu-id="faf5c-102">.NET Framework 4.7.1에서 도입된 `Switch.System.Windows.Forms.UseLegacyImages` 호환성 스위치는 .NET Core 3.0의 Windows Forms에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="faf5c-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="faf5c-103">변경 내용 설명</span><span class="sxs-lookup"><span data-stu-id="faf5c-103">Change description</span></span>

<span data-ttu-id="faf5c-104">.NET Framework 4.6.2 및 이전 버전에서는 <xref:System.Windows.Forms.RichTextBox> 컨트롤이 Win32 RichEdit 컨트롤 v3.0을 인스턴스화하고, .NET Framework 4.7.1을 대상으로 하는 애플리케이션의 경우 <xref:System.Windows.Forms.RichTextBox> 컨트롤이 *msftedit.dll*에서 RichEdit v4.1을 인스턴스화합니다.</span><span class="sxs-lookup"><span data-stu-id="faf5c-104">In the .NET Framework 4.6.2 and previous versions, the <xref:System.Windows.Forms.RichTextBox> control would instantiate the Win32 RichEdit control v3.0, and for applications that target .NET Framework 4.7.1, the  <xref:System.Windows.Forms.RichTextBox> control would instantiate RichEdit v4.1 (in *msftedit.dll*).</span></span> <span data-ttu-id="faf5c-105">`Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` 호환성 스위치는 .NET Framework 4.7.1 이상 버전을 대상으로 하는 애플리케이션이 새 RichEdit v4.1 컨트롤을 옵트아웃하고 이전 RichEdit v3 컨트롤을 대신 사용할 수 있도록 하기 위해 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="faf5c-105">The `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` compatibility switch was introduced to allow applications that target .NET Framework 4.7.1 and later versions to opt-out of the new RichEdit v4.1 control and use the old RichEdit v3 control instead.</span></span>

<span data-ttu-id="faf5c-106">.NET Core에서는 `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` 스위치가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="faf5c-106">In .NET Core, the `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` switch is not supported.</span></span> <span data-ttu-id="faf5c-107">새 버전의 <xref:System.Windows.Forms.RichTextBox> 컨트롤만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="faf5c-107">Only new versions of the  <xref:System.Windows.Forms.RichTextBox> control are supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="faf5c-108">도입된 버전</span><span class="sxs-lookup"><span data-stu-id="faf5c-108">Version introduced</span></span>

<span data-ttu-id="faf5c-109">3.0 미리 보기 9</span><span class="sxs-lookup"><span data-stu-id="faf5c-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="faf5c-110">권장 조치</span><span class="sxs-lookup"><span data-stu-id="faf5c-110">Recommended action</span></span>

<span data-ttu-id="faf5c-111">스위치를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="faf5c-111">Remove the switch.</span></span> <span data-ttu-id="faf5c-112">이 스위치는 지원되지 않으며, 사용 가능한 대체 기능이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="faf5c-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="faf5c-113">범주</span><span class="sxs-lookup"><span data-stu-id="faf5c-113">Category</span></span>

<span data-ttu-id="faf5c-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="faf5c-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="faf5c-115">영향을 받는 API</span><span class="sxs-lookup"><span data-stu-id="faf5c-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

#### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->
