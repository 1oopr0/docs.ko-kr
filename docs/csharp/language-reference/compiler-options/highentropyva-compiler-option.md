---
description: -highentropyva(C# 컴파일러 옵션)
title: -highentropyva(C# 컴파일러 옵션)
ms.date: 07/20/2015
f1_keywords:
- /highentropyva
helpviewer_keywords:
- /highentropyva compiler option [C#]
- -highentropyva compiler option [C#]
- highentropyva compiler option [C#]
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
ms.openlocfilehash: 2c2e2780693a89072c4bb55b318be94089bf3ced
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125659"
---
# <a name="-highentropyva-c-compiler-options"></a><span data-ttu-id="a3c66-103">-highentropyva(C# 컴파일러 옵션)</span><span class="sxs-lookup"><span data-stu-id="a3c66-103">-highentropyva (C# Compiler Options)</span></span>
<span data-ttu-id="a3c66-104">**-highentropyva** 컴파일러 옵션은 특정 실행 파일이 높은 엔트로피 ASLR(Address Space Layout Randomization)을 지원하는지 여부를 Windows 커널에 알려줍니다.</span><span class="sxs-lookup"><span data-stu-id="a3c66-104">The **-highentropyva** compiler option tells the Windows kernel whether a particular executable supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3c66-105">구문</span><span class="sxs-lookup"><span data-stu-id="a3c66-105">Syntax</span></span>  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="a3c66-106">인수</span><span class="sxs-lookup"><span data-stu-id="a3c66-106">Arguments</span></span>  
 <span data-ttu-id="a3c66-107">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="a3c66-107">`+` &#124; `-`</span></span>  
 <span data-ttu-id="a3c66-108">이 옵션은 [-platform:anycpu](./platform-compiler-option.md) 컴파일러 옵션으로 표시된 실행 파일이나 64비트 실행 파일이 높은 엔트로피 가상 주소 공간을 지원하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a3c66-108">This option specifies that a 64-bit executable or an executable that is marked by the [-platform:anycpu](./platform-compiler-option.md) compiler option supports a high entropy virtual address space.</span></span> <span data-ttu-id="a3c66-109">이 옵션은 기본적으로 비활성화되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3c66-109">The option is disabled by default.</span></span> <span data-ttu-id="a3c66-110">**-highentropyva+** 또는 **-highentropyva**를 사용하여 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a3c66-110">Use **-highentropyva+** or **-highentropyva** to enable it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3c66-111">설명</span><span class="sxs-lookup"><span data-stu-id="a3c66-111">Remarks</span></span>  
 <span data-ttu-id="a3c66-112">**-highentropyva** 옵션은 Windows 커널의 호환되는 버전에서 ASLR의 일부로 프로세스의 주소 공간 레이아웃을 임의로 선택할 때 보다 높은 수준의 엔트로피를 사용할 수 있게 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3c66-112">The **-highentropyva** option enables compatible versions of the Windows kernel to use higher degrees of entropy when randomizing the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="a3c66-113">더 높은 수준의 엔트로피를 사용하면 스택 및 힙과 같은 메모리 영역에 더 많은 주소를 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3c66-113">Using higher degrees of entropy means that a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="a3c66-114">따라서 특정 메모리 영역의 위치를 추측하기 어려워집니다.</span><span class="sxs-lookup"><span data-stu-id="a3c66-114">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="a3c66-115">**-highentropyva** 컴파일러 옵션을 지정하면 대상 실행 파일과 이 실행 파일이 종속된 모든 모듈이 64비트 프로세스로 실행될 때 4GB(기가바이트)보다 큰 포인터 값을 처리할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3c66-115">When the **-highentropyva** compiler option is specified, the target executable and any modules that it depends on must be able to handle pointer values that are larger than 4 gigabytes (GB) when they are running as a 64-bit process.</span></span>
