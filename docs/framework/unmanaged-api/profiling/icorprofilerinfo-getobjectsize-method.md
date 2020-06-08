---
title: ICorProfilerInfo::GetObjectSize 메서드
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetObjectSize
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetObjectSize
helpviewer_keywords:
- GetObjectSize method [.NET Framework profiling]
- ICorProfilerInfo::GetObjectSize method [.NET Framework profiling]
ms.assetid: 9f02e763-73f7-42cb-a41c-f78499d9482c
topic_type:
- apiref
ms.openlocfilehash: 15c843fe138be55a3480f46e0ef8b37bcb445ad0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497974"
---
# <a name="icorprofilerinfogetobjectsize-method"></a><span data-ttu-id="f3e78-102">ICorProfilerInfo::GetObjectSize 메서드</span><span class="sxs-lookup"><span data-stu-id="f3e78-102">ICorProfilerInfo::GetObjectSize Method</span></span>
<span data-ttu-id="f3e78-103">지정 된 개체의 크기를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f3e78-103">Gets the size of a specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3e78-104">구문</span><span class="sxs-lookup"><span data-stu-id="f3e78-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3e78-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f3e78-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="f3e78-106">진행 개체의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="f3e78-106">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="f3e78-107">제한이 개체의 크기 (바이트)에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f3e78-107">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3e78-108">설명</span><span class="sxs-lookup"><span data-stu-id="f3e78-108">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f3e78-109">이 메서드는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f3e78-109">This method is obsolete.</span></span> <span data-ttu-id="f3e78-110">64 비트 플랫폼에서 4GB 보다 큰 개체에 대 한 COR_E_OVERFLOW를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3e78-110">It returns COR_E_OVERFLOW for objects greater than 4GB on 64-bit platforms.</span></span> <span data-ttu-id="f3e78-111">대신 [ICorProfilerInfo4:: GetObjectSize2](icorprofilerinfo4-getobjectsize2-method.md) 메서드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3e78-111">Use the  [ICorProfilerInfo4::GetObjectSize2](icorprofilerinfo4-getobjectsize2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="f3e78-112">동일한 유형의 개체 마다 크기가 같은 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="f3e78-112">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="f3e78-113">그러나 배열 또는 문자열과 같은 일부 형식에는 각 개체에 대해 다른 크기를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3e78-113">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
 <span data-ttu-id="f3e78-114">메서드에서 반환 되는 크기에는 `GetObjectSize` 개체가 가비지 컬렉션 힙에 있는 후에 나타날 수 있는 맞춤 패딩이 포함 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f3e78-114">The size returned by the `GetObjectSize` method does not include any alignment padding that may appear after the object is on the garbage collection heap.</span></span> <span data-ttu-id="f3e78-115">메서드를 사용 하 여 `GetObjectSize` 가비지 수집 힙의 개체에서 개체로 이동 하는 경우 필요에 따라 맞춤 안쪽 여백을 수동으로 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3e78-115">If you use the `GetObjectSize` method to advance from object to object on the garbage collection heap, add alignment padding manually, as necessary.</span></span>  
  
- <span data-ttu-id="f3e78-116">32 비트 Windows, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1 및 COR_PRF_GC_GEN_2 4 바이트 맞춤을 사용 하 고 COR_PRF_GC_LARGE_OBJECT_HEAP에서는 8 바이트 맞춤을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3e78-116">On 32-bit Windows, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1, and COR_PRF_GC_GEN_2 use 4-byte alignment, and COR_PRF_GC_LARGE_OBJECT_HEAP uses 8-byte alignment.</span></span>  
  
- <span data-ttu-id="f3e78-117">64 비트 Windows에서는 맞춤이 항상 8 바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="f3e78-117">On 64-bit Windows, the alignment is always 8 bytes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3e78-118">요구 사항</span><span class="sxs-lookup"><span data-stu-id="f3e78-118">Requirements</span></span>  
 <span data-ttu-id="f3e78-119">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f3e78-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3e78-120">**헤더:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f3e78-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f3e78-121">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f3e78-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3e78-122">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3e78-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3e78-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f3e78-123">See also</span></span>

- [<span data-ttu-id="f3e78-124">ICorProfilerInfo 인터페이스</span><span class="sxs-lookup"><span data-stu-id="f3e78-124">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
