---
title: CLR 활성화 문제를 디버깅하는 방법
description: .NET에서 CLR(공용 언어 런타임) 활성화 문제를 디버그하는 방법을 알아봅니다. CLR 활성화 로그를 확인하고 디버그합니다. 이 로그는 근본 원인을 확인하는 데 유용할 수 있습니다.
ms.date: 03/30/2017
helpviewer_keywords:
- CLR activation, debugging issues
ms.assetid: 4fe17546-d56e-4344-a930-6d8e4a545914
ms.openlocfilehash: 5215e82aebf93fa8d6d1937563ab348126a01d97
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622616"
---
# <a name="how-to-debug-clr-activation-issues"></a><span data-ttu-id="dc87d-104">CLR 활성화 문제를 디버깅하는 방법</span><span class="sxs-lookup"><span data-stu-id="dc87d-104">How to debug CLR activation issues</span></span>

<span data-ttu-id="dc87d-105">애플리케이션이 올바른 버전의 CLR(공용 언어 런타임)로 실행되도록 하는 데 문제가 있는 경우 CLR 활성화 로그를 보고 디버그할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc87d-105">If you encounter problems in getting your application to run with the correct version of the common language runtime (CLR), you can view and debug CLR activation logs.</span></span> <span data-ttu-id="dc87d-106">이러한 로그는 애플리케이션이 예상과 다른 CLR 버전을 로드하거나 CLR을 로드하지 않을 때 활성화 문제의 근본 원인을 파악하는 데 매우 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc87d-106">These logs can be very useful in determining the root cause of an activation issue, when your application either loads a different CLR version than expected or doesn't load the CLR at all.</span></span> <span data-ttu-id="dc87d-107">[.NET Framework 초기화 오류: 사용자 경험 관리](initialization-errors-managing-the-user-experience.md)에서는 애플리케이션에 대한 CLR이 없는 경우의 경험에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="dc87d-107">The [.NET Framework Initialization Errors: Managing the User Experience](initialization-errors-managing-the-user-experience.md) discusses the experience when no CLR is found for an application.</span></span>

<span data-ttu-id="dc87d-108">HKEY_LOCAL_MACHINE 레지스트리 키 또는 시스템 환경 변수를 통해 시스템 전체에서 CLR 활성화 로깅을 사용하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc87d-108">CLR activation logging can be enabled system-wide by using an HKEY_LOCAL_MACHINE registry key or a system environment variable.</span></span> <span data-ttu-id="dc87d-109">레지스트리 항목 또는 환경 변수를 제거할 때까지 로그가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc87d-109">The log will be generated until the registry entry or the environment variable is removed.</span></span> <span data-ttu-id="dc87d-110">또는 사용자 또는 프로세스 로컬 환경 변수를 통해 다양한 범위와 기간으로 로깅을 사용하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc87d-110">Alternatively, you can use a user or process-local environment variable to enable logging with a different scope and duration.</span></span>

<span data-ttu-id="dc87d-111">CLR 활성화 로그와 [어셈블리 바인딩 로그](../tools/fuslogvw-exe-assembly-binding-log-viewer.md)는 완전히 다르므로 혼동하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc87d-111">CLR activation logs shouldn't be confused with [assembly binding logs](../tools/fuslogvw-exe-assembly-binding-log-viewer.md), which are entirely different.</span></span>

## <a name="to-enable-clr-activation-logging"></a><span data-ttu-id="dc87d-112">CLR 활성화 로깅을 사용하도록 설정하려면</span><span class="sxs-lookup"><span data-stu-id="dc87d-112">To enable CLR activation logging</span></span>

### <a name="using-the-registry"></a><span data-ttu-id="dc87d-113">레지스트리 사용</span><span class="sxs-lookup"><span data-stu-id="dc87d-113">Using the registry</span></span>

1. <span data-ttu-id="dc87d-114">레지스트리 편집기에서 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework(32비트 컴퓨터) 또는 HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework 폴더(64비트 컴퓨터)로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="dc87d-114">In the Registry Editor, navigate to HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework (on a 32-bit computer) or HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework folder (on a 64-bit computer).</span></span>

2. <span data-ttu-id="dc87d-115">`CLRLoadLogDir`이라는 문자열 값을 추가하고 CLR 활성화 로그를 저장할 기존 디렉터리의 전체 경로로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="dc87d-115">Add a string value named `CLRLoadLogDir`, and set it to the full path of an existing directory where you'd like to store CLR activation logs.</span></span>

<span data-ttu-id="dc87d-116">문자열 값을 제거할 때까지 활성화 로깅이 계속 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc87d-116">Activation logging remains enabled until you remove the string value.</span></span>

### <a name="using-an-environment-variable"></a><span data-ttu-id="dc87d-117">환경 변수 사용</span><span class="sxs-lookup"><span data-stu-id="dc87d-117">Using an environment variable</span></span>

- <span data-ttu-id="dc87d-118">CLR 활성화 로그를 저장할 기존 디렉터리의 전체 경로를 나타내는 문자열로 `COMPLUS_CLRLoadLogDir` 환경 변수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="dc87d-118">Set the `COMPLUS_CLRLoadLogDir` environment variable to a string that represents the full path of an existing directory where you'd like to store CLR activation logs.</span></span>

    <span data-ttu-id="dc87d-119">환경 변수를 설정하는 방법에 따라 해당 범위가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc87d-119">How you set the environment variable determines its scope:</span></span>

  - <span data-ttu-id="dc87d-120">시스템 수준에서 설정하는 경우 환경 변수를 제거할 때까지 해당 컴퓨터의 모든 .NET Framework 애플리케이션에 대해 활성화 로깅이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc87d-120">If you set it at the system level, activation logging is enabled for all .NET Framework applications on that computer until the environment variable is removed.</span></span>

  - <span data-ttu-id="dc87d-121">사용자 수준에서 설정하는 경우 현재 사용자 계정에 대해서만 활성화 로깅이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc87d-121">If you set it at the user level, activation logging is enabled only for the current user account.</span></span> <span data-ttu-id="dc87d-122">환경 변수를 제거할 때까지 로깅이 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc87d-122">Logging continues until the environment variable is removed.</span></span>

  - <span data-ttu-id="dc87d-123">CLR을 로드하기 전에 프로세스 내에서 설정하는 경우 프로세스가 종료될 때까지 활성화 로깅이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc87d-123">If you set it from within the process before loading the CLR, activation logging is enabled until the process terminates.</span></span>

  - <span data-ttu-id="dc87d-124">애플리케이션을 실행하기 전에 명령 프롬프트에서 설정하는 경우 해당 명령 프롬프트에서 실행되는 모든 애플리케이션에 대해 활성화 로깅이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc87d-124">If you set it at a command prompt before you run an application, activation logging is enabled for any application that is run from that command prompt.</span></span>

    <span data-ttu-id="dc87d-125">예를 들어 프로세스 수준 범위로 c:\clrloadlogs 디렉터리에 활성화 로그를 저장하려면 애플리케이션을 실행하기 전에 명령 프롬프트 창을 열고 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="dc87d-125">For example, to store activation logs in the c:\clrloadlogs directory with process-level scope, open a Command Prompt window and type the following before you run the application:</span></span>

    ```console
    set COMPLUS_CLRLoadLogDir=c:\clrloadlogs
    ```

## <a name="example"></a><span data-ttu-id="dc87d-126">예</span><span class="sxs-lookup"><span data-stu-id="dc87d-126">Example</span></span>

<span data-ttu-id="dc87d-127">CLR 활성화 로그는 CLR 활성화 및 CLR 호스팅 API 사용에 대한 많은 양의 데이터를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="dc87d-127">CLR activation logs provide a large amount of data about CLR activation and the use of the CLR hosting APIs.</span></span> <span data-ttu-id="dc87d-128">이 데이터는 대부분 Microsoft 내부에서 사용되지만 일부 데이터는 이 문서의 설명과 같이 개발자에게도 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc87d-128">Most of this data is used internally by Microsoft, but some of the data can also be useful to developers, as described in this article.</span></span>

<span data-ttu-id="dc87d-129">로그는 CLR 호스팅 API가 호출된 순서를 반영합니다.</span><span class="sxs-lookup"><span data-stu-id="dc87d-129">The log reflects the order in which the CLR hosting APIs were called.</span></span> <span data-ttu-id="dc87d-130">또한 컴퓨터에서 검색된 설치된 런타임 집합에 대한 유용한 데이터도 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="dc87d-130">It also includes useful data about the set of installed runtimes detected on the computer.</span></span> <span data-ttu-id="dc87d-131">CLR 활성화 로그 형식 자체는 문서화되지 않지만 CLR 활성화 문제를 해결해야 하는 개발자를 지원하는 데 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc87d-131">The CLR activation log format is not itself documented, but can be used to aid developers who need to resolve CLR activation issues.</span></span>

> [!NOTE]
> <span data-ttu-id="dc87d-132">CLR을 사용하는 프로세스가 종료될 때까지 활성화 로그를 열 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dc87d-132">You cannot open an activation log until the process that uses the CLR has terminated.</span></span>

> [!NOTE]
> <span data-ttu-id="dc87d-133">CLR 활성화 로그는 지역화되지 않으며 항상 영어로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc87d-133">CLR activation logs are not localized; they are always generated in the English language.</span></span>

<span data-ttu-id="dc87d-134">활성화 로그의 다음 예제에서는 가장 유용한 정보가 강조 표시되고 로그 다음에 설명됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc87d-134">In the following example of an activation log, the most useful information is highlighted and described after the log.</span></span>

```output
532,205950.367,CLR Loading log for C:\Tests\myapp.exe
532,205950.367,Log started at 4:26:12 PM on 10/6/2011
532,205950.367,-----------------------------------
532,205950.382,FunctionCall: _CorExeMain
532,205950.382,FunctionCall: ClrCreateInstance, Clsid: {2EBCD49A-1B47-4A61-B13A-4A03701E594B}, Iid: {E2190695-77B2-492E-8E14-C4B3A7FDD593}
532,205950.382,MethodCall: ICLRMetaHostPolicy::GetRequestedRuntime. Version: (null), Metahost Policy Flags: 0x168, Binary: (null), Iid: {BD39D1D2-BA2F-486A-89B0-B4B0CB466891}
532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0
532,205950.382,Input values for ComputeVersionString follow this line
532,205950.382,-----------------------------------
532,205950.382,Default Application Name: C:\Tests\myapp.exe
532,205950.382,IsLegacyBind is: 0
532,205950.382,IsCapped is 0
532,205950.382,SkuCheckFlags are 0
532,205950.382,ShouldEmulateExeLaunch is 0
532,205950.382,LegacyBindRequired is 0
532,205950.382,-----------------------------------
532,205950.382,Parsing config file: C:\Tests\myapp.exe
532,205950.382,UseLegacyV2RuntimeActivationPolicy is set to 0
532,205950.382,LegacyFunctionCall: GetFileVersion. Filename: C:\Tests\myapp.exe
532,205950.382,LegacyFunctionCall: GetFileVersion. Filename: C:\Tests\myapp.exe
532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727
532,205950.382,ERROR: Version v2.0.50727 is not present on the machine.
532,205950.398,SEM_FAILCRITICALERRORS is set to 0
532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3
532,205950.398,FunctionCall: RealDllMain. Reason: 0
532,205950.398,FunctionCall: OnShimDllMainCalled. Reason: 0
```

- <span data-ttu-id="dc87d-135">**CLR 로드 로그**에서는 관리 코드를 로드하는 프로세스를 시작한 실행 파일의 경로를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="dc87d-135">**CLR Loading log** provides the path to the executable that started the process that loaded managed code.</span></span> <span data-ttu-id="dc87d-136">이는 기본 호스트일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc87d-136">Note that this could be a native host.</span></span>

    ```output
    532,205950.367,CLR Loading log for C:\Tests\myapp.exe
    ```

- <span data-ttu-id="dc87d-137">**설치된 런타임**은 활성화 요청의 후보가 되는, 컴퓨터에 설치된 CLR 버전 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="dc87d-137">**Installed Runtime** is the set of CLR versions installed on the computer that are candidates for the activation request.</span></span>

    ```output
    532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0
    ```

- <span data-ttu-id="dc87d-138">**built with version**은 [ICLRMetaHostPolicy::GetRequestedRuntime](../unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) 등의 메서드에 제공된 이진 파일을 작성하는 데 사용된 CLR 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="dc87d-138">**built with version** is the version of the CLR that was used to build the binary that was provided to a method such as [ICLRMetaHostPolicy::GetRequestedRuntime](../unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md).</span></span>

    ```output
    532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727
    ```

- <span data-ttu-id="dc87d-139">**feature-on-demand installation**은 Windows 8에서 .NET Framework 3.5를 사용하는 경우를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="dc87d-139">**feature-on-demand installation** refers to enabling the .NET Framework 3.5 on Windows 8.</span></span> <span data-ttu-id="dc87d-140">이 시나리오에 대한 자세한 내용은 [.NET Framework 초기화 오류: 사용자 환경 관리](initialization-errors-managing-the-user-experience.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dc87d-140">See [.NET Framework Initialization Errors: Managing the User Experience](initialization-errors-managing-the-user-experience.md) for more information about this scenario.</span></span>

    ```output
    532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3
    ```

## <a name="see-also"></a><span data-ttu-id="dc87d-141">참조</span><span class="sxs-lookup"><span data-stu-id="dc87d-141">See also</span></span>

- [<span data-ttu-id="dc87d-142">배포</span><span class="sxs-lookup"><span data-stu-id="dc87d-142">Deployment</span></span>](index.md)
- [<span data-ttu-id="dc87d-143">방법: .NET Framework 4 이상 버전을 지원하도록 앱 구성</span><span class="sxs-lookup"><span data-stu-id="dc87d-143">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
