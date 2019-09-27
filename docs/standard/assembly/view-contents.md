---
title: '방법: 어셈블리 콘텐츠 보기'
ms.date: 08/20/2019
helpviewer_keywords:
- assembly manifest, viewing information
- Ildasm.exe
- MSIL Disassembler
- assemblies [.NET Framework], viewing contents
- viewing assembly information
- MSIL
- viewing MSIL information
ms.assetid: fb7baaab-4c0d-47ad-8fd3-4591cf834709
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 40ed31bb2231775bb2b6eb24586e07c8b07a85bb
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053952"
---
# <a name="how-to-view-assembly-contents"></a><span data-ttu-id="e40c1-102">방법: 어셈블리 콘텐츠 보기</span><span class="sxs-lookup"><span data-stu-id="e40c1-102">How to: View assembly contents</span></span>

<span data-ttu-id="e40c1-103">[Ildasm.exe(IL 디스어셈블러)](../../framework/tools/ildasm-exe-il-disassembler.md)를 사용하여 파일의 MSIL(Microsoft Intermediate Language) 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e40c1-103">You can use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to view Microsoft intermediate language (MSIL) information in a file.</span></span> <span data-ttu-id="e40c1-104">검사되는 파일이 어셈블리이면 이 정보에 어셈블리의 특성뿐만 아니라 다른 모듈 및 어셈블리에 대한 참조가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e40c1-104">If the file being examined is an assembly, this information can include the assembly's attributes, as well as references to other modules and assemblies.</span></span> <span data-ttu-id="e40c1-105">이 정보는 파일이 어셈블리 또는 어셈블리의 일부인지 여부 및 파일이 다른 모듈 또는 어셈블리에 대한 참조를 포함하는지 여부를 확인하는 데 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e40c1-105">This information can be helpful in determining whether a file is an assembly or part of an assembly, and whether the file has references to other modules or assemblies.</span></span>  
  
<span data-ttu-id="e40c1-106">*Ildasm.exe*를 사용하여 어셈블리의 콘텐츠를 표시하려면 명령 프롬프트에서 **ildasm** \<*assembly name*>을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e40c1-106">To display the contents of an assembly using *Ildasm.exe*, type **ildasm** \<*assembly name*> at a command prompt.</span></span> <span data-ttu-id="e40c1-107">예를 들어 다음 명령은 *Hello.exe* 어셈블리를 디스어셈블합니다.</span><span class="sxs-lookup"><span data-stu-id="e40c1-107">For example, the following command disassembles the *Hello.exe* assembly.</span></span>  

```cmd
ildasm Hello.exe  
```  

<span data-ttu-id="e40c1-108">어셈블리 매니페스트 정보를 보려면 MSIL 디스어셈블러 창에서 **매니페스트** 아이콘을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e40c1-108">To view assembly manifest information, double-click the **Manifest** icon in the MSIL Disassembler window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e40c1-109">예</span><span class="sxs-lookup"><span data-stu-id="e40c1-109">Example</span></span>  

<span data-ttu-id="e40c1-110">다음 예제는 기본 "Hello World" 프로그램으로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="e40c1-110">The following example starts with a basic "Hello World" program.</span></span> <span data-ttu-id="e40c1-111">프로그램을 컴파일한 후 *Ildasm.exe*를 사용하여 *Hello.exe* 어셈블리를 디스어셈블하고 어셈블리 매니페스트를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="e40c1-111">After compiling the program, use *Ildasm.exe* to disassemble the *Hello.exe* assembly and view the assembly manifest.</span></span>  

```cpp
using namespace System;

class MainApp
{
public:
    static void Main()
    {
        Console::WriteLine("Hello World using C++/CLI!");
    }
};

int main()
{
    MainApp::Main();
}
```

```csharp
using System;

class MainApp
{
    public static void Main()
    {
        Console.WriteLine("Hello World using C#!");
    }
}
```

```vb
Imports System

Class MainApp
    Public Shared Sub Main()
        Console.WriteLine("Hello World using Visual Basic!")
    End Sub
End Class
```

<span data-ttu-id="e40c1-112">*Hello.exe* 어셈블리에서 *ildasm.exe* 명령을 실행하고 MSIL 디스어셈블러 창에서 **매니페스트** 아이콘을 두 번 클릭하면 다음과 같은 출력이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e40c1-112">Running the command *ildasm.exe* on the *Hello.exe* assembly and double-clicking the **Manifest** icon in the MSIL Disassembler window produces the following output:</span></span>  

```output
// Metadata version: v4.0.30319  
.assembly extern mscorlib  
{  
  .publickeytoken = (B7 7A 5C 56 19 34 E0 89 )                         // .z\V.4..  
  .ver 4:0:0:0  
}  
.assembly Hello  
{  
  .custom instance void [mscorlib]System.Runtime.CompilerServices.CompilationRelaxationsAttribute::.ctor(int32) = ( 01 00 08 00 00 00 00 00 )   
  .custom instance void [mscorlib]System.Runtime.CompilerServices.RuntimeCompatibilityAttribute::.ctor() = ( 01 00 01 00 54 02 16 57 72 61 70 4E 6F 6E 45 78   // ....T..WrapNonEx  
                                                                                                             63 65 70 74 69 6F 6E 54 68 72 6F 77 73 01 )       // ceptionThrows.  
  .hash algorithm 0x00008004  
  .ver 0:0:0:0  
}  
.module Hello.exe  
// MVID: {7C2770DB-1594-438D-BAE5-98764C39CCCA}  
.imagebase 0x00400000  
.file alignment 0x00000200  
.stackreserve 0x00100000  
.subsystem 0x0003       // WINDOWS_CUI  
.corflags 0x00000001    //  ILONLY  
// Image base: 0x00600000  
```  
  
 <span data-ttu-id="e40c1-113">다음 표에서는 예제에 사용된 *Hello.exe* 어셈블리의 어셈블리 매니페스트에 있는 각 지시문에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e40c1-113">The following table describes each directive in the assembly manifest of the *Hello.exe* assembly used in the example.</span></span>  
  
|<span data-ttu-id="e40c1-114">지시문</span><span class="sxs-lookup"><span data-stu-id="e40c1-114">Directive</span></span>|<span data-ttu-id="e40c1-115">설명</span><span class="sxs-lookup"><span data-stu-id="e40c1-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e40c1-116">**.assembly extern \<** *assembly name* **>**</span><span class="sxs-lookup"><span data-stu-id="e40c1-116">**.assembly extern \<** *assembly name* **>**</span></span>|<span data-ttu-id="e40c1-117">현재 모듈에서 참조하는 항목이 포함된 다른 어셈블리를 지정합니다(이 예제에서는 `mscorlib`).</span><span class="sxs-lookup"><span data-stu-id="e40c1-117">Specifies another assembly that contains items referenced by the current module (in this example, `mscorlib`).</span></span>|  
|<span data-ttu-id="e40c1-118">**.publickeytoken \<** *token* **>**</span><span class="sxs-lookup"><span data-stu-id="e40c1-118">**.publickeytoken \<** *token* **>**</span></span>|<span data-ttu-id="e40c1-119">참조된 어셈블리의 실제 키의 토큰을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e40c1-119">Specifies the token of the actual key of the referenced assembly.</span></span>|  
|<span data-ttu-id="e40c1-120">**.ver \<** *version number* **>**</span><span class="sxs-lookup"><span data-stu-id="e40c1-120">**.ver \<** *version number* **>**</span></span>|<span data-ttu-id="e40c1-121">참조된 어셈블리의 버전 번호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e40c1-121">Specifies the version number of the referenced assembly.</span></span>|  
|<span data-ttu-id="e40c1-122">**.assembly \<** *assembly name* **>**</span><span class="sxs-lookup"><span data-stu-id="e40c1-122">**.assembly \<** *assembly name* **>**</span></span>|<span data-ttu-id="e40c1-123">어셈블리 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e40c1-123">Specifies the assembly name.</span></span>|  
|<span data-ttu-id="e40c1-124">**.hash algorithm \<** *int32 value* **>**</span><span class="sxs-lookup"><span data-stu-id="e40c1-124">**.hash algorithm \<** *int32 value* **>**</span></span>|<span data-ttu-id="e40c1-125">사용되는 해시 알고리즘을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e40c1-125">Specifies the hash algorithm used.</span></span>|  
|<span data-ttu-id="e40c1-126">**.ver \<** *version number* **>**</span><span class="sxs-lookup"><span data-stu-id="e40c1-126">**.ver \<** *version number* **>**</span></span>|<span data-ttu-id="e40c1-127">어셈블리의 버전 번호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e40c1-127">Specifies the version number of the assembly.</span></span>|  
|<span data-ttu-id="e40c1-128">**.module \<** *file name* **>**</span><span class="sxs-lookup"><span data-stu-id="e40c1-128">**.module \<** *file name* **>**</span></span>|<span data-ttu-id="e40c1-129">어셈블리를 구성하는 모듈의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e40c1-129">Specifies the name of the modules that make up the assembly.</span></span> <span data-ttu-id="e40c1-130">이 예제에서는 어셈블리가 파일 하나로만 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e40c1-130">In this example, the assembly consists of only one file.</span></span>|  
|<span data-ttu-id="e40c1-131">**.subsystem \<** *value* **>**</span><span class="sxs-lookup"><span data-stu-id="e40c1-131">**.subsystem \<** *value* **>**</span></span>|<span data-ttu-id="e40c1-132">프로그램에 필요한 애플리케이션 환경을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e40c1-132">Specifies the application environment required for the program.</span></span> <span data-ttu-id="e40c1-133">이 예제에서 값 3은 이 실행 파일이 콘솔에서 실행됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e40c1-133">In this example, the value 3 indicates that this executable is run from a console.</span></span>|  
|<span data-ttu-id="e40c1-134">**.corflags**</span><span class="sxs-lookup"><span data-stu-id="e40c1-134">**.corflags**</span></span>|<span data-ttu-id="e40c1-135">현재 메타데이터에서 예약된 필드입니다.</span><span class="sxs-lookup"><span data-stu-id="e40c1-135">Currently a reserved field in the metadata.</span></span>|  
  
 <span data-ttu-id="e40c1-136">어셈블리 매니페스트에는 어셈블리의 내용에 따라 여러 다른 지시문이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e40c1-136">An assembly manifest can contain a number of different directives, depending on the contents of the assembly.</span></span> <span data-ttu-id="e40c1-137">어셈블리 매니페스트에 있는 지시문의 광범위한 목록은 ECMA 설명서, 특히 "파티션 II: 메타데이터 정의 및 의미 체계" "파티션 III: CIL 명령 집합"을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e40c1-137">For an extensive list of the directives in the assembly manifest, see the ECMA documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set."</span></span> <span data-ttu-id="e40c1-138">이 설명서는 온라인으로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="e40c1-138">The documentation is available online.</span></span> <span data-ttu-id="e40c1-139">MSDN의 [ECMA C# 및 공용 언어 인프라 표준](https://go.microsoft.com/fwlink/?LinkID=99212) 및 ECMA International 웹 사이트의 [표준 ECMA-335 - CLI(공통 언어 인프라)](https://go.microsoft.com/fwlink/?LinkID=65552)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e40c1-139">See [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the ECMA International website.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e40c1-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e40c1-140">See also</span></span>

- [<span data-ttu-id="e40c1-141">애플리케이션 도메인 및 어셈블리</span><span class="sxs-lookup"><span data-stu-id="e40c1-141">Application domains and assemblies</span></span>](../../framework/app-domains/application-domains.md#application-domains-and-assemblies)
- [<span data-ttu-id="e40c1-142">애플리케이션 도메인 및 어셈블리 방법 항목</span><span class="sxs-lookup"><span data-stu-id="e40c1-142">Application domains and assemblies how-to topics</span></span>](../../framework/app-domains/application-domains-and-assemblies-how-to-topics.md)
- [<span data-ttu-id="e40c1-143">Ildasm.exe(IL 디스어셈블러)</span><span class="sxs-lookup"><span data-stu-id="e40c1-143">Ildasm.exe (IL Disassembler)</span></span>](../../framework/tools/ildasm-exe-il-disassembler.md)