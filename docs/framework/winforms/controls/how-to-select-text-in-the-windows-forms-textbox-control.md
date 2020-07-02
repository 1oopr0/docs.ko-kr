---
title: TextBox 컨트롤에서 텍스트 선택
description: Windows Forms TextBox 컨트롤에서 프로그래밍 방식으로 텍스트를 선택 하는 방법을 알아봅니다. 또한 발견 된 문자열의 위치를 판독기에 시각적으로 알리는 방법에 대해 알아봅니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], selecting text programmatically
- text boxes [Windows Forms], selecting text programmatically
- text [Windows Forms], selecting in text boxes programmatically
ms.assetid: 8c591546-6a01-45c7-8e03-f78431f903b1
ms.openlocfilehash: b8fdaff76461c4d6766dfc6afaef5e814d982834
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621563"
---
# <a name="how-to-select-text-in-the-windows-forms-textbox-control"></a><span data-ttu-id="5d5c7-104">방법: Windows Forms TextBox 컨트롤에서 텍스트 선택</span><span class="sxs-lookup"><span data-stu-id="5d5c7-104">How to: Select Text in the Windows Forms TextBox Control</span></span>
<span data-ttu-id="5d5c7-105">Windows Forms 컨트롤에서 프로그래밍 방식으로 텍스트를 선택할 수 있습니다 <xref:System.Windows.Forms.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="5d5c7-105">You can select text programmatically in the Windows Forms <xref:System.Windows.Forms.TextBox> control.</span></span> <span data-ttu-id="5d5c7-106">예를 들어 텍스트에서 특정 문자열을 검색 하는 함수를 만드는 경우 텍스트를 선택 하 여 발견 된 문자열의 위치를 판독기에 시각적으로 경고할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d5c7-106">For example, if you create a function that searches text for a particular string, you can select the text to visually alert the reader of the found string's position.</span></span>  
  
### <a name="to-select-text-programmatically"></a><span data-ttu-id="5d5c7-107">프로그래밍 방식으로 텍스트를 선택 하려면</span><span class="sxs-lookup"><span data-stu-id="5d5c7-107">To select text programmatically</span></span>  
  
1. <span data-ttu-id="5d5c7-108">속성을 <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> 선택 하려는 텍스트의 시작 부분으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d5c7-108">Set the <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property to the beginning of the text you want to select.</span></span>  
  
     <span data-ttu-id="5d5c7-109"><xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A>속성은 텍스트 문자열 내에서 삽입 지점을 나타내는 숫자입니다. 0은 맨 왼쪽 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="5d5c7-109">The <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property is a number that indicates the insertion point within the string of text, with 0 being the left-most position.</span></span> <span data-ttu-id="5d5c7-110"><xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A>속성이 텍스트 상자의 문자 수보다 크거나 같은 값으로 설정 된 경우 삽입 지점은 마지막 문자 뒤에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5d5c7-110">If the <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property is set to a value equal to or greater than the number of characters in the text box, the insertion point is placed after the last character.</span></span>  
  
2. <span data-ttu-id="5d5c7-111">속성을 <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> 선택 하려는 텍스트의 길이로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d5c7-111">Set the <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> property to the length of the text you want to select.</span></span>  
  
     <span data-ttu-id="5d5c7-112"><xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A>속성은 삽입 지점의 너비를 설정 하는 숫자 값입니다.</span><span class="sxs-lookup"><span data-stu-id="5d5c7-112">The <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> property is a numeric value that sets the width of the insertion point.</span></span> <span data-ttu-id="5d5c7-113">를 <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> 0 보다 큰 값으로 설정 하면 현재 삽입 지점부터 시작 하 여 문자 수가 선택 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5d5c7-113">Setting the <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> to a number greater than 0 causes that number of characters to be selected, starting from the current insertion point.</span></span>  
  
3. <span data-ttu-id="5d5c7-114">필드 속성을 통해 선택한 텍스트에 액세스 합니다 <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A> .</span><span class="sxs-lookup"><span data-stu-id="5d5c7-114">(Optional) Access the selected text through the <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A> property.</span></span>  
  
     <span data-ttu-id="5d5c7-115">아래 코드는 컨트롤의 이벤트가 발생할 때 텍스트 상자의 내용을 선택 합니다 <xref:System.Windows.Forms.Control.Enter> .</span><span class="sxs-lookup"><span data-stu-id="5d5c7-115">The code below selects the contents of a text box when the control's <xref:System.Windows.Forms.Control.Enter> event occurs.</span></span> <span data-ttu-id="5d5c7-116">이 예에서는 텍스트 상자에 <xref:System.Windows.Forms.TextBox.Text%2A> 또는 빈 문자열이 아닌 속성 값이 있는지 여부를 확인 합니다 `null` .</span><span class="sxs-lookup"><span data-stu-id="5d5c7-116">This example checks if the text box has a value for the <xref:System.Windows.Forms.TextBox.Text%2A> property that is not `null` or an empty string.</span></span> <span data-ttu-id="5d5c7-117">텍스트 상자에 포커스가 있으면 텍스트 상자의 현재 텍스트가 선택 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5d5c7-117">When the text box receives the focus, the current text in the text box is selected.</span></span> <span data-ttu-id="5d5c7-118">`TextBox1_Enter`이벤트 처리기는 컨트롤에 바인딩되어야 합니다. 자세한 내용은 [방법: 런타임에 Windows Forms 이벤트 처리기 만들기](../how-to-create-event-handlers-at-run-time-for-windows-forms.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5d5c7-118">The `TextBox1_Enter` event handler must be bound to the control; for more information, see [How to: Create Event Handlers at Run Time for Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span></span>  
  
     <span data-ttu-id="5d5c7-119">이 예를 테스트 하려면 입력란에 포커스가 있을 때까지 Tab 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="5d5c7-119">To test this example, press the Tab key until the text box has the focus.</span></span> <span data-ttu-id="5d5c7-120">텍스트 상자를 클릭 하면 텍스트가 선택 취소 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5d5c7-120">If you click in the text box, the text is unselected.</span></span>  
  
    ```vb  
    Private Sub TextBox1_Enter(ByVal sender As Object, ByVal e As System.EventArgs) Handles TextBox1.Enter  
       If (Not String.IsNullOrEmpty(TextBox1.Text)) Then  
          TextBox1.SelectionStart = 0  
          TextBox1.SelectionLength = TextBox1.Text.Length  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_Enter(object sender, System.EventArgs e){  
       if (!String.IsNullOrEmpty(textBox1.Text))  
       {  
          textBox1.SelectionStart = 0;  
          textBox1.SelectionLength = textBox1.Text.Length;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void textBox1_Enter(System::Object ^ sender,  
          System::EventArgs ^ e) {  
       if (!System::String::IsNullOrEmpty(textBox1->Text))  
       {  
          textBox1->SelectionStart = 0;  
          textBox1->SelectionLength = textBox1->Text->Length;  
       }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5d5c7-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5d5c7-121">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="5d5c7-122">TextBox 컨트롤 개요</span><span class="sxs-lookup"><span data-stu-id="5d5c7-122">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="5d5c7-123">방법: Windows Forms TextBox 컨트롤에서 삽입 지점 제어</span><span class="sxs-lookup"><span data-stu-id="5d5c7-123">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="5d5c7-124">방법: Windows Forms TextBox 컨트롤을 사용하여 암호 텍스트 상자 만들기</span><span class="sxs-lookup"><span data-stu-id="5d5c7-124">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="5d5c7-125">방법: 읽기 전용 텍스트 상자 만들기</span><span class="sxs-lookup"><span data-stu-id="5d5c7-125">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="5d5c7-126">방법: 문자열에 인용 부호 넣기</span><span class="sxs-lookup"><span data-stu-id="5d5c7-126">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="5d5c7-127">방법: Windows Forms TextBox 컨트롤에서 여러 줄 표시</span><span class="sxs-lookup"><span data-stu-id="5d5c7-127">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="5d5c7-128">TextBox 컨트롤</span><span class="sxs-lookup"><span data-stu-id="5d5c7-128">TextBox Control</span></span>](textbox-control-windows-forms.md)
