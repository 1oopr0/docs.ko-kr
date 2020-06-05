---
title: Option Compare 문
ms.date: 07/20/2015
f1_keywords:
- vb.Compare
- vb.OptionCompare
helpviewer_keywords:
- case sensitivity, Option Compare statement
- Compare keyword [Visual Basic]
- binary comparison [Visual Basic]
- strings [Visual Basic], returning from functions
- binary comparison [Visual Basic], Option Compare statement
- strings [Visual Basic], comparing
- string comparison [Visual Basic], Option Compare statement
- Text keyword [Visual Basic], Option Compare statement
- Binary keyword [Visual Basic], Option Compare statement
- string comparison [Visual Basic], sorting data
- Option Compare statement [Visual Basic]
- text [Visual Basic], comparing
ms.assetid: 54e8eeeb-3b0d-4fb9-acce-fbfbd5975f6e
ms.openlocfilehash: 1ffe3e45a296d02364f488540d987d85133013bd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404384"
---
# <a name="option-compare-statement"></a><span data-ttu-id="bd32b-102">Option Compare 문</span><span class="sxs-lookup"><span data-stu-id="bd32b-102">Option Compare Statement</span></span>
<span data-ttu-id="bd32b-103">문자열 데이터를 비교할 때 사용할 기본 비교 방법을 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="bd32b-103">Declares the default comparison method to use when comparing string data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd32b-104">구문</span><span class="sxs-lookup"><span data-stu-id="bd32b-104">Syntax</span></span>  
  
```vb  
Option Compare { Binary | Text }  
```  
  
## <a name="parts"></a><span data-ttu-id="bd32b-105">부분</span><span class="sxs-lookup"><span data-stu-id="bd32b-105">Parts</span></span>  
  
|<span data-ttu-id="bd32b-106">용어</span><span class="sxs-lookup"><span data-stu-id="bd32b-106">Term</span></span>|<span data-ttu-id="bd32b-107">정의</span><span class="sxs-lookup"><span data-stu-id="bd32b-107">Definition</span></span>|  
|---|---|  
|`Binary`|<span data-ttu-id="bd32b-108">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="bd32b-108">Optional.</span></span> <span data-ttu-id="bd32b-109">문자의 내부 이진 표현에서 파생된 정렬 순서에 따라 문자열을 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="bd32b-109">Results in string comparisons based on a sort order derived from the internal binary representations of the characters.</span></span><br /><br /> <span data-ttu-id="bd32b-110">이 유형의 비교는 문자열에 텍스트로 해석할 수 없는 문자가 포함될 수 있는 경우 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="bd32b-110">This type of comparison is useful especially if the strings can contain characters that are not to be interpreted as text.</span></span> <span data-ttu-id="bd32b-111">이 경우 대/소문자 미구분 등의 영문자 동일 여부에 따라 비교 결과가 달라지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bd32b-111">In this case, you do not want to bias comparisons with alphabetical equivalences, such as case insensitivity.</span></span>|  
|`Text`|<span data-ttu-id="bd32b-112">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="bd32b-112">Optional.</span></span> <span data-ttu-id="bd32b-113">시스템의 로캘에 따라 결정되는 대/소문자 미구분 텍스트 정렬 순서에 따라 문자열을 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="bd32b-113">Results in string comparisons based on a case-insensitive text sort order determined by your system's locale.</span></span><br /><br /> <span data-ttu-id="bd32b-114">문자열에 텍스트 문자만 포함되며 대/소문자 미구분, 밀접하게 관련된 문자 등의 영문자 동일 여부를 고려하여 이러한 문자를 비교하려는 경우에는 이 유형의 비교가 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="bd32b-114">This type of comparison is useful if your strings contain all text characters, and you want to compare them taking into account alphabetic equivalences such as case insensitivity and closely related letters.</span></span> <span data-ttu-id="bd32b-115">예를 들어 `A`와 `a`를 같은 문자로 간주하고 `Ä` 및 `ä`가 `B` 및 `b` 앞에 온다고 간주할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd32b-115">For example, you might want to consider `A` and `a` to be equal, and `Ä` and `ä` to come before `B` and `b`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd32b-116">설명</span><span class="sxs-lookup"><span data-stu-id="bd32b-116">Remarks</span></span>  
 <span data-ttu-id="bd32b-117">`Option Compare` 문은 사용하는 경우 파일에서 다른 소스 코드 문 앞에 나와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd32b-117">If used, the `Option Compare` statement must appear in a file before any other source code statements.</span></span>  
  
 <span data-ttu-id="bd32b-118">`Option Compare` 문은 문자열 비교 방법(`Binary` 또는 `Text`)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bd32b-118">The `Option Compare` statement specifies the string comparison method (`Binary` or `Text`).</span></span>  <span data-ttu-id="bd32b-119">기본 텍스트 비교 방법은 `Binary`입니다.</span><span class="sxs-lookup"><span data-stu-id="bd32b-119">The default text comparison method is `Binary`.</span></span>  
  
 <span data-ttu-id="bd32b-120">`Binary` 비교에서는 각 문자열 내 각 문자의 숫자 유니코드 값을 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="bd32b-120">A `Binary` comparison compares the numeric Unicode value of each character in each string.</span></span> <span data-ttu-id="bd32b-121">`Text` 비교에서는 현재 문화권의 어휘 의미에 따라 각 유니코드 문자를 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="bd32b-121">A `Text` comparison compares each Unicode character based on its lexical meaning in the current culture.</span></span>  
  
 <span data-ttu-id="bd32b-122">Microsoft windows에서 정렬 순서는 코드 페이지에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd32b-122">In Microsoft Windows, sort order is determined by the code page.</span></span> <span data-ttu-id="bd32b-123">자세한 내용은 [코드 페이지](/cpp/c-runtime-library/code-pages) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bd32b-123">For more information, see [Code Pages](/cpp/c-runtime-library/code-pages).</span></span>  
  
 <span data-ttu-id="bd32b-124">다음 예제에서는 `Option Compare Binary`를 사용하여 영어/유럽어 코드 페이지(ANSI 1252)의 문자를 정렬합니다. 그러면 일반적인 이진 정렬 순서가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd32b-124">In the following example, characters in the English/European code page (ANSI 1252) are sorted by using `Option Compare Binary`, which produces a typical binary sort order.</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="bd32b-125">`Option Compare Text`를 사용하여 같은 코드 페이지의 같은 문자를 정렬하면 다음 텍스트 정렬 순서가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd32b-125">When the same characters in the same code page are sorted by using `Option Compare Text`, the following text sort order is produced.</span></span>  
  
 `(A=a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
## <a name="when-an-option-compare-statement-is-not-present"></a><span data-ttu-id="bd32b-126">Option Compare 문이 없는 경우</span><span class="sxs-lookup"><span data-stu-id="bd32b-126">When an Option Compare Statement Is Not Present</span></span>  
 <span data-ttu-id="bd32b-127">소스 코드에 문이 포함 되어 있지 않은 경우 `Option Compare` 컴파일 페이지에서 **Option Compare** 설정이 사용 됩니다 [(Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) .</span><span class="sxs-lookup"><span data-stu-id="bd32b-127">If the source code does not contain an `Option Compare` statement, the **Option Compare** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="bd32b-128">명령줄 컴파일러를 사용 하는 경우 [-옵션 비교](../../reference/command-line-compiler/optioncompare.md) 컴파일러 옵션에 지정 된 설정이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd32b-128">If you use the command-line compiler, the setting specified by the [-optioncompare](../../reference/command-line-compiler/optioncompare.md) compiler option is used.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
#### <a name="to-set-option-compare-in-the-ide"></a><span data-ttu-id="bd32b-129">IDE에서 Option Compare를 설정하려면</span><span class="sxs-lookup"><span data-stu-id="bd32b-129">To set Option Compare in the IDE</span></span>  
  
1. <span data-ttu-id="bd32b-130">**솔루션 탐색기**에서 프로젝트를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd32b-130">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="bd32b-131">**프로젝트** 메뉴에서 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bd32b-131">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="bd32b-132">**컴파일** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bd32b-132">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="bd32b-133">**옵션 비교** 상자에서 값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd32b-133">Set the value in the **Option Compare** box.</span></span>  
  
 <span data-ttu-id="bd32b-134">프로젝트를 만들 때 **컴파일** 탭의 **옵션 비교** 설정이 **옵션** 대화 상자의 **옵션 비교** 설정으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd32b-134">When you create a project, the **Option Compare** setting on the **Compile** tab is set to the **Option Compare** setting in the **Options** dialog box.</span></span> <span data-ttu-id="bd32b-135">이 설정을 변경 하려면 **도구** 메뉴에서 **옵션**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd32b-135">To change this setting, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="bd32b-136">**옵션** 대화 상자에서 **프로젝트 및 솔루션**을 확장하고 **VB 기본값**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bd32b-136">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="bd32b-137">**VB 기본값** 의 초기 기본 설정은 **Binary**입니다.</span><span class="sxs-lookup"><span data-stu-id="bd32b-137">The initial default setting in **VB Defaults** is **Binary**.</span></span>  
  
#### <a name="to-set-option-compare-on-the-command-line"></a><span data-ttu-id="bd32b-138">명령줄에서 Option Compare를 설정하려면</span><span class="sxs-lookup"><span data-stu-id="bd32b-138">To set Option Compare on the command line</span></span>  
  
- <span data-ttu-id="bd32b-139">**Vbc** 명령에 [-옵션 compare](../../reference/command-line-compiler/optioncompare.md) 컴파일러 옵션을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd32b-139">Include the [-optioncompare](../../reference/command-line-compiler/optioncompare.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd32b-140">예제</span><span class="sxs-lookup"><span data-stu-id="bd32b-140">Example</span></span>  
 <span data-ttu-id="bd32b-141">다음 예제에서는 `Option Compare` 문을 사용하여 이진 비교를 기본 문자열 비교 방법으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="bd32b-141">The following example uses the `Option Compare` statement to set the binary comparison as the default string comparison method.</span></span> <span data-ttu-id="bd32b-142">이 코드를 사용하려면 `Option Compare Binary` 문의 주석 처리를 제거하여 소스 파일 맨 위에 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="bd32b-142">To use this code, uncomment the `Option Compare Binary` statement, and put it at the top of the source file.</span></span>  
  
 [!code-vb[VbVbalrStatements#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#45)]  
  
## <a name="example"></a><span data-ttu-id="bd32b-143">예제</span><span class="sxs-lookup"><span data-stu-id="bd32b-143">Example</span></span>  
 <span data-ttu-id="bd32b-144">다음 예제에서는 `Option Compare` 문을 사용하여 대/소문자 미구분 텍스트 정렬 순서를 기본 문자열 비교 방법으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="bd32b-144">The following example uses the `Option Compare` statement to set the case-insensitive text sort order as the default string comparison method.</span></span> <span data-ttu-id="bd32b-145">이 코드를 사용하려면 `Option Compare Text` 문의 주석 처리를 제거하여 소스 파일 맨 위에 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="bd32b-145">To use this code, uncomment the `Option Compare Text` statement, and put it at the top of the source file.</span></span>  
  
 [!code-vb[VbVbalrStatements#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#46)]  
  
## <a name="see-also"></a><span data-ttu-id="bd32b-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bd32b-146">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.InStrRev%2A>
- <xref:Microsoft.VisualBasic.Strings.Replace%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [<span data-ttu-id="bd32b-147">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="bd32b-147">-optioncompare</span></span>](../../reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="bd32b-148">비교 연산자</span><span class="sxs-lookup"><span data-stu-id="bd32b-148">Comparison Operators</span></span>](../operators/comparison-operators.md)
- [<span data-ttu-id="bd32b-149">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bd32b-149">Comparison Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="bd32b-150">Like 연산자</span><span class="sxs-lookup"><span data-stu-id="bd32b-150">Like Operator</span></span>](../operators/like-operator.md)
- [<span data-ttu-id="bd32b-151">문자열 함수</span><span class="sxs-lookup"><span data-stu-id="bd32b-151">String Functions</span></span>](../functions/string-functions.md)
- [<span data-ttu-id="bd32b-152">Option Explicit 문</span><span class="sxs-lookup"><span data-stu-id="bd32b-152">Option Explicit Statement</span></span>](option-explicit-statement.md)
- [<span data-ttu-id="bd32b-153">Option Strict 문</span><span class="sxs-lookup"><span data-stu-id="bd32b-153">Option Strict Statement</span></span>](option-strict-statement.md)
