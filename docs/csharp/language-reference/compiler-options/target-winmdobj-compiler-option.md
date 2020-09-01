---
description: -target:winmdobj(C# 컴파일러 옵션)
title: -target:winmdobj(C# 컴파일러 옵션)
ms.date: 07/20/2015
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
ms.openlocfilehash: 66a4bddb34832705ad4779829e561afd9442be8f
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139088"
---
# <a name="-targetwinmdobj-c-compiler-options"></a><span data-ttu-id="7e202-103">-target:winmdobj(C# 컴파일러 옵션)</span><span class="sxs-lookup"><span data-stu-id="7e202-103">-target:winmdobj (C# Compiler Options)</span></span>
<span data-ttu-id="7e202-104">**-target:winmdobj** 컴파일러 옵션을 사용하는 경우 컴파일러는 사용자가 Windows 런타임 이진(.winmd) 파일로 변환할 수 있는 중간 .winmdobj 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7e202-104">If you use the **-target:winmdobj** compiler option, the compiler creates an intermediate .winmdobj file that you can convert to a Windows Runtime binary (.winmd) file.</span></span> <span data-ttu-id="7e202-105">그런 다음 관리되는 언어 프로그램뿐만 아니라 JavaScript 및 C++ 프로그램에서도 .winmd 파일을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e202-105">The .winmd file can then be consumed by JavaScript and C++ programs, in addition to managed language programs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e202-106">구문</span><span class="sxs-lookup"><span data-stu-id="7e202-106">Syntax</span></span>  
  
```console  
-target:winmdobj  
```  
  
## <a name="remarks"></a><span data-ttu-id="7e202-107">설명</span><span class="sxs-lookup"><span data-stu-id="7e202-107">Remarks</span></span>  
 <span data-ttu-id="7e202-108">**winmdobj** 설정이 컴파일러에 중간 모듈이 필요하다는 신호를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="7e202-108">The **winmdobj** setting signals to the compiler that an intermediate module is required.</span></span> <span data-ttu-id="7e202-109">이에 대한 응답으로 Visual Studio에서 C# 클래스 라이브러리를 .winmdobj 파일로 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="7e202-109">In response, Visual Studio compiles the C# class library as a .winmdobj file.</span></span> <span data-ttu-id="7e202-110">그런 다음 <xref:Microsoft.Build.Tasks.WinMDExp> 내보내기 도구를 통해 .winmdobj 파일을 공급하여 Windows 메타데이터(.winmd) 파일을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e202-110">The .winmdobj file can then be fed through the <xref:Microsoft.Build.Tasks.WinMDExp> export tool to produce a Windows metadata (.winmd) file.</span></span> <span data-ttu-id="7e202-111">.winmd 파일에는 원본 라이브러리의 코드와 JavaScript 또는 C++ 및 Windows 런타임에서 사용하는 WinMD 메타데이터가 모두 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e202-111">The .winmd file contains both the code from the original library and the WinMD metadata that is used by JavaScript or C++ and by the Windows Runtime.</span></span>  
  
 <span data-ttu-id="7e202-112">**-target:winmdobj** 컴파일러 옵션을 사용하여 컴파일된 파일의 출력은 WimMDExp 내보내기 도구의 입력으로만 사용하도록 설계되었습니다. .winmdobj 파일 자체는 직접 참조되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7e202-112">The output of a file that’s compiled by using the **-target:winmdobj** compiler option is designed to be used only as input for the WimMDExp export tool; the .winmdobj file itself isn’t referenced directly.</span></span>  
  
 <span data-ttu-id="7e202-113">[-out](./out-compiler-option.md) 옵션을 사용하지 않으면 첫 번째 입력 파일의 이름이 출력 파일의 이름으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e202-113">Unless you use the [-out](./out-compiler-option.md) option, the output file name takes the name of the first input file.</span></span> <span data-ttu-id="7e202-114">[Main](../../programming-guide/main-and-command-args/index.md) 메서드는 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7e202-114">A [Main](../../programming-guide/main-and-command-args/index.md) method isn’t required.</span></span>  
  
 <span data-ttu-id="7e202-115">명령 프롬프트에서 -target:winmdobj 옵션을 지정하면 Windows 프로그램을 만드는 데 다음 **-out** 또는 [-target:module](./target-module-compiler-option.md) 옵션까지의 모든 파일이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e202-115">If you specify the -target:winmdobj option at a command prompt, all files until the next **-out** or [-target:module](./target-module-compiler-option.md) option are used to create the Windows program.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-ide-for-a-windows-store-app"></a><span data-ttu-id="7e202-116">Windows 스토어 응용 프로그램용 Visual Studio IDE에서 이 컴파일러 옵션을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="7e202-116">To set this compiler option in the Visual Studio IDE for a Windows Store app</span></span>  
  
1. <span data-ttu-id="7e202-117">**솔루션 탐색기**에서 프로젝트의 바로 가기 메뉴를 열고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7e202-117">In **Solution Explorer**, open the shortcut menu for your project, and then choose **Properties**.</span></span>  
  
2. <span data-ttu-id="7e202-118">**애플리케이션** 탭을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7e202-118">Choose the **Application** tab.</span></span>  
  
3. <span data-ttu-id="7e202-119">**출력 형식** 목록에서 **WinMD 파일**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7e202-119">In the **Output type** list, choose **WinMD File**.</span></span>  
  
     <span data-ttu-id="7e202-120">**WinMD 파일** 옵션은 Windows 8.x 스토어 앱 템플릿에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e202-120">The **WinMD File** option is available only for Windows 8.x Store app templates.</span></span>  
  
 <span data-ttu-id="7e202-121">이 컴파일러 옵션을 프로그래밍 방식으로 설정하는 방법에 대한 자세한 내용은 <xref:VSLangProj80.ProjectProperties3.OutputType%2A>을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="7e202-121">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e202-122">예제</span><span class="sxs-lookup"><span data-stu-id="7e202-122">Example</span></span>  
 <span data-ttu-id="7e202-123">다음 명령은 `filename.cs`를 중간 .winmdobj 파일로 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="7e202-123">The following command compiles `filename.cs` into an intermediate .winmdobj file.</span></span>  
  
```console  
csc -target:winmdobj filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="7e202-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7e202-124">See also</span></span>

- [<span data-ttu-id="7e202-125">-target(C# 컴파일러 옵션)</span><span class="sxs-lookup"><span data-stu-id="7e202-125">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="7e202-126">C# 컴파일러 옵션</span><span class="sxs-lookup"><span data-stu-id="7e202-126">C# Compiler Options</span></span>](./index.md)
