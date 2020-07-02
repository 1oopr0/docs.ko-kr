---
title: pInvokeStackImbalance MDA
description: 플랫폼 호출을 수행 하거나 수행할 때 액세스 위반 또는 메모리 손상 중에 활성화 될 수 있는 PInvokeStackImbalance MDA를 검토 합니다.
ms.date: 03/30/2017
helpviewer_keywords:
- signatures, platform invoke
- stack depth
- platform invoke stack imbalance
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- PInvokeStackImbalance MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: 34ddc6bd-1675-4f35-86aa-de1645d5c631
ms.openlocfilehash: 89afd3fce3f2a8bffe88d45991ceeb59fc5e5b76
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803666"
---
# <a name="pinvokestackimbalance-mda"></a><span data-ttu-id="65fbc-103">PInvokeStackImbalance MDA</span><span class="sxs-lookup"><span data-stu-id="65fbc-103">PInvokeStackImbalance MDA</span></span>

<span data-ttu-id="65fbc-104">`PInvokeStackImbalance`MDA (관리 디버깅 도우미)는 특성에 지정 된 호출 규칙 <xref:System.Runtime.InteropServices.DllImportAttribute> 및 관리 되는 시그니처의 매개 변수 선언에 따라 플랫폼 호출 후 스택 깊이가 예상 스택 깊이와 일치 하지 않음을 감지 하면 활성화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="65fbc-104">The `PInvokeStackImbalance` managed debugging assistant (MDA) is activated when the CLR detects that the stack depth after a platform invoke call does not match the expected stack depth, given the calling convention specified in the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute and the declaration of the parameters in the managed signature.</span></span>

<span data-ttu-id="65fbc-105">`PInvokeStackImbalance` MDA는 32비트 x86 플랫폼에 대해서만 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="65fbc-105">The `PInvokeStackImbalance` MDA is implemented only for 32-bit x86 platforms.</span></span>

> [!NOTE]
> <span data-ttu-id="65fbc-106">`PInvokeStackImbalance`MDA는 기본적으로 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65fbc-106">The `PInvokeStackImbalance` MDA is disabled by default.</span></span> <span data-ttu-id="65fbc-107">Visual Studio 2017 이상 버전에서 `PInvokeStackImbalance` MDA는 **예외 설정** 대화 상자의 **관리 디버깅 도우미** 목록에 표시 됩니다 ( **Debug**  >  **Windows**  >  **예외 설정**디버그를 선택 하면 표시 됨).</span><span class="sxs-lookup"><span data-stu-id="65fbc-107">In Visual Studio 2017 and later versions, the `PInvokeStackImbalance` MDA appears in the **Managed Debugging Assistants** list in the **Exception Settings** dialog box (which is displayed when you select **Debug** > **Windows** > **Exception Settings**).</span></span> <span data-ttu-id="65fbc-108">그러나 **Throw 되는 경우 중단** 확인란을 선택 하거나 선택 취소 하면 MDA가 활성화 또는 비활성화 되지 않습니다. MDA가 활성화 될 때 Visual Studio에서 예외를 throw 하는지 여부를 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="65fbc-108">However, selecting or clearing the **Break When Thrown** check box does not enable or disable the MDA; it only controls whether Visual Studio throws an exception when the MDA is activated.</span></span>

## <a name="symptoms"></a><span data-ttu-id="65fbc-109">증상</span><span class="sxs-lookup"><span data-stu-id="65fbc-109">Symptoms</span></span>

<span data-ttu-id="65fbc-110">애플리케이션이 플랫폼 호출을 수행할 때나 이후에 액세스 위반 또는 메모리 손상을 발견합니다.</span><span class="sxs-lookup"><span data-stu-id="65fbc-110">An application encounters an access violation or memory corruption when making or following a platform invoke call.</span></span>

## <a name="cause"></a><span data-ttu-id="65fbc-111">원인</span><span class="sxs-lookup"><span data-stu-id="65fbc-111">Cause</span></span>

<span data-ttu-id="65fbc-112">플랫폼 호출의 관리되는 서명이 호출되는 메서드의 관리되지 않는 서명과 일치하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65fbc-112">The managed signature of the platform invoke call might not match the unmanaged signature of the method being called.</span></span>  <span data-ttu-id="65fbc-113">이 불일치는 관리되는 서명에서 올바른 개수의 매개 변수를 선언하지 않았거나 매개 변수에 대해 적절한 크기를 지정하지 않아서 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65fbc-113">This mismatch can be caused by the managed signature not declaring the correct number of parameters or not specifying the appropriate size for the parameters.</span></span>  <span data-ttu-id="65fbc-114"><xref:System.Runtime.InteropServices.DllImportAttribute> 특성에 지정될 수 있는 호출 규칙이 관리되지 않는 호출 규칙과 일치하지 않아 MDA가 활성화될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65fbc-114">The MDA can also activate because the calling convention, possibly specified by the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute, does not match the unmanaged calling convention.</span></span>

## <a name="resolution"></a><span data-ttu-id="65fbc-115">해결 방법</span><span class="sxs-lookup"><span data-stu-id="65fbc-115">Resolution</span></span>

<span data-ttu-id="65fbc-116">관리되는 플랫폼 호출 서명과 호출 규칙을 검토하여 기본 대상의 서명 및 호출 규칙과 일치하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="65fbc-116">Review the managed platform invoke signature and calling convention to confirm it matches the signature and calling convention of the native target.</span></span>  <span data-ttu-id="65fbc-117">관리되는 측면과 관리되지 않는 측면 둘 다에서 호출 규칙을 명시적으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="65fbc-117">Try explicitly specifying the calling convention on both the managed and unmanaged sides.</span></span> <span data-ttu-id="65fbc-118">가능성은 적지만 관리되지 않는 컴파일러의 버그와 같은 다른 이유로 관리되지 않는 함수에서 스택 불균형이 발생했을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65fbc-118">It is also possible, although not as likely, that the unmanaged function unbalanced the stack for some other reason, such as a bug in the unmanaged compiler.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="65fbc-119">런타임에 대한 영향</span><span class="sxs-lookup"><span data-stu-id="65fbc-119">Effect on the Runtime</span></span>

<span data-ttu-id="65fbc-120">모든 플랫폼 호출이 CLR에서 최적화되지 않은 경로를 사용하도록 강제합니다.</span><span class="sxs-lookup"><span data-stu-id="65fbc-120">Forces all platform invoke calls to take the nonoptimized path in the CLR.</span></span>

## <a name="output"></a><span data-ttu-id="65fbc-121">출력</span><span class="sxs-lookup"><span data-stu-id="65fbc-121">Output</span></span>

<span data-ttu-id="65fbc-122">MDA 메시지는 스택 불균형을 발생시키는 플랫폼 호출 메서드 호출의 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="65fbc-122">The MDA message gives the name of the platform invoke method call that is causing the stack imbalance.</span></span> <span data-ttu-id="65fbc-123">`SampleMethod` 메서드의 플랫폼 호출 샘플 메시지는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="65fbc-123">A sample message of a platform invoke call on method `SampleMethod` is:</span></span>

<span data-ttu-id="65fbc-124">**PInvoke 함수 ' SampleMethod '에 대 한 호출이 스택에서 불균형 했습니다. 이는 관리 되는 PInvoke 서명이 관리 되지 않는 대상 시그니처와 일치 하지 않기 때문일 수 있습니다. PInvoke 시그니처의 호출 규칙 및 매개 변수가 관리 되지 않는 대상 시그니처와 일치 하는지 확인 합니다.**</span><span class="sxs-lookup"><span data-stu-id="65fbc-124">**A call to PInvoke function 'SampleMethod' has unbalanced the stack. This is likely because the managed PInvoke signature does not match the unmanaged target signature. Check that the calling convention and parameters of the PInvoke signature match the target unmanaged signature.**</span></span>

## <a name="configuration"></a><span data-ttu-id="65fbc-125">Configuration</span><span class="sxs-lookup"><span data-stu-id="65fbc-125">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <pInvokeStackImbalance />
  </assistants>
</mdaConfig>
```

## <a name="see-also"></a><span data-ttu-id="65fbc-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="65fbc-126">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="65fbc-127">관리 디버깅 도우미를 사용하여 오류 진단</span><span class="sxs-lookup"><span data-stu-id="65fbc-127">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="65fbc-128">interop 마샬링</span><span class="sxs-lookup"><span data-stu-id="65fbc-128">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
