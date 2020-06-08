---
title: ICorProfilerCallback::ExceptionThrown 메서드
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionThrown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionThrown
helpviewer_keywords:
- ExceptionThrown method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionThrown method [.NET Framework profiling]
ms.assetid: f1a23f3b-ac21-4905-8abf-8ea59f15af53
topic_type:
- apiref
ms.openlocfilehash: cd8030d6e57932a4605413fc2acc25a59de6c385
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500171"
---
# <a name="icorprofilercallbackexceptionthrown-method"></a><span data-ttu-id="b62e1-102">ICorProfilerCallback::ExceptionThrown 메서드</span><span class="sxs-lookup"><span data-stu-id="b62e1-102">ICorProfilerCallback::ExceptionThrown Method</span></span>
<span data-ttu-id="b62e1-103">예외가 throw 되었음을 프로파일러에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="b62e1-103">Notifies the profiler that an exception has been thrown.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b62e1-104">이 함수는 예외가 관리 코드에 도달 하는 경우에만 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b62e1-104">This function is called only if the exception reaches managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b62e1-105">구문</span><span class="sxs-lookup"><span data-stu-id="b62e1-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionThrown(  
    [in] ObjectID thrownObjectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b62e1-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="b62e1-106">Parameters</span></span>

- `thrownObjectId`

  <span data-ttu-id="b62e1-107">\[in] 예외를 throw 한 개체의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="b62e1-107">\[in] The ID of the object that caused the exception to be thrown.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="b62e1-108">설명</span><span class="sxs-lookup"><span data-stu-id="b62e1-108">Remarks</span></span>  
 <span data-ttu-id="b62e1-109">스택은 가비지 수집을 허용 하는 상태가 아닐 수 있으므로 선점형 가비지 수집을 사용 하도록 설정할 수 없기 때문에 프로파일러는이 메서드의 구현에서 차단 해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b62e1-109">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="b62e1-110">프로파일러가 여기에서 차단 되 고 가비지 수집이 시도 되는 경우이 콜백이 반환 될 때까지 런타임이 차단 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b62e1-110">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="b62e1-111">이 메서드의 프로파일러 구현은 관리 코드를 호출 하거나 관리 되는 메모리 할당을 발생 시 키 지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b62e1-111">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b62e1-112">요구 사항</span><span class="sxs-lookup"><span data-stu-id="b62e1-112">Requirements</span></span>  
 <span data-ttu-id="b62e1-113">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b62e1-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b62e1-114">**헤더:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b62e1-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b62e1-115">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b62e1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b62e1-116">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b62e1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b62e1-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b62e1-117">See also</span></span>

- [<span data-ttu-id="b62e1-118">ICorProfilerCallback 인터페이스</span><span class="sxs-lookup"><span data-stu-id="b62e1-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
