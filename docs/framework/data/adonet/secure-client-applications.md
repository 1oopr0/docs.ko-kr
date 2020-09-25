---
title: 안전한 클라이언트 애플리케이션
ms.date: 03/30/2017
ms.assetid: 6239592e-fa7d-4dea-9f00-d296d0048b01
ms.openlocfilehash: 96b43d28d3e22df66cb7f7010916b5c7f7a86b77
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189008"
---
# <a name="secure-client-applications"></a><span data-ttu-id="4d665-102">안전한 클라이언트 애플리케이션</span><span class="sxs-lookup"><span data-stu-id="4d665-102">Secure Client Applications</span></span>

<span data-ttu-id="4d665-103">일반적으로 애플리케이션은 데이터 손실을 야기하거나 시스템을 손상시킬 수 있는 취약성으로부터 보호되어야 하는 다양한 부분으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d665-103">Applications typically consist of many parts that must all be protected from vulnerabilities that could result in data loss or otherwise compromise the system.</span></span> <span data-ttu-id="4d665-104">안전한 사용자 인터페이스를 만들면 공격자가 데이터나 시스템 리소스에 액세스하기 전에 이를 차단함으로써 여러 가지 문제를 예방할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d665-104">Creating secure user interfaces can prevent many problems by blocking attackers before they can access data or system resources.</span></span>  
  
## <a name="validate-user-input"></a><span data-ttu-id="4d665-105">사용자 입력 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="4d665-105">Validate User Input</span></span>  

 <span data-ttu-id="4d665-106">데이터에 액세스하는 애플리케이션을 만들 경우 유효성이 입증되기 전에는 모든 사용자 입력을 악의적인 것으로 간주해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d665-106">When constructing an application that accesses data, you should assume that all user input is malicious until proven otherwise.</span></span> <span data-ttu-id="4d665-107">그렇지 않으면 애플리케이션이 공격에 취약해질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d665-107">Failure to do so can leave your application vulnerable to attack.</span></span> <span data-ttu-id="4d665-108">.NET Framework에서는 입력할 수 있는 문자 수를 제한하는 등 입력 컨트롤에 대한 값 범위를 설정할 수 있게 해 주는 클래스가 포함되어 있으며,</span><span class="sxs-lookup"><span data-stu-id="4d665-108">The .NET Framework contains classes to help you enforce a domain of values for input controls, such as limiting the number of characters that can be entered.</span></span> <span data-ttu-id="4d665-109">값의 유효성을 검사하는 프로시저를 작성하기 위한 이벤트 후크도 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4d665-109">Event hooks allow you to write procedures to check the validity of values.</span></span> <span data-ttu-id="4d665-110">사용자 입력 데이터에 대해 유효성을 검사하고 강력한 형식을 지정함으로써 애플리케이션이 스크립트나 SQL 삽입 공격에 노출되지 않도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d665-110">User input data can be validated and strongly typed, limiting an application's exposure to script and SQL injection exploits.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4d665-111">클라이언트 애플리케이션뿐만 아니라 데이터 소스에서도 사용자 입력의 유효성을 검사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d665-111">You must also validate user input at the data source as well as in the client application.</span></span> <span data-ttu-id="4d665-112">공격자가 애플리케이션에 침투하여 데이터 소스를 직접 공격하는 방식을 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d665-112">An attacker may choose to circumvent your application and attack the data source directly.</span></span>  
  
 [<span data-ttu-id="4d665-113">보안 및 사용자 입력</span><span class="sxs-lookup"><span data-stu-id="4d665-113">Security and User Input</span></span>](../../../standard/security/security-and-user-input.md)  
 <span data-ttu-id="4d665-114">사용자 입력과 관련하여 잠재적 위험이 있는 버그를 처리하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4d665-114">Describes how to handle subtle and potentially dangerous bugs involving user input.</span></span>  
  
 <span data-ttu-id="4d665-115">[ASP.NET 웹 페이지에서 사용자 입력 유효성 검사](/previous-versions/aspnet/7kh55542(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4d665-115">[Validating User Input in ASP.NET Web Pages](/previous-versions/aspnet/7kh55542(v=vs.100))</span></span>  
 <span data-ttu-id="4d665-116">ASP.NET 유효성 검사 컨트롤을 통한 사용자 입력 유효성 검사에 대해 간략하게 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4d665-116">Overview of validating user input using ASP.NET validation controls.</span></span>  
  
 [<span data-ttu-id="4d665-117">Windows Forms에 사용자 입력</span><span class="sxs-lookup"><span data-stu-id="4d665-117">User Input in Windows Forms</span></span>](/dotnet/desktop/winforms/user-input-in-windows-forms)  
 <span data-ttu-id="4d665-118">Windows Forms 애플리케이션의 마우스 및 키보드 입력에 대한 유효성 검사와 관련된 정보 및 링크를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4d665-118">Provides links and information for validating mouse and keyboard input in a Windows Forms application.</span></span>  
  
 [<span data-ttu-id="4d665-119">.NET Framework 정규식</span><span class="sxs-lookup"><span data-stu-id="4d665-119">.NET Framework Regular Expressions</span></span>](../../../standard/base-types/regular-expressions.md)  
 <span data-ttu-id="4d665-120"><xref:System.Text.RegularExpressions.Regex> 클래스를 사용하여 사용자 입력의 유효성을 검사하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4d665-120">Describes how to use the <xref:System.Text.RegularExpressions.Regex> class to check the validity of user input.</span></span>  
  
## <a name="windows-applications"></a><span data-ttu-id="4d665-121">Windows 애플리케이션</span><span class="sxs-lookup"><span data-stu-id="4d665-121">Windows Applications</span></span>  

 <span data-ttu-id="4d665-122">예전에는 일반적으로 Windows 애플리케이션이 모든 권한으로 실행되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4d665-122">In the past, Windows applications generally ran with full permissions.</span></span> <span data-ttu-id="4d665-123">.NET Framework에서는 CAS(코드 액세스 보안)를 사용하여 Windows 애플리케이션에서의 코드 실행을 제한하는 인프라를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4d665-123">The .NET Framework provides the infrastructure to restrict code executing in a Windows application by using code access security (CAS).</span></span> <span data-ttu-id="4d665-124">하지만 CAS만으로는 애플리케이션을 보호하기에 부족합니다.</span><span class="sxs-lookup"><span data-stu-id="4d665-124">However, CAS alone is not enough to protect your application.</span></span>  
  
 [<span data-ttu-id="4d665-125">Windows Forms 보안</span><span class="sxs-lookup"><span data-stu-id="4d665-125">Windows Forms Security</span></span>](/dotnet/desktop/winforms/windows-forms-security)  
 <span data-ttu-id="4d665-126">Windows Forms 애플리케이션의 보안을 유지하는 방법을 설명하며 관련 항목 링크를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4d665-126">Discusses how to secure Windows Forms applications and provides links to related topics.</span></span>  
  
 [<span data-ttu-id="4d665-127">Windows Forms 및 관리되지 않는 애플리케이션</span><span class="sxs-lookup"><span data-stu-id="4d665-127">Windows Forms and Unmanaged Applications</span></span>](/dotnet/desktop/winforms/advanced/windows-forms-and-unmanaged-applications)  
 <span data-ttu-id="4d665-128">Windows Forms 애플리케이션에서 관리되지 않는 애플리케이션과 상호 작용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4d665-128">Describes how to interact with unmanaged applications in a Windows Forms application.</span></span>  
  
 [<span data-ttu-id="4d665-129">Windows Forms용 ClickOnce 배포</span><span class="sxs-lookup"><span data-stu-id="4d665-129">ClickOnce Deployment for Windows Forms</span></span>](/dotnet/desktop/winforms/clickonce-deployment-for-windows-forms)  
 <span data-ttu-id="4d665-130">Windows Forms 애플리케이션에서 `ClickOnce` 배포를 사용하는 방법 및 이와 관련된 보안 문제에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4d665-130">Describes how to use `ClickOnce` deployment in a Windows Forms application and discusses the security implications.</span></span>  
  
## <a name="aspnet-and-xml-web-services"></a><span data-ttu-id="4d665-131">ASP.NET 및 XML Web Services</span><span class="sxs-lookup"><span data-stu-id="4d665-131">ASP.NET and XML Web Services</span></span>  

 <span data-ttu-id="4d665-132">ASP.NET 애플리케이션은 일반적으로 웹 사이트의 특정 부분에 대한 액세스를 제한하고 데이터 보호 및 사이트 보안을 위한 기타 메커니즘을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d665-132">ASP.NET applications generally need to restrict access to some portions of the Web site and provide other mechanisms for data protection and site security.</span></span> <span data-ttu-id="4d665-133">다음 링크에서는 ASP.NET 애플리케이션 보안에 관련된 유용한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4d665-133">These links provide useful information for securing your ASP.NET application.</span></span>  
  
 <span data-ttu-id="4d665-134">XML Web service는 ASP.NET 애플리케이션, Windows Forms 애플리케이션 또는 다른 웹 서비스에서 사용할 수 있는 데이터를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4d665-134">An XML Web service provides data that can be consumed by an ASP.NET application, a Windows Forms application, or another Web service.</span></span> <span data-ttu-id="4d665-135">따라서 클라이언트 애플리케이션의 보안뿐만 아니라 웹 서비스 자체의 보안도 관리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d665-135">You need to manage security for the Web service itself as well as security for the client application.</span></span>  
  
 <span data-ttu-id="4d665-136">자세한 내용은 다음 리소스를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4d665-136">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="4d665-137">리소스</span><span class="sxs-lookup"><span data-stu-id="4d665-137">Resource</span></span>|<span data-ttu-id="4d665-138">설명</span><span class="sxs-lookup"><span data-stu-id="4d665-138">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="4d665-139">[ASP.NET 웹 사이트 보안](/previous-versions/aspnet/91f66yxt(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4d665-139">[Securing ASP.NET Web Sites](/previous-versions/aspnet/91f66yxt(v=vs.100))</span></span>|<span data-ttu-id="4d665-140">ASP.NET 애플리케이션의 보안을 유지하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4d665-140">Discusses how to secure ASP.NET applications.</span></span>|  
|<span data-ttu-id="4d665-141">[ASP.NET을 사용하여 만든 XML Web services에 보안 설정](/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4d665-141">[Securing XML Web Services Created Using ASP.NET](/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100))</span></span>|<span data-ttu-id="4d665-142">ASP.NET 웹 서비스의 보안을 구현하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4d665-142">Discusses how to implement security for an ASP.NET Web Service.</span></span>|  
|<span data-ttu-id="4d665-143">[스크립트 악용 개요](/previous-versions/aspnet/w1sw53ds(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4d665-143">[Script Exploits Overview](/previous-versions/aspnet/w1sw53ds(v=vs.100))</span></span>|<span data-ttu-id="4d665-144">악의적인 문자를 웹 페이지에 삽입하려고 시도하는 스크립트 기반 공격을 차단하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4d665-144">Discusses how to guard against a script exploit attack, which attempts to insert malicious characters into a Web page.</span></span>|  
|<span data-ttu-id="4d665-145">[웹 애플리케이션에 대 한 기본 보안 사례](/previous-versions/aspnet/zdh19h94(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4d665-145">[Basic Security Practices for Web Applications](/previous-versions/aspnet/zdh19h94(v=vs.100))</span></span>|<span data-ttu-id="4d665-146">일반 보안 관련 정보와 추가 정보에 대한 링크를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4d665-146">General security information and links to further discussion,</span></span>|  
  
## <a name="remoting"></a><span data-ttu-id="4d665-147">원격 통신</span><span class="sxs-lookup"><span data-stu-id="4d665-147">Remoting</span></span>  

 <span data-ttu-id="4d665-148">.NET Remoting을 사용하면 애플리케이션 구성 요소가 모두 한 컴퓨터에 있는지 또는 전 세계에 분산되어 있는지 여부에 관계없이 다양한 영역에 배포되는 애플리케이션을 쉽게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d665-148">.NET remoting enables you to build widely distributed applications easily, whether the application components are all on one computer or spread out across the entire world.</span></span> <span data-ttu-id="4d665-149">같은 컴퓨터 또는 해당 네트워크를 통해 연결할 수 있는 다른 모든 컴퓨터에 있는 다른 프로세스의 개체를 사용하는 클라이언트 애플리케이션을 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d665-149">You can build client applications that use objects in other processes on the same computer or on any other computer that is reachable over its network.</span></span> <span data-ttu-id="4d665-150">또한 .NET Remoting을 사용하면 동일한 프로세스에 있는 다른 애플리케이션 도메인과 통신할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d665-150">You can also use .NET remoting to communicate with other application domains in the same process.</span></span>  
  
|<span data-ttu-id="4d665-151">리소스</span><span class="sxs-lookup"><span data-stu-id="4d665-151">Resource</span></span>|<span data-ttu-id="4d665-152">설명</span><span class="sxs-lookup"><span data-stu-id="4d665-152">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="4d665-153">[원격 응용 프로그램 구성](/previous-versions/dotnet/netframework-4.0/b8tysty8(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4d665-153">[Configuration of Remote Applications](/previous-versions/dotnet/netframework-4.0/b8tysty8(v=vs.100))</span></span>|<span data-ttu-id="4d665-154">자주 발생하는 문제를 피할 수 있도록 원격 애플리케이션을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4d665-154">Discusses how to configure remoting applications in order to avoid common problems.</span></span>|  
|<span data-ttu-id="4d665-155">[원격 서비스의 보안](/previous-versions/dotnet/netframework-4.0/9hwst9th(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4d665-155">[Security in Remoting](/previous-versions/dotnet/netframework-4.0/9hwst9th(v=vs.100))</span></span>|<span data-ttu-id="4d665-156">인증 및 암호화에 대해 설명하고 원격 통신과 관련한 추가 보안 항목을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4d665-156">Describes authentication and encryption as well as additional security topics relevant to remoting.</span></span>|  
|[<span data-ttu-id="4d665-157">보안 및 원격 서비스 고려 사항</span><span class="sxs-lookup"><span data-stu-id="4d665-157">Security and Remoting Considerations</span></span>](../../misc/security-and-remoting-considerations.md)|<span data-ttu-id="4d665-158">보호되는 개체 및 애플리케이션 도메인 간의 보안 문제에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4d665-158">Describes security issues with protected objects and application domain crossing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4d665-159">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4d665-159">See also</span></span>

- [<span data-ttu-id="4d665-160">ADO.NET 애플리케이션 보안</span><span class="sxs-lookup"><span data-stu-id="4d665-160">Securing ADO.NET Applications</span></span>](securing-ado-net-applications.md)
- <span data-ttu-id="4d665-161">[데이터 액세스 전략에 대 한 권장 사항](/previous-versions/visualstudio/visual-studio-2008/8fxztkff(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="4d665-161">[Recommendations for Data Access Strategies](/previous-versions/visualstudio/visual-studio-2008/8fxztkff(v=vs.90))</span></span>
- [<span data-ttu-id="4d665-162">응용 프로그램 보안</span><span class="sxs-lookup"><span data-stu-id="4d665-162">Securing Applications</span></span>](/visualstudio/ide/securing-applications)
- [<span data-ttu-id="4d665-163">연결 정보 보호</span><span class="sxs-lookup"><span data-stu-id="4d665-163">Protecting Connection Information</span></span>](protecting-connection-information.md)
- [<span data-ttu-id="4d665-164">ADO.NET 개요</span><span class="sxs-lookup"><span data-stu-id="4d665-164">ADO.NET Overview</span></span>](ado-net-overview.md)
