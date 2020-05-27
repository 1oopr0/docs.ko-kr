---
ms.openlocfilehash: acb8ed44b7d18b257731e32339f087c8fe5fdd4a
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721563"
---
### <a name="types-in-microsoftvisualbasicmyservices-namespace-not-available"></a><span data-ttu-id="6d5b5-101">Microsoft.VisualBasic.MyServices 네임스페이스의 형식을 사용할 수 없음</span><span class="sxs-lookup"><span data-stu-id="6d5b5-101">Types in Microsoft.VisualBasic.MyServices namespace not available</span></span>

<span data-ttu-id="6d5b5-102"><xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> 네임스페이스의 형식을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6d5b5-102">The types in the <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> namespace are not available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6d5b5-103">도입된 버전</span><span class="sxs-lookup"><span data-stu-id="6d5b5-103">Version introduced</span></span>

<span data-ttu-id="6d5b5-104">.NET Core 3.0 미리 보기 8</span><span class="sxs-lookup"><span data-stu-id="6d5b5-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="6d5b5-105">변경 내용 설명</span><span class="sxs-lookup"><span data-stu-id="6d5b5-105">Change description</span></span>

<span data-ttu-id="6d5b5-106">일부 .NET Core 3.0 미리 보기 릴리스에서는 <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> 네임스페이스의 형식을 사용할 수 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="6d5b5-106">The types in the <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> namespace were available in some .NET Core 3.0 Preview releases.</span></span> <span data-ttu-id="6d5b5-107">.NET Core 3.0 미리 보기 9부터는 해당 형식을 더 이상 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6d5b5-107">They are no longer available starting with .NET Core 3.0 Preview 9.</span></span>

<span data-ttu-id="6d5b5-108">후속 릴리스에서 불필요한 어셈블리 종속성이나 호환성이 손상되는 변경을 방지하기 위해 형식을 제거했습니다.</span><span class="sxs-lookup"><span data-stu-id="6d5b5-108">The types were removed to avoid unnecessary assembly dependencies or breaking changes in subsequent releases.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6d5b5-109">권장 조치</span><span class="sxs-lookup"><span data-stu-id="6d5b5-109">Recommended action</span></span>

<span data-ttu-id="6d5b5-110">코드에서 **Microsoft.VisualBasic.MyServices** 형식과 해당 멤버를 사용해야 하는 경우, .NET 클래스 라이브러리에 해당 형식과 멤버가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d5b5-110">If your code depends on the use of **Microsoft.VisualBasic.MyServices** types and their members, there are corresponding types and members in the .NET class library.</span></span> <span data-ttu-id="6d5b5-111">**Microsoft.VisualBasic.MyServices** 형식과 동등한 .NET 클래스 라이브러리 형식의 매핑은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6d5b5-111">The following is a mapping of  **Microsoft.VisualBasic.MyServices** types to their equivalent .NET class library types:</span></span>

|<span data-ttu-id="6d5b5-112">Microsoft.VisualBasic.MyServices 형식</span><span class="sxs-lookup"><span data-stu-id="6d5b5-112">Microsoft.VisualBasic.MyServices type</span></span>|<span data-ttu-id="6d5b5-113">.NET 클래스 라이브러리 형식</span><span class="sxs-lookup"><span data-stu-id="6d5b5-113">.NET class library type</span></span>|
|--|--|
|<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>|<span data-ttu-id="6d5b5-114">WPF 애플리케이션의 경우 <xref:System.Windows.Clipboard?displayProperty=nameWithType>, Windows Forms 애플리케이션의 경우 <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="6d5b5-114"><xref:System.Windows.Clipboard?displayProperty=nameWithType> for WPF applications, <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> for Windows Forms applications</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy>|<span data-ttu-id="6d5b5-115"><xref:System.IO> 네임스페이스의 형식</span><span class="sxs-lookup"><span data-stu-id="6d5b5-115">Types in the <xref:System.IO> namespace</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>|<span data-ttu-id="6d5b5-116"><xref:Microsoft.Win32> 네임스페이스의 레지스트리 관련 형식</span><span class="sxs-lookup"><span data-stu-id="6d5b5-116">Registry-related types in the <xref:Microsoft.Win32> namespace</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.SpecialDirectoriesProxy>|<xref:System.Environment.GetFolderPath%2A?displayProperty=nameWithType>|

#### <a name="category"></a><span data-ttu-id="6d5b5-117">범주</span><span class="sxs-lookup"><span data-stu-id="6d5b5-117">Category</span></span>

<span data-ttu-id="6d5b5-118">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6d5b5-118">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6d5b5-119">영향을 받는 API</span><span class="sxs-lookup"><span data-stu-id="6d5b5-119">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>

<!--

#### Affected APIs

- `N:Microsoft.VisualBasic.MyServices`

-->
