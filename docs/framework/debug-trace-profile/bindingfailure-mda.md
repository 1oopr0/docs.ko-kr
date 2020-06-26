---
title: bindingFailure MDA
description: .NET에서 어셈블리를 로드 하지 못할 때 활성화 되는 bindingFailure MDA (관리 디버깅 도우미)에 대해 읽어 보십시오.
ms.date: 03/30/2017
helpviewer_keywords:
- binding failure
- binding, failures
- MDAs (managed debugging assistants), binding failures
- assemblies [.NET Framework], binding failures
- managed debugging assistants (MDAs), binding failures
- BindingFailure MDA
ms.assetid: 26ada5af-175c-4576-931a-9f07fa1723e9
ms.openlocfilehash: 98c7947c7e5d2a1f0af8c26744d3b292ed8cb4c4
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415630"
---
# <a name="bindingfailure-mda"></a><span data-ttu-id="9df14-103">bindingFailure MDA</span><span class="sxs-lookup"><span data-stu-id="9df14-103">bindingFailure MDA</span></span>

<span data-ttu-id="9df14-104">`bindingFailure` MDA(관리 디버깅 도우미)는 어셈블리 로드에 실패할 때 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="9df14-104">The `bindingFailure` managed debugging assistant (MDA) is activated when an assembly fails to load.</span></span>

## <a name="symptoms"></a><span data-ttu-id="9df14-105">증상</span><span class="sxs-lookup"><span data-stu-id="9df14-105">Symptoms</span></span>

<span data-ttu-id="9df14-106">코드에서 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> 또는 <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> 같은 로더 메서드 중 하나 또는 정적 참조를 사용하여 어셈블리를 로드하려고 했습니다.</span><span class="sxs-lookup"><span data-stu-id="9df14-106">Code has attempted to load an assembly using a static reference or one of the loader methods, such as <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9df14-107">어셈블리가 로드되지 않고 <xref:System.IO.FileNotFoundException> 또는 <xref:System.IO.FileLoadException> 예외가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="9df14-107">The assembly is not loaded and a <xref:System.IO.FileNotFoundException> or <xref:System.IO.FileLoadException> exception is thrown.</span></span>

## <a name="cause"></a><span data-ttu-id="9df14-108">원인</span><span class="sxs-lookup"><span data-stu-id="9df14-108">Cause</span></span>

<span data-ttu-id="9df14-109">바인딩 실패는 런타임이 어셈블리를 로드할 수 없는 경우에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="9df14-109">A binding failure occurs when the runtime is unable to load an assembly.</span></span> <span data-ttu-id="9df14-110">바인딩 실패는 다음과 같은 상황 중 하나의 결과일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9df14-110">A binding failure might be the result of one of the following situations:</span></span>

- <span data-ttu-id="9df14-111">CLR(공용 언어 런타임)이 요청된 어셈블리를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9df14-111">The common language runtime (CLR) cannot find the requested assembly.</span></span> <span data-ttu-id="9df14-112">이 문제는 어셈블리가 설치되지 않음, 애플리케이션이 어셈블리를 찾도록 올바르게 구성되지 않음 등 여러 가지 이유로 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9df14-112">There are many reasons this can occur, such as the assembly not being installed or the application not being correctly configured to find the assembly.</span></span>

- <span data-ttu-id="9df14-113">일반적인 문제 시나리오는 다른 애플리케이션 도메인에 형식을 전달하여 CLR이 다른 애플리케이션 도메인에서 해당 형식을 포함하는 어셈블리를 로드해야 하는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="9df14-113">A common problem scenario is passing a type to another application domain, which requires the CLR to load the assembly containing that type in the other application domain.</span></span> <span data-ttu-id="9df14-114">다른 애플리케이션 도메인이 원래 애플리케이션 도메인과 다르게 구성된 경우 런타임이 어셈블리를 로드하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9df14-114">It may not be possible for the runtime to load the assembly if the other application domain is configured differently from the original application domain.</span></span> <span data-ttu-id="9df14-115">예를 들어 두 애플리케이션 도메인이 서로 다른 <xref:System.AppDomain.BaseDirectory%2A> 속성 값을 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9df14-115">For example, the two application domains might have different <xref:System.AppDomain.BaseDirectory%2A> property values.</span></span>

- <span data-ttu-id="9df14-116">요청된 어셈블리가 손상되었거나 어셈블리가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="9df14-116">The requested assembly is corrupted or is not an assembly.</span></span>

- <span data-ttu-id="9df14-117">어셈블리를 로드하려는 코드에 어셈블리를 로드할 수 있는 올바른 코드 액세스 보안 권한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9df14-117">The code attempting to load the assembly does not have the correct code access security permissions to load assemblies.</span></span>

- <span data-ttu-id="9df14-118">사용자 자격 증명이 파일을 읽는 데 필요한 권한을 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9df14-118">The user credentials do not provide the required permissions to read the file.</span></span>

## <a name="resolution"></a><span data-ttu-id="9df14-119">해결 방법</span><span class="sxs-lookup"><span data-stu-id="9df14-119">Resolution</span></span>

<span data-ttu-id="9df14-120">첫 번째 단계는 CLR이 요청된 어셈블리에 바인딩할 수 없는 이유를 확인하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9df14-120">The first step is to determine why the CLR could not bind to the requested assembly.</span></span> <span data-ttu-id="9df14-121">런타임이 원인 섹션에 나열된 시나리오 같이 요청된 어셈블리를 찾거나 로드할 수 없는 많은 이유가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9df14-121">There are many reasons why the runtime might not have found or been able load the requested assembly, such as the scenarios listed in the Cause section.</span></span> <span data-ttu-id="9df14-122">바인딩 실패의 원인을 제거하기 위해 다음 작업이 권장됩니다.</span><span class="sxs-lookup"><span data-stu-id="9df14-122">The following actions are recommended to eliminate the cause of the binding failure:</span></span>

- <span data-ttu-id="9df14-123">`bindingFailure` MDA에서 제공하는 데이터를 사용하여 원인 확인:</span><span class="sxs-lookup"><span data-stu-id="9df14-123">Determine the cause by using the data provided by the `bindingFailure` MDA:</span></span>

  - <span data-ttu-id="9df14-124">[Fuslogvw.exe(어셈블리 바인딩 로그 뷰어)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md)를 실행하여 어셈블리 바인더를 통해 생성된 오류 로그를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="9df14-124">Run the [Fuslogvw.exe (Assembly Binding Log Viewer)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) to read the error logs produced by the assembly binder.</span></span>

  - <span data-ttu-id="9df14-125">어셈블리가 요청된 위치에 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="9df14-125">Determine if the assembly is at the location requested.</span></span> <span data-ttu-id="9df14-126"><xref:System.Reflection.Assembly.LoadFrom%2A> 및 <xref:System.Reflection.Assembly.LoadFile%2A> 메서드의 경우 요청된 위치를 쉽게 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9df14-126">In the case of the <xref:System.Reflection.Assembly.LoadFrom%2A> and <xref:System.Reflection.Assembly.LoadFile%2A> methods, the requested location can be easily determined.</span></span> <span data-ttu-id="9df14-127">어셈블리 ID를 사용하여 바인딩하는 <xref:System.Reflection.Assembly.Load%2A> 메서드의 경우 애플리케이션 도메인의 <xref:System.AppDomain.BaseDirectory%2A> 속성 프로브 경로와 전역 어셈블리 캐시에서 해당 ID와 일치하는 어셈블리를 찾아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9df14-127">In the case of the <xref:System.Reflection.Assembly.Load%2A> method, which binds using the assembly identity, you must look for assemblies that match that identity in the application domain's <xref:System.AppDomain.BaseDirectory%2A> property probe path and the global assembly cache.</span></span>

- <span data-ttu-id="9df14-128">위의 확인에 따라 원인을 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="9df14-128">Resolve the cause based on the preceding determination.</span></span> <span data-ttu-id="9df14-129">가능한 해결 옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9df14-129">Possible resolution options are the following:</span></span>

  - <span data-ttu-id="9df14-130">전역 어셈블리 캐시에 요청된 어셈블리를 설치하고</span><span class="sxs-lookup"><span data-stu-id="9df14-130">Install the requested assembly in the global assembly cache and call the.</span></span> <span data-ttu-id="9df14-131"><xref:System.Reflection.Assembly.Load%2A> 메서드를 호출하여 ID로 어셈블리를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="9df14-131"><xref:System.Reflection.Assembly.Load%2A> method to load the assembly by identity.</span></span>

  - <span data-ttu-id="9df14-132">요청된 어셈블리를 애플리케이션 디렉터리에 복사하고 <xref:System.Reflection.Assembly.Load%2A> 메서드를 호출하여 ID로 어셈블리를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="9df14-132">Copy the requested assembly into the application directory and call the <xref:System.Reflection.Assembly.Load%2A> method to load the assembly by identity.</span></span>

  - <span data-ttu-id="9df14-133"><xref:System.AppDomain.BaseDirectory%2A> 속성을 변경하거나 전용 검색 경로를 추가하여 바인딩 실패가 발생한 애플리케이션 도메인에 어셈블리 경로가 포함되도록 다시 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="9df14-133">Reconfigure the application domain in which the binding failure occurred to include the assembly path by either changing the <xref:System.AppDomain.BaseDirectory%2A> property or adding private probing paths.</span></span>

  - <span data-ttu-id="9df14-134">로그온한 사용자가 파일을 읽을 수 있도록 파일에 대한 액세스 제어 목록을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="9df14-134">Change the access control list for the file to allow the logged-on user to read the file.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="9df14-135">런타임에 대한 영향</span><span class="sxs-lookup"><span data-stu-id="9df14-135">Effect on the Runtime</span></span>

<span data-ttu-id="9df14-136">이 MDA는 CLR에 아무런 영향을 미치지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9df14-136">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="9df14-137">바인딩 실패에 대한 데이터를 보고만 합니다.</span><span class="sxs-lookup"><span data-stu-id="9df14-137">It only reports data about binding failures.</span></span>

## <a name="output"></a><span data-ttu-id="9df14-138">출력</span><span class="sxs-lookup"><span data-stu-id="9df14-138">Output</span></span>

<span data-ttu-id="9df14-139">MDA가 요청된 경로 및/또는 표시 이름, 바인딩 컨텍스트, 로드가 요청된 애플리케이션 도메인, 실패 이유를 포함하여 로드하지 못한 어셈블리를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="9df14-139">The MDA reports the assembly that failed to load, including the requested path and/or display name, the binding context, the application domain in which the load was requested, and the reason for the failure.</span></span>

<span data-ttu-id="9df14-140">CLR이 해당 데이터를 사용할 수 없는 경우 표시 이름이나 요청된 경로가 비어 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9df14-140">The display name or requested path may be blank if that data was not available to the CLR.</span></span> <span data-ttu-id="9df14-141"><xref:System.Reflection.Assembly.Load%2A> 메서드 호출이 실패한 경우 런타임이 어셈블리의 표시 이름을 확인할 수 없어 실패했을 가능성이 큽니다.</span><span class="sxs-lookup"><span data-stu-id="9df14-141">If the call that failed was to the <xref:System.Reflection.Assembly.Load%2A> method, it is likely the runtime could not determine the display name for the assembly.</span></span>

## <a name="configuration"></a><span data-ttu-id="9df14-142">구성</span><span class="sxs-lookup"><span data-stu-id="9df14-142">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <bindingFailure />
  </assistants>
</mdaConfig>
```

## <a name="example"></a><span data-ttu-id="9df14-143">예제</span><span class="sxs-lookup"><span data-stu-id="9df14-143">Example</span></span>

<span data-ttu-id="9df14-144">다음 코드 예제에서는 이 MDA를 활성화할 수 있는 상황을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9df14-144">The following code example demonstrates a situation that can activate this MDA:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Text;
using System.Reflection;
namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            // This call attempts to load a nonexistent assembly.
            // The call will throw a System.IO.FileNotFound exception
            // and cause the activation of the bindingFailure MDA
            // if it is registered.
            Assembly.Load("NonExistentAssembly");
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="9df14-145">추가 정보</span><span class="sxs-lookup"><span data-stu-id="9df14-145">See also</span></span>

- [<span data-ttu-id="9df14-146">관리 디버깅 도우미를 사용하여 오류 진단</span><span class="sxs-lookup"><span data-stu-id="9df14-146">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
