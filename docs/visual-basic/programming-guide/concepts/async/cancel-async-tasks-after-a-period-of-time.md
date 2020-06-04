---
title: 일정 기간 이후 비동기 작업 취소
ms.date: 07/20/2015
ms.assetid: a48045a3-6a99-42af-b824-af340f0b9a5d
ms.openlocfilehash: 048d4c19d459905ea579ede96c69230e718d55aa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396690"
---
# <a name="cancel-async-tasks-after-a-period-of-time-visual-basic"></a><span data-ttu-id="12dda-102">일정 기간 이후 비동기 작업 취소(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="12dda-102">Cancel Async Tasks after a Period of Time (Visual Basic)</span></span>

<span data-ttu-id="12dda-103">작업이 완료될 때까지 대기하지 않으려는 경우 일정 기간 후에 <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> 메서드를 사용하여 비동기 작업을 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12dda-103">You can cancel an asynchronous operation after a period of time by using the  <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> method if you don't want to wait for the operation to finish.</span></span> <span data-ttu-id="12dda-104">이 메서드는 `CancelAfter` 식으로 지정된 일정 기간 내에 완료되지 않은 연결된 작업의 취소를 예약합니다.</span><span class="sxs-lookup"><span data-stu-id="12dda-104">This method schedules the cancellation of any associated tasks that aren’t complete within the period of time that’s designated by the `CancelAfter` expression.</span></span>

<span data-ttu-id="12dda-105">이 예제는 [비동기 작업 또는 작업 목록 취소(Visual Basic)](cancel-an-async-task-or-a-list-of-tasks.md)에서 개발된 코드에 추가되어 웹 사이트 목록을 다운로드하고 각 웹 사이트의 콘텐츠 길이를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="12dda-105">This example adds to the code that’s developed in [Cancel an Async Task or a List of Tasks (Visual Basic)](cancel-an-async-task-or-a-list-of-tasks.md) to download a list of websites and to display the length of the contents of each one.</span></span>

> [!NOTE]
> <span data-ttu-id="12dda-106">예제를 실행하려면 Visual Studio 2012 이상 및 .NET Framework 4.5 이상이 컴퓨터에 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="12dda-106">To run the examples, you must have Visual Studio 2012 or later and the .NET Framework 4.5 or later installed on your computer.</span></span>

## <a name="downloading-the-example"></a><span data-ttu-id="12dda-107">예제 다운로드</span><span class="sxs-lookup"><span data-stu-id="12dda-107">Downloading the Example</span></span>

<span data-ttu-id="12dda-108">[Async 샘플: 애플리케이션 세부 조정](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)에서 전체 WPF(Windows Presentation Foundation) 프로젝트를 다운로드한 후 다음 단계를 따를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12dda-108">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="12dda-109">다운로드한 파일의 압축을 푼 다음 Visual Studio를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="12dda-109">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="12dda-110">메뉴 모음에서 **파일**, **열기**, **프로젝트/솔루션**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="12dda-110">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>

3. <span data-ttu-id="12dda-111">**프로젝트 열기** 대화 상자에서 압축을 해제한 샘플 코드가 포함된 폴더를 열고 AsyncFineTuningVB에 대한 솔루션(.sln) 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="12dda-111">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>

4. <span data-ttu-id="12dda-112">**솔루션 탐색기**에서 **CancelAfterTime** 프로젝트에 대한 바로 가기 메뉴를 열고 **시작 프로젝트로 설정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="12dda-112">In **Solution Explorer**, open the shortcut menu for the **CancelAfterTime** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="12dda-113">F5 키를 선택하여 프로젝트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="12dda-113">Choose the F5 key to run the project.</span></span>

     <span data-ttu-id="12dda-114">디버그하지 않고 프로젝트를 실행하려면 Ctrl+F5를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="12dda-114">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>

6. <span data-ttu-id="12dda-115">프로그램을 여러 번 실행하여 모든 웹 사이트 또는 일부 웹 사이트에 대한 출력이 표시되는지, 또는 웹 사이트에 대한 출력이 표시되지 않는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="12dda-115">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span>

 <span data-ttu-id="12dda-116">프로젝트를 다운로드하지 않으려는 경우 이 항목의 끝에 있는 MainWindow.xaml.vb 파일을 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12dda-116">If you don't want to download the project, you can review the MainWindow.xaml.vb file at the end of this topic.</span></span>

## <a name="building-the-example"></a><span data-ttu-id="12dda-117">예제 빌드</span><span class="sxs-lookup"><span data-stu-id="12dda-117">Building the Example</span></span>

<span data-ttu-id="12dda-118">이 항목의 예제는 [비동기 작업 또는 작업 목록 취소(Visual Basic)](cancel-an-async-task-or-a-list-of-tasks.md)에서 개발된 프로젝트에 추가되어 작업 목록을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="12dda-118">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks (Visual Basic)](cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="12dda-119">**취소** 단추는 명시적으로 사용되지 않지만 예제에서는 같은 UI를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="12dda-119">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>

<span data-ttu-id="12dda-120">직접 예제를 빌드하려면 "예제 다운로드" 섹션의 지침을 단계별로 따르되, **CancelAListOfTasks**를 **시작 프로젝트**로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="12dda-120">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="12dda-121">이 항목의 변경 내용을 해당 프로젝트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="12dda-121">Add the changes in this topic to that project.</span></span>

<span data-ttu-id="12dda-122">작업이 취소됨으로 표시되기 전에 소요되는 최대 시간을 지정하려면 다음 예제와 같이 `CancelAfter` 호출을 `startButton_Click`에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="12dda-122">To specify a maximum time before the tasks are marked as canceled, add a call to `CancelAfter` to `startButton_Click`, as the following example shows.</span></span> <span data-ttu-id="12dda-123">추가된 내용에는 별표가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="12dda-123">The addition is marked with asterisks.</span></span>

```vb
Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)

    ' Instantiate the CancellationTokenSource.
    cts = New CancellationTokenSource()

    resultsTextBox.Clear()

    Try
        ' ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You
        ' can adjust the time.)
        cts.CancelAfter(2500)

        Await AccessTheWebAsync(cts.Token)
        resultsTextBox.Text &= vbCrLf & "Downloads complete."

    Catch ex As OperationCanceledException
        resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf

    Catch ex As Exception
        resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf
    End Try

    ' Set the CancellationTokenSource to Nothing when the download is complete.
    cts = Nothing
End Sub
```

<span data-ttu-id="12dda-124">프로그램을 여러 번 실행하여 모든 웹 사이트 또는 일부 웹 사이트에 대한 출력이 표시되는지, 또는 웹 사이트에 대한 출력이 표시되지 않는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="12dda-124">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span> <span data-ttu-id="12dda-125">다음 출력은 샘플입니다.</span><span class="sxs-lookup"><span data-stu-id="12dda-125">The following output is a sample:</span></span>

```console
Length of the downloaded string: 35990.

Length of the downloaded string: 407399.

Length of the downloaded string: 226091.

Downloads canceled.
```

## <a name="complete-example"></a><span data-ttu-id="12dda-126">전체 예제</span><span class="sxs-lookup"><span data-stu-id="12dda-126">Complete Example</span></span>

<span data-ttu-id="12dda-127">다음 코드는 예제에 대한 MainWindow.xaml.vb 파일의 전체 텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="12dda-127">The following code is the complete text of the MainWindow.xaml.vb file for the example.</span></span> <span data-ttu-id="12dda-128">별표는 이 예제에 대해 추가된 요소를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="12dda-128">Asterisks mark the elements that were added for this example.</span></span>

<span data-ttu-id="12dda-129"><xref:System.Net.Http>에 대한 참조를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="12dda-129">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="12dda-130">[Async 샘플: 애플리케이션 미세 조정](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)에서 프로젝트를 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12dda-130">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

```vb
' Add an Imports directive and a reference for System.Net.Http.
Imports System.Net.Http

' Add the following Imports directive for System.Threading.
Imports System.Threading

Class MainWindow

    ' Declare a System.Threading.CancellationTokenSource.
    Dim cts As CancellationTokenSource

    Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)

        ' Instantiate the CancellationTokenSource.
        cts = New CancellationTokenSource()

        resultsTextBox.Clear()

        Try
            ' ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You
            ' can adjust the time.)
            cts.CancelAfter(2500)

            Await AccessTheWebAsync(cts.Token)
            resultsTextBox.Text &= vbCrLf & "Downloads complete."

        Catch ex As OperationCanceledException
            resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf

        Catch ex As Exception
            resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf
        End Try

        ' Set the CancellationTokenSource to Nothing when the download is complete.
        cts = Nothing
    End Sub

    ' You can still include a Cancel button if you want to.
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)

        If cts IsNot Nothing Then
            cts.Cancel()
        End If
    End Sub

    ' Provide a parameter for the CancellationToken.
    ' Change the return type to Task because the method has no return statement.
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task

        Dim client As HttpClient = New HttpClient()

        ' Call SetUpURLList to make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        ' Process each element in the list of web addresses.
        For Each url In urlList
            ' GetAsync returns a Task(Of HttpResponseMessage).
            ' Argument ct carries the message if the Cancel button is chosen.
            ' Note that the Cancel button can cancel all remaining downloads.
            Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

            ' Retrieve the website contents from the HttpResponseMessage.
            Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

            resultsTextBox.Text &=
                vbCrLf & $"Length of the downloaded string: {urlContents.Length}." & vbCrLf
        Next
    End Function

    ' Add a method that creates a list of web addresses.
    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function

End Class

' Sample output:

' Length of the downloaded string: 35990.

' Length of the downloaded string: 407399.

' Length of the downloaded string: 226091.

' Downloads canceled.
```

## <a name="see-also"></a><span data-ttu-id="12dda-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="12dda-131">See also</span></span>

- [<span data-ttu-id="12dda-132">Async 및 Await를 사용한 비동기 프로그래밍(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="12dda-132">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="12dda-133">연습: Async 및 Await를 사용하여 웹에 액세스(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="12dda-133">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="12dda-134">비동기 작업 또는 작업 목록 취소(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="12dda-134">Cancel an Async Task or a List of Tasks (Visual Basic)</span></span>](cancel-an-async-task-or-a-list-of-tasks.md)
- [<span data-ttu-id="12dda-135">Async 애플리케이션 미세 조정(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="12dda-135">Fine-Tuning Your Async Application (Visual Basic)</span></span>](fine-tuning-your-async-application.md)
- [<span data-ttu-id="12dda-136">Async 샘플: 애플리케이션 미세 조정</span><span class="sxs-lookup"><span data-stu-id="12dda-136">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
