---
title: Visual Studio용 개발자 명령 프롬프트
description: .NET 도구를 더 쉽게 사용할 수 있는 Visual Studio용 개발자 명령 프롬프트를 사용하는 방법에 대해 알아봅니다. 이는 특정 환경 변수를 자동으로 설정합니다.
ms.date: 01/05/2020
helpviewer_keywords:
- command prompt, Windows SDK
- Visual Studio command prompt
- command prompt, Visual Studio
- SDK command prompt
- tools [.NET Framework], setting environment variables
- environment variables, setting for tools
- developer command prompt
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
ms.openlocfilehash: 92416820f47cb778dfcc916b8626df4aa328814c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167169"
---
# <a name="developer-command-prompt-for-visual-studio"></a><span data-ttu-id="63f46-104">Visual Studio용 개발자 명령 프롬프트</span><span class="sxs-lookup"><span data-stu-id="63f46-104">Developer Command Prompt for Visual Studio</span></span>

<span data-ttu-id="63f46-105">Visual Studio에 대한 개발자 명령 프롬프트를 통해 .NET Framework 도구를 더 쉽게 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f46-105">Developer Command Prompt for Visual Studio enables you to use .NET Framework tools more easily.</span></span> <span data-ttu-id="63f46-106">이는 특정 환경 변수를 자동으로 설정하는 명령 프롬프트입니다.</span><span class="sxs-lookup"><span data-stu-id="63f46-106">It's a command prompt that automatically sets specific environment variables.</span></span> <span data-ttu-id="63f46-107">개발자 명령 프롬프트를 연 후 `ildasm` 또는 `clrver`와 같은 [.NET Framework 도구](index.md)에 대한 명령을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f46-107">After opening Developer Command Prompt, you can enter the commands for [.NET Framework tools](index.md) such as `ildasm` or `clrver`.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="63f46-108">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="63f46-108">Prerequisites</span></span>

- [<span data-ttu-id="63f46-109">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="63f46-109">Visual Studio 2019</span></span>](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

## <a name="search-for-the-command-prompt-on-your-machine"></a><span data-ttu-id="63f46-110">머신에서 명령 프롬프트 검색</span><span class="sxs-lookup"><span data-stu-id="63f46-110">Search for the command prompt on your machine</span></span>

<span data-ttu-id="63f46-111">설치한 Visual Studio의 버전과 추가 SDK 및 워크로드에 따라 여러 개의 명령 프롬프트가 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f46-111">You may have multiple command prompts, depending on the version of Visual Studio and any additional SDKs and workloads you've installed.</span></span> <span data-ttu-id="63f46-112">다음 단계가 작동하지 않는 경우 [머신에서 수동으로 파일 찾기](#manually-locate-the-files-on-your-machine) 또는 [Visual Studio 내에서 명령 프롬프트 시작](#start-the-command-prompt-from-inside-visual-studio)을 시도해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f46-112">If the following steps don't work, you can try to [manually locate the files on your machine](#manually-locate-the-files-on-your-machine) or [start the command prompt from inside Visual Studio](#start-the-command-prompt-from-inside-visual-studio).</span></span>

### <a name="windows-10"></a><span data-ttu-id="63f46-113">Windows 10</span><span class="sxs-lookup"><span data-stu-id="63f46-113">Windows 10</span></span>

1. <span data-ttu-id="63f46-114">**시작** ![키보드의 Windows 로고 키](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="63f46-114">Select **Start** ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="63f46-115">**V** 문자로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="63f46-115">and scroll to the letter **V**.</span></span>

1. <span data-ttu-id="63f46-116">**Visual Studio 2019** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="63f46-116">Expand the **Visual Studio 2019** folder.</span></span>

1. <span data-ttu-id="63f46-117">**VS 2019용 개발자 명령 프롬프트**(또는 사용할 명령 프롬프트)를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="63f46-117">Choose **Developer Command Prompt for VS 2019** (or the command prompt you want to use).</span></span>

   <span data-ttu-id="63f46-118">또는 작업 표시줄의 검색 상자에서 명령 프롬프트의 이름을 입력하고 결과 목록에 검색 일치가 표시되기 시작할 때 원하는 결과를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f46-118">Alternatively, you can start typing the name of the command prompt in the search box on the taskbar, and choose the result you want as the result list starts to display the search matches.</span></span>

   ![Windows 10의 검색 동작을 보여 주는 애니메이션 gif](./media/developer-command-prompt-for-vs/windows10-search.gif)

### <a name="windows-81"></a><span data-ttu-id="63f46-120">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="63f46-120">Windows 8.1</span></span>

1. <span data-ttu-id="63f46-121">Windows 로고 키 ![키보드에서 Windows 로고 키](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)를 눌러 **시작** 화면으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="63f46-121">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="63f46-122">예를 들어 키보드에서</span><span class="sxs-lookup"><span data-stu-id="63f46-122">on your keyboard for example.</span></span>

1. <span data-ttu-id="63f46-123">**시작** 화면에서 **Ctrl**+**Tab**을 눌러 **앱** 목록을 열고 **V**를 누릅니다. 그러면 설치된 모든 Visual Studio 명령 프롬프트가 포함된 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="63f46-123">On the **Start** screen, press **Ctrl**+**Tab** to open the **Apps** list, and then press **V**. This brings up a list that includes all installed Visual Studio command prompts.</span></span>

1. <span data-ttu-id="63f46-124">**VS 2019용 개발자 명령 프롬프트**(또는 사용할 명령 프롬프트)를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="63f46-124">Choose **Developer Command Prompt for VS 2019** (or the command prompt you want to use).</span></span>

### <a name="windows-7"></a><span data-ttu-id="63f46-125">Windows 7</span><span class="sxs-lookup"><span data-stu-id="63f46-125">Windows 7</span></span>

1. <span data-ttu-id="63f46-126">**시작**을 선택한 다음 **모든 프로그램**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="63f46-126">Choose **Start** and then expand **All Programs**.</span></span>

1. <span data-ttu-id="63f46-127">**Visual Studio 2019** > **Visual Studio Tools** > **VS 2019용 개발자 명령 프롬프트** 또는 사용하려는 명령 프롬프트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="63f46-127">Choose **Visual Studio 2019** > **Visual Studio Tools** > **Developer Command Prompt for VS 2019**, or the command prompt you want to use.</span></span>

   ![명령 프롬프트가 강조 표시된 Windows 7 시작 메뉴](./media/developer-command-prompt-for-vs/windows7-menu.png)

<span data-ttu-id="63f46-129">[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 또는 [이전 버전](https://developer.microsoft.com/windows/downloads/sdk-archive)과 같은 다른 SDK를 설치한 경우 추가 명령 프롬프트가 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f46-129">If you have other SDKs installed, such as the [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) or [previous versions](https://developer.microsoft.com/windows/downloads/sdk-archive), you may see additional command prompts.</span></span> <span data-ttu-id="63f46-130">각 도구의 설명서를 확인하여 사용할 명령 프롬프트 버전을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="63f46-130">Check the documentation for the individual tools to determine which version of the command prompt you should use.</span></span>

## <a name="manually-locate-the-files-on-your-machine"></a><span data-ttu-id="63f46-131">머신에서 수동으로 파일 찾기</span><span class="sxs-lookup"><span data-stu-id="63f46-131">Manually locate the files on your machine</span></span>

<span data-ttu-id="63f46-132">일반적으로 설치한 명령 프롬프트의 바로 가기는 *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019\Visual Studio Tools*와 같이 Visual Studio에 대한 **시작 메뉴** 폴더에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="63f46-132">Usually, the shortcuts for the command prompts you have installed are placed at the **Start Menu** folder for Visual Studio, such as in *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019\Visual Studio Tools*.</span></span> <span data-ttu-id="63f46-133">하지만 어떤 이유로 명령 프롬프트를 검색했는데 예상된 결과가 나타나지 않는 경우, 컴퓨터에서 수동으로 바로 가기를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f46-133">But if, for some reason, searching for the command prompt doesn't produce the expected results, you can try to manually locate the shortcut on your machine.</span></span> <span data-ttu-id="63f46-134">*VsDevCmd.bat*와 같은 명령 프롬프트 파일의 이름 검색을 시도하거나 *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools*와 같은 도구 폴더로 이동합니다(경로는 Visual Studio 버전, 에디션 및 설치 위치에 따라 바뀜).</span><span class="sxs-lookup"><span data-stu-id="63f46-134">Try searching for the name of the command prompt file, such as *VsDevCmd.bat*, or go to the Tools folder, such as *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools* (path changes according to your Visual Studio version, edition, and installation location).</span></span>

## <a name="start-the-command-prompt-from-inside-visual-studio"></a><span data-ttu-id="63f46-135">Visual Studio 내에서 명령 프롬프트 시작</span><span class="sxs-lookup"><span data-stu-id="63f46-135">Start the command prompt from inside Visual Studio</span></span>

<span data-ttu-id="63f46-136">개발자 명령 프롬프트 또는 다른 명령 프롬프트를 Visual Studio의 도구 메뉴에 추가하면 쉽게 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f46-136">For easier access, you can add Developer Command Prompt, or any other command prompt, to the Tools menu in Visual Studio.</span></span> <span data-ttu-id="63f46-137">도구를 사용 가능하도록 하려면 외부 도구 목록에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="63f46-137">To make the tool available, add it to the external tools list.</span></span> <span data-ttu-id="63f46-138">단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="63f46-138">Here are the steps:</span></span>

1. <span data-ttu-id="63f46-139">Visual Studio를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="63f46-139">Open Visual Studio.</span></span>

1. <span data-ttu-id="63f46-140">시작 창에서 **코드를 사용하지 않고 계속**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="63f46-140">On the start window, choose **Continue without code**.</span></span>

1. <span data-ttu-id="63f46-141">메뉴 모음에서 **도구**  >  **외부 도구**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="63f46-141">On the menu bar, choose **Tools** > **External Tools**.</span></span>

1. <span data-ttu-id="63f46-142">**외부 도구** 대화 상자에서 **추가** 단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="63f46-142">On the **External Tools** dialog box, choose the **Add** button.</span></span> <span data-ttu-id="63f46-143">새 항목이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="63f46-143">A new entry appears.</span></span>

1. <span data-ttu-id="63f46-144">`Command Prompt`와 같은 새 메뉴 항목에 대해 **제목**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="63f46-144">Enter a **Title** for your new menu item such as `Command Prompt`.</span></span>

1. <span data-ttu-id="63f46-145">**명령** 필드에서 `%comspec%` 또는 `C:\Windows\System32\cmd.exe` 등의 시작하려는 파일을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="63f46-145">In the **Command** field, specify the file you want to launch, such as `%comspec%` or `C:\Windows\System32\cmd.exe`.</span></span>

1. <span data-ttu-id="63f46-146">**인수** 필드에서 `/k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"`과 같이 사용하려는 특정 명령 프롬프트가 있는 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="63f46-146">In the **Arguments** field, specify where to find the specific command prompt you want to use, such as `/k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"`.</span></span> <span data-ttu-id="63f46-147">이 명령은 Visual Studio 2019 커뮤니티와 함께 설치된 개발자 명령 프롬프트를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="63f46-147">This command launches the Developer Command Prompt that's installed with Visual Studio 2019 Community.</span></span> <span data-ttu-id="63f46-148">Visual Studio 버전, 에디션 및 설치 위치에 따라 이 값을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="63f46-148">Change this value according to your Visual Studio version, edition, and installation location.</span></span>

1. <span data-ttu-id="63f46-149">**초기 디렉터리** 필드에 명령 프롬프트가 시작될 디렉터리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="63f46-149">In the **Initial directory** field, specify the directory in which the command prompt will start.</span></span> <span data-ttu-id="63f46-150">필드 옆에 있는 화살표를 선택하여 **프로젝트 디렉터리**와 같은 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="63f46-150">Choose a value such as **Project Directory** by selecting the arrow next to the field.</span></span>

1. <span data-ttu-id="63f46-151">**확인** 단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="63f46-151">Choose the **OK** button.</span></span>

   ![필드 값이 채워진 외부 도구 대화 상자](./media/developer-command-prompt-for-vs/add-external-tool.png)

   <span data-ttu-id="63f46-153">새 메뉴 항목이 추가되고 도구 메뉴에서 명령 프롬프트에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f46-153">The new menu item is added, and you can access the command prompt from the Tools menu.</span></span>

   ![Visual Studio의 명령 프롬프트 메뉴 항목](./media/developer-command-prompt-for-vs/command-prompt-vs-menu.png)

## <a name="see-also"></a><span data-ttu-id="63f46-155">참조</span><span class="sxs-lookup"><span data-stu-id="63f46-155">See also</span></span>

- [<span data-ttu-id="63f46-156">.NET Framework 도구</span><span class="sxs-lookup"><span data-stu-id="63f46-156">.NET Framework Tools</span></span>](index.md)
- [<span data-ttu-id="63f46-157">외부 도구 관리</span><span class="sxs-lookup"><span data-stu-id="63f46-157">Managing External Tools</span></span>](/visualstudio/ide/managing-external-tools)
- [<span data-ttu-id="63f46-158">명령줄에서 Microsoft C++ 도구 집합 사용</span><span class="sxs-lookup"><span data-stu-id="63f46-158">Use the Microsoft C++ toolset from the command line</span></span>](/cpp/build/building-on-the-command-line)
