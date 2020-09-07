---
ms.openlocfilehash: 450bfc56c99a3df9be71be2ef7df6e4e12d4ed76
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496694"
---
### <a name="a-concurrentdictionary-serialized-in-net-framework-45-with-netdatacontractserializer-cannot-be-deserialized-by-net-framework-451-or-452"></a><span data-ttu-id="d30e5-101">.NET Framework 4.5에서 NetDataContractSerializer로 직렬화된 ConcurrentDictionary는 .NET Framework 4.5.1 또는 4.5.2에서 역직렬화될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d30e5-101">A ConcurrentDictionary serialized in .NET Framework 4.5 with NetDataContractSerializer cannot be deserialized by .NET Framework 4.5.1 or 4.5.2</span></span>

#### <a name="details"></a><span data-ttu-id="d30e5-102">세부 정보</span><span class="sxs-lookup"><span data-stu-id="d30e5-102">Details</span></span>

<span data-ttu-id="d30e5-103">이 형식의 내부 변경 내용으로 인해 <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName>을 사용하여 .NET Framework 4.5로 직렬화된 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> 개체를 .NET Framework 4.5.1 또는 .NET Framework 4.5.2에서 역직렬화할 수 없습니다. 반대 방향의 경우(.NET Framework 4.5.x로 직렬화하고 .NET Framework 4.5로 역직렬화하는 경우)는 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="d30e5-103">Due to internal changes to the type, <xref:System.Collections.Concurrent.ConcurrentDictionary%602> objects that are serialized with the .NET Framework 4.5 using the <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> cannot be deserialized in the .NET Framework 4.5.1 or in the .NET Framework 4.5.2.Note that moving in the other direction (serializing with the .NET Framework 4.5.x and deserializing with the .NET Framework 4.5) works.</span></span> <span data-ttu-id="d30e5-104">마찬가지로 .NET Framework 4.6으로 모든 4.x 버전 간 직렬화가 실행됩니다. 단일 버전의 .NET Framework로 직렬화 및 역직렬화하는 것은 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d30e5-104">Similarly, all 4.x cross-version serialization works with the .NET Framework 4.6.Serializing and deserializing with a single version of the .NET Framework is not affected.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d30e5-105">제안 해결 방법</span><span class="sxs-lookup"><span data-stu-id="d30e5-105">Suggestion</span></span>

<span data-ttu-id="d30e5-106">.NET Framework 4.5와 .NET Framework 4.5.1/4.5.2 간에 <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName>을 직렬화 및 역직렬화해야 하는 경우 <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> 대신 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName> 또는 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> 직렬기와 같은 대체 직렬기가 사용되어야 합니다. 또는 .NET Framework 4.6에서 이 문제가 해결되므로 해당 버전의 .NET Framework로 업그레이드하여 이 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d30e5-106">If it is necessary to serialize and deserialize a <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName> between the .NET Framework 4.5 and .NET Framework 4.5.1/4.5.2, an alternate serializer like the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName> or <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> serializer should be used instead of the <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName>.Alternatively, because this issue is addressed in the .NET Framework 4.6, it may be solved by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="d30e5-107">Name</span><span class="sxs-lookup"><span data-stu-id="d30e5-107">Name</span></span>    | <span data-ttu-id="d30e5-108">값</span><span class="sxs-lookup"><span data-stu-id="d30e5-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d30e5-109">Scope</span><span class="sxs-lookup"><span data-stu-id="d30e5-109">Scope</span></span>   |<span data-ttu-id="d30e5-110">부</span><span class="sxs-lookup"><span data-stu-id="d30e5-110">Minor</span></span>|
|<span data-ttu-id="d30e5-111">버전</span><span class="sxs-lookup"><span data-stu-id="d30e5-111">Version</span></span>|<span data-ttu-id="d30e5-112">4.5.1</span><span class="sxs-lookup"><span data-stu-id="d30e5-112">4.5.1</span></span>|
|<span data-ttu-id="d30e5-113">형식</span><span class="sxs-lookup"><span data-stu-id="d30e5-113">Type</span></span>|<span data-ttu-id="d30e5-114">런타임</span><span class="sxs-lookup"><span data-stu-id="d30e5-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="d30e5-115">영향을 받는 API</span><span class="sxs-lookup"><span data-stu-id="d30e5-115">Affected APIs</span></span>

<span data-ttu-id="d30e5-116">API 분석을 통해 검색할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d30e5-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
