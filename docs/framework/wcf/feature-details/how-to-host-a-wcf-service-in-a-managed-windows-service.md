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
# <a name="how-to-host-a-wcf-service-in-a-managed-windows-service"></a>방법: 관리형 Windows 서비스에서 WCF 서비스 호스팅

이 항목에서는 Windows 서비스에서 호스트 되는 WCF (Windows Communication Foundation) 서비스를 만드는 데 필요한 기본 단계에 대해 간략하게 설명 합니다. 이 시나리오는 메시지가 활성화 되지 않은 보안 환경의 인터넷 정보 서비스 (IIS) 외부에서 호스트 되는 장기 실행 WCF 서비스인 관리 되는 Windows 서비스 호스팅 옵션을 통해 사용 하도록 설정 됩니다. 서비스 수명은 대신 운영 체제에 의해 제어됩니다. 모든 버전의 Windows에서 이 호스팅 옵션을 사용할 수 있습니다.

Windows 서비스는 MMC(Microsoft Management Console)의 Microsoft.ManagementConsole.SnapIn을 통해 관리되고 시스템 부팅 시 자동으로 시작되도록 구성될 수 있습니다. 이 호스팅 옵션은 서비스의 프로세스 수명이 Windows 서비스의 SCM (서비스 제어 관리자)에 의해 제어 되도록 WCF 서비스를 관리 되는 Windows 서비스로 호스팅하는 응용 프로그램 도메인 (AppDomain)을 등록 하는 것으로 구성 됩니다.

서비스 코드에는 서비스 계약에 대한 서비스 구현, Windows 서비스 클래스 및 설치 관리자 클래스가 포함됩니다. 서비스 구현 클래스인는 `CalculatorService` WCF 서비스입니다. `CalculatorWindowsService`는 Windows 서비스입니다. Windows 서비스로 정규화하기 위해 클래스가 `ServiceBase`에서 상속되고 `OnStart` 및 `OnStop` 메서드를 구현합니다. `OnStart`에서 <xref:System.ServiceModel.ServiceHost> 형식에 대한 `CalculatorService`가 만들어지고 열립니다. `OnStop`에서 서비스가 중지되고 삭제됩니다. 또한 호스트는 애플리케이션 설정에서 구성된 대로 기본 주소를 서비스 호스트에 제공합니다. <xref:System.Configuration.Install.Installer>에서 상속되는 설치 관리자 클래스를 사용하면 프로그램을 Installutil.exe 도구를 통해 Windows 서비스로 설치할 수 있습니다.

## <a name="construct-the-service-and-provide-the-hosting-code"></a>서비스 생성 및 호스팅 코드 제공

1. **Service**라는 새 Visual Studio **콘솔 응용 프로그램** 프로젝트를 만듭니다.

2. Program.cs의 이름을 Service.cs로 바꿉니다.

3. 네임 스페이스를로 변경 `Microsoft.ServiceModel.Samples` 합니다.

4. 다음 어셈블리에 대한 참조를 추가합니다.

    - System.ServiceModel.dll

    - System.ServiceProcess.dll

    - System.Configuration.Install.dll

5. 다음 using 문을 Service.cs에 추가합니다.

     [!code-csharp[c_HowTo_HostInNTService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#0)]
     [!code-vb[c_HowTo_HostInNTService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#0)]

6. 다음 코드와 같이 `ICalculator` 서비스 계약을 정의합니다.

     [!code-csharp[c_HowTo_HostInNTService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#1)]
     [!code-vb[c_HowTo_HostInNTService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#1)]

7. 다음 코드와 같이 `CalculatorService` 클래스에서 서비스 계약을 구현합니다.

     [!code-csharp[c_HowTo_HostInNTService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#2)]
     [!code-vb[c_HowTo_HostInNTService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#2)]

8. `CalculatorWindowsService` 클래스에서 상속되는 <xref:System.ServiceProcess.ServiceBase> 클래스를 새로 만듭니다. `serviceHost` 인스턴스를 참조하는 <xref:System.ServiceModel.ServiceHost> 로컬 변수를 추가합니다. `Main`을 호출하는 `ServiceBase.Run(new CalculatorWindowsService)` 메서드를 정의합니다.

     [!code-csharp[c_HowTo_HostInNTService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#3)]
     [!code-vb[c_HowTo_HostInNTService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#3)]

9. 다음 코드와 같이 새 <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> 인스턴스를 만든 다음 열어서 <xref:System.ServiceModel.ServiceHost> 메서드를 재정의합니다.

     [!code-csharp[c_HowTo_HostInNTService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#4)]
     [!code-vb[c_HowTo_HostInNTService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#4)]

10. 다음 코드와 같이 <xref:System.ServiceProcess.ServiceBase.OnStop%2A>를 닫는 <xref:System.ServiceModel.ServiceHost> 메서드를 재정의합니다.

     [!code-csharp[c_HowTo_HostInNTService#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#5)]
     [!code-vb[c_HowTo_HostInNTService#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#5)]

11. `ProjectInstaller`에서 상속되며 <xref:System.Configuration.Install.Installer>로 설정된  <xref:System.ComponentModel.RunInstallerAttribute>로 표시되는 `true` 클래스를 새로 만듭니다. 그러면 Installutil.exe 도구를 통해 Windows 서비스를 설치할 수 있습니다.

     [!code-csharp[c_HowTo_HostInNTService#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#6)]
     [!code-vb[c_HowTo_HostInNTService#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#6)]

12. 프로젝트를 만들 때 생성된 `Service` 클래스를 제거합니다.

13. 프로젝트에 애플리케이션 구성 파일을 추가합니다. 파일의 내용을 다음 구성 XML로 바꿉니다.

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

     **솔루션 탐색기** 에서 app.config 파일을 마우스 오른쪽 단추로 클릭 하 고 **속성**을 선택 합니다. **출력 디렉터리에 복사** 에서 **최신 버전으로 복사**를 선택 합니다.

     다음 예제에서는 구성 파일의 엔드포인트를 명시적으로 지정합니다. 서비스에 엔드포인트를 추가하지 않으면 런타임에서 기본 엔드포인트를 자동으로 추가합니다. 이 예제에서는 서비스의 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>가 `true`로 설정되어 있으므로 서비스의 메타데이터 게시 기능도 사용하도록 설정되었습니다. 기본 엔드포인트, 바인딩 및 동작에 대한 자세한 내용은 [단순화된 구성](../simplified-configuration.md) 및 [WCF 서비스를 위한 단순화된 구성](../samples/simplified-configuration-for-wcf-services.md)을 참조하세요.

## <a name="install-and-run-the-service"></a>서비스를 설치하고 실행합니다.

1. 솔루션을 빌드하여 `Service.exe` 실행 파일을 만듭니다.

2. Visual Studio에 대 한 개발자 명령 프롬프트를 열고 프로젝트 디렉터리로 이동 합니다. 명령 프롬프트에서 `installutil bin\service.exe`를 입력하여 Windows 서비스를 설치합니다.

     명령 프롬프트에서 `services.msc`를 입력하여 SCM(서비스 제어 관리자)에 액세스합니다. Windows 서비스는 서비스에서 "WCFWindowsServiceSample"로 표시되어야 합니다. WCF 서비스는 Windows 서비스가 실행 중인 경우에만 클라이언트에 응답할 수 있습니다. 서비스를 시작 하려면 SCM에서 해당 서비스를 마우스 오른쪽 단추로 클릭 하 고 "시작"을 선택 하거나 명령 프롬프트에서 **net Start WCFWindowsServiceSample** 를 입력 합니다.

3. 서비스를 변경하려면 먼저 서비스를 중지하고 제거해야 합니다. 서비스를 중지 하려면 SCM에서 해당 서비스를 마우스 오른쪽 단추로 클릭 하 고 "중지"를 선택 하거나 명령 프롬프트에서 **net Stop WCFWindowsServiceSample을 입력** 합니다. Windows 서비스를 중지한 다음 클라이언트를 실행할 경우 클라이언트가 서비스에 액세스하려고 할 때 <xref:System.ServiceModel.EndpointNotFoundException> 예외가 발생합니다. Windows 서비스를 제거 하려면 명령 프롬프트에서 **installutil.exe/u bin\service.exe** 를 입력 합니다.

## <a name="example"></a>예제

다음은이 항목에서 사용 되는 전체 코드 목록입니다.

[!code-csharp[c_HowTo_HostInNTService#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#8)]
[!code-vb[c_HowTo_HostInNTService#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#8)]

&quot;자체 호스팅&quot; 옵션과 같이 Windows 서비스 호스팅 환경에서는 일부 호스팅 코드를 애플리케이션의 일부로 작성해야 합니다. 서비스는 콘솔 애플리케이션으로 구현되고 자체 호스팅 코드가 포함됩니다. 다른 호스팅 환경의 경우 IIS(인터넷 정보 서비스)의 WAS(Windows Process Activation Service) 호스팅과 같이 개발자가 호스팅 코드를 작성할 필요가 없습니다.

## <a name="see-also"></a>참고 항목

- [단순화된 구성](../simplified-configuration.md)
- [관리되는 애플리케이션에서의 호스팅](hosting-in-a-managed-application.md)
- [서비스 호스팅](../hosting-services.md)
- [Windows Server App Fabric 호스팅 기능](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
