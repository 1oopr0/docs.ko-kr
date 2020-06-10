---
title: '방법: 관리형 Windows 서비스에서 WCF 서비스 호스팅'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8e37363b-4dad-4fb6-907f-73c30fac1d9a
ms.openlocfilehash: dbd51abbc30b1010f7c4f206aad9a773eca0a714
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593180"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-windows-service"></a><span data-ttu-id="57ac4-102">방법: 관리형 Windows 서비스에서 WCF 서비스 호스팅</span><span class="sxs-lookup"><span data-stu-id="57ac4-102">How to: Host a WCF Service in a Managed Windows Service</span></span>

<span data-ttu-id="57ac4-103">이 항목에서는 Windows 서비스에서 호스트 되는 WCF (Windows Communication Foundation) 서비스를 만드는 데 필요한 기본 단계에 대해 간략하게 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-103">This topic outlines the basic steps required to create a Windows Communication Foundation (WCF) service that is hosted by a Windows Service.</span></span> <span data-ttu-id="57ac4-104">이 시나리오는 메시지가 활성화 되지 않은 보안 환경의 인터넷 정보 서비스 (IIS) 외부에서 호스트 되는 장기 실행 WCF 서비스인 관리 되는 Windows 서비스 호스팅 옵션을 통해 사용 하도록 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-104">The scenario is enabled by the managed Windows service hosting option that is a long-running WCF service hosted outside of Internet Information Services (IIS) in a secure environment that is not message activated.</span></span> <span data-ttu-id="57ac4-105">서비스 수명은 대신 운영 체제에 의해 제어됩니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-105">The lifetime of the service is controlled instead by the operating system.</span></span> <span data-ttu-id="57ac4-106">모든 버전의 Windows에서 이 호스팅 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-106">This hosting option is available in all versions of Windows.</span></span>

<span data-ttu-id="57ac4-107">Windows 서비스는 MMC(Microsoft Management Console)의 Microsoft.ManagementConsole.SnapIn을 통해 관리되고 시스템 부팅 시 자동으로 시작되도록 구성될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-107">Windows services can be managed with the Microsoft.ManagementConsole.SnapIn in Microsoft Management Console (MMC) and can be configured to start up automatically when the system boots up.</span></span> <span data-ttu-id="57ac4-108">이 호스팅 옵션은 서비스의 프로세스 수명이 Windows 서비스의 SCM (서비스 제어 관리자)에 의해 제어 되도록 WCF 서비스를 관리 되는 Windows 서비스로 호스팅하는 응용 프로그램 도메인 (AppDomain)을 등록 하는 것으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-108">This hosting option consists of registering the application domain (AppDomain) that hosts a WCF service as a managed Windows service so that the process lifetime of the service is controlled by the Service Control Manager (SCM) for Windows services.</span></span>

<span data-ttu-id="57ac4-109">서비스 코드에는 서비스 계약에 대한 서비스 구현, Windows 서비스 클래스 및 설치 관리자 클래스가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-109">The service code includes a service implementation of the service contract, a Windows Service class, and an installer class.</span></span> <span data-ttu-id="57ac4-110">서비스 구현 클래스인는 `CalculatorService` WCF 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-110">The service implementation class, `CalculatorService`, is a WCF service.</span></span> <span data-ttu-id="57ac4-111">`CalculatorWindowsService`는 Windows 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-111">The `CalculatorWindowsService` is a Windows service.</span></span> <span data-ttu-id="57ac4-112">Windows 서비스로 정규화하기 위해 클래스가 `ServiceBase`에서 상속되고 `OnStart` 및 `OnStop` 메서드를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-112">To qualify as a Windows service, the class inherits from `ServiceBase` and implements the `OnStart` and `OnStop` methods.</span></span> <span data-ttu-id="57ac4-113">`OnStart`에서 <xref:System.ServiceModel.ServiceHost> 형식에 대한 `CalculatorService`가 만들어지고 열립니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-113">In `OnStart`, a <xref:System.ServiceModel.ServiceHost> is created for the `CalculatorService` type and opened.</span></span> <span data-ttu-id="57ac4-114">`OnStop`에서 서비스가 중지되고 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-114">In `OnStop`, the service is stopped and disposed.</span></span> <span data-ttu-id="57ac4-115">또한 호스트는 애플리케이션 설정에서 구성된 대로 기본 주소를 서비스 호스트에 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-115">The host is also responsible for providing a base address to the service host, which has been configured in application settings.</span></span> <span data-ttu-id="57ac4-116"><xref:System.Configuration.Install.Installer>에서 상속되는 설치 관리자 클래스를 사용하면 프로그램을 Installutil.exe 도구를 통해 Windows 서비스로 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-116">The installer class, which inherits from <xref:System.Configuration.Install.Installer>, allows the program to be installed as a Windows service by the Installutil.exe tool.</span></span>

## <a name="construct-the-service-and-provide-the-hosting-code"></a><span data-ttu-id="57ac4-117">서비스 생성 및 호스팅 코드 제공</span><span class="sxs-lookup"><span data-stu-id="57ac4-117">Construct the service and provide the hosting code</span></span>

1. <span data-ttu-id="57ac4-118">**Service**라는 새 Visual Studio **콘솔 응용 프로그램** 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-118">Create a new Visual Studio **Console app** project called **Service**.</span></span>

2. <span data-ttu-id="57ac4-119">Program.cs의 이름을 Service.cs로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-119">Rename Program.cs to Service.cs.</span></span>

3. <span data-ttu-id="57ac4-120">네임 스페이스를로 변경 `Microsoft.ServiceModel.Samples` 합니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-120">Change the namespace to `Microsoft.ServiceModel.Samples`.</span></span>

4. <span data-ttu-id="57ac4-121">다음 어셈블리에 대한 참조를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-121">Add references to the following assemblies:</span></span>

    - <span data-ttu-id="57ac4-122">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="57ac4-122">System.ServiceModel.dll</span></span>

    - <span data-ttu-id="57ac4-123">System.ServiceProcess.dll</span><span class="sxs-lookup"><span data-stu-id="57ac4-123">System.ServiceProcess.dll</span></span>

    - <span data-ttu-id="57ac4-124">System.Configuration.Install.dll</span><span class="sxs-lookup"><span data-stu-id="57ac4-124">System.Configuration.Install.dll</span></span>

5. <span data-ttu-id="57ac4-125">다음 using 문을 Service.cs에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-125">Add the following using statements to Service.cs.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#0)]
     [!code-vb[c_HowTo_HostInNTService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#0)]

6. <span data-ttu-id="57ac4-126">다음 코드와 같이 `ICalculator` 서비스 계약을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-126">Define the `ICalculator` service contract as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#1)]
     [!code-vb[c_HowTo_HostInNTService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#1)]

7. <span data-ttu-id="57ac4-127">다음 코드와 같이 `CalculatorService` 클래스에서 서비스 계약을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-127">Implement the service contract in a class called `CalculatorService` as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#2)]
     [!code-vb[c_HowTo_HostInNTService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#2)]

8. <span data-ttu-id="57ac4-128">`CalculatorWindowsService` 클래스에서 상속되는 <xref:System.ServiceProcess.ServiceBase> 클래스를 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-128">Create a new class called `CalculatorWindowsService` that inherits from the <xref:System.ServiceProcess.ServiceBase> class.</span></span> <span data-ttu-id="57ac4-129">`serviceHost` 인스턴스를 참조하는 <xref:System.ServiceModel.ServiceHost> 로컬 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-129">Add a local variable called `serviceHost` to reference the <xref:System.ServiceModel.ServiceHost> instance.</span></span> <span data-ttu-id="57ac4-130">`Main`을 호출하는 `ServiceBase.Run(new CalculatorWindowsService)` 메서드를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-130">Define the `Main` method that calls `ServiceBase.Run(new CalculatorWindowsService)`</span></span>

     [!code-csharp[c_HowTo_HostInNTService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#3)]
     [!code-vb[c_HowTo_HostInNTService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#3)]

9. <span data-ttu-id="57ac4-131">다음 코드와 같이 새 <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> 인스턴스를 만든 다음 열어서 <xref:System.ServiceModel.ServiceHost> 메서드를 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-131">Override the <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> method by creating and opening a new <xref:System.ServiceModel.ServiceHost> instance as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#4)]
     [!code-vb[c_HowTo_HostInNTService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#4)]

10. <span data-ttu-id="57ac4-132">다음 코드와 같이 <xref:System.ServiceProcess.ServiceBase.OnStop%2A>를 닫는 <xref:System.ServiceModel.ServiceHost> 메서드를 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-132">Override the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method closing the <xref:System.ServiceModel.ServiceHost> as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#5)]
     [!code-vb[c_HowTo_HostInNTService#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#5)]

11. <span data-ttu-id="57ac4-133">`ProjectInstaller`에서 상속되며 <xref:System.Configuration.Install.Installer>로 설정된  <xref:System.ComponentModel.RunInstallerAttribute>로 표시되는 `true` 클래스를 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-133">Create a new class called `ProjectInstaller` that inherits from <xref:System.Configuration.Install.Installer> and that is marked with the <xref:System.ComponentModel.RunInstallerAttribute> set to `true`.</span></span> <span data-ttu-id="57ac4-134">그러면 Installutil.exe 도구를 통해 Windows 서비스를 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-134">This allows the Windows service to be installed by the Installutil.exe tool.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#6)]
     [!code-vb[c_HowTo_HostInNTService#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#6)]

12. <span data-ttu-id="57ac4-135">프로젝트를 만들 때 생성된 `Service` 클래스를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-135">Remove the `Service` class that was generated when you created the project.</span></span>

13. <span data-ttu-id="57ac4-136">프로젝트에 애플리케이션 구성 파일을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-136">Add an application configuration file to the project.</span></span> <span data-ttu-id="57ac4-137">파일의 내용을 다음 구성 XML로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-137">Replace the contents of the file with the following configuration XML.</span></span>

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
      <system.serviceModel>    <services>
          <!-- This section is optional with the new configuration model
               introduced in .NET Framework 4. -->
          <service name="Microsoft.ServiceModel.Samples.CalculatorService"
                   behaviorConfiguration="CalculatorServiceBehavior">
            <host>
              <baseAddresses>
                <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>
              </baseAddresses>
            </host>
            <!-- this endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service  -->
            <endpoint address=""
                      binding="wsHttpBinding"
                      contract="Microsoft.ServiceModel.Samples.ICalculator" />
            <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
            <endpoint address="mex"
                      binding="mexHttpBinding"
                      contract="IMetadataExchange" />
          </service>
        </services>
        <behaviors>
          <serviceBehaviors>
            <behavior name="CalculatorServiceBehavior">
              <serviceMetadata httpGetEnabled="true"/>
              <serviceDebug includeExceptionDetailInFaults="False"/>
            </behavior>
          </serviceBehaviors>
        </behaviors>
      </system.serviceModel>
    </configuration>
    ```

     <span data-ttu-id="57ac4-138">**솔루션 탐색기** 에서 app.config 파일을 마우스 오른쪽 단추로 클릭 하 고 **속성**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-138">Right click the App.config file in the **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="57ac4-139">**출력 디렉터리에 복사** 에서 **최신 버전으로 복사**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-139">Under **Copy to Output Directory** select **Copy if Newer**.</span></span>

     <span data-ttu-id="57ac4-140">다음 예제에서는 구성 파일의 엔드포인트를 명시적으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-140">This example explicitly specifies endpoints in the configuration file.</span></span> <span data-ttu-id="57ac4-141">서비스에 엔드포인트를 추가하지 않으면 런타임에서 기본 엔드포인트를 자동으로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-141">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="57ac4-142">이 예제에서는 서비스의 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>가 `true`로 설정되어 있으므로 서비스의 메타데이터 게시 기능도 사용하도록 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-142">In this example, because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> set to `true`, your service also has publishing metadata enabled.</span></span> <span data-ttu-id="57ac4-143">기본 엔드포인트, 바인딩 및 동작에 대한 자세한 내용은 [단순화된 구성](../simplified-configuration.md) 및 [WCF 서비스를 위한 단순화된 구성](../samples/simplified-configuration-for-wcf-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="57ac4-143">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../simplified-configuration.md) and [Simplified Configuration for WCF Services](../samples/simplified-configuration-for-wcf-services.md).</span></span>

## <a name="install-and-run-the-service"></a><span data-ttu-id="57ac4-144">서비스를 설치하고 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-144">Install and run the service</span></span>

1. <span data-ttu-id="57ac4-145">솔루션을 빌드하여 `Service.exe` 실행 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-145">Build the solution to create the `Service.exe` executable.</span></span>

2. <span data-ttu-id="57ac4-146">Visual Studio에 대 한 개발자 명령 프롬프트를 열고 프로젝트 디렉터리로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-146">Open Developer Command Prompt for Visual Studio and navigate to the project directory.</span></span> <span data-ttu-id="57ac4-147">명령 프롬프트에서 `installutil bin\service.exe`를 입력하여 Windows 서비스를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-147">Type `installutil bin\service.exe` at the command prompt to install the Windows service.</span></span>

     <span data-ttu-id="57ac4-148">명령 프롬프트에서 `services.msc`를 입력하여 SCM(서비스 제어 관리자)에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-148">Type `services.msc` at the command prompt to access the Service Control Manager (SCM).</span></span> <span data-ttu-id="57ac4-149">Windows 서비스는 서비스에서 "WCFWindowsServiceSample"로 표시되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-149">The Windows service should appear in Services as "WCFWindowsServiceSample".</span></span> <span data-ttu-id="57ac4-150">WCF 서비스는 Windows 서비스가 실행 중인 경우에만 클라이언트에 응답할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-150">The WCF service can only respond to clients if the Windows service is running.</span></span> <span data-ttu-id="57ac4-151">서비스를 시작 하려면 SCM에서 해당 서비스를 마우스 오른쪽 단추로 클릭 하 고 "시작"을 선택 하거나 명령 프롬프트에서 **net Start WCFWindowsServiceSample** 를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-151">To start the service, right-click it in the SCM and select "Start", or type **net start WCFWindowsServiceSample** at the command prompt.</span></span>

3. <span data-ttu-id="57ac4-152">서비스를 변경하려면 먼저 서비스를 중지하고 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-152">If you make changes to the service, you must first stop it and uninstall it.</span></span> <span data-ttu-id="57ac4-153">서비스를 중지 하려면 SCM에서 해당 서비스를 마우스 오른쪽 단추로 클릭 하 고 "중지"를 선택 하거나 명령 프롬프트에서 **net Stop WCFWindowsServiceSample을 입력** 합니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-153">To stop the service, right-click the service in the SCM and select "Stop", or **type net stop WCFWindowsServiceSample** at the command prompt.</span></span> <span data-ttu-id="57ac4-154">Windows 서비스를 중지한 다음 클라이언트를 실행할 경우 클라이언트가 서비스에 액세스하려고 할 때 <xref:System.ServiceModel.EndpointNotFoundException> 예외가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-154">Note that if you stop the Windows service and then run a client, an <xref:System.ServiceModel.EndpointNotFoundException> exception occurs when a client attempts to access the service.</span></span> <span data-ttu-id="57ac4-155">Windows 서비스를 제거 하려면 명령 프롬프트에서 **installutil.exe/u bin\service.exe** 를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-155">To uninstall the Windows service type **installutil /u bin\service.exe** at the command prompt.</span></span>

## <a name="example"></a><span data-ttu-id="57ac4-156">예제</span><span class="sxs-lookup"><span data-stu-id="57ac4-156">Example</span></span>

<span data-ttu-id="57ac4-157">다음은이 항목에서 사용 되는 전체 코드 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-157">The following is a complete listing of the code used by this topic:</span></span>

[!code-csharp[c_HowTo_HostInNTService#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#8)]
[!code-vb[c_HowTo_HostInNTService#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#8)]

<span data-ttu-id="57ac4-158">&quot;자체 호스팅&quot; 옵션과 같이 Windows 서비스 호스팅 환경에서는 일부 호스팅 코드를 애플리케이션의 일부로 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-158">Like the "Self-Hosting" option, the Windows service hosting environment requires that some hosting code be written as part of the application.</span></span> <span data-ttu-id="57ac4-159">서비스는 콘솔 애플리케이션으로 구현되고 자체 호스팅 코드가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-159">The service is implemented as a console application and contains its own hosting code.</span></span> <span data-ttu-id="57ac4-160">다른 호스팅 환경의 경우 IIS(인터넷 정보 서비스)의 WAS(Windows Process Activation Service) 호스팅과 같이 개발자가 호스팅 코드를 작성할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="57ac4-160">In other hosting environments, such as Windows Process Activation Service (WAS) hosting in Internet Information Services (IIS), it is not necessary for developers to write hosting code.</span></span>

## <a name="see-also"></a><span data-ttu-id="57ac4-161">참고 항목</span><span class="sxs-lookup"><span data-stu-id="57ac4-161">See also</span></span>

- [<span data-ttu-id="57ac4-162">단순화된 구성</span><span class="sxs-lookup"><span data-stu-id="57ac4-162">Simplified Configuration</span></span>](../simplified-configuration.md)
- [<span data-ttu-id="57ac4-163">관리되는 애플리케이션에서의 호스팅</span><span class="sxs-lookup"><span data-stu-id="57ac4-163">Hosting in a Managed Application</span></span>](hosting-in-a-managed-application.md)
- [<span data-ttu-id="57ac4-164">서비스 호스팅</span><span class="sxs-lookup"><span data-stu-id="57ac4-164">Hosting Services</span></span>](../hosting-services.md)
- <span data-ttu-id="57ac4-165">[Windows Server App Fabric 호스팅 기능](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="57ac4-165">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
