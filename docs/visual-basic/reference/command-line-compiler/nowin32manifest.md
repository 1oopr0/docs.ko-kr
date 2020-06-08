---
title: -nowin32manifest
ms.date: 03/13/2018
helpviewer_keywords:
- /nowin32manifest compiler option [Visual Basic]
- nowin32manifest compiler option [Visual Basic]
- -nowin32manifest compiler option [Visual Basic]
ms.assetid: c0528aae-83b3-4425-99f0-19448e9843e3
ms.openlocfilehash: d9323cd541eaf611551de90e58a181f6915fad89
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397456"
---
# <a name="-nowin32manifest-visual-basic"></a><span data-ttu-id="54337-102">-nowin32manifest(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="54337-102">-nowin32manifest (Visual Basic)</span></span>
<span data-ttu-id="54337-103">실행 파일에 애플리케이션 매니페스트를 포함하지 않도록 컴파일러에 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="54337-103">Instructs the compiler not to embed any application manifest into the executable file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54337-104">구문</span><span class="sxs-lookup"><span data-stu-id="54337-104">Syntax</span></span>  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a><span data-ttu-id="54337-105">설명</span><span class="sxs-lookup"><span data-stu-id="54337-105">Remarks</span></span>  
 <span data-ttu-id="54337-106">이 옵션을 사용하는 경우 Win32 리소스 파일에서 또는 이후 빌드 단계 중에 애플리케이션 매니페스트를 제공하지 않으면 Windows Vista에서 애플리케이션에 가상화가 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="54337-106">When this option is used, the application will be subject to virtualization on Windows Vista unless you provide an application manifest in a Win32 Resource file or during a later build step.</span></span> <span data-ttu-id="54337-107">가상화에 대한 자세한 내용은 [ClickOnce Deployment on Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista)(Windows Vista의 ClickOnce 배포)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="54337-107">For more information about virtualization, see [ClickOnce Deployment on Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span></span>  
  
 <span data-ttu-id="54337-108">매니페스트 생성에 대한 자세한 내용은 [-win32manifest(Visual Basic)](win32manifest.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="54337-108">For more information about manifest creation, see [-win32manifest (Visual Basic)](win32manifest.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54337-109">참조</span><span class="sxs-lookup"><span data-stu-id="54337-109">See also</span></span>

- [<span data-ttu-id="54337-110">Visual Basic 명령줄 컴파일러</span><span class="sxs-lookup"><span data-stu-id="54337-110">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="54337-111">프로젝트 디자이너, 애플리케이션 페이지(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="54337-111">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
