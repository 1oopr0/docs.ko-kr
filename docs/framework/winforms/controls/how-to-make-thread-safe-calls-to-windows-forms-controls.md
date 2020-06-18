---
title: 스레드로부터 안전한 컨트롤 호출
ms.date: 02/19/2019
description: 스레드로부터 안전한 방식으로 크로스 스레드 컨트롤을 호출 하 여 앱에서 다중 스레딩을 구현 하는 방법에 대해 알아봅니다.
dev_langs:
- csharp
- vb
f1_keywords:
- EHInvalidOperation.WinForms.IllegalCrossThreadCall
helpviewer_keywords:
- thread safety [Windows Forms], calling controls [Windows Forms]
- calling controls [Windows Forms], thread safety [Windows Forms]
- CheckForIllegalCrossThreadCalls property [Windows Forms]
- Windows Forms controls [Windows Forms], multithreading
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], cross-thread calls
- controls [Windows Forms], multithreading
ms.assetid: 138f38b6-1099-4fd5-910c-390b41cbad35
ms.openlocfilehash: b5f4de7bd3d8d89de98dbe27e2dbf360763670d0
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904184"
---
# <a name="how-to-make-thread-safe-calls-to-windows-forms-controls"></a><span data-ttu-id="cf680-103">방법: 스레드로부터 안전한 호출을 Windows Forms 컨트롤 만들기</span><span class="sxs-lookup"><span data-stu-id="cf680-103">How to: Make thread-safe calls to Windows Forms controls</span></span>

<span data-ttu-id="cf680-104">다중 스레딩을 사용 하면 Windows Forms 앱의 성능을 향상 시킬 수 있지만 Windows Forms 컨트롤에 대 한 액세스는 기본적으로 스레드로부터 안전 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cf680-104">Multithreading can improve the performance of Windows Forms apps, but access to Windows Forms controls isn't inherently thread-safe.</span></span> <span data-ttu-id="cf680-105">다중 스레딩을 통해 코드를 매우 심각 하 고 복잡 한 버그에 노출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf680-105">Multithreading can expose your code to very serious and complex bugs.</span></span> <span data-ttu-id="cf680-106">컨트롤을 조작 하는 두 개 이상의 스레드가 컨트롤을 일관 되지 않은 상태로 강제 적용 하 여 경합 상태, 교착 상태, 중단 또는 중단을 초래할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf680-106">Two or more threads manipulating a control can force the control into an inconsistent state and lead to race conditions, deadlocks, and freezes or hangs.</span></span> <span data-ttu-id="cf680-107">응용 프로그램에서 다중 스레딩을 구현 하는 경우에는 스레드로부터 안전한 방식으로 크로스 스레드 컨트롤을 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf680-107">If you implement multithreading in your app, be sure to call cross-thread controls in a thread-safe way.</span></span> <span data-ttu-id="cf680-108">자세한 내용은 [관리 되는 스레딩 모범 사례](../../../standard/threading/managed-threading-best-practices.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="cf680-108">For more information, see [Managed threading best practices](../../../standard/threading/managed-threading-best-practices.md).</span></span>

<span data-ttu-id="cf680-109">해당 컨트롤을 만들지 않은 스레드에서 Windows Forms 제어를 안전 하 게 호출 하는 방법에는 두 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf680-109">There are two ways to safely call a Windows Forms control from a thread that didn't create that control.</span></span> <span data-ttu-id="cf680-110">메서드를 사용 하 여 <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> 주 스레드에서 만든 대리자를 호출할 수 있습니다. 그러면이 대리자가 컨트롤을 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf680-110">You can use the <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> method to call a delegate created in the main thread, which in turn calls the control.</span></span> <span data-ttu-id="cf680-111">또는 <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> 이벤트 기반 모델을 사용 하 여 백그라운드 스레드에서 수행 된 작업을 결과에 대 한 보고에서 분리 하는를 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf680-111">Or, you can implement a <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>, which uses an event-driven model to separate work done in the background thread from reporting on the results.</span></span>

## <a name="unsafe-cross-thread-calls"></a><span data-ttu-id="cf680-112">안전 하지 않은 크로스 스레드 호출</span><span class="sxs-lookup"><span data-stu-id="cf680-112">Unsafe cross-thread calls</span></span>

<span data-ttu-id="cf680-113">컨트롤을 만들지 않은 스레드에서 직접 호출 하는 것은 안전 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cf680-113">It's unsafe to call a control directly from a thread that didn't create it.</span></span> <span data-ttu-id="cf680-114">다음 코드 조각에서는 컨트롤에 대 한 안전 하지 않은 호출을 보여 줍니다 <xref:System.Windows.Forms.TextBox?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="cf680-114">The following code snippet illustrates an unsafe call to the <xref:System.Windows.Forms.TextBox?displayProperty=nameWithType> control.</span></span> <span data-ttu-id="cf680-115">`Button1_Click`이벤트 처리기는 `WriteTextUnsafe` 주 스레드의 속성을 직접 설정 하는 새 스레드를 만듭니다 <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="cf680-115">The `Button1_Click` event handler creates a new `WriteTextUnsafe` thread, which sets the main thread's <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> property directly.</span></span>

```csharp
private void Button1_Click(object sender, EventArgs e)
{
    thread2 = new Thread(new ThreadStart(WriteTextUnsafe));
    thread2.Start();
}
private void WriteTextUnsafe()
{
    textBox1.Text = "This text was set unsafely.";
}
```

```vb
Private Sub Button1_Click(ByVal sender As Object, e As EventArgs) Handles Button1.Click
    Thread2 = New Thread(New ThreadStart(AddressOf WriteTextUnsafe))
    Thread2.Start()
End Sub

Private Sub WriteTextUnsafe()
    TextBox1.Text = "This text was set unsafely."
End Sub
```

<span data-ttu-id="cf680-116">Visual Studio 디버거는 <xref:System.InvalidOperationException> 메시지, **크로스 스레드 작업이 유효 하지 않은 상태로를 발생 시켜 이러한 안전 하지 않은 스레드 호출을 검색 합니다. "" 컨트롤이 만들어진 스레드가 아닌 스레드에서 액세스 되었습니다.**</span><span class="sxs-lookup"><span data-stu-id="cf680-116">The Visual Studio debugger detects these unsafe thread calls by raising an <xref:System.InvalidOperationException> with the message, **Cross-thread operation not valid. Control "" accessed from a thread other than the thread it was created on.**</span></span> <span data-ttu-id="cf680-117">는 <xref:System.InvalidOperationException> Visual Studio 디버깅 중 안전 하지 않은 크로스 스레드 호출에 대해 항상 발생 하며, 앱 런타임에서 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf680-117">The <xref:System.InvalidOperationException> always occurs for unsafe cross-thread calls during Visual Studio debugging, and may occur at app runtime.</span></span> <span data-ttu-id="cf680-118">문제를 해결 해야 하지만 속성을로 설정 하 여 예외를 비활성화할 수 있습니다 <xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A?displayProperty=nameWithType> `false` .</span><span class="sxs-lookup"><span data-stu-id="cf680-118">You should fix the issue, but you can disable the exception by setting the <xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A?displayProperty=nameWithType> property to `false`.</span></span>

## <a name="safe-cross-thread-calls"></a><span data-ttu-id="cf680-119">안전한 크로스 스레드 호출</span><span class="sxs-lookup"><span data-stu-id="cf680-119">Safe cross-thread calls</span></span>

<span data-ttu-id="cf680-120">다음 코드 예제에서는 코드를 만들지 않은 스레드에서 Windows Forms 제어를 안전 하 게 호출 하는 두 가지 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="cf680-120">The following code examples demonstrate two ways to safely call a Windows Forms control from a thread that didn't create it:</span></span>

1. <span data-ttu-id="cf680-121"><xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName>컨트롤을 호출 하기 위해 주 스레드에서 대리자를 호출 하는 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="cf680-121">The <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> method, which calls a delegate from the main thread to call the control.</span></span>
2. <span data-ttu-id="cf680-122"><xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>이벤트 기반 모델을 제공 하는 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="cf680-122">A <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> component, which offers an event-driven model.</span></span>

<span data-ttu-id="cf680-123">두 예제에서 백그라운드 스레드는 1 초 동안 대기 하 여 해당 스레드에서 수행 되는 작업을 시뮬레이션 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf680-123">In both examples, the background thread sleeps for one second to simulate work being done in that thread.</span></span>

<span data-ttu-id="cf680-124">C # 또는 Visual Basic 명령줄에서 .NET Framework 앱으로 이러한 예제를 빌드하고 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf680-124">You can build and run these examples as .NET Framework apps from the C# or Visual Basic command line.</span></span> <span data-ttu-id="cf680-125">자세한 내용은 [csc.exe를 사용 하 여 명령줄 빌드](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) 또는 [명령줄에서 빌드 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="cf680-125">For more information, see [Command-line building with csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) or [Build from the command line (Visual Basic)](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>

<span data-ttu-id="cf680-126">.NET Core 3.0부터 .NET Core Windows Forms \* \<folder name> .csproj\* 프로젝트 파일이 있는 폴더에서 Windows .net core 앱으로 예제를 빌드하고 실행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf680-126">Starting with .NET Core 3.0, you can also build and run the examples as Windows .NET Core apps from a folder that has a .NET Core Windows Forms *\<folder name>.csproj* project file.</span></span>

## <a name="example-use-the-invoke-method-with-a-delegate"></a><span data-ttu-id="cf680-127">예제: 대리자와 함께 Invoke 메서드 사용</span><span class="sxs-lookup"><span data-stu-id="cf680-127">Example: Use the Invoke method with a delegate</span></span>

<span data-ttu-id="cf680-128">다음 예제에서는 Windows Forms 컨트롤을 스레드로부터 안전 하 게 호출 하는 패턴을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="cf680-128">The following example demonstrates a pattern for ensuring thread-safe calls to a Windows Forms control.</span></span> <span data-ttu-id="cf680-129">이 메서드는 <xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName> 컨트롤의 스레드 id를 호출 하는 스레드 id와 비교 하는 속성을 쿼리 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf680-129">It queries the <xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName> property, which compares the control's creating thread ID to the calling thread ID.</span></span> <span data-ttu-id="cf680-130">스레드 Id가 동일 하면 컨트롤을 직접 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf680-130">If the thread IDs are the same, it calls the control directly.</span></span> <span data-ttu-id="cf680-131">스레드 Id가 다른 경우에는 기본 스레드에서 대리자를 사용 하 여 메서드를 호출 합니다 <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=nameWithType> . 그러면이 메서드는 컨트롤에 대 한 실제 호출을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf680-131">If the thread IDs are different, it calls the <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=nameWithType> method with a delegate from the main thread, which makes the actual call to the control.</span></span>

<span data-ttu-id="cf680-132">는 `SafeCallDelegate` 컨트롤의 속성을 설정할 수 있습니다 <xref:System.Windows.Forms.TextBox> <xref:System.Windows.Forms.TextBox.Text%2A> .</span><span class="sxs-lookup"><span data-stu-id="cf680-132">The `SafeCallDelegate` enables setting the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span> <span data-ttu-id="cf680-133">`WriteTextSafe`메서드 쿼리입니다 <xref:System.Windows.Forms.Control.InvokeRequired%2A> .</span><span class="sxs-lookup"><span data-stu-id="cf680-133">The `WriteTextSafe` method queries <xref:System.Windows.Forms.Control.InvokeRequired%2A>.</span></span> <span data-ttu-id="cf680-134">가를 반환 하는 경우를 <xref:System.Windows.Forms.Control.InvokeRequired%2A> `true` `WriteTextSafe` `SafeCallDelegate` 메서드에 전달 하 여 <xref:System.Windows.Forms.Control.Invoke%2A> 컨트롤에 대 한 실제 호출을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf680-134">If <xref:System.Windows.Forms.Control.InvokeRequired%2A> returns `true`, `WriteTextSafe` passes the `SafeCallDelegate` to the <xref:System.Windows.Forms.Control.Invoke%2A> method to make the actual call to the control.</span></span> <span data-ttu-id="cf680-135"><xref:System.Windows.Forms.Control.InvokeRequired%2A> `false` 가를 반환 하면를 `WriteTextSafe` <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> 직접 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf680-135">If <xref:System.Windows.Forms.Control.InvokeRequired%2A> returns `false`, `WriteTextSafe` sets the <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> directly.</span></span> <span data-ttu-id="cf680-136">`Button1_Click`이벤트 처리기는 새 스레드를 만들고 메서드를 실행 합니다 `WriteTextSafe` .</span><span class="sxs-lookup"><span data-stu-id="cf680-136">The `Button1_Click` event handler creates the new thread and runs the `WriteTextSafe` method.</span></span>

 [!code-csharp[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/vb/Form1.vb)]  

## <a name="example-use-a-backgroundworker-event-handler"></a><span data-ttu-id="cf680-137">예: BackgroundWorker 이벤트 처리기 사용</span><span class="sxs-lookup"><span data-stu-id="cf680-137">Example: Use a BackgroundWorker event handler</span></span>

<span data-ttu-id="cf680-138">다중 스레딩을 구현 하는 쉬운 방법은 <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> 이벤트 구동 모델을 사용 하는 구성 요소를 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="cf680-138">An easy way to implement multithreading is with the <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> component, which uses an event-driven model.</span></span> <span data-ttu-id="cf680-139">백그라운드 스레드는 <xref:System.ComponentModel.BackgroundWorker.DoWork?displayProperty=nameWithType> 주 스레드와 상호 작용 하지 않는 이벤트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf680-139">The background thread runs the <xref:System.ComponentModel.BackgroundWorker.DoWork?displayProperty=nameWithType> event, which doesn't interact with the main thread.</span></span> <span data-ttu-id="cf680-140">주 스레드는 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged?displayProperty=nameWithType> <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted?displayProperty=nameWithType> 주 스레드의 컨트롤을 호출할 수 있는 및 이벤트 처리기를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf680-140">The main thread runs the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged?displayProperty=nameWithType> and <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted?displayProperty=nameWithType> event handlers, which can call the main thread's controls.</span></span>

<span data-ttu-id="cf680-141">를 사용 하 여 스레드로부터 안전한 호출을 수행 하려면 <xref:System.ComponentModel.BackgroundWorker> 백그라운드 스레드에서 작업을 수행 하는 메서드를 만들어 이벤트에 바인딩합니다 <xref:System.ComponentModel.BackgroundWorker.DoWork> .</span><span class="sxs-lookup"><span data-stu-id="cf680-141">To make a thread-safe call by using <xref:System.ComponentModel.BackgroundWorker>, create a method in the background thread to do the work, and bind it to the <xref:System.ComponentModel.BackgroundWorker.DoWork> event.</span></span> <span data-ttu-id="cf680-142">주 스레드에 다른 메서드를 만들어 백그라운드 작업의 결과를 보고 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> 하거나 또는 이벤트에 바인딩합니다 <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> .</span><span class="sxs-lookup"><span data-stu-id="cf680-142">Create another method in the main thread to report the results of the background work, and bind it to the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> or <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event.</span></span> <span data-ttu-id="cf680-143">백그라운드 스레드를 시작 하려면를 호출 <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A?displayProperty=nameWithType> 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf680-143">To start the background thread, call <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="cf680-144">이 예제에서는 이벤트 처리기를 사용 하 여 <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> <xref:System.Windows.Forms.TextBox> 컨트롤의 속성을 설정 합니다 <xref:System.Windows.Forms.TextBox.Text%2A> .</span><span class="sxs-lookup"><span data-stu-id="cf680-144">The example uses the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler to set the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span> <span data-ttu-id="cf680-145">이벤트를 사용 하는 예제는 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> 를 참조 하십시오 <xref:System.ComponentModel.BackgroundWorker> .</span><span class="sxs-lookup"><span data-stu-id="cf680-145">For an example using the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event, see <xref:System.ComponentModel.BackgroundWorker>.</span></span>

 [!code-csharp[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/vb/Form1.vb)]  

## <a name="see-also"></a><span data-ttu-id="cf680-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cf680-146">See also</span></span>

- <xref:System.ComponentModel.BackgroundWorker>
- [<span data-ttu-id="cf680-147">방법: 백그라운드에서 작업 실행</span><span class="sxs-lookup"><span data-stu-id="cf680-147">How to: Run an operation in the background</span></span>](how-to-run-an-operation-in-the-background.md)
- [<span data-ttu-id="cf680-148">방법: 백그라운드 작업을 사용 하는 폼 구현</span><span class="sxs-lookup"><span data-stu-id="cf680-148">How to: Implement a form that uses a background operation</span></span>](how-to-implement-a-form-that-uses-a-background-operation.md)
- [<span data-ttu-id="cf680-149">.NET Framework를 사용 하 여 사용자 지정 Windows Forms 컨트롤 개발</span><span class="sxs-lookup"><span data-stu-id="cf680-149">Develop custom Windows Forms controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
