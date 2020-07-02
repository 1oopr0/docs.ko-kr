---
title: 애플리케이션 개발
description: Windows Presentation Foundation (WPF) 프레임 워크를 사용 하 여 다양 한 응용 프로그램을 빌드하는 방법에 대해 알아봅니다.
ms.date: 01/26/2018
helpviewer_keywords:
- WPF [WPF], about application development
- application development [WPF], about
ms.assetid: 2996ce5e-81e9-49ae-881b-952db3dd1b7e
ms.openlocfilehash: ac4227785f2fc398217b3aa8984176844264bbaa
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85613737"
---
# <a name="application-development"></a><span data-ttu-id="dc9df-103">애플리케이션 개발</span><span class="sxs-lookup"><span data-stu-id="dc9df-103">Application Development</span></span>
<a name="introduction"></a><span data-ttu-id="dc9df-104">WPF (Windows Presentation Foundation)는 다음과 같은 종류의 응용 프로그램을 개발 하는 데 사용할 수 있는 프레젠테이션 프레임 워크입니다.</span><span class="sxs-lookup"><span data-stu-id="dc9df-104">Windows Presentation Foundation (WPF) is a presentation framework that can be used to develop the following types of applications:</span></span>  
  
- <span data-ttu-id="dc9df-105">독립 실행형 응용 프로그램 (클라이언트 컴퓨터에 설치 되 고 실행 되는 실행 가능 어셈블리로 빌드된 기존 스타일의 Windows 응용 프로그램).</span><span class="sxs-lookup"><span data-stu-id="dc9df-105">Standalone Applications (traditional style Windows applications built as executable assemblies that are installed to and run from the client computer).</span></span>  
  
- <span data-ttu-id="dc9df-106">Xbap (XAML 브라우저 응용 프로그램) (실행 가능 어셈블리로 빌드되고 Microsoft Internet Explorer 또는 Mozilla Firefox와 같은 웹 브라우저에서 호스트 되는 탐색 페이지로 구성 된 응용 프로그램)</span><span class="sxs-lookup"><span data-stu-id="dc9df-106">XAML browser applications (XBAPs) (applications composed of navigation pages that are built as executable assemblies and hosted by Web browsers such as Microsoft Internet Explorer or Mozilla Firefox).</span></span>  
  
- <span data-ttu-id="dc9df-107">사용자 지정 컨트롤 라이브러리(재사용 가능한 컨트롤을 포함하는 실행 불가능한 어셈블리)</span><span class="sxs-lookup"><span data-stu-id="dc9df-107">Custom Control Libraries (non-executable assemblies containing reusable controls).</span></span>  
  
- <span data-ttu-id="dc9df-108">클래스 라이브러리(재사용 가능한 클래스를 포함하는 실행 불가능한 어셈블리)</span><span class="sxs-lookup"><span data-stu-id="dc9df-108">Class Libraries (non-executable assemblies that contain reusable classes).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dc9df-109">Windows 서비스에서 WPF 유형을 사용해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc9df-109">Using WPF types in a Windows service is strongly discouraged.</span></span> <span data-ttu-id="dc9df-110">Windows 서비스에서 이러한 기능을 사용하려고 하면 예상대로 작동하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc9df-110">If you attempt to use these features in a Windows service, they may not work as expected.</span></span>  
  
 <span data-ttu-id="dc9df-111">WPF는 이러한 응용 프로그램 집합을 빌드하기 위해 서비스 호스트를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc9df-111">To build this set of applications, WPF implements a host of services.</span></span> <span data-ttu-id="dc9df-112">이 항목에서 이러한 서비스의 개요를 제공하며 자세한 정보를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc9df-112">This topic provides an overview of these services and where to find more information.</span></span>  

<a name="Application_Management"></a>
## <a name="application-management"></a><span data-ttu-id="dc9df-113">애플리케이션 관리</span><span class="sxs-lookup"><span data-stu-id="dc9df-113">Application Management</span></span>  
 <span data-ttu-id="dc9df-114">실행 가능한 WPF 응용 프로그램에는 일반적으로 다음을 포함 하는 핵심 기능 집합이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc9df-114">Executable WPF applications commonly require a core set of functionality that includes the following:</span></span>  
  
- <span data-ttu-id="dc9df-115">일반적인 애플리케이션 인프라 만들기 및 관리(시스템 및 입력 메시지를 수신하는 Windows 메시지 루프 및 진입점 메서드 만들기 포함)</span><span class="sxs-lookup"><span data-stu-id="dc9df-115">Creating and managing common application infrastructure (including creating an entry point method and a Windows message loop to receive system and input messages).</span></span>  
  
- <span data-ttu-id="dc9df-116">애플리케이션의 수명 추적 및 상호 작용</span><span class="sxs-lookup"><span data-stu-id="dc9df-116">Tracking and interacting with the lifetime of an application.</span></span>  
  
- <span data-ttu-id="dc9df-117">명령줄 매개 변수 검색 및 처리</span><span class="sxs-lookup"><span data-stu-id="dc9df-117">Retrieving and processing command-line parameters.</span></span>  
  
- <span data-ttu-id="dc9df-118">애플리케이션 범위 속성 및 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 리소스 공유</span><span class="sxs-lookup"><span data-stu-id="dc9df-118">Sharing application-scope properties and [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] resources.</span></span>  
  
- <span data-ttu-id="dc9df-119">처리되지 않은 예외 검색 및 처리</span><span class="sxs-lookup"><span data-stu-id="dc9df-119">Detecting and processing unhandled exceptions.</span></span>  
  
- <span data-ttu-id="dc9df-120">종료 코드 반환</span><span class="sxs-lookup"><span data-stu-id="dc9df-120">Returning exit codes.</span></span>  
  
- <span data-ttu-id="dc9df-121">독립 실행형 애플리케이션에서 창 관리</span><span class="sxs-lookup"><span data-stu-id="dc9df-121">Managing windows in standalone applications.</span></span>  
  
- <span data-ttu-id="dc9df-122">탐색 창과 프레임을 사용 하 여 Xbap (XAML 브라우저 응용 프로그램) 및 독립 실행형 응용 프로그램에서 탐색을 추적 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc9df-122">Tracking navigation in XAML browser applications (XBAPs), and standalone applications with navigation windows and frames.</span></span>  
  
 <span data-ttu-id="dc9df-123">이러한 기능은 *애플리케이션 정의*를 사용하여 애플리케이션에 추가되는 <xref:System.Windows.Application> 클래스에 의해 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc9df-123">These capabilities are implemented by the <xref:System.Windows.Application> class, which you add to your applications using an *application definition*.</span></span>  
  
 <span data-ttu-id="dc9df-124">자세한 내용은 [애플리케이션 관리 개요](application-management-overview.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dc9df-124">For more information, see [Application Management Overview](application-management-overview.md).</span></span>  
  
<a name="WPF_Application_Resource__Content__and_Data_Files"></a>
## <a name="wpf-application-resource-content-and-data-files"></a><span data-ttu-id="dc9df-125">WPF 애플리케이션 리소스, 콘텐츠 및 데이터 파일</span><span class="sxs-lookup"><span data-stu-id="dc9df-125">WPF Application Resource, Content, and Data Files</span></span>  
 <span data-ttu-id="dc9df-126">WPF는 리소스, 콘텐츠 및 데이터의 세 가지 종류의 비실행 데이터 파일에 대 한 지원을 포함 하는 포함 리소스에 대 한 Microsoft .NET Framework의 핵심 지원을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc9df-126">WPF extends the core support in the Microsoft .NET Framework for embedded resources with support for three kinds of non-executable data files: resource, content, and data.</span></span> <span data-ttu-id="dc9df-127">자세한 내용은 [WPF 애플리케이션 리소스, 콘텐츠 및 데이터 파일](wpf-application-resource-content-and-data-files.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dc9df-127">For more information, see [WPF Application Resource, Content, and Data Files](wpf-application-resource-content-and-data-files.md).</span></span>  
  
 <span data-ttu-id="dc9df-128">WPF 실행 불가능 데이터 파일에 대 한 지원의 핵심 구성 요소는 고유한 URI를 사용 하 여 해당 파일을 식별 하 고 로드 하는 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="dc9df-128">A key component of the support for WPF non-executable data files is the ability to identify and load them using a unique URI.</span></span> <span data-ttu-id="dc9df-129">자세한 내용은 [WPF의 Pack uri](pack-uris-in-wpf.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="dc9df-129">For more information, see [Pack URIs in WPF](pack-uris-in-wpf.md).</span></span>  
  
<a name="Windows_and_Dialog_Boxes"></a>
## <a name="windows-and-dialog-boxes"></a><span data-ttu-id="dc9df-130">창 및 대화 상자</span><span class="sxs-lookup"><span data-stu-id="dc9df-130">Windows and Dialog Boxes</span></span>  
 <span data-ttu-id="dc9df-131">사용자는 windows를 통해 WPF 독립 실행형 응용 프로그램과 상호 작용 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc9df-131">Users interact with WPF standalone applications through windows.</span></span> <span data-ttu-id="dc9df-132">창의 목적은 애플리케이션 콘텐츠를 호스트하고 일반적으로 사용자가 콘텐츠와 상호 작용할 수 있도록 애플리케이션 기능을 노출하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="dc9df-132">The purpose of a window is to host application content and expose application functionality that usually allows users to interact with the content.</span></span> <span data-ttu-id="dc9df-133">WPF에서 windows는 <xref:System.Windows.Window> 다음을 지 원하는 클래스에 캡슐화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc9df-133">In WPF, windows are encapsulated by the <xref:System.Windows.Window> class, which supports:</span></span>  
  
- <span data-ttu-id="dc9df-134">창 만들기 및 표시</span><span class="sxs-lookup"><span data-stu-id="dc9df-134">Creating and showing windows.</span></span>  
  
- <span data-ttu-id="dc9df-135">소유자/피소유자 창 관계 설정</span><span class="sxs-lookup"><span data-stu-id="dc9df-135">Establishing owner/owned window relationships.</span></span>  
  
- <span data-ttu-id="dc9df-136">창 모양 구성(예: 크기, 위치, 아이콘, 제목 표시줄 텍스트, 테두리)</span><span class="sxs-lookup"><span data-stu-id="dc9df-136">Configuring window appearance (for example, size, location, icons, title bar text, border).</span></span>  
  
- <span data-ttu-id="dc9df-137">창의 수명 추적 및 상호 작용</span><span class="sxs-lookup"><span data-stu-id="dc9df-137">Tracking and interacting with the lifetime of a window.</span></span>  
  
 <span data-ttu-id="dc9df-138">자세한 내용은 [WPF 창 개요](wpf-windows-overview.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dc9df-138">For more information, see [WPF Windows Overview](wpf-windows-overview.md).</span></span>  
  
 <span data-ttu-id="dc9df-139"><xref:System.Windows.Window>는 대화 상자로 알려진 특별한 유형의 창을 만드는 기능을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="dc9df-139"><xref:System.Windows.Window> supports the ability to create a special type of window known as a dialog box.</span></span> <span data-ttu-id="dc9df-140">모달 및 모덜리스 유형의 대화 상자를 모두 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc9df-140">Both modal and modeless types of dialog boxes can be created.</span></span>  
  
 <span data-ttu-id="dc9df-141">편의를 위해 응용 프로그램에 대 한 재사용 및 일관적인 사용자 환경의 이점 및 WPF는, 및의 세 가지 일반적인 창 대화 상자를 노출 합니다. <xref:Microsoft.Win32.OpenFileDialog> <xref:Microsoft.Win32.SaveFileDialog> <xref:System.Windows.Controls.PrintDialog></span><span class="sxs-lookup"><span data-stu-id="dc9df-141">For convenience, and the benefits of reusability and a consistent user experience across applications, WPF exposes three of the common Windows dialog boxes: <xref:Microsoft.Win32.OpenFileDialog>, <xref:Microsoft.Win32.SaveFileDialog>, and <xref:System.Windows.Controls.PrintDialog>.</span></span>  
  
 <span data-ttu-id="dc9df-142">메시지 상자는 중요한 텍스트 정보를 보여 주고 간단한 예/아니요/확인/취소 질문을 묻는 특별한 유형의 대화 상자입니다.</span><span class="sxs-lookup"><span data-stu-id="dc9df-142">A message box is a special type of dialog box for showing important textual information to users, and for asking simple Yes/No/OK/Cancel questions.</span></span> <span data-ttu-id="dc9df-143"><xref:System.Windows.MessageBox> 클래스를 사용하여 메시지 상자를 만들고 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="dc9df-143">You use the <xref:System.Windows.MessageBox> class to create and show message boxes.</span></span>  
  
 <span data-ttu-id="dc9df-144">자세한 내용은 [대화 상자 개요](dialog-boxes-overview.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dc9df-144">For more information, see [Dialog Boxes Overview](dialog-boxes-overview.md).</span></span>  
  
<a name="Navigation"></a>
## <a name="navigation"></a><span data-ttu-id="dc9df-145">탐색</span><span class="sxs-lookup"><span data-stu-id="dc9df-145">Navigation</span></span>  
 <span data-ttu-id="dc9df-146">WPF는 페이지 ( <xref:System.Windows.Controls.Page> ) 및 하이퍼링크 ()를 사용 하 여 웹 스타일 탐색을 지원 <xref:System.Windows.Documents.Hyperlink> 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc9df-146">WPF supports Web-style navigation using pages (<xref:System.Windows.Controls.Page>) and hyperlinks (<xref:System.Windows.Documents.Hyperlink>).</span></span> <span data-ttu-id="dc9df-147">다음을 포함한 다양한 방법으로 탐색을 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc9df-147">Navigation can be implemented in a variety of ways that include the following:</span></span>  
  
- <span data-ttu-id="dc9df-148">웹 브라우저에 호스트되는 독립 실행형 페이지</span><span class="sxs-lookup"><span data-stu-id="dc9df-148">Standalone pages that are hosted in a Web browser.</span></span>  
  
- <span data-ttu-id="dc9df-149">웹 브라우저에서 호스팅되는 XBAP로 컴파일되는 페이지입니다.</span><span class="sxs-lookup"><span data-stu-id="dc9df-149">Pages compiled into an XBAP that is hosted in a Web browser.</span></span>  
  
- <span data-ttu-id="dc9df-150">독립 실행형 애플리케이션으로 컴파일되고 탐색 창(<xref:System.Windows.Navigation.NavigationWindow>)에서 호스트하는 페이지</span><span class="sxs-lookup"><span data-stu-id="dc9df-150">Pages compiled into a standalone application and hosted by a navigation window (<xref:System.Windows.Navigation.NavigationWindow>).</span></span>  
  
- <span data-ttu-id="dc9df-151">독립 실행형 페이지에서 호스팅될 수 있는 프레임 ()에서 호스트 되는 페이지 <xref:System.Windows.Controls.Frame> 또는 XBAP 또는 독립 실행형 응용 프로그램으로 컴파일된 페이지.</span><span class="sxs-lookup"><span data-stu-id="dc9df-151">Pages that are hosted by a frame (<xref:System.Windows.Controls.Frame>), which may be hosted in a standalone page, or a page compiled into either an XBAP or a standalone application.</span></span>  
  
 <span data-ttu-id="dc9df-152">WPF는 탐색을 용이 하 게 하기 위해 다음을 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc9df-152">To facilitate navigation, WPF implements the following:</span></span>  
  
- <span data-ttu-id="dc9df-153"><xref:System.Windows.Navigation.NavigationService>, <xref:System.Windows.Controls.Frame> <xref:System.Windows.Navigation.NavigationWindow> 및 xbap에서 응용 프로그램 내 탐색을 지원 하기 위해 사용 하는 탐색 요청을 처리 하기 위한 공유 탐색 엔진입니다.</span><span class="sxs-lookup"><span data-stu-id="dc9df-153"><xref:System.Windows.Navigation.NavigationService>, the shared navigation engine for processing navigation requests that is used by <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow>, and XBAPs to support intra-application navigation.</span></span>  
  
- <span data-ttu-id="dc9df-154">탐색을 시작하는 탐색 메서드</span><span class="sxs-lookup"><span data-stu-id="dc9df-154">Navigation methods to initiate navigation.</span></span>  
  
- <span data-ttu-id="dc9df-155">탐색 수명을 추적하고 상호 작용하는 탐색 이벤트</span><span class="sxs-lookup"><span data-stu-id="dc9df-155">Navigation events to track and interact with navigation lifetime.</span></span>  
  
- <span data-ttu-id="dc9df-156">저널을 사용하여 뒤로/앞으로 탐색 저장(검사하고 조작할 수도 있음)</span><span class="sxs-lookup"><span data-stu-id="dc9df-156">Remembering back and forward navigation using a journal, which can also be inspected and manipulated.</span></span>  
  
 <span data-ttu-id="dc9df-157">자세한 내용은 [탐색 개요](navigation-overview.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dc9df-157">For information, see [Navigation Overview](navigation-overview.md).</span></span>  
  
 <span data-ttu-id="dc9df-158">WPF는 구조화 된 탐색 이라고 하는 특수 한 유형의 탐색도 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc9df-158">WPF also supports a special type of navigation known as structured navigation.</span></span> <span data-ttu-id="dc9df-159">구조적 탐색을 사용하여 호출 함수와 일치하는 구조적이고 예측 가능한 방식으로 데이터를 반환하는 하나 이상의 페이지를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc9df-159">Structured navigation can be used to call one or more pages that return data in a structured and predictable way that is consistent with calling functions.</span></span> <span data-ttu-id="dc9df-160">이 기능은 <xref:System.Windows.Navigation.PageFunction%601> 클래스에 따라 달라지며 [구조적 탐색 개요](structured-navigation-overview.md)에 자세히 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc9df-160">This capability depends on the <xref:System.Windows.Navigation.PageFunction%601> class, which is described further in [Structured Navigation Overview](structured-navigation-overview.md).</span></span> <span data-ttu-id="dc9df-161"><xref:System.Windows.Navigation.PageFunction%601>은 복잡한 탐색 토폴로지 생성을 간소화하는 역할도 합니다. 이러한 탐색 토폴로지에 대한 설명은 [탐색 토폴로지 개요](navigation-topologies-overview.md)에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc9df-161"><xref:System.Windows.Navigation.PageFunction%601> also serves to simplify the creation of complex navigation topologies, which are described in [Navigation Topologies Overview](navigation-topologies-overview.md).</span></span>  
  
<a name="Hosting"></a>
## <a name="hosting"></a><span data-ttu-id="dc9df-162">Hosting</span><span class="sxs-lookup"><span data-stu-id="dc9df-162">Hosting</span></span>  
 <span data-ttu-id="dc9df-163">Xbap는 Microsoft Internet Explorer 또는 Firefox에서 호스팅될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc9df-163">XBAPs can be hosted in Microsoft Internet Explorer or Firefox.</span></span> <span data-ttu-id="dc9df-164">각 호스팅 모델에는 [호스팅](hosting-wpf-applications.md)에서 다루는 고유한 고려 사항 및 제약 조건 집합이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc9df-164">Each hosting model has its own set of considerations and constraints that are covered in [Hosting](hosting-wpf-applications.md).</span></span>  
  
<a name="Build_and_Deploy"></a>
## <a name="build-and-deploy"></a><span data-ttu-id="dc9df-165">빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="dc9df-165">Build and Deploy</span></span>  
 <span data-ttu-id="dc9df-166">간단한 WPF 응용 프로그램은 명령줄 컴파일러를 사용 하 여 명령 프롬프트에서 빌드할 수 있지만 WPF는 Visual Studio와 통합 되어 개발 및 빌드 프로세스를 간소화 하는 추가 지원을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc9df-166">Although simple WPF applications can be built from a command prompt using command-line compilers, WPF integrates with Visual Studio to provide additional support that simplified the development and build process.</span></span> <span data-ttu-id="dc9df-167">자세한 내용은 [WPF 애플리케이션 빌드](building-a-wpf-application-wpf.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dc9df-167">For more information, see [Building a WPF Application](building-a-wpf-application-wpf.md).</span></span>  
  
 <span data-ttu-id="dc9df-168">빌드하는 애플리케이션의 유형에 따라 선택할 수 있는 하나 이상의 배포 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc9df-168">Depending on the type of application you build, there are one or more deployment options to choose from.</span></span> <span data-ttu-id="dc9df-169">자세한 내용은 [WPF 애플리케이션 배포](deploying-a-wpf-application-wpf.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dc9df-169">For more information, see [Deploying a WPF Application](deploying-a-wpf-application-wpf.md).</span></span>  
  
<a name="related_topics"></a>
## <a name="related-topics"></a><span data-ttu-id="dc9df-170">관련 항목</span><span class="sxs-lookup"><span data-stu-id="dc9df-170">Related Topics</span></span>  
  
|<span data-ttu-id="dc9df-171">제목</span><span class="sxs-lookup"><span data-stu-id="dc9df-171">Title</span></span>|<span data-ttu-id="dc9df-172">설명</span><span class="sxs-lookup"><span data-stu-id="dc9df-172">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="dc9df-173">응용 프로그램 관리 개요</span><span class="sxs-lookup"><span data-stu-id="dc9df-173">Application Management Overview</span></span>](application-management-overview.md)|<span data-ttu-id="dc9df-174">애플리케이션 수명, 창, 애플리케이션 리소스 및 탐색 관리를 비롯하여 <xref:System.Windows.Application> 클래스에 대해 개략적으로 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="dc9df-174">Provides an overview of the <xref:System.Windows.Application> class including managing application lifetime, windows, application resources, and navigation.</span></span>|  
|[<span data-ttu-id="dc9df-175">WPF의 창</span><span class="sxs-lookup"><span data-stu-id="dc9df-175">Windows in WPF</span></span>](windows-in-wpf-applications.md)|<span data-ttu-id="dc9df-176"><xref:System.Windows.Window> 클래스 및 대화 상자의 사용 방법을 비롯하여 애플리케이션의 창 관리에 대해 세부적으로 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="dc9df-176">Provides details of managing windows in your application including how to use the <xref:System.Windows.Window> class and dialog boxes.</span></span>|  
|[<span data-ttu-id="dc9df-177">탐색 개요</span><span class="sxs-lookup"><span data-stu-id="dc9df-177">Navigation Overview</span></span>](navigation-overview.md)|<span data-ttu-id="dc9df-178">애플리케이션 페이지 간의 탐색 관리에 대해 개략적으로 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="dc9df-178">Provides an overview of managing navigation between pages of your application.</span></span>|  
|[<span data-ttu-id="dc9df-179">호스팅</span><span class="sxs-lookup"><span data-stu-id="dc9df-179">Hosting</span></span>](hosting-wpf-applications.md)|<span data-ttu-id="dc9df-180">Xbap (XAML 브라우저 응용 프로그램)에 대 한 개요를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc9df-180">Provides an overview of XAML browser applications (XBAPs).</span></span>|  
|[<span data-ttu-id="dc9df-181">빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="dc9df-181">Build and Deploy</span></span>](building-and-deploying-wpf-applications.md)|<span data-ttu-id="dc9df-182">WPF 애플리케이션을 빌드하고 배포하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="dc9df-182">Describes how to build and deploy your WPF application.</span></span>|  
|[<span data-ttu-id="dc9df-183">Visual Studio에서의 WPF 소개</span><span class="sxs-lookup"><span data-stu-id="dc9df-183">Introduction to WPF in Visual Studio</span></span>](../getting-started/introduction-to-wpf-in-vs.md)|<span data-ttu-id="dc9df-184">WPF의 주요 기능에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="dc9df-184">Describes the main features of WPF.</span></span>|  
|[<span data-ttu-id="dc9df-185">연습: 내 첫 WPF 데스크톱 애플리케이션</span><span class="sxs-lookup"><span data-stu-id="dc9df-185">Walkthrough: My first WPF desktop application</span></span>](../getting-started/walkthrough-my-first-wpf-desktop-application.md)|<span data-ttu-id="dc9df-186">페이지 탐색, 레이아웃, 컨트롤, 이미지, 스타일 및 바인딩을 사용하여 WPF 애플리케이션을 만드는 방법을 보여 주는 연습입니다.</span><span class="sxs-lookup"><span data-stu-id="dc9df-186">A walkthrough that shows how to create a WPF application using page navigation, layout, controls, images, styles, and binding.</span></span>|
