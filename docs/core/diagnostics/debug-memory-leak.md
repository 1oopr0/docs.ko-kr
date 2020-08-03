---
title: 메모리 누수 디버그 자습서
description: .NET Core의 메모리 누수를 디버그하는 방법을 알아봅니다.
ms.topic: tutorial
ms.date: 04/20/2020
ms.openlocfilehash: ff684f9b9402cb8b7b648e792a1d37ddcc96b399
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924892"
---
# <a name="debug-a-memory-leak-in-net-core"></a><span data-ttu-id="fa99c-103">.NET Core의 메모리 누수 디버그</span><span class="sxs-lookup"><span data-stu-id="fa99c-103">Debug a memory leak in .NET Core</span></span>

<span data-ttu-id="fa99c-104">**이 문서의 적용 대상:** ✔️ .NET Core 3.1 SDK 이상 버전</span><span class="sxs-lookup"><span data-stu-id="fa99c-104">**This article applies to:** ✔️ .NET Core 3.1 SDK and later versions</span></span>

<span data-ttu-id="fa99c-105">이 자습서에서는 .NET Core 메모리 누수를 분석하는 도구를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-105">This tutorial demonstrates the tools to analyze a .NET Core memory leak.</span></span>

<span data-ttu-id="fa99c-106">이 자습서에서는 의도적으로 메모리가 누수되도록 설계된 샘플 앱을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-106">This tutorial uses a sample app, which is designed to intentionally leak memory.</span></span> <span data-ttu-id="fa99c-107">이 샘플은 연습용으로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-107">The sample is provided as an exercise.</span></span> <span data-ttu-id="fa99c-108">의도치 않게 메모리 누수가 발생하는 앱을 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-108">You can analyze an app that is unintentionally leaking memory too.</span></span>

<span data-ttu-id="fa99c-109">이 자습서에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-109">In this tutorial, you will:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="fa99c-110">[dotnet-counters](dotnet-counters.md)를 사용하여 관리되는 메모리 사용량을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-110">Examine managed memory usage with [dotnet-counters](dotnet-counters.md).</span></span>
> - <span data-ttu-id="fa99c-111">덤프 파일을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-111">Generate a dump file.</span></span>
> - <span data-ttu-id="fa99c-112">덤프 파일을 사용하여 메모리 사용량을 분석합니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-112">Analyze the memory usage using the dump file.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fa99c-113">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="fa99c-113">Prerequisites</span></span>

<span data-ttu-id="fa99c-114">이 자습서에서는 다음을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-114">The tutorial uses:</span></span>

- <span data-ttu-id="fa99c-115">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) 이상 버전.</span><span class="sxs-lookup"><span data-stu-id="fa99c-115">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="fa99c-116">프로세스를 나열하는 [dotnet-trace](dotnet-trace.md).</span><span class="sxs-lookup"><span data-stu-id="fa99c-116">[dotnet-trace](dotnet-trace.md) to list processes.</span></span>
- <span data-ttu-id="fa99c-117">관리되는 메모리 사용량을 검사하는 [dotnet-counters](dotnet-counters.md).</span><span class="sxs-lookup"><span data-stu-id="fa99c-117">[dotnet-counters](dotnet-counters.md) to check managed memory usage.</span></span>
- <span data-ttu-id="fa99c-118">덤프 파일을 수집 및 분석하는 [dotnet-dump](dotnet-dump.md).</span><span class="sxs-lookup"><span data-stu-id="fa99c-118">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file.</span></span>
- <span data-ttu-id="fa99c-119">진단할 [샘플 디버그 대상](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) 앱.</span><span class="sxs-lookup"><span data-stu-id="fa99c-119">A [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) app to diagnose.</span></span>

<span data-ttu-id="fa99c-120">이 자습서에서는 샘플 및 도구가 설치되고 사용할 준비가 되었다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-120">The tutorial assumes the sample and tools are installed and ready to use.</span></span>

## <a name="examine-managed-memory-usage"></a><span data-ttu-id="fa99c-121">관리되는 메모리 사용량 검사</span><span class="sxs-lookup"><span data-stu-id="fa99c-121">Examine managed memory usage</span></span>

<span data-ttu-id="fa99c-122">이 시나리오의 근본 원인을 해결하는 데 도움이 되도록 진단 데이터 수집을 시작하기 전에 실제로 메모리 누수(메모리 증가)가 발생하는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-122">Before you start collecting diagnostics data to help us root cause this scenario, you need to make sure you're actually seeing a memory leak (memory growth).</span></span> <span data-ttu-id="fa99c-123">[dotnet-counters](dotnet-counters.md) 도구를 사용하여 이를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-123">You can use the [dotnet-counters](dotnet-counters.md) tool to confirm that.</span></span>

<span data-ttu-id="fa99c-124">콘솔 창을 열고 [샘플 디버그 대상](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/)을 다운로드하고 압축을 푼 디렉터리로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-124">Open a console window and navigate to the directory where you downloaded and unzipped the [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/).</span></span> <span data-ttu-id="fa99c-125">대상을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-125">Run the target:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="fa99c-126">별도의 콘솔에서 [dotnet-trace](dotnet-trace.md) 도구를 사용하여 프로세스 ID를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-126">From a separate console, find the process ID using the [dotnet-trace](dotnet-trace.md) tool:</span></span>

```console
dotnet-trace ps
```

<span data-ttu-id="fa99c-127">출력은 다음과 비슷해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-127">The output should be similar to:</span></span>

```console
4807 DiagnosticScena /home/user/git/samples/core/diagnostics/DiagnosticScenarios/bin/Debug/netcoreapp3.0/DiagnosticScenarios
```

<span data-ttu-id="fa99c-128">이제 [dotnet-counters](dotnet-counters.md) 도구를 사용하여 관리되는 메모리 사용량을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-128">Now, check managed memory usage with the [dotnet-counters](dotnet-counters.md) tool.</span></span> <span data-ttu-id="fa99c-129">`--refresh-interval`을 새로 고침 간격(초)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-129">The `--refresh-interval` specifies the number of seconds between refreshes:</span></span>

```console
dotnet-counters monitor --refresh-interval 1 -p 4807
```

<span data-ttu-id="fa99c-130">라이브 출력은 다음과 비슷해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-130">The live output should be similar to:</span></span>

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[System.Runtime]
    # of Assemblies Loaded                           118
    % Time in GC (since last GC)                       0
    Allocation Rate (Bytes / sec)                 37,896
    CPU Usage (%)                                      0
    Exceptions / sec                                   0
    GC Heap Size (MB)                                  4
    Gen 0 GC / sec                                     0
    Gen 0 Size (B)                                     0
    Gen 1 GC / sec                                     0
    Gen 1 Size (B)                                     0
    Gen 2 GC / sec                                     0
    Gen 2 Size (B)                                     0
    LOH Size (B)                                       0
    Monitor Lock Contention Count / sec                0
    Number of Active Timers                            1
    ThreadPool Completed Work Items / sec             10
    ThreadPool Queue Length                            0
    ThreadPool Threads Count                           1
    Working Set (MB)                                  83
```

<span data-ttu-id="fa99c-131">이 줄에 집중합니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-131">Focusing on this line:</span></span>

```console
    GC Heap Size (MB)                                  4
```

<span data-ttu-id="fa99c-132">시작 직후 관리되는 힙 메모리가 4MB인 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-132">You can see that the managed heap memory is 4 MB right after startup.</span></span>

<span data-ttu-id="fa99c-133">이제 URL `https://localhost:5001/api/diagscenario/memleak/20000`을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-133">Now, hit the URL `https://localhost:5001/api/diagscenario/memleak/20000`.</span></span>

<span data-ttu-id="fa99c-134">메모리 사용량이 30MB로 증가하는 것을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-134">Observe that the memory usage has grown to 30 MB.</span></span>

```console
    GC Heap Size (MB)                                 30
```

<span data-ttu-id="fa99c-135">메모리 사용량을 확인하여 메모리가 증가 또는 감소하는지를 확실히 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-135">By watching the memory usage, you can safely say that memory is growing or leaking.</span></span> <span data-ttu-id="fa99c-136">다음 단계는 메모리 분석에 적합한 데이터를 수집하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-136">The next step is to collect the right data for memory analysis.</span></span>

### <a name="generate-memory-dump"></a><span data-ttu-id="fa99c-137">메모리 덤프 생성</span><span class="sxs-lookup"><span data-stu-id="fa99c-137">Generate memory dump</span></span>

<span data-ttu-id="fa99c-138">가능한 메모리 누수를 분석할 때 앱의 메모리 힙에 액세스해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-138">When analyzing possible memory leaks, you need access to the app's memory heap.</span></span> <span data-ttu-id="fa99c-139">그런 다음 메모리 내용을 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-139">Then you can analyze the memory contents.</span></span> <span data-ttu-id="fa99c-140">개체 간의 관계를 살펴보면 메모리가 확보되지 않는 이유에 대하여 이론을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-140">Looking at relationships between objects, you create theories on why memory isn't being freed.</span></span> <span data-ttu-id="fa99c-141">일반적인 진단 데이터 원본은 Windows의 메모리 덤프 또는 Linux의 해당 코어 덤프입니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-141">A common diagnostics data source is a memory dump on Windows or the equivalent core dump on Linux.</span></span> <span data-ttu-id="fa99c-142">.NET Core 애플리케이션의 덤프를 생성하려면 [dotnet-dump)](dotnet-dump.md) 도구를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-142">To generate a dump of a .NET Core application, you can use the [dotnet-dump)](dotnet-dump.md) tool.</span></span>

<span data-ttu-id="fa99c-143">이전에 시작된 [샘플 디버그 대상](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/)을 사용하여 다음 명령을 실행하고 Linux 코어 덤프를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-143">Using the [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) previously started, run the following command to generate a Linux core dump:</span></span>

```dotnetcli
dotnet-dump collect -p 4807
```

<span data-ttu-id="fa99c-144">그 결과, 동일한 폴더에 코어 덤프가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-144">The result is a core dump located in the same folder.</span></span>

```console
Writing minidump with heap to ./core_20190430_185145
Complete
```

### <a name="restart-the-failed-process"></a><span data-ttu-id="fa99c-145">실패한 프로세스 다시 시작</span><span class="sxs-lookup"><span data-stu-id="fa99c-145">Restart the failed process</span></span>

<span data-ttu-id="fa99c-146">덤프가 수집되면 실패한 프로세스를 진단하는 데 충분한 정보가 확보될 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-146">Once the dump is collected, you should have sufficient information to diagnose the failed process.</span></span> <span data-ttu-id="fa99c-147">실패한 프로세스가 프로덕션 서버에서 실행 중이라면 프로세스를 다시 시작하여 단기 수정하기에 가장 적합한 때입니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-147">If the failed process is running on a production server, now it's the ideal time for short-term remediation by restarting the process.</span></span>

<span data-ttu-id="fa99c-148">이 자습서에서는 [샘플 디버그 대상](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/)이 완료되었으므로 이를 종료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-148">In this tutorial, you're now done with the [Sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) and you can close it.</span></span> <span data-ttu-id="fa99c-149">서버를 시작한 터미널로 이동하고 <kbd>Ctrl+C</kbd>를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-149">Navigate to the terminal that started the server, and press <kbd>Ctrl+C</kbd>.</span></span>

### <a name="analyze-the-core-dump"></a><span data-ttu-id="fa99c-150">코어 덤프 분석</span><span class="sxs-lookup"><span data-stu-id="fa99c-150">Analyze the core dump</span></span>

<span data-ttu-id="fa99c-151">이제 코어 덤프가 생성되었으므로 [dotnet-dump](dotnet-dump.md) 도구를 사용하여 덤프를 분석합니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-151">Now that you have a core dump generated, use the [dotnet-dump](dotnet-dump.md) tool to analyze the dump:</span></span>

```dotnetcli
dotnet-dump analyze core_20190430_185145
```

<span data-ttu-id="fa99c-152">여기서 `core_20190430_185145`는 분석하려는 코어 덤프의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-152">Where `core_20190430_185145` is the name of the core dump you want to analyze.</span></span>

> [!NOTE]
> <span data-ttu-id="fa99c-153">*libdl.so*를 찾을 수 없다는 오류가 표시되는 경우 *libc6-dev* 패키지를 설치해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-153">If you see an error complaining that *libdl.so* cannot be found, you may have to install the *libc6-dev* package.</span></span> <span data-ttu-id="fa99c-154">자세한 내용은 [Linux에서 .NET Core의 필수 조건](../install/dependencies.md?pivots=os-linux)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fa99c-154">For more information, see [Prerequisites for .NET Core on Linux](../install/dependencies.md?pivots=os-linux).</span></span>

<span data-ttu-id="fa99c-155">SOS 명령을 입력할 수 있는 프롬프트가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-155">You'll be presented with a prompt where you can enter SOS commands.</span></span> <span data-ttu-id="fa99c-156">일반적으로는 관리되는 힙의 전반적인 상태를 확인하는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-156">Commonly, the first thing you want to look at is the overall state of the managed heap:</span></span>

```console
> dumpheap -stat

Statistics:
              MT    Count    TotalSize Class Name
...
00007f6c1eeefba8      576        59904 System.Reflection.RuntimeMethodInfo
00007f6c1dc021c8     1749        95696 System.SByte[]
00000000008c9db0     3847       116080      Free
00007f6c1e784a18      175       128640 System.Char[]
00007f6c1dbf5510      217       133504 System.Object[]
00007f6c1dc014c0      467       416464 System.Byte[]
00007f6c21625038        6      4063376 testwebapi.Controllers.Customer[]
00007f6c20a67498   200000      4800000 testwebapi.Controllers.Customer
00007f6c1dc00f90   206770     19494060 System.String
Total 428516 objects
```

<span data-ttu-id="fa99c-157">여기에서 대부분의 개체는 `String` 또는 `Customer` 개체임을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-157">Here you can see that most objects are either `String` or `Customer` objects.</span></span>

<span data-ttu-id="fa99c-158">MT(메서드 테이블)와 함께 `dumpheap` 명령을 사용하여 모든 `String` 인스턴스의 목록을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-158">You can use the `dumpheap` command again with the method table (MT) to get a list of all the `String` instances:</span></span>

```console
> dumpheap -mt 00007faddaa50f90

         Address               MT     Size
...
00007f6ad09421f8 00007faddaa50f90       94
...
00007f6ad0965b20 00007f6c1dc00f90       80
00007f6ad0965c10 00007f6c1dc00f90       80
00007f6ad0965d00 00007f6c1dc00f90       80
00007f6ad0965df0 00007f6c1dc00f90       80
00007f6ad0965ee0 00007f6c1dc00f90       80

Statistics:
              MT    Count    TotalSize Class Name
00007f6c1dc00f90   206770     19494060 System.String
Total 206770 objects
```

<span data-ttu-id="fa99c-159">이제 `System.String` 인스턴스에 `gcroot` 명령을 사용하여 개체가 루팅된 방법과 이유를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-159">You can now use the `gcroot` command on a `System.String` instance to see how and why the object is rooted.</span></span> <span data-ttu-id="fa99c-160">이 명령은 30MB 힙까지 몇 분이 걸리므로 잠시 기다려 주세요.</span><span class="sxs-lookup"><span data-stu-id="fa99c-160">Be patient because this command takes several minutes with a 30-MB heap:</span></span>

```console
> gcroot -all 00007f6ad09421f8

Thread 3f68:
    00007F6795BB58A0 00007F6C1D7D0745 System.Diagnostics.Tracing.CounterGroup.PollForValues() [/_/src/System.Private.CoreLib/shared/System/Diagnostics/Tracing/CounterGroup.cs @ 260]
        rbx:  (interior)
            ->  00007F6BDFFFF038 System.Object[]
            ->  00007F69D0033570 testwebapi.Controllers.Processor
            ->  00007F69D0033588 testwebapi.Controllers.CustomerCache
            ->  00007F69D00335A0 System.Collections.Generic.List`1[[testwebapi.Controllers.Customer, DiagnosticScenarios]]
            ->  00007F6C000148A0 testwebapi.Controllers.Customer[]
            ->  00007F6AD0942258 testwebapi.Controllers.Customer
            ->  00007F6AD09421F8 System.String

HandleTable:
    00007F6C98BB15F8 (pinned handle)
    -> 00007F6BDFFFF038 System.Object[]
    -> 00007F69D0033570 testwebapi.Controllers.Processor
    -> 00007F69D0033588 testwebapi.Controllers.CustomerCache
    -> 00007F69D00335A0 System.Collections.Generic.List`1[[testwebapi.Controllers.Customer, DiagnosticScenarios]]
    -> 00007F6C000148A0 testwebapi.Controllers.Customer[]
    -> 00007F6AD0942258 testwebapi.Controllers.Customer
    -> 00007F6AD09421F8 System.String

Found 2 roots.
```

<span data-ttu-id="fa99c-161">`Customer` 개체에서 직접적으로, `CustomerCache` 개체에서 간접적으로 `String`을 보유하는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-161">You can see that the `String` is directly held by the `Customer` object and indirectly held by a `CustomerCache` object.</span></span>

<span data-ttu-id="fa99c-162">개체를 계속 덤프하여 대부분의 `String` 개체가 비슷한 패턴을 따르는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-162">You can continue dumping out objects to see that most `String` objects follow a similar pattern.</span></span> <span data-ttu-id="fa99c-163">이 시점에서 조사를 통해 코드에서 근본 원인을 식별하는 데 충분한 정보가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-163">At this point, the investigation provided sufficient information to identify the root cause in your code.</span></span>

<span data-ttu-id="fa99c-164">이 일반적인 절차를 사용하면 주요 메모리 누수의 원인을 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-164">This general procedure allows you to identify the source of major memory leaks.</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="fa99c-165">리소스 정리</span><span class="sxs-lookup"><span data-stu-id="fa99c-165">Clean up resources</span></span>

<span data-ttu-id="fa99c-166">이 자습서에서 샘플 웹 서버를 시작했습니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-166">In this tutorial, you started a sample web server.</span></span> <span data-ttu-id="fa99c-167">이 서버는 [실패한 프로세스 다시 시작](#restart-the-failed-process) 섹션에서 설명한 것과 같이 종료되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-167">This server should have been shut down as explained in the [Restart the failed process](#restart-the-failed-process) section.</span></span>

<span data-ttu-id="fa99c-168">또한 생성된 덤프 파일을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa99c-168">You can also delete the dump file that was created.</span></span>

## <a name="see-also"></a><span data-ttu-id="fa99c-169">참조</span><span class="sxs-lookup"><span data-stu-id="fa99c-169">See also</span></span>

- <span data-ttu-id="fa99c-170">프로세스를 나열하는 [dotnet-trace](dotnet-trace.md)</span><span class="sxs-lookup"><span data-stu-id="fa99c-170">[dotnet-trace](dotnet-trace.md) to list processes</span></span>
- <span data-ttu-id="fa99c-171">관리되는 메모리 사용량을 검사하는 [dotnet-counters](dotnet-counters.md)</span><span class="sxs-lookup"><span data-stu-id="fa99c-171">[dotnet-counters](dotnet-counters.md) to check managed memory usage</span></span>
- <span data-ttu-id="fa99c-172">덤프 파일을 수집 및 분석하는 [dotnet-dump](dotnet-dump.md)</span><span class="sxs-lookup"><span data-stu-id="fa99c-172">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file</span></span>
- [<span data-ttu-id="fa99c-173">dotnet/diagnostics</span><span class="sxs-lookup"><span data-stu-id="fa99c-173">dotnet/diagnostics</span></span>](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial)

## <a name="next-steps"></a><span data-ttu-id="fa99c-174">다음 단계</span><span class="sxs-lookup"><span data-stu-id="fa99c-174">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fa99c-175">.NET Core에서 높은 CPU 디버그</span><span class="sxs-lookup"><span data-stu-id="fa99c-175">Debug high CPU in .NET Core</span></span>](debug-highcpu.md)
