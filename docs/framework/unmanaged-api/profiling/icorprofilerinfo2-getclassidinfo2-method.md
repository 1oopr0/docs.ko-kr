---
title: ICorProfilerInfo2::GetClassIDInfo2 메서드
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassIDInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassIDInfo2
helpviewer_keywords:
- GetClassIDInfo2 method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassIDInfo2 method [.NET Framework profiling]
ms.assetid: 0141d582-d066-4d49-8d1f-ae82129a1960
topic_type:
- apiref
ms.openlocfilehash: a33e51969dc0579d976f08470ebc6e2bcca04dd7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497168"
---
# <a name="icorprofilerinfo2getclassidinfo2-method"></a><span data-ttu-id="b321b-102">ICorProfilerInfo2::GetClassIDInfo2 메서드</span><span class="sxs-lookup"><span data-stu-id="b321b-102">ICorProfilerInfo2::GetClassIDInfo2 Method</span></span>
<span data-ttu-id="b321b-103">지정 된 클래스의 개방형 제네릭 정의, `ClassID` 부모 클래스의 및 `ClassID` 클래스의 각 형식 인수 (있는 경우)에 대 한 부모 모듈 및 메타 데이터 토큰을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b321b-103">Gets the parent module and metadata token for the open generic definition of the specified class, the `ClassID` of its parent class, and the `ClassID` for each type argument, if present, of the class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b321b-104">구문</span><span class="sxs-lookup"><span data-stu-id="b321b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassIDInfo2(  
    [in]  ClassID classId,  
    [out] ModuleID *pModuleId,  
    [out] mdTypeDef *pTypeDefToken,  
    [out] ClassID *pParentClassId,  
    [in]  ULONG32 cNumTypeArgs,  
    [out] ULONG32 *pcNumTypeArgs,  
    [out] ClassID typeArgs[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b321b-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="b321b-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="b321b-106">[in] 정보가 검색되는 클래스의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="b321b-106">[in] The ID of the class for which information will be retrieved.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="b321b-107">제한이 지정 된 클래스에 대 한 개방형 제네릭 정의의 부모 모듈 ID에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="b321b-107">[out] Pointer to the ID of the parent module for the open generic definition of the specified class.</span></span>  
  
 `pTypeDefToken`  
 <span data-ttu-id="b321b-108">제한이 지정 된 클래스의 개방형 제네릭 정의에 대 한 메타 데이터 토큰에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="b321b-108">[out] Pointer to the metadata token for the open generic definition of the specified class.</span></span>  
  
 `pParentClassId`  
 <span data-ttu-id="b321b-109">[out] 부모 클래스의 ID에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="b321b-109">[out] Pointer to the ID of the parent class.</span></span>  
  
 `cNumTypeArgs`  
 <span data-ttu-id="b321b-110">[in] `typeArgs` 배열의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="b321b-110">[in] The size of the `typeArgs` array.</span></span>  
  
 `pcNumTypeArgs`  
 <span data-ttu-id="b321b-111">[out] 사용 가능한 요소의 총수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="b321b-111">[out] Pointer to the total number of available elements.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="b321b-112">[out] 각각 클래스의 형식 인수 ID를 나타내는 `ClassID` 값의 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="b321b-112">[out] An array of `ClassID` values, each of which represents the ID of a type argument of the class.</span></span> <span data-ttu-id="b321b-113">메서드가 반환되면 `typeArgs`에 사용 가능한 `ClassID` 값이 일부 또는 모두 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="b321b-113">When the method returns, `typeArgs` will contain some or all the available `ClassID` values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b321b-114">설명</span><span class="sxs-lookup"><span data-stu-id="b321b-114">Remarks</span></span>  
 <span data-ttu-id="b321b-115">`GetClassIDInfo2`메서드는 [ICorProfilerInfo:: GetClassIDInfo](icorprofilerinfo-getclassidinfo-method.md) 메서드와 유사 하지만 `GetClassIDInfo2` 제네릭 형식에 대 한 추가 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b321b-115">The `GetClassIDInfo2` method is similar to the [ICorProfilerInfo::GetClassIDInfo](icorprofilerinfo-getclassidinfo-method.md) method, but `GetClassIDInfo2` obtains additional information about a generic type.</span></span>  
  
 <span data-ttu-id="b321b-116">프로파일러 코드는 [ICorProfilerInfo:: GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) 를 호출 하 여 지정 된 모듈에 대 한 [메타 데이터](../metadata/index.md) 인터페이스를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b321b-116">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) to obtain a [metadata](../metadata/index.md) interface for a given module.</span></span> <span data-ttu-id="b321b-117">그런 다음 `pTypeDefToken`에서 참조된 위치로 반환되는 메타데이터 토큰을 사용하여 클래스에 대한 메타데이터에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b321b-117">The metadata token that is returned to the location referenced by `pTypeDefToken` can then be used to access the metadata for the class.</span></span>  
  
 <span data-ttu-id="b321b-118">`GetClassIDInfo2`가 반환된 후 `typeArgs` 버퍼가 `ClassID` 값을 모두 포함할 수 있을 만큼 충분히 큰지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b321b-118">After `GetClassIDInfo2` returns, you must verify that the `typeArgs` buffer was large enough to contain all the `ClassID` values.</span></span> <span data-ttu-id="b321b-119">이렇게 하려면 `pcNumTypeArgs`가 가리키는 값을 `cNumTypeArgs` 매개 변수의 값과 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="b321b-119">To do this, compare the value that `pcNumTypeArgs` points to with the value of the `cNumTypeArgs` parameter.</span></span> <span data-ttu-id="b321b-120">`pcNumTypeArgs`이 `cNumTypeArgs`보다 큰 값을 가리키는 경우 더 큰 `typeArgs` 버퍼를 할당하고 `cNumTypeArgs`을 더 큰 새 크기로 업데이트한 후 `GetClassIDInfo2`를 다시 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="b321b-120">If `pcNumTypeArgs` points to a value that is larger than `cNumTypeArgs`, allocate a larger `typeArgs` buffer, update `cNumTypeArgs` with the new, larger size, and call `GetClassIDInfo2` again.</span></span>  
  
 <span data-ttu-id="b321b-121">또는 길이가 0인 `typeArgs` 버퍼로 `GetClassIDInfo2`를 먼저 호출하여 올바른 버퍼 크기를 구합니다.</span><span class="sxs-lookup"><span data-stu-id="b321b-121">Alternatively, you can first call `GetClassIDInfo2` with a zero-length `typeArgs` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="b321b-122">그런 다음 `typeArgs` 버퍼 크기를 `pcNumTypeArgs`에 반환된 값으로 설정하고 `GetClassIDInfo2`를 다시 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="b321b-122">You can then set the `typeArgs` buffer size to the value returned in `pcNumTypeArgs` and call `GetClassIDInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b321b-123">요구 사항</span><span class="sxs-lookup"><span data-stu-id="b321b-123">Requirements</span></span>  
 <span data-ttu-id="b321b-124">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b321b-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b321b-125">**헤더:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b321b-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b321b-126">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b321b-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b321b-127">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b321b-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b321b-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b321b-128">See also</span></span>

- [<span data-ttu-id="b321b-129">ICorProfilerInfo 인터페이스</span><span class="sxs-lookup"><span data-stu-id="b321b-129">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="b321b-130">ICorProfilerInfo2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="b321b-130">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
- [<span data-ttu-id="b321b-131">프로파일링 인터페이스</span><span class="sxs-lookup"><span data-stu-id="b321b-131">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="b321b-132">프로파일링</span><span class="sxs-lookup"><span data-stu-id="b321b-132">Profiling</span></span>](index.md)
