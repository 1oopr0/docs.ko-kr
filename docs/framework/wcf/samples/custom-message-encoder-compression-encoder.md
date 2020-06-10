---
title: '사용자 지정 메시지 인코더: 압축 인코더'
ms.date: 03/30/2017
ms.assetid: 57450b6c-89fe-4b8a-8376-3d794857bfd7
ms.openlocfilehash: db20ec20579d6fcb0ec202920db0d7781b0676df
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600622"
---
# <a name="custom-message-encoder-compression-encoder"></a><span data-ttu-id="2eed1-102">사용자 지정 메시지 인코더: 압축 인코더</span><span class="sxs-lookup"><span data-stu-id="2eed1-102">Custom Message Encoder: Compression Encoder</span></span>

<span data-ttu-id="2eed1-103">이 샘플에서는 WCF (Windows Communication Foundation) 플랫폼을 사용 하 여 사용자 지정 인코더를 구현 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-103">This sample demonstrates how to implement a custom encoder using the Windows Communication Foundation (WCF) platform.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2eed1-104">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-104">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2eed1-105">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="2eed1-105">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="2eed1-106">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2eed1-107">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-107">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`

## <a name="sample-details"></a><span data-ttu-id="2eed1-108">샘플 세부 정보</span><span class="sxs-lookup"><span data-stu-id="2eed1-108">Sample Details</span></span>

<span data-ttu-id="2eed1-109">이 샘플은 클라이언트 콘솔 프로그램(.exe), 자체 호스팅 서비스 콘솔 프로그램(.exe) 및 압축 메시지 인코더 라이브러리(.dll)로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-109">This sample consists of a client console program (.exe), a self-hosted service console program (.exe) and a compression message encoder library (.dll).</span></span> <span data-ttu-id="2eed1-110">이 서비스는 요청-회신 통신 패턴을 정의하는 계약을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-110">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="2eed1-111">이 계약은 기본 문자열 echo 작업(`ISampleServer` 및 `Echo`)을 노출하는 `BigEcho` 인터페이스에 의해 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-111">The contract is defined by the `ISampleServer` interface, which exposes basic string echoing operations (`Echo` and `BigEcho`).</span></span> <span data-ttu-id="2eed1-112">클라이언트가 지정된 작업에 대한 동기적 요청을 만들면 서비스는 이 메시지를 다시 클라이언트에게 보내는 방법으로 회신합니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-112">The client makes synchronous requests to a given operation and the service replies by repeating the message back to the client.</span></span> <span data-ttu-id="2eed1-113">클라이언트와 서비스 동작은 콘솔 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-113">Client and service activity is visible in the console windows.</span></span> <span data-ttu-id="2eed1-114">이 샘플의 목적은 사용자 지정 인코더의 작성 방법과 통신 중 메시지 압축이 미치는 영향을 보여 주는 데 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-114">The intent of this sample is to show how to write a custom encoder and demonstrate the impact of compression of a message on the wire.</span></span> <span data-ttu-id="2eed1-115">압축 메시지 인코더에 계측을 추가하여 메시지 크기, 처리 시간 또는 둘 다를 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-115">You can add instrumentation to the compression message encoder to calculate message size, processing time, or both.</span></span>

> [!NOTE]
> <span data-ttu-id="2eed1-116">.NET Framework 4에서는 서버에서 GZip 또는 Deflate와 같은 알고리즘을 사용 하 여 만든 압축 된 응답을 보내는 경우 WCF 클라이언트에서 자동 압축 풀기를 사용 하도록 설정 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-116">In the .NET Framework 4, automatic decompression has been enabled on a WCF client if the server is sending a compressed response (created with an algorithm such as GZip or Deflate).</span></span> <span data-ttu-id="2eed1-117">서비스가 IIS(인터넷 정보 서버)에 웹 호스팅된 경우 서비스에서 압축된 응답을 보낼 수 있도록 IIS를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-117">If the service is Web-hosted in Internet Information Server (IIS), then IIS can be configured for the service to send a compressed response.</span></span> <span data-ttu-id="2eed1-118">이 샘플은 클라이언트와 서비스 모두에서 압축 및 압축 해제를 수행하거나 서비스가 자체 호스팅되는 경우에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-118">This sample can be used if the requirement is to do compression and decompression on both the client and the service or if the service is self-hosted.</span></span>

<span data-ttu-id="2eed1-119">이 샘플에서는 사용자 지정 메시지 인코더를 빌드하고 WCF 응용 프로그램에 통합 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-119">The sample demonstrates how to build and integrate a custom message encoder into a WCF application.</span></span> <span data-ttu-id="2eed1-120">라이브러리 GZipEncoder.dll은 클라이언트와 서비스 모두와 함께 배포됩니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-120">The library GZipEncoder.dll is deployed with both the client and the service.</span></span> <span data-ttu-id="2eed1-121">또한 이 샘플에서는 메시지 압축이 미치는 영향을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-121">This sample also demonstrates the impact of compressing messages.</span></span> <span data-ttu-id="2eed1-122">GZipEncoder.dll의 코드는 다음 작업을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-122">The code in GZipEncoder.dll demonstrates the following:</span></span>

- <span data-ttu-id="2eed1-123">사용자 지정 인코더 및 인코더 팩터리 빌드</span><span class="sxs-lookup"><span data-stu-id="2eed1-123">Building a custom encoder and encoder factory.</span></span>

- <span data-ttu-id="2eed1-124">사용자 지정 인코더의 바인딩 요소 개발</span><span class="sxs-lookup"><span data-stu-id="2eed1-124">Developing a binding element for a custom encoder.</span></span>

- <span data-ttu-id="2eed1-125">사용자 지정 바인딩 요소 통합에 사용자 지정 바인딩 구성 사용</span><span class="sxs-lookup"><span data-stu-id="2eed1-125">Using the custom binding configuration for integrating custom binding elements.</span></span>

- <span data-ttu-id="2eed1-126">사용자 지정 바인딩 요소의 파일 구성을 허용하는 사용자 지정 구성 처리기 개발</span><span class="sxs-lookup"><span data-stu-id="2eed1-126">Developing a custom configuration handler to allow file configuration of a custom binding element.</span></span>

<span data-ttu-id="2eed1-127">앞에서 설명한 대로 사용자 지정 인코더에는 몇 개의 계층이 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-127">As indicated previously, there are several layers that are implemented in a custom encoder.</span></span> <span data-ttu-id="2eed1-128">이 각 계층 간의 관계를 더 명확하게 보여 주기 위해 서비스 시작을 위한 간단한 이벤트 순서는 다음 목록과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-128">To better illustrate the relationship between each of these layers, a simplified order of events for service start-up is in the following list:</span></span>

1. <span data-ttu-id="2eed1-129">서버가 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-129">The server starts.</span></span>

2. <span data-ttu-id="2eed1-130">구성 정보를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-130">The configuration information is read.</span></span>

    1. <span data-ttu-id="2eed1-131">서버 구성이 사용자 지정 구성 처리기를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-131">The service configuration registers the custom configuration handler.</span></span>

    2. <span data-ttu-id="2eed1-132">서버 호스트가 만들어지고 열립니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-132">The service host is created and opened.</span></span>

    3. <span data-ttu-id="2eed1-133">사용자 지정 구성 요소가 사용자 지정 바인딩 요소를 만들어 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-133">The custom configuration element creates and returns the custom binding element.</span></span>

    4. <span data-ttu-id="2eed1-134">사용자 지정 바인딩 요소가 메시지 인코더 팩터리를 만들어 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-134">The custom binding element creates and returns a message encoder factory.</span></span>

3. <span data-ttu-id="2eed1-135">메시지가 수신됩니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-135">A message is received.</span></span>

4. <span data-ttu-id="2eed1-136">메시지 인코더 팩터리는 메시지를 읽고 응답을 기록하기 위한 메시지 인코더를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-136">The message encoder factory returns a message encoder for reading in the message and writing out the response.</span></span>

5. <span data-ttu-id="2eed1-137">인코더 계층이 클래스 팩터리로 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-137">The encoder layer is implemented as a class factory.</span></span> <span data-ttu-id="2eed1-138">인코더 클래스 팩터리만 사용자 지정 인코더에 대해 공개적으로 노출되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-138">Only the encoder class factory must be publicly exposed for the custom encoder.</span></span> <span data-ttu-id="2eed1-139"><xref:System.ServiceModel.ServiceHost> 또는 <xref:System.ServiceModel.ChannelFactory%601> 개체가 만들어질 때 바인딩 요소가 팩터리 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-139">The factory object is returned by the binding element when the <xref:System.ServiceModel.ServiceHost> or <xref:System.ServiceModel.ChannelFactory%601> object is created.</span></span> <span data-ttu-id="2eed1-140">메시지 인코더는 버퍼링 모드 또는 스트리밍 모드에서 작동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-140">Message encoders can operate in a buffered or streaming mode.</span></span> <span data-ttu-id="2eed1-141">이 샘플에서는 버퍼링 모드와 스트리밍 모드를 모두 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-141">This sample demonstrates both buffered mode and streaming mode.</span></span>

<span data-ttu-id="2eed1-142">각 모드에 대해 추상 `ReadMessage` 클래스에 관련 `WriteMessage` 및 `MessageEncoder` 메서드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-142">For each mode there is an accompanying `ReadMessage` and `WriteMessage` method on the abstract `MessageEncoder` class.</span></span> <span data-ttu-id="2eed1-143">인코딩 작업 중 대부분은 이 메서드에서 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-143">A majority of the encoding work takes place in these methods.</span></span> <span data-ttu-id="2eed1-144">이 샘플은 기존 텍스트 및 이진 메시지 인코더를 래핑합니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-144">The sample wraps the existing text and binary message encoders.</span></span> <span data-ttu-id="2eed1-145">따라서 샘플에서 메시지 연결 표시의 읽기 및 쓰기를 내부 인코더로 위임할 수 있고 압축 인코더가 그 결과를 압축하거나 압축을 풀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-145">This allows the sample to delegate the reading and writing of the wire representation of messages to the inner encoder and allows the compression encoder to compress or decompress the results.</span></span> <span data-ttu-id="2eed1-146">메시지 인코딩에 대 한 파이프라인이 없으므로 WCF에서 여러 인코더를 사용 하는 유일한 모델은이 모델입니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-146">Because there is no pipeline for message encoding, this is the only model for using multiple encoders in WCF.</span></span> <span data-ttu-id="2eed1-147">메시지의 압축을 풀었으면 결과 메시지는 채널 스택에서 처리하도록 스택을 따라 위로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-147">Once the message has been decompressed, the resulting message is passed up the stack for the channel stack to handle.</span></span> <span data-ttu-id="2eed1-148">압축 과정에서 압축된 결과 메시지는 제공된 스트림에 직접 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-148">During compression, the resulting compressed message is written directly to the stream provided.</span></span>

<span data-ttu-id="2eed1-149">이 샘플에서는 `CompressBuffer` 클래스를 사용하기 위해 도우미 메서드(`DecompressBuffer` 및 `GZipStream`)를 사용하여 버퍼에서 스트림으로의 변환을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-149">This sample uses helper methods (`CompressBuffer` and `DecompressBuffer`) to perform conversion from buffers to streams to use the `GZipStream` class.</span></span>

<span data-ttu-id="2eed1-150">버퍼링된 `ReadMessage` 및 `WriteMessage` 클래스는 `BufferManager` 클래스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-150">The buffered `ReadMessage` and `WriteMessage` classes make use of the `BufferManager` class.</span></span> <span data-ttu-id="2eed1-151">인코더는 인코더 팩터리를 통해서만 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-151">The encoder is accessible only through the encoder factory.</span></span> <span data-ttu-id="2eed1-152">추상 `MessageEncoderFactory` 클래스는 현재 인코더에 액세스하기 위해 `Encoder`라는 이름의 속성을, 세션을 지원하는 인코더를 만들기 위해 `CreateSessionEncoder`라는 이름의 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-152">The abstract `MessageEncoderFactory` class provides a property named `Encoder` for accessing the current encoder and a method named `CreateSessionEncoder` for creating an encoder that supports sessions.</span></span> <span data-ttu-id="2eed1-153">이러한 인코더는 채널이 세션을 지원하는 시나리오에서 사용 가능하며 순서가 지정되었고 신뢰할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-153">Such an encoder can be used in the scenario where the channel supports sessions, is ordered and is reliable.</span></span> <span data-ttu-id="2eed1-154">이 시나리오에서는 연결 중에 기록된 데이터의 세션별로 최적화를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-154">This scenario allows for optimization in each session of the data written to the wire.</span></span> <span data-ttu-id="2eed1-155">이를 원치 않을 경우 기본 메서드를 오버로드해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-155">If this is not desired, the base method should not be overloaded.</span></span> <span data-ttu-id="2eed1-156">`Encoder` 속성은 세션 없는 인코더에 액세스하기 위한 메커니즘을 제공하며 `CreateSessionEncoder` 메서드의 기본 구현은 속성의 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-156">The `Encoder` property provides a mechanism for accessing the session-less encoder and the default implementation of the `CreateSessionEncoder` method returns the value of the property.</span></span> <span data-ttu-id="2eed1-157">이 샘플에서는 압축을 제공하기 위해 기존 인코더를 래핑하므로 `MessageEncoderFactory` 구현은 내부 인코더 팩터리를 나타내는 `MessageEncoderFactory`를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-157">Because the sample wraps an existing encoder to provide compression, the `MessageEncoderFactory` implementation accepts a `MessageEncoderFactory` that represents the inner encoder factory.</span></span>

<span data-ttu-id="2eed1-158">이제 인코더 및 인코더 팩터리가 정의 되었으므로 WCF 클라이언트 및 서비스에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-158">Now that the encoder and encoder factory are defined, they can be used with a WCF client and service.</span></span> <span data-ttu-id="2eed1-159">그러나 이 인코더가 채널 스택에 추가되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-159">However, these encoders must be added to the channel stack.</span></span> <span data-ttu-id="2eed1-160"><xref:System.ServiceModel.ServiceHost> 및 <xref:System.ServiceModel.ChannelFactory%601> 클래스로부터 클래스를 파생하고 `OnInitialize` 메서드를 재정의하여 이 인코더 팩터리를 수동으로 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-160">You can derive classes from the <xref:System.ServiceModel.ServiceHost> and <xref:System.ServiceModel.ChannelFactory%601> classes and override the `OnInitialize` methods to add this encoder factory manually.</span></span> <span data-ttu-id="2eed1-161">또한 사용자 지정 바인딩 요소를 통해 인코더 팩터리를 노출할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-161">You can also expose the encoder factory through a custom binding element.</span></span>

<span data-ttu-id="2eed1-162">새 사용자 지정 바인딩 요소를 만들려면 <xref:System.ServiceModel.Channels.BindingElement> 클래스로부터 클래스를 파생합니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-162">To create a new custom binding element, derive a class from the <xref:System.ServiceModel.Channels.BindingElement> class.</span></span> <span data-ttu-id="2eed1-163">그러나 바인딩 요소에는 몇 가지 형식이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-163">There are, however, several types of binding elements.</span></span> <span data-ttu-id="2eed1-164">사용자 지정 바인딩 요소가 메시지 인코딩 바인딩 요소로 인식되기 위해서는 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>도 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-164">To ensure that the custom binding element is recognized as a message encoding binding element, you also must implement the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.</span></span> <span data-ttu-id="2eed1-165"><xref:System.ServiceModel.Channels.MessageEncodingBindingElement>는 새 메시지 인코더를 만들기 위한 메서드 팩터리(`CreateMessageEncoderFactory`)를 노출하며 이는 일치하는 메시지 인코더 팩터리의 인스턴스를 반환하기 위해 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-165">The <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> exposes a method for creating a new message encoder factory (`CreateMessageEncoderFactory`), which is implemented to return an instance of the matching message encoder factory.</span></span> <span data-ttu-id="2eed1-166">또한 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>는 주소 지정 버전을 나타내는 속성을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-166">Additionally, the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> has a property to indicate the addressing version.</span></span> <span data-ttu-id="2eed1-167">이 샘플에서 기존 인코더를 래핑하기 때문에 샘플 구현 시 기존 인코더 바인딩 요소도 래핑하며 내부 인코더 바인딩 요소를 생성자의 매개 변수로 받아 어떤 속성을 통해 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-167">Because this sample wraps the existing encoders, the sample implementation also wraps the existing encoder binding elements and takes an inner encoder binding element as a parameter to the constructor and exposes it through a property.</span></span> <span data-ttu-id="2eed1-168">다음 샘플 코드에서는 `GZipMessageEncodingBindingElement` 클래스의 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-168">The following sample code shows the implementation of the `GZipMessageEncodingBindingElement` class.</span></span>

```csharp
public sealed class GZipMessageEncodingBindingElement
                        : MessageEncodingBindingElement //BindingElement
                        , IPolicyExportExtension
{

    //We use an inner binding element to store information
    //required for the inner encoder.
    MessageEncodingBindingElement innerBindingElement;

        //By default, use the default text encoder as the inner encoder.
        public GZipMessageEncodingBindingElement()
            : this(new TextMessageEncodingBindingElement()) { }

    public GZipMessageEncodingBindingElement(MessageEncodingBindingElement messageEncoderBindingElement)
    {
        this.innerBindingElement = messageEncoderBindingElement;
    }

    public MessageEncodingBindingElement InnerMessageEncodingBindingElement
    {
        get { return innerBindingElement; }
        set { innerBindingElement = value; }
    }

    //Main entry point into the encoder binding element.
    // Called by WCF to get the factory that creates the
    //message encoder.
    public override MessageEncoderFactory CreateMessageEncoderFactory()
    {
        return new
GZipMessageEncoderFactory(innerBindingElement.CreateMessageEncoderFactory());
    }

    public override MessageVersion MessageVersion
    {
        get { return innerBindingElement.MessageVersion; }
        set { innerBindingElement.MessageVersion = value; }
    }

    public override BindingElement Clone()
    {
        return new
        GZipMessageEncodingBindingElement(this.innerBindingElement);
    }

    public override T GetProperty<T>(BindingContext context)
    {
        if (typeof(T) == typeof(XmlDictionaryReaderQuotas))
        {
            return innerBindingElement.GetProperty<T>(context);
        }
        else
        {
            return base.GetProperty<T>(context);
        }
    }

    public override IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)
    {
        if (context == null)
            throw new ArgumentNullException("context");

        context.BindingParameters.Add(this);
        return context.BuildInnerChannelFactory<TChannel>();
    }

    public override IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)
    {
        if (context == null)
            throw new ArgumentNullException("context");

        context.BindingParameters.Add(this);
        return context.BuildInnerChannelListener<TChannel>();
    }

    public override bool CanBuildChannelListener<TChannel>(BindingContext context)
    {
        if (context == null)
            throw new ArgumentNullException("context");

        context.BindingParameters.Add(this);
        return context.CanBuildInnerChannelListener<TChannel>();
    }

    void IPolicyExportExtension.ExportPolicy(MetadataExporter exporter, PolicyConversionContext policyContext)
    {
        if (policyContext == null)
        {
            throw new ArgumentNullException("policyContext");
        }
       XmlDocument document = new XmlDocument();
       policyContext.GetBindingAssertions().Add(document.CreateElement(
            GZipMessageEncodingPolicyConstants.GZipEncodingPrefix,
            GZipMessageEncodingPolicyConstants.GZipEncodingName,
            GZipMessageEncodingPolicyConstants.GZipEncodingNamespace));
    }
}
```

<span data-ttu-id="2eed1-169">`GZipMessageEncodingBindingElement` 클래스가 `IPolicyExportExtension` 인터페이스를 구현하므로 다음 예제에서와 같이 이 바인딩 요소는 메타데이터에 정책으로 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-169">Note that `GZipMessageEncodingBindingElement` class implements the `IPolicyExportExtension` interface, so that this binding element can be exported as a policy in metadata, as shown in the following example.</span></span>

```xml
<wsp:Policy wsu:Id="BufferedHttpSampleServer_ISampleServer_policy">
    <wsp:ExactlyOne>
      <wsp:All>
        <gzip:text xmlns:gzip=
        "http://schemas.microsoft.com/ws/06/2004/mspolicy/netgzip1" />
       <wsaw:UsingAddressing />
     </wsp:All>
   </wsp:ExactlyOne>
</wsp:Policy>
```

<span data-ttu-id="2eed1-170">`GZipMessageEncodingBindingElementImporter` 클래스는 `IPolicyImportExtension` 인터페이스를 구현하고 이 클래스는 `GZipMessageEncodingBindingElement`를 위한 정책을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-170">The `GZipMessageEncodingBindingElementImporter` class implements the `IPolicyImportExtension` interface, this class imports policy for `GZipMessageEncodingBindingElement`.</span></span> <span data-ttu-id="2eed1-171">Svcutil.exe 도구는 정책을 구성 파일로 가져올 때 사용할 수 있습니다. `GZipMessageEncodingBindingElement`를 처리하려면 Svcutil.exe.config에 다음을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-171">Svcutil.exe tool can be used to import policies to the configuration file, to handle `GZipMessageEncodingBindingElement`, the following should be added to Svcutil.exe.config.</span></span>

```xml
<configuration>
  <system.serviceModel>
    <extensions>
      <bindingElementExtensions>
        <add name="gzipMessageEncoding"
          type=
            "Microsoft.ServiceModel.Samples.GZipMessageEncodingElement, GZipEncoder, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
      </bindingElementExtensions>
    </extensions>
    <client>
      <metadata>
        <policyImporters>
          <remove type=
"System.ServiceModel.Channels.MessageEncodingBindingElementImporter, System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
          <extension type=
"Microsoft.ServiceModel.Samples.GZipMessageEncodingBindingElementImporter, GZipEncoder, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
        </policyImporters>
      </metadata>
    </client>
  </system.serviceModel>
</configuration>
```

<span data-ttu-id="2eed1-172">이제 압축 인코더에 일치하는 바인딩 요소가 있으므로 프로그래밍 방식으로 이를 서비스 또는 클라이언트에 후크할 수 있습니다. 다음 샘플 코드에서와 같이 새 사용자 지정 바인딩 개체를 생성하고 사용자 지정 바인딩 요소를 개체에 추가하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-172">Now that there is a matching binding element for the compression encoder, it can be programmatically hooked into the service or client by constructing a new custom binding object and adding the custom binding element to it, as shown in the following sample code.</span></span>

```csharp
ICollection<BindingElement> bindingElements = new List<BindingElement>();
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();
GZipMessageEncodingBindingElement compBindingElement = new GZipMessageEncodingBindingElement ();
bindingElements.Add(compBindingElement);
bindingElements.Add(httpBindingElement);
CustomBinding binding = new CustomBinding(bindingElements);
binding.Name = "SampleBinding";
binding.Namespace = "http://tempuri.org/bindings";
```

<span data-ttu-id="2eed1-173">대부분의 사용자 시나리오에서는 이 정도로 충분할 수 있지만 서비스가 웹 호스팅되는 경우 파일 구성 지원이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-173">While this may be sufficient for the majority of user scenarios, supporting a file configuration is critical if a service is to be Web-hosted.</span></span> <span data-ttu-id="2eed1-174">웹 호스팅되는 시나리오를 지원하려면 파일에서 사용자 지정 바인딩 요소를 구성할 수 있도록 사용자 지정 구성 처리기를 개발해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-174">To support the Web-hosted scenario, you must develop a custom configuration handler to allow a custom binding element to be configurable in a file.</span></span>

<span data-ttu-id="2eed1-175">구성 시스템 위에 바인딩 요소에 대 한 구성 처리기를 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-175">You can build a configuration handler for the binding element on top of the configuration system.</span></span> <span data-ttu-id="2eed1-176">바인딩 요소의 구성 처리기는 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> 클래스에서 파생되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-176">The configuration handler for the binding element must derive from the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> class.</span></span> <span data-ttu-id="2eed1-177">는 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.BindingElementType?displayProperty=nameWithType> 이 섹션에 대해 만들 바인딩 요소의 형식을 구성 시스템에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-177">The <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.BindingElementType?displayProperty=nameWithType> informs the configuration system of the type of binding element to create for this section.</span></span> <span data-ttu-id="2eed1-178">설정 가능한 모든 `BindingElement`의 요소는 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> 파생 클래스에서 속성으로 노출되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-178">All aspects of the `BindingElement` that can be set should be exposed as properties in the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> derived class.</span></span> <span data-ttu-id="2eed1-179">는 <xref:System.Configuration.ConfigurationPropertyAttribute> 구성 요소 특성을 속성에 매핑하고 특성이 누락 된 경우 기본값을 설정 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-179">The <xref:System.Configuration.ConfigurationPropertyAttribute> assists in mapping the configuration element attributes to the properties and setting default values if attributes are missing.</span></span> <span data-ttu-id="2eed1-180">구성으로부터 값이 로드되어 속성에 적용된 후 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A?displayProperty=nameWithType> 메서드가 호출되며 이 메서드는 속성을 바인딩 요소의 구체적인 인스턴스로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-180">After the values from configuration are loaded and applied to the properties, the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A?displayProperty=nameWithType> method is called, which converts the properties into a concrete instance of a binding element.</span></span> <span data-ttu-id="2eed1-181"><xref:System.ServiceModel.Configuration.BindingElementExtensionElement.ApplyConfiguration%2A?displayProperty=nameWithType>메서드는 파생 클래스의 속성을 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> 새로 만든 바인딩 요소에 설정 될 값으로 변환 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-181">The <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.ApplyConfiguration%2A?displayProperty=nameWithType> method is used to convert the properties on the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> derived class into the values to be set on the newly created binding element.</span></span>

<span data-ttu-id="2eed1-182">다음 샘플 코드에서는 `GZipMessageEncodingElement`의 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-182">The following sample code shows the implementation of the `GZipMessageEncodingElement`.</span></span>

```csharp
public class GZipMessageEncodingElement : BindingElementExtensionElement
{
    public GZipMessageEncodingElement()
    {
    }

//Called by the WCF to discover the type of binding element this
//config section enables
    public override Type BindingElementType
    {
        get { return typeof(GZipMessageEncodingBindingElement); }
    }

    //The only property we need to configure for our binding element is
    //the type of inner encoder to use. Here, we support text and
    //binary.
    [ConfigurationProperty("innerMessageEncoding",
                         DefaultValue = "textMessageEncoding")]
    public string InnerMessageEncoding
    {
        get { return (string)base["innerMessageEncoding"]; }
        set { base["innerMessageEncoding"] = value; }
    }

    //Called by the WCF to apply the configuration settings (the
    //property above) to the binding element
    public override void ApplyConfiguration(BindingElement bindingElement)
    {
        GZipMessageEncodingBindingElement binding =
                (GZipMessageEncodingBindingElement)bindingElement;
        PropertyInformationCollection propertyInfo =
                    this.ElementInformation.Properties;
        if (propertyInfo["innerMessageEncoding"].ValueOrigin !=
                                     PropertyValueOrigin.Default)
        {
            switch (this.InnerMessageEncoding)
            {
                case "textMessageEncoding":
                    binding.InnerMessageEncodingBindingElement =
                      new TextMessageEncodingBindingElement();
                    break;
                case "binaryMessageEncoding":
                    binding.InnerMessageEncodingBindingElement =
                         new BinaryMessageEncodingBindingElement();
                    break;
            }
        }
    }

    //Called by the WCF to create the binding element
    protected override BindingElement CreateBindingElement()
    {
        GZipMessageEncodingBindingElement bindingElement =
                new GZipMessageEncodingBindingElement();
        this.ApplyConfiguration(bindingElement);
        return bindingElement;
    }
}
```

<span data-ttu-id="2eed1-183">이 구성 처리기는 서비스나 클라이언트의 App.config 또는 Web.config에 있는 다음 표현에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-183">This configuration handler maps to the following representation in the App.config or Web.config for the service or client.</span></span>

```xml
<gzipMessageEncoding innerMessageEncoding="textMessageEncoding" />
```

<span data-ttu-id="2eed1-184">이 구성 처리기를 사용 하려면 [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) 다음 샘플 구성에 표시 된 것 처럼 요소 내에 등록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-184">To use this configuration handler, it must be registered within the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element, as shown in the following sample configuration.</span></span>

```xml
<extensions>
    <bindingElementExtensions>
       <add
           name="gzipMessageEncoding"
           type=
           "Microsoft.ServiceModel.Samples.GZipMessageEncodingElement,
           GZipEncoder, Version=1.0.0.0, Culture=neutral,
           PublicKeyToken=null" />
      </bindingElementExtensions>
</extensions>
```

<span data-ttu-id="2eed1-185">서버를 실행하면 작업 요청 및 응답이 콘솔 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-185">When you run the server, the operation requests and responses are displayed in the console window.</span></span> <span data-ttu-id="2eed1-186">서버를 종료하려면 창에서 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-186">Press ENTER in the window to shut down the server.</span></span>

```console
Press Enter key to Exit.

        Server Echo(string input) called:
        Client message: Simple hello

        Server BigEcho(string[] input) called:
        64 client messages
```

<span data-ttu-id="2eed1-187">클라이언트를 실행하면 작업 요청 및 응답이 콘솔 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-187">When you run the client, the operation requests and responses are displayed in the console window.</span></span> <span data-ttu-id="2eed1-188">클라이언트를 종료하려면 클라이언트 창에서 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-188">Press ENTER in the client window to shut down the client.</span></span>

```console
Calling Echo(string):
Server responds: Simple hello Simple hello

Calling BigEcho(string[]):
Server responds: Hello 0

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2eed1-189">샘플을 설치, 빌드 및 실행하려면</span><span class="sxs-lookup"><span data-stu-id="2eed1-189">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="2eed1-190">다음 명령을 사용 하 여 ASP.NET 4.0을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-190">Install ASP.NET 4.0 using the following command:</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="2eed1-191">[Windows Communication Foundation 샘플에 대 한 일회성 설치 절차](one-time-setup-procedure-for-the-wcf-samples.md)를 수행 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-191">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="2eed1-192">솔루션을 빌드하려면 [Windows Communication Foundation 샘플 빌드](building-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="2eed1-192">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="2eed1-193">단일 컴퓨터 또는 다중 컴퓨터 구성에서 샘플을 실행 하려면 [Windows Communication Foundation 샘플 실행](running-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="2eed1-193">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2eed1-194">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-194">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2eed1-195">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="2eed1-195">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="2eed1-196">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-196">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2eed1-197">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2eed1-197">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`
