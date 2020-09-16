---
title: ICorProfilerInfo9::GetNativeCodeStartAddresses
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetNativeCodeStartAddresses
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: ca1643dfa980fa647164accf6432082428124acb
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90541241"
---
# <a name="icorprofilerinfo9getnativecodestartaddresses-method"></a><span data-ttu-id="b67f9-102">ICorProfilerInfo9:: GetNativeCodeStartAddresses 메서드</span><span class="sxs-lookup"><span data-stu-id="b67f9-102">ICorProfilerInfo9::GetNativeCodeStartAddresses Method</span></span>

<span data-ttu-id="b67f9-103">FunctionId 및 rejitId가 지정 된 경우 현재 존재 하는이 코드의 모든 jit 컴파일된 버전의 네이티브 코드 시작 주소를 열거 합니다.</span><span class="sxs-lookup"><span data-stu-id="b67f9-103">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span>

## <a name="syntax"></a><span data-ttu-id="b67f9-104">구문</span><span class="sxs-lookup"><span data-stu-id="b67f9-104">Syntax</span></span>

```cpp
HRESULT GetNativeCodeStartAddresses( [in]  FunctionID functionID,
                                     [in]  ReJITID reJitId,
                                     [in]  ULONG32 cCodeStartAddresses,
                                     [out] ULONG32 *pcCodeStartAddresses,
                                     [out] UINT_PTR codeStartAddresses[]);
```

## <a name="parameters"></a><span data-ttu-id="b67f9-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="b67f9-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="b67f9-106">\[in] 네이티브 코드 시작 주소가 반환 되어야 하는 함수의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="b67f9-106">\[in] The ID of the function whose native code start addresses should be returned.</span></span>

- `reJitId`

  <span data-ttu-id="b67f9-107">\[in] JIT 다시 컴파일된 함수의 id입니다.</span><span class="sxs-lookup"><span data-stu-id="b67f9-107">\[in] The identity of the JIT-recompiled function.</span></span>

- `cCodeStartAddresses`

  <span data-ttu-id="b67f9-108">\[in] 배열의 최대 크기 `codeStartAddresses` 입니다.</span><span class="sxs-lookup"><span data-stu-id="b67f9-108">\[in] The maximum size of the `codeStartAddresses` array.</span></span>

- `pcCodeStartAddresses`

  <span data-ttu-id="b67f9-109">\[out] 사용 가능한 주소 수입니다.</span><span class="sxs-lookup"><span data-stu-id="b67f9-109">\[out] The number of available addresses.</span></span>

- `codeStartAddresses`

  <span data-ttu-id="b67f9-110">\[out]의 배열로 `UINT_PTR` , 각는 지정 된 함수에 대 한 네이티브 본문의 시작 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="b67f9-110">\[out] An array of `UINT_PTR`, each one of which is the start address for a native body for the specified function.</span></span>

## <a name="remarks"></a><span data-ttu-id="b67f9-111">설명</span><span class="sxs-lookup"><span data-stu-id="b67f9-111">Remarks</span></span>

<span data-ttu-id="b67f9-112">계층화 된 컴파일을 사용 하는 경우 함수에 둘 이상의 네이티브 코드 본문이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b67f9-112">When tiered compilation is enabled, a function may have more than one native code body.</span></span>

## <a name="requirements"></a><span data-ttu-id="b67f9-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="b67f9-113">Requirements</span></span>

<span data-ttu-id="b67f9-114">**플랫폼:** [.Net Core 지원 운영 체제](../../../core/install/windows.md?pivots=os-windows)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b67f9-114">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="b67f9-115">**헤더:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b67f9-115">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="b67f9-116">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b67f9-116">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="b67f9-117">**.Net 버전:**[!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b67f9-117">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="b67f9-118">참조</span><span class="sxs-lookup"><span data-stu-id="b67f9-118">See also</span></span>

- [<span data-ttu-id="b67f9-119">ICorProfilerInfo9 인터페이스</span><span class="sxs-lookup"><span data-stu-id="b67f9-119">ICorProfilerInfo9 Interface</span></span>](icorprofilerinfo9-interface.md)
