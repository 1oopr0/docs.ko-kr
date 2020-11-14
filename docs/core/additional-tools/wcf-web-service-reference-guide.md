---
title: WCF Web Service 참조 추가
description: .NET Framework 프로젝트용 서비스 참조 추가와 유사하게, .NET Core 및 ASP.NET Core 프로젝트 기능을 추가하는 Microsoft WCF Web Service Reference Provider 도구에 대한 개요입니다.
author: dasetser
ms.date: 10/29/2019
ms.custom: mvc
ms.openlocfilehash: 1f7b1831a956553dbef26f58f4f257c2f3914ede
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400606"
---
# <a name="use-the-wcf-web-service-reference-provider-tool"></a><span data-ttu-id="1f234-103">WCF Web Service Reference Provider 도구 사용</span><span class="sxs-lookup"><span data-stu-id="1f234-103">Use the WCF Web Service Reference Provider Tool</span></span>

<span data-ttu-id="1f234-104">지난 몇 년 동안, 많은 Visual Studio 개발자가 .NET Framework 프로젝트에서 웹 서비스에 액세스해야 할 때 제공된 [**서비스 참조 추가**](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) 도구를 통해 생산성을 향상시킬 수 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="1f234-104">Over the years, many Visual Studio developers have enjoyed the productivity that the [**Add Service Reference**](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) tool provided when their .NET Framework projects needed to access web services.</span></span>  <span data-ttu-id="1f234-105">**WCF Web Service Reference** 도구는 .NET Core 및 ASP.NET Core 프로젝트에 대한 서비스 참조 추가 기능과 같은 환경을 제공하는 Visual Studio 연결된 서비스 확장입니다.</span><span class="sxs-lookup"><span data-stu-id="1f234-105">The **WCF Web Service Reference** tool is a Visual Studio connected service extension that provides an experience like the Add Service Reference functionality for .NET Core and ASP.NET Core projects.</span></span> <span data-ttu-id="1f234-106">이 도구는 현재 솔루션, 네트워크 위치 또는 WSDL 파일의 웹 서비스에서 메타 데이터를 검색하고, 해당 웹 서비스를 액세스하는 데 사용할 수 있는 WCF(Windows Communication Foundation) 클라이언트 프록시 코드가 포함된 .NET Core 호환 소스 파일을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="1f234-106">This tool retrieves metadata from a web service in the current solution, on a network location, or from a WSDL file, and generates a .NET Core compatible source file containing Windows Communication Foundation (WCF) client proxy code that you can use to access the web service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1f234-107">신뢰할 수 있는 원본의 서비스만 참조해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f234-107">You should only reference services from a trusted source.</span></span> <span data-ttu-id="1f234-108">신뢰할 수 없는 원본에서 참조를 추가하면 보안이 손상될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f234-108">Adding references from an untrusted source may compromise security.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1f234-109">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="1f234-109">Prerequisites</span></span>

- <span data-ttu-id="1f234-110">[Visual Studio 2017 버전 15.5](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) 이상 버전</span><span class="sxs-lookup"><span data-stu-id="1f234-110">[Visual Studio 2017 version 15.5](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) or later versions</span></span>

## <a name="how-to-use-the-extension"></a><span data-ttu-id="1f234-111">확장을 사용하는 방법</span><span class="sxs-lookup"><span data-stu-id="1f234-111">How to use the extension</span></span>

> [!NOTE]
> <span data-ttu-id="1f234-112">**WCF Web Service Reference** 옵션은 다음과 같은 프로젝트 템플릿을 사용하여 만든 프로젝트에 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f234-112">The **WCF Web Service Reference** option is applicable to projects created using the following project templates:</span></span>
>
> - <span data-ttu-id="1f234-113">**Visual C#**  >  **.NET Core**</span><span class="sxs-lookup"><span data-stu-id="1f234-113">**Visual C#** > **.NET Core**</span></span>
> - <span data-ttu-id="1f234-114">**Visual C#**  >  **.NET Standard**</span><span class="sxs-lookup"><span data-stu-id="1f234-114">**Visual C#** > **.NET Standard**</span></span>
> - <span data-ttu-id="1f234-115">**Visual C#**  > **Web** > **ASP.NET Core Web Application**</span><span class="sxs-lookup"><span data-stu-id="1f234-115">**Visual C#** > **Web** > **ASP.NET Core Web Application**</span></span>

<span data-ttu-id="1f234-116">이 문서에서는 **ASP.NET Core 웹 애플리케이션** 프로젝트 템플릿을 예로 사용하여 WCF 서비스 참조를 프로젝트에 추가하는 과정을 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="1f234-116">Using the **ASP.NET Core Web Application** project template as an example, this article walks you through adding a WCF service reference to the project:</span></span>

1. <span data-ttu-id="1f234-117">솔루션 탐색기에서 프로젝트의 **연결된 서비스** 노드를 두 번 클릭합니다(.NET Core 또는 .NET Standard 프로젝트의 경우 이 옵션은 솔루션 탐색기에서 프로젝트의 **종속성** 노드를 마우스 오른쪽 단추로 클릭할 때 사용 가능함).</span><span class="sxs-lookup"><span data-stu-id="1f234-117">In Solution Explorer, double-click the **Connected Services** node of the project (for a .NET Core or .NET Standard project this option is available when you right-click on the **Dependencies** node of the project in Solution Explorer).</span></span>

    <span data-ttu-id="1f234-118">다음 이미지와 같이 **연결된 서비스** 페이지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f234-118">The **Connected Services** page appears as shown in the following image:</span></span>

    ![.NET Core용 Visual Studio 연결된 서비스 탭](./media/wcf-web-service-reference-guide/wcfcs-ConnectedServicesPage.png)

2. <span data-ttu-id="1f234-120">**연결된 서비스** 페이지에서 **Microsoft WCF Web Service Reference Provider** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1f234-120">On the **Connected Services** page, click **Microsoft WCF Web Service Reference Provider**.</span></span> <span data-ttu-id="1f234-121">그러면 **WCF Web Service Reference 구성** 마법사가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="1f234-121">This brings up the **Configure WCF Web Service Reference** wizard:</span></span>

    ![.NET Core용 Visual Studio 서비스 엔드포인트 탭](./media/wcf-web-service-reference-guide/wcfcs-ServiceEndpointPage.png)

3. <span data-ttu-id="1f234-123">서비스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1f234-123">Select a service.</span></span>

    <span data-ttu-id="1f234-124">3a.</span><span class="sxs-lookup"><span data-stu-id="1f234-124">3a.</span></span> <span data-ttu-id="1f234-125">**WCF Web Service Reference 구성** 마법사 내에서 사용 가능한 여러 서비스 검색 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f234-125">There are several services search options available within the **Configure WCF Web Service Reference** wizard:</span></span>

     * <span data-ttu-id="1f234-126">현재 솔루션에 정의된 서비스를 검색하려면 **검색** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1f234-126">To search for services defined in the current solution, click the **Discover** button.</span></span>
     * <span data-ttu-id="1f234-127">지정된 주소에서 호스트되는 서비스를 검색하려면 **주소** 상자에 서비스 URL을 입력하고 **이동** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1f234-127">To search for services hosted at a specified address, enter a service URL in the **Address** box and click the **Go** button.</span></span>
     * <span data-ttu-id="1f234-128">웹 서비스 메타데이터 정보를 포함하는 WSDL 파일을 선택하려 **찾아보기** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1f234-128">To select a WSDL file that contains the web service metadata information, click the **Browse** button.</span></span>

    <span data-ttu-id="1f234-129">3b.</span><span class="sxs-lookup"><span data-stu-id="1f234-129">3b.</span></span> <span data-ttu-id="1f234-130">**서비스** 상자의 검색 결과 목록에서 서비스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1f234-130">Select the service from the search results list in the **Services** box.</span></span> <span data-ttu-id="1f234-131">필요한 경우 해당 **네임스페이스** 입력란에 생성된 코드에 대한 네임스페이스를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1f234-131">If needed, enter the namespace for the generated code in the corresponding **Namespace** text box.</span></span>

    <span data-ttu-id="1f234-132">3c.</span><span class="sxs-lookup"><span data-stu-id="1f234-132">3c.</span></span> <span data-ttu-id="1f234-133">**다음** 단추를 클릭하면 **데이터 형식 옵션** 및 **클라이언트 옵션** 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="1f234-133">Click the **Next** button to open the **Data Type Options** and the **Client Options** pages.</span></span> <span data-ttu-id="1f234-134">또는 **마침** 단추를 클릭하고 기본 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1f234-134">Alternatively, click the **Finish** button to use the default options.</span></span>

4. <span data-ttu-id="1f234-135">**데이터 형식 옵션** 양식을 사용하여 생성된 서비스 참조 구성 설정을 구체화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f234-135">The **Data Type Options** form enables you to refine the generated service reference configuration settings:</span></span>

    ![.NET Core용 Visual Studio 데이터 형식 옵션 탭](./media/wcf-web-service-reference-guide/wcfcs-DataTypesPage.png)

    > [!NOTE]
    > <span data-ttu-id="1f234-137">**참조된 어셈블리의 형식 재사용** 확인란 옵션은 서비스 참조 코드 생성에 필요한 데이터 형식이 프로젝트의 참조 어셈블리 중 하나에 정의될 때 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="1f234-137">The **Reuse types in referenced assemblies** check box option is useful when data types needed for service reference code generation are defined in one of your project's referenced assemblies.</span></span>  <span data-ttu-id="1f234-138">컴파일 시간 형식 충돌 또는 런타임 문제를 피하기 위해 기존 데이터 형식을 다시 사용하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="1f234-138">It's important to reuse those existing data types to avoid compile-time type clash or runtime issues.</span></span>

    <span data-ttu-id="1f234-139">프로젝트 종속성 및 기타 시스템 성능 요소의 수에 따라 형식 정보가 로드되는 동안 지연이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f234-139">There may be a delay while type information is loaded, depending on the number of project dependencies and other system performance factors.</span></span> <span data-ttu-id="1f234-140">**참조된 어셈블리의 형식 재사용** 확인란을 선택 하면 로드 중에 **마침** 단추가 비활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f234-140">The **Finish** button is disabled during loading unless the **Reuse types in referenced assemblies** check box is unchecked.</span></span>

5. <span data-ttu-id="1f234-141">완료했으면 **마침** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1f234-141">Click **Finish** when you are done.</span></span>

<span data-ttu-id="1f234-142">진행률을 표시하면서 도구가 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="1f234-142">While displaying progress, the tool:</span></span>

- <span data-ttu-id="1f234-143">WCF 서비스에서 메타데이터를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="1f234-143">Downloads metadata from the WCF service.</span></span>
- <span data-ttu-id="1f234-144">*reference.cs* 라는 파일에 서비스 참조 코드를 생성하고 **연결된 서비스** 노드 아래의 프로젝트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="1f234-144">Generates the service reference code in a file named *reference.cs* , and adds it to your project under the **Connected Services** node.</span></span>
- <span data-ttu-id="1f234-145">대상 플랫폼에서 컴파일 및 실행하는 데 필요한 NuGet 패키지 참조로 프로젝트 파일(.csproj)을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="1f234-145">Updates the project file (.csproj) with NuGet package references required to compile and run on the target platform.</span></span>

![Visual Studio 진행률 창](./media/wcf-web-service-reference-guide/wcfcs-ProgressWindow.png)

<span data-ttu-id="1f234-147">이러한 과정을 완료하면 생성된 WCF 클라이언트 형식의 인스턴스를 만들고 서비스 작업을 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f234-147">When these processes complete, you can create an instance of the generated WCF client type and invoke the service operations.</span></span>

## <a name="see-also"></a><span data-ttu-id="1f234-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1f234-148">See also</span></span>

- [<span data-ttu-id="1f234-149">Windows Communication Foundation 애플리케이션 시작하기</span><span class="sxs-lookup"><span data-stu-id="1f234-149">Get started with Windows Communication Foundation applications</span></span>](../../framework/wcf/getting-started-tutorial.md)
- [<span data-ttu-id="1f234-150">Windows Communication Foundation 서비스 및 Visual Studio의 WCF.NET 데이터 서비스</span><span class="sxs-lookup"><span data-stu-id="1f234-150">Windows Communication Foundation services and WCF data services in Visual Studio</span></span>](/visualstudio/data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio)
- [<span data-ttu-id="1f234-151">.NET Core의 WCF 지원 기능</span><span class="sxs-lookup"><span data-stu-id="1f234-151">WCF supported features on .NET Core</span></span>](https://github.com/dotnet/wcf/blob/master/release-notes/SupportedFeatures-v2.1.0.md)

## <a name="feedback--questions"></a><span data-ttu-id="1f234-152">사용자 의견 및 질문</span><span class="sxs-lookup"><span data-stu-id="1f234-152">Feedback & questions</span></span>

<span data-ttu-id="1f234-153">제품 피드백이 있는 경우 [문제 보고](/visualstudio/ide/how-to-report-a-problem-with-visual-studio) 도구를 사용하여 [개발자 커뮤니티](https://aka.ms/feedback/report?space=61)에 보고하세요.</span><span class="sxs-lookup"><span data-stu-id="1f234-153">If you have any product feedback, report it at [Developer Community](https://aka.ms/feedback/report?space=61) using the [Report a problem](/visualstudio/ide/how-to-report-a-problem-with-visual-studio) tool.</span></span>

## <a name="release-notes"></a><span data-ttu-id="1f234-154">릴리스 정보</span><span class="sxs-lookup"><span data-stu-id="1f234-154">Release notes</span></span>

- <span data-ttu-id="1f234-155">알려진 문제를 비롯한 업데이트된 릴리스 정보는 [릴리스 정보](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1f234-155">Refer to the [Release notes](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md) for updated release information, including known issues.</span></span>
