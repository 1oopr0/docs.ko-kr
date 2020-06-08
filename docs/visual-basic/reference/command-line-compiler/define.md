---
title: -define
ms.date: 03/10/2018
helpviewer_keywords:
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
ms.openlocfilehash: d0d1b03d9ab98f28a0112198f1ecc1e928d6d4a7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408714"
---
# <a name="-define-visual-basic"></a><span data-ttu-id="72e35-102">-define(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72e35-102">-define (Visual Basic)</span></span>
<span data-ttu-id="72e35-103">조건부 컴파일러 상수를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="72e35-103">Defines conditional compiler constants.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72e35-104">구문</span><span class="sxs-lookup"><span data-stu-id="72e35-104">Syntax</span></span>  
  
```console  
-define:["]symbol[=value][,symbol[=value]]["]  
```

<span data-ttu-id="72e35-105">또는</span><span class="sxs-lookup"><span data-stu-id="72e35-105">or</span></span>

```console  
-d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a><span data-ttu-id="72e35-106">인수</span><span class="sxs-lookup"><span data-stu-id="72e35-106">Arguments</span></span>  
  
|<span data-ttu-id="72e35-107">용어</span><span class="sxs-lookup"><span data-stu-id="72e35-107">Term</span></span>|<span data-ttu-id="72e35-108">정의</span><span class="sxs-lookup"><span data-stu-id="72e35-108">Definition</span></span>|  
|---|---|  
|`symbol`|<span data-ttu-id="72e35-109">필수 요소.</span><span class="sxs-lookup"><span data-stu-id="72e35-109">Required.</span></span> <span data-ttu-id="72e35-110">정의할 기호입니다.</span><span class="sxs-lookup"><span data-stu-id="72e35-110">The symbol to define.</span></span>|  
|`value`|<span data-ttu-id="72e35-111">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="72e35-111">Optional.</span></span> <span data-ttu-id="72e35-112">`symbol`을 할당할 값입니다.</span><span class="sxs-lookup"><span data-stu-id="72e35-112">The value to assign `symbol`.</span></span> <span data-ttu-id="72e35-113">`value`가 문자열이면 따옴표 대신 백슬래시/따옴표 시퀀스(\\")로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="72e35-113">If `value` is a string, it must be surrounded by backslash/quotation-mark sequences (\\") instead of quotation marks.</span></span> <span data-ttu-id="72e35-114">값을 지정하지 않으면 True가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="72e35-114">If no value is specified, then it is taken to be True.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72e35-115">설명</span><span class="sxs-lookup"><span data-stu-id="72e35-115">Remarks</span></span>  
 <span data-ttu-id="72e35-116">`-define` 옵션은 `-define`로 정의된 상수가 공용상수이며 프로젝트의 모든 파일에 적용된다는 점을 제외하고 원본 파일에서 `#Const` 전처리기 지시문을 사용하는 것과 유사한 효과가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72e35-116">The `-define` option has an effect similar to using a `#Const` preprocessor directive in your source file, except that constants defined with `-define` are public and apply to all files in the project.</span></span>  
  
 <span data-ttu-id="72e35-117">이 옵션으로 만든 기호를 `#If`...`Then`...`#Else` 지시문과 함께 사용하면 소스 파일을 조건부 컴파일할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72e35-117">You can use symbols created by this option with the `#If`...`Then`...`#Else` directive to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="72e35-118">`-d`는 약식 `-define`입니다.</span><span class="sxs-lookup"><span data-stu-id="72e35-118">`-d` is the short form of `-define`.</span></span>  
  
 <span data-ttu-id="72e35-119">쉼표를 사용해 기호 정의를 구분하여 `-define`으로 여러 기호를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72e35-119">You can define multiple symbols with `-define` by using a comma to separate symbol definitions.</span></span>  
  
|<span data-ttu-id="72e35-120">Visual Studio 통합 개발 환경에서 -define을 설정하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="72e35-120">To set -define in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="72e35-121">1.  **솔루션 탐색기**에서 프로젝트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="72e35-121">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="72e35-122">**프로젝트** 메뉴에서 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="72e35-122">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="72e35-123">2.  **컴파일** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="72e35-123">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="72e35-124">3.  **고급**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="72e35-124">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="72e35-125">4.  **사용자 지정 상수** 상자의 값을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="72e35-125">4.  Modify the value in the **Custom Constants** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="72e35-126">예제</span><span class="sxs-lookup"><span data-stu-id="72e35-126">Example</span></span>  
 <span data-ttu-id="72e35-127">다음 코드는 두 조건부 컴파일러 상수를 정의한 다음 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="72e35-127">The following code defines and then uses two conditional compiler constants.</span></span>  
  
 [!code-vb[VbVbalrCompiler#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#45)]  
  
## <a name="see-also"></a><span data-ttu-id="72e35-128">참조</span><span class="sxs-lookup"><span data-stu-id="72e35-128">See also</span></span>

- [<span data-ttu-id="72e35-129">Visual Basic 명령줄 컴파일러</span><span class="sxs-lookup"><span data-stu-id="72e35-129">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="72e35-130">#If...Then...#Else 지시문</span><span class="sxs-lookup"><span data-stu-id="72e35-130">#If...Then...#Else Directives</span></span>](../../language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="72e35-131">#Const 지시문</span><span class="sxs-lookup"><span data-stu-id="72e35-131">#Const Directive</span></span>](../../language-reference/directives/const-directive.md)
- [<span data-ttu-id="72e35-132">샘플 컴파일 명령줄</span><span class="sxs-lookup"><span data-stu-id="72e35-132">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
