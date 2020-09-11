---
title: .NET Core 및 오픈 소스
description: .NET Standard의 범용 모듈식 플랫폼 간 오픈 소스 구현인 .NET Core에 대한 개요를 읽습니다.
ms.date: 03/30/2017
ms.assetid: e6bd4655-ce37-4003-8462-468a6fe2c40f
ms.openlocfilehash: 4627d4cc1bf45f3a7ad3f269279384b4a303f00d
ms.sourcegitcommit: b1f4756120deaecb8b554477bb040620f69a4209
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/03/2020
ms.locfileid: "89414918"
---
# <a name="net-core-and-open-source"></a><span data-ttu-id="97eea-103">.NET Core 및 오픈 소스</span><span class="sxs-lookup"><span data-stu-id="97eea-103">.NET Core and open source</span></span>

<span data-ttu-id="97eea-104">이 문서에서는 .NET Core에 대한 간략한 개요 및 자세한 정보를 찾는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="97eea-104">This article provides a brief overview of what .NET Core is and shows how you can find more information.</span></span>

## <a name="what-is-net-core"></a><span data-ttu-id="97eea-105">.NET Core란?</span><span class="sxs-lookup"><span data-stu-id="97eea-105">What is .NET Core?</span></span>  

<span data-ttu-id="97eea-106">.NET Core는 .NET Standard의 범용 모듈식 플랫폼 간 오픈 소스 구현입니다.</span><span class="sxs-lookup"><span data-stu-id="97eea-106">.NET Core is a general purpose, modular, cross-platform, and open-source implementation of the .NET Standard.</span></span> <span data-ttu-id="97eea-107">.NET Framework와 동일한 많은 API를 포함하고 있으며(.NET Core는 작은 집합) 다양한 운영 체제 및 대상 칩을 지원하는 런타임, 프레임워크, 컴파일러 및 도구 구성 요소를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="97eea-107">It contains many of the same APIs as the .NET Framework (but .NET Core is a smaller set) and includes runtime, framework, compiler, and tools components that support a variety of operating systems and chip targets.</span></span> <span data-ttu-id="97eea-108">.NET Core 구현은 주로 ASP.NET Core 작업을 기반으로 하지만 많은 최신 구현에 대한 필요와 욕구에 의해서도 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="97eea-108">The .NET Core implementation was primarily driven by the ASP.NET Core workloads but also by the need and desire to have a more modern implementation.</span></span> <span data-ttu-id="97eea-109">디바이스, 클라우드 및 포함/IoT 시나리오에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97eea-109">It can be used in device, cloud, and embedded/IoT scenarios.</span></span>  
  
<span data-ttu-id="97eea-110">.NET Core를 시작하려면 .NET 자습서 [Hello World 10분 완성](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro)를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="97eea-110">To get started with .NET Core, visit the .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro).</span></span>  
  
<span data-ttu-id="97eea-111">다음은 .NET Core의 주요 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="97eea-111">The main characteristics of .NET Core are:</span></span>
  
- <span data-ttu-id="97eea-112">**플랫폼 간:** .NET Core는 필요한 앱 기능을 구현하고 플랫폼 대상에 관계없이 이 코드를 재사용하기 위한 주요 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="97eea-112">**Cross-platform:** .NET Core provides key functionality to implement the app features you need and reuse this code regardless of your platform target.</span></span> <span data-ttu-id="97eea-113">현재 세 개의 주요 OS(운영 체제)를 지원합니다. Windows, Linux 및 macOS.</span><span class="sxs-lookup"><span data-stu-id="97eea-113">It currently supports three main operating systems (OS): Windows, Linux, and macOS.</span></span> <span data-ttu-id="97eea-114">지원되는 운영 체제 간에 수정하지 않고 실행되는 앱과 라이브러리를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97eea-114">You can write apps and libraries that run unmodified across supported operating systems.</span></span> <span data-ttu-id="97eea-115">지원되는 운영 체제의 목록을 보려면 [.NET Core roadmap](https://github.com/dotnet/core/blob/master/roadmap.md)(.NET Core 로드맵)을 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="97eea-115">To see the list of supported operating systems, visit [.NET Core roadmap](https://github.com/dotnet/core/blob/master/roadmap.md).</span></span>
  
- <span data-ttu-id="97eea-116">**오픈 소스:** .NET Core는 [.NET Foundation](https://www.dotnetfoundation.org/)에서 관리하는 여러 프로젝트 중 하나이며 [GitHub](https://github.com/)에서 사용 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="97eea-116">**Open source:** .NET Core is one of the many projects under the stewardship of the [.NET Foundation](https://www.dotnetfoundation.org/) and is available on [GitHub](https://github.com/).</span></span> <span data-ttu-id="97eea-117">오픈 소스 프로젝트인 .NET Core는 더욱 투명한 개발 프로세스와 적극적으로 참여하는 커뮤니티를 촉진합니다.</span><span class="sxs-lookup"><span data-stu-id="97eea-117">As an open-source project, .NET Core promotes a more transparent development process and an active and engaged community.</span></span>  
  
- <span data-ttu-id="97eea-118">**유연한 배포:** 응용 프로그램을 배포하는 방법은 프레임워크 종속 배포 또는 자체 포함 배포의 두 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97eea-118">**Flexible deployment:** there are two main ways to deploy your app: framework-dependent deployment or self-contained deployment.</span></span> <span data-ttu-id="97eea-119">프레임워크 종속 배포를 사용하는 경우, 사용자 응용 프로그램 및 제3자 종속 프로그램만 설치되고 사용자의 응용 프로그램이 .NET Core의 시스템 전체 버전에 따라 존재하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="97eea-119">With framework-dependent deployment, only your app and third-party dependencies are installed and your app depends on a system-wide version of .NET Core to be present.</span></span> <span data-ttu-id="97eea-120">자체 포함 배포를 사용하는 경우, 애플리케이션을 빌드하는 데 사용된 .NET Core 버전도 애플리케이션 및 타사 종속 프로그램과 함께 배포되며 다른 버전과 함께 나란히 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97eea-120">With self-contained deployment, the .NET Core version used to build your application is also deployed along with your app and third-party dependencies and can run side by side with other versions.</span></span> <span data-ttu-id="97eea-121">자세한 내용은 [.NET Core 애플리케이션 배포](../../core/deploying/index.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="97eea-121">For more information, see [.NET Core Application Deployment](../../core/deploying/index.md).</span></span>

- <span data-ttu-id="97eea-122">**모듈식:** .NET Core는 NuGet을 통해 작은 어셈블리 패키지로 릴리스되므로 모듈식입니다.</span><span class="sxs-lookup"><span data-stu-id="97eea-122">**Modular:** .NET Core is modular because it's released through NuGet in smaller assembly packages.</span></span> <span data-ttu-id="97eea-123">대부분의 핵심 기능을 포함하는 하나의 큰 어셈블리 대신, .NET Core는 작은 기능 중심 패키지로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="97eea-123">Rather than one large assembly that contains most of the core functionality, .NET Core is made available as smaller, feature-centric packages.</span></span> <span data-ttu-id="97eea-124">이런 모듈화는 더 많은 Agile 개발 모델을 활성화하고 필요한 NuGet 패키지만 포함하도록 애플리케이션을 최적화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97eea-124">This modularity enables a more agile development model for us and allows you to optimize your app to include just the NuGet packages you need.</span></span> <span data-ttu-id="97eea-125">작은 응용 프로그램 노출 영역 혜택에는 보안 강화, 서비스 절감, 성능 향상 및 사용한 만큼만 지불하는 비용 감소가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="97eea-125">The benefits of a smaller app surface area include tighter security, reduced servicing, improved performance, and decreased costs in a pay-for-what-you-use model.</span></span>  
  
## <a name="the-net-core-platform"></a><span data-ttu-id="97eea-126">.NET Core 플랫폼</span><span class="sxs-lookup"><span data-stu-id="97eea-126">The .NET Core platform</span></span>
  
<span data-ttu-id="97eea-127">.NET Core 플랫폼은 관리되는 컴파일러, 런타임, 기본 클래스 라이브러리 및 ASP.NET Core와 같은 다양한 애플리케이션 모델을 포함하는 여러 요소로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="97eea-127">The .NET Core platform is made up of several components, including the managed compilers, the runtime, the base class libraries, and numerous application models, such as ASP.NET Core.</span></span> <span data-ttu-id="97eea-128">다음의 [GitHub](https://github.com/) 리포지토리를 방문하여 다양한 구성 요소에 대해 자세히 알아보고 참여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97eea-128">You can learn more about the different components and get engaged by visiting the following [GitHub](https://github.com/) repos:</span></span>  
  
- [<span data-ttu-id="97eea-129">.NET Core 홈</span><span class="sxs-lookup"><span data-stu-id="97eea-129">.NET Core home</span></span>](https://github.com/dotnet/core)  
  
- [<span data-ttu-id="97eea-130">런타임 - .NET Core 플랫폼 및 런타임</span><span class="sxs-lookup"><span data-stu-id="97eea-130">Runtime - .NET Core platform and runtime</span></span>](https://github.com/dotnet/runtime)  
  
- [<span data-ttu-id="97eea-131">CLI - .NET Core 명령줄 도구</span><span class="sxs-lookup"><span data-stu-id="97eea-131">CLI - .NET Core command-line tools</span></span>](https://github.com/dotnet/cli)  
  
- [<span data-ttu-id="97eea-132">Roslyn - .NET 컴파일러 플랫폼</span><span class="sxs-lookup"><span data-stu-id="97eea-132">Roslyn - .NET Compiler Platform</span></span>](https://github.com/dotnet/roslyn)  
  
- [<span data-ttu-id="97eea-133">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="97eea-133">ASP.NET Core</span></span>](https://github.com/dotnet/aspnetcore)  
  
## <a name="see-also"></a><span data-ttu-id="97eea-134">참조</span><span class="sxs-lookup"><span data-stu-id="97eea-134">See also</span></span>

- [<span data-ttu-id="97eea-135">.NET 자습서 - Hello World 10분 완성</span><span class="sxs-lookup"><span data-stu-id="97eea-135">.NET tutorial - Hello World in 10 minutes</span></span>](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro)
- [<span data-ttu-id="97eea-136">.NET Core 소개</span><span class="sxs-lookup"><span data-stu-id="97eea-136">.NET Core introduction</span></span>](../../core/introduction.md)
- [<span data-ttu-id="97eea-137">ASP.NET Core 문서</span><span class="sxs-lookup"><span data-stu-id="97eea-137">ASP.NET Core docs</span></span>](/aspnet/core/)
