---
title: 앱에 대 한 프로젝트 구조 Blazor
description: ASP.NET Web Forms 및 프로젝트의 프로젝트 구조를 비교 하는 방법을 알아봅니다 Blazor .
author: danroth27
ms.author: daroth
no-loc:
- Blazor
- WebAssembly
ms.date: 09/11/2019
ms.openlocfilehash: 473b708a9b58fa88844bc6f79a898943d5a7db71
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173044"
---
# <a name="project-structure-for-blazor-apps"></a><span data-ttu-id="31367-103">앱에 대 한 프로젝트 구조 Blazor</span><span class="sxs-lookup"><span data-stu-id="31367-103">Project structure for Blazor apps</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="31367-104">중요 한 프로젝트 구조 차이에도 불구 하 고 ASP.NET Web Forms 하 고 Blazor 다양 한 개념을 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="31367-104">Despite their significant project structure differences, ASP.NET Web Forms and Blazor share many similar concepts.</span></span> <span data-ttu-id="31367-105">여기서는 프로젝트의 구조를 살펴보고 Blazor ASP.NET Web Forms 프로젝트와 비교 합니다.</span><span class="sxs-lookup"><span data-stu-id="31367-105">Here, we'll look at the structure of a Blazor project and compare it to an ASP.NET Web Forms project.</span></span>

<span data-ttu-id="31367-106">첫 번째 앱을 만들려면 Blazor [ Blazor 시작 단계의](/aspnet/core/blazor/get-started)지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="31367-106">To create your first Blazor app, follow the instructions in the [Blazor getting started steps](/aspnet/core/blazor/get-started).</span></span> <span data-ttu-id="31367-107">지침에 따라 Blazor 서버 앱 또는 Blazor WebAssembly ASP.NET Core에서 호스트 되는 앱을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31367-107">You can follow the instructions to create either a Blazor Server app or a Blazor WebAssembly app hosted in ASP.NET Core.</span></span> <span data-ttu-id="31367-108">호스팅 모델 관련 논리를 제외 하 고, 두 프로젝트의 대부분의 코드는 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="31367-108">Except for the hosting model-specific logic, most of the code in both projects is the same.</span></span>

## <a name="project-file"></a><span data-ttu-id="31367-109">프로젝트 파일</span><span class="sxs-lookup"><span data-stu-id="31367-109">Project file</span></span>

Blazor<span data-ttu-id="31367-110">서버 앱은 .NET Core 프로젝트입니다.</span><span class="sxs-lookup"><span data-stu-id="31367-110"> Server apps are .NET Core projects.</span></span> <span data-ttu-id="31367-111">서버 앱에 대 한 프로젝트 파일은 다음과 같이 간단 하 게 Blazor 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31367-111">The project file for the Blazor Server app is about as simple as it can get:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="31367-112">앱에 대 한 프로젝트 파일은 Blazor WebAssembly 약간 더 복잡 합니다. 정확한 버전 번호는 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31367-112">The project file for a Blazor WebAssembly app looks slightly more involved (exact version numbers may vary):</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
    <RazorLangVersion>3.0</RazorLangVersion>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.AspNetCore.Blazor" Version="3.1.0" />
    <PackageReference Include="Microsoft.AspNetCore.Blazor.Build" Version="3.1.0" PrivateAssets="all" />
    <PackageReference Include="Microsoft.AspNetCore.Blazor.HttpClient" Version="3.1.0" />
    <PackageReference Include="Microsoft.AspNetCore.Blazor.DevServer" Version="3.1.0" PrivateAssets="all" />
  </ItemGroup>

  <ItemGroup>
    <ProjectReference Include="..\Shared\BlazorWebAssemblyApp1.Shared.csproj" />
  </ItemGroup>

</Project>
```

Blazor<span data-ttu-id="31367-113">WebAssembly프로젝트는 기반 .net 런타임의 브라우저에서 실행 되므로 .Net Core 대신 .NET Standard를 대상 WebAssembly 으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="31367-113"> WebAssembly projects target .NET Standard instead of .NET Core because they run in the browser on a WebAssembly-based .NET runtime.</span></span> <span data-ttu-id="31367-114">서버 또는 개발자 컴퓨터에서 사용할 수 있는 것과 같은 방법으로 웹 브라우저에 .NET을 설치할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="31367-114">You can't install .NET into a web browser like you can on a server or developer machine.</span></span> <span data-ttu-id="31367-115">따라서 프로젝트는 Blazor 개별 패키지 참조를 사용 하 여 프레임 워크를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="31367-115">Consequently, the project references the Blazor framework using individual package references.</span></span>

<span data-ttu-id="31367-116">비교 하 여 기본 ASP.NET Web Forms 프로젝트에는 *.csproj* 파일에 거의 300 줄의 XML이 포함 되어 있으며, 대부분의 XML은 프로젝트의 다양 한 코드 및 콘텐츠 파일을 명시적으로 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="31367-116">By comparison, a default ASP.NET Web Forms project includes almost 300 lines of XML in its *.csproj* file, most of which is explicitly listing the various code and content files in the project.</span></span> <span data-ttu-id="31367-117">.NET Core 및 .NET Standard 기반 프로젝트의 많은 단순화는 sdk를 참조 하 여 가져온 기본 대상 및 속성에서 제공 됩니다 `Microsoft.NET.Sdk.Web` . 일반적으로 웹 sdk 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="31367-117">Many of the simplifications in the .NET Core- and .NET Standard-based projects come from the default targets and properties imported by referencing the `Microsoft.NET.Sdk.Web` SDK, often referred to as simply the Web SDK.</span></span> <span data-ttu-id="31367-118">웹 SDK에는 프로젝트에 코드 및 콘텐츠 파일의 포함을 간소화 하는 와일드 카드 및 기타 편리 하며 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31367-118">The Web SDK includes wildcards and other conveniences that simplify inclusion of code and content files in the project.</span></span> <span data-ttu-id="31367-119">파일을 명시적으로 나열할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="31367-119">You don't need to list the files explicitly.</span></span> <span data-ttu-id="31367-120">.NET Core를 대상으로 하는 경우 웹 SDK는 .NET Core 및 ASP.NET Core 공유 프레임 워크에 대 한 프레임 워크 참조도 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="31367-120">When targeting .NET Core, the Web SDK also adds framework references to both the .NET Core and ASP.NET Core shared frameworks.</span></span> <span data-ttu-id="31367-121">프레임 워크는 솔루션 탐색기 창의 **종속성**  >  **프레임 워크** 노드에서 볼 수 **Solution Explorer** 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31367-121">The frameworks are visible from the **Dependencies** > **Frameworks** node in the **Solution Explorer** window.</span></span> <span data-ttu-id="31367-122">공유 프레임 워크는 .NET Core를 설치할 때 컴퓨터에 설치 된 어셈블리의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="31367-122">The shared frameworks are collections of assemblies that were installed on the machine when installing .NET Core.</span></span>

<span data-ttu-id="31367-123">지원 되기는 하지만 개별 어셈블리 참조는 .NET Core 프로젝트에서 더 일반적이 지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="31367-123">Although they're supported, individual assembly references are less common in .NET Core projects.</span></span> <span data-ttu-id="31367-124">대부분의 프로젝트 종속성은 NuGet 패키지 참조로 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="31367-124">Most project dependencies are handled as NuGet package references.</span></span> <span data-ttu-id="31367-125">.NET Core 프로젝트에서 최상위 패키지 종속성을 참조 하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="31367-125">You only need to reference top-level package dependencies in .NET Core projects.</span></span> <span data-ttu-id="31367-126">전이적 종속성이 자동으로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="31367-126">Transitive dependencies are included automatically.</span></span> <span data-ttu-id="31367-127">ASP.NET Web Forms 프로젝트에서 일반적으로 발견 되는 *packages.config* 파일을 사용 하는 대신 패키지 참조는 요소를 사용 하 여 프로젝트 파일에 추가 됩니다 `<PackageReference>` .</span><span class="sxs-lookup"><span data-stu-id="31367-127">Instead of using the *packages.config* file commonly found in ASP.NET Web Forms projects to reference packages, package references are added to the project file using the `<PackageReference>` element.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

## <a name="entry-point"></a><span data-ttu-id="31367-128">진입점</span><span class="sxs-lookup"><span data-stu-id="31367-128">Entry point</span></span>

<span data-ttu-id="31367-129">Blazor서버 앱의 진입점은 콘솔 앱에서 볼 수 있는 것 처럼 *Program.cs* 파일에 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="31367-129">The Blazor Server app's entry point is defined in the *Program.cs* file, as you would see in a Console app.</span></span> <span data-ttu-id="31367-130">앱이 실행 되 면 웹 앱과 관련 된 기본값을 사용 하 여 웹 호스트 인스턴스를 만들고 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="31367-130">When the app executes, it creates and runs a web host instance using defaults specific to web apps.</span></span> <span data-ttu-id="31367-131">웹 호스트는 Blazor 서버 앱의 수명 주기를 관리 하 고 호스트 수준 서비스를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="31367-131">The web host manages the Blazor Server app's lifecycle and sets up host-level services.</span></span> <span data-ttu-id="31367-132">이러한 서비스의 예로는 구성, 로깅, 종속성 주입 및 HTTP 서버가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31367-132">Examples of such services are configuration, logging, dependency injection, and the HTTP server.</span></span> <span data-ttu-id="31367-133">이 코드는 대부분 상용구 이며 변경 되지 않은 상태로 유지 되는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="31367-133">This code is mostly boilerplate and is often left unchanged.</span></span>

```csharp
public class Program
{
    public static void Main(string[] args)
    {
        CreateHostBuilder(args).Build().Run();
    }

    public static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureWebHostDefaults(webBuilder =>
            {
                webBuilder.UseStartup<Startup>();
            });
}
```

Blazor<span data-ttu-id="31367-134">WebAssembly또한 앱은 *Program.cs*에서 진입점을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="31367-134"> WebAssembly apps also define an entry point in *Program.cs*.</span></span> <span data-ttu-id="31367-135">코드는 약간 다르게 보입니다.</span><span class="sxs-lookup"><span data-stu-id="31367-135">The code looks slightly different.</span></span> <span data-ttu-id="31367-136">코드는 앱 호스트를 설정 하 여 앱에 동일한 호스트 수준 서비스를 제공 한다는 점에서 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="31367-136">The code is similar in that it's setting up the app host to provide the same host-level services to the app.</span></span> <span data-ttu-id="31367-137">WebAssembly그러나 응용 프로그램 호스트는 브라우저에서 직접 실행 되므로 HTTP 서버를 설정 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="31367-137">The WebAssembly app host doesn't, however, set up an HTTP server because it executes directly in the browser.</span></span>

Blazor<span data-ttu-id="31367-138">앱에는 `Startup` 응용 프로그램에 대 한 시작 논리를 정의 하 *는 global.asax* 파일 대신 클래스가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31367-138"> apps have a `Startup` class instead of a *Global.asax* file to define the startup logic for the app.</span></span> <span data-ttu-id="31367-139">`Startup`클래스는 앱 및 앱 별 서비스를 구성 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="31367-139">The `Startup` class is used to configure the app and any app-specific services.</span></span> <span data-ttu-id="31367-140">Blazor서버 앱에서 `Startup` 클래스는 Blazor 클라이언트 브라우저와 서버 간에에서 사용 되는 실시간 연결에 대 한 끝점을 설정 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="31367-140">In the Blazor Server app, the `Startup` class is used to set up the endpoint for the real-time connection used by Blazor between the client browsers and the server.</span></span> <span data-ttu-id="31367-141">앱에서 Blazor WebAssembly `Startup` 클래스는 앱의 루트 구성 요소를 정의 하 고 렌더링 해야 하는 위치를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="31367-141">In the Blazor WebAssembly app, the `Startup` class defines the root components for the app and where they should be rendered.</span></span> <span data-ttu-id="31367-142">`Startup` [앱 시작](./app-startup.md) 섹션의 클래스를 자세히 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="31367-142">We'll take a deeper look at the `Startup` class in the [App startup](./app-startup.md) section.</span></span>

## <a name="static-files"></a><span data-ttu-id="31367-143">정적 파일</span><span class="sxs-lookup"><span data-stu-id="31367-143">Static files</span></span>

<span data-ttu-id="31367-144">ASP.NET Web Forms 프로젝트와 달리 프로젝트의 모든 파일을 Blazor 정적 파일로 요청할 수 있는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="31367-144">Unlike ASP.NET Web Forms projects, not all files in a Blazor project can be requested as static files.</span></span> <span data-ttu-id="31367-145">*Wwwroot* 폴더의 파일만 웹 주소 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31367-145">Only the files in the *wwwroot* folder are web-addressable.</span></span> <span data-ttu-id="31367-146">이 폴더는 앱의 "웹 루트" 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="31367-146">This folder is referred to the app's "web root".</span></span> <span data-ttu-id="31367-147">앱의 웹 루트 외부에 있는 모든 항목은 웹 주소 지정이 가능 *하지 않습니다* .</span><span class="sxs-lookup"><span data-stu-id="31367-147">Anything outside of the app's web root *isn't* web-addressable.</span></span> <span data-ttu-id="31367-148">이 설치 프로그램은 웹을 통해 프로젝트 파일이 실수로 노출 되는 것을 방지 하는 추가 보안 수준을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="31367-148">This setup provides an additional level of security that prevents accidental exposing of project files over the web.</span></span>

## <a name="configuration"></a><span data-ttu-id="31367-149">구성</span><span class="sxs-lookup"><span data-stu-id="31367-149">Configuration</span></span>

<span data-ttu-id="31367-150">ASP.NET Web Forms apps의 구성은 일반적으로 하나 이상의 *web.config* 파일을 사용 하 여 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="31367-150">Configuration in ASP.NET Web Forms apps is typically handled using one or more *web.config* files.</span></span> Blazor<span data-ttu-id="31367-151">앱은 일반적으로 *web.config* 파일을 포함 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="31367-151"> apps don't typically have *web.config* files.</span></span> <span data-ttu-id="31367-152">이 경우 IIS에서 호스팅되는 경우에만 파일이 IIS 관련 설정을 구성 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="31367-152">If they do, the file is only used to configure IIS-specific settings when hosted on IIS.</span></span> <span data-ttu-id="31367-153">대신, Blazor 서버 앱은 ASP.NET Core 구성 추상화를 사용 합니다 Blazor WebAssembly . 현재 앱은 동일한 구성 추상화를 지원 하지만 이후에 추가 된 기능 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31367-153">Instead, Blazor Server apps use the ASP.NET Core configuration abstractions (Blazor WebAssembly apps don't currently support the same configuration abstractions, but that may be a feature added in the future).</span></span> <span data-ttu-id="31367-154">예를 들어 기본 Blazor 서버 앱은 *appsettings.js*에 일부 설정을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="31367-154">For example, the default Blazor Server app stores some settings in *appsettings.json*.</span></span>

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft": "Warning",
      "Microsoft.Hosting.Lifetime": "Information"
    }
  },
  "AllowedHosts": "*"
}
```

<span data-ttu-id="31367-155">[구성 섹션에서](./config.md) ASP.NET Core 프로젝트의 구성에 대해 자세히 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="31367-155">We'll learn more about configuration in ASP.NET Core projects in the [Configuration](./config.md) section.</span></span>

## <a name="razor-components"></a><span data-ttu-id="31367-156">Razor 구성 요소</span><span class="sxs-lookup"><span data-stu-id="31367-156">Razor components</span></span>

<span data-ttu-id="31367-157">프로젝트에서 대부분의 파일 Blazor 은 *razor* 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="31367-157">Most files in Blazor projects are *.razor* files.</span></span> <span data-ttu-id="31367-158">Razor는 웹 UI를 동적으로 생성 하는 데 사용 되는 HTML 및 c #을 기반으로 하는 템플릿 언어입니다.</span><span class="sxs-lookup"><span data-stu-id="31367-158">Razor is a templating language based on HTML and C# that is used to dynamically generate web UI.</span></span> <span data-ttu-id="31367-159">*Razor* 파일은 앱의 UI를 구성 하는 구성 요소를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="31367-159">The *.razor* files define components that make up the UI of the app.</span></span> <span data-ttu-id="31367-160">대부분의 경우 구성 요소는 서버와 앱 모두에서 동일 Blazor Blazor WebAssembly 합니다.</span><span class="sxs-lookup"><span data-stu-id="31367-160">For the most part, the components are identical for both the Blazor Server and Blazor WebAssembly apps.</span></span> <span data-ttu-id="31367-161">의 구성 요소 Blazor 는 ASP.NET Web Forms의 사용자 컨트롤과 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="31367-161">Components in Blazor are analogous to user controls in ASP.NET Web Forms.</span></span>

<span data-ttu-id="31367-162">각 Razor 구성 요소 파일은 프로젝트가 빌드될 때 .NET 클래스로 컴파일됩니다.</span><span class="sxs-lookup"><span data-stu-id="31367-162">Each Razor component file is compiled into a .NET class when the project is built.</span></span> <span data-ttu-id="31367-163">생성 된 클래스는 구성 요소의 상태, 렌더링 논리, 수명 주기 메서드, 이벤트 처리기 및 기타 논리를 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="31367-163">The generated class captures the component's state, rendering logic, lifecycle methods, event handlers, and other logic.</span></span> <span data-ttu-id="31367-164">[다시 사용 Blazor 가능한 UI 구성 요소 빌드](./components.md) 섹션에서 구성 요소를 작성 하는 방법을 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="31367-164">We'll look at authoring components in the [Building reusable UI components with Blazor](./components.md) section.</span></span>

<span data-ttu-id="31367-165">*_Imports razor* 파일은 razor 구성 요소 파일이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="31367-165">The *_Imports.razor* files aren't Razor component files.</span></span> <span data-ttu-id="31367-166">대신, 동일한 폴더와 해당 하위 폴더에 있는 다른 *razor* 파일로 가져오기 위한 razor 지시문 집합을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="31367-166">Instead, they define a set of Razor directives to import into other *.razor* files within the same folder and in its subfolders.</span></span> <span data-ttu-id="31367-167">예를 들어 *_Imports razor* 파일은 `using` 일반적으로 사용 되는 네임 스페이스에 대 한 지시문을 추가 하는 일반적인 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="31367-167">For example, a *_Imports.razor* file is a conventional way to add `using` directives for commonly used namespaces:</span></span>

```razor
@using System.Net.Http
@using Microsoft.AspNetCore.Authorization
@using Microsoft.AspNetCore.Components.Authorization
@using Microsoft.AspNetCore.Components.Forms
@using Microsoft.AspNetCore.Components.Routing
@using Microsoft.AspNetCore.Components.Web
@using Microsoft.JSInterop
@using BlazorApp1
@using BlazorApp1.Shared
```

## <a name="pages"></a><span data-ttu-id="31367-168">페이지</span><span class="sxs-lookup"><span data-stu-id="31367-168">Pages</span></span>

<span data-ttu-id="31367-169">앱의 페이지는 어디에 Blazor 있나요?</span><span class="sxs-lookup"><span data-stu-id="31367-169">Where are the pages in the Blazor apps?</span></span> Blazor<span data-ttu-id="31367-170">ASP.NET Web Forms apps의 *.aspx* 파일과 같이 주소 지정 가능한 페이지에 대 한 별도의 파일 확장명을 정의 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="31367-170"> doesn't define a separate file extension for addressable pages, like the *.aspx* files in ASP.NET Web Forms apps.</span></span> <span data-ttu-id="31367-171">대신, 페이지는 구성 요소에 경로를 할당 하 여 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="31367-171">Instead, pages are defined by assigning routes to components.</span></span> <span data-ttu-id="31367-172">경로는 일반적으로 Razor 지시어를 사용 하 여 할당 됩니다 `@page` .</span><span class="sxs-lookup"><span data-stu-id="31367-172">A route is typically assigned using the `@page` Razor directive.</span></span> <span data-ttu-id="31367-173">예를 들어 `Counter` *Pages/Counter. razor* 파일에서 작성 된 구성 요소는 다음 경로를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="31367-173">For example, the `Counter` component authored in the *Pages/Counter.razor* file defines the following route:</span></span>

```razor
@page "/counter"
```

<span data-ttu-id="31367-174">에서 라우팅은 Blazor 서버가 아닌 클라이언트 쪽에서 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="31367-174">Routing in Blazor is handled client-side, not on the server.</span></span> <span data-ttu-id="31367-175">사용자가 브라우저에서 탐색할 때는 Blazor 탐색을 가로채 고 일치 하는 경로를 사용 하 여 구성 요소를 렌더링 합니다.</span><span class="sxs-lookup"><span data-stu-id="31367-175">As the user navigates in the browser, Blazor intercepts the navigation and then renders the component with the matching route.</span></span>

<span data-ttu-id="31367-176">현재 구성 요소 경로는 *.aspx* 페이지와 마찬가지로 구성 요소의 파일 위치에 의해 유추 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="31367-176">The component routes aren't currently inferred by the component's file location like they are with *.aspx* pages.</span></span> <span data-ttu-id="31367-177">이 기능은 나중에 추가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31367-177">This feature may be added in the future.</span></span> <span data-ttu-id="31367-178">각 경로는 구성 요소에서 명시적으로 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="31367-178">Each route must be specified explicitly on the component.</span></span> <span data-ttu-id="31367-179">라우팅할 수 있는 구성 요소를 *Pages* 폴더에 저장 하는 것은 특별 한 의미가 없으며 전적으로 규칙입니다.</span><span class="sxs-lookup"><span data-stu-id="31367-179">Storing routable components in a *Pages* folder has no special meaning and is purely a convention.</span></span>

<span data-ttu-id="31367-180">Blazor [페이지, 라우팅 및 레이아웃](./pages-routing-layouts.md) 섹션에서 라우팅하는 방법에 대해 더 자세히 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="31367-180">We'll look in greater detail at routing in Blazor in the [Pages, routing, and layouts](./pages-routing-layouts.md) section.</span></span>

## <a name="layout"></a><span data-ttu-id="31367-181">레이아웃</span><span class="sxs-lookup"><span data-stu-id="31367-181">Layout</span></span>

<span data-ttu-id="31367-182">ASP.NET Web Forms apps에서 일반 페이지 레이아웃은 마스터*페이지 (site.master*)를 사용 하 여 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="31367-182">In ASP.NET Web Forms apps, common page layout is handled using master pages (*Site.Master*).</span></span> <span data-ttu-id="31367-183">Blazor앱에서 페이지 레이아웃은 레이아웃 구성 요소 (*Shared/mainlayout. razor*)를 사용 하 여 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="31367-183">In Blazor apps, page layout is handled using layout components (*Shared/MainLayout.razor*).</span></span> <span data-ttu-id="31367-184">레이아웃 구성 요소는 [페이지, 라우팅 및 레이아웃](./pages-routing-layouts.md) 섹션에 자세히 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31367-184">Layout components will be discussed in more detail in [Page, routing, and layouts](./pages-routing-layouts.md) section.</span></span>

## <a name="bootstrap-blazor"></a><span data-ttu-id="31367-185">부트스트랩Blazor</span><span class="sxs-lookup"><span data-stu-id="31367-185">Bootstrap Blazor</span></span>

<span data-ttu-id="31367-186">부트스트랩 하려면 Blazor 앱에서 다음을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="31367-186">To bootstrap Blazor, the app must:</span></span>

- <span data-ttu-id="31367-187">페이지에서 루트 구성 요소 (*응용 프로그램 Razor*)를 렌더링 해야 하는 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="31367-187">Specify where on the page the root component (*App.Razor*) should be rendered.</span></span>
- <span data-ttu-id="31367-188">해당 Blazor 프레임 워크 스크립트를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="31367-188">Add the corresponding Blazor framework script.</span></span>

<span data-ttu-id="31367-189">Blazor서버 앱에서 루트 구성 요소의 호스트 페이지는 *_Host. cshtml* 파일에 정의 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31367-189">In the Blazor Server app, the root component's host page is defined in the *_Host.cshtml* file.</span></span> <span data-ttu-id="31367-190">이 파일은 구성 요소가 아닌 Razor 페이지를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="31367-190">This file defines a Razor Page, not a component.</span></span> <span data-ttu-id="31367-191">Razor Pages Razor 구문를 사용 하 여 .aspx 페이지와 매우 유사한 서버 주소 지정 가능 페이지를 정의 합니다 *.*</span><span class="sxs-lookup"><span data-stu-id="31367-191">Razor Pages use Razor syntax to define a server-addressable page, very much like an *.aspx* page.</span></span> <span data-ttu-id="31367-192">`Html.RenderComponentAsync<TComponent>(RenderMode)`메서드는 루트 수준 구성 요소를 렌더링 해야 하는 위치를 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="31367-192">The `Html.RenderComponentAsync<TComponent>(RenderMode)` method is used to define where a root-level component should be rendered.</span></span> <span data-ttu-id="31367-193">`RenderMode`옵션은 구성 요소가 렌더링 되는 방식을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="31367-193">The `RenderMode` option indicates the manner in which the component should be rendered.</span></span> <span data-ttu-id="31367-194">다음 표에서는 지원 되는 옵션을 간략하게 설명 합니다 `RenderMode` .</span><span class="sxs-lookup"><span data-stu-id="31367-194">The following table outlines the supported `RenderMode` options.</span></span>

|<span data-ttu-id="31367-195">옵션</span><span class="sxs-lookup"><span data-stu-id="31367-195">Option</span></span>                        |<span data-ttu-id="31367-196">설명</span><span class="sxs-lookup"><span data-stu-id="31367-196">Description</span></span>       |
|------------------------------|------------------|
|`RenderMode.Server`           |<span data-ttu-id="31367-197">브라우저와의 연결이 설정 되 면 대화형으로 렌더링 됨</span><span class="sxs-lookup"><span data-stu-id="31367-197">Rendered interactively once a connection with the browser is established</span></span>|
|`RenderMode.ServerPrerendered`|<span data-ttu-id="31367-198">첫 번째 미리 렌더링 된 대화형으로 렌더링</span><span class="sxs-lookup"><span data-stu-id="31367-198">First prerendered and then rendered interactively</span></span>|
|`RenderMode.Static`           |<span data-ttu-id="31367-199">정적 콘텐츠로 렌더링 됨</span><span class="sxs-lookup"><span data-stu-id="31367-199">Rendered as static content</span></span>|

<span data-ttu-id="31367-200">*_Framework/blazor.server.js* 에 대 한 스크립트 참조를 사용 하 여 서버와의 실시간 연결을 설정 하 고 모든 사용자 상호 작용 및 UI 업데이트를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="31367-200">The script reference to *_framework/blazor.server.js* establishes the real-time connection with the server and then deals with all user interactions and UI updates.</span></span>

```razor
@page "/"
@namespace BlazorApp1.Pages
@addTagHelper *, Microsoft.AspNetCore.Mvc.TagHelpers

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>BlazorApp1</title>
    <base href="~/" />
    <link rel="stylesheet" href="css/bootstrap/bootstrap.min.css" />
    <link href="css/site.css" rel="stylesheet" />
</head>
<body>
    <app>
        @(await Html.RenderComponentAsync<App>(RenderMode.ServerPrerendered))
    </app>

    <script src="_framework/blazor.server.js"></script>
</body>
</html>
```

<span data-ttu-id="31367-201">앱에서 Blazor WebAssembly 호스트 페이지는 *wwwroot/index.html*아래의 간단한 정적 HTML 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="31367-201">In the Blazor WebAssembly app, the host page is a simple static HTML file under *wwwroot/index.html*.</span></span> <span data-ttu-id="31367-202">`<app>`요소는 루트 구성 요소가 렌더링 되어야 하는 위치를 나타내는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="31367-202">The `<app>` element is used to indicate where the root component should be rendered.</span></span>

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width" />
    <title>BlazorApp2</title>
    <base href="/" />
    <link href="css/bootstrap/bootstrap.min.css" rel="stylesheet" />
    <link href="css/site.css" rel="stylesheet" />
</head>
<body>
    <app>Loading...</app>

    <script src="_framework/blazor.webassembly.js"></script>
</body>
</html>
```

<span data-ttu-id="31367-203">렌더링할 특정 구성 요소는 `Startup.Configure` 구성 요소가 렌더링 되어야 하는 위치를 나타내는 해당 CSS 선택기를 사용 하 여 앱의 메서드에서 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="31367-203">The specific component to render is configured in the app's `Startup.Configure` method with a corresponding CSS selector indicating where the component should be rendered.</span></span>

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
    }

    public void Configure(IComponentsApplicationBuilder app)
    {
        app.AddComponent<App>("app");
    }
}
```

## <a name="build-output"></a><span data-ttu-id="31367-204">빌드 출력</span><span class="sxs-lookup"><span data-stu-id="31367-204">Build output</span></span>

<span data-ttu-id="31367-205">프로젝트를 Blazor 빌드할 때 모든 Razor 구성 요소와 코드 파일은 단일 어셈블리로 컴파일됩니다.</span><span class="sxs-lookup"><span data-stu-id="31367-205">When a Blazor project is built, all Razor component and code files are compiled into a single assembly.</span></span> <span data-ttu-id="31367-206">ASP.NET Web Forms 프로젝트와 달리에서는 Blazor UI 논리의 런타임 컴파일을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="31367-206">Unlike ASP.NET Web Forms projects, Blazor doesn't support runtime compilation of the UI logic.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="31367-207">앱 실행</span><span class="sxs-lookup"><span data-stu-id="31367-207">Run the app</span></span>

<span data-ttu-id="31367-208">서버 앱을 실행 하려면 Blazor `F5` Visual Studio에서 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="31367-208">To run the Blazor Server app, press `F5` in Visual Studio.</span></span> Blazor<span data-ttu-id="31367-209">앱은 런타임 컴파일을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="31367-209"> apps don't support runtime compilation.</span></span> <span data-ttu-id="31367-210">코드 및 구성 요소 태그 변경의 결과를 확인 하려면 디버거가 연결 된 앱을 다시 빌드하고 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="31367-210">To see the results of code and component markup changes, rebuild and restart the app with the debugger attached.</span></span> <span data-ttu-id="31367-211">디버거를 연결 하지 않고 ()를 실행 하는 경우 `Ctrl+F5` Visual Studio는 파일 변경 내용을 감시 하 고 변경 내용이 적용 되 면 앱을 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="31367-211">If you run without the debugger attached (`Ctrl+F5`), Visual Studio watches for file changes and restarts the app as changes are made.</span></span> <span data-ttu-id="31367-212">변경 사항이 적용 되 면 브라우저를 수동으로 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="31367-212">You manually refresh the browser as changes are made.</span></span>

<span data-ttu-id="31367-213">앱을 실행 하려면 Blazor WebAssembly 다음 방법 중 하나를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="31367-213">To run the Blazor WebAssembly app, choose one of the following approaches:</span></span>

- <span data-ttu-id="31367-214">개발 서버를 사용 하 여 직접 클라이언트 프로젝트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="31367-214">Run the client project directly using the development server.</span></span>
- <span data-ttu-id="31367-215">ASP.NET Core를 사용 하 여 앱을 호스팅할 때 서버 프로젝트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="31367-215">Run the server project when hosting the app with ASP.NET Core.</span></span>

Blazor<span data-ttu-id="31367-216">WebAssembly앱은 Visual Studio를 사용 하 여 디버깅을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="31367-216"> WebAssembly apps don't support debugging using Visual Studio.</span></span> <span data-ttu-id="31367-217">앱을 실행 하려면 대신을 사용 `Ctrl+F5` `F5` 합니다.</span><span class="sxs-lookup"><span data-stu-id="31367-217">To run the app, use `Ctrl+F5` instead of `F5`.</span></span> <span data-ttu-id="31367-218">대신 Blazor WebAssembly 브라우저에서 직접 앱을 디버그할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31367-218">You can instead debug Blazor WebAssembly apps directly in the browser.</span></span> <span data-ttu-id="31367-219">자세한 내용은 [디버그 Blazor ASP.NET Core](/aspnet/core/blazor/debug) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="31367-219">See [Debug ASP.NET Core Blazor](/aspnet/core/blazor/debug) for details.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="31367-220">[이전](hosting-models.md)
>[다음](app-startup.md)</span><span class="sxs-lookup"><span data-stu-id="31367-220">[Previous](hosting-models.md)
[Next](app-startup.md)</span></span>
