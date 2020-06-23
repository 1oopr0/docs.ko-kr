---
title: Getting Started 샘플
description: WCF를 사용 하 여 일반 서비스와 일반 클라이언트를 구현 하는 방법에 대해 알아봅니다. 이 샘플은 다른 모든 기본 기술 샘플의 기준이 됩니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- basic samples [WCF], getting started
ms.assetid: 967a3d94-0261-49ff-b85a-20bb07f1af20
ms.openlocfilehash: b23be1b33f227154b916429c063ec4106229bb3c
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246235"
---
# <a name="getting-started-sample"></a><span data-ttu-id="6c893-104">Getting Started 샘플</span><span class="sxs-lookup"><span data-stu-id="6c893-104">Getting Started Sample</span></span>

<span data-ttu-id="6c893-105">시작 샘플에서는 WCF (Windows Communication Foundation)를 사용 하 여 일반 서비스와 일반 클라이언트를 구현 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-105">The Getting Started sample demonstrates how to implement a typical service and a typical client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="6c893-106">이 샘플은 다른 모든 기본 기술 샘플의 기준이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-106">This sample is the basis for all other basic technology samples.</span></span>

> [!NOTE]
> <span data-ttu-id="6c893-107">이 샘플의 설치 절차 및 빌드 지침은 이 항목의 끝부분에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6c893-108">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-108">The samples may already be installed on your computer.</span></span> <span data-ttu-id="6c893-109">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="6c893-109">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="6c893-110">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6c893-111">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-111">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\GettingStarted\GettingStarted`

<span data-ttu-id="6c893-112">서비스는 메타데이터로 공개적으로 노출하는 서비스 계약에서 수행하는 작업을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-112">The service describes the operations it performs in a service contract that it exposes publicly as metadata.</span></span> <span data-ttu-id="6c893-113">또한 서비스에는 작업을 구현하기 위한 코드가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-113">The service also contains the code to implement the operations.</span></span>

<span data-ttu-id="6c893-114">클라이언트에는 서비스에 액세스하기 위한 프록시 클래스와 서비스 계약에 대한 정의가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-114">The client contains a definition of the service contract and a proxy class for accessing the service.</span></span> <span data-ttu-id="6c893-115">프록시 코드는 [ServiceModel Metadata 유틸리티 도구 (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)를 사용 하 여 서비스 메타 데이터에서 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-115">The proxy code is generated from the service metadata using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>

<span data-ttu-id="6c893-116">Windows Vista에서 서비스는 WAS (Windows Activation Service)에서 호스팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-116">On Windows Vista, the service is hosted in the Windows Activation Service (WAS).</span></span> <span data-ttu-id="6c893-117">Windows XP 및 Windows Server 2003에서는 인터넷 정보 서비스 (IIS) 및 ASP.NET에서 호스트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-117">On Windows XP and Windows Server 2003, it is hosted by Internet Information Services (IIS) and ASP.NET.</span></span> <span data-ttu-id="6c893-118">IIS 또는 WAS에서 서비스를 호스팅하면 서비스에 처음 액세스할 때 서비스를 자동으로 활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-118">Hosting a service in IIS or WAS allows the service to be activated automatically when it is accessed for the first time.</span></span>

> [!NOTE]
> <span data-ttu-id="6c893-119">IIS 대신 콘솔 응용 프로그램에서 서비스를 호스팅하는 샘플을 사용 하려는 경우 [자체 호스트](self-host.md) 샘플을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6c893-119">If you would prefer to get started with a sample that hosts the service in a console application instead of IIS, see the [Self-Host](self-host.md) sample.</span></span>

<span data-ttu-id="6c893-120">서비스와 클라이언트는 구성 파일 설정에서 액세스 세부 정보를 지정하므로 배포 시에 유연성을 갖게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-120">The service and client specify access details in configuration file settings, which provide flexibility at the time of deployment.</span></span> <span data-ttu-id="6c893-121">주소, 바인딩 및 계약을 지정하는 엔드포인트 정의가 여기에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-121">This includes an endpoint definition that specifies an address, binding, and contract.</span></span> <span data-ttu-id="6c893-122">바인딩은 서비스를 액세스하는 방법에 대한 전송 및 보안 세부 정보를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-122">The binding specifies transport and security details for how the service is to be accessed.</span></span>

<span data-ttu-id="6c893-123">서비스는 해당 메타데이터를 게시하기 위한 런타임 동작을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-123">The service configures a run-time behavior to publish its metadata.</span></span>

<span data-ttu-id="6c893-124">이 서비스는 요청-회신 통신 패턴을 정의하는 계약을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-124">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="6c893-125">계약은 수학 연산(Add, Subtract, Multiply 및 Divide)을 노출시키는 `ICalculator` 인터페이스에 의해 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-125">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="6c893-126">클라이언트에서 지정된 수학 연산을 요청하면 서비스에서 결과로 회신합니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-126">The client makes requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="6c893-127">서비스는 다음 코드에 정의된 `ICalculator` 계약을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-127">The service implements an `ICalculator` contract that is defined in the following code.</span></span>

```vb
' Define a service contract.
    <ServiceContract(Namespace:="http://Microsoft.Samples.GettingStarted")>
     Public Interface ICalculator
        <OperationContract()>
        Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()>
        Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()>
        Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()>
        Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double
    End Interface
```

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    [OperationContract]
    double Subtract(double n1, double n2);
    [OperationContract]
    double Multiply(double n1, double n2);
    [OperationContract]
    double Divide(double n1, double n2);
}
```

<span data-ttu-id="6c893-128">다음 예제 코드와 같이 서비스 구현은 적절한 결과를 계산하여 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-128">The service implementation calculates and returns the appropriate result, as shown in the following example code.</span></span>

```vb
' Service class which implements the service contract.
Public Class CalculatorService
Implements ICalculator
Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Add
Return n1 + n2
End Function

Public Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Subtract
Return n1 - n2
End Function

Public Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Multiply
Return n1 * n2
End Function

Public Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Divide
Return n1 / n2
End Function
End Class
```

```csharp
// Service class that implements the service contract.
public class CalculatorService : ICalculator
{
    public double Add(double n1, double n2)
    {
        return n1 + n2;
    }
    public double Subtract(double n1, double n2)
    {
        return n1 - n2;
    }
    public double Multiply(double n1, double n2)
    {
        return n1 * n2;
    }
    public double Divide(double n1, double n2)
    {
        return n1 / n2;
    }
}
```

<span data-ttu-id="6c893-129">다음 샘플 구성과 같이 서비스에서는 구성 파일(Web.config)을 사용하여 정의하는 서비스와의 통신을 위한 엔드포인트를 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-129">The service exposes an endpoint for communicating with the service, defined using a configuration file (Web.config), as shown in the following sample configuration.</span></span>

```xaml
<services>
    <service
        name="Microsoft.ServiceModel.Samples.CalculatorService"
        behaviorConfiguration="CalculatorServiceBehavior">
        <!-- ICalculator is exposed at the base address provided by
         host: http://localhost/servicemodelsamples/service.svc.  -->
       <endpoint address=""
              binding="wsHttpBinding"
              contract="Microsoft.ServiceModel.Samples.ICalculator" />
       ...
    </service>
</services>
```

<span data-ttu-id="6c893-130">서비스는 IIS 또는 WAS 호스트에서 제공되는 기본 주소에서 엔드포인트를 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-130">The service exposes the endpoint at the base address provided by the IIS or WAS host.</span></span> <span data-ttu-id="6c893-131">바인딩은 표준 <xref:System.ServiceModel.WSHttpBinding>을 사용하여 구성되어 주소 지정 및 보안을 위한 HTTP 통신 및 표준 웹 서비스 프로토콜을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-131">The binding is configured with a standard <xref:System.ServiceModel.WSHttpBinding>, which provides HTTP communication and standard Web service protocols for addressing and security.</span></span> <span data-ttu-id="6c893-132">계약은 서비스에 의해 구현되는 `ICalculator`입니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-132">The contract is the `ICalculator` implemented by the service.</span></span>

<span data-ttu-id="6c893-133">구성 된 대로 `http://localhost/servicemodelsamples/service.svc` 동일한 컴퓨터의 클라이언트에서 서비스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-133">As configured, the service can be accessed at `http://localhost/servicemodelsamples/service.svc` by a client on the same computer.</span></span> <span data-ttu-id="6c893-134">원격 컴퓨터의 클라이언트가 서비스에 액세스하려면 localhost 대신 정규화된 도메인 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-134">For clients on remote computers to access the service, a fully-qualified domain name must be specified instead of localhost.</span></span>

<span data-ttu-id="6c893-135">기본적으로 프레임워크에서는 메타데이터를 노출하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-135">The framework does not expose metadata by default.</span></span> <span data-ttu-id="6c893-136">이와 같이 서비스는를 켜고에서 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> MEX (metadata exchange) 끝점을 노출 `http://localhost/servicemodelsamples/service.svc/mex` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-136">As such, the service turns on the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> and exposes a metadata exchange (MEX) endpoint at `http://localhost/servicemodelsamples/service.svc/mex`.</span></span> <span data-ttu-id="6c893-137">다음 구성에서는 이를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-137">The following configuration demonstrates this.</span></span>

```xaml
<system.serviceModel>
  <services>
    <service
        name="Microsoft.ServiceModel.Samples.CalculatorService"
        behaviorConfiguration="CalculatorServiceBehavior">
      ...
      <!-- the mex endpoint is exposed at
       http://localhost/servicemodelsamples/service.svc/mex -->
      <endpoint address="mex"
                binding="mexHttpBinding"
                contract="IMetadataExchange" />
    </service>
  </services>

  <!--For debugging purposes set the includeExceptionDetailInFaults
   attribute to true-->
  <behaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior">
        <serviceMetadata httpGetEnabled="True"/>
        <serviceDebug includeExceptionDetailInFaults="False" />
      </behavior>
    </serviceBehaviors>
  </behaviors>
</system.serviceModel>
```

<span data-ttu-id="6c893-138">클라이언트는 [ServiceModel Metadata 유틸리티 도구 (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)에 의해 생성 된 클라이언트 클래스를 사용 하 여 지정 된 계약 형식을 사용 하 여 통신 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-138">The client communicates using a given contract type by using a client class that is generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="6c893-139">생성된 이 클라이언트는 generatedClient.cs 또는 generatedClient.vb 파일에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-139">This generated client is contained in the file generatedClient.cs or generatedClient.vb.</span></span> <span data-ttu-id="6c893-140">이 유틸리티는 지정된 서비스에 대한 메타데이터를 검색하고 지정된 계약 형식으로 통신하기 위해 클라이언트 애플리케이션에 사용되는 클라이언트를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-140">This utility retrieves metadata for a given service and generates a client for use by the client application to communicate using a given contract type.</span></span> <span data-ttu-id="6c893-141">업데이트된 메타데이터를 검색하는 데 호스트된 서비스가 사용되므로 클라이언트 코드를 생성하기 위해 해당 서비스를 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-141">The hosted service must be available to generate the client code, because the service is used to retrieve the updated metadata.</span></span>

 <span data-ttu-id="6c893-142">클라이언트 디렉터리의 SDK 명령 프롬프트에서 다음 명령을 실행하여 형식화된 프록시를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-142">Run the following command from the SDK command prompt in the client directory to generate the typed proxy:</span></span>

```console
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs
```

<span data-ttu-id="6c893-143">Visual Basic에서 클라이언트를 생성하려면 SDK 명령 프롬프트에서 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-143">To generate client in Visual Basic type the following from the SDK command prompt:</span></span>

`Svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb`

<span data-ttu-id="6c893-144">생성된 클라이언트를 사용하면 클라이언트에서 적절한 주소와 바인딩을 구성하여 지정된 서비스 엔드포인트에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-144">By using the generated client, the client can access a given service endpoint by configuring the appropriate address and binding.</span></span> <span data-ttu-id="6c893-145">서비스와 마찬가지로 클라이언트는 구성 파일(App.config)을 사용하여 통신할 엔드포인트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-145">Like the service, the client uses a configuration file (App.config) to specify the endpoint with which it wants to communicate.</span></span> <span data-ttu-id="6c893-146">다음 예제와 같이 클라이언트 엔드포인트 구성은 서비스 엔드포인트의 절대 주소, 바인딩 및 계약으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-146">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract, as shown in the following example.</span></span>

```xaml
<client>
     <endpoint
         address="http://localhost/servicemodelsamples/service.svc"
         binding="wsHttpBinding"
         contract=" Microsoft.ServiceModel.Samples.ICalculator" />
</client>
```

<span data-ttu-id="6c893-147">다음 예제 코드와 같이 클라이언트 구현은 클라이언트를 인스턴스화하고 형식화된 인터페이스를 사용하여 서비스와 통신을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-147">The client implementation instantiates the client and uses the typed interface to begin communicating with the service, as shown in the following example code.</span></span>

```vb
' Create a client
Dim client As New CalculatorClient()

' Call the Add service operation.
            Dim value1 = 100.0R
            Dim value2 = 15.99R
            Dim result = client.Add(value1, value2)
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)

' Call the Subtract service operation.
value1 = 145.00R
value2 = 76.54R
result = client.Subtract(value1, value2)
Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result)

' Call the Multiply service operation.
value1 = 9.00R
value2 = 81.25R
result = client.Multiply(value1, value2)
Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result)

' Call the Divide service operation.
value1 = 22.00R
value2 = 7.00R
result = client.Divide(value1, value2)
Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result)

'Closing the client gracefully closes the connection and cleans up resources
```

```csharp
// Create a client.
CalculatorClient client = new CalculatorClient();

// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = client.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

// Call the Subtract service operation.
value1 = 145.00D;
value2 = 76.54D;
result = client.Subtract(value1, value2);
Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);

// Call the Multiply service operation.
value1 = 9.00D;
value2 = 81.25D;
result = client.Multiply(value1, value2);
Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);

// Call the Divide service operation.
value1 = 22.00D;
value2 = 7.00D;
result = client.Divide(value1, value2);
Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);

//Closing the client releases all communication resources.
client.Close();
```

<span data-ttu-id="6c893-148">샘플을 실행하면 작업 요청 및 응답이 클라이언트 콘솔 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-148">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="6c893-149">클라이언트를 종료하려면 클라이언트 창에서 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-149">Press ENTER in the client window to shut down the client.</span></span>

```output
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

<span data-ttu-id="6c893-150">Getting Started 샘플은 서비스와 클라이언트를 만드는 표준 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-150">The Getting Started sample shows the standard way to create a service and client.</span></span> <span data-ttu-id="6c893-151">이 샘플의 다른 [기본](basic-sample.md) 빌드는 특정 제품 기능을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-151">The other [Basic](basic-sample.md) build on this sample to demonstrate specific product features.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6c893-152">샘플을 설치, 빌드 및 실행하려면</span><span class="sxs-lookup"><span data-stu-id="6c893-152">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="6c893-153">[Windows Communication Foundation 샘플에 대 한 일회성 설치 절차](one-time-setup-procedure-for-the-wcf-samples.md)를 수행 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-153">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="6c893-154">C# 또는 Visual Basic .NET 버전의 솔루션을 빌드하려면 [Building the Windows Communication Foundation Samples](building-the-samples.md)의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="6c893-154">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="6c893-155">단일 컴퓨터 또는 다중 컴퓨터 구성에서 샘플을 실행 하려면 [Windows Communication Foundation 샘플 실행](running-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="6c893-155">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6c893-156">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6c893-156">See also</span></span>

- [<span data-ttu-id="6c893-157">방법: 관리형 애플리케이션에서 WCF 서비스 호스트</span><span class="sxs-lookup"><span data-stu-id="6c893-157">How to: Host a WCF Service in a Managed Application</span></span>](../how-to-host-a-wcf-service-in-a-managed-application.md)
- [<span data-ttu-id="6c893-158">방법: IIS에서 WCF 서비스 호스팅</span><span class="sxs-lookup"><span data-stu-id="6c893-158">How to: Host a WCF Service in IIS</span></span>](../feature-details/how-to-host-a-wcf-service-in-iis.md)
