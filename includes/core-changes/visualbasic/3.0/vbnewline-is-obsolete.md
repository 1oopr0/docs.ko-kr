---
ms.openlocfilehash: 072ed716910e2e1f1f98dbddc56d5bd097b75acc
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555914"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a><span data-ttu-id="4a953-101">Microsoft.VisualBasic.Constants.vbNewLine은 사용되지 않습니다</span><span class="sxs-lookup"><span data-stu-id="4a953-101">Microsoft.VisualBasic.Constants.vbNewLine is obsolete</span></span>

<span data-ttu-id="4a953-102"><xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> 상수는 .NET Core 3.0부터 [\[사용되지 않음\]](xref:System.ObsoleteAttribute)으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a953-102">The <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant is marked as [\[Obsolete\]](xref:System.ObsoleteAttribute) starting with .NET Core 3.0.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4a953-103">도입된 버전</span><span class="sxs-lookup"><span data-stu-id="4a953-103">Version introduced</span></span>

<span data-ttu-id="4a953-104">3.0</span><span class="sxs-lookup"><span data-stu-id="4a953-104">3.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="4a953-105">변경 내용 설명</span><span class="sxs-lookup"><span data-stu-id="4a953-105">Change description</span></span>

<span data-ttu-id="4a953-106">.NET Core 3.0부터 <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> 상수에 [Obsolete](xref:System.ObsoleteAttribute) 특성이 적용되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4a953-106">Starting with .NET Core 3.0, the [Obsolete](xref:System.ObsoleteAttribute) attribute has been applied to the <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant.</span></span> <span data-ttu-id="4a953-107">이 상수를 사용하면 컴파일러 경고가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a953-107">Use of the constant produces a compiler warning.</span></span> <span data-ttu-id="4a953-108">.NET Framework 및 .NET Core의 이전 릴리스에서는 사용되지 않음으로 표시되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="4a953-108">In .NET Framework and previous releases of .NET Core, it was not marked as obsolete.</span></span>

<span data-ttu-id="4a953-109">이 변경은 다중 플랫폼 개발 언어로 Visual Basic을 지원하기 위해 적용된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4a953-109">This change was made to support Visual Basic as a language for multi-platform development.</span></span> <span data-ttu-id="4a953-110"><xref:Microsoft.VisualBasic.Constants.vbNewLine> 상수는 Windows의 줄 바꿈 문자 시퀀스인 `\r\n`과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="4a953-110">The <xref:Microsoft.VisualBasic.Constants.vbNewLine> constant is equivalent to `\r\n`, the newline character sequence on Windows.</span></span> <span data-ttu-id="4a953-111">Unix 기반 시스템에서 줄 바꿈 문자는 `\n`입니다.</span><span class="sxs-lookup"><span data-stu-id="4a953-111">On Unix-based systems, the newline character is `\n`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4a953-112">권장 조치</span><span class="sxs-lookup"><span data-stu-id="4a953-112">Recommended action</span></span>

<span data-ttu-id="4a953-113"><xref:Microsoft.VisualBasic.Constants.vbNewLine>의 [Obsolete](xref:System.ObsoleteAttribute) 특성 메시지에는 다음 권장 사항이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a953-113">The [Obsolete](xref:System.ObsoleteAttribute) attribute message for <xref:Microsoft.VisualBasic.Constants.vbNewLine> includes the following recommendation:</span></span>

<span data-ttu-id="4a953-114">캐리지 리턴 및 줄 바꿈의 경우 <xref:Microsoft.VisualBasic.Constants.vbCrLf>를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4a953-114">For a carriage return and line feed, use <xref:Microsoft.VisualBasic.Constants.vbCrLf>.</span></span> <span data-ttu-id="4a953-115">현재 플랫폼의 줄 바꿈의 경우 <xref:System.Environment.NewLine?displayProperty=nameWithType>를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4a953-115">For the current platform's newline, use <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="4a953-116">범주</span><span class="sxs-lookup"><span data-stu-id="4a953-116">Category</span></span>

<span data-ttu-id="4a953-117">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4a953-117">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4a953-118">영향을 받는 API</span><span class="sxs-lookup"><span data-stu-id="4a953-118">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

#### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->
