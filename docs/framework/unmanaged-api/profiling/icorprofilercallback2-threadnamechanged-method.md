---
title: ICorProfilerCallback2::ThreadNameChanged 메서드
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.ThreadNameChanged
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::ThreadNameChanged
helpviewer_keywords:
- ThreadNameChanged method [.NET Framework profiling]
- ICorProfilerCallback2::ThreadNameChanged method [.NET Framework profiling]
ms.assetid: c8bbd76d-a9ff-44f2-87a6-be052819da36
topic_type:
- apiref
ms.openlocfilehash: 3eb108ed20d0fd1287cb82eb4d552206aeae15d4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499729"
---
# <a name="icorprofilercallback2threadnamechanged-method"></a><span data-ttu-id="63cd0-102">ICorProfilerCallback2::ThreadNameChanged 메서드</span><span class="sxs-lookup"><span data-stu-id="63cd0-102">ICorProfilerCallback2::ThreadNameChanged Method</span></span>
<span data-ttu-id="63cd0-103">스레드의 이름이 변경 되었음을 코드 프로파일러에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="63cd0-103">Notifies the code profiler that the name of a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63cd0-104">구문</span><span class="sxs-lookup"><span data-stu-id="63cd0-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadNameChanged(  
    [in] ThreadID threadId,  
    [in] ULONG cchName,  
    [in] WCHAR name[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63cd0-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="63cd0-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="63cd0-106">진행 스레드의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="63cd0-106">[in] The ID of the thread.</span></span>  
  
 `cchName`  
 <span data-ttu-id="63cd0-107">진행 스레드의 새 이름 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="63cd0-107">[in] The length of the new name of the thread.</span></span>  
  
 `name`  
 <span data-ttu-id="63cd0-108">진행 스레드의 새 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="63cd0-108">[in] The new name of the thread.</span></span> <span data-ttu-id="63cd0-109">이름이 null로 종료 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="63cd0-109">The name is not null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63cd0-110">요구 사항</span><span class="sxs-lookup"><span data-stu-id="63cd0-110">Requirements</span></span>  
 <span data-ttu-id="63cd0-111">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="63cd0-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63cd0-112">**헤더:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="63cd0-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="63cd0-113">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63cd0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63cd0-114">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63cd0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63cd0-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="63cd0-115">See also</span></span>

- [<span data-ttu-id="63cd0-116">ICorProfilerCallback 인터페이스</span><span class="sxs-lookup"><span data-stu-id="63cd0-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="63cd0-117">ICorProfilerCallback2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="63cd0-117">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
