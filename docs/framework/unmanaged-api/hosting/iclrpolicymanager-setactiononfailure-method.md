---
title: ICLRPolicyManager::SetActionOnFailure 메서드
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetActionOnFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetActionOnFailure
helpviewer_keywords:
- SetActionOnFailure method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnFailure method [.NET Framework hosting]
ms.assetid: 4664033f-db97-4388-b988-2ec470796e58
topic_type:
- apiref
ms.openlocfilehash: 727cd82226b9a59c4879ffea5e87f93dd5fe38c9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504110"
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a><span data-ttu-id="b4a2e-102">ICLRPolicyManager::SetActionOnFailure 메서드</span><span class="sxs-lookup"><span data-stu-id="b4a2e-102">ICLRPolicyManager::SetActionOnFailure Method</span></span>
<span data-ttu-id="b4a2e-103">지정 된 오류가 발생할 때 CLR (공용 언어 런타임)이 수행 해야 하는 정책 동작을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4a2e-103">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4a2e-104">구문</span><span class="sxs-lookup"><span data-stu-id="b4a2e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4a2e-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="b4a2e-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="b4a2e-106">진행 작업을 수행할 실패 유형을 나타내는 [EClrFailure](eclrfailure-enumeration.md) 값 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="b4a2e-106">[in] One of the [EClrFailure](eclrfailure-enumeration.md) values, indicating the type of failure for which to take action.</span></span>  
  
 `action`  
 <span data-ttu-id="b4a2e-107">진행 오류가 발생할 때 수행할 작업을 나타내는 [EPolicyAction](epolicyaction-enumeration.md) 값 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="b4a2e-107">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action to be taken when a failure occurs.</span></span> <span data-ttu-id="b4a2e-108">지원 되는 값의 목록은 설명 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b4a2e-108">For a list of supported values, see the Remarks section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b4a2e-109">반환 값</span><span class="sxs-lookup"><span data-stu-id="b4a2e-109">Return Value</span></span>  
  
|<span data-ttu-id="b4a2e-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b4a2e-110">HRESULT</span></span>|<span data-ttu-id="b4a2e-111">설명</span><span class="sxs-lookup"><span data-stu-id="b4a2e-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b4a2e-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="b4a2e-112">S_OK</span></span>|<span data-ttu-id="b4a2e-113">`SetActionOnFailure`성공적으로 반환 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b4a2e-113">`SetActionOnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="b4a2e-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b4a2e-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b4a2e-115">CLR이 프로세스에 로드 되지 않았거나 CLR이 관리 코드를 실행할 수 없거나 호출을 성공적으로 처리할 수 없는 상태에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4a2e-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b4a2e-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b4a2e-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b4a2e-117">호출 시간이 초과 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b4a2e-117">The call timed out.</span></span>|  
|<span data-ttu-id="b4a2e-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b4a2e-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b4a2e-119">호출자가 잠금을 소유 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b4a2e-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b4a2e-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b4a2e-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b4a2e-121">차단 된 스레드나 파이버에서 대기 하는 동안 이벤트를 취소 했습니다.</span><span class="sxs-lookup"><span data-stu-id="b4a2e-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b4a2e-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b4a2e-122">E_FAIL</span></span>|<span data-ttu-id="b4a2e-123">알 수 없는 치명적인 오류가 발생 했습니다.</span><span class="sxs-lookup"><span data-stu-id="b4a2e-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b4a2e-124">메서드가 E_FAIL 반환 된 후에는 프로세스 내에서 CLR을 더 이상 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b4a2e-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b4a2e-125">호스팅 메서드를 이후에 호출 하면 HOST_E_CLRNOTAVAILABLE 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4a2e-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b4a2e-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="b4a2e-126">E_INVALIDARG</span></span>|<span data-ttu-id="b4a2e-127">지정 된 작업에 대해 정책 작업을 설정할 수 없거나 작업에 대해 잘못 된 정책 동작을 지정한 경우</span><span class="sxs-lookup"><span data-stu-id="b4a2e-127">A policy action cannot be set for the specified operation, or an invalid policy action was specified for the operation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4a2e-128">설명</span><span class="sxs-lookup"><span data-stu-id="b4a2e-128">Remarks</span></span>  
 <span data-ttu-id="b4a2e-129">기본적으로 CLR은 메모리와 같은 리소스를 할당 하지 못한 경우 예외를 throw 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4a2e-129">By default, the CLR throws an exception when it fails to allocate a resource such as memory.</span></span> <span data-ttu-id="b4a2e-130">`SetActionOnFailure`오류가 발생할 때 수행할 정책 작업을 지정 하 여 호스트가이 동작을 재정의할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4a2e-130">`SetActionOnFailure` allows the host to override this behavior by specifying the policy action to take upon failure.</span></span> <span data-ttu-id="b4a2e-131">다음 표에서는 지원 되는 [EClrFailure](eclrfailure-enumeration.md) 및 [EPolicyAction](epolicyaction-enumeration.md) 값의 조합을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b4a2e-131">The following table shows the combinations of [EClrFailure](eclrfailure-enumeration.md) and [EPolicyAction](epolicyaction-enumeration.md) values that are supported.</span></span> <span data-ttu-id="b4a2e-132">FAIL_ 접두사는 [EClrFailure](eclrfailure-enumeration.md) 값에서 생략 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4a2e-132">(The FAIL_ prefix is omitted from [EClrFailure](eclrfailure-enumeration.md) values.)</span></span>  
  
||<span data-ttu-id="b4a2e-133">NonCriticalResource</span><span class="sxs-lookup"><span data-stu-id="b4a2e-133">NonCriticalResource</span></span>|<span data-ttu-id="b4a2e-134">CriticalResource</span><span class="sxs-lookup"><span data-stu-id="b4a2e-134">CriticalResource</span></span>|<span data-ttu-id="b4a2e-135">FatalRuntime</span><span class="sxs-lookup"><span data-stu-id="b4a2e-135">FatalRuntime</span></span>|<span data-ttu-id="b4a2e-136">OrphanedLock</span><span class="sxs-lookup"><span data-stu-id="b4a2e-136">OrphanedLock</span></span>|<span data-ttu-id="b4a2e-137">StackOverflow</span><span class="sxs-lookup"><span data-stu-id="b4a2e-137">StackOverflow</span></span>|<span data-ttu-id="b4a2e-138">AccessViolation</span><span class="sxs-lookup"><span data-stu-id="b4a2e-138">AccessViolation</span></span>|<span data-ttu-id="b4a2e-139">CodeContract</span><span class="sxs-lookup"><span data-stu-id="b4a2e-139">CodeContract</span></span>|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|<span data-ttu-id="b4a2e-140">X</span><span class="sxs-lookup"><span data-stu-id="b4a2e-140">X</span></span>|<span data-ttu-id="b4a2e-141">X</span><span class="sxs-lookup"><span data-stu-id="b4a2e-141">X</span></span>||||<span data-ttu-id="b4a2e-142">해당 없음</span><span class="sxs-lookup"><span data-stu-id="b4a2e-142">N/A</span></span>||  
|<span data-ttu-id="b4a2e-143">eThrowException</span><span class="sxs-lookup"><span data-stu-id="b4a2e-143">eThrowException</span></span>|<span data-ttu-id="b4a2e-144">X</span><span class="sxs-lookup"><span data-stu-id="b4a2e-144">X</span></span>|<span data-ttu-id="b4a2e-145">X</span><span class="sxs-lookup"><span data-stu-id="b4a2e-145">X</span></span>||||<span data-ttu-id="b4a2e-146">해당 없음</span><span class="sxs-lookup"><span data-stu-id="b4a2e-146">N/A</span></span>||  
|`eAbortThread`|<span data-ttu-id="b4a2e-147">X</span><span class="sxs-lookup"><span data-stu-id="b4a2e-147">X</span></span>|<span data-ttu-id="b4a2e-148">X</span><span class="sxs-lookup"><span data-stu-id="b4a2e-148">X</span></span>||||<span data-ttu-id="b4a2e-149">해당 없음</span><span class="sxs-lookup"><span data-stu-id="b4a2e-149">N/A</span></span>|<span data-ttu-id="b4a2e-150">X</span><span class="sxs-lookup"><span data-stu-id="b4a2e-150">X</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="b4a2e-151">X</span><span class="sxs-lookup"><span data-stu-id="b4a2e-151">X</span></span>|<span data-ttu-id="b4a2e-152">X</span><span class="sxs-lookup"><span data-stu-id="b4a2e-152">X</span></span>||||<span data-ttu-id="b4a2e-153">해당 없음</span><span class="sxs-lookup"><span data-stu-id="b4a2e-153">N/A</span></span>|<span data-ttu-id="b4a2e-154">X</span><span class="sxs-lookup"><span data-stu-id="b4a2e-154">X</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="b4a2e-155">X</span><span class="sxs-lookup"><span data-stu-id="b4a2e-155">X</span></span>|<span data-ttu-id="b4a2e-156">X</span><span class="sxs-lookup"><span data-stu-id="b4a2e-156">X</span></span>||<span data-ttu-id="b4a2e-157">X</span><span class="sxs-lookup"><span data-stu-id="b4a2e-157">X</span></span>||<span data-ttu-id="b4a2e-158">해당 없음</span><span class="sxs-lookup"><span data-stu-id="b4a2e-158">N/A</span></span>|<span data-ttu-id="b4a2e-159">X</span><span class="sxs-lookup"><span data-stu-id="b4a2e-159">X</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="b4a2e-160">X</span><span class="sxs-lookup"><span data-stu-id="b4a2e-160">X</span></span>|<span data-ttu-id="b4a2e-161">X</span><span class="sxs-lookup"><span data-stu-id="b4a2e-161">X</span></span>||<span data-ttu-id="b4a2e-162">X</span><span class="sxs-lookup"><span data-stu-id="b4a2e-162">X</span></span>|<span data-ttu-id="b4a2e-163">X</span><span class="sxs-lookup"><span data-stu-id="b4a2e-163">X</span></span>|<span data-ttu-id="b4a2e-164">해당 없음</span><span class="sxs-lookup"><span data-stu-id="b4a2e-164">N/A</span></span>|<span data-ttu-id="b4a2e-165">X</span><span class="sxs-lookup"><span data-stu-id="b4a2e-165">X</span></span>|  
|`eExitProcess`|<span data-ttu-id="b4a2e-166">X</span><span class="sxs-lookup"><span data-stu-id="b4a2e-166">X</span></span>|<span data-ttu-id="b4a2e-167">X</span><span class="sxs-lookup"><span data-stu-id="b4a2e-167">X</span></span>||<span data-ttu-id="b4a2e-168">X</span><span class="sxs-lookup"><span data-stu-id="b4a2e-168">X</span></span>|<span data-ttu-id="b4a2e-169">X</span><span class="sxs-lookup"><span data-stu-id="b4a2e-169">X</span></span>|<span data-ttu-id="b4a2e-170">해당 없음</span><span class="sxs-lookup"><span data-stu-id="b4a2e-170">N/A</span></span>|<span data-ttu-id="b4a2e-171">X</span><span class="sxs-lookup"><span data-stu-id="b4a2e-171">X</span></span>|  
|<span data-ttu-id="b4a2e-172">eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="b4a2e-172">eFastExitProcess</span></span>|<span data-ttu-id="b4a2e-173">X</span><span class="sxs-lookup"><span data-stu-id="b4a2e-173">X</span></span>|<span data-ttu-id="b4a2e-174">X</span><span class="sxs-lookup"><span data-stu-id="b4a2e-174">X</span></span>||<span data-ttu-id="b4a2e-175">X</span><span class="sxs-lookup"><span data-stu-id="b4a2e-175">X</span></span>|<span data-ttu-id="b4a2e-176">X</span><span class="sxs-lookup"><span data-stu-id="b4a2e-176">X</span></span>|<span data-ttu-id="b4a2e-177">해당 없음</span><span class="sxs-lookup"><span data-stu-id="b4a2e-177">N/A</span></span>||  
|`eRudeExitProcess`|<span data-ttu-id="b4a2e-178">X</span><span class="sxs-lookup"><span data-stu-id="b4a2e-178">X</span></span>|<span data-ttu-id="b4a2e-179">X</span><span class="sxs-lookup"><span data-stu-id="b4a2e-179">X</span></span>|<span data-ttu-id="b4a2e-180">X</span><span class="sxs-lookup"><span data-stu-id="b4a2e-180">X</span></span>|<span data-ttu-id="b4a2e-181">X</span><span class="sxs-lookup"><span data-stu-id="b4a2e-181">X</span></span>|<span data-ttu-id="b4a2e-182">X</span><span class="sxs-lookup"><span data-stu-id="b4a2e-182">X</span></span>|<span data-ttu-id="b4a2e-183">해당 없음</span><span class="sxs-lookup"><span data-stu-id="b4a2e-183">N/A</span></span>||  
|`eDisableRuntime`|<span data-ttu-id="b4a2e-184">X</span><span class="sxs-lookup"><span data-stu-id="b4a2e-184">X</span></span>|<span data-ttu-id="b4a2e-185">X</span><span class="sxs-lookup"><span data-stu-id="b4a2e-185">X</span></span>|<span data-ttu-id="b4a2e-186">X</span><span class="sxs-lookup"><span data-stu-id="b4a2e-186">X</span></span>|<span data-ttu-id="b4a2e-187">X</span><span class="sxs-lookup"><span data-stu-id="b4a2e-187">X</span></span>|<span data-ttu-id="b4a2e-188">X</span><span class="sxs-lookup"><span data-stu-id="b4a2e-188">X</span></span>|<span data-ttu-id="b4a2e-189">해당 없음</span><span class="sxs-lookup"><span data-stu-id="b4a2e-189">N/A</span></span>||  
  
## <a name="requirements"></a><span data-ttu-id="b4a2e-190">요구 사항</span><span class="sxs-lookup"><span data-stu-id="b4a2e-190">Requirements</span></span>  
 <span data-ttu-id="b4a2e-191">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b4a2e-191">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4a2e-192">**헤더:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="b4a2e-192">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b4a2e-193">**라이브러리:** Mscoree.dll에 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4a2e-193">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b4a2e-194">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4a2e-194">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4a2e-195">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b4a2e-195">See also</span></span>

- [<span data-ttu-id="b4a2e-196">EClrFailure 열거형</span><span class="sxs-lookup"><span data-stu-id="b4a2e-196">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="b4a2e-197">EPolicyAction 열거형</span><span class="sxs-lookup"><span data-stu-id="b4a2e-197">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="b4a2e-198">ICLRControl 인터페이스</span><span class="sxs-lookup"><span data-stu-id="b4a2e-198">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="b4a2e-199">ICLRPolicyManager 인터페이스</span><span class="sxs-lookup"><span data-stu-id="b4a2e-199">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
