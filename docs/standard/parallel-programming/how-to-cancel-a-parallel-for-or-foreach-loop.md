---
title: '방법: Parallel.For 또는 ForEach 루프 취소'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel foreach loop, how to cancel
- parallel for loops, how to cancel
ms.assetid: 9d19b591-ea95-4418-8ea7-b6266af9905b
ms.openlocfilehash: d29137127dd47844f8f08d3ac689cf2827d9efe2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288227"
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a><span data-ttu-id="b8cbf-102">방법: Parallel.For 또는 ForEach 루프 취소</span><span class="sxs-lookup"><span data-stu-id="b8cbf-102">How to: Cancel a Parallel.For or ForEach Loop</span></span>
<span data-ttu-id="b8cbf-103"><xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> 및 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> 메서드는 취소 토큰을 사용하는 방법으로 취소 기능을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="b8cbf-103">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> methods support cancellation through the use of cancellation tokens.</span></span> <span data-ttu-id="b8cbf-104">일반적으로 취소에 대한 자세한 내용은 [취소](../threading/cancellation-in-managed-threads.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b8cbf-104">For more information about cancellation in general, see [Cancellation](../threading/cancellation-in-managed-threads.md).</span></span> <span data-ttu-id="b8cbf-105">병렬 루프에서는 <xref:System.Threading.CancellationToken>을 <xref:System.Threading.Tasks.ParallelOptions> 매개 변수의 메서드에 제공하고 try-catch 블록으로 병렬 호출을 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="b8cbf-105">In a parallel loop, you supply the <xref:System.Threading.CancellationToken> to the method in the <xref:System.Threading.Tasks.ParallelOptions> parameter and then enclose the parallel call in a try-catch block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8cbf-106">예제</span><span class="sxs-lookup"><span data-stu-id="b8cbf-106">Example</span></span>  
 <span data-ttu-id="b8cbf-107">다음 예제는 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>에 대한 호출을 취소하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="b8cbf-107">The following example shows how to cancel a call to <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b8cbf-108"><xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> 호출에 동일한 접근 방식을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8cbf-108">You can apply the same approach to a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> call.</span></span>  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 <span data-ttu-id="b8cbf-109">취소 신호를 보내는 토큰이 <xref:System.Threading.Tasks.ParallelOptions> 인스턴스에 지정된 것과 동일한 토큰이면 병렬 루프에서 취소에 대한 단일 <xref:System.OperationCanceledException>를 throw합니다.</span><span class="sxs-lookup"><span data-stu-id="b8cbf-109">If the token that signals the cancellation is the same token that is specified in the <xref:System.Threading.Tasks.ParallelOptions> instance, then the parallel loop will throw a single <xref:System.OperationCanceledException> on cancellation.</span></span> <span data-ttu-id="b8cbf-110">다른 토큰이 취소를 발생시키는 경우 루프에서 <xref:System.OperationCanceledException>이 InnerException으로 설정된 <xref:System.AggregateException>을 throw합니다.</span><span class="sxs-lookup"><span data-stu-id="b8cbf-110">If some other token causes cancellation, the loop will throw an <xref:System.AggregateException> with an <xref:System.OperationCanceledException> as an InnerException.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8cbf-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b8cbf-111">See also</span></span>

- [<span data-ttu-id="b8cbf-112">데이터 병렬 처리</span><span class="sxs-lookup"><span data-stu-id="b8cbf-112">Data Parallelism</span></span>](data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="b8cbf-113">PLINQ 및 TPL의 람다 식</span><span class="sxs-lookup"><span data-stu-id="b8cbf-113">Lambda Expressions in PLINQ and TPL</span></span>](lambda-expressions-in-plinq-and-tpl.md)
