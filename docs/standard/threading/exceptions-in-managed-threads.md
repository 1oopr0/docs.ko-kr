---
title: 관리되는 스레드의 예외
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- unhandled exceptions,in managed threads
- threading [.NET Framework],unhandled exceptions
- threading [.NET Framework],exceptions in managed threads
- managed threading
ms.assetid: 11294769-2e89-43cb-890e-ad4ad79cfbee
ms.openlocfilehash: 56900ddab5e1e6ee5375c8979dc19694d4ad9c54
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279700"
---
# <a name="exceptions-in-managed-threads"></a><span data-ttu-id="42e16-102">관리되는 스레드의 예외</span><span class="sxs-lookup"><span data-stu-id="42e16-102">Exceptions in Managed Threads</span></span>
<span data-ttu-id="42e16-103">NET Framework 버전 2.0부터 공용 언어 런타임을 통해 스레드에 있는 대부분의 처리되지 않은 예외가 정상적으로 진행됩니다.</span><span class="sxs-lookup"><span data-stu-id="42e16-103">Starting with the .NET Framework version 2.0, the common language runtime allows most unhandled exceptions in threads to proceed naturally.</span></span> <span data-ttu-id="42e16-104">즉, 대부분의 경우에서 처리되지 않은 예외는 애플리케이션을 종료시킵니다.</span><span class="sxs-lookup"><span data-stu-id="42e16-104">In most cases this means that the unhandled exception causes the application to terminate.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="42e16-105">이 내용은 .NET Framework 버전 1.0 및 1.1과 비교하여 크게 달라진 것으로, 여러 처리되지 않은 예외(예: 스레드 풀 스레드의 처리되지 않은 예외)에 백업을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="42e16-105">This is a significant change from the .NET Framework versions 1.0 and 1.1, which provide a backstop for many unhandled exceptions — for example, unhandled exceptions in thread pool threads.</span></span> <span data-ttu-id="42e16-106">이 항목의 뒷부분에 나오는 [이전 버전의 변경 내용](#ChangeFromPreviousVersions)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="42e16-106">See [Change from Previous Versions](#ChangeFromPreviousVersions) later in this topic.</span></span>  
  
 <span data-ttu-id="42e16-107">공용 언어 런타임은 프로그램 흐름을 제어하는 데 사용되는 처리되지 않은 예외에 백업을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="42e16-107">The common language runtime provides a backstop for certain unhandled exceptions that are used for controlling program flow:</span></span>  
  
- <span data-ttu-id="42e16-108"><xref:System.Threading.Thread.Abort%2A>가 호출되었으므로 스레드에서 <xref:System.Threading.ThreadAbortException>이 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="42e16-108">A <xref:System.Threading.ThreadAbortException> is thrown in a thread because <xref:System.Threading.Thread.Abort%2A> was called.</span></span>  
  
- <span data-ttu-id="42e16-109">스레드가 실행 중인 애플리케이션 도메인이 언로드되는 중이므로 스레드에서 <xref:System.AppDomainUnloadedException>이 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="42e16-109">An <xref:System.AppDomainUnloadedException> is thrown in a thread because the application domain in which the thread is executing is being unloaded.</span></span>  
  
- <span data-ttu-id="42e16-110">공용 언어 런타임 또는 호스트 프로세스에서 내부 예외를 throw하여 스레드를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="42e16-110">The common language runtime or a host process terminates the thread by throwing an internal exception.</span></span>  
  
 <span data-ttu-id="42e16-111">이러한 예외가 공용 언어 런타임에서 만든 스레드에서 처리되지 않는 경우 해당 예외는 스레드를 종료시키지만, 공용 언어 런타임에서 해당 예외가 계속 진행되도록 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="42e16-111">If any of these exceptions are unhandled in threads created by the common language runtime, the exception terminates the thread, but the common language runtime does not allow the exception to proceed further.</span></span>  
  
 <span data-ttu-id="42e16-112">이러한 예외가 주 스레드나 비관리 코드에서 런타임으로 들어간 스레드에서 처리되지 않는 경우 해당 예외는 정상적으로 진행되고 애플리케이션이 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="42e16-112">If these exceptions are unhandled in the main thread, or in threads that entered the runtime from unmanaged code, they proceed normally, resulting in termination of the application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="42e16-113">관리 코드가 예외 처리기를 설치하기 전에 런타임은 처리되지 않은 예외를 throw할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42e16-113">It is possible for the runtime to throw an unhandled exception before any managed code has had a chance to install an exception handler.</span></span> <span data-ttu-id="42e16-114">관리 코드가 이러한 예외를 처리하지 못하더라도 예외는 정상적으로 진행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42e16-114">Even though managed code had no chance to handle such an exception, the exception is allowed to proceed naturally.</span></span>  
  
## <a name="exposing-threading-problems-during-development"></a><span data-ttu-id="42e16-115">개발하는 동안 스레딩 문제 노출</span><span class="sxs-lookup"><span data-stu-id="42e16-115">Exposing Threading Problems During Development</span></span>  
 <span data-ttu-id="42e16-116">애플리케이션이 종료되지 않고 스레드에 오류가 발생할 수 있는 경우 심각한 프로그래밍 문제를 발견하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42e16-116">When threads are allowed to fail silently, without terminating the application, serious programming problems can go undetected.</span></span> <span data-ttu-id="42e16-117">이것은 확장된 기간 동안 실행되는 서비스와 기타 애플리케이션에 특정된 문제입니다.</span><span class="sxs-lookup"><span data-stu-id="42e16-117">This is a particular problem for services and other applications which run for extended periods.</span></span> <span data-ttu-id="42e16-118">스레드에 오류가 발생하면 프로그램 상태가 서서히 손상됩니다.</span><span class="sxs-lookup"><span data-stu-id="42e16-118">As threads fail, program state gradually becomes corrupted.</span></span> <span data-ttu-id="42e16-119">애플리케이션 성능이 저하되거나 애플리케이션이 응답하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42e16-119">Application performance may degrade, or the application might become unresponsive.</span></span>  
  
 <span data-ttu-id="42e16-120">운영 체제가 응용 프로그램을 종료시킬 때까지 스레드의 처리되지 않은 예외가 정상적으로 진행되도록 허용하면 개발이나 테스트하는 동안 이러한 문제에 노출됩니다.</span><span class="sxs-lookup"><span data-stu-id="42e16-120">Allowing unhandled exceptions in threads to proceed naturally, until the operating system terminates the program, exposes such problems during development and testing.</span></span> <span data-ttu-id="42e16-121">프로그램 종료에 대한 오류 보고서는 디버깅을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="42e16-121">Error reports on program terminations support debugging.</span></span>  
  
<a name="ChangeFromPreviousVersions"></a>
## <a name="change-from-previous-versions"></a><span data-ttu-id="42e16-122">이전 버전의 변경 내용</span><span class="sxs-lookup"><span data-stu-id="42e16-122">Change from Previous Versions</span></span>  
 <span data-ttu-id="42e16-123">가장 중대한 변경은 관리되는 스레드와 관련됩니다.</span><span class="sxs-lookup"><span data-stu-id="42e16-123">The most significant change pertains to managed threads.</span></span> <span data-ttu-id="42e16-124">NET Framework 버전 1.0 및 1.1에서는 공용 언어 런타임이 다음과 같은 상황에서 처리되지 않은 예외에 백업을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="42e16-124">In the .NET Framework versions 1.0 and 1.1, the common language runtime provides a backstop for unhandled exceptions in the following situations:</span></span>  
  
- <span data-ttu-id="42e16-125">스레드 풀 스레드에 처리되지 않은 예외가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="42e16-125">There is no such thing as an unhandled exception on a thread pool thread.</span></span> <span data-ttu-id="42e16-126">작업이 처리하지 않는 예외를 throw하는 경우 런타임은 해당 예외의 스택 추적을 콘솔에 출력한 다음 해당 스레드를 스레드 풀에 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="42e16-126">When a task throws an exception that it does not handle, the runtime prints the exception stack trace to the console and then returns the thread to the thread pool.</span></span>  
  
- <span data-ttu-id="42e16-127"><xref:System.Threading.Thread> 클래스의 <xref:System.Threading.Thread.Start%2A> 메서드를 사용하여 만들어진 스레드에는 처리되지 않은 예외가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="42e16-127">There is no such thing as an unhandled exception on a thread created with the <xref:System.Threading.Thread.Start%2A> method of the <xref:System.Threading.Thread> class.</span></span> <span data-ttu-id="42e16-128">해당 스레드에서 실행되는 코드가 처리하지 않는 예외를 throw하는 경우 런타임은 해당 예외의 스택 추적을 콘솔에 출력한 다음 해당 스레드를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="42e16-128">When code running on such a thread throws an exception that it does not handle, the runtime prints the exception stack trace to the console and then gracefully terminates the thread.</span></span>  
  
- <span data-ttu-id="42e16-129">종료자 스레드에 처리되지 않은 예외가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="42e16-129">There is no such thing as an unhandled exception on the finalizer thread.</span></span> <span data-ttu-id="42e16-130">종료자가 처리하지 않는 예외를 throw하는 경우 런타임은 해당 예외의 스택 추적을 콘솔에 출력한 다음 해당 종료자 스레드가 종료자 실행을 다시 시작하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="42e16-130">When a finalizer throws an exception that it does not handle, the runtime prints the exception stack trace to the console and then allows the finalizer thread to resume running finalizers.</span></span>  
  
 <span data-ttu-id="42e16-131">관리되는 스레드의 포그라운드 또는 백그라운드 상태가 이 동작에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="42e16-131">The foreground or background status of a managed thread does not affect this behavior.</span></span>  
  
 <span data-ttu-id="42e16-132">비관리 코드에서 발생되는 스레드의 처리되지 않은 예외의 경우 이 차이점은 더 미묘합니다.</span><span class="sxs-lookup"><span data-stu-id="42e16-132">For unhandled exceptions on threads originating in unmanaged code, the difference is more subtle.</span></span> <span data-ttu-id="42e16-133">네이티브 코드를 통해 전달된 스레드의 관리되는 예외 또는 네이티브 예외에 대해 런타임 JIT 연결 대화 상자가 운영 체제 대화 상자를 선점합니다.</span><span class="sxs-lookup"><span data-stu-id="42e16-133">The runtime JIT-attach dialog preempts the operating system dialog for managed exceptions or native exceptions on threads that have passed through native code.</span></span> <span data-ttu-id="42e16-134">모든 경우에 프로세스가 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="42e16-134">The process terminates in all cases.</span></span>  
  
### <a name="migrating-code"></a><span data-ttu-id="42e16-135">코드 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="42e16-135">Migrating Code</span></span>  
 <span data-ttu-id="42e16-136">일반적으로 변경이 되면 이전에 인식할 수 없었던 프로그래밍 문제가 노출되므로 이러한 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42e16-136">In general, the change will expose previously unrecognized programming problems so that they can be fixed.</span></span> <span data-ttu-id="42e16-137">그러나 경우에 따라 프로그래머는 스레드를 종료하기 위한 목적 등으로 런타임 백업을 활용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42e16-137">In some cases, however, programmers might have taken advantage of the runtime backstop, for example to terminate threads.</span></span> <span data-ttu-id="42e16-138">상황에 따라 프로그래머는 다음 마이그레이션 전략 중 하나를 고려해 보는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="42e16-138">Depending on the situation, they should consider one of the following migration strategies:</span></span>  
  
- <span data-ttu-id="42e16-139">코드를 재구성하여 신호를 받으면 스레드가 정상적으로 종료되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="42e16-139">Restructure the code so the thread exits gracefully when a signal is received.</span></span>  
  
- <span data-ttu-id="42e16-140"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 메서드를 사용하여 스레드를 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="42e16-140">Use the <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method to abort the thread.</span></span>  
  
- <span data-ttu-id="42e16-141">프로세스 종료가 진행될 수 있도록 스레드가 중단되어야 하는 경우 해당 스레드를 백그라운드 스레드로 만들어 프로세스가 종료되면 자동으로 종료되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="42e16-141">If a thread must be stopped so that process termination can proceed, make the thread a background thread so that it is automatically terminated on process exit.</span></span>  
  
 <span data-ttu-id="42e16-142">모든 경우에서 전략은 예외에 대한 다음 디자인 지침을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42e16-142">In all cases, the strategy should follow the design guidelines for exceptions.</span></span> <span data-ttu-id="42e16-143">[예외 디자인 지침](../design-guidelines/exceptions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="42e16-143">See [Design Guidelines for Exceptions](../design-guidelines/exceptions.md).</span></span>  
  
### <a name="application-compatibility-flag"></a><span data-ttu-id="42e16-144">애플리케이션 호환 플래그</span><span class="sxs-lookup"><span data-stu-id="42e16-144">Application Compatibility Flag</span></span>  
 <span data-ttu-id="42e16-145">임시 호환을 위해 관리자는 애플리케이션 구성 파일의 `<runtime>` 섹션에 호환 플래그를 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42e16-145">As a temporary compatibility measure, administrators can place a compatibility flag in the `<runtime>` section of the application configuration file.</span></span> <span data-ttu-id="42e16-146">이렇게 하면 공용 언어 런타임이 버전 1.0 및 1.1의 동작으로 다시 돌아옵니다.</span><span class="sxs-lookup"><span data-stu-id="42e16-146">This causes the common language runtime to revert to the behavior of versions 1.0 and 1.1.</span></span>  
  
```xml  
<legacyUnhandledExceptionPolicy enabled="1"/>  
```  
  
## <a name="host-override"></a><span data-ttu-id="42e16-147">호스트 재정의</span><span class="sxs-lookup"><span data-stu-id="42e16-147">Host Override</span></span>  
 <span data-ttu-id="42e16-148">.NET Framework 버전 2.0에서는 관리되지 않는 호스트가 호스팅 API의 [ICLRPolicyManager](../../framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) 인터페이스를 사용하여 공용 언어 런타임의 기본 처리되지 않은 예외를 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42e16-148">In the .NET Framework version 2.0, an unmanaged host can use the [ICLRPolicyManager](../../framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) interface in the Hosting API to override the default unhandled exception policy of the common language runtime.</span></span> <span data-ttu-id="42e16-149">[ICLRPolicyManager::SetUnhandledExceptionPolicy](../../framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md) 함수를 사용하여 처리되지 않은 예외에 대한 정책을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="42e16-149">The [ICLRPolicyManager::SetUnhandledExceptionPolicy](../../framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md) function is used to set the policy for unhandled exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42e16-150">참고 항목</span><span class="sxs-lookup"><span data-stu-id="42e16-150">See also</span></span>

- [<span data-ttu-id="42e16-151">관리되는 스레딩 기본 사항</span><span class="sxs-lookup"><span data-stu-id="42e16-151">Managed Threading Basics</span></span>](managed-threading-basics.md)
