---
ms.openlocfilehash: 7e42a294b151d07a6fdc61308cdf92df7a31a1d6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614722"
---
### <a name="deflatestream-uses-native-apis-for-decompression"></a><span data-ttu-id="8261d-101">DeflateStream은 압축 풀기에 네이티브 API를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8261d-101">DeflateStream uses native APIs for decompression</span></span>

#### <a name="details"></a><span data-ttu-id="8261d-102">설명</span><span class="sxs-lookup"><span data-stu-id="8261d-102">Details</span></span>

<span data-ttu-id="8261d-103">.NET Framework 4.7.2부터 `T:System.IO.Compression.DeflateStream` 클래스에서 압축 풀기의 구현은 기본적으로 네이티브 Windows API를 사용하는 것으로 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8261d-103">Starting with the .NET Framework 4.7.2, the implementation of decompression in the `T:System.IO.Compression.DeflateStream` class has changed to use native Windows APIs by default.</span></span> <span data-ttu-id="8261d-104">일반적으로 이로 인해 성능이 크게 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="8261d-104">Typically, this results in a substantial performance improvement.</span></span> <span data-ttu-id="8261d-105">.NET Framework 버전 4.7.2 이상을 대상으로 하는 모든 .NET 애플리케이션은 네이티브 구현을 사용합니다. 이 변경 내용으로 인해 다음을 포함하여 동작에 일부 차이점이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8261d-105">All .NET applications targeting the .NET Framework version 4.7.2 or higher use the native implementation.This change might result in some differences in behavior, which include:</span></span>

- <span data-ttu-id="8261d-106">예외 메시지는 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8261d-106">Exception messages may be different.</span></span> <span data-ttu-id="8261d-107">그러나 throw된 예외의 형식은 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="8261d-107">However, the type of exception thrown remains the same.</span></span>
- <span data-ttu-id="8261d-108">작업을 완료하는 데 메모리가 충분하지 않은 것과 같은 일부 특수한 상황은 다르게 처리될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8261d-108">Some special situations, such as not having enough memory to complete an operation, may be handled differently.</span></span>
- <span data-ttu-id="8261d-109">gzip 헤더를 구문 분석하는 데 알려진 차이점이 있습니다(참고: 압축 풀기에 대한 `GZipStream` 설정만 영향을 받음).</span><span class="sxs-lookup"><span data-stu-id="8261d-109">There are known differences for parsing gzip header (note: only `GZipStream` set for decompression is affected):</span></span>
- <span data-ttu-id="8261d-110">잘못된 헤더를 구분 분석하는 경우 예외는 서로 다른 시간에 throw될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8261d-110">Exceptions when parsing invalid headers may be thrown at different times.</span></span>
- <span data-ttu-id="8261d-111">네이티브 구현은 gzip 헤더 내부의 일부 예약된 플래그에 대한 값(즉, [FLG](http://www.zlib.org/rfc-gzip.html#header-trailer))이 사양에 따라 설정되도록 적용합니다. 이로 인해 이전에 잘못된 값이 무시되었던 예외를 throw할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8261d-111">The native implementation enforces that values for some reserved flags inside the gzip header (i.e. [FLG](http://www.zlib.org/rfc-gzip.html#header-trailer)) are set according to the specification, which may cause it to throw an exception where previously invalid values were ignored.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8261d-112">제안 해결 방법</span><span class="sxs-lookup"><span data-stu-id="8261d-112">Suggestion</span></span>

<span data-ttu-id="8261d-113">네이티브 API를 사용하는 압축 풀기가 앱의 동작에 부정적으로 영향을 준 경우 app.config 파일의 `runtime` 섹션에 `Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression` 스위치를 추가하고 `true`로 설정하여 이 기능을 옵트아웃할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8261d-113">If decompression with native APIs has adversely affected the behavior of your app, you can opt out of this feature by adding the `Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression` switch to the `runtime` section of your app.config file and setting it to `true`:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression=true" />
  </runtime>
</configuration>
```

| <span data-ttu-id="8261d-114">이름</span><span class="sxs-lookup"><span data-stu-id="8261d-114">Name</span></span>    | <span data-ttu-id="8261d-115">값</span><span class="sxs-lookup"><span data-stu-id="8261d-115">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8261d-116">Scope</span><span class="sxs-lookup"><span data-stu-id="8261d-116">Scope</span></span>   | <span data-ttu-id="8261d-117">부</span><span class="sxs-lookup"><span data-stu-id="8261d-117">Minor</span></span>       |
| <span data-ttu-id="8261d-118">버전</span><span class="sxs-lookup"><span data-stu-id="8261d-118">Version</span></span> | <span data-ttu-id="8261d-119">4.7.2</span><span class="sxs-lookup"><span data-stu-id="8261d-119">4.7.2</span></span>       |
| <span data-ttu-id="8261d-120">형식</span><span class="sxs-lookup"><span data-stu-id="8261d-120">Type</span></span>    | <span data-ttu-id="8261d-121">대상 변경</span><span class="sxs-lookup"><span data-stu-id="8261d-121">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="8261d-122">영향을 받는 API</span><span class="sxs-lookup"><span data-stu-id="8261d-122">Affected APIs</span></span>

- <xref:System.IO.Compression.DeflateStream?displayProperty=nameWithType>
- <xref:System.IO.Compression.GZipStream?displayProperty=nameWithType>
