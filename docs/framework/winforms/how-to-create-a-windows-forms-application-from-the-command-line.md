---
title: 명령줄에서 Windows Forms 응용 프로그램 만들기
titleSuffix: ''
description: 명령줄에서 Windows Forms 응용 프로그램을 만들고 실행 하는 기본 단계를 완료 하는 방법에 대해 알아봅니다.
ms.date: 03/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, application development from command line
- Windows Forms, getting started
- Windows Forms, creating basic form
ms.assetid: 45ad3f8b-1c26-4c9f-91a9-3bb0759a47a4
ms.openlocfilehash: b63bf884b9fd03a0510c7f240f19d7a14196971a
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903456"
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a><span data-ttu-id="07d92-103">방법: 명령줄에서 Windows Forms 응용 프로그램 만들기</span><span class="sxs-lookup"><span data-stu-id="07d92-103">How to: Create a Windows Forms application from the command line</span></span>

<span data-ttu-id="07d92-104">다음 절차에서는 명령줄에서 Windows Forms 애플리케이션을 만들고 실행하기 위해 완료해야 하는 기본 단계를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="07d92-104">The following procedures describe the basic steps that you must complete to create and run a Windows Forms application from the command line.</span></span> <span data-ttu-id="07d92-105">Visual Studio에서는 이러한 절차가 광범위하게 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="07d92-105">There is extensive support for these procedures in Visual Studio.</span></span>  <span data-ttu-id="07d92-106">또한 [연습: WPF에서 Windows Forms 컨트롤 호스팅을](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="07d92-106">Also see [Walkthrough: Hosting a Windows Forms Control in WPF](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span></span>
  
## <a name="procedure"></a><span data-ttu-id="07d92-107">절차</span><span class="sxs-lookup"><span data-stu-id="07d92-107">Procedure</span></span>  
  
#### <a name="to-create-the-form"></a><span data-ttu-id="07d92-108">폼을 만들려면</span><span class="sxs-lookup"><span data-stu-id="07d92-108">To create the form</span></span>  
  
1. <span data-ttu-id="07d92-109">빈 코드 파일에 다음 또는 문을 입력 합니다 `Imports` `using` .</span><span class="sxs-lookup"><span data-stu-id="07d92-109">In an empty code file, type the following `Imports` or `using` statements:</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2. <span data-ttu-id="07d92-110">`Form1`Form 클래스에서 상속 되는 이라는 클래스를 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="07d92-110">Declare a class named `Form1` that inherits from the Form class:</span></span>
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3. <span data-ttu-id="07d92-111">에 대해 매개 변수가 없는 생성자를 만듭니다 `Form1` .</span><span class="sxs-lookup"><span data-stu-id="07d92-111">Create a parameterless constructor for `Form1`.</span></span>
  
     <span data-ttu-id="07d92-112">이후 절차에서 생성자에 더 많은 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="07d92-112">You will add more code to the constructor in a subsequent procedure.</span></span>
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4. <span data-ttu-id="07d92-113">클래스에 `Main` 메서드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="07d92-113">Add a `Main` method to the class.</span></span>
  
    1. <span data-ttu-id="07d92-114">를 <xref:System.STAThreadAttribute> c # 메서드에 적용 `Main` 하 여 Windows Forms 응용 프로그램이 단일 스레드 아파트 인지 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="07d92-114">Apply the <xref:System.STAThreadAttribute> to the C# `Main` method to specify your Windows Forms application is a single-threaded apartment.</span></span> <span data-ttu-id="07d92-115">(Visual Basic를 사용 하 여 개발 된 Windows forms 응용 프로그램은 기본적으로 단일 스레드 아파트 모델을 사용 하므로 Visual Basic에서는이 특성이 필요 하지 않습니다.)</span><span class="sxs-lookup"><span data-stu-id="07d92-115">(The attribute is not necessary in Visual Basic, since Windows forms applications developed with Visual Basic use a single-threaded apartment model by default.)</span></span>  
  
    2. <span data-ttu-id="07d92-116"><xref:System.Windows.Forms.Application.EnableVisualStyles%2A>을 호출 하 여 응용 프로그램에 운영 체제 스타일을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="07d92-116">Call <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> to apply operating system styles to your application.</span></span>  
  
    3. <span data-ttu-id="07d92-117">폼 인스턴스를 만들고 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="07d92-117">Create an instance of the form and run it.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### <a name="to-compile-and-run-the-application"></a><span data-ttu-id="07d92-118">애플리케이션을 컴파일하고 실행하려면</span><span class="sxs-lookup"><span data-stu-id="07d92-118">To compile and run the application</span></span>  
  
1. <span data-ttu-id="07d92-119">.NET Framework 명령 프롬프트에서 `Form1` 클래스를 만든 디렉터리로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="07d92-119">At the .NET Framework command prompt, navigate to the directory you created the `Form1` class.</span></span>  
  
2. <span data-ttu-id="07d92-120">폼을 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="07d92-120">Compile the form.</span></span>  
  
    - <span data-ttu-id="07d92-121">C #을 사용 하는 경우 다음을 입력 합니다.`csc form1.cs`</span><span class="sxs-lookup"><span data-stu-id="07d92-121">If you are using C#, type: `csc form1.cs`</span></span>  
  
         `-or-`  
  
    - <span data-ttu-id="07d92-122">Visual Basic를 사용 하는 경우 다음을 입력 합니다.`vbc form1.vb`</span><span class="sxs-lookup"><span data-stu-id="07d92-122">If you are using Visual Basic, type: `vbc form1.vb`</span></span>  
  
3. <span data-ttu-id="07d92-123">명령 프롬프트에 다음을 입력합니다. `Form1.exe`</span><span class="sxs-lookup"><span data-stu-id="07d92-123">At the command prompt, type: `Form1.exe`</span></span>  
  
## <a name="adding-a-control-and-handling-an-event"></a><span data-ttu-id="07d92-124">컨트롤 추가 및 이벤트 처리</span><span class="sxs-lookup"><span data-stu-id="07d92-124">Adding a control and handling an event</span></span>

<span data-ttu-id="07d92-125">이전 절차의 단계에서는 컴파일 및 실행되는 기본 Windows Form을 만드는 방법만 보여 주었습니다.</span><span class="sxs-lookup"><span data-stu-id="07d92-125">The previous procedure steps demonstrated how to just create a basic Windows Form that compiles and runs.</span></span> <span data-ttu-id="07d92-126">다음 절차에서는 컨트롤을 만들고 폼에 추가한 다음 컨트롤에 대한 이벤트를 처리하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="07d92-126">The next procedure will show you how to create and add a control to the form, and handle an event for the control.</span></span> <span data-ttu-id="07d92-127">Windows Forms에 추가할 수 있는 컨트롤에 대 한 자세한 내용은 [Windows Forms 컨트롤](./controls/index.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="07d92-127">For more information about the controls you can add to Windows Forms, see [Windows Forms Controls](./controls/index.md).</span></span>
  
 <span data-ttu-id="07d92-128">Windows Forms 애플리케이션을 만드는 방법을 이해하는 것은 물론 이벤트 기반 프로그래밍 및 사용자 입력을 처리하는 방법도 이해해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="07d92-128">In addition to understanding how to create Windows Forms applications, you should understand event-based programming and how to handle user input.</span></span> <span data-ttu-id="07d92-129">자세한 내용은 [Windows Forms에서 이벤트 처리기 만들기](creating-event-handlers-in-windows-forms.md)및 [사용자 입력 처리](./controls/handling-user-input.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="07d92-129">For more information, see [Creating Event Handlers in Windows Forms](creating-event-handlers-in-windows-forms.md), and [Handling User Input](./controls/handling-user-input.md)</span></span>  
  
#### <a name="to-declare-a-button-control-and-handle-its-click-event"></a><span data-ttu-id="07d92-130">단추 컨트롤을 선언하고 해당 click 이벤트를 처리하려면</span><span class="sxs-lookup"><span data-stu-id="07d92-130">To declare a button control and handle its click event</span></span>  
  
1. <span data-ttu-id="07d92-131">`button1`이라는 단추 컨트롤을 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="07d92-131">Declare a button control named `button1`.</span></span>  
  
2. <span data-ttu-id="07d92-132">생성자에서 단추를 만들고 해당 <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> 및 <xref:System.Windows.Forms.Control.Text%2A> 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="07d92-132">In the constructor, create the button and set its <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> and <xref:System.Windows.Forms.Control.Text%2A> properties.</span></span>  
  
3. <span data-ttu-id="07d92-133">폼에 단추를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="07d92-133">Add the button to the form.</span></span>  
  
     <span data-ttu-id="07d92-134">다음 코드 예제에서는 단추 컨트롤을 선언 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="07d92-134">The following code example demonstrates how to declare the button control:</span></span>
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4. <span data-ttu-id="07d92-135">단추에 대한 <xref:System.Windows.Forms.Control.Click> 이벤트를 처리할 메서드를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="07d92-135">Create a method to handle the <xref:System.Windows.Forms.Control.Click> event for the button.</span></span>  
  
5. <span data-ttu-id="07d92-136">click 이벤트 처리기에서 "Hello World" 메시지와 함께 <xref:System.Windows.Forms.MessageBox>를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="07d92-136">In the click event handler, display a <xref:System.Windows.Forms.MessageBox> with the message, "Hello World".</span></span>  
  
     <span data-ttu-id="07d92-137">다음 코드 예제에서는 단추 컨트롤의 click 이벤트를 처리 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="07d92-137">The following code example demonstrates how to handle the button control's click event:</span></span>
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6. <span data-ttu-id="07d92-138">만든 메서드에 <xref:System.Windows.Forms.Control.Click> 이벤트를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="07d92-138">Associate the <xref:System.Windows.Forms.Control.Click> event with the method you created.</span></span>  
  
     <span data-ttu-id="07d92-139">다음 코드 예제에서는 이벤트를 메서드에 연결하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="07d92-139">The following code example demonstrates how to associate the event with the method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7. <span data-ttu-id="07d92-140">이전 절차에서 설명한 대로 애플리케이션을 컴파일 및 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="07d92-140">Compile and run the application as described in the previous procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07d92-141">예제</span><span class="sxs-lookup"><span data-stu-id="07d92-141">Example</span></span>  

<span data-ttu-id="07d92-142">다음 코드 예제는 이전 절차의 전체 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="07d92-142">The following code example is the complete example from the previous procedures:</span></span>
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="07d92-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="07d92-143">See also</span></span>

- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Control>
- [<span data-ttu-id="07d92-144">Windows Forms의 모양 변경</span><span class="sxs-lookup"><span data-stu-id="07d92-144">Changing the Appearance of Windows Forms</span></span>](changing-the-appearance-of-windows-forms.md)
- [<span data-ttu-id="07d92-145">Windows Forms 애플리케이션 강화</span><span class="sxs-lookup"><span data-stu-id="07d92-145">Enhancing Windows Forms Applications</span></span>](./advanced/index.md)
- [<span data-ttu-id="07d92-146">Windows Forms 시작</span><span class="sxs-lookup"><span data-stu-id="07d92-146">Getting Started with Windows Forms</span></span>](getting-started-with-windows-forms.md)
