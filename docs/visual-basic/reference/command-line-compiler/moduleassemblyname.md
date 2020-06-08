---
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
ms.openlocfilehash: 99f2b9d65f3c2a128e026666c5efb384e22643f9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403150"
---
# <a name="-moduleassemblyname"></a><span data-ttu-id="6ca69-102">-moduleassemblyname</span><span class="sxs-lookup"><span data-stu-id="6ca69-102">-moduleassemblyname</span></span>
<span data-ttu-id="6ca69-103">이 모듈이 속할 어셈블리의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6ca69-103">Specifies the name of the assembly that this module will be a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ca69-104">구문</span><span class="sxs-lookup"><span data-stu-id="6ca69-104">Syntax</span></span>  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="6ca69-105">인수</span><span class="sxs-lookup"><span data-stu-id="6ca69-105">Arguments</span></span>  
  
|<span data-ttu-id="6ca69-106">용어</span><span class="sxs-lookup"><span data-stu-id="6ca69-106">Term</span></span>|<span data-ttu-id="6ca69-107">정의</span><span class="sxs-lookup"><span data-stu-id="6ca69-107">Definition</span></span>|  
|---|---|  
|`assembly_name`|<span data-ttu-id="6ca69-108">이 모듈이 속할 어셈블리의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="6ca69-108">The name of the assembly that this module will be a part of.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ca69-109">설명</span><span class="sxs-lookup"><span data-stu-id="6ca69-109">Remarks</span></span>  
 <span data-ttu-id="6ca69-110">컴파일러는 `-target:module` 옵션이 지정된 경우에만 `-moduleassemblyname` 옵션을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="6ca69-110">The compiler processes the `-moduleassemblyname` option only if the `-target:module` option has been specified.</span></span> <span data-ttu-id="6ca69-111">이렇게 하면 컴파일러가 모듈을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6ca69-111">This causes the compiler to create a module.</span></span> <span data-ttu-id="6ca69-112">컴파일러에서 만든 모듈은 `-moduleassemblyname` 옵션으로 지정된 어셈블리에만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="6ca69-112">The module created by the compiler is valid only for the assembly specified with the `-moduleassemblyname` option.</span></span> <span data-ttu-id="6ca69-113">모듈을 다른 어셈블리에 배치하면 런타임 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="6ca69-113">If you place the module in a different assembly, run-time errors will occur.</span></span>  
  
 <span data-ttu-id="6ca69-114">`-moduleassemblyname` 옵션은 다음 조건이 충족되는 경우에만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6ca69-114">The `-moduleassemblyname` option is needed only when the following are true:</span></span>  
  
- <span data-ttu-id="6ca69-115">모듈의 데이터 형식에는 참조된 어셈블리의 `Friend` 형식에 대한 액세스 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6ca69-115">A data type in the module needs access to a `Friend` type in a referenced assembly.</span></span>  
  
- <span data-ttu-id="6ca69-116">참조된 어셈블리는 모듈을 빌드할 어셈블리에 대한 friend 어셈블리 액세스 권한을 부여했습니다.</span><span class="sxs-lookup"><span data-stu-id="6ca69-116">The referenced assembly has granted friend assembly access to the assembly into which the module will be built.</span></span>  
  
 <span data-ttu-id="6ca69-117">모듈 만들기에 대한 자세한 내용은 [-target(Visual Basic)](target.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6ca69-117">For more information about creating a module, see [-target (Visual Basic)](target.md).</span></span> <span data-ttu-id="6ca69-118">friend 어셈블리에 대한 자세한 내용은 [Friend 어셈블리](../../../standard/assembly/friend.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6ca69-118">For more information about friend assemblies, see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6ca69-119">Visual Studio 개발 환경 내에서는 `-moduleassemblyname` 옵션을 사용할 수 없습니다. 명령 프롬프트에서 컴파일하는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ca69-119">The `-moduleassemblyname` option is not available from within the Visual Studio development environment; it is available only when you compile from a command prompt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ca69-120">참조</span><span class="sxs-lookup"><span data-stu-id="6ca69-120">See also</span></span>

- [<span data-ttu-id="6ca69-121">방법: 다중 파일 어셈블리 빌드</span><span class="sxs-lookup"><span data-stu-id="6ca69-121">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/build-multifile-assembly.md)
- [<span data-ttu-id="6ca69-122">Visual Basic 명령줄 컴파일러</span><span class="sxs-lookup"><span data-stu-id="6ca69-122">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="6ca69-123">-target(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6ca69-123">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="6ca69-124">-main</span><span class="sxs-lookup"><span data-stu-id="6ca69-124">-main</span></span>](main.md)
- [<span data-ttu-id="6ca69-125">-reference(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6ca69-125">-reference (Visual Basic)</span></span>](reference.md)
- [<span data-ttu-id="6ca69-126">-addmodule</span><span class="sxs-lookup"><span data-stu-id="6ca69-126">-addmodule</span></span>](addmodule.md)
- [<span data-ttu-id="6ca69-127">.NET 어셈블리</span><span class="sxs-lookup"><span data-stu-id="6ca69-127">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="6ca69-128">샘플 컴파일 명령줄</span><span class="sxs-lookup"><span data-stu-id="6ca69-128">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="6ca69-129">Friend 어셈블리</span><span class="sxs-lookup"><span data-stu-id="6ca69-129">Friend Assemblies</span></span>](../../../standard/assembly/friend.md)
