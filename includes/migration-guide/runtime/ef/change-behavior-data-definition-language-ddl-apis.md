---
ms.openlocfilehash: 4416a7c09f2d163961fe2fe3d6dfaa8bd5e66f93
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497825"
---
### <a name="change-in-behavior-in-data-definition-language-ddl-apis"></a><span data-ttu-id="c41e7-101">DDL(데이터 정의 언어) API에서 동작 변경</span><span class="sxs-lookup"><span data-stu-id="c41e7-101">Change in behavior in Data Definition Language (DDL) APIs</span></span>

#### <a name="details"></a><span data-ttu-id="c41e7-102">설명</span><span class="sxs-lookup"><span data-stu-id="c41e7-102">Details</span></span>

<span data-ttu-id="c41e7-103">AttachDBFilename이 지정되면 DDL API의 동작은 다음과 같이 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="c41e7-103">The behavior of DDL APIs when AttachDBFilename is specified has changed as follows:</span></span><ul><li><span data-ttu-id="c41e7-104">연결 문자열에 초기 카탈로그 값을 지정할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c41e7-104">Connection strings need not specify an Initial Catalog value.</span></span> <span data-ttu-id="c41e7-105">이전에는 AttachDBFilename 및 초기 카탈로그가 모두 필요했습니다.</span><span class="sxs-lookup"><span data-stu-id="c41e7-105">Previously, both AttachDBFilename and Initial Catalog were required.</span></span></li><li><span data-ttu-id="c41e7-106">AttachDBFilename 및 초기 카탈로그가 모두 지정되고 제공된 MDF 파일이 있는 경우 <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A> 메서드는 <code>true</code>를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c41e7-106">If both AttachDBFilename and Initial Catalog are specified and the given MDF file exists, the <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A> method returns <code>true</code>.</span></span> <span data-ttu-id="c41e7-107">이전에는 <code>false</code>를 반환했습니다.</span><span class="sxs-lookup"><span data-stu-id="c41e7-107">Previously, it returned <code>false</code>.</span></span></li><li><span data-ttu-id="c41e7-108">AttachDBFilename 및 초기 카탈로그가 모두 지정되고 제공된 MDF 파일이 있는 경우 <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> 메서드 호출은 파일을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="c41e7-108">If both AttachDBFilename and Initial Catalog are specified and the given MDF file exists, calling the <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> method deletes the files.</span></span></li><li><span data-ttu-id="c41e7-109">존재하지 않는 MDF 및 존재하지 않는 Initial Catalog로 연결 문자열이 AttachDBFilename 값을 지정할 때 <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A>가 호출되면, 이 메서드는 <xref:System.InvalidOperationException> 예외를 throw합니다.</span><span class="sxs-lookup"><span data-stu-id="c41e7-109">If <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> is called when the connection string specifies an AttachDBFilename value with an MDF that doesn't exist and an Initial Catalog that doesn't exist, the method throws an <xref:System.InvalidOperationException> exception.</span></span> <span data-ttu-id="c41e7-110">이전에는 <xref:System.Data.SqlClient.SqlException> 예외를 throw했습니다.</span><span class="sxs-lookup"><span data-stu-id="c41e7-110">Previously, it threw a <xref:System.Data.SqlClient.SqlException> exception.</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="c41e7-111">제안 해결 방법</span><span class="sxs-lookup"><span data-stu-id="c41e7-111">Suggestion</span></span>

<span data-ttu-id="c41e7-112">이러한 변경으로 인해 DDL API를 사용하는 도구와 애플리케이션을 보다 쉽게 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c41e7-112">These changes make it easier to build tools and applications that use the DDL APIs.</span></span> <span data-ttu-id="c41e7-113">이러한 변경 사항은 다음 시나리오에서 애플리케이션 호환성에 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c41e7-113">These changes can affect application compatibility in the following scenarios:</span></span><ul><li><span data-ttu-id="c41e7-114"><code>DROP DATABASE</code>가 <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A>를 반환할 경우 <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A>를 호출하는 대신 사용자는 <code>true</code> 명령을 직접 실행하는 코드를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="c41e7-114">The user writes code that executes a <code>DROP DATABASE</code> command directly instead of calling <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> if <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A> returns <code>true</code>.</span></span> <span data-ttu-id="c41e7-115">이는 데이터베이스가 연결되지 않았지만 MDF 파일이 있는 경우 기존 코드를 중단시킵니다.</span><span class="sxs-lookup"><span data-stu-id="c41e7-115">This breaks existing code If the database is not attached but the MDF file exists.</span></span></li><li><span data-ttu-id="c41e7-116">사용자는 <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> 메서드에서 Initial Catalog 및 MDF 파일이 없을 때 <xref:System.InvalidOperationException>이 아닌 <xref:System.Data.SqlClient.SqlException>을 throw하도록 기대되는 코드를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="c41e7-116">The user writes code that expects the <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> method to throw a <xref:System.Data.SqlClient.SqlException> rather than an <xref:System.InvalidOperationException> when the Initial Catalog and MDF file don't exist.</span></span></li></ul>

| <span data-ttu-id="c41e7-117">이름</span><span class="sxs-lookup"><span data-stu-id="c41e7-117">Name</span></span>    | <span data-ttu-id="c41e7-118">값</span><span class="sxs-lookup"><span data-stu-id="c41e7-118">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c41e7-119">Scope</span><span class="sxs-lookup"><span data-stu-id="c41e7-119">Scope</span></span>   |<span data-ttu-id="c41e7-120">부</span><span class="sxs-lookup"><span data-stu-id="c41e7-120">Minor</span></span>|
|<span data-ttu-id="c41e7-121">버전</span><span class="sxs-lookup"><span data-stu-id="c41e7-121">Version</span></span>|<span data-ttu-id="c41e7-122">4.5</span><span class="sxs-lookup"><span data-stu-id="c41e7-122">4.5</span></span>|
|<span data-ttu-id="c41e7-123">형식</span><span class="sxs-lookup"><span data-stu-id="c41e7-123">Type</span></span>|<span data-ttu-id="c41e7-124">런타임</span><span class="sxs-lookup"><span data-stu-id="c41e7-124">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="c41e7-125">영향을 받는 API</span><span class="sxs-lookup"><span data-stu-id="c41e7-125">Affected APIs</span></span>

<span data-ttu-id="c41e7-126">API 분석을 통해 검색할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c41e7-126">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
