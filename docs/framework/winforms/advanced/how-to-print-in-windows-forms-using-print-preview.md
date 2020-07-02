---
title: 인쇄 미리 보기를 사용 하 여 인쇄
description: Windows Forms PrintPreviewDialog 컨트롤을 사용 하 여 인쇄 미리 보기 서비스를 응용 프로그램에 추가 하는 방법을 알아봅니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing [Windows Forms], using print preview
- printing [Windows Forms], with print preview
- print preview
ms.assetid: 4a16f7e2-ae10-4485-b0ae-3d558334d0fe
ms.openlocfilehash: abcf77db40f648df1a0cd49922bb49e5c9407811
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621615"
---
# <a name="how-to-print-in-windows-forms-using-print-preview"></a><span data-ttu-id="fa4be-103">방법: Windows Forms에서 인쇄 미리 보기를 사용하여 인쇄</span><span class="sxs-lookup"><span data-stu-id="fa4be-103">How to: Print in Windows Forms Using Print Preview</span></span>
<span data-ttu-id="fa4be-104">Windows Forms 프로그래밍에서는 인쇄 서비스 외에 인쇄 미리 보기를 제공하는 것이 일반적입니다.</span><span class="sxs-lookup"><span data-stu-id="fa4be-104">It is very common in Windows Forms programming to offer print preview in addition to printing services.</span></span> <span data-ttu-id="fa4be-105">인쇄 미리 보기 서비스를 애플리케이션에 추가하는 편리한 방법은 파일 인쇄에 대한 <xref:System.Windows.Forms.PrintPreviewDialog> 이벤트 처리 논리와 함께 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 컨트롤을 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fa4be-105">An easy way to add print preview services to your application is to use a <xref:System.Windows.Forms.PrintPreviewDialog> control in combination with the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event-handling logic for printing a file.</span></span>  
  
### <a name="to-preview-a-text-document-with-a-printpreviewdialog-control"></a><span data-ttu-id="fa4be-106">PrintPreviewDialog 컨트롤을 사용하여 텍스트 문서를 미리 보려면</span><span class="sxs-lookup"><span data-stu-id="fa4be-106">To preview a text document with a PrintPreviewDialog control</span></span>  
  
1. <span data-ttu-id="fa4be-107"><xref:System.Windows.Forms.PrintPreviewDialog>, <xref:System.Drawing.Printing.PrintDocument>및 두 개의 문자열을 폼에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fa4be-107">Add a <xref:System.Windows.Forms.PrintPreviewDialog>, <xref:System.Drawing.Printing.PrintDocument>, and two strings to your form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#1)]  
  
2. <span data-ttu-id="fa4be-108"><xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> 속성을 인쇄할 문서로 설정하고 문서를 연 다음 이전에 추가한 문자열까지 문서 내용을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="fa4be-108">Set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property to the document you wish to print, and open and read the document's contents to the string you added previously.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#2)]  
  
3. <span data-ttu-id="fa4be-109">문서를 인쇄할 때와 마찬가지로, <xref:System.Drawing.Printing.PrintDocument.PrintPage> 이벤트 처리기에서 <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> 클래스의 <xref:System.Drawing.Printing.PrintPageEventArgs> 속성과 파일 내용을 사용하여 페이지당 줄 수를 계산하고 문서 내용을 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="fa4be-109">As you would for printing the document, in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class and the file contents to calculate lines per page and render the document's contents.</span></span> <span data-ttu-id="fa4be-110">각 페이지가 그려진 후 마지막 페이지인지 확인하고 <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> 의 <xref:System.Drawing.Printing.PrintPageEventArgs> 속성을 적절하게 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="fa4be-110">After each page is drawn, check to see if it is the last page, and set the <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> accordingly.</span></span> <span data-ttu-id="fa4be-111"><xref:System.Drawing.Printing.PrintDocument.PrintPage> 가 <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> 가 될 때까지 `false`이벤트가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="fa4be-111">The <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised until <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> is `false`.</span></span> <span data-ttu-id="fa4be-112">문서 렌더링이 완료되면 렌더링할 문자열을 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="fa4be-112">When the document has finished rendering, reset the string to be rendered.</span></span> <span data-ttu-id="fa4be-113">또한 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 이벤트가 해당 이벤트 처리 메서드에 연결되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="fa4be-113">Also, make sure the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is associated with its event-handling method.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="fa4be-114">애플리케이션에서 인쇄를 구현한 경우 2단계와 3단계를 이미 완료했을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa4be-114">You may have already completed steps 2 and 3 if you have implemented printing in your application.</span></span>  
  
     <span data-ttu-id="fa4be-115">다음 코드 예제에서 이벤트 처리기는 "testPage.txt" 파일을 폼에 사용된 것과 동일한 글꼴로 인쇄하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa4be-115">In the following code example, the event handler is used to print the "testPage.txt" file in the same font used on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#3)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#3)]  
  
4. <span data-ttu-id="fa4be-116"><xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> 컨트롤의 <xref:System.Windows.Forms.PrintPreviewDialog> 속성을 폼의 <xref:System.Drawing.Printing.PrintDocument> 구성 요소로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="fa4be-116">Set the <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintPreviewDialog> control to the <xref:System.Drawing.Printing.PrintDocument> component on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#5)]  
  
5. <span data-ttu-id="fa4be-117"><xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 컨트롤에 대해 <xref:System.Windows.Forms.PrintPreviewDialog> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="fa4be-117">Call the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method on the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="fa4be-118">일반적으로 단추의 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 이벤트 처리 메서드에서 <xref:System.Windows.Forms.Control.Click> 를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="fa4be-118">You would typically call <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> from the <xref:System.Windows.Forms.Control.Click> event-handling method of a button.</span></span> <span data-ttu-id="fa4be-119"><xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 를 호출하면 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 이벤트가 발생하고 출력이 <xref:System.Windows.Forms.PrintPreviewDialog> 컨트롤에 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa4be-119">Calling <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> raises the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event and renders the output to the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="fa4be-120">사용자가 대화 상자에서 인쇄 아이콘을 클릭하면 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 이벤트가 다시 발생하여 미리 보기 대화 상자 대신 프린터로 출력을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="fa4be-120">When the user clicks the print icon on the dialog, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised again, sending the output to the printer instead of the preview dialog.</span></span> <span data-ttu-id="fa4be-121">이 때문에 3단계에서 렌더링 프로세스가 끝날 때 문자열을 다시 설정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fa4be-121">This is why the string is reset at the end of the rendering process in step 3.</span></span>  
  
     <span data-ttu-id="fa4be-122">다음 코드 예제에서는 폼의 단추에 대한 <xref:System.Windows.Forms.Control.Click> 이벤트 처리 메서드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fa4be-122">The following code example shows the <xref:System.Windows.Forms.Control.Click> event-handling method for a button on the form.</span></span> <span data-ttu-id="fa4be-123">이 이벤트 처리 메서드는 문서를 읽고 인쇄 미리 보기 대화 상자를 표시하는 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="fa4be-123">This event-handling method calls the methods to read the document and show the print preview dialog.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#4)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="fa4be-124">예제</span><span class="sxs-lookup"><span data-stu-id="fa4be-124">Example</span></span>  
 [!code-csharp[System.Drawing.Printing.PrintPreviewExample#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintPreviewExample#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fa4be-125">코드 컴파일</span><span class="sxs-lookup"><span data-stu-id="fa4be-125">Compiling the Code</span></span>  
 <span data-ttu-id="fa4be-126">이 예제에는 다음 사항이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="fa4be-126">This example requires:</span></span>  
  
- <span data-ttu-id="fa4be-127">System, System.Windows.Forms, System.Drawing 어셈블리에 대한 참조</span><span class="sxs-lookup"><span data-stu-id="fa4be-127">References to the System, System.Windows.Forms, System.Drawing assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa4be-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fa4be-128">See also</span></span>

- [<span data-ttu-id="fa4be-129">방법: Windows Forms에서 다중 페이지 텍스트 파일 인쇄</span><span class="sxs-lookup"><span data-stu-id="fa4be-129">How to: Print a Multi-Page Text File in Windows Forms</span></span>](how-to-print-a-multi-page-text-file-in-windows-forms.md)
- [<span data-ttu-id="fa4be-130">Windows Forms 인쇄 지원</span><span class="sxs-lookup"><span data-stu-id="fa4be-130">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
- [<span data-ttu-id="fa4be-131">Windows Forms의 인쇄 추가 보안</span><span class="sxs-lookup"><span data-stu-id="fa4be-131">More Secure Printing in Windows Forms</span></span>](../more-secure-printing-in-windows-forms.md)
