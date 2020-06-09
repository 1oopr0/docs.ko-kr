---
title: '방법: 구성에서 서비스 엔드포인트 만들기'
ms.date: 06/16/2016
ms.assetid: f474e25d-2a27-4f31-84c5-395c442b8e70
ms.openlocfilehash: 56b29da0c147eb9e73a08e2875e33e384da729ed
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598920"
---
# <a name="how-to-create-a-service-endpoint-in-configuration"></a><span data-ttu-id="5ee62-102">방법: 구성에서 서비스 엔드포인트 만들기</span><span class="sxs-lookup"><span data-stu-id="5ee62-102">How to: Create a Service Endpoint in Configuration</span></span>
<span data-ttu-id="5ee62-103">끝점은 WCF (Windows Communication Foundation) 서비스에서 제공 하는 기능에 대 한 액세스를 클라이언트에 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ee62-103">Endpoints provide clients with access to the functionality a Windows Communication Foundation (WCF) service offers.</span></span> <span data-ttu-id="5ee62-104">상대 및 절대 엔드포인트 주소 조합을 사용하여 엔드포인트를 하나 이상 정의할 수 있으며, 서비스 엔드포인트를 정의하지 않는 경우에는 런타임이 기본적으로 일부 엔드포인트를 자동으로 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5ee62-104">You can define one or more endpoints for a service by using a combination of relative and absolute endpoint addresses, or if you do not define any service endpoints, the runtime provides some by default for you.</span></span> <span data-ttu-id="5ee62-105">이 항목에서는 상대 주소와 절대 주소를 모두 포함하는 구성 파일을 사용해 엔드포인트를 추가하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5ee62-105">This topic shows how to add endpoints using a configuration file that contain both relative and absolute addresses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ee62-106">예제</span><span class="sxs-lookup"><span data-stu-id="5ee62-106">Example</span></span>  
 <span data-ttu-id="5ee62-107">다음 서비스 구성에는 기본 주소와 5개의 엔드포인트가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ee62-107">The following service configuration specifies a base address and five endpoints.</span></span>  
  
```xml  
<configuration>  
  
  <appSettings>  
    <!-- use appSetting to configure base address provided by host -->  
    <add key="baseAddress" value="http://localhost:8000/servicemodelsamples/service" />  
  </appSettings>  
  
  <system.serviceModel>  
    <services>  
    <!-- This section is optional with the default configuration introduced in .NET Framework 4. -->  
      <service name="Microsoft.ServiceModel.Samples.CalculatorService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
          </baseAddresses>  
        </host>  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <endpoint address="/test"  
                  binding="wsHttpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <endpoint address="http://localhost:8001/hello/servicemodelsamples"  
                  binding="wsHttpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
                  binding="netTcpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is another relative address exposed at   
             http://localhost:8000/ServiceModelSamples/service/mex -->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="5ee62-108">예제</span><span class="sxs-lookup"><span data-stu-id="5ee62-108">Example</span></span>  
 <span data-ttu-id="5ee62-109">기본 주소는 다음 샘플에서처럼 service/host/baseAddresses 아래 `add` 요소를 사용하여 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5ee62-109">The base address is specified using the `add` element, under service/host/baseAddresses, as shown in the following sample.</span></span>  
  
```xml  
<service
    name="Microsoft.ServiceModel.Samples.CalculatorService">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
```  
  
## <a name="example"></a><span data-ttu-id="5ee62-110">예제</span><span class="sxs-lookup"><span data-stu-id="5ee62-110">Example</span></span>  
 <span data-ttu-id="5ee62-111">다음 샘플에서처럼 첫 번째 엔드포인트 정의는 엔드포인트 주소가 기본 주소와 URI(Uniform Resource Identifier) 컴퍼지션 다음에 오는 상대 주소의 조합인 상대 주소를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5ee62-111">The first endpoint definition shown in the following sample specifies a relative address, which means the endpoint address is a combination of the base address and the relative address following the rules of Uniform Resource Identifier (URI) composition.</span></span> <span data-ttu-id="5ee62-112">상대 주소가 비어 있으므로("") 엔드포인트 주소는 기본 주소와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="5ee62-112">The relative address is empty (""), so the endpoint address is the same as the base address.</span></span> <span data-ttu-id="5ee62-113">실제 끝점 주소는 `http://localhost:8000/servicemodelsamples/service` 입니다.</span><span class="sxs-lookup"><span data-stu-id="5ee62-113">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service`.</span></span>  
  
```xml  
<endpoint address=""
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="5ee62-114">예제</span><span class="sxs-lookup"><span data-stu-id="5ee62-114">Example</span></span>  
 <span data-ttu-id="5ee62-115">두 번째 엔드포인트 정의도 다음 샘플 구성에서처럼 상대 주소를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5ee62-115">The second endpoint definition also specifies a relative address, as shown in the following sample configuration.</span></span> <span data-ttu-id="5ee62-116">상대 주소 "test"가 기본 주소에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ee62-116">The relative address, "test", is appended to the base address.</span></span> <span data-ttu-id="5ee62-117">실제 끝점 주소는 `http://localhost:8000/servicemodelsamples/service/test` 입니다.</span><span class="sxs-lookup"><span data-stu-id="5ee62-117">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service/test`.</span></span>  
  
```xml  
<endpoint address="/test"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="5ee62-118">예제</span><span class="sxs-lookup"><span data-stu-id="5ee62-118">Example</span></span>  
 <span data-ttu-id="5ee62-119">세 번째 엔드포인트 정의는 다음 샘플 구성에서처럼 절대 주소를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5ee62-119">The third endpoint definition specifies an absolute address, as shown in the following sample configuration.</span></span> <span data-ttu-id="5ee62-120">주소에서 기본 주소는 아무런 역할도 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5ee62-120">The base address plays no role in the address.</span></span> <span data-ttu-id="5ee62-121">실제 끝점 주소는 `http://localhost:8001/hello/servicemodelsamples` 입니다.</span><span class="sxs-lookup"><span data-stu-id="5ee62-121">The actual endpoint address is `http://localhost:8001/hello/servicemodelsamples`.</span></span>  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="5ee62-122">예제</span><span class="sxs-lookup"><span data-stu-id="5ee62-122">Example</span></span>  
 <span data-ttu-id="5ee62-123">네 번째 엔드포인트 주소는 절대 주소 및 다른 전송(TCP)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5ee62-123">The fourth endpoint address specifies an absolute address and a different transport—TCP.</span></span> <span data-ttu-id="5ee62-124">주소에서 기본 주소는 아무런 역할도 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5ee62-124">The base address plays no role in the address.</span></span> <span data-ttu-id="5ee62-125">실제 엔드포인트 주소는 net.tcp://localhost:9000/servicemodelsamples/service입니다.</span><span class="sxs-lookup"><span data-stu-id="5ee62-125">The actual endpoint address is net.tcp://localhost:9000/servicemodelsamples/service.</span></span>  
  
```xml  
<endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
    binding="netTcpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="5ee62-126">예제</span><span class="sxs-lookup"><span data-stu-id="5ee62-126">Example</span></span>  
 <span data-ttu-id="5ee62-127">런타임에서 제공하는 기본 엔드포인트를 사용하려면 코드나 구성 파일에 서비스 엔드포인트를 지정하지 않으면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ee62-127">To use the default endpoints provided by the runtime, do not specify any service endpoints in either the code or the configuration file.</span></span> <span data-ttu-id="5ee62-128">이 예제에서는 서비스를 열 때 런타임이 기본 엔드포인트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5ee62-128">In this example, the runtime creates the default endpoints when the service is opened.</span></span> <span data-ttu-id="5ee62-129">기본 엔드포인트, 바인딩 및 동작에 대한 자세한 내용은 [단순화된 구성](../simplified-configuration.md) 및 [WCF 서비스를 위한 단순화된 구성](../samples/simplified-configuration-for-wcf-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5ee62-129">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../simplified-configuration.md) and [Simplified Configuration for WCF Services](../samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
```xml  
<configuration>  
  
  <appSettings>  
    <!-- use appSetting to configure base address provided by host -->  
    <add key="baseAddress" value="http://localhost:8000/servicemodelsamples/service" />  
  </appSettings>  
  
  <system.serviceModel>  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
  
</configuration>  
```
