---
title: IHostTaskManager::ReverseEnterRuntime 메서드
ms.date: 03/30/2017
api_name:
- IHostTaskManager.ReverseEnterRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::ReverseEnterRuntime
helpviewer_keywords:
- IHostTaskManager::ReverseEnterRuntime method [.NET Framework hosting]
- ReverseEnterRuntime method [.NET Framework hosting]
ms.assetid: b1e26bff-d3ea-436e-9867-29720df999f4
topic_type:
- apiref
ms.openlocfilehash: 41955bd2f64d53e3620dede6b6da4cef2aab45f4
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842298"
---
# <a name="ihosttaskmanagerreverseenterruntime-method"></a><span data-ttu-id="e8aac-102">IHostTaskManager::ReverseEnterRuntime 메서드</span><span class="sxs-lookup"><span data-stu-id="e8aac-102">IHostTaskManager::ReverseEnterRuntime Method</span></span>
<span data-ttu-id="e8aac-103">비관리 코드에서 CLR (공용 언어 런타임)에 대 한 호출이 수행 되 고 있음을 호스트에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="e8aac-103">Notifies the host that a call is being made into the common language runtime (CLR) from unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8aac-104">구문</span><span class="sxs-lookup"><span data-stu-id="e8aac-104">Syntax</span></span>  
  
```cpp  
HRESULT ReverseEnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e8aac-105">Return Value</span><span class="sxs-lookup"><span data-stu-id="e8aac-105">Return Value</span></span>  
  
|<span data-ttu-id="e8aac-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e8aac-106">HRESULT</span></span>|<span data-ttu-id="e8aac-107">Description</span><span class="sxs-lookup"><span data-stu-id="e8aac-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e8aac-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="e8aac-108">S_OK</span></span>|<span data-ttu-id="e8aac-109">`ReverseEnterRuntime`성공적으로 반환 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e8aac-109">`ReverseEnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="e8aac-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e8aac-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e8aac-111">CLR이 프로세스에 로드 되지 않았거나 CLR이 관리 코드를 실행할 수 없거나 호출을 성공적으로 처리할 수 없는 상태에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8aac-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e8aac-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e8aac-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e8aac-113">호출 시간이 초과 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e8aac-113">The call timed out.</span></span>|  
|<span data-ttu-id="e8aac-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e8aac-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e8aac-115">호출자가 잠금을 소유 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8aac-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e8aac-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e8aac-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e8aac-117">차단 된 스레드나 파이버에서 대기 하는 동안 이벤트를 취소 했습니다.</span><span class="sxs-lookup"><span data-stu-id="e8aac-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e8aac-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e8aac-118">E_FAIL</span></span>|<span data-ttu-id="e8aac-119">알 수 없는 치명적인 오류가 발생 했습니다.</span><span class="sxs-lookup"><span data-stu-id="e8aac-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e8aac-120">메서드가 E_FAIL 반환 하는 경우 해당 프로세스 내에서 더 이상 CLR을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e8aac-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e8aac-121">호스팅 메서드를 이후에 호출 하면 HOST_E_CLRNOTAVAILABLE 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8aac-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e8aac-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="e8aac-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="e8aac-123">메모리가 부족 하 여 요청 된 리소스 할당을 완료할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e8aac-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8aac-124">설명</span><span class="sxs-lookup"><span data-stu-id="e8aac-124">Remarks</span></span>  
 <span data-ttu-id="e8aac-125">관리 코드에서 시작 된 시퀀스에서 CLR 호출을 수행 하는 경우에 대 한 각 호출은 `ReverseEnterRuntime` [ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md)에 대 한 호출에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8aac-125">If the call into the CLR is made from a sequence that originated in managed code, each call to `ReverseEnterRuntime` corresponds to a call to [ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e8aac-126">호출은 비관리 코드에서 중첩 되지 않고 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8aac-126">Calls can originate from unmanaged code without being nested.</span></span> <span data-ttu-id="e8aac-127">이 경우 [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](ihosttaskmanager-leaveruntime-method.md)또는에 대 한 호출이 없고,에 대 한 `ReverseLeaveRuntime` 호출 수가에 대 한 호출 수와 `ReverseEnterRuntime` 같지 않습니다 `ReverseLeaveRuntime` .</span><span class="sxs-lookup"><span data-stu-id="e8aac-127">In this case, there is no call to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](ihosttaskmanager-leaveruntime-method.md), or `ReverseLeaveRuntime`, and the number of calls to `ReverseEnterRuntime` does not equal the number of calls to `ReverseLeaveRuntime`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8aac-128">요구 사항</span><span class="sxs-lookup"><span data-stu-id="e8aac-128">Requirements</span></span>  
 <span data-ttu-id="e8aac-129">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e8aac-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8aac-130">**헤더:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="e8aac-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e8aac-131">**라이브러리:** Mscoree.dll에 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8aac-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e8aac-132">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8aac-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8aac-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e8aac-133">See also</span></span>

- [<span data-ttu-id="e8aac-134">ICLRTask 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e8aac-134">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="e8aac-135">ICLRTaskManager 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e8aac-135">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="e8aac-136">IHostTask 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e8aac-136">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="e8aac-137">IHostTaskManager 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e8aac-137">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
