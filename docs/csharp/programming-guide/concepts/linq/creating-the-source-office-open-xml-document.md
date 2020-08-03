---
title: 원본 Office Open XML 문서 만들기(C#)
description: C# 자습서와 함께 사용할 Office Open XML WordprocessingML 문서를 만듭니다. 이 문서에는 Microsoft Office가 필요합니다.
ms.date: 07/20/2015
ms.assetid: 653c8cdb-73be-4dc2-927f-924cfb4ed9ed
ms.openlocfilehash: e6d6908ee6560218793454f3871705e74095f543
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103993"
---
# <a name="creating-the-source-office-open-xml-document-c"></a><span data-ttu-id="8fcfe-104">원본 Office Open XML 문서 만들기(C#)</span><span class="sxs-lookup"><span data-stu-id="8fcfe-104">Creating the Source Office Open XML Document (C#)</span></span>

<span data-ttu-id="8fcfe-105">이 항목에서는 이 자습서의 다른 예제에서 사용하는 Office Open XML WordprocessingML 문서를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8fcfe-105">This topic shows how to create the Office Open XML WordprocessingML document that the other examples in this tutorial use.</span></span> <span data-ttu-id="8fcfe-106">이러한 지침을 따르는 경우 출력은 각 예제에서 제공되는 출력과 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="8fcfe-106">If you follow these instructions, your output will match the output provided in each example.</span></span>

<span data-ttu-id="8fcfe-107">그러나 이 자습서의 예제는 모든 유효한 WordprocessingML 문서와 함께 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="8fcfe-107">However, the examples in this tutorial will work with any valid WordprocessingML document.</span></span>

<span data-ttu-id="8fcfe-108">이 자습서에서 사용하는 문서를 만들려면 Microsoft Office 2007 이상이 설치되어 있거나 Word, Excel 및 PowerPoint 2007 파일 형식용 Microsoft Office 호환 기능 팩이 포함된 Microsoft Office 2003이 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fcfe-108">To create the document that this tutorial uses, you must either have Microsoft Office 2007 or later installed, or you must have Microsoft Office 2003 with the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>

## <a name="creating-the-wordprocessingml-document"></a><span data-ttu-id="8fcfe-109">WordprocessingML 문서 만들기</span><span class="sxs-lookup"><span data-stu-id="8fcfe-109">Creating the WordprocessingML Document</span></span>

#### <a name="to-create-the-wordprocessingml-document"></a><span data-ttu-id="8fcfe-110">WordprocessingML 문서를 만들려면</span><span class="sxs-lookup"><span data-stu-id="8fcfe-110">To create the WordprocessingML document</span></span>

1. <span data-ttu-id="8fcfe-111">Microsoft Word 문서를 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8fcfe-111">Create a new Microsoft Word document.</span></span>

2. <span data-ttu-id="8fcfe-112">다음 텍스트를 새 문서에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="8fcfe-112">Paste the following text into the new document:</span></span>

    ```text
    Parsing WordprocessingML with LINQ to XML

    The following example prints to the console.

    using System;

    class Program {
        public static void Main(string[] args) {
            Console.WriteLine("Hello World");
        }
    }

    This example produces the following output:

    Hello World
    ```

3. <span data-ttu-id="8fcfe-113">"제목 1" 스타일로 첫 번째 줄의 서식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8fcfe-113">Format the first line with the style "Heading 1".</span></span>

4. <span data-ttu-id="8fcfe-114">C# 코드가 포함된 줄을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8fcfe-114">Select the lines that contain the C# code.</span></span> <span data-ttu-id="8fcfe-115">첫 번째 줄은 `using` 키워드로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="8fcfe-115">The first line starts with the `using` keyword.</span></span> <span data-ttu-id="8fcfe-116">마지막 줄은 마지막 닫는 괄호입니다.</span><span class="sxs-lookup"><span data-stu-id="8fcfe-116">The last line is the last closing brace.</span></span> <span data-ttu-id="8fcfe-117">courier 글꼴로 줄의 서식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8fcfe-117">Format the lines with the courier font.</span></span> <span data-ttu-id="8fcfe-118">새 스타일로 줄의 서식을 지정한 다음 새 스타일의 이름을 "Code"로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8fcfe-118">Format them with a new style, and name the new style "Code".</span></span>

5. <span data-ttu-id="8fcfe-119">마지막으로 출력이 포함된 전체 줄을 선택하고 `Code` 스타일로 서식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8fcfe-119">Finally, select the entire line that contains the output, and format it with the `Code` style.</span></span>

6. <span data-ttu-id="8fcfe-120">문서를 저장하고 SampleDoc.docx로 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8fcfe-120">Save the document, and name it SampleDoc.docx.</span></span>

    > [!NOTE]
    > <span data-ttu-id="8fcfe-121">Microsoft Word 2003을 사용하는 경우 **파일 형식** 드롭다운 목록에서 **Word 2007 문서**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8fcfe-121">If you are using Microsoft Word 2003, select **Word 2007 Document** in the **Save as Type** drop-down list.</span></span>
