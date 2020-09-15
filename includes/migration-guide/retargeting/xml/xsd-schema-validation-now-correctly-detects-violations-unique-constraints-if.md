---
ms.openlocfilehash: 349854b0dec5a585990b9c5e7c0b575df5bf70f3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615727"
---
### <a name="xsd-schema-validation-now-correctly-detects-violations-of-unique-constraints-if-compound-keys-are-used-and-one-key-is-empty"></a><span data-ttu-id="5d7d3-101">복합 키를 사용하고 하나의 키가 비어 있는 경우 XSD 스키마 유효성 검사는 이제 올바르게 UNIQUE 제약 조건 위반을 감지함</span><span class="sxs-lookup"><span data-stu-id="5d7d3-101">XSD Schema validation now correctly detects violations of unique constraints if compound keys are used and one key is empty</span></span>

#### <a name="details"></a><span data-ttu-id="5d7d3-102">세부 정보</span><span class="sxs-lookup"><span data-stu-id="5d7d3-102">Details</span></span>

<span data-ttu-id="5d7d3-103">.NET Framework 4.6 이전 버전은 키 중 하나가 비어있는 경우 XSD 유효성 검사가 복합 키에서 UNIQUE 제약 조건을 감지하지 않는 버그가 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="5d7d3-103">Versions of the .NET Framework prior to 4.6 had a bug that caused XSD validation to not detect unique constraints on compound keys if one of the keys was empty.</span></span> <span data-ttu-id="5d7d3-104">.NET Framework 4.6에서 이 문제가 수정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5d7d3-104">In the .NET Framework 4.6, this issue is corrected.</span></span> <span data-ttu-id="5d7d3-105">이렇게 하면 보다 정확한 유효성 검사가 되지만 이전에 검사되었던 일부 XML이 유효성 검사되지 않는 결과를 발생시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d7d3-105">This will result in more correct validation, but it may also result in some XML not validating which previously would have.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5d7d3-106">제안 해결 방법</span><span class="sxs-lookup"><span data-stu-id="5d7d3-106">Suggestion</span></span>

<span data-ttu-id="5d7d3-107">완화된 .NET Framework 4.0 유효성 검사가 필요한 경우 유효성 검사 애플리케이션은 .NET Framework 4.5(또는 이전) 버전을 대상으로 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d7d3-107">If looser .NET Framework 4.0 validation is needed, the validating application can target version 4.5 (or earlier) of the .NET Framework.</span></span> <span data-ttu-id="5d7d3-108">하지만 .NET Framework 4.6으로 다시 대상을 지정하는 경우 중복 복합 키가 (이 문제 설명에 기술된 것처럼) 유효성 검사되지 않도록 코드 검토를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d7d3-108">When retargeting to .NET Framework 4.6, however, code review should be done to be sure that duplicate compound keys (as described in this issue's description) are not expected to validate.</span></span>

| <span data-ttu-id="5d7d3-109">이름</span><span class="sxs-lookup"><span data-stu-id="5d7d3-109">Name</span></span>    | <span data-ttu-id="5d7d3-110">값</span><span class="sxs-lookup"><span data-stu-id="5d7d3-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5d7d3-111">Scope</span><span class="sxs-lookup"><span data-stu-id="5d7d3-111">Scope</span></span>   | <span data-ttu-id="5d7d3-112">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="5d7d3-112">Edge</span></span>        |
| <span data-ttu-id="5d7d3-113">버전</span><span class="sxs-lookup"><span data-stu-id="5d7d3-113">Version</span></span> | <span data-ttu-id="5d7d3-114">4.6</span><span class="sxs-lookup"><span data-stu-id="5d7d3-114">4.6</span></span>         |
| <span data-ttu-id="5d7d3-115">형식</span><span class="sxs-lookup"><span data-stu-id="5d7d3-115">Type</span></span>    | <span data-ttu-id="5d7d3-116">대상 변경</span><span class="sxs-lookup"><span data-stu-id="5d7d3-116">Retargeting</span></span> |
