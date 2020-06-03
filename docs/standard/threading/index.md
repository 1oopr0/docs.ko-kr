---
title: 관리되는 스레딩
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 7b46a7d9-c6f1-46d1-a947-ae97471bba87
ms.openlocfilehash: e4c19b664e8fc040fdc4a284b30f6104d676088d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279156"
---
# <a name="managed-threading"></a><span data-ttu-id="a9d2f-102">관리되는 스레딩</span><span class="sxs-lookup"><span data-stu-id="a9d2f-102">Managed Threading</span></span>
<span data-ttu-id="a9d2f-103">개발 대상 컴퓨터에 프로세서가 1개 있든, 여러 개 있든, 애플리케이션이 현재 다른 작업을 수행하면서도 사용자에게 가장 먼저 반응하는 방식으로 상호 작용을 제공하는 것을 원할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a9d2f-103">Whether you are developing for computers with one processor or several, you want your application to provide the most responsive interaction with the user, even if the application is currently doing other work.</span></span> <span data-ttu-id="a9d2f-104">다중 스레드 방식의 실행을 사용하는 것이 사용자에 대한 애플리케이션 응답성을 유지하면서 사용자 이벤트 중간에 프로세서를 최대한 활용할 수 있는 가장 강력한 방법 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="a9d2f-104">Using multiple threads of execution is one of the most powerful ways to keep your application responsive to the user and at the same time make use of the processor in between or even during user events.</span></span> <span data-ttu-id="a9d2f-105">이 섹션에서는 스레딩의 기본 개념을 소개하지만 관리되는 스레딩 개념 및 관리되는 스레딩 사용을 집중적으로 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="a9d2f-105">While this section introduces the basic concepts of threading, it focuses on managed threading concepts and using managed threading.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a9d2f-106">.NET Framework 4부터는 <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> 및 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 클래스, [PLINQ(병렬 LINQ)](../parallel-programming/introduction-to-plinq.md), <xref:System.Collections.Concurrent?displayProperty=nameWithType> 네임스페이스의 새로운 동시 컬렉션 클래스, 그리고 스레드가 아닌 작업 개념을 기반으로 하는 새로운 프로그래밍 모델로 인해 다중 스레드 프로그래밍이 매우 간소화되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a9d2f-106">Starting with the .NET Framework 4, multithreaded programming is greatly simplified with the <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> classes, [Parallel LINQ (PLINQ)](../parallel-programming/introduction-to-plinq.md), new concurrent collection classes in the <xref:System.Collections.Concurrent?displayProperty=nameWithType> namespace, and a new programming model that is based on the concept of tasks rather than threads.</span></span> <span data-ttu-id="a9d2f-107">자세한 내용은 [병렬 프로그래밍](../parallel-programming/index.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a9d2f-107">For more information, see [Parallel Programming](../parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a9d2f-108">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="a9d2f-108">In This Section</span></span>  
 [<span data-ttu-id="a9d2f-109">관리되는 스레딩 기본 사항</span><span class="sxs-lookup"><span data-stu-id="a9d2f-109">Managed Threading Basics</span></span>](managed-threading-basics.md)  
 <span data-ttu-id="a9d2f-110">관리되는 스레딩의 개요를 제공하고 다중 스레드를 사용해야 하는 경우를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a9d2f-110">Provides an overview of managed threading and discusses when to use multiple threads.</span></span>  
  
 [<span data-ttu-id="a9d2f-111">스레드 및 스레딩 사용</span><span class="sxs-lookup"><span data-stu-id="a9d2f-111">Using Threads and Threading</span></span>](using-threads-and-threading.md)  
 <span data-ttu-id="a9d2f-112">스레드를 만들고, 시작하고, 일시 중지하고, 재개하고, 중단하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a9d2f-112">Explains how to create, start, pause, resume, and abort threads.</span></span>  
  
 [<span data-ttu-id="a9d2f-113">관리되는 스레딩을 구현하는 최선의 방법</span><span class="sxs-lookup"><span data-stu-id="a9d2f-113">Managed Threading Best Practices</span></span>](managed-threading-best-practices.md)  
 <span data-ttu-id="a9d2f-114">동기화 수준, 교착 상태 및 경합 상태를 방지하는 방법, 기타 스레딩 문제에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a9d2f-114">Discusses levels of synchronization, how to avoid deadlocks and race conditions, and other threading issues.</span></span>  
  
 [<span data-ttu-id="a9d2f-115">스레딩 개체 및 기능</span><span class="sxs-lookup"><span data-stu-id="a9d2f-115">Threading Objects and Features</span></span>](threading-objects-and-features.md)  
 <span data-ttu-id="a9d2f-116">스레드 작업과 다른 스레드에서 액세스되는 개체 데이터를 동기화하는 데 사용할 수 있는 관리되는 클래스에 대해 설명하고 스레드 풀 스레드에 대해 대략적으로 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a9d2f-116">Describes the managed classes you can use to synchronize the activities of threads and the data of objects accessed on different threads, and provides an overview of thread pool threads.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a9d2f-117">참고</span><span class="sxs-lookup"><span data-stu-id="a9d2f-117">Reference</span></span>  
 <xref:System.Threading>  
 <span data-ttu-id="a9d2f-118">관리되는 스레드를 사용하고 동기화하기 위한 클래스를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="a9d2f-118">Contains classes for using and synchronizing managed threads.</span></span>  
  
 <xref:System.Collections.Concurrent>  
 <span data-ttu-id="a9d2f-119">여러 스레드에서 사용해도 안전한 컬렉션 클래스를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="a9d2f-119">Contains collection classes that are safe for use with multiple threads.</span></span>  
  
 <xref:System.Threading.Tasks>  
 <span data-ttu-id="a9d2f-120">동시 처리 작업을 만들고 예약하기 위한 클래스를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="a9d2f-120">Contains classes for creating and scheduling concurrent processing tasks.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a9d2f-121">관련 단원</span><span class="sxs-lookup"><span data-stu-id="a9d2f-121">Related Sections</span></span>  
 [<span data-ttu-id="a9d2f-122">애플리케이션 도메인</span><span class="sxs-lookup"><span data-stu-id="a9d2f-122">Application Domains</span></span>](../../framework/app-domains/application-domains.md)  
 <span data-ttu-id="a9d2f-123">애플리케이션 도메인과 공용 언어 인프라에서 이를 사용하는 방법에 대한 개요를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a9d2f-123">Provides an overview of application domains and their use by the Common Language Infrastructure.</span></span>  
  
 [<span data-ttu-id="a9d2f-124">비동기 파일 I/O</span><span class="sxs-lookup"><span data-stu-id="a9d2f-124">Asynchronous File I/O</span></span>](../io/asynchronous-file-i-o.md)  
 <span data-ttu-id="a9d2f-125">비동기 I/O의 기본 연산 및 성능상의 이점에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a9d2f-125">Describes the performance advantages and basic operation of asynchronous I/O.</span></span>  
  
 [<span data-ttu-id="a9d2f-126">TAP(작업 기반 비동기 패턴)</span><span class="sxs-lookup"><span data-stu-id="a9d2f-126">Task-based Asynchronous Pattern (TAP)</span></span>](../asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 <span data-ttu-id="a9d2f-127">.NET에서 비동기 프로그래밍의 권장 패턴에 대한 개요를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a9d2f-127">Provides an overview of the recommended pattern for asynchronous programming in .NET.</span></span>  
  
 [<span data-ttu-id="a9d2f-128">동기 메서드를 비동기 방식으로 호출</span><span class="sxs-lookup"><span data-stu-id="a9d2f-128">Calling Synchronous Methods Asynchronously</span></span>](../asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="a9d2f-129">대리자의 기본 제공 기능을 사용하여 스레드 풀 스레드에 대해 메서드를 호출하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a9d2f-129">Explains how to call methods on thread pool threads using built-in features of delegates.</span></span>  
  
 [<span data-ttu-id="a9d2f-130">병렬 프로그래밍</span><span class="sxs-lookup"><span data-stu-id="a9d2f-130">Parallel Programming</span></span>](../parallel-programming/index.md)  
 <span data-ttu-id="a9d2f-131">애플리케이션에서 다중 스레드를 간편하게 사용할 수 있도록 하는 병렬 프로그래밍 라이브러리에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a9d2f-131">Describes the parallel programming libraries, which simplify the use of multiple threads in applications.</span></span>  
  
 [<span data-ttu-id="a9d2f-132">PLINQ(병렬 LINQ)</span><span class="sxs-lookup"><span data-stu-id="a9d2f-132">Parallel LINQ (PLINQ)</span></span>](../parallel-programming/introduction-to-plinq.md)  
 <span data-ttu-id="a9d2f-133">다중 프로세서를 활용하기 위해 쿼리를 병렬로 실행하기 위한 시스템을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a9d2f-133">Describes a system for running queries in parallel, to take advantage of multiple processors.</span></span>
