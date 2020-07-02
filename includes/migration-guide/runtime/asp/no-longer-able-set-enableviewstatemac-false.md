---
ms.openlocfilehash: cecb7b2abd4f57fdaacb0ea373cc19dc3cd9b24a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620169"
---
### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a><span data-ttu-id="66b87-101">더 이상 EnableViewStateMac를 false로 설정할 수 없음</span><span class="sxs-lookup"><span data-stu-id="66b87-101">No longer able to set EnableViewStateMac to false</span></span>

#### <a name="details"></a><span data-ttu-id="66b87-102">설명</span><span class="sxs-lookup"><span data-stu-id="66b87-102">Details</span></span>

<span data-ttu-id="66b87-103">ASP.NET에서 개발자는 더 이상 <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> 또는 <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="66b87-103">ASP.NET no longer allows developers to specify <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> or <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>.</span></span> <span data-ttu-id="66b87-104">포함된 뷰 상태가 사용된 모든 요청에 뷰 상태 MAC(메시지 인증 코드)가 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="66b87-104">The view state message authentication code (MAC) is now enforced for all requests with embedded view state.</span></span> <span data-ttu-id="66b87-105">EnableViewStateMac 속성이 <code>false</code>로 명시적으로 설정된 앱에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="66b87-105">Only apps that explicitly set the EnableViewStateMac property to <code>false</code> are affected.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="66b87-106">제안 해결 방법</span><span class="sxs-lookup"><span data-stu-id="66b87-106">Suggestion</span></span>

<span data-ttu-id="66b87-107">EnableViewStateMac은 true로 간주되어야 하고 모든 결과 MAC 오류는(MAC 오류 원인의 세부 정보에 따른 여러 해결 방법을 포함하는 [이 지침](https://support.microsoft.com/kb/2915218)에 설명된 대로) 해결되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="66b87-107">EnableViewStateMac must be assumed to be true, and any resulting MAC errors must be resolved (as explained in [this guidance](https://support.microsoft.com/kb/2915218), which contains multiple resolutions depending on the specifics of what is causing MAC errors).</span></span>

| <span data-ttu-id="66b87-108">이름</span><span class="sxs-lookup"><span data-stu-id="66b87-108">Name</span></span>    | <span data-ttu-id="66b87-109">값</span><span class="sxs-lookup"><span data-stu-id="66b87-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="66b87-110">Scope</span><span class="sxs-lookup"><span data-stu-id="66b87-110">Scope</span></span>   |<span data-ttu-id="66b87-111">주요함</span><span class="sxs-lookup"><span data-stu-id="66b87-111">Major</span></span>|
|<span data-ttu-id="66b87-112">버전</span><span class="sxs-lookup"><span data-stu-id="66b87-112">Version</span></span>|<span data-ttu-id="66b87-113">4.5.2</span><span class="sxs-lookup"><span data-stu-id="66b87-113">4.5.2</span></span>|
|<span data-ttu-id="66b87-114">형식</span><span class="sxs-lookup"><span data-stu-id="66b87-114">Type</span></span>|<span data-ttu-id="66b87-115">런타임</span><span class="sxs-lookup"><span data-stu-id="66b87-115">Runtime</span></span>|
