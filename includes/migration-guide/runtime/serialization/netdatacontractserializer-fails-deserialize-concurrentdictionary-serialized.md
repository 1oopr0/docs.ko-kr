---
ms.openlocfilehash: 6c120f155660863ce5ae3cf5bd81ea858a68ef8d
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496507"
---
### <a name="netdatacontractserializer-fails-to-deserialize-a-concurrentdictionary-serialized-with-a-different-net-version"></a><span data-ttu-id="5d006-101">NetDataContractSerializer가 다른 .NET 버전으로 직렬화된 ConcurrentDictionary를 역직렬화하지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="5d006-101">NetDataContractSerializer fails to deserialize a ConcurrentDictionary serialized with a different .NET version</span></span>

#### <a name="details"></a><span data-ttu-id="5d006-102">설명</span><span class="sxs-lookup"><span data-stu-id="5d006-102">Details</span></span>

<span data-ttu-id="5d006-103">기본적으로 직렬화 측과 역직렬화 측이 모두 동일한 CLR 형식을 공유하는 경우에만 <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName>을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d006-103">By design, the <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> can be used only if both the serializing and deserializing ends share the same CLR types.</span></span> <span data-ttu-id="5d006-104">따라서 한 버전의 .NET Framework를 사용하여 직렬화된 개체를 다른 버전으로 역직렬화할 수 있다고 보장할 수 없습니다.<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="5d006-104">Therefore, it is not guaranteed that an object serialized with one version of the .NET Framework can be deserialized by a different version.<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName></span></span> <span data-ttu-id="5d006-105">.NET Framework 4.5 또는 이전 버전으로 직렬화되고 .NET Framework 4.5.1 이상으로 역직렬화되면 올바르게 역직렬화하지 않는 것으로 알려진 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="5d006-105">is a type that is known to not to deserialize correctly if serialized with the .NET Framework 4.5 or earlier and deserialized with the .NET Framework 4.5.1 or later.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5d006-106">제안 해결 방법</span><span class="sxs-lookup"><span data-stu-id="5d006-106">Suggestion</span></span>

<span data-ttu-id="5d006-107">이 문제에 대한 해결 방법에는 여러 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d006-107">There are a number of possible work-arounds for this issue:</span></span><ul><li><span data-ttu-id="5d006-108">.NET Framework 4.5.1도 사용하도록 직렬화 컴퓨터를 업그레이드합니다.</span><span class="sxs-lookup"><span data-stu-id="5d006-108">Upgrade the serializing computer to use the .NET Framework 4.5.1, as well.</span></span></li><li><span data-ttu-id="5d006-109">직렬화 및 역직렬화 측 모두에서 정확히 동일한 CLR 형식이 필요하지 않으므로 <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> 대신 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName>을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5d006-109">Use <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName> instead of <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> as this does not expect the exact same CLR types at both serializing and deserializing ends.</span></span></li><li><span data-ttu-id="5d006-110">이 특정 4.5-&gt;4.5.1 문제가 발생하지 않으므로 <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName> 대신 <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName>을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5d006-110">Use <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName> instead of <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName> since it does not exhibit this particular 4.5-&gt;4.5.1 break.</span></span></li></ul>

| <span data-ttu-id="5d006-111">이름</span><span class="sxs-lookup"><span data-stu-id="5d006-111">Name</span></span>    | <span data-ttu-id="5d006-112">값</span><span class="sxs-lookup"><span data-stu-id="5d006-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5d006-113">Scope</span><span class="sxs-lookup"><span data-stu-id="5d006-113">Scope</span></span>   |<span data-ttu-id="5d006-114">부</span><span class="sxs-lookup"><span data-stu-id="5d006-114">Minor</span></span>|
|<span data-ttu-id="5d006-115">버전</span><span class="sxs-lookup"><span data-stu-id="5d006-115">Version</span></span>|<span data-ttu-id="5d006-116">4.5.1</span><span class="sxs-lookup"><span data-stu-id="5d006-116">4.5.1</span></span>|
|<span data-ttu-id="5d006-117">형식</span><span class="sxs-lookup"><span data-stu-id="5d006-117">Type</span></span>|<span data-ttu-id="5d006-118">런타임</span><span class="sxs-lookup"><span data-stu-id="5d006-118">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="5d006-119">영향을 받는 API</span><span class="sxs-lookup"><span data-stu-id="5d006-119">Affected APIs</span></span>

- <xref:System.Runtime.Serialization.NetDataContractSerializer.Deserialize(System.IO.Stream)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Runtime.Serialization.NetDataContractSerializer.Deserialize(System.IO.Stream)`

-->
