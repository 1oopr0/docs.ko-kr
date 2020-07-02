---
ms.openlocfilehash: 0bd90b3d479a7e0897aaf78b7718ae156a4a239f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620193"
---
### <a name="assemblies-compiled-with-regexcompiletoassembly-breaks-between-40-and-45"></a><span data-ttu-id="63839-101">Regex.CompileToAssembly로 컴파일된 어셈블리가 4.0과 4.5 사이에서 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="63839-101">Assemblies compiled with Regex.CompileToAssembly breaks between 4.0 and 4.5</span></span>

#### <a name="details"></a><span data-ttu-id="63839-102">설명</span><span class="sxs-lookup"><span data-stu-id="63839-102">Details</span></span>

<span data-ttu-id="63839-103">컴파일된 정규식의 어셈블리가 .NET Framework 4.5로 빌드되었지만 .NET Framework 4를 대상으로 하는 경우, .NET Framework 4가 설치된 시스템에서 해당 어셈블리의 정규식 중 하나를 사용하려고 하면 예외가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="63839-103">If an assembly of compiled regular expressions is built with the .NET Framework 4.5 but targets the .NET Framework 4, attempting to use one of the regular expressions in that assembly on a system with .NET Framework 4 installed throws an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="63839-104">제안 해결 방법</span><span class="sxs-lookup"><span data-stu-id="63839-104">Suggestion</span></span>

<span data-ttu-id="63839-105">이 문제를 해결하기 위해서는 다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="63839-105">To work around this problem, you can do either of the following:</span></span><ul><li><span data-ttu-id="63839-106">.NET Framework 4를 사용하여 정규식이 포함된 어셈블리를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="63839-106">Build the assembly that contains the regular expressions with the .NET Framework 4.</span></span></li><li><span data-ttu-id="63839-107">해석된 정규식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="63839-107">Use an interpreted regular expression.</span></span></li></ul>

| <span data-ttu-id="63839-108">이름</span><span class="sxs-lookup"><span data-stu-id="63839-108">Name</span></span>    | <span data-ttu-id="63839-109">값</span><span class="sxs-lookup"><span data-stu-id="63839-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="63839-110">Scope</span><span class="sxs-lookup"><span data-stu-id="63839-110">Scope</span></span>   |<span data-ttu-id="63839-111">부</span><span class="sxs-lookup"><span data-stu-id="63839-111">Minor</span></span>|
|<span data-ttu-id="63839-112">버전</span><span class="sxs-lookup"><span data-stu-id="63839-112">Version</span></span>|<span data-ttu-id="63839-113">4.5</span><span class="sxs-lookup"><span data-stu-id="63839-113">4.5</span></span>|
|<span data-ttu-id="63839-114">형식</span><span class="sxs-lookup"><span data-stu-id="63839-114">Type</span></span>|<span data-ttu-id="63839-115">런타임</span><span class="sxs-lookup"><span data-stu-id="63839-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="63839-116">영향을 받는 API</span><span class="sxs-lookup"><span data-stu-id="63839-116">Affected APIs</span></span>

-<xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName)?displayProperty=nameWithType></li><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[])?displayProperty=nameWithType></li><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[],System.String)?displayProperty=nameWithType></li></ul>|
