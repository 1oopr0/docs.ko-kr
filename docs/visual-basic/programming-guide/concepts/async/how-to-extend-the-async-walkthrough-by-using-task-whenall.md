---
title: '방법: Task.WhenAll을 사용하여 비동기 연습 확장'
ms.date: 07/20/2015
ms.assetid: c06d386d-e996-4da9-bf3d-05a3b6c0a258
ms.openlocfilehash: fb323852c83b1edf51396a0b800c2d54a833d0c0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396625"
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-visual-basic"></a><span data-ttu-id="45681-102">방법: Task.WhenAll을 사용하여 비동기 연습 확장(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45681-102">How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)</span></span>

<span data-ttu-id="45681-103">[연습: 비동기를 사용 하 여 웹에 액세스 하 고](walkthrough-accessing-the-web-by-using-async-and-await.md) 메서드를 사용 하 여 wait (Visual Basic)를 사용 하 여 비동기 솔루션의 성능을 향상 시킬 수 있습니다 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="45681-103">You can improve the performance of the async solution in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md) by using the <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="45681-104">이 메서드는 작업 컬렉션으로 표시되는 여러 개의 비동기 작업을 비동기적으로 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="45681-104">This method asynchronously awaits multiple asynchronous operations, which are represented as a collection of tasks.</span></span>

<span data-ttu-id="45681-105">연습에서 웹 사이트 다운로드 속도가 각기 다른 것을 보셨을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="45681-105">You might have noticed in the walkthrough that the websites download at different rates.</span></span> <span data-ttu-id="45681-106">때로는 웹 사이트 중 하나가 매우 느려 나머지 다운로드가 모두 지연됩니다.</span><span class="sxs-lookup"><span data-stu-id="45681-106">Sometimes one of the websites is very slow, which delays all the remaining downloads.</span></span> <span data-ttu-id="45681-107">연습에서 빌드하는 비동기 솔루션을 실행하는 경우 대기하지 않으려면 프로그램을 쉽게 종료할 수 있지만, 동시에 모든 다운로드를 시작한 후 더 빠른 다운로드는 지연되는 다운로드를 기다리지 않고 계속되도록 하는 것이 더 낫습니다.</span><span class="sxs-lookup"><span data-stu-id="45681-107">When you run the asynchronous solutions that you build in the walkthrough, you can end the program easily if you don't want to wait, but a better option would be to start all the downloads at the same time and let faster downloads continue without waiting for the one that’s delayed.</span></span>

<span data-ttu-id="45681-108">작업 컬렉션에 `Task.WhenAll` 메서드를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="45681-108">You apply the `Task.WhenAll` method to a collection of tasks.</span></span> <span data-ttu-id="45681-109">`WhenAll` 애플리케이션은 컬렉션의 모든 작업이 완료될 때까지 완료되지 않는 단일 작업을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="45681-109">The application of `WhenAll` returns a single task that isn’t complete until every task in the collection is completed.</span></span> <span data-ttu-id="45681-110">작업이 병렬로 실행되는 것처럼 보이지만 추가 스레드는 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="45681-110">The tasks appear to run in parallel, but no additional threads are created.</span></span> <span data-ttu-id="45681-111">작업이 임의 순서로 완료될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45681-111">The tasks can complete in any order.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="45681-112">다음 절차에서는 [연습: async 및 wait를 사용 하 여 웹에 액세스 (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md)에서 개발 된 비동기 응용 프로그램에 대 한 확장을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="45681-112">The following procedures describe extensions to the async applications that are developed in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="45681-113">연습을 완료하거나 [개발자 코드 샘플](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)에서 코드를 다운로드하여 애플리케이션을 개발할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45681-113">You can develop the applications by either completing the walkthrough or downloading the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>
>
> <span data-ttu-id="45681-114">예제를 실행하려면 Visual Studio 2012 이상이 컴퓨터에 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45681-114">To run the example, you must have Visual Studio 2012 or later installed on your computer.</span></span>

### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a><span data-ttu-id="45681-115">GetURLContentsAsync 솔루션에 Task.WhenAll을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="45681-115">To add Task.WhenAll to your GetURLContentsAsync solution</span></span>

1. <span data-ttu-id="45681-116">`ProcessURLAsync` [연습: Async 및 Wait를 사용 하 여 웹에 액세스 (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md)에서 개발 된 첫 번째 응용 프로그램에 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="45681-116">Add the `ProcessURLAsync` method to the first application that's developed in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>

    - <span data-ttu-id="45681-117">[개발자 코드 샘플](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)에서 코드를 다운로드 한 경우 asyncwalkthrough 프로젝트를 열고 `ProcessURLAsync` mainwindow.xaml 파일에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="45681-117">If you downloaded the code from  [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough project, and then add `ProcessURLAsync` to the MainWindow.xaml.vb file.</span></span>

    - <span data-ttu-id="45681-118">연습을 완료하여 코드를 개발한 경우 `GetURLContentsAsync` 메서드를 포함하는 애플리케이션에 `ProcessURLAsync`를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="45681-118">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that includes the `GetURLContentsAsync` method.</span></span> <span data-ttu-id="45681-119">이 응용 프로그램에 대 한 Mainwindow.xaml 파일은 "연습의 전체 코드 예제" 섹션에서 첫 번째 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="45681-119">The MainWindow.xaml.vb file for this application is the first example in the "Complete Code Examples from the Walkthrough" section.</span></span>

     <span data-ttu-id="45681-120">`ProcessURLAsync` 메서드는 원래 연습의 `SumPageSizesAsync`에 `For Each` 루프 본문의 작업을 통합합니다.</span><span class="sxs-lookup"><span data-stu-id="45681-120">The `ProcessURLAsync` method consolidates the actions in the body of the `For Each` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="45681-121">이 메서드는 비동기적으로 지정된 웹 사이트의 내용을 바이트 배열로 다운로드한 다음 바이트 배열의 길이를 표시하고 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="45681-121">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>

    ```vb
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)

        Dim byteArray = Await GetURLContentsAsync(url)
        DisplayResults(url, byteArray)
        Return byteArray.Length
    End Function
    ```

2. <span data-ttu-id="45681-122">다음 코드와 같이 `SumPageSizesAsync`의 `For Each` 루프를 주석으로 처리하거나 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="45681-122">Comment out or delete the `For Each` loop in `SumPageSizesAsync`, as the following code shows.</span></span>

    ```vb
    'Dim total = 0
    'For Each url In urlList

    '    Dim urlContents As Byte() = Await GetURLContentsAsync(url)

    '    ' The previous line abbreviates the following two assignment statements.

    '    ' GetURLContentsAsync returns a task. At completion, the task
    '    ' produces a byte array.
    '    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)
    '    'Dim urlContents As Byte() = Await getContentsTask

    '    DisplayResults(url, urlContents)

    '    ' Update the total.
    '    total += urlContents.Length
    'Next
    ```

3. <span data-ttu-id="45681-123">작업 컬렉션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="45681-123">Create a collection of tasks.</span></span> <span data-ttu-id="45681-124">다음 코드는 <xref:System.Linq.Enumerable.ToArray%2A> 메서드가 실행할 때 각 웹 사이트의 내용을 다운로드하는 작업 컬렉션을 만드는 [쿼리](../linq/index.md)를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="45681-124">The following code defines a [query](../linq/index.md) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="45681-125">작업은 쿼리가 평가될 때 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="45681-125">The tasks are started when the query is evaluated.</span></span>

     <span data-ttu-id="45681-126">`SumPageSizesAsync` 메서드의 `urlList` 선언 뒤에 다음 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="45681-126">Add the following code to method `SumPageSizesAsync` after the declaration of `urlList`.</span></span>

    ```vb
    ' Create a query.
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
        From url In urlList Select ProcessURLAsync(url)

    ' Use ToArray to execute the query and start the download tasks.
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()
    ```

4. <span data-ttu-id="45681-127">작업 컬렉션 `downloadTasks`에서 `Task.WhenAll`을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="45681-127">Apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="45681-128">`Task.WhenAll`은 작업 컬렉션의 모든 작업이 완료될 때 완료되는 단일 작업을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="45681-128">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>

     <span data-ttu-id="45681-129">다음 예제에서 `Await` 식은 `WhenAll`이 반환하는 단일 작업이 완료될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="45681-129">In the following example, the `Await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="45681-130">식은 각 정수가 다운로드된 웹 사이트의 길이인 정수 배열로 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="45681-130">The expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="45681-131">이전 단계에서 추가한 코드 뒤의 `SumPageSizesAsync`에 다음 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="45681-131">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>

    ```vb
    ' Await the completion of all the running tasks.
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)

    '' The previous line is equivalent to the following two statements.
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)
    'Dim lengths As Integer() = Await whenAllTask
    ```

5. <span data-ttu-id="45681-132">마지막으로, <xref:System.Linq.Enumerable.Sum%2A> 메서드를 사용하여 모든 웹 사이트의 길이 합계를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="45681-132">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to calculate the sum of the lengths of all the websites.</span></span> <span data-ttu-id="45681-133">`SumPageSizesAsync`에 다음 줄을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="45681-133">Add the following line to `SumPageSizesAsync`.</span></span>

    ```vb
    Dim total = lengths.Sum()
    ```

### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a><span data-ttu-id="45681-134">HttpClient.GetByteArrayAsync 솔루션에 Task.WhenAll을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="45681-134">To add Task.WhenAll to the HttpClient.GetByteArrayAsync solution</span></span>

1. <span data-ttu-id="45681-135">`ProcessURLAsync` [연습: Async 및 Wait를 사용 하 여 웹에 액세스 (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md)에서 개발 된 두 번째 응용 프로그램에 다음 버전의를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="45681-135">Add the following version of `ProcessURLAsync` to the second application that's developed in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>

    - <span data-ttu-id="45681-136">[개발자 코드 샘플](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)에서 코드를 다운로드 한 경우 AsyncWalkthrough_HttpClient 프로젝트를 열고를 `ProcessURLAsync` mainwindow.xaml 파일에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="45681-136">If you downloaded the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough_HttpClient project, and then add `ProcessURLAsync` to the MainWindow.xaml.vb file.</span></span>

    - <span data-ttu-id="45681-137">연습을 완료하여 코드를 개발한 경우 `HttpClient.GetByteArrayAsync` 메서드를 사용하는 애플리케이션에 `ProcessURLAsync`를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="45681-137">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that uses the `HttpClient.GetByteArrayAsync` method.</span></span> <span data-ttu-id="45681-138">이 응용 프로그램에 대 한 Mainwindow.xaml 파일은 "연습의 전체 코드 예제" 섹션에서 두 번째 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="45681-138">The MainWindow.xaml.vb file for this application is the second example in the "Complete Code Examples from the Walkthrough" section.</span></span>

     <span data-ttu-id="45681-139">`ProcessURLAsync` 메서드는 원래 연습의 `SumPageSizesAsync`에 `For Each` 루프 본문의 작업을 통합합니다.</span><span class="sxs-lookup"><span data-stu-id="45681-139">The `ProcessURLAsync` method consolidates the actions in the body of the `For Each` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="45681-140">이 메서드는 비동기적으로 지정된 웹 사이트의 내용을 바이트 배열로 다운로드한 다음 바이트 배열의 길이를 표시하고 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="45681-140">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>

     <span data-ttu-id="45681-141">이전 절차의 `ProcessURLAsync` 메서드와 차이점은 <xref:System.Net.Http.HttpClient> 인스턴스 `client`를 사용한다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="45681-141">The only difference from the `ProcessURLAsync` method in the previous procedure is the use of the <xref:System.Net.Http.HttpClient> instance, `client`.</span></span>

    ```vb
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)

        Dim byteArray = Await client.GetByteArrayAsync(url)
        DisplayResults(url, byteArray)
        Return byteArray.Length
    End Function
    ```

2. <span data-ttu-id="45681-142">다음 코드와 같이 `SumPageSizesAsync`의 `For Each` 루프를 주석으로 처리하거나 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="45681-142">Comment out or delete the `For Each` loop in `SumPageSizesAsync`, as the following code shows.</span></span>

    ```vb
    'Dim total = 0
    'For Each url In urlList
    '    ' GetByteArrayAsync returns a task. At completion, the task
    '    ' produces a byte array.
    '    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)

    '    ' The following two lines can replace the previous assignment statement.
    '    'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)
    '    'Dim urlContents As Byte() = Await getContentsTask

    '    DisplayResults(url, urlContents)

    '    ' Update the total.
    '    total += urlContents.Length
    'Next
    ```

3. <span data-ttu-id="45681-143"><xref:System.Linq.Enumerable.ToArray%2A> 메서드에서 실행할 때 각 웹 사이트의 내용을 다운로드하는 작업 컬렉션을 만드는 [쿼리](../linq/index.md)를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="45681-143">Define a [query](../linq/index.md) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="45681-144">작업은 쿼리가 평가될 때 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="45681-144">The tasks are started when the query is evaluated.</span></span>

     <span data-ttu-id="45681-145">`SumPageSizesAsync` 메서드의 `client` 및 `urlList` 선언 뒤에 다음 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="45681-145">Add the following code to method `SumPageSizesAsync` after the declaration of `client` and `urlList`.</span></span>

    ```vb
    ' Create a query.
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
        From url In urlList Select ProcessURLAsync(url, client)

    ' Use ToArray to execute the query and start the download tasks.
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()
    ```

4. <span data-ttu-id="45681-146">작업 컬렉션 `downloadTasks`에서 `Task.WhenAll`을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="45681-146">Next, apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="45681-147">`Task.WhenAll`은 작업 컬렉션의 모든 작업이 완료될 때 완료되는 단일 작업을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="45681-147">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>

     <span data-ttu-id="45681-148">다음 예제에서 `Await` 식은 `WhenAll`이 반환하는 단일 작업이 완료될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="45681-148">In the following example, the `Await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="45681-149">완료되면 `Await` 식은 각 정수가 다운로드된 웹 사이트의 길이인 정수 배열로 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="45681-149">When complete, the `Await` expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="45681-150">이전 단계에서 추가한 코드 뒤의 `SumPageSizesAsync`에 다음 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="45681-150">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>

    ```vb
    ' Await the completion of all the running tasks.
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)

    '' The previous line is equivalent to the following two statements.
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)
    'Dim lengths As Integer() = Await whenAllTask
    ```

5. <span data-ttu-id="45681-151">마지막으로, <xref:System.Linq.Enumerable.Sum%2A> 메서드를 사용하여 모든 웹 사이트의 길이 합계를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="45681-151">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to get the sum of the lengths of all the websites.</span></span> <span data-ttu-id="45681-152">`SumPageSizesAsync`에 다음 줄을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="45681-152">Add the following line to `SumPageSizesAsync`.</span></span>

    ```vb
    Dim total = lengths.Sum()
    ```

### <a name="to-test-the-taskwhenall-solutions"></a><span data-ttu-id="45681-153">Task.WhenAll 솔루션을 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="45681-153">To test the Task.WhenAll solutions</span></span>

<span data-ttu-id="45681-154">두 솔루션 중 하나에 대해 F5 키를 선택하여 프로그램을 실행한 다음 **시작** 단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="45681-154">For either solution, choose the F5 key to run the program, and then choose the **Start** button.</span></span> <span data-ttu-id="45681-155">출력은 [연습: async 및 wait를 사용 하 여 웹에 액세스 (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md)의 비동기 솔루션의 출력과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="45681-155">The output should resemble the output from the async solutions in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="45681-156">그러나 웹 사이트가 매번 다른 순서로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="45681-156">However, notice that the websites appear in a different order each time.</span></span>

## <a name="example"></a><span data-ttu-id="45681-157">예제</span><span class="sxs-lookup"><span data-stu-id="45681-157">Example</span></span>

<span data-ttu-id="45681-158">다음 코드에서는 `GetURLContentsAsync` 메서드를 사용하여 웹에서 콘텐츠를 다운로드하는 프로젝트에 대한 확장을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="45681-158">The following code shows the extensions to the project that uses the `GetURLContentsAsync` method to download content from the web.</span></span>

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http
Imports System.Net
Imports System.IO

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click

        resultsTextBox.Clear()

        ' One-step async call.
        Await SumPageSizesAsync()

        '' Two-step async call.
        'Dim sumTask As Task = SumPageSizesAsync()
        'Await sumTask

        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."
    End Sub

    Private Async Function SumPageSizesAsync() As Task

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        ' Create a query.
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
            From url In urlList Select ProcessURLAsync(url)

        ' Use ToArray to execute the query and start the download tasks.
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()

        ' You can do other work here before awaiting.

        ' Await the completion of all the running tasks.
        Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)

        '' The previous line is equivalent to the following two statements.
        'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)
        'Dim lengths As Integer() = Await whenAllTask

        Dim total = lengths.Sum()

        'Dim total = 0
        'For Each url In urlList

        '    Dim urlContents As Byte() = Await GetURLContentsAsync(url)

        '    ' The previous line abbreviates the following two assignment statements.

        '    ' GetURLContentsAsync returns a task. At completion, the task
        '    ' produces a byte array.
        '    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)
        '    'Dim urlContents As Byte() = Await getContentsTask

        '    DisplayResults(url, urlContents)

        '    ' Update the total.
        '    total += urlContents.Length
        'NextNext

        ' Display the total count for all of the web addresses.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function

    ' The actions from the foreach loop are moved to this async method.
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)

        Dim byteArray = Await GetURLContentsAsync(url)
        DisplayResults(url, byteArray)
        Return byteArray.Length
    End Function

    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())

        ' The downloaded resource ends up in the variable named content.
        Dim content = New MemoryStream()

        ' Initialize an HttpWebRequest for the current URL.
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)

        ' Send the request to the Internet resource and wait for
        ' the response.
        Using response As WebResponse = Await webReq.GetResponseAsync()
            ' Get the data stream that is associated with the specified URL.
            Using responseStream As Stream = response.GetResponseStream()
                ' Read the bytes in responseStream and copy them to content.
                ' CopyToAsync returns a Task, not a Task<T>.
                Await responseStream.CopyToAsync(content)
            End Using
        End Using

        ' Return the result as a byte array.
        Return content.ToArray()
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub

End Class
```

## <a name="example"></a><span data-ttu-id="45681-159">예제</span><span class="sxs-lookup"><span data-stu-id="45681-159">Example</span></span>

<span data-ttu-id="45681-160">다음 코드에서는 `HttpClient.GetByteArrayAsync` 메서드를 사용하여 웹에서 콘텐츠를 다운로드하는 프로젝트에 대한 확장을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="45681-160">The following code shows the extensions to the project that uses method `HttpClient.GetByteArrayAsync` to download content from the web.</span></span>

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http
Imports System.Net
Imports System.IO

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click

        resultsTextBox.Clear()

        '' One-step async call.
        Await SumPageSizesAsync()

        '' Two-step async call.
        'Dim sumTask As Task = SumPageSizesAsync()
        'Await sumTask

        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."
    End Sub

    Private Async Function SumPageSizesAsync() As Task

        ' Declare an HttpClient object and increase the buffer size. The
        ' default buffer size is 65,536.
        Dim client As HttpClient =
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        ' Create a query.
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
            From url In urlList Select ProcessURLAsync(url, client)

        ' Use ToArray to execute the query and start the download tasks.
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()

        ' You can do other work here before awaiting.

        ' Await the completion of all the running tasks.
        Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)

        '' The previous line is equivalent to the following two statements.
        'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)
        'Dim lengths As Integer() = Await whenAllTask

        Dim total = lengths.Sum()

        ''<snippet7>
        'Dim total = 0
        'For Each url In urlList
        '    ' GetByteArrayAsync returns a task. At completion, the task
        '    ' produces a byte array.
        '    '<snippet31>
        '    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)
        '    '</snippet31>

        '    ' The following two lines can replace the previous assignment statement.
        '    'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)
        '    'Dim urlContents As Byte() = Await getContentsTask

        '    DisplayResults(url, urlContents)

        '    ' Update the total.
        '    total += urlContents.Length
        'NextNext

        ' Display the total count for all of the web addresses.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://www.msdn.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function

    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)

        Dim byteArray = Await client.GetByteArrayAsync(url)
        DisplayResults(url, byteArray)
        Return byteArray.Length
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub

End Class
```

## <a name="see-also"></a><span data-ttu-id="45681-161">참고 항목</span><span class="sxs-lookup"><span data-stu-id="45681-161">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>
- [<span data-ttu-id="45681-162">연습: Async 및 Await를 사용하여 웹에 액세스(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45681-162">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](walkthrough-accessing-the-web-by-using-async-and-await.md)
