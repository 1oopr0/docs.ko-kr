---
ms.openlocfilehash: 4303b177ffe01328965c909a5a3809414fcead91
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614932"
---
### <a name="the-default-hash-algorithm-for-wpfs-markup-compiler-is-now-sha256"></a><span data-ttu-id="a8aeb-101">WPF의 마크업 컴파일러에 대한 기본 해시 알고리즘은 이제 SHA256</span><span class="sxs-lookup"><span data-stu-id="a8aeb-101">The default hash algorithm for WPF's Markup Compiler is now SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="a8aeb-102">설명</span><span class="sxs-lookup"><span data-stu-id="a8aeb-102">Details</span></span>

<span data-ttu-id="a8aeb-103">WPF MarkupCompiler는 XAML 마크업 파일에 대한 컴파일 서비스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a8aeb-103">The WPF MarkupCompiler provides compilation services for XAML markup files.</span></span>  <span data-ttu-id="a8aeb-104">.NET Framework 4.7.1 및 이전 버전에서 체크섬에 사용되는 기본 해시 알고리즘은 SHA1입니다.</span><span class="sxs-lookup"><span data-stu-id="a8aeb-104">In the .NET Framework 4.7.1 and earlier versions, the default hash algorithm used for checksums was SHA1.</span></span> <span data-ttu-id="a8aeb-105">SHA1의 최근 보안 문제로 인해 이 기본값은 .NET Framework 4.7.2부터 SHA256으로 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a8aeb-105">Due to recent security concerns with SHA1, this default has been changed to SHA256 starting with the .NET Framework 4.7.2.</span></span>  <span data-ttu-id="a8aeb-106">이 변경은 컴파일 동안 마크업 파일에 대한 모든 체크섬 생성에 영향을 미칩니다.</span><span class="sxs-lookup"><span data-stu-id="a8aeb-106">This change affects all checksum generation for markup files during compilation.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a8aeb-107">제안 해결 방법</span><span class="sxs-lookup"><span data-stu-id="a8aeb-107">Suggestion</span></span>

<span data-ttu-id="a8aeb-108">.NET Framework 4.7.2 이상을 대상으로 하고 SHA1 해시 동작으로 되돌리려는 개발자는 다음 AppContext 플래그를 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8aeb-108">A developer who targets .NET Framework 4.7.2 or greater and wants to revert to SHA1 hashing behavior must set the following AppContext flag.</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

<span data-ttu-id="a8aeb-109">.NET 4.7.2 미만 프레임워크 버전을 대상으로 하면서 SHA256 해시를 활용하려는 개발자는 아래의 AppContext 플래그를 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8aeb-109">A developer who wants to utilize SHA256 hashing while targeting a framework version below .NET 4.7.2 must set the below AppContext flag.</span></span>  <span data-ttu-id="a8aeb-110">.NET Framework의 설치된 버전은 4.7.2 이상이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8aeb-110">Note that the installed version of the .NET Framework must be 4.7.2 or greater.</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=false&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="a8aeb-111">이름</span><span class="sxs-lookup"><span data-stu-id="a8aeb-111">Name</span></span>    | <span data-ttu-id="a8aeb-112">값</span><span class="sxs-lookup"><span data-stu-id="a8aeb-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a8aeb-113">Scope</span><span class="sxs-lookup"><span data-stu-id="a8aeb-113">Scope</span></span>   | <span data-ttu-id="a8aeb-114">투명</span><span class="sxs-lookup"><span data-stu-id="a8aeb-114">Transparent</span></span> |
| <span data-ttu-id="a8aeb-115">버전</span><span class="sxs-lookup"><span data-stu-id="a8aeb-115">Version</span></span> | <span data-ttu-id="a8aeb-116">4.7.2</span><span class="sxs-lookup"><span data-stu-id="a8aeb-116">4.7.2</span></span>       |
| <span data-ttu-id="a8aeb-117">형식</span><span class="sxs-lookup"><span data-stu-id="a8aeb-117">Type</span></span>    | <span data-ttu-id="a8aeb-118">대상 변경</span><span class="sxs-lookup"><span data-stu-id="a8aeb-118">Retargeting</span></span> |
