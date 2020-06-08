---
title: COR_GC_STATS 구조체
ms.date: 03/30/2017
api_name:
- COR_GC_STATS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_STATS
helpviewer_keywords:
- COR_GC_STATS structure [.NET Framework hosting]
ms.assetid: 8d4ff73e-739b-40f6-9349-359fbc99c2f9
topic_type:
- apiref
ms.openlocfilehash: 7a6553de31d4f9627809af7691218c39dc734c6f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501666"
---
# <a name="cor_gc_stats-structure"></a><span data-ttu-id="52a05-102">COR_GC_STATS 구조체</span><span class="sxs-lookup"><span data-stu-id="52a05-102">COR_GC_STATS Structure</span></span>
<span data-ttu-id="52a05-103">CLR (공용 언어 런타임)의 가비지 수집 메커니즘에 대 한 통계를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="52a05-103">Provides statistics about the garbage collection mechanism of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52a05-104">구문</span><span class="sxs-lookup"><span data-stu-id="52a05-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_STATS {  
    ULONG   Flags;
    SIZE_T  ExplicitGCCount;  
    SIZE_T  GenCollectionsTaken[3];  
    SIZE_T  CommittedKBytes;
    SIZE_T  ReservedKBytes;  
    SIZE_T  Gen0HeapSizeKBytes;  
    SIZE_T  Gen1HeapSizeKBytes;  
    SIZE_T  Gen2HeapSizeKBytes;  
    SIZE_T  LargeObjectHeapSizeKBytes;  
    SIZE_T  KBytesPromotedFromGen0;  
    SIZE_T  KBytesPromotedFromGen1;  
} COR_GC_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="52a05-105">멤버</span><span class="sxs-lookup"><span data-stu-id="52a05-105">Members</span></span>  
  
|<span data-ttu-id="52a05-106">멤버</span><span class="sxs-lookup"><span data-stu-id="52a05-106">Member</span></span>|<span data-ttu-id="52a05-107">설명</span><span class="sxs-lookup"><span data-stu-id="52a05-107">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="52a05-108">계산 되 고 반환 되어야 하는 필드 값을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="52a05-108">Indicates which field values should be calculated and returned.</span></span>|  
|`ExplicitGCCount`|<span data-ttu-id="52a05-109">외부 요청에 의해 강제 적용 된 가비지 수집 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="52a05-109">Indicates the number of garbage collections that were forced by external request.</span></span>|  
|`GenCollectionsTaken`|<span data-ttu-id="52a05-110">각 세대에 대해 수행 되는 가비지 컬렉션 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="52a05-110">Indicates the number of garbage collections performed for each generation.</span></span>|  
|`CommittedKBytes`|<span data-ttu-id="52a05-111">모든 힙에서 커밋된 총 kb 수입니다.</span><span class="sxs-lookup"><span data-stu-id="52a05-111">The total number of kilobytes committed in all heaps.</span></span>|  
|`ReservedKBytes`|<span data-ttu-id="52a05-112">모든 힙에서 예약 된 총 kb 수입니다.</span><span class="sxs-lookup"><span data-stu-id="52a05-112">The total number of kilobytes reserved in all heaps.</span></span>|  
|`Gen0HeapSizeKBytes`|<span data-ttu-id="52a05-113">0 세대 힙의 크기 (kb)입니다.</span><span class="sxs-lookup"><span data-stu-id="52a05-113">The size, in kilobytes, of the generation-zero heap.</span></span>|  
|`Gen1HeapSizeKBytes`|<span data-ttu-id="52a05-114">1 세대 힙의 크기 (kb)입니다.</span><span class="sxs-lookup"><span data-stu-id="52a05-114">The size, in kilobytes, of the generation-one heap.</span></span>|  
|`Gen2HeapSizeKBytes`|<span data-ttu-id="52a05-115">2 세대 힙의 크기 (kb)입니다.</span><span class="sxs-lookup"><span data-stu-id="52a05-115">The size, in kilobytes, of the generation-two heap.</span></span>|  
|`LargeObjectHeapSizeKBytes`|<span data-ttu-id="52a05-116">큰 개체 힙의 크기 (kb)입니다.</span><span class="sxs-lookup"><span data-stu-id="52a05-116">The size, in kilobytes, of the large object heap.</span></span>|  
|`KBytesPromotedFromGen0`|<span data-ttu-id="52a05-117">0 세대에서 1 세대로 수준이 올려진 개체의 크기 (kb)입니다.</span><span class="sxs-lookup"><span data-stu-id="52a05-117">The size, in kilobytes, of the objects promoted from generation zero to generation one.</span></span>|  
|`KBytesPromotedFromGen1`|<span data-ttu-id="52a05-118">1 세대에서 2 세대로 수준이 올려진 개체의 크기 (kb)입니다.</span><span class="sxs-lookup"><span data-stu-id="52a05-118">The size, in kilobytes, of the objects promoted from generation one to generation two.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52a05-119">설명</span><span class="sxs-lookup"><span data-stu-id="52a05-119">Remarks</span></span>  
 <span data-ttu-id="52a05-120">[ICLRGCManager:: GetStats](iclrgcmanager-getstats-method.md) 메서드를 사용 하려면 `Flags` 구조체의 필드를 `COR_GC_STATS` [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) 열거형 값 중 하나 이상으로 설정 하 여 설정할 통계를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52a05-120">The [ICLRGCManager::GetStats](iclrgcmanager-getstats-method.md) method requires the `Flags` field of the `COR_GC_STATS` structure to be set to one or more values of the [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) enumeration to specify which statistics are to be set.</span></span>  
  
 <span data-ttu-id="52a05-121">다음 표에서는이 구조체에 의해 제공 되는 통계를 두 [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) 열거형 값에 `COR_GC_COUNTS` 매핑합니다 `COR_GC_MEMORYUSAGE` .</span><span class="sxs-lookup"><span data-stu-id="52a05-121">The following table maps the statistics provided by this structure to the two [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) enumeration values, `COR_GC_COUNTS` and `COR_GC_MEMORYUSAGE`.</span></span>  
  
|<span data-ttu-id="52a05-122">COR_GC_COUNTS에서 지정</span><span class="sxs-lookup"><span data-stu-id="52a05-122">Specified by COR_GC_COUNTS</span></span>|<span data-ttu-id="52a05-123">COR_GC_MEMORYUSAGE에서 지정</span><span class="sxs-lookup"><span data-stu-id="52a05-123">Specified by COR_GC_MEMORYUSAGE</span></span>|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 <span data-ttu-id="52a05-124">사용 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="52a05-124">An example of the usage is as follows:</span></span>  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="52a05-125">요구 사항</span><span class="sxs-lookup"><span data-stu-id="52a05-125">Requirements</span></span>  
 <span data-ttu-id="52a05-126">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="52a05-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52a05-127">**헤더:** GCHost</span><span class="sxs-lookup"><span data-stu-id="52a05-127">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="52a05-128">**라이브러리:** Mscoree.dll에 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="52a05-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="52a05-129">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52a05-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52a05-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="52a05-130">See also</span></span>

- [<span data-ttu-id="52a05-131">호스팅 구조체</span><span class="sxs-lookup"><span data-stu-id="52a05-131">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="52a05-132">자동 메모리 관리</span><span class="sxs-lookup"><span data-stu-id="52a05-132">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="52a05-133">가비지 수집</span><span class="sxs-lookup"><span data-stu-id="52a05-133">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
