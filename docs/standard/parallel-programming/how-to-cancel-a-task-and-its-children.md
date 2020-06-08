---
title: '방법: 작업 및 해당 자식 취소'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to cancel
ms.assetid: 08574301-8331-4719-ad50-9cf7f6ff3048
ms.openlocfilehash: ca6b5f10840d935aa45cb660da86685d1c90554b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290034"
---
# <a name="how-to-cancel-a-task-and-its-children"></a><span data-ttu-id="86a6a-102">방법: 작업 및 해당 자식 취소</span><span class="sxs-lookup"><span data-stu-id="86a6a-102">How to: Cancel a Task and Its Children</span></span>
<span data-ttu-id="86a6a-103">이 예제는 다음 작업을 수행하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="86a6a-103">These examples show how to perform the following tasks:</span></span>  
  
1. <span data-ttu-id="86a6a-104">취소 가능한 작업을 만들고 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="86a6a-104">Create and start a cancelable task.</span></span>  
  
2. <span data-ttu-id="86a6a-105">사용자 대리자에 그리고 선택적으로 작업 인스턴스에 취소 토큰을 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="86a6a-105">Pass a cancellation token to your user delegate and optionally to the task instance.</span></span>  
  
3. <span data-ttu-id="86a6a-106">사용자 대리자의 취소 요청을 확인하고 이에 응답합니다.</span><span class="sxs-lookup"><span data-stu-id="86a6a-106">Notice and respond to the cancellation request in your user delegate.</span></span>  
  
4. <span data-ttu-id="86a6a-107">선택적으로 작업이 취소된 호출 스레드를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="86a6a-107">Optionally notice on the calling thread that the task was canceled.</span></span>  
  
 <span data-ttu-id="86a6a-108">호출 스레드가 작업을 강제로 종료하지 않으며, 취소가 요청되었다는 신호만 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="86a6a-108">The calling thread does not forcibly end the task; it only signals that cancellation is requested.</span></span> <span data-ttu-id="86a6a-109">작업이 이미 실행 중인 경우 사용자 대리자가 요청을 알리고 적절하게 응답해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="86a6a-109">If the task is already running, it is up to the user delegate to notice the request and respond appropriately.</span></span> <span data-ttu-id="86a6a-110">작업 실행 전에 취소를 요청하면 사용자 대리자가 실행되지 않고 작업 개체가 Canceled 상태로 전환됩니다.</span><span class="sxs-lookup"><span data-stu-id="86a6a-110">If cancellation is requested before the task runs, then the user delegate is never executed and the task object transitions into the Canceled state.</span></span>  
  
## <a name="example"></a><span data-ttu-id="86a6a-111">예제</span><span class="sxs-lookup"><span data-stu-id="86a6a-111">Example</span></span>  
 <span data-ttu-id="86a6a-112">이 예제는 취소 요청에 대한 응답으로 <xref:System.Threading.Tasks.Task> 및 해당 자식을 종료하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="86a6a-112">This example shows how to terminate a <xref:System.Threading.Tasks.Task> and its children in response to a cancellation request.</span></span> <span data-ttu-id="86a6a-113">또한 <xref:System.Threading.Tasks.TaskCanceledException>을 throw하여 사용자 대리자가 종료될 때 호출 스레드에서 필요에 따라 <xref:System.Threading.Tasks.Task.Wait%2A> 메서드나 <xref:System.Threading.Tasks.Task.WaitAll%2A> 메서드를 사용하여 작업이 종료될 때까지 대기할 수 있음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="86a6a-113">It also shows that when a user delegate terminates by throwing a <xref:System.Threading.Tasks.TaskCanceledException>, the calling thread can optionally use the <xref:System.Threading.Tasks.Task.Wait%2A> method or <xref:System.Threading.Tasks.Task.WaitAll%2A> method to wait for the tasks to finish.</span></span> <span data-ttu-id="86a6a-114">이 경우 `try/catch` 블록을 사용하여 호출 스레드에서 예외를 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="86a6a-114">In this case, you must use a `try/catch` block to handle the exceptions on the calling thread.</span></span>  
  
 [!code-csharp[TPL_Cancellation#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/cancel1.cs#04)]
 [!code-vb[TPL_Cancellation#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/cancel1.vb#04)]  
  
 <span data-ttu-id="86a6a-115"><xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 클래스는 <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> 및 <xref:System.Threading.CancellationToken?displayProperty=nameWithType> 유형을 기반으로 하는 취소 모델과 완전히 통합되었습니다.</span><span class="sxs-lookup"><span data-stu-id="86a6a-115">The <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> class is fully integrated with the cancellation model that is based on the <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> and <xref:System.Threading.CancellationToken?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="86a6a-116">자세한 내용은 [관리되는 스레드의 취소](../threading/cancellation-in-managed-threads.md) 및 [작업 취소](task-cancellation.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="86a6a-116">For more information, see [Cancellation in Managed Threads](../threading/cancellation-in-managed-threads.md) and [Task Cancellation](task-cancellation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86a6a-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="86a6a-117">See also</span></span>

- <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType>
- <xref:System.Threading.CancellationToken?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>
- [<span data-ttu-id="86a6a-118">작업 기반 비동기 프로그래밍</span><span class="sxs-lookup"><span data-stu-id="86a6a-118">Task-based Asynchronous Programming</span></span>](task-based-asynchronous-programming.md)
- [<span data-ttu-id="86a6a-119">연결된 자식 작업 및 분리된 자식 작업</span><span class="sxs-lookup"><span data-stu-id="86a6a-119">Attached and Detached Child Tasks</span></span>](attached-and-detached-child-tasks.md)
- [<span data-ttu-id="86a6a-120">PLINQ 및 TPL의 람다 식</span><span class="sxs-lookup"><span data-stu-id="86a6a-120">Lambda Expressions in PLINQ and TPL</span></span>](lambda-expressions-in-plinq-and-tpl.md)
