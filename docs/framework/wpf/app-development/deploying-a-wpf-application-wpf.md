---
title: 앱 배포
description: Windows 및 .NET Framework Windows Presentation Foundation (WPF) 응용 프로그램에 사용 하는 배포 기술을 살펴봅니다.
ms.date: 03/30/2017
helpviewer_keywords:
- WPF applications [WPF], deployment
- deployment [WPF], applications
ms.assetid: 12cadca0-b32c-4064-9a56-e6a306dcc76d
ms.openlocfilehash: 62904ccd47800c8340d68c223e50688902170063
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619301"
---
# <a name="deploy-a-wpf-application"></a><span data-ttu-id="f7874-103">WPF 응용 프로그램 배포</span><span class="sxs-lookup"><span data-stu-id="f7874-103">Deploy a WPF Application</span></span>

<span data-ttu-id="f7874-104">Windows Presentation Foundation (WPF) 응용 프로그램을 빌드한 후 배포 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-104">After Windows Presentation Foundation (WPF) applications are built, they need to be deployed.</span></span> <span data-ttu-id="f7874-105">Windows 및 .NET Framework에는 몇 가지 배포 기술이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-105">Windows and the .NET Framework include several deployment technologies.</span></span> <span data-ttu-id="f7874-106">WPF 응용 프로그램을 배포 하는 데 사용 되는 배포 기술은 응용 프로그램 유형에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-106">The deployment technology that is used to deploy a WPF application depends on the application type.</span></span> <span data-ttu-id="f7874-107">이 항목에서는 각 배포 기술에 대 한 간략 한 개요와 각 WPF 응용 프로그램 유형의 배포 요구 사항과 함께 사용 되는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-107">This topic provides a brief overview of each deployment technology, and how they are used in conjunction with the deployment requirements of each WPF application type.</span></span>

<a name="Deployment_Technologies"></a>
## <a name="deployment-technologies"></a><span data-ttu-id="f7874-108">배포 기술</span><span class="sxs-lookup"><span data-stu-id="f7874-108">Deployment Technologies</span></span>  
 <span data-ttu-id="f7874-109">Windows 및 .NET Framework에는 다음과 같은 몇 가지 배포 기술이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-109">Windows and the .NET Framework include several deployment technologies, including:</span></span>  
  
- <span data-ttu-id="f7874-110">XCopy 배포.</span><span class="sxs-lookup"><span data-stu-id="f7874-110">XCopy deployment.</span></span>  
  
- <span data-ttu-id="f7874-111">배포를 Windows Installer 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-111">Windows Installer deployment.</span></span>  
  
- <span data-ttu-id="f7874-112">ClickOnce 배포.</span><span class="sxs-lookup"><span data-stu-id="f7874-112">ClickOnce deployment.</span></span>  
  
<a name="XCopy_Deployment"></a>
### <a name="xcopy-deployment"></a><span data-ttu-id="f7874-113">XCopy 배포</span><span class="sxs-lookup"><span data-stu-id="f7874-113">XCopy Deployment</span></span>  
 <span data-ttu-id="f7874-114">XCopy 배포는 XCopy 명령줄 프로그램을 사용하여 한 위치에서 다른 위치로 파일을 복사하는 방법을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-114">XCopy deployment refers to the use of the XCopy command-line program to copy files from one location to another.</span></span> <span data-ttu-id="f7874-115">XCopy 배포는 다음과 같은 경우에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-115">XCopy deployment is suitable under the following circumstances:</span></span>  
  
- <span data-ttu-id="f7874-116">애플리케이션이 독립적이며,</span><span class="sxs-lookup"><span data-stu-id="f7874-116">The application is self-contained.</span></span> <span data-ttu-id="f7874-117">실행하기 위해 클라이언트를 업데이트할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-117">It does not need to update the client to run.</span></span>  
  
- <span data-ttu-id="f7874-118">빌드 위치 (로컬 디스크, UNC 파일 공유 등)에서 게시 위치 (웹 사이트, UNC 파일 공유 등)로 응용 프로그램 파일을 이동 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-118">Application files must be moved from one location to another, such as from a build location (local disk, UNC file share, and so on) to a publish location (Web site, UNC file share, and so on).</span></span>  
  
- <span data-ttu-id="f7874-119">애플리케이션에 셸 통합(시작 메뉴 바로 가기, 데스크톱 아이콘 등)이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-119">The application does not require shell integration (Start menu shortcut, desktop icon, and so on).</span></span>  
  
 <span data-ttu-id="f7874-120">XCopy는 간단한 배포 시나리오에 적합하지만 좀더 복잡한 배포 기능이 필요한 경우 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-120">Although XCopy is suitable for simple deployment scenarios, it is limited when more complex deployment capabilities are required.</span></span> <span data-ttu-id="f7874-121">특히 XCopy를 사용하면 강력한 방식으로 배포를 관리하기 위한 스크립트를 작성, 실행 및 유지 관리하는 오버헤드가 자주 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-121">In particular, using XCopy often incurs the overhead for creating, executing, and maintaining scripts for managing deployment in a robust way.</span></span> <span data-ttu-id="f7874-122">또한 XCopy는 버전 관리, 제거 또는 롤백을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-122">Furthermore, XCopy does not support versioning, uninstallation, or rollback.</span></span>  
  
<a name="Windows_Installer"></a>
### <a name="windows-installer"></a><span data-ttu-id="f7874-123">Windows Installer</span><span class="sxs-lookup"><span data-stu-id="f7874-123">Windows Installer</span></span>  
 <span data-ttu-id="f7874-124">Windows Installer를 사용 하면 쉽게 클라이언트에 배포 하 고 실행할 수 있는 자체 포함 실행 파일로 응용 프로그램을 패키지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-124">Windows Installer allows applications to be packaged as self-contained executables that can be easily distributed to clients and run.</span></span> <span data-ttu-id="f7874-125">또한 Windows Installer는 Windows와 함께 설치 되며 바탕 화면, 시작 메뉴 및 프로그램 제어판과 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-125">Furthermore, Windows Installer is installed with Windows and enables integration with the desktop, the Start menu, and the Programs control panel.</span></span>  
  
 <span data-ttu-id="f7874-126">Windows Installer는 응용 프로그램의 설치 및 제거를 간소화 하지만 설치 된 응용 프로그램이 버전 관리 관점에서 최신 상태로 유지 되도록 하는 기능을 제공 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-126">Windows Installer simplifies the installation and uninstallation of applications, but it does not provide facilities for ensuring that installed applications are kept up-to-date from a versioning standpoint.</span></span>  
  
 <span data-ttu-id="f7874-127">Windows Installer에 대 한 자세한 내용은 [Windows Installer 배포](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f7874-127">For more information about Windows Installer, see [Windows Installer Deployment](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).</span></span>
  
<a name="ClickOnce_Deployment"></a>
### <a name="clickonce-deployment"></a><span data-ttu-id="f7874-128">ClickOnce 배포</span><span class="sxs-lookup"><span data-stu-id="f7874-128">ClickOnce Deployment</span></span>  
 <span data-ttu-id="f7874-129">ClickOnce를 사용 하면 웹 스타일 응용 프로그램을 사용 하지 않는 응용 프로그램을 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-129">ClickOnce enables Web-style application deployment for non-Web applications.</span></span> <span data-ttu-id="f7874-130">애플리케이션이 웹 또는 파일 서버에서 게시되고 배포됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-130">Applications are published to and deployed from Web or file servers.</span></span> <span data-ttu-id="f7874-131">ClickOnce는 Windows Installer 설치 된 응용 프로그램에서 사용할 수 있는 클라이언트 기능의 전체 범위를 지원 하지 않지만 다음을 포함 하는 하위 집합을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-131">Although ClickOnce does not support the full range of client features that Windows Installer-installed applications do, it does support a subset that includes the following:</span></span>  
  
- <span data-ttu-id="f7874-132">시작 메뉴 및 프로그램 제어판과의 통합.</span><span class="sxs-lookup"><span data-stu-id="f7874-132">Integration with the Start menu and Programs control panel.</span></span>  
  
- <span data-ttu-id="f7874-133">버전 관리, 롤백 및 제거.</span><span class="sxs-lookup"><span data-stu-id="f7874-133">Versioning, rollback, and uninstallation.</span></span>  
  
- <span data-ttu-id="f7874-134">항상 배포 위치에서 애플리케이션을 시작하는 온라인 설치 모드.</span><span class="sxs-lookup"><span data-stu-id="f7874-134">Online install mode, which always launches an application from the deployment location.</span></span>  
  
- <span data-ttu-id="f7874-135">새 버전이 릴리스되는 경우 자동 업데이트.</span><span class="sxs-lookup"><span data-stu-id="f7874-135">Automatic updating when new versions are released.</span></span>  
  
- <span data-ttu-id="f7874-136">파일 확장명 등록.</span><span class="sxs-lookup"><span data-stu-id="f7874-136">Registration of file extensions.</span></span>  
  
 <span data-ttu-id="f7874-137">ClickOnce에 대 한 자세한 내용은 [Clickonce 보안 및 배포](/visualstudio/deployment/clickonce-security-and-deployment)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f7874-137">For more information about ClickOnce, see [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment).</span></span>  
  
<a name="Deploying_WPF_Applications"></a>
## <a name="deploying-wpf-applications"></a><span data-ttu-id="f7874-138">WPF 애플리케이션 배포</span><span class="sxs-lookup"><span data-stu-id="f7874-138">Deploying WPF Applications</span></span>  
 <span data-ttu-id="f7874-139">WPF 응용 프로그램에 대 한 배포 옵션은 응용 프로그램의 형식에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-139">The deployment options for a WPF application depend on the type of application.</span></span> <span data-ttu-id="f7874-140">배포 관점에서 WPF는 다음과 같은 세 가지 중요 한 응용 프로그램 유형을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-140">From a deployment perspective, WPF has three significant application types:</span></span>  
  
- <span data-ttu-id="f7874-141">독립 실행형 애플리케이션.</span><span class="sxs-lookup"><span data-stu-id="f7874-141">Standalone applications.</span></span>  
  
- <span data-ttu-id="f7874-142">마크업 전용 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 애플리케이션.</span><span class="sxs-lookup"><span data-stu-id="f7874-142">Markup-only [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] applications.</span></span>  
  
- <span data-ttu-id="f7874-143">Xbap (XAML 브라우저 응용 프로그램).</span><span class="sxs-lookup"><span data-stu-id="f7874-143">XAML browser applications (XBAPs).</span></span>  
  
<a name="Deploying_Standalone_Applications"></a>
### <a name="deploying-standalone-applications"></a><span data-ttu-id="f7874-144">독립 실행형 애플리케이션 배포</span><span class="sxs-lookup"><span data-stu-id="f7874-144">Deploying Standalone Applications</span></span>  
 <span data-ttu-id="f7874-145">독립 실행형 응용 프로그램은 ClickOnce 또는 Windows Installer를 사용 하 여 배포 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-145">Standalone applications are deployed using either ClickOnce or Windows Installer.</span></span> <span data-ttu-id="f7874-146">두 방법 모두 독립 실행형 애플리케이션을 실행하려면 완전 신뢰가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-146">Either way, standalone applications require full trust to run.</span></span> <span data-ttu-id="f7874-147">Windows Installer를 사용 하 여 배포 되는 독립 실행형 응용 프로그램에는 완전 신뢰가 자동으로 부여 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-147">Full trust is automatically granted to standalone applications that are deployed using Windows Installer.</span></span> <span data-ttu-id="f7874-148">ClickOnce를 사용 하 여 배포 되는 독립 실행형 응용 프로그램에는 완전 신뢰가 자동으로 부여 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-148">Standalone applications that are deployed using ClickOnce are not automatically granted full trust.</span></span> <span data-ttu-id="f7874-149">대신 ClickOnce는 독립 실행형 응용 프로그램을 설치 하기 전에 사용자가 동의 해야 하는 보안 경고 대화 상자를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-149">Instead, ClickOnce displays a security warning dialog that users must accept before a standalone application is installed.</span></span> <span data-ttu-id="f7874-150">동의하면 독립 실행형 애플리케이션이 설치되고 완전 신뢰가 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-150">If accepted, the standalone application is installed and granted full trust.</span></span> <span data-ttu-id="f7874-151">동의하지 않으면 독립 실행형 애플리케이션이 설치되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-151">If not, the standalone application is not installed.</span></span>  
  
<a name="Deploying_Markup_Only_XAML_Applications"></a>
### <a name="deploying-markup-only-xaml-applications"></a><span data-ttu-id="f7874-152">마크업 전용 XAML 애플리케이션 배포</span><span class="sxs-lookup"><span data-stu-id="f7874-152">Deploying Markup-Only XAML Applications</span></span>  
 <span data-ttu-id="f7874-153">태그 전용 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 페이지는 일반적으로 HTML 페이지와 같은 웹 서버에 게시 되며 Internet Explorer를 사용 하 여 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-153">Markup-only [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pages are usually published to Web servers, like HTML pages, and can be viewed using Internet Explorer.</span></span> <span data-ttu-id="f7874-154">마크업 전용 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 페이지는 인터넷 영역 권한 설정에 정의된 제한 사항이 있는 부분 신뢰 보안 샌드박스 내에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-154">Markup-only [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pages run within a partial-trust security sandbox with restrictions that are defined by the Internet zone permission set.</span></span> <span data-ttu-id="f7874-155">HTML 기반 웹 응용 프로그램에 해당 하는 보안 샌드박스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-155">This provides an equivalent security sandbox to HTML-based Web applications.</span></span>  
  
 <span data-ttu-id="f7874-156">WPF 응용 프로그램의 보안에 대 한 자세한 내용은 [보안](../security-wpf.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f7874-156">For more information about security for WPF applications, see [Security](../security-wpf.md).</span></span>  
  
 <span data-ttu-id="f7874-157">마크업 전용 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 페이지는 XCopy 또는 Windows Installer를 사용 하 여 로컬 파일 시스템에 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-157">Markup-only [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pages can be installed to the local file system by using either XCopy or Windows Installer.</span></span> <span data-ttu-id="f7874-158">이러한 페이지는 Internet Explorer 또는 Windows 탐색기를 사용 하 여 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-158">These pages can be viewed using Internet Explorer or Windows Explorer.</span></span>  
  
 <span data-ttu-id="f7874-159">XAML에 대한 자세한 내용은 [XAML 개요(WPF)](../../../desktop-wpf/fundamentals/xaml.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f7874-159">For more information about XAML, see [XAML Overview (WPF)](../../../desktop-wpf/fundamentals/xaml.md).</span></span>  
  
<a name="Deploying_XAML_Browser_Applications"></a>
### <a name="deploying-xaml-browser-applications"></a><span data-ttu-id="f7874-160">XAML 브라우저 애플리케이션 배포</span><span class="sxs-lookup"><span data-stu-id="f7874-160">Deploying XAML Browser Applications</span></span>  
 <span data-ttu-id="f7874-161">Xbap는 다음 세 개의 파일을 배포 해야 하는 컴파일된 응용 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-161">XBAPs are compiled applications that require the following three files to be deployed:</span></span>  
  
- <span data-ttu-id="f7874-162">*ApplicationName*.exe: 실행 가능한 어셈블리 애플리케이션 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-162">*ApplicationName*.exe: The executable assembly application file.</span></span>  
  
- <span data-ttu-id="f7874-163">*ApplicationName*.xbap: 배포 매니페스트입니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-163">*ApplicationName*.xbap: The deployment manifest.</span></span>  
  
- <span data-ttu-id="f7874-164">*ApplicationName*.exe.manifest: 애플리케이션 매니페스트입니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-164">*ApplicationName*.exe.manifest: The application manifest.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f7874-165">배포 및 애플리케이션 매니페스트에 대한 자세한 내용은 [WPF 애플리케이션 만들기](building-a-wpf-application-wpf.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f7874-165">For more information about deployment and application manifests, see [Building a WPF Application](building-a-wpf-application-wpf.md).</span></span>  
  
 <span data-ttu-id="f7874-166">이러한 파일은 XBAP를 빌드할 때 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-166">These files are produced when an XBAP is built.</span></span> <span data-ttu-id="f7874-167">자세한 내용은 [방법: 새 WPF 브라우저 애플리케이션 프로젝트 만들기](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628663(v=vs.100))를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f7874-167">For more information, see [How to: Create a New WPF Browser Application Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628663(v=vs.100)).</span></span> <span data-ttu-id="f7874-168">태그 전용 페이지와 마찬가지로 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] xbap는 일반적으로 웹 서버에 게시 되 고 Internet Explorer를 사용 하 여 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-168">Like markup-only [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pages, XBAPs are typically published to a Web server and viewed using Internet Explorer.</span></span>  
  
 <span data-ttu-id="f7874-169">Xbap는 배포 방법 중 하나를 사용 하 여 클라이언트에 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-169">XBAPs can be deployed to clients using any of the deployment techniques.</span></span> <span data-ttu-id="f7874-170">그러나 ClickOnce는 다음과 같은 기능을 제공 하므로 권장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-170">However, ClickOnce is recommended since it provides the following capabilities:</span></span>  
  
1. <span data-ttu-id="f7874-171">새 버전이 게시될 때 자동 업데이트.</span><span class="sxs-lookup"><span data-stu-id="f7874-171">Automatic updates when a new version is published.</span></span>  
  
2. <span data-ttu-id="f7874-172">완전 신뢰로 실행 되는 XBAP에 대 한 권한 상승 권한입니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-172">Elevation privileges for the XBAP running with full trust.</span></span>  
  
 <span data-ttu-id="f7874-173">기본적으로 ClickOnce는 .deploy 확장명을 사용하여 애플리케이션 파일을 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-173">By default, ClickOnce publishes application files with the .deploy extension.</span></span> <span data-ttu-id="f7874-174">그러면 문제가 될 수 있지만 사용하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-174">This can be problematic, but can be disabled.</span></span> <span data-ttu-id="f7874-175">자세한 내용은 [ClickOnce 배포 시 서버 및 클라이언트 구성 문제](/visualstudio/deployment/server-and-client-configuration-issues-in-clickonce-deployments)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f7874-175">For more information, see [Server and Client Configuration Issues in ClickOnce Deployments](/visualstudio/deployment/server-and-client-configuration-issues-in-clickonce-deployments).</span></span>  
  
 <span data-ttu-id="f7874-176">Xbap (XAML 브라우저 응용 프로그램)를 배포 하는 방법에 대 한 자세한 내용은 [WPF XAML 브라우저 응용 프로그램 개요](wpf-xaml-browser-applications-overview.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f7874-176">For more information about deploying XAML browser applications (XBAPs), see [WPF XAML Browser Applications Overview](wpf-xaml-browser-applications-overview.md).</span></span>  
  
<a name="Installing__NET_Framework_3_0"></a>
## <a name="installing-the-net-framework"></a><span data-ttu-id="f7874-177">.NET Framework 설치</span><span class="sxs-lookup"><span data-stu-id="f7874-177">Installing the .NET Framework</span></span>  
 <span data-ttu-id="f7874-178">WPF 응용 프로그램을 실행 하려면 클라이언트에 Microsoft .NET 프레임 워크를 설치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-178">To run a WPF application, the Microsoft .NET Framework must be installed on the client.</span></span> <span data-ttu-id="f7874-179">Internet Explorer는 WPF 브라우저에서 호스트 되는 응용 프로그램을 볼 때 클라이언트가 .NET Framework와 함께 설치 되는지 여부를 자동으로 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-179">Internet Explorer automatically detects whether clients are installed with .NET Framework when WPF browser-hosted applications are viewed.</span></span> <span data-ttu-id="f7874-180">.NET Framework 설치 되어 있지 않으면 Internet Explorer에서 사용자에 게 설치를 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-180">If the .NET Framework is not installed, Internet Explorer prompts users to install it.</span></span>  
  
 <span data-ttu-id="f7874-181">.NET Framework 설치 되어 있는지 여부를 검색 하기 위해 Internet Explorer에는 확장명이 .xaml, .xps, xbap 및 응용 프로그램 인 콘텐츠 파일에 대 한 대체 (fallback) MIME (fallback) 처리기로 등록 된 부트스트래퍼 응용 프로그램이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-181">To detect whether the .NET Framework is installed, Internet Explorer includes a bootstrapper application that is registered as the fallback Multipurpose Internet Mail Extensions (MIME) handler for content files with the following extensions: .xaml, .xps, .xbap, and .application.</span></span> <span data-ttu-id="f7874-182">이러한 파일 형식으로 이동 하 여 클라이언트에 .NET Framework 설치 되어 있지 않으면 부트스트래퍼 응용 프로그램에서 설치 권한을 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-182">If you navigate to these file types and the .NET Framework is not installed on the client, the bootstrapper application requests permission to install it.</span></span> <span data-ttu-id="f7874-183">사용 권한이 제공 되지 않으면 .NET Framework 및 응용 프로그램은 설치 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-183">If permission is not provided, neither the .NET Framework nor the application is installed.</span></span>  
  
 <span data-ttu-id="f7874-184">사용 권한이 부여 된 경우 Internet Explorer는 Microsoft Background Intelligent Transfer Service (BITS)를 사용 하 여 .NET Framework를 다운로드 하 고 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-184">If permission is granted, Internet Explorer downloads and installs the .NET Framework using the Microsoft Background Intelligent Transfer Service (BITS).</span></span> <span data-ttu-id="f7874-185">.NET Framework를 성공적으로 설치한 후에는 원래 요청한 파일이 새 브라우저 창에서 열립니다.</span><span class="sxs-lookup"><span data-stu-id="f7874-185">After successful installation of the .NET Framework, the originally requested file is opened in a new browser window.</span></span>  
  
 <span data-ttu-id="f7874-186">자세한 내용은 [.NET Framework 및 애플리케이션 배포](../../deployment/index.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f7874-186">For more information, see [Deploying the .NET Framework and Applications](../../deployment/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7874-187">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f7874-187">See also</span></span>

- [<span data-ttu-id="f7874-188">WPF 애플리케이션 빌드</span><span class="sxs-lookup"><span data-stu-id="f7874-188">Building a WPF Application</span></span>](building-a-wpf-application-wpf.md)
- [<span data-ttu-id="f7874-189">보안</span><span class="sxs-lookup"><span data-stu-id="f7874-189">Security</span></span>](../security-wpf.md)
