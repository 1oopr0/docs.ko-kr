---
title: MEF(Managed Extensibility Framework)
description: 애플리케이션 개발자가 .NET 4 이상에서 구성 없이 확장을 검색하고 사용할 수 있게 해주는 MEF(Managed Extensibility Framework)에 대해 알아봅니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Managed Extensibility Framework, overview
- MEF, overview
ms.assetid: 6c61b4ec-c6df-4651-80f1-4854f8b14dde
ms.openlocfilehash: 00ed48f2202d4c04039ac264b1fe71474a02432e
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281253"
---
# <a name="managed-extensibility-framework-mef"></a><span data-ttu-id="fcbf4-103">MEF(Managed Extensibility Framework)</span><span class="sxs-lookup"><span data-stu-id="fcbf4-103">Managed Extensibility Framework (MEF)</span></span>

<span data-ttu-id="fcbf4-104">이 항목에서는 .NET Framework 4에 도입된 Managed Extensibility Framework에 대해 간략하게 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-104">This topic provides an overview of the Managed Extensibility Framework that was introduced in the .NET Framework 4.</span></span>

## <a name="what-is-mef"></a><span data-ttu-id="fcbf4-105">MEF란?</span><span class="sxs-lookup"><span data-stu-id="fcbf4-105">What is MEF?</span></span>

<span data-ttu-id="fcbf4-106">MEF(Managed Extensibility Framework)는 확장 가능한 경량 애플리케이션을 만드는 데 사용할 수 있는 라이브러리입니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-106">The Managed Extensibility Framework or MEF is a library for creating lightweight, and extensible applications.</span></span> <span data-ttu-id="fcbf4-107">애플리케이션 개발자는 MEF를 통해 구성을 수행하지 않고도 확장을 검색하여 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-107">It allows application developers to discover and use extensions with no configuration required.</span></span> <span data-ttu-id="fcbf4-108">또한 확장명 개발자는 코드를 쉽게 캡슐화하고 취약한 강한 종속성을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-108">It also lets extension developers easily encapsulate code and avoid fragile hard dependencies.</span></span> <span data-ttu-id="fcbf4-109">MEF를 통해 애플리케이션 내에서뿐 아니라 애플리케이션 간에도 확장을 다시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-109">MEF not only allows extensions to be reused within applications, but across applications as well.</span></span>

## <a name="the-problem-of-extensibility"></a><span data-ttu-id="fcbf4-110">확장성 문제</span><span class="sxs-lookup"><span data-stu-id="fcbf4-110">The problem of extensibility</span></span>

<span data-ttu-id="fcbf4-111">확장성을 지원해야 하는 대규모 애플리케이션을 설계한다고 가정해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-111">Imagine that you are the architect of a large application that must provide support for extensibility.</span></span> <span data-ttu-id="fcbf4-112">애플리케이션은 작은 구성 요소를 여러 개 포함해야 할 수 있으며 이러한 구성 요소를 만들고 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-112">Your application has to include a potentially large number of smaller components, and is responsible for creating and running them.</span></span>

<span data-ttu-id="fcbf4-113">이 경우 사용할 수 있는 가장 간단한 방식은 구성 요소를 애플리케이션에 코드로 포함하여 코드에서 직접 호출하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-113">The simplest approach to the problem is to include the components as source code in your application, and call them directly from your code.</span></span> <span data-ttu-id="fcbf4-114">그러나 이 방식에는 여러 가지 명백한 단점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-114">This has a number of obvious drawbacks.</span></span> <span data-ttu-id="fcbf4-115">그중 가장 중요한 것은 소스 코드를 수정하지 않으면 새 구성 요소를 추가할 수가 없다는 것입니다. 웹 애플리케이션의 경우에는 이러한 제한이 있어도 큰 문제가 없을 수 있지만 클라이언트 애플리케이션에서는 이러한 제한이 있어서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-115">Most importantly, you cannot add new components without modifying the source code, a restriction that might be acceptable in, for example, a Web application, but is unworkable in a client application.</span></span> <span data-ttu-id="fcbf4-116">또한 타사에서 개발한 구성 요소의 소스 코드에는 액세스할 수 없으며 자신이 개발한 구성 요소를 타사에서 액세스하도록 허용할 수 없다는 점도 문제입니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-116">Equally problematic, you may not have access to the source code for the components, because they might be developed by third parties, and for the same reason you cannot allow them to access yours.</span></span>

<span data-ttu-id="fcbf4-117">이 방식보다 약간 더 고급 방식은 애플리케이션과 구성 요소를 분리할 수 있도록 확장점(인터페이스)을 제공하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-117">A slightly more sophisticated approach would be to provide an extension point or interface, to permit decoupling between the application and its components.</span></span> <span data-ttu-id="fcbf4-118">이 모델에서는 구성 요소가 구현할 수 있는 인터페이스와 구성 요소가 애플리케이션과 상호 작용하는 데 사용할 수 있는 API를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-118">Under this model, you might provide an interface that a component can implement, and an API to enable it to interact with your application.</span></span> <span data-ttu-id="fcbf4-119">그러면 소스 코드 액세스가 필요하다는 문제는 해결되지만 이 방식에도 고유한 문제점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-119">This solves the problem of requiring source code access, but it still has its own difficulties.</span></span>

<span data-ttu-id="fcbf4-120">애플리케이션에는 자체적으로 구성 요소를 검색하는 기능이 없으므로 사용 가능하며 로드해야 하는 구성 요소를 명시적으로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-120">Because the application lacks any capacity for discovering components on its own, it must still be explicitly told which components are available and should be loaded.</span></span> <span data-ttu-id="fcbf4-121">일반적으로는 이를 위해 사용 가능한 구성 요소를 구성 파일에 명시적으로 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-121">This is typically accomplished by explicitly registering the available components in a configuration file.</span></span> <span data-ttu-id="fcbf4-122">따라서 구성 요소가 올바른지를 확인하는 과정에서 유지 관리 문제가 발생할 수 있습니다(특히 업데이트를 수행하는 개발자가 아닌 최종 사용자의 경우).</span><span class="sxs-lookup"><span data-stu-id="fcbf4-122">This means that assuring that the components are correct becomes a maintenance issue, particularly if it is the end user and not the developer who is expected to do the updating.</span></span>

<span data-ttu-id="fcbf4-123">또한 구성 요소는 엄격하게 정의된 애플리케이션 자체 채널을 통해서가 아니면 서로 통신할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-123">In addition, components are incapable of communicating with one another, except through the rigidly defined channels of the application itself.</span></span> <span data-ttu-id="fcbf4-124">일반적으로 애플리케이션 설계자가 특정 통신이 필요함을 예측하지 못했다면 이러한 통신은 불가능합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-124">If the application architect has not anticipated the need for a particular communication, it is usually impossible.</span></span>

<span data-ttu-id="fcbf4-125">마지막으로, 구성 요소 개발자는 구현하는 인터페이스를 포함하는 어셈블리에 대한 강한 종속성을 허용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-125">Finally, the component developers must accept a hard dependency on what assembly contains the interface they implement.</span></span> <span data-ttu-id="fcbf4-126">이로 인해 구성 요소를 둘 이상의 애플리케이션에서 사용하기가 어려워지며, 구성 요소용 테스트 프레임워크를 만들 때도 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-126">This makes it difficult for a component to be used in more than one application, and can also create problems when you create a test framework for components.</span></span>

## <a name="what-mef-provides"></a><span data-ttu-id="fcbf4-127">MEF에서 제공하는 기능</span><span class="sxs-lookup"><span data-stu-id="fcbf4-127">What MEF provides</span></span>

<span data-ttu-id="fcbf4-128">이처럼 사용 가능한 구성 요소를 명시적으로 등록하는 대신 MEF는 *컴퍼지션*을 통해 구성 요소를 암시적으로 검색하는 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-128">Instead of this explicit registration of available components, MEF provides a way to discover them implicitly, via *composition*.</span></span> <span data-ttu-id="fcbf4-129">MEF 구성 요소(‘파트’)는 해당 종속성(*Import*)과 제공하는 기능(*Export*)을 모두 선언적으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-129">A MEF component, called a *part*, declaratively specifies both its dependencies (known as *imports*) and what capabilities (known as *exports*) it makes available.</span></span> <span data-ttu-id="fcbf4-130">파트를 작성할 때 MEF 컴퍼지션 엔진은 다른 파트에서 제공되는 항목을 사용하여 Import를 충족합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-130">When a part is created, the MEF composition engine satisfies its imports with what is available from other parts.</span></span>

<span data-ttu-id="fcbf4-131">이러한 방식이 사용되므로 이전 섹션에서 설명한 문제가 해결됩니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-131">This approach solves the problems discussed in the previous section.</span></span> <span data-ttu-id="fcbf4-132">MEF 파트는 해당 기능을 선언적으로 지정하기 때문에 런타임에 검색이 가능합니다. 따라서 애플리케이션이 하드 코드된 참조나 취약한 구성 파일 없이도 파트를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-132">Because MEF parts declaratively specify their capabilities, they are discoverable at runtime, which means an application can make use of parts without either hard-coded references or fragile configuration files.</span></span> <span data-ttu-id="fcbf4-133">MEF를 사용하는 경우 애플리케이션이 파트를 인스턴스화하거나 어셈블리를 로드하지 않고도 메타데이터를 기준으로 파트를 검색 및 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-133">MEF allows applications to discover and examine parts by their metadata, without instantiating them or even loading their assemblies.</span></span> <span data-ttu-id="fcbf4-134">그러므로 확장을 로드해야 하는 시기와 방법을 면밀하게 지정하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-134">As a result, there is no need to carefully specify when and how extensions should be loaded.</span></span>

<span data-ttu-id="fcbf4-135">파트너는 제공된 Export뿐 아니라 Import(다른 파트에 의해 채워짐)도 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-135">In addition to its provided exports, a part can specify its imports, which will be filled by other parts.</span></span> <span data-ttu-id="fcbf4-136">따라서 파트가 서로 쉽게 통신할 수 있으며 효율적인 코드 팩터링이 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-136">This makes communication among parts not only possible, but easy, and allows for good factoring of code.</span></span> <span data-ttu-id="fcbf4-137">예를 들어 여러 구성 요소에 공통적으로 사용되는 서비스를 별도의 파트에 팩터링하여 쉽게 수정하거나 대체할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-137">For example, services common to many components can be factored into a separate part and easily modified or replaced.</span></span>

<span data-ttu-id="fcbf4-138">MEF 모델에서는 특정 애플리케이션 어셈블리에 대한 강한 종속성이 필요하지 않으므로 애플리케이션 간에 확장을 다시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-138">Because the MEF model requires no hard dependency on a particular application assembly, it allows extensions to be reused from application to application.</span></span> <span data-ttu-id="fcbf4-139">이로 인해 애플리케이션에 관계없이 확장명 구성 요소를 테스트하기 위한 테스트 경도를 쉽게 개발할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-139">This also makes it easy to develop a test harness, independent of the application, to test extension components.</span></span>

<span data-ttu-id="fcbf4-140">MEF를 사용하여 작성된 확장 가능한 애플리케이션은 확장 구성 요소를 통해 채울 수 있는 Import를 선언하며, 애플리케이션 서비스를 확장에 노출하기 위해 Export도 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-140">An extensible application written by using MEF declares an import that can be filled by extension components, and may also declare exports in order to expose application services to extensions.</span></span> <span data-ttu-id="fcbf4-141">각 확장명 구성 요소는 Export를 선언하며 Import도 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-141">Each extension component declares an export, and may also declare imports.</span></span> <span data-ttu-id="fcbf4-142">이러한 방식으로 인해 확장명 구성 요소 자체를 자동으로 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-142">In this way, extension components themselves are automatically extensible.</span></span>

## <a name="where-mef-is-available"></a><span data-ttu-id="fcbf4-143">MEF를 사용할 수 있는 위치</span><span class="sxs-lookup"><span data-stu-id="fcbf4-143">Where MEF is available</span></span>

<span data-ttu-id="fcbf4-144">MEF는 .NET Framework 4의 필수 요소로, .NET Framework를 사용하는 모든 위치에서 사용 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-144">MEF is an integral part of the .NET Framework 4, and is available wherever the .NET Framework is used.</span></span> <span data-ttu-id="fcbf4-145">Windows Forms, WPF 또는 기타 기술을 사용하는 클라이언트 애플리케이션이나 ASP.NET을 사용하는 서버 애플리케이션에서 MEF를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-145">You can use MEF in your client applications, whether they use Windows Forms, WPF, or any other technology, or in server applications that use ASP.NET.</span></span>

## <a name="mef-and-maf"></a><span data-ttu-id="fcbf4-146">MEF 및 MAF</span><span class="sxs-lookup"><span data-stu-id="fcbf4-146">MEF and MAF</span></span>

<span data-ttu-id="fcbf4-147">이전 버전의 .NET Framework에는 애플리케이션이 확장을 격리 및 관리하도록 허용하는 MAF(Managed Add-in Framework)가 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-147">Previous versions of the .NET Framework introduced the Managed Add-in Framework (MAF), designed to allow applications to isolate and manage extensions.</span></span> <span data-ttu-id="fcbf4-148">MAF는 MEF에 비해 다소 수준이 높으며 확장 격리와 어셈블리 로드/언로드에 주력하는 반면 MEF에서는 검색 기능, 확장성 및 이동성에 주력합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-148">The focus of MAF is slightly higher-level than MEF, concentrating on extension isolation and assembly loading and unloading, while MEF's focus is on discoverability, extensibility, and portability.</span></span> <span data-ttu-id="fcbf4-149">이 두 프레임워크는 원활하게 상호 작용하며, 애플리케이션 하나에서 두 프레임워크를 모두 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-149">The two frameworks interoperate smoothly, and a single application can take advantage of both.</span></span>

## <a name="simplecalculator-an-example-application"></a><span data-ttu-id="fcbf4-150">SimpleCalculator: 예제 애플리케이션</span><span class="sxs-lookup"><span data-stu-id="fcbf4-150">SimpleCalculator: An example application</span></span>

<span data-ttu-id="fcbf4-151">MEF에서 수행할 수 있는 작업을 확인하는 가장 간단한 방법은 간단한 MEF 애플리케이션을 빌드하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-151">The simplest way to see what MEF can do is to build a simple MEF application.</span></span> <span data-ttu-id="fcbf4-152">이 예제에서는 SimpleCalculator라는 매우 간단한 계산기를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-152">In this example, you build a very simple calculator named SimpleCalculator.</span></span> <span data-ttu-id="fcbf4-153">SimpleCalculator에서는 &quot;5+3&quot; 또는 &quot;6-2&quot;와 같은 형식의 기본적인 산술 명령을 수락하고 정답을 반환하는 콘솔 애플리케이션을 만들려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-153">The goal of SimpleCalculator is to create a console application that accepts basic arithmetic commands, in the form "5+3" or "6-2", and returns the correct answers.</span></span> <span data-ttu-id="fcbf4-154">MEF를 사용하면 애플리케이션 코드를 변경하지 않고도 새 연산자를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-154">Using MEF, you'll be able to add new operators without changing the application code.</span></span>

<span data-ttu-id="fcbf4-155">이 예제의 전체 코드를 다운로드하려면 [SimpleCalculator sample (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/simple-calculator-vb/)(SimpleCalculator 샘플(Visual Basic))을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-155">To download the complete code for this example, see the [SimpleCalculator sample (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/simple-calculator-vb/).</span></span>

> [!NOTE]
> <span data-ttu-id="fcbf4-156">SimpleCalculator는 사용 방식을 보여 주는 실제 시나리오를 제공하기보다는 MEF의 개념과 구문을 제시하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-156">The purpose of SimpleCalculator is to demonstrate the concepts and syntax of MEF, rather than to necessarily provide a realistic scenario for its use.</span></span> <span data-ttu-id="fcbf4-157">MEF의 이점을 가장 효율적으로 활용할 수 있는 대부분의 애플리케이션은 SimpleCalculator보다 복잡합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-157">Many of the applications that would benefit most from the power of MEF are more complex than SimpleCalculator.</span></span> <span data-ttu-id="fcbf4-158">보다 포괄적인 예제는 GitHub에서 [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-158">For more extensive examples, see the [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef) on GitHub.</span></span>

- <span data-ttu-id="fcbf4-159">우선 Visual Studio에서 새 콘솔 애플리케이션 프로젝트를 만들고 이름을 `SimpleCalculator`로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-159">To start, in Visual Studio, create a new Console Application project and name it `SimpleCalculator`.</span></span>

- <span data-ttu-id="fcbf4-160">MEF가 있는 `System.ComponentModel.Composition` 어셈블리에 대한 참조를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-160">Add a reference to the `System.ComponentModel.Composition` assembly, where MEF resides.</span></span>

- <span data-ttu-id="fcbf4-161">*Module1.vb* 또는 *Program.cs*를 열고 `Imports` 및 `using`에 대한 `System.ComponentModel.Composition` 또는 `System.ComponentModel.Composition.Hosting`문을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-161">Open *Module1.vb* or *Program.cs* and add `Imports` or `using` statements for `System.ComponentModel.Composition` and `System.ComponentModel.Composition.Hosting`.</span></span> <span data-ttu-id="fcbf4-162">이 두 네임스페이스는 확장 가능한 애플리케이션을 개발하는 데 필요한 MEF 형식을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-162">These two namespaces contain MEF types you will need to develop an extensible application.</span></span>

- <span data-ttu-id="fcbf4-163">Visual Basic을 사용하는 경우 `Module1` 모듈을 선언하는 줄에 `Public` 키워드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-163">If you're using Visual Basic, add the `Public` keyword to the line that declares the `Module1` module.</span></span>

## <a name="composition-container-and-catalogs"></a><span data-ttu-id="fcbf4-164">컴퍼지션 컨테이너 및 카탈로그</span><span class="sxs-lookup"><span data-stu-id="fcbf4-164">Composition container and catalogs</span></span>

<span data-ttu-id="fcbf4-165">MEF 컴퍼지션 모델에서 핵심적인 요소는 사용 가능한 모든 파트를 포함하며 컴퍼지션을 수행하는 ‘컴퍼지션 컨테이너’입니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-165">The core of the MEF composition model is the *composition container*, which contains all the parts available and performs composition.</span></span> <span data-ttu-id="fcbf4-166">컴퍼지션이란 Import를 Export에 일치시키는 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-166">Composition is the matching up of imports to exports.</span></span> <span data-ttu-id="fcbf4-167">SimpleCalculator에서는 가장 일반적인 유형의 컴퍼지션 컨테이너인 <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-167">The most common type of composition container is <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, and you'll use this for SimpleCalculator.</span></span>

<span data-ttu-id="fcbf4-168">Visual Basic을 사용하는 경우 *Module1.vb*에서 `Program`이라는 public 클래스를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-168">If you're using Visual Basic, add a public class named `Program` in *Module1.vb*.</span></span>

<span data-ttu-id="fcbf4-169">*Module1.vb* 또는 *Program.cs*의 `Program` 클래스에 다음 줄을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-169">Add the following line to the `Program` class in *Module1.vb* or *Program.cs*:</span></span>

```vb
Dim _container As CompositionContainer
```

```csharp
private CompositionContainer _container;
```

<span data-ttu-id="fcbf4-170">컴퍼지션 컨테이너는 사용 가능한 파트를 검색하기 위해 ‘카탈로그’를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-170">In order to discover the parts available to it, the composition containers makes use of a *catalog*.</span></span> <span data-ttu-id="fcbf4-171">카탈로그는 일부 소스에서 사용 가능한 파트를 검색하는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-171">A catalog is an object that makes available parts discovered from some source.</span></span> <span data-ttu-id="fcbf4-172">MEF는 제공된 형식, 어셈블리 또는 디렉터리에서 파트를 검색하기 위한 카탈로그를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-172">MEF provides catalogs to discover parts from a provided type, an assembly, or a directory.</span></span> <span data-ttu-id="fcbf4-173">애플리케이션 개발자는 쉽게 새 카탈로그를 만들어 웹 서비스 등의 다른 소스에서 파트를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-173">Application developers can easily create new catalogs to discover parts from other sources, such as a Web service.</span></span>

<span data-ttu-id="fcbf4-174">`Program` 클래스에 다음 생성자를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-174">Add the following constructor to the `Program` class:</span></span>

```vb
Public Sub New()
    ' An aggregate catalog that combines multiple catalogs.
     Dim catalog = New AggregateCatalog()

    ' Adds all the parts found in the same assembly as the Program class.
    catalog.Catalogs.Add(New AssemblyCatalog(GetType(Program).Assembly))

    ' Create the CompositionContainer with the parts in the catalog.
    _container = New CompositionContainer(catalog)

    ' Fill the imports of this object.
    Try
        _container.ComposeParts(Me)
    Catch ex As CompositionException
        Console.WriteLine(ex.ToString)
    End Try
End Sub
```

```csharp
private Program()
{
    // An aggregate catalog that combines multiple catalogs.
    var catalog = new AggregateCatalog();
    // Adds all the parts found in the same assembly as the Program class.
    catalog.Catalogs.Add(new AssemblyCatalog(typeof(Program).Assembly));

    // Create the CompositionContainer with the parts in the catalog.
    _container = new CompositionContainer(catalog);

    // Fill the imports of this object.
    try
    {
        this._container.ComposeParts(this);
    }
    catch (CompositionException compositionException)
    {
        Console.WriteLine(compositionException.ToString());
   }
}
```

<span data-ttu-id="fcbf4-175"><xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A>를 호출하면 컴퍼지션 컨테이너에 특정 파트 집합(여기서는 현재 `Program` 인스턴스)을 작성하도록 명령합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-175">The call to <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> tells the composition container to compose a specific set of parts, in this case the current instance of `Program`.</span></span> <span data-ttu-id="fcbf4-176">그러나 이 시점에서는 `Program`에 채울 Import가 없으므로 아무 작업도 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-176">At this point, however, nothing will happen, since `Program` has no imports to fill.</span></span>

## <a name="imports-and-exports-with-attributes"></a><span data-ttu-id="fcbf4-177">특성이 포함된 Import 및 Export</span><span class="sxs-lookup"><span data-stu-id="fcbf4-177">Imports and Exports with attributes</span></span>

<span data-ttu-id="fcbf4-178">먼저 `Program`에서 계산기 Import를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-178">First, you have `Program` import a calculator.</span></span> <span data-ttu-id="fcbf4-179">그러면 `Program`으로 전송되는 콘솔 입력 및 출력과 같은 사용자 인터페이스 관련 사항을 계산기 논리에서 분리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-179">This allows the separation of user interface concerns, such as the console input and output that will go into `Program`, from the logic of the calculator.</span></span>

<span data-ttu-id="fcbf4-180">`Program` 클래스에 다음 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-180">Add the following code to the `Program` class:</span></span>

```vb
<Import(GetType(ICalculator))>
Public Property calculator As ICalculator
```

```csharp
[Import(typeof(ICalculator))]
public ICalculator calculator;
```

<span data-ttu-id="fcbf4-181">`calculator` 개체는 일반적인 방식으로 선언되지만 여기서는 해당 개체가 <xref:System.ComponentModel.Composition.ImportAttribute> 특성으로 데코레이팅되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-181">Notice that the declaration of the `calculator` object is not unusual, but that it is decorated with the <xref:System.ComponentModel.Composition.ImportAttribute> attribute.</span></span> <span data-ttu-id="fcbf4-182">이 특성은 Import로 지정할 항목을 선언합니다 즉, 개체를 구성할 때 컴퍼지션 엔진에서 특성이 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-182">This attribute declares something to be an import; that is, it will be filled by the composition engine when the object is composed.</span></span>

<span data-ttu-id="fcbf4-183">모든 Import에는 일치시킬 Export를 결정하는 ‘계약’이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-183">Every import has a *contract*, which determines what exports it will be matched with.</span></span> <span data-ttu-id="fcbf4-184">계약은 명시적으로 지정된 문자열일 수도 있고 MEF가 특정 형식(여기서는 `ICalculator` 인터페이스)에서 자동으로 생성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-184">The contract can be an explicitly specified string, or it can be automatically generated by MEF from a given type, in this case the interface `ICalculator`.</span></span> <span data-ttu-id="fcbf4-185">일치하는 계약을 사용하여 선언된 Export는 이 Import를 충족합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-185">Any export declared with a matching contract will fulfill this import.</span></span> <span data-ttu-id="fcbf4-186">여기서는 `calculator` 개체의 실제 형식이 `ICalculator`이지만 반드시 형식이 일치해야 하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-186">Note that while the type of the `calculator` object is in fact `ICalculator`, this is not required.</span></span> <span data-ttu-id="fcbf4-187">계약은 가져오는 개체의 형식과는 별개입니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-187">The contract is independent from the type of the importing object.</span></span> <span data-ttu-id="fcbf4-188">그러므로 여기서 `typeof(ICalculator)`를 빼도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-188">(In this case, you could leave out the `typeof(ICalculator)`.</span></span> <span data-ttu-id="fcbf4-189">명시적으로 지정하지 않는 경우 MEF는 계약이 Import 형식을 기준으로 한다고 자동으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-189">MEF will automatically assume the contract to be based on the type of the import unless you specify it explicitly.)</span></span>

<span data-ttu-id="fcbf4-190">아래의 매우 간단한 인터페이스를 모듈 또는 `SimpleCalculator` 네임스페이스에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-190">Add this very simple interface to the module or `SimpleCalculator` namespace:</span></span>

```vb
Public Interface ICalculator
    Function Calculate(input As String) As String
End Interface
```

```csharp
public interface ICalculator
{
    String Calculate(String input);
}
```

<span data-ttu-id="fcbf4-191">`ICalculator`를 정의한 후에는 이 형식을 구현하는 클래스를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-191">Now that you have defined `ICalculator`, you need a class that implements it.</span></span> <span data-ttu-id="fcbf4-192">모듈 또는 `SimpleCalculator` 네임스페이스에 다음 클래스를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-192">Add the following class to the module or `SimpleCalculator` namespace:</span></span>

```vb
<Export(GetType(ICalculator))>
Public Class MySimpleCalculator
   Implements ICalculator

End Class
```

```csharp
[Export(typeof(ICalculator))]
class MySimpleCalculator : ICalculator
{

}
```

<span data-ttu-id="fcbf4-193">위의 코드에는 `Program`의 Import와 일치하는 Export가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-193">Here is the export that will match the import in `Program`.</span></span> <span data-ttu-id="fcbf4-194">Export와 Import가 일치하려면 Export에 동일한 계약이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-194">In order for the export to match the import, the export must have the same contract.</span></span> <span data-ttu-id="fcbf4-195">`typeof(MySimpleCalculator)` 기반 계약 하의 Export를 지정하는 경우 불일치가 발생하며 Import는 채워지지 않습니다. 계약은 정확히 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-195">Exporting under a contract based on `typeof(MySimpleCalculator)` would produce a mismatch, and the import would not be filled; the contract needs to match exactly.</span></span>

<span data-ttu-id="fcbf4-196">컴퍼지션 컨테이너는 이 어셈블리에서 사용 가능한 모든 파트로 채워지므로 `MySimpleCalculator` 파트를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-196">Since the composition container will be populated with all the parts available in this assembly, the `MySimpleCalculator` part will be available.</span></span> <span data-ttu-id="fcbf4-197">`Program`의 생성자가 `Program` 개체에 대해 컴퍼지션을 수행할 때 해당 Import는 해당 용도로 작성되는 `MySimpleCalculator` 개체로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-197">When the constructor for `Program` performs composition on the `Program` object, its import will be filled with a `MySimpleCalculator` object, which will be created for that purpose.</span></span>

<span data-ttu-id="fcbf4-198">사용자 인터페이스 계층(`Program`)은 다른 항목을 확인할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-198">The user interface layer (`Program`) does not need to know anything else.</span></span> <span data-ttu-id="fcbf4-199">따라서 `Main` 메서드에서 나머지 사용자 인터페이스 논리를 채울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-199">You can therefore fill in the rest of the user interface logic in the `Main` method.</span></span>

<span data-ttu-id="fcbf4-200">`Main` 메서드에 다음 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-200">Add the following code to the `Main` method:</span></span>

```vb
Sub Main()
    ' Composition is performed in the constructor.
    Dim p As New Program()
    Dim s As String
    Console.WriteLine("Enter Command:")
    While (True)
        s = Console.ReadLine()
        Console.WriteLine(p.calculator.Calculate(s))
    End While
End Sub
```

```csharp
static void Main(string[] args)
{
    // Composition is performed in the constructor.
    var p = new Program();
    string s;
    Console.WriteLine("Enter Command:");
    while (true)
    {
        s = Console.ReadLine();
        Console.WriteLine(p.calculator.Calculate(s));
    }
}
```

 <span data-ttu-id="fcbf4-201">이 코드는 단순히 입력 줄을 읽고 결과에서 `Calculate`의 `ICalculator` 함수를 호출하여 콘솔에 쓰기 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-201">This code simply reads a line of input and calls the `Calculate` function of `ICalculator` on the result, which it writes back to the console.</span></span> <span data-ttu-id="fcbf4-202">`Program`에서 필요한 코드는 이것뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-202">That is all the code you need in `Program`.</span></span> <span data-ttu-id="fcbf4-203">나머지 모든 작업은 파트에서 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-203">All the rest of the work will happen in the parts.</span></span>

## <a name="further-imports-and-importmany"></a><span data-ttu-id="fcbf4-204">추가 Import 및 ImportMany</span><span class="sxs-lookup"><span data-stu-id="fcbf4-204">Further Imports and ImportMany</span></span>

<span data-ttu-id="fcbf4-205">SimpleCalculator를 확장하려면 operations 목록을 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-205">In order for SimpleCalculator to be extensible, it needs to import a list of operations.</span></span> <span data-ttu-id="fcbf4-206">일반적인 <xref:System.ComponentModel.Composition.ImportAttribute> 특성은 <xref:System.ComponentModel.Composition.ExportAttribute> 하나만으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-206">An ordinary <xref:System.ComponentModel.Composition.ImportAttribute> attribute is filled by one and only one <xref:System.ComponentModel.Composition.ExportAttribute>.</span></span> <span data-ttu-id="fcbf4-207">이 클래스를 둘 이상 사용할 수 있는 경우에는 컴퍼지션 엔진에서 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-207">If more than one is available, the composition engine produces an error.</span></span> <span data-ttu-id="fcbf4-208">Export를 수에 관계없이 채울 수 있는 Import를 만들려는 경우에는 <xref:System.ComponentModel.Composition.ImportManyAttribute> 특성을 사용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-208">To create an import that can be filled by any number of exports, you can use the <xref:System.ComponentModel.Composition.ImportManyAttribute> attribute.</span></span>

<span data-ttu-id="fcbf4-209">`MySimpleCalculator` 클래스에 다음 operations 속성을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-209">Add the following operations property to the `MySimpleCalculator` class:</span></span>

```vb
<ImportMany()>
Public Property operations As IEnumerable(Of Lazy(Of IOperation, IOperationData))
```

```csharp
[ImportMany]
IEnumerable<Lazy<IOperation, IOperationData>> operations;
```

<span data-ttu-id="fcbf4-210"><xref:System.Lazy%602>는 Export에 대한 간접 참조를 저장할 수 있도록 MEF에서 제공하는 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-210"><xref:System.Lazy%602> is a type provided by MEF to hold indirect references to exports.</span></span> <span data-ttu-id="fcbf4-211">여기서는 내보낸 개체 자체뿐 아니라 내보낸 개체를 설명하는 정보인 ‘내보내기 메타데이터’도 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-211">Here, in addition to the exported object itself, you also get *export metadata*, or information that describes the exported object.</span></span> <span data-ttu-id="fcbf4-212">각 <xref:System.Lazy%602>는 실제 연산을 나타내는 `IOperation` 개체와 해당 메타데이터를 나타내는 `IOperationData` 개체를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-212">Each <xref:System.Lazy%602> contains an `IOperation` object, representing an actual operation, and an `IOperationData` object, representing its metadata.</span></span>

<span data-ttu-id="fcbf4-213">모듈 또는 `SimpleCalculator` 네임스페이스에 다음과 같은 간단한 인터페이스를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-213">Add the following simple interfaces to the module or `SimpleCalculator` namespace:</span></span>

```vb
Public Interface IOperation
    Function Operate(left As Integer, right As Integer) As Integer
End Interface

Public Interface IOperationData
    ReadOnly Property Symbol As Char
End Interface
```

```csharp
public interface IOperation
{
     int Operate(int left, int right);
}

public interface IOperationData
{
    Char Symbol { get; }
}
```

 <span data-ttu-id="fcbf4-214">여기서 각 연산의 메타데이터는 +, -, \* 등 해당 연산을 나타내는 기호입니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-214">In this case, the metadata for each operation is the symbol that represents that operation, such as +, -, \*, and so on.</span></span> <span data-ttu-id="fcbf4-215">추가 연산을 사용하려면 모듈 또는 `SimpleCalculator` 네임스페이스에 다음 클래스를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-215">To make the addition operation available, add the following class to the module or `SimpleCalculator` namespace:</span></span>

```vb
<Export(GetType(IOperation))>
<ExportMetadata("Symbol", "+"c)>
Public Class Add
    Implements IOperation

    Public Function Operate(left As Integer, right As Integer) As Integer Implements IOperation.Operate
        Return left + right
    End Function
End Class
```

```csharp
[Export(typeof(IOperation))]
[ExportMetadata("Symbol", '+')]
class Add: IOperation
{
    public int Operate(int left, int right)
    {
        return left + right;
    }
}
```

<span data-ttu-id="fcbf4-216"><xref:System.ComponentModel.Composition.ExportAttribute> 특성은 이전과 같이 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-216">The <xref:System.ComponentModel.Composition.ExportAttribute> attribute functions as it did before.</span></span> <span data-ttu-id="fcbf4-217"><xref:System.ComponentModel.Composition.ExportMetadataAttribute> 특성은 메타데이터를 해당 Export에 이름-값 쌍 형식으로 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-217">The <xref:System.ComponentModel.Composition.ExportMetadataAttribute> attribute attaches metadata, in the form of a name-value pair, to that export.</span></span> <span data-ttu-id="fcbf4-218">`Add` 클래스가 `IOperation`을 구현하는 동안에는 `IOperationData`를 구현하는 클래스가 명시적으로 정의되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-218">While the `Add` class implements `IOperation`, a class that implements `IOperationData` is not explicitly defined.</span></span> <span data-ttu-id="fcbf4-219">대신 제공된 메타데이터 이름을 기준으로 하는 속성을 사용하여 MEF에서 클래스를 암시적으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-219">Instead, a class is implicitly created by MEF with properties based on the names of the metadata provided.</span></span> <span data-ttu-id="fcbf4-220">이는 MEF에서 메타데이터에 액세스하는 여러 방법 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-220">(This is one of several ways to access metadata in MEF.)</span></span>

<span data-ttu-id="fcbf4-221">MEF에서 컴퍼지션은 ‘재귀’ 방식으로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-221">Composition in MEF is *recursive*.</span></span> <span data-ttu-id="fcbf4-222">즉, 명시적으로 구성한 `Program` 개체가 `ICalculator` 형식으로 확인된 `MySimpleCalculator`를 가져왔습니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-222">You explicitly composed the `Program` object, which imported an `ICalculator` that turned out to be of type `MySimpleCalculator`.</span></span> <span data-ttu-id="fcbf4-223">`MySimpleCalculator`는 `IOperation` 개체 컬렉션을 가져오며 해당 Import는 `MySimpleCalculator`를 만들 때 `Program`의 Import와 동시에 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-223">`MySimpleCalculator`, in turn, imports a collection of `IOperation` objects, and that import will be filled when `MySimpleCalculator` is created, at the same time as the imports of `Program`.</span></span> <span data-ttu-id="fcbf4-224">`Add` 클래스가 추가 Import를 선언한 경우에는 해당 Import도 채워지는 식으로 작업이 진행됩니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-224">If the `Add` class declared a further import, that too would have to be filled, and so on.</span></span> <span data-ttu-id="fcbf4-225">채워지지 않은 Import가 있으면 컴퍼지션 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-225">Any import left unfilled results in a composition error.</span></span> <span data-ttu-id="fcbf4-226">그러나 Import를 선택 사항으로 선언하거나 Import에 기본값을 할당할 수는 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-226">(It is possible, however, to declare imports to be optional or to assign them default values.)</span></span>

## <a name="calculator-logic"></a><span data-ttu-id="fcbf4-227">계산기 논리</span><span class="sxs-lookup"><span data-stu-id="fcbf4-227">Calculator Logic</span></span>

<span data-ttu-id="fcbf4-228">이러한 파트를 배치한 후에는 계산기 논리 자체만 추가하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-228">With these parts in place, all that remains is the calculator logic itself.</span></span> <span data-ttu-id="fcbf4-229">`MySimpleCalculator` 클래스에 다음 코드를 추가하여 `Calculate` 메서드를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-229">Add the following code in the `MySimpleCalculator` class to implement the `Calculate` method:</span></span>

```vb
Public Function Calculate(input As String) As String Implements ICalculator.Calculate
    Dim left, right As Integer
    Dim operation As Char
    ' Finds the operator.
    Dim fn = FindFirstNonDigit(input)
    If fn < 0 Then
        Return "Could not parse command."
    End If
    operation = input(fn)
    Try
        ' Separate out the operands.
        left = Integer.Parse(input.Substring(0, fn))
        right = Integer.Parse(input.Substring(fn + 1))
    Catch ex As Exception
        Return "Could not parse command."
    End Try
    For Each i As Lazy(Of IOperation, IOperationData) In operations
        If i.Metadata.symbol = operation Then
            Return i.Value.Operate(left, right).ToString()
        End If
    Next
    Return "Operation not found!"
End Function
```

```csharp
public String Calculate(string input)
{
    int left;
    int right;
    char operation;
    // Finds the operator.
    int fn = FindFirstNonDigit(input);
    if (fn < 0) return "Could not parse command.";

    try
    {
        // Separate out the operands.
        left = int.Parse(input.Substring(0, fn));
        right = int.Parse(input.Substring(fn + 1));
    }
    catch
    {
        return "Could not parse command.";
    }

    operation = input[fn];

    foreach (Lazy<IOperation, IOperationData> i in operations)
    {
        if (i.Metadata.Symbol.Equals(operation)) return i.Value.Operate(left, right).ToString();
    }
    return "Operation Not Found!";
}
```

<span data-ttu-id="fcbf4-230">초기 단계에서는 입력 문자열을 왼쪽 및 오른쪽 피연산자와 연산자 문자로 구문 분석합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-230">The initial steps parse the input string into left and right operands and an operator character.</span></span> <span data-ttu-id="fcbf4-231">`foreach` 루프에서는 `operations` 컬렉션의 모든 멤버를 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-231">In the `foreach` loop, every member of the `operations` collection is examined.</span></span> <span data-ttu-id="fcbf4-232">이러한 개체는 <xref:System.Lazy%602> 형식이며 <xref:System.Lazy%602.Metadata%2A> 속성과 <xref:System.Lazy%601.Value%2A> 속성을 각각 사용하여 해당 메타데이터 값과 내보낸 개체에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-232">These objects are of type <xref:System.Lazy%602>, and their metadata values and exported object can be accessed with the <xref:System.Lazy%602.Metadata%2A> property and the <xref:System.Lazy%601.Value%2A> property respectively.</span></span> <span data-ttu-id="fcbf4-233">여기서 `Symbol` 개체의 `IOperationData` 속성이 일치하는 것으로 확인되면 계산기는 `Operate` 개체의 `IOperation` 메서드를 호출하고 결과를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-233">In this case, if the `Symbol` property of the `IOperationData` object is discovered to be a match, the calculator calls the `Operate` method of the `IOperation` object and returns the result.</span></span>

<span data-ttu-id="fcbf4-234">계산기를 완성하려면 문자열에서 숫자가 아닌 첫 번째 문자의 위치를 반환하는 도우미 메서드도 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-234">To complete the calculator, you also need a helper method that returns the position of the first non-digit character in a string.</span></span> <span data-ttu-id="fcbf4-235">`MySimpleCalculator` 클래스에 다음 도우미 메서드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-235">Add the following helper method to the `MySimpleCalculator` class:</span></span>

```vb
Private Function FindFirstNonDigit(s As String) As Integer
    For i = 0 To s.Length - 1
        If Not Char.IsDigit(s(i)) Then Return i
    Next
    Return -1
End Function
```

```csharp
private int FindFirstNonDigit(string s)
{
    for (int i = 0; i < s.Length; i++)
    {
        if (!Char.IsDigit(s[i])) return i;
    }
    return -1;
}
```

<span data-ttu-id="fcbf4-236">이제 프로젝트를 컴파일하고 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-236">You should now be able to compile and run the project.</span></span> <span data-ttu-id="fcbf4-237">Visual Basic에서 `Public` 키워드를 `Module1`에 추가했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-237">In Visual Basic, make sure that you added the `Public` keyword to `Module1`.</span></span> <span data-ttu-id="fcbf4-238">콘솔 창에서 “5+3” 등의 더하기 연산을 입력하면 계산기가 결과를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-238">In the console window, type an addition operation, such as "5+3", and the calculator returns the results.</span></span> <span data-ttu-id="fcbf4-239">다른 연산자를 추가하면 “Operation Not Found!” 메시지가</span><span class="sxs-lookup"><span data-stu-id="fcbf4-239">Any other operator results in the "Operation Not Found!"</span></span> <span data-ttu-id="fcbf4-240">반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-240">message.</span></span>

## <a name="extending-simplecalculator-using-a-new-class"></a><span data-ttu-id="fcbf4-241">새 클래스를 사용하여 SimpleCalculator 확장</span><span class="sxs-lookup"><span data-stu-id="fcbf4-241">Extending SimpleCalculator using a new class</span></span>

<span data-ttu-id="fcbf4-242">계산기가 작동하면 새 연산을 쉽게 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-242">Now that the calculator works, adding a new operation is easy.</span></span> <span data-ttu-id="fcbf4-243">모듈 또는 `SimpleCalculator` 네임스페이스에 다음 클래스를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-243">Add the following class to the module or `SimpleCalculator` namespace:</span></span>

```vb
<Export(GetType(IOperation))>
<ExportMetadata("Symbol", "-"c)>
Public Class Subtract
    Implements IOperation

    Public Function Operate(left As Integer, right As Integer) As Integer Implements IOperation.Operate
        Return left - right
    End Function
End Class
```

```csharp
[Export(typeof(IOperation))]
[ExportMetadata("Symbol", '-')]
class Subtract : IOperation
{
    public int Operate(int left, int right)
    {
        return left - right;
    }
}
```

<span data-ttu-id="fcbf4-244">프로젝트를 컴파일하고 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-244">Compile and run the project.</span></span> <span data-ttu-id="fcbf4-245">"5-3"과 같은 빼기 연산을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-245">Type a subtraction operation, such as "5-3".</span></span> <span data-ttu-id="fcbf4-246">이제 계산기에서 더하기는 물론 빼기도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-246">The calculator now supports subtraction as well as addition.</span></span>

## <a name="extending-simplecalculator-using-a-new-assembly"></a><span data-ttu-id="fcbf4-247">새 어셈블리를 사용하여 SimpleCalculator 확장</span><span class="sxs-lookup"><span data-stu-id="fcbf4-247">Extending SimpleCalculator using a new assembly</span></span>

<span data-ttu-id="fcbf4-248">소스 코드에 클래스를 추가하는 것은 간단하지만 MEF는 애플리케이션 자체의 소스 외부에서 파트를 확인할 수 있는 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-248">Adding classes to the source code is simple enough, but MEF provides the ability to look outside an application’s own source for parts.</span></span> <span data-ttu-id="fcbf4-249">이 기능을 확인하려면 <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>를 추가하여 자체 어셈블리는 물론 디렉터리에서도 파트를 검색하도록 SimpleCalculator를 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-249">To demonstrate this, you will need to modify SimpleCalculator to search a directory, as well as its own assembly, for parts, by adding a <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>.</span></span>

<span data-ttu-id="fcbf4-250">`Extensions`라는 새 디렉터리를 SimpleCalculator 프로젝트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-250">Add a new directory named `Extensions` to the SimpleCalculator project.</span></span> <span data-ttu-id="fcbf4-251">솔루션 수준이 아닌 프로젝트 수준에 디렉터리를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-251">Make sure to add it at the project level, and not at the solution level.</span></span> <span data-ttu-id="fcbf4-252">`ExtendedOperations`라는 새 클래스 라이브러리 프로젝트를 솔루션에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-252">Then add a new Class Library project to the solution, named `ExtendedOperations`.</span></span> <span data-ttu-id="fcbf4-253">새 프로젝트가 별도의 어셈블리로 컴파일됩니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-253">The new project will compile into a separate assembly.</span></span>

<span data-ttu-id="fcbf4-254">ExtendedOperations 프로젝트에 대해 프로젝트 속성 디자이너를 열고 **컴파일** 또는 **빌드** 탭을 클릭합니다. **빌드 출력 경로** 또는 **출력 경로**가 SimpleCalculator 프로젝트 디렉터리의 Extensions 디렉터리( *..\SimpleCalculator\Extensions\\* )를 가리키도록 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-254">Open the Project Properties Designer for the ExtendedOperations project and click the **Compile** or **Build** tab. Change the **Build output path** or **Output path** to point to the Extensions directory in the SimpleCalculator project directory (*..\SimpleCalculator\Extensions\\*).</span></span>

 <span data-ttu-id="fcbf4-255">*Module1.vb* 또는 *Program.cs*에서 `Program` 생성자에 다음 줄을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-255">In *Module1.vb* or *Program.cs*, add the following line to the `Program` constructor:</span></span>

```vb
catalog.Catalogs.Add(New DirectoryCatalog("C:\SimpleCalculator\SimpleCalculator\Extensions"))
```

```csharp
catalog.Catalogs.Add(new DirectoryCatalog("C:\\SimpleCalculator\\SimpleCalculator\\Extensions"));
```

<span data-ttu-id="fcbf4-256">예제 경로를 Extensions 디렉터리의 경로로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-256">Replace the example path with the path to your Extensions directory.</span></span> <span data-ttu-id="fcbf4-257">이 경로는 디버깅용으로만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-257">(This absolute path is for debugging purposes only.</span></span> <span data-ttu-id="fcbf4-258">프로덕션 애플리케이션에서는 상대 경로를 사용합니다. 이제 <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>는 Extensions 디렉터리의 어셈블리에서 발견되는 파트를 컴퍼지션 컨테이너에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-258">In a production application, you would use a relative path.) The <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> will now add any parts found in any assemblies in the Extensions directory to the composition container.</span></span>

<span data-ttu-id="fcbf4-259">ExtendedOperations 프로젝트에서 SimpleCalculator 및 System.ComponentModel.Composition에 대한 참조를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-259">In the ExtendedOperations project, add references to SimpleCalculator and System.ComponentModel.Composition.</span></span> <span data-ttu-id="fcbf4-260">ExtendedOperations 클래스 파일에서 System.ComponentModel.Composition에 대해 `Imports` 또는 `using` 문을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-260">In the ExtendedOperations class file, add an `Imports` or a `using` statement for System.ComponentModel.Composition.</span></span> <span data-ttu-id="fcbf4-261">Visual Basic에서 SimpleCalculator에 대해 `Imports` 문도 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-261">In Visual Basic, also add an `Imports` statement for SimpleCalculator.</span></span> <span data-ttu-id="fcbf4-262">그런 다음 ExtendedOperations 클래스 파일에 다음 클래스를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-262">Then add the following class to the ExtendedOperations class file:</span></span>

```vb
<Export(GetType(SimpleCalculator.IOperation))>
<ExportMetadata("Symbol", "%"c)>
Public Class Modulo
    Implements IOperation

    Public Function Operate(left As Integer, right As Integer) As Integer Implements IOperation.Operate
        Return left Mod right
    End Function
End Class
```

```csharp
[Export(typeof(SimpleCalculator.IOperation))]
[ExportMetadata("Symbol", '%')]
public class Mod : SimpleCalculator.IOperation
{
    public int Operate(int left, int right)
    {
        return left % right;
    }
}
```

<span data-ttu-id="fcbf4-263">계약이 일치하려면 <xref:System.ComponentModel.Composition.ExportAttribute> 특성의 형식이 <xref:System.ComponentModel.Composition.ImportAttribute>와 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-263">Note that in order for the contract to match, the <xref:System.ComponentModel.Composition.ExportAttribute> attribute must have the same type as the <xref:System.ComponentModel.Composition.ImportAttribute>.</span></span>

<span data-ttu-id="fcbf4-264">프로젝트를 컴파일하고 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-264">Compile and run the project.</span></span> <span data-ttu-id="fcbf4-265">새 Mod(%) 연산자를 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-265">Test the new Mod (%) operator.</span></span>

## <a name="conclusion"></a><span data-ttu-id="fcbf4-266">결론</span><span class="sxs-lookup"><span data-stu-id="fcbf4-266">Conclusion</span></span>

<span data-ttu-id="fcbf4-267">이 항목에서는 MEF의 기본 개념에 대해 설명했습니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-267">This topic covered the basic concepts of MEF.</span></span>

- <span data-ttu-id="fcbf4-268">파트, 카탈로그 및 컴퍼지션 컨테이너</span><span class="sxs-lookup"><span data-stu-id="fcbf4-268">Parts, catalogs, and the composition container</span></span>

     <span data-ttu-id="fcbf4-269">파트와 컴퍼지션은 MEF 애플리케이션의 기본 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-269">Parts and the composition container are the basic building blocks of a MEF application.</span></span> <span data-ttu-id="fcbf4-270">파트는 값을 가져오거나 내보내는 모든 개체(자기 자신 포함)입니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-270">A part is any object that imports or exports a value, up to and including itself.</span></span> <span data-ttu-id="fcbf4-271">카탈로그는 특정 소스의 파트 컬렉션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-271">A catalog provides a collection of parts from a particular source.</span></span> <span data-ttu-id="fcbf4-272">컴퍼지션 컨테이너는 카탈로그에서 제공하는 파트를 사용하여 컴퍼지션(Import와 Export의 바인딩)을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-272">The composition container uses the parts provided by a catalog to perform composition, the binding of imports to exports.</span></span>

- <span data-ttu-id="fcbf4-273">Import 및 Export</span><span class="sxs-lookup"><span data-stu-id="fcbf4-273">Imports and exports</span></span>

     <span data-ttu-id="fcbf4-274">구성 요소는 Import와 Export를 사용하여 통신합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-274">Imports and exports are the way by which components communicate.</span></span> <span data-ttu-id="fcbf4-275">구성 요소는 Import를 통해 특정 값이나 개체의 요구 사항을 지정하고 Export를 통해 값 사용 가능 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-275">With an import, the component specifies a need for a particular value or object, and with an export it specifies the availability of a value.</span></span> <span data-ttu-id="fcbf4-276">계약을 통해 Export 목록에서 각 Import와 일치하는 항목을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-276">Each import is matched with a list of exports by way of its contract.</span></span>

## <a name="next-steps"></a><span data-ttu-id="fcbf4-277">다음 단계</span><span class="sxs-lookup"><span data-stu-id="fcbf4-277">Next steps</span></span>

<span data-ttu-id="fcbf4-278">이 예제의 전체 코드를 다운로드하려면 [SimpleCalculator sample (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/simple-calculator-vb/)(SimpleCalculator 샘플(Visual Basic))을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-278">To download the complete code for this example, see the [SimpleCalculator sample (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/simple-calculator-vb/).</span></span>

 <span data-ttu-id="fcbf4-279">코드 예제에 대한 자세한 내용은 [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-279">For more information and code examples, see [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef).</span></span> <span data-ttu-id="fcbf4-280">MEF 형식 목록은 <xref:System.ComponentModel.Composition?displayProperty=nameWithType> 네임스페이스를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fcbf4-280">For a list of the MEF types, see the <xref:System.ComponentModel.Composition?displayProperty=nameWithType> namespace.</span></span>
