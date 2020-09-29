---
title: 클라우드를 위한 복원력 있는 서비스 빌드 클라우드의 일시적 오류 포용
description: Azure Cloud 및 Windows 컨테이너를 사용하여 기존 .NET 애플리케이션 현대화 | 클라우드를 위한 복원력 있는 서비스 빌드 클라우드의 일시적 오류 포용
ms.date: 04/30/2018
ms.openlocfilehash: 8e9f1eda71e4b98a56cbfc1c7a4ff34e67bee3f4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172159"
---
# <a name="build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud"></a><span data-ttu-id="f5933-105">클라우드를 위한 탄력적인 서비스 빌드: 클라우드의 일시적 오류 포용</span><span class="sxs-lookup"><span data-stu-id="f5933-105">Build resilient services ready for the cloud: Embrace transient failures in the cloud</span></span>

<span data-ttu-id="f5933-106">복원력은 오류를 복구하고 계속 작업을 진행하는 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="f5933-106">Resiliency is the ability to recover from failures and continue to function.</span></span> <span data-ttu-id="f5933-107">복원력은 실패를 방지하는 기능이 아닌 실패가 발생할 수 있다는 사실을 받아들이고 가동 중지 시간 또는 데이터 손실을 방지할 수 있도록 해당 실패에 응답하는 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="f5933-107">Resiliency is not about avoiding failures, but accepting the fact that failures will occur, and then responding to them in a way that avoids downtime or data loss.</span></span> <span data-ttu-id="f5933-108">복원력의 목표는 오류 발생 후 애플리케이션을 완전히 작동 중인 상태로 되돌리는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f5933-108">The goal of resiliency is to return the application to a fully functioning state after a failure.</span></span>

<span data-ttu-id="f5933-109">애플리케이션은 최소한 하드웨어 기반 모델이 아닌 소프트웨어 기반 모델의 복원력을 구현하는 경우 클라우드에 사용할 준비가 된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f5933-109">Your application is ready for the cloud when, at a minimum, it implements a software-based model of resiliency, rather than a hardware-based model.</span></span> <span data-ttu-id="f5933-110">클라우드 애플리케이션은 결국 발생하게 되는 부분 실패를 수용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5933-110">Your cloud application must embrace the partial failures that will certainly occur.</span></span> <span data-ttu-id="f5933-111">애플리케이션을 디자인하거나 부분적으로 리팩터링하여 예상되는 부분 실패에 대한 복원력을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="f5933-111">Design or partially refactor your application to achieve resiliency with expected partial failures.</span></span> <span data-ttu-id="f5933-112">애플리케이션은 클라우드에서의 일시적 네트워크 중단과 노드 또는 VM 충돌과 같은 부분 실패에 대처할 수 있도록 디자인되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5933-112">It should be designed to cope with partial failures, like transient network outages and nodes, or VMs crashing in the cloud.</span></span> <span data-ttu-id="f5933-113">오케스트레이터 클러스터 내에서 다른 노드로 이동한 컨테이너도 애플리케이션에서 일시적 단기 실패를 유발할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5933-113">Even containers being moved to a different node within an orchestrator cluster can cause intermittent short failures within the application.</span></span>

## <a name="handling-partial-failure"></a><span data-ttu-id="f5933-114">부분 실패 처리</span><span class="sxs-lookup"><span data-stu-id="f5933-114">Handling partial failure</span></span>

<span data-ttu-id="f5933-115">클라우드 기반 애플리케이션의 경우 부분 실패의 위험이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5933-115">In a cloud-based application, there's an ever-present risk of partial failure.</span></span> <span data-ttu-id="f5933-116">예를 들어, 단일 웹 사이트 인스턴스 또는 컨테이너가 실패할 수도 있고, 단기간 동안 사용할 수 없거나 응답하지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5933-116">For instance, a single website instance or a container might fail, or it might be unavailable or unresponsive for a short time.</span></span> <span data-ttu-id="f5933-117">또는 단일 VM 또는 서버에서 충돌이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5933-117">Or, a single VM or server might crash.</span></span>

<span data-ttu-id="f5933-118">클라이언트와 서비스는 별도의 프로세스이기 때문에 서비스가 클라이언트의 요청에 적시에 응답하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5933-118">Because clients and services are separate processes, a service might not be able to respond in a timely manner to a client's request.</span></span> <span data-ttu-id="f5933-119">서비스가 오버로드되고 요청에 느리게 응답하거나, 네트워크 문제로 인해 짧은 시간 동안 액세스하지 못할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5933-119">The service might be overloaded and respond slowly to requests, or it might not be accessible for a short time because of network issues.</span></span>

<span data-ttu-id="f5933-120">예를 들어 Azure SQL Database에서 데이터베이스에 액세스하는 모놀리식 .NET 애플리케이션이 있다고 가정해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="f5933-120">For example, consider a monolithic .NET application that accesses a database in Azure SQL Database.</span></span> <span data-ttu-id="f5933-121">Azure SQL 데이터베이스 또는 다른 타사 서비스가 잠시 동안 응답하지 않는 경우(Azure SQL 데이터베이스는 다른 노드 또는 서버로 이동하고 몇 초 동안 응답하지 않을 수 있음) 사용자가 작업을 수행하려고 하면 애플리케이션에 충돌이 발생하고 이와 동시에 예외가 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5933-121">If the Azure SQL database or any other third-party service is unresponsive for a brief time (an Azure SQL database might be moved to a different node or server, and be unresponsive for a few seconds), when the user tries to do any action, the application might crash and show an exception at the same moment.</span></span>

<span data-ttu-id="f5933-122">HTTP 서비스를 사용하는 앱에서도 비슷한 시나리오가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5933-122">A similar scenario might occur in an app that consumes HTTP services.</span></span> <span data-ttu-id="f5933-123">단기간의 일시적 실패 동안 클라우드에서 네트워크 또는 서비스 자체를 사용하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5933-123">The network or the service itself might not be available in the cloud during a short, transient failure.</span></span>

<span data-ttu-id="f5933-124">그림 4-9에 표시된 것과 같은 복원력 있는 애플리케이션은 "지수 백오프를 사용하여 다시 시도"와 같은 기술을 구현하여 애플리케이션에서 리소스의 일시적 실패를 처리할 수 있는 기회가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5933-124">A resilient application like the one shown in Figure 4-9 should implement techniques like "retries with exponential backoff" to give the application an opportunity to handle transient failures in resources.</span></span> <span data-ttu-id="f5933-125">또한 애플리케이션에서 "회로 차단기"를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5933-125">You also should use "circuit breakers" in your applications.</span></span> <span data-ttu-id="f5933-126">회로 차단기는 실제로 장기 오류일 때 애플리케이션이 리소스에 액세스를 시도하는 것을 차단합니다.</span><span class="sxs-lookup"><span data-stu-id="f5933-126">A circuit breaker stops an application from trying to access a resource when it's actually a long-term failure.</span></span> <span data-ttu-id="f5933-127">애플리케이션은 회로 차단기를 사용하여 자신에 대한 서비스 거부를 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="f5933-127">By using a circuit breaker, the application avoids provoking a denial of service to itself.</span></span>

![지수 백오프를 사용하여 다시 시도에 의해 처리되는 부분 실패의 다이어그램](./media/retry-partial-failures.png)

<span data-ttu-id="f5933-129">**그림 4-9.**</span><span class="sxs-lookup"><span data-stu-id="f5933-129">**Figure 4-9.**</span></span> <span data-ttu-id="f5933-130">지수 백오프를 사용하여 다시 시도에 의해 처리되는 부분 실패</span><span class="sxs-lookup"><span data-stu-id="f5933-130">Partial failures handled by retries with exponential backoff</span></span>

<span data-ttu-id="f5933-131">HTTP 리소스와 데이터베이스 리소스 모두에서 이러한 기술을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5933-131">You can use these techniques both in HTTP resources and in database resources.</span></span> <span data-ttu-id="f5933-132">그림 4-9에서는 애플리케이션이 3계층 아키텍처를 기반으로 하므로 서비스 수준(HTTP) 및 데이터 계층 수준(TCP)에서 이러한 기술이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f5933-132">In Figure 4-9, the application is based on a 3-tier architecture, so you need these techniques at the services level (HTTP) and at the data tier level (TCP).</span></span> <span data-ttu-id="f5933-133">데이터베이스 이외에 단일 앱 계층만 사용하는 모놀리식 애플리케이션(추가 서비스 또는 마이크로 서비스가 없음)에서는 데이터베이스 연결 수준에서 일시적 실패를 처리하는 것으로 충분할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5933-133">In a monolithic application that uses only a single app tier in addition to the database (no additional services or microservices), handling transient failures at the database connection level might be enough.</span></span> <span data-ttu-id="f5933-134">이 시나리오에서는 특정한 데이터베이스 연결 구성만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f5933-134">In that scenario, just a particular configuration of the database connection is required.</span></span>

<span data-ttu-id="f5933-135">데이터베이스에 액세스하는 복원력 있는 통신을 구현하는 경우 이는 사용 중인 .NET 버전에 따라 간단할 수 있습니다. (예를 들어 [Entity Framework 6 이상](/ef/ef6/fundamentals/connection-resiliency/retry-logic)에서는</span><span class="sxs-lookup"><span data-stu-id="f5933-135">When implementing resilient communications that access the database, depending on the version of .NET you are using, it can be straightforward (for example, [with Entity Framework 6 or later](/ef/ef6/fundamentals/connection-resiliency/retry-logic).</span></span> <span data-ttu-id="f5933-136">데이터베이스 연결을 구성하는 문제일 뿐입니다.)</span><span class="sxs-lookup"><span data-stu-id="f5933-136">It's just a matter of configuring the database connection).</span></span> <span data-ttu-id="f5933-137">또는 [일시적 실패 처리 애플리케이션 블록](/previous-versions/msp-n-p/hh680934(v=pandp.50))과 같은 추가 라이브러를 사용하거나(이전 버전의 .NET) 심지어 사용자 고유 라이브러리를 구현해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5933-137">Or, you might need to use additional libraries like the [Transient Fault Handling Application Block](/previous-versions/msp-n-p/hh680934(v=pandp.50)) (for earlier versions of .NET), or even implement your own library.</span></span>

<span data-ttu-id="f5933-138">HTTP 다시 시도 및 회로 차단기를 구현할 때 .NET 관련 권장 사항은 .NET Core 지원을 포함하는 .NET Framework 4.0, .NET Framework 4.5 및 .NET Standard 1.1을 대상으로 하는 [Polly](https://github.com/App-vNext/Polly) 라이브러리를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f5933-138">When implementing HTTP retries and circuit breakers, the recommendation for .NET is to use the [Polly](https://github.com/App-vNext/Polly) library, which targets .NET Framework 4.0, .NET Framework 4.5, and .NET Standard 1.1, which includes .NET Core support.</span></span>

<span data-ttu-id="f5933-139">클라우드에서 부분 실패를 처리하기 위한 전략을 구현하는 방법을 알아보려면 다음 참조를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f5933-139">To learn how to implement strategies for handling partial failures in the cloud, see the following references.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="f5933-140">추가 자료</span><span class="sxs-lookup"><span data-stu-id="f5933-140">Additional resources</span></span>

- <span data-ttu-id="f5933-141">**부분 실패를 처리하기 위한 복원력 있는 통신 구현**</span><span class="sxs-lookup"><span data-stu-id="f5933-141">**Implementing resilient communication to handle partial failure**</span></span>

    [https://docs.microsoft.com/dotnet/architecture/microservices/implement-resilient-applications/partial-failure-strategies](../../microservices/implement-resilient-applications/partial-failure-strategies.md)

- <span data-ttu-id="f5933-142">**Entity Framework 연결 복원력 및 다시 시도 논리(버전 6 이상)**</span><span class="sxs-lookup"><span data-stu-id="f5933-142">**Entity Framework connection resiliency and retry logic (version 6 and later)**</span></span>

    [https://docs.microsoft.com/ef/ef6/fundamentals/connection-resiliency/retry-logic](/ef/ef6/fundamentals/connection-resiliency/retry-logic)

- <span data-ttu-id="f5933-143">**일시적인 오류 처리 애플리케이션 블록**</span><span class="sxs-lookup"><span data-stu-id="f5933-143">**The Transient Fault Handling Application Block**</span></span>

- <https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50)>

- <span data-ttu-id="f5933-144">**복원력 있는 HTTP 통신용 Polly 라이브러리**</span><span class="sxs-lookup"><span data-stu-id="f5933-144">**Polly library for resilient HTTP communication**</span></span>

    <https://github.com/App-vNext/Polly>

>[!div class="step-by-step"]
><span data-ttu-id="f5933-145">[이전](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
>[다음](modernize-your-apps-with-monitoring-and-telemetry.md)</span><span class="sxs-lookup"><span data-stu-id="f5933-145">[Previous](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Next](modernize-your-apps-with-monitoring-and-telemetry.md)</span></span>
