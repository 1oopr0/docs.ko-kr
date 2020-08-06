---
title: dotnet-trace 도구 - .NET Core
description: dotnet-trace 명령줄 도구를 설치하고 사용합니다.
ms.date: 11/21/2019
ms.openlocfilehash: 25178a0e59ce9edb69d15ee761c1b9e56aa5eb3a
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517310"
---
# <a name="dotnet-trace-performance-analysis-utility"></a><span data-ttu-id="a7012-103">dotnet-trace 성능 분석 유틸리티</span><span class="sxs-lookup"><span data-stu-id="a7012-103">dotnet-trace performance analysis utility</span></span>

<span data-ttu-id="a7012-104">**이 문서의 적용 대상:**  ✔️ .NET Core 3.0 SDK 이상 버전</span><span class="sxs-lookup"><span data-stu-id="a7012-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-trace"></a><span data-ttu-id="a7012-105">dotnet-trace 설치</span><span class="sxs-lookup"><span data-stu-id="a7012-105">Install dotnet-trace</span></span>

<span data-ttu-id="a7012-106">[dotnet tool install](../tools/dotnet-tool-install.md) 명령으로 `dotnet-trace`[NuGet 패키지](https://www.nuget.org/packages/dotnet-trace) 설치:</span><span class="sxs-lookup"><span data-stu-id="a7012-106">Install `dotnet-trace` [NuGet package](https://www.nuget.org/packages/dotnet-trace) with the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a><span data-ttu-id="a7012-107">개요</span><span class="sxs-lookup"><span data-stu-id="a7012-107">Synopsis</span></span>

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="a7012-108">설명</span><span class="sxs-lookup"><span data-stu-id="a7012-108">Description</span></span>

<span data-ttu-id="a7012-109">`dotnet-trace` 도구:</span><span class="sxs-lookup"><span data-stu-id="a7012-109">The `dotnet-trace` tool:</span></span>

* <span data-ttu-id="a7012-110">크로스 플랫폼 .NET Core 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-110">Is a cross-platform .NET Core tool.</span></span>
* <span data-ttu-id="a7012-111">네이티브 프로파일러 없이 실행 중인 프로세스의 .NET Core 추적을 수집할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-111">Enables the collection of .NET Core traces of a running process without a native profiler.</span></span>
* <span data-ttu-id="a7012-112">.NET Core 런타임의 크로스 플랫폼 `EventPipe` 기술을 기반으로 하여 빌드되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-112">Is built around the cross-platform `EventPipe` technology of the .NET Core runtime.</span></span>
* <span data-ttu-id="a7012-113">Windows, Linux 또는 macOS에서 동일한 환경을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-113">Delivers the same experience on Windows, Linux, or macOS.</span></span>

## <a name="options"></a><span data-ttu-id="a7012-114">옵션</span><span class="sxs-lookup"><span data-stu-id="a7012-114">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="a7012-115">명령줄 도움말을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-115">Shows command-line help.</span></span>

- **`--version`**

  <span data-ttu-id="a7012-116">dotnet-trace 유틸리티의 버전을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-116">Displays the version of the dotnet-trace utility.</span></span>

## <a name="commands"></a><span data-ttu-id="a7012-117">명령</span><span class="sxs-lookup"><span data-stu-id="a7012-117">Commands</span></span>

| <span data-ttu-id="a7012-118">명령</span><span class="sxs-lookup"><span data-stu-id="a7012-118">Command</span></span>                                                   |
|-----------------------------------------------------------|
| [<span data-ttu-id="a7012-119">dotnet-trace collect</span><span class="sxs-lookup"><span data-stu-id="a7012-119">dotnet-trace collect</span></span>](#dotnet-trace-collect)             |
| [<span data-ttu-id="a7012-120">dotnet-trace convert</span><span class="sxs-lookup"><span data-stu-id="a7012-120">dotnet-trace convert</span></span>](#dotnet-trace-convert)             |
| [<span data-ttu-id="a7012-121">dotnet-trace ps</span><span class="sxs-lookup"><span data-stu-id="a7012-121">dotnet-trace ps</span></span>](#dotnet-trace-ps)                       |
| [<span data-ttu-id="a7012-122">dotnet-trace list-profiles</span><span class="sxs-lookup"><span data-stu-id="a7012-122">dotnet-trace list-profiles</span></span>](#dotnet-trace-list-profiles) |

## <a name="dotnet-trace-collect"></a><span data-ttu-id="a7012-123">dotnet-trace collect</span><span class="sxs-lookup"><span data-stu-id="a7012-123">dotnet-trace collect</span></span>

<span data-ttu-id="a7012-124">실행 중인 프로세스에서 진단 추적을 수집합니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-124">Collects a diagnostic trace from a running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="a7012-125">개요</span><span class="sxs-lookup"><span data-stu-id="a7012-125">Synopsis</span></span>

```console
dotnet-trace collect [--buffersize <size>] [--clreventlevel <clreventlevel>] [--clrevents <clrevents>]
    [--format <Chromium|NetTrace|Speedscope>] [-h|--help]
    [-n, --name <name>]  [-o|--output <trace-file-path>] [-p|--process-id <pid>]
    [--profile <profile-name>] [--providers <list-of-comma-separated-providers>]
```

### <a name="options"></a><span data-ttu-id="a7012-126">옵션</span><span class="sxs-lookup"><span data-stu-id="a7012-126">Options</span></span>

- **`--buffersize <size>`**

  <span data-ttu-id="a7012-127">메모리 내 순환 버퍼의 크기를 MB(메가바이트) 단위로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-127">Sets the size of the in-memory circular buffer, in megabytes.</span></span> <span data-ttu-id="a7012-128">기본값은 256MB입니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-128">Default 256 MB.</span></span>

- **`--clreventlevel <clreventlevel>`**

  <span data-ttu-id="a7012-129">내보낼 CLR 이벤트의 자세한 정도입니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-129">Verbosity of CLR events to be emitted.</span></span>

- **`--clrevents <clrevents>`**

  <span data-ttu-id="a7012-130">내보낼 CLR 런타임 이벤트의 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-130">List of CLR runtime events to emit.</span></span>

- **`--format {Chromium|NetTrace|Speedscope}`**

  <span data-ttu-id="a7012-131">추적 파일 변환에 대한 출력 형식을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-131">Sets the output format for the trace file conversion.</span></span> <span data-ttu-id="a7012-132">기본값은 `NetTrace`입니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-132">The default is `NetTrace`.</span></span>

- **`-n, --name <name>`**

  <span data-ttu-id="a7012-133">추적을 수집할 프로세스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-133">The name of the process to collect the trace from.</span></span>

- **`-o|--output <trace-file-path>`**

  <span data-ttu-id="a7012-134">수집된 추적 데이터의 출력 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-134">The output path for the collected trace data.</span></span> <span data-ttu-id="a7012-135">지정하지 않으면 기본값인 `trace.nettrace`로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-135">If not specified, it defaults to `trace.nettrace`.</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="a7012-136">추적을 수집할 프로세스 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-136">The process id to collect the trace from.</span></span>

- **`--profile <profile-name>`**

  <span data-ttu-id="a7012-137">일반적인 추적 시나리오를 간략하게 지정할 수 있는 미리 정의되어 명명된 공급자 구성 세트입니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-137">A named pre-defined set of provider configurations that allows common tracing scenarios to be specified succinctly.</span></span>

- **`--providers <list-of-comma-separated-providers>`**

  <span data-ttu-id="a7012-138">사용하도록 설정할 `EventPipe` 공급자에 대한 쉼표로 구분된 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-138">A comma-separated list of `EventPipe` providers to be enabled.</span></span> <span data-ttu-id="a7012-139">이러한 공급자는 `--profile <profile-name>`에서 암시하는 모든 공급자를 보완합니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-139">These providers supplement any providers implied by `--profile <profile-name>`.</span></span> <span data-ttu-id="a7012-140">특정 공급자에 대한 불일치 항목이 있는 경우 이 구성이 프로필의 암시적 구성보다 우선합니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-140">If there's any inconsistency for a particular provider, this configuration takes precedence over the implicit configuration from the profile.</span></span>

  <span data-ttu-id="a7012-141">이 공급자 목록의 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-141">This list of providers is in the form:</span></span>

  - `Provider[,Provider]`
  - <span data-ttu-id="a7012-142">`Provider`의 형식: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`</span><span class="sxs-lookup"><span data-stu-id="a7012-142">`Provider` is in the form: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span></span>
  - <span data-ttu-id="a7012-143">`KeyValueArgs`의 형식: `[key1=value1][;key2=value2]`</span><span class="sxs-lookup"><span data-stu-id="a7012-143">`KeyValueArgs` is in the form: `[key1=value1][;key2=value2]`.</span></span>

## <a name="dotnet-trace-convert"></a><span data-ttu-id="a7012-144">dotnet-trace convert</span><span class="sxs-lookup"><span data-stu-id="a7012-144">dotnet-trace convert</span></span>

<span data-ttu-id="a7012-145">`nettrace` 추적을 대체 추적 분석 도구와 함께 사용할 대체 형식으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-145">Converts `nettrace` traces to alternate formats for use with alternate trace analysis tools.</span></span>

### <a name="synopsis"></a><span data-ttu-id="a7012-146">개요</span><span class="sxs-lookup"><span data-stu-id="a7012-146">Synopsis</span></span>

```console
dotnet-trace convert [<input-filename>] [--format <Chromium|NetTrace|Speedscope>] [-h|--help] [-o|--output <output-filename>]
```

### <a name="arguments"></a><span data-ttu-id="a7012-147">인수</span><span class="sxs-lookup"><span data-stu-id="a7012-147">Arguments</span></span>

- **`<input-filename>`**

  <span data-ttu-id="a7012-148">변환할 입력 추적 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-148">Input trace file to be converted.</span></span> <span data-ttu-id="a7012-149">기본값은 *trace.nettrace*입니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-149">Defaults to *trace.nettrace*.</span></span>

### <a name="options"></a><span data-ttu-id="a7012-150">옵션</span><span class="sxs-lookup"><span data-stu-id="a7012-150">Options</span></span>

- **`--format <Chromium|NetTrace|Speedscope>`**

  <span data-ttu-id="a7012-151">추적 파일 변환에 대한 출력 형식을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-151">Sets the output format for the trace file conversion.</span></span>

- **`-o|--output <output-filename>`**

  <span data-ttu-id="a7012-152">출력 파일 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-152">Output filename.</span></span> <span data-ttu-id="a7012-153">대상 형식의 확장명이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-153">Extension of target format will be added.</span></span>

## <a name="dotnet-trace-ps"></a><span data-ttu-id="a7012-154">dotnet-trace ps</span><span class="sxs-lookup"><span data-stu-id="a7012-154">dotnet-trace ps</span></span>

 <span data-ttu-id="a7012-155">추적을 수집할 수 있는 dotnet 프로세스를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-155">Lists the dotnet processes that traces can be collected from.</span></span>

### <a name="synopsis"></a><span data-ttu-id="a7012-156">개요</span><span class="sxs-lookup"><span data-stu-id="a7012-156">Synopsis</span></span>

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a><span data-ttu-id="a7012-157">dotnet-trace list-profiles</span><span class="sxs-lookup"><span data-stu-id="a7012-157">dotnet-trace list-profiles</span></span>

<span data-ttu-id="a7012-158">각 프로필에 있는 공급자 및 필터에 대한 설명이 포함된 미리 작성된 추적 프로필을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-158">Lists pre-built tracing profiles with a description of what providers and filters are in each profile.</span></span>

### <a name="synopsis"></a><span data-ttu-id="a7012-159">개요</span><span class="sxs-lookup"><span data-stu-id="a7012-159">Synopsis</span></span>

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a><span data-ttu-id="a7012-160">dotnet-trace로 추적 수집</span><span class="sxs-lookup"><span data-stu-id="a7012-160">Collect a trace with dotnet-trace</span></span>

<span data-ttu-id="a7012-161">`dotnet-trace`을(를) 사용하여 추적을 수집하는 방법:</span><span class="sxs-lookup"><span data-stu-id="a7012-161">To collect traces using `dotnet-trace`:</span></span>

- <span data-ttu-id="a7012-162">추적을 수집할 .NET Core 애플리케이션의 PID(프로세스 식별자)를 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-162">Get the process identifier (PID) of the .NET Core application to collect traces from.</span></span>

  - <span data-ttu-id="a7012-163">예를 들어, Windows에서 작업 관리자 또는 `tasklist` 명령을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-163">On Windows, you can use Task Manager or the `tasklist` command, for example.</span></span>
  - <span data-ttu-id="a7012-164">예를 들어, Linux에서는 `ps` 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-164">On Linux, for example, the `ps` command.</span></span>
  - [<span data-ttu-id="a7012-165">dotnet-trace ps</span><span class="sxs-lookup"><span data-stu-id="a7012-165">dotnet-trace ps</span></span>](#dotnet-trace-ps)

- <span data-ttu-id="a7012-166">다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-166">Run the following command:</span></span>

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  <span data-ttu-id="a7012-167">위의 명령은 다음과 유사한 출력을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-167">The preceding command generates output similar to the following:</span></span>

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- <span data-ttu-id="a7012-168">`<Enter>` 키를 눌러 수집을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-168">Stop collection by pressing the `<Enter>` key.</span></span> <span data-ttu-id="a7012-169">`dotnet-trace`을(를) 사용하면 *trace.nettrace* 파일의 이벤트 로깅이 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-169">`dotnet-trace` will finish logging events to the *trace.nettrace* file.</span></span>

## <a name="view-the-trace-captured-from-dotnet-trace"></a><span data-ttu-id="a7012-170">dotnet-trace에서 캡처된 추적 보기</span><span class="sxs-lookup"><span data-stu-id="a7012-170">View the trace captured from dotnet-trace</span></span>

<span data-ttu-id="a7012-171">Windows에서는 분석을 위해 [PerfView](https://github.com/microsoft/perfview)에서 *.nettrace* 파일을 볼 수 있습니다. 다른 플랫폼에서 수집된 추적의 경우, 추적 파일을 Windows 머신으로 이동하여 PerfView에서 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-171">On Windows, *.nettrace* files can be viewed on [PerfView](https://github.com/microsoft/perfview) for analysis: For traces collected on other platforms, the trace file can be moved to a Windows machine to be viewed on PerfView.</span></span>

<span data-ttu-id="a7012-172">Linux에서는 `dotnet-trace`의 출력 형식을 `speedscope`(으)로 변경하여 추적을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-172">On Linux, the trace can be viewed by changing the output format of `dotnet-trace` to `speedscope`.</span></span> <span data-ttu-id="a7012-173">출력 파일 형식은 `-f|--format` 옵션을 사용하여 변경할 수 있습니다. `-f speedscope`을(를) 사용하면 `dotnet-trace`에서 `speedscope` 파일을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-173">The output file format can be changed using the `-f|--format` option - `-f speedscope` will make `dotnet-trace` produce a `speedscope` file.</span></span> <span data-ttu-id="a7012-174">`nettrace`(기본 옵션) 및 `speedscope` 중에서 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-174">You can choose between `nettrace` (the default option) and `speedscope`.</span></span> <span data-ttu-id="a7012-175">`Speedscope` 파일은 <https://www.speedscope.app>에서 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-175">`Speedscope` files can be opened at <https://www.speedscope.app>.</span></span>

> [!NOTE]
> <span data-ttu-id="a7012-176">.NET Core 런타임은 `nettrace` 형식으로 추적을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-176">The .NET Core runtime generates traces in the `nettrace` format.</span></span> <span data-ttu-id="a7012-177">추적이 완료된 후 추적이 speedscope(지정 된 경우)로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-177">The traces are converted to speedscope (if specified) after the trace is completed.</span></span> <span data-ttu-id="a7012-178">일부 변환으로 인해 데이터가 손실될 수 있으므로 원본 `nettrace` 파일이 변환된 파일과 함께 보존됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-178">Since some conversions may result in loss of data, the original `nettrace` file is preserved next to the converted file.</span></span>

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a><span data-ttu-id="a7012-179">dotnet-trace를 사용하여 시간 경과에 따라 카운터 값 사용</span><span class="sxs-lookup"><span data-stu-id="a7012-179">Use dotnet-trace to collect counter values over time</span></span>

<span data-ttu-id="a7012-180">`dotnet-trace` 기능:</span><span class="sxs-lookup"><span data-stu-id="a7012-180">`dotnet-trace` can:</span></span>

* <span data-ttu-id="a7012-181">성능에 민감한 환경에서 기본 상태 모니터링을 위해 `EventCounter`을(를) 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-181">Use `EventCounter` for basic health monitoring in performance-sensitive environments.</span></span> <span data-ttu-id="a7012-182">예를 들어, 프로덕션 환경에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-182">For example, in production.</span></span>
* <span data-ttu-id="a7012-183">실시간으로 볼 필요가 없는 추적을 수집합니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-183">Collect traces so they don't need to be viewed in real time.</span></span>

<span data-ttu-id="a7012-184">예를 들어, 런타임 성능 카운터 값을 수집하려면 다음 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-184">For example, to collect runtime performance counter values, use the following command:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

<span data-ttu-id="a7012-185">앞의 명령은 간단한 상태 모니터링을 위해 런타임 카운터에서 초당 한 번씩 보고하도록 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-185">The preceding command tells the runtime counters to report once every second for lightweight health monitoring.</span></span> <span data-ttu-id="a7012-186">`EventCounterIntervalSec=1`을 더 높은 값(예: 60)으로 바꾸면 카운터 데이터에서 세분성이 낮은 추적을 수집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-186">Replacing `EventCounterIntervalSec=1` with a higher value (for example, 60) allows collection of a smaller trace with less granularity in the counter data.</span></span>

<span data-ttu-id="a7012-187">다음 명령은 앞의 명령보다 오버 헤드 및 추적 크기를 더 크게 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-187">The following command reduces overhead and trace size more than the preceding one:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

<span data-ttu-id="a7012-188">앞의 명령은 런타임 이벤트와 관리되는 스택 프로파일러를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-188">The preceding command disables runtime events and the managed stack profiler.</span></span>

## <a name="net-providers"></a><span data-ttu-id="a7012-189">.NET 공급자</span><span class="sxs-lookup"><span data-stu-id="a7012-189">.NET Providers</span></span>

<span data-ttu-id="a7012-190">.NET Core 런타임은 다음과 같은 .NET 공급자를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-190">The .NET Core runtime supports the following .NET providers.</span></span> <span data-ttu-id="a7012-191">.NET Core에서 동일한 키워드를 사용하여 `Event Tracing for Windows (ETW)` 및 `EventPipe` 추적을 모두 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-191">.NET Core uses the same keywords to enable both `Event Tracing for Windows (ETW)` and `EventPipe` traces.</span></span>

| <span data-ttu-id="a7012-192">공급자 이름</span><span class="sxs-lookup"><span data-stu-id="a7012-192">Provider name</span></span>                            | <span data-ttu-id="a7012-193">정보</span><span class="sxs-lookup"><span data-stu-id="a7012-193">Information</span></span> |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [<span data-ttu-id="a7012-194">런타임 공급자</span><span class="sxs-lookup"><span data-stu-id="a7012-194">The Runtime Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[<span data-ttu-id="a7012-195">CLR 런타임 키워드</span><span class="sxs-lookup"><span data-stu-id="a7012-195">CLR Runtime Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [<span data-ttu-id="a7012-196">런다운 공급자</span><span class="sxs-lookup"><span data-stu-id="a7012-196">The Rundown Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[<span data-ttu-id="a7012-197">CLR 런다운 키워드</span><span class="sxs-lookup"><span data-stu-id="a7012-197">CLR Rundown Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | <span data-ttu-id="a7012-198">샘플 프로파일러를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a7012-198">Enables the sample profiler.</span></span> |
