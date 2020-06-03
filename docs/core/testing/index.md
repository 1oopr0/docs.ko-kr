---
title: .NET Core 및 .NET Standard의 단위 테스트
description: 이 문서에서는 .NET Core 및 .NET Standard 프로젝트에 대한 단위 테스트의 간략한 개요를 제공합니다.
author: ardalis
ms.author: wiwagn
ms.date: 05/18/2020
zone_pivot_groups: unit-testing-framework-set-one
ms.openlocfilehash: e15f80b173389cdff86c6e62013e9c0f21171dd6
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703096"
---
# <a name="unit-testing-in-net-core-and-net-standard"></a><span data-ttu-id="1df3f-103">.NET Core 및 .NET Standard의 단위 테스트</span><span class="sxs-lookup"><span data-stu-id="1df3f-103">Unit testing in .NET Core and .NET Standard</span></span>

<span data-ttu-id="1df3f-104">.NET Core를 통해 쉽게 단위 테스트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1df3f-104">.NET Core makes it easy to create unit tests.</span></span> <span data-ttu-id="1df3f-105">이 문서에서는 단위 테스트를 소개하고 이 테스트와 다른 테스트의 차이점을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1df3f-105">This article introduces unit tests and illustrates how they differ from other kinds of tests.</span></span> <span data-ttu-id="1df3f-106">페이지 아래쪽에 있는 연결된 리소스는 테스트 프로젝트를 솔루션에 추가하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="1df3f-106">The linked resources near the bottom of the page show you how to add a test project to your solution.</span></span> <span data-ttu-id="1df3f-107">테스트 프로젝트를 설정한 후에 명령줄 또는 Visual Studio를 사용하여 단위 테스트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1df3f-107">After you set up your test project, you will be able to run your unit tests using the command line or Visual Studio.</span></span>

<span data-ttu-id="1df3f-108">**ASP.NET Core** 프로젝트를 테스트하는 경우 [ASP.NET Core의 통합 테스트](/aspnet/core/test/integration-tests#test-app-prerequisites)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1df3f-108">If you're testing an **ASP.NET Core** project, see [Integration tests in ASP.NET Core](/aspnet/core/test/integration-tests#test-app-prerequisites).</span></span>

<span data-ttu-id="1df3f-109">.NET Core 2.0 이상은 [.NET Standard 2.0](../../standard/net-standard.md)을 지원하며 해당 라이브러리를 사용하여 단위 테스트를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="1df3f-109">.NET Core 2.0 and later supports [.NET Standard 2.0](../../standard/net-standard.md), and we will use its libraries to demonstrate unit tests.</span></span>

<span data-ttu-id="1df3f-110">C#, F# 및 Visual Basic에서 개인 프로젝트에 대한 시작점으로 기본 제공.NET Core 2.0 이상의 단위 테스트 프로젝트 템플릿을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1df3f-110">You are able to use built-in .NET Core 2.0 and later unit test project templates for C#, F# and Visual Basic as a starting point for your personal project.</span></span>

## <a name="what-are-unit-tests"></a><span data-ttu-id="1df3f-111">단위 테스트란?</span><span class="sxs-lookup"><span data-stu-id="1df3f-111">What are unit tests?</span></span>

<span data-ttu-id="1df3f-112">자동화된 테스트가 있다면 소프트웨어 애플리케이션이 작성자가 의도한 대로 수행되는지 확인하는 좋은 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="1df3f-112">Having automated tests is a great way to ensure a software application does what its authors intend it to do.</span></span> <span data-ttu-id="1df3f-113">소프트웨어 애플리케이션에 대해 여러 종류의 테스트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1df3f-113">There are multiple types of tests for software applications.</span></span> <span data-ttu-id="1df3f-114">여기에는 통합 테스트, 웹 테스트, 부하 테스트 등이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1df3f-114">These include integration tests, web tests, load tests, and others.</span></span> <span data-ttu-id="1df3f-115">**단위 테스트**는 개별 소프트웨어 구성 요소와 메서드를 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="1df3f-115">**Unit tests** test individual software components and methods.</span></span> <span data-ttu-id="1df3f-116">단위 테스트는 개발자의 제어 내에서만 코드를 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1df3f-116">Unit tests should only test code within the developer’s control.</span></span> <span data-ttu-id="1df3f-117">인프라 문제를 테스트하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1df3f-117">They should not test infrastructure concerns.</span></span> <span data-ttu-id="1df3f-118">인프라 문제에는 데이터베이스, 파일 시스템 및 네트워크 리소스가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1df3f-118">Infrastructure concerns include databases, file systems, and network resources.</span></span>

<span data-ttu-id="1df3f-119">또한 테스트를 작성하는 모범 사례가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1df3f-119">Also, keep in mind there are best practices for writing tests.</span></span> <span data-ttu-id="1df3f-120">예를 들어 [TDD(테스트 기반 개발)](https://deviq.com/test-driven-development/)는 확인하려는 코드보다 단위 테스트를 먼저 작성한 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="1df3f-120">For example, [Test Driven Development (TDD)](https://deviq.com/test-driven-development/) is when a unit test is written before the code it is meant to check.</span></span> <span data-ttu-id="1df3f-121">TDD는 책을 작성하기 전에 책에 대한 개요를 만드는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1df3f-121">TDD is like creating an outline for a book before we write it.</span></span> <span data-ttu-id="1df3f-122">이 기능을 통해 개발자가 간단하고 읽을 수 있고 효율적인 코드를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1df3f-122">It is meant to help developers write simpler, more readable, and efficient code.</span></span>

> [!NOTE]
> <span data-ttu-id="1df3f-123">ASP.NET 팀은 [이러한 규칙](https://github.com/dotnet/aspnetcore/wiki/Engineering-guidelines#unit-tests-and-functional-tests)을 따라 개발자가 테스트 클래스 및 메서드에 대해 적절한 이름을 제공할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="1df3f-123">The ASP.NET team follows [these conventions](https://github.com/dotnet/aspnetcore/wiki/Engineering-guidelines#unit-tests-and-functional-tests) to help developers come up with good names for test classes and methods.</span></span>

<span data-ttu-id="1df3f-124">단위 테스트를 작성하는 경우 인프라에 대한 종속성을 도입하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1df3f-124">Try not to introduce dependencies on infrastructure when writing unit tests.</span></span> <span data-ttu-id="1df3f-125">테스트가 느리고 불안정해지며 통합 테스트를 위해 예약되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1df3f-125">These make the tests slow and brittle, and should be reserved for integration tests.</span></span> <span data-ttu-id="1df3f-126">[명시적 종속성 원칙](https://deviq.com/explicit-dependencies-principle/)을 따르고 [종속성 주입](/aspnet/core/fundamentals/dependency-injection)을 사용하여 애플리케이션에서 이러한 종속성을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1df3f-126">You can avoid these dependencies in your application by following the [Explicit Dependencies Principle](https://deviq.com/explicit-dependencies-principle/) and using [Dependency Injection](/aspnet/core/fundamentals/dependency-injection).</span></span> <span data-ttu-id="1df3f-127">통합 테스트의 개별 프로젝트에서 단위 테스트를 유지할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1df3f-127">You can also keep your unit tests in a separate project from your integration tests.</span></span> <span data-ttu-id="1df3f-128">이렇게 하면 단위 테스트 프로젝트가 인프라 패키지에 대한 참조 또는 종속성을 갖지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1df3f-128">This ensures your unit test project doesn’t have references to or dependencies on infrastructure packages.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1df3f-129">다음 단계</span><span class="sxs-lookup"><span data-stu-id="1df3f-129">Next steps</span></span>

<span data-ttu-id="1df3f-130">.NET Core 프로젝트의 단위 테스트에 대한 자세한 내용:</span><span class="sxs-lookup"><span data-stu-id="1df3f-130">More information on unit testing in .NET Core projects:</span></span>

<span data-ttu-id="1df3f-131">.NET Core 단위 테스트 프로젝트는 다음에 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="1df3f-131">.NET Core unit test projects are supported for:</span></span>

- [<span data-ttu-id="1df3f-132">C#</span><span class="sxs-lookup"><span data-stu-id="1df3f-132">C#</span></span>](../../csharp/index.yml)
- [<span data-ttu-id="1df3f-133">F#</span><span class="sxs-lookup"><span data-stu-id="1df3f-133">F#</span></span>](../../fsharp/index.yml)
- [<span data-ttu-id="1df3f-134">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1df3f-134">Visual Basic</span></span>](../../visual-basic/index.yml)

<span data-ttu-id="1df3f-135">여러 단위 테스트 프레임워크 중에서 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1df3f-135">You can also choose between several unit test frameworks:</span></span>

- [<span data-ttu-id="1df3f-136">xUnit</span><span class="sxs-lookup"><span data-stu-id="1df3f-136">xUnit</span></span>](https://xunit.net/)
- [<span data-ttu-id="1df3f-137">NUnit</span><span class="sxs-lookup"><span data-stu-id="1df3f-137">NUnit</span></span>](https://nunit.org)
- [<span data-ttu-id="1df3f-138">MSTest</span><span class="sxs-lookup"><span data-stu-id="1df3f-138">MSTest</span></span>](https://github.com/Microsoft/testfx-docs)

<span data-ttu-id="1df3f-139">다음 연습에서 자세히 알아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1df3f-139">You can learn more in the following walkthroughs:</span></span>

:::zone pivot="mstest"

- <span data-ttu-id="1df3f-140">.NET Core CLI와 함께 [*MSTest* 및 *C#* 을 사용하여 단위 테스트 만들기](unit-testing-with-mstest.md)</span><span class="sxs-lookup"><span data-stu-id="1df3f-140">Create unit tests using [*MSTest* and *C#* with the .NET Core CLI](unit-testing-with-mstest.md).</span></span>
- <span data-ttu-id="1df3f-141">.NET Core CLI와 함께 [*MSTest* 및 *F#* 을 사용하여 단위 테스트 만들기](unit-testing-fsharp-with-mstest.md)</span><span class="sxs-lookup"><span data-stu-id="1df3f-141">Create unit tests using [*MSTest* and *F#* with the .NET Core CLI](unit-testing-fsharp-with-mstest.md).</span></span>
- <span data-ttu-id="1df3f-142">.NET Core CLI와 함께 [*MSTest* 및 *Visual Basic*을 사용하여 단위 테스트 만들기](unit-testing-visual-basic-with-mstest.md)</span><span class="sxs-lookup"><span data-stu-id="1df3f-142">Create unit tests using [*MSTest* and *Visual Basic* with the .NET Core CLI](unit-testing-visual-basic-with-mstest.md).</span></span>

:::zone-end
:::zone pivot="xunit"

- <span data-ttu-id="1df3f-143">.NET Core CLI와 함께 [*xUnit* 및 *C#* 을 사용하여 단위 테스트 만들기](unit-testing-with-dotnet-test.md)</span><span class="sxs-lookup"><span data-stu-id="1df3f-143">Create unit tests using [*xUnit* and *C#* with the .NET Core CLI](unit-testing-with-dotnet-test.md).</span></span>
- <span data-ttu-id="1df3f-144">.NET Core CLI와 함께 [*xUnit* 및 *F#* 을 사용하여 단위 테스트 만들기](unit-testing-fsharp-with-dotnet-test.md)</span><span class="sxs-lookup"><span data-stu-id="1df3f-144">Create unit tests using [*xUnit* and *F#* with the .NET Core CLI](unit-testing-fsharp-with-dotnet-test.md).</span></span>
- <span data-ttu-id="1df3f-145">.NET Core CLI와 함께 [*xUnit* 및 *Visual Basic*을 사용하여 단위 테스트 만들기](unit-testing-visual-basic-with-dotnet-test.md)</span><span class="sxs-lookup"><span data-stu-id="1df3f-145">Create unit tests using [*xUnit* and *Visual Basic* with the .NET Core CLI](unit-testing-visual-basic-with-dotnet-test.md).</span></span>

:::zone-end
:::zone pivot="nunit"

- <span data-ttu-id="1df3f-146">.NET Core CLI와 함께 [*NUnit* 및 *C#* 을 사용하여 단위 테스트 만들기](unit-testing-with-nunit.md)</span><span class="sxs-lookup"><span data-stu-id="1df3f-146">Create unit tests using [*NUnit* and *C#* with the .NET Core CLI](unit-testing-with-nunit.md).</span></span>
- <span data-ttu-id="1df3f-147">.NET Core CLI와 함께 [*NUnit* 및 *F#* 을 사용하여 단위 테스트 만들기](unit-testing-fsharp-with-nunit.md)</span><span class="sxs-lookup"><span data-stu-id="1df3f-147">Create unit tests using [*NUnit* and *F#* with the .NET Core CLI](unit-testing-fsharp-with-nunit.md).</span></span>
- <span data-ttu-id="1df3f-148">.NET Core CLI와 함께 [*NUnit* 및 *Visual Basic*을 사용하여 단위 테스트 만들기](unit-testing-visual-basic-with-nunit.md)</span><span class="sxs-lookup"><span data-stu-id="1df3f-148">Create unit tests using [*NUnit* and *Visual Basic* with the .NET Core CLI](unit-testing-visual-basic-with-nunit.md).</span></span>

:::zone-end

<span data-ttu-id="1df3f-149">다음 문서에서 자세히 알아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1df3f-149">You can learn more in the following articles:</span></span>

- <span data-ttu-id="1df3f-150">Visual Studio Enterprise는 .NET Core를 위한 훌륭한 테스트 도구를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1df3f-150">Visual Studio Enterprise offers great testing tools for .NET Core.</span></span> <span data-ttu-id="1df3f-151">[Live Unit Testing](/visualstudio/test/live-unit-testing) 또는 [ 코드 검사](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md#working-with-code-coverage)를 통해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="1df3f-151">Check out [Live Unit Testing](/visualstudio/test/live-unit-testing) or [code coverage](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md#working-with-code-coverage) to learn more.</span></span>
- <span data-ttu-id="1df3f-152">선택적 단위 테스트를 실행하는 방법에 대한 추가 정보는 [선택적 단위 테스트 실행](selective-unit-tests.md) 또는 [Visual Studio를 사용하여 테스트 포함 및 제외](/visualstudio/test/live-unit-testing#include-and-exclude-test-projects-and-test-methods)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1df3f-152">For more information on how to run selective unit tests, see [Running selective unit tests](selective-unit-tests.md), or [including and excluding tests with Visual Studio](/visualstudio/test/live-unit-testing#include-and-exclude-test-projects-and-test-methods).</span></span>
- <span data-ttu-id="1df3f-153">[.NET Core 및 Visual Studio와 xUnit을 사용하는 방법](https://xunit.github.io/docs/getting-started-dotnet-core.html)</span><span class="sxs-lookup"><span data-stu-id="1df3f-153">[How to use xUnit with .NET Core and Visual Studio](https://xunit.github.io/docs/getting-started-dotnet-core.html).</span></span>
