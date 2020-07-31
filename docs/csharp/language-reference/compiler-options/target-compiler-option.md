---
title: -target(C# 컴파일러 옵션)
ms.date: 07/20/2015
f1_keywords:
- /target
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
ms.openlocfilehash: 80cec001b27000e71b74f380a0f33e30602c01af
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86473911"
---
# <a name="-target-c-compiler-options"></a><span data-ttu-id="00f48-102">-target(C# 컴파일러 옵션)</span><span class="sxs-lookup"><span data-stu-id="00f48-102">-target (C# Compiler Options)</span></span>
<span data-ttu-id="00f48-103">**-target** 컴파일러 옵션은 다음 형태 중 하나로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00f48-103">The **-target** compiler option can be specified in one of the following forms:</span></span>  
  
 [<span data-ttu-id="00f48-104">/target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="00f48-104">-target:appcontainerexe</span></span>](./target-appcontainerexe-compiler-option.md)  
 <span data-ttu-id="00f48-105">Windows 8.x 스토어 앱에 사용할 .exe 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="00f48-105">To create an .exe file for Windows 8.x Store apps.</span></span>  
  
 [<span data-ttu-id="00f48-106">/target:exe</span><span class="sxs-lookup"><span data-stu-id="00f48-106">-target:exe</span></span>](./target-exe-compiler-option.md)  
 <span data-ttu-id="00f48-107">.exe 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="00f48-107">To create an .exe file.</span></span>  
  
 [<span data-ttu-id="00f48-108">/target:library</span><span class="sxs-lookup"><span data-stu-id="00f48-108">-target:library</span></span>](./target-library-compiler-option.md)  
 <span data-ttu-id="00f48-109">코드 라이브러리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="00f48-109">To create a code library.</span></span>  
  
 [<span data-ttu-id="00f48-110">/target:module</span><span class="sxs-lookup"><span data-stu-id="00f48-110">-target:module</span></span>](./target-module-compiler-option.md)  
 <span data-ttu-id="00f48-111">모듈을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="00f48-111">To create a module.</span></span>  
  
 [<span data-ttu-id="00f48-112">/target:winexe</span><span class="sxs-lookup"><span data-stu-id="00f48-112">-target:winexe</span></span>](./target-winexe-compiler-option.md)  
 <span data-ttu-id="00f48-113">Windows 프로그램을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="00f48-113">To create a Windows program.</span></span>  
  
 [<span data-ttu-id="00f48-114">/target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="00f48-114">-target:winmdobj</span></span>](./target-winmdobj-compiler-option.md)  
 <span data-ttu-id="00f48-115">중간 .winmdobj 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="00f48-115">To create an intermediate .winmdobj file.</span></span>  
  
 <span data-ttu-id="00f48-116">**-target:module**을 지정하지 않으면 **-target**은 .NET Framework 어셈블리 매니페스트가 출력 파일에 배치되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="00f48-116">Unless you specify **-target:module**, **-target** causes a .NET Framework assembly manifest to be placed in an output file.</span></span> <span data-ttu-id="00f48-117">자세한 내용은 [.NET의 어셈블리](../../../standard/assembly/index.md) 및 [공통 특성](../attributes/global.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="00f48-117">For more information, see [Assemblies in .NET](../../../standard/assembly/index.md) and [Common Attributes](../attributes/global.md).</span></span>  
  
 <span data-ttu-id="00f48-118">어셈블리 매니페스트는 컴파일의 첫 번째 .exe 출력 파일 또는 .exe 출력 파일이 없는 경우 첫 번째 DLL에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="00f48-118">The assembly manifest is placed in the first .exe output file in the compilation or in the first DLL, if there is no .exe output file.</span></span> <span data-ttu-id="00f48-119">예를 들어 다음 명령줄에서 매니페스트는 `1.exe`에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="00f48-119">For example, in the following command line, the manifest will be placed in `1.exe`:</span></span>  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 <span data-ttu-id="00f48-120">컴파일러는 컴파일당 하나의 어셈블리 매니페스트만 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="00f48-120">The compiler creates only one assembly manifest per compilation.</span></span> <span data-ttu-id="00f48-121">컴파일의 모든 파일에 대한 정보가 어셈블리 매니페스트에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="00f48-121">Information about all files in a compilation is placed in the assembly manifest.</span></span> <span data-ttu-id="00f48-122">**-target:module**을 사용하여 생성된 파일을 제외한 모든 출력 파일에 어셈블리 매니페스트가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00f48-122">All output files except those created with **-target:module** can contain an assembly manifest.</span></span> <span data-ttu-id="00f48-123">명령줄에서 여러 출력 파일을 생성하는 경우 하나의 어셈블리 매니페스트만 만들 수 있으며, 명령줄에 지정된 첫 번째 출력 파일로 이동해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00f48-123">When producing multiple output files at the command line, only one assembly manifest can be created and it must go into the first output file specified on the command line.</span></span> <span data-ttu-id="00f48-124">첫 번째 출력 파일이 **-target:exe**, **-target:winexe**, **-target:library** 또는 **-target:module** 중 무엇이든 관계없이 동일한 컴파일에서 생성된 다른 출력 파일은 모듈( **-target:module**)이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00f48-124">No matter what the first output file is (**-target:exe**, **-target:winexe**, **-target:library** or **-target:module**), any other output files produced in the same compilation must be modules (**-target:module**).</span></span>  
  
 <span data-ttu-id="00f48-125">어셈블리를 만드는 경우 <xref:System.CLSCompliantAttribute> 특성을 사용하여 코드의 전체 또는 일부를 CLS 규격으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00f48-125">If you create an assembly, you can indicate that all or part of your code is CLS compliant with the <xref:System.CLSCompliantAttribute> attribute.</span></span>  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 <span data-ttu-id="00f48-126">이 컴파일러 옵션을 프로그래밍 방식으로 설정하는 방법에 대한 자세한 내용은 <xref:VSLangProj80.ProjectProperties3.OutputType%2A>을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="00f48-126">For more information about setting this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00f48-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="00f48-127">See also</span></span>

- [<span data-ttu-id="00f48-128">C# 컴파일러 옵션</span><span class="sxs-lookup"><span data-stu-id="00f48-128">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="00f48-129">프로젝트 및 솔루션 속성 관리</span><span class="sxs-lookup"><span data-stu-id="00f48-129">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="00f48-130">-subsystemversion(C# 컴파일러 옵션)</span><span class="sxs-lookup"><span data-stu-id="00f48-130">-subsystemversion (C# Compiler Options)</span></span>](./subsystemversion-compiler-option.md)
