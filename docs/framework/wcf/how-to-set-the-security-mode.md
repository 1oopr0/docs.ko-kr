---
title: '방법: 보안 모드 설정'
description: 대부분의 미리 정의 된 바인딩에서 전송, 메시지 및 TransportWithMessageCredential의 세 가지 일반적인 WCF 보안 모드를 설정 하는 방법에 대해 알아봅니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Mode property
- WCF, security mode
- WCF, security
ms.assetid: 6e01dd9f-b5dd-4474-b24c-06e124de4ff7
ms.openlocfilehash: 2f834e1930b7676592f6cbc29a577424d75ebc01
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244545"
---
# <a name="how-to-set-the-security-mode"></a><span data-ttu-id="11a4f-103">방법: 보안 모드 설정</span><span class="sxs-lookup"><span data-stu-id="11a4f-103">How to: Set the Security Mode</span></span>

<span data-ttu-id="11a4f-104">WCF (Windows Communication Foundation) 보안에는 대부분의 미리 정의 된 바인딩 (전송, 메시지 및 "메시지 자격 증명을 사용한 전송")에서 발견 되는 세 가지 일반적인 보안 모드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11a4f-104">Windows Communication Foundation (WCF) security has three common security modes that are found on most predefined bindings: transport, message, and "transport with message credential."</span></span> <span data-ttu-id="11a4f-105">두 개의 추가 모드는 두 바인딩에만 해당됩니다. 즉, "전송-자격 증명만" 모드는 <xref:System.ServiceModel.BasicHttpBinding>에서 사용되고, "모두" 모드는 <xref:System.ServiceModel.NetMsmqBinding>에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="11a4f-105">Two additional modes are specific to two bindings: the "transport-credential only" mode found on the <xref:System.ServiceModel.BasicHttpBinding>, and the "Both" mode, found on the <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="11a4f-106">그러나 이 항목에서는 세 가지 일반 보안 모드(<xref:System.ServiceModel.SecurityMode.Transport>, <xref:System.ServiceModel.SecurityMode.Message>, <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>)에 대해 중점적으로 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="11a4f-106">However, this topic concentrates on the three common security modes: <xref:System.ServiceModel.SecurityMode.Transport>, <xref:System.ServiceModel.SecurityMode.Message>, and <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>

<span data-ttu-id="11a4f-107">모든 미리 정의된 바인딩이 이러한 모드를 모두 지원하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="11a4f-107">Note that not every predefined binding supports all of these modes.</span></span> <span data-ttu-id="11a4f-108">이 항목에서는 <xref:System.ServiceModel.WSHttpBinding> 및 <xref:System.ServiceModel.NetTcpBinding> 클래스를 사용하여 모드를 설정하고 프로그래밍 방식과 구성을 통한 모드 설정 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="11a4f-108">This topic sets the mode with the <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding> classes and demonstrates how to set the mode both programmatically and through configuration.</span></span>

<span data-ttu-id="11a4f-109">자세한 내용은 WCF 보안, [보안 개요](./feature-details/security-overview.md), [서비스](securing-services.md)보안 및 [서비스 및 클라이언트 보안](./feature-details/securing-services-and-clients.md)설정을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="11a4f-109">For more information, see WCF security, see [Security Overview](./feature-details/security-overview.md), [Securing Services](securing-services.md), and [Securing Services and Clients](./feature-details/securing-services-and-clients.md).</span></span> <span data-ttu-id="11a4f-110">전송 모드 및 메시지에 대 한 자세한 내용은 [전송 보안](./feature-details/transport-security.md) 및 [메시지 보안](./feature-details/message-security-in-wcf.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="11a4f-110">For more information about transport mode and message, see [Transport Security](./feature-details/transport-security.md) and [Message Security](./feature-details/message-security-in-wcf.md).</span></span>

## <a name="to-set-the-security-mode-in-code"></a><span data-ttu-id="11a4f-111">코드에서 보안 모드를 설정하려면</span><span class="sxs-lookup"><span data-stu-id="11a4f-111">To set the security mode in code</span></span>

1. <span data-ttu-id="11a4f-112">사용 중인 바인딩 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="11a4f-112">Create an instance of the binding class that you are using.</span></span> <span data-ttu-id="11a4f-113">미리 정의 된 바인딩 목록은 [시스템 제공 바인딩](system-provided-bindings.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="11a4f-113">For a list of predefined bindings, see [System-Provided Bindings](system-provided-bindings.md).</span></span> <span data-ttu-id="11a4f-114">이 예제에서는 <xref:System.ServiceModel.WSHttpBinding> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="11a4f-114">This example creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class.</span></span>

2. <span data-ttu-id="11a4f-115">`Mode` 속성에서 반환하는 개체의 `Security` 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="11a4f-115">Set the `Mode` property of the object returned by the `Security` property.</span></span>

     [!code-csharp[c_SettingSecurityMode#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#1)]
     [!code-vb[c_SettingSecurityMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#1)]

     <span data-ttu-id="11a4f-116">또는 다음 코드에 표시된 것처럼 모드를 메시지로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="11a4f-116">Alternatively, set the mode to message, as shown in the following code.</span></span>

     [!code-csharp[c_SettingSecurityMode#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#2)]
     [!code-vb[c_SettingSecurityMode#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#2)]

     <span data-ttu-id="11a4f-117">또는 다음 코드에 표시된 것처럼 모드를 메시지 자격 증명을 사용한 전송으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="11a4f-117">Or set the mode to transport with message credentials, as shown in the following code.</span></span>

     [!code-csharp[c_SettingSecurityMode#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#3)]
     [!code-vb[c_SettingSecurityMode#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#3)]

3. <span data-ttu-id="11a4f-118">다음 코드에 표시된 것처럼 바인딩의 생성자에서 모드를 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11a4f-118">You can also set the mode in the constructor of the binding, as shown in the following code.</span></span>

     [!code-csharp[c_SettingSecurityMode#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#4)]
     [!code-vb[c_SettingSecurityMode#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#4)]

## <a name="setting-the-clientcredentialtype-property"></a><span data-ttu-id="11a4f-119">ClientCredentialType 속성 설정</span><span class="sxs-lookup"><span data-stu-id="11a4f-119">Setting the ClientCredentialType Property</span></span>

<span data-ttu-id="11a4f-120">모드를 세 값 중 하나로 설정하면 `ClientCredentialType` 속성을 설정하는 방법이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="11a4f-120">Setting the mode to one of the three values determines how you set the `ClientCredentialType` property.</span></span> <span data-ttu-id="11a4f-121">예를 들어, <xref:System.ServiceModel.WSHttpBinding> 클래스를 사용하여 모드를 `Transport`로 설정할 경우 <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> 클래스의 <xref:System.ServiceModel.HttpTransportSecurity> 속성을 적절한 값으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a4f-121">For example, using the <xref:System.ServiceModel.WSHttpBinding> class, setting the mode to `Transport` means you must set the <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> property of the <xref:System.ServiceModel.HttpTransportSecurity> class to an appropriate value.</span></span>

### <a name="to-set-the-clientcredentialtype-property-for-transport-mode"></a><span data-ttu-id="11a4f-122">전송 모드에 대해 ClientCredentialType 속성을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="11a4f-122">To set the ClientCredentialType property for Transport mode</span></span>

1. <span data-ttu-id="11a4f-123">바인딩의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="11a4f-123">Create an instance of the binding.</span></span>

2. <span data-ttu-id="11a4f-124">`Mode` 속성을 `Transport`으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="11a4f-124">Set the `Mode` property to `Transport`.</span></span>

3. <span data-ttu-id="11a4f-125">`ClientCredential` 속성을 적절한 값으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="11a4f-125">Set the `ClientCredential` property to an appropriate value.</span></span> <span data-ttu-id="11a4f-126">다음 코드에서는 속성을 `Windows`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="11a4f-126">The following code sets the property to `Windows`.</span></span>

     [!code-csharp[c_SettingSecurityMode#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#5)]
     [!code-vb[c_SettingSecurityMode#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#5)]

### <a name="to-set-the-clientcredentialtype-property-for-message-mode"></a><span data-ttu-id="11a4f-127">메시지 모드에 대해 ClientCredentialType 속성을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="11a4f-127">To set the ClientCredentialType property for Message mode</span></span>

1. <span data-ttu-id="11a4f-128">바인딩의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="11a4f-128">Create an instance of the binding.</span></span>

2. <span data-ttu-id="11a4f-129">`Mode` 속성을 `Message`으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="11a4f-129">Set the `Mode` property to `Message`.</span></span>

3. <span data-ttu-id="11a4f-130">`ClientCredential` 속성을 적절한 값으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="11a4f-130">Set the `ClientCredential` property to an appropriate value.</span></span> <span data-ttu-id="11a4f-131">다음 코드에서는 속성을 `Certificate`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="11a4f-131">The following code sets the property to `Certificate`.</span></span>

     [!code-csharp[c_SettingSecurityMode#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#6)]
     [!code-vb[c_SettingSecurityMode#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#6)]

### <a name="to-set-the-mode-and-clientcredentialtype-property-in-configuration"></a><span data-ttu-id="11a4f-132">구성에서 모드 및 ClientCredentialType 속성을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="11a4f-132">To set the Mode and ClientCredentialType property in configuration</span></span>

1. <span data-ttu-id="11a4f-133">구성 파일의 요소에 적절 한 바인딩 요소를 추가 [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a4f-133">Add an appropriate binding element to the [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) element of the configuration file.</span></span> <span data-ttu-id="11a4f-134">다음 예제에서는 요소를 추가 합니다 [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="11a4f-134">The following example adds a [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>

2. <span data-ttu-id="11a4f-135">요소를 추가 하 `<binding>` 고 해당 `name` 특성을 적절 한 값으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a4f-135">Add a `<binding>` element and set its `name` attribute to an appropriate value.</span></span>

3. <span data-ttu-id="11a4f-136">`<security>` 요소를 추가하고 `mode` 특성을 `Message`, `Transport` 또는 `TransportWithMessageCredential`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="11a4f-136">Add a `<security>` element and set the `mode` attribute to `Message`, `Transport`, or `TransportWithMessageCredential`.</span></span>

4. <span data-ttu-id="11a4f-137">모드를 `Transport`로 설정한 경우 `<transport>` 요소를 추가하고 `clientCredential` 특성을 적절한 값으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="11a4f-137">If the mode is set to `Transport`, add a `<transport>` element and set the `clientCredential` attribute to an appropriate value.</span></span>

     <span data-ttu-id="11a4f-138">다음 예제에서는 모드를 "`Transport"`로 설정한 다음 `clientCredentialType` 요소의 `<transport>` 특성을 "`Windows"`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="11a4f-138">The following example sets the mode to "`Transport"`, and then sets the `clientCredentialType` attribute of the `<transport>` element to "`Windows"`.</span></span>

    ```xml
    <wsHttpBinding>
    <binding name="TransportSecurity">
        <security mode="Transport" >
           <transport clientCredentialType = "Windows" />
        </security>
    </binding>
    </wsHttpBinding >
    ```

     <span data-ttu-id="11a4f-139">또는 `security mode`를 "`Message"`로 설정한 다음 `<"message">` 요소를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="11a4f-139">Alternatively, set the `security mode` to "`Message"`, followed by a `<"message">` element.</span></span> <span data-ttu-id="11a4f-140">이 예제에서는 `clientCredentialType`을 "`Certificate"`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="11a4f-140">This example sets the `clientCredentialType` to "`Certificate"`.</span></span>

    ```xml
    <wsHttpBinding>
    <binding name="MessageSecurity">
        <security mode="Message" >
           <message clientCredentialType = "Certificate" />
        </security>
    </binding>
    </wsHttpBinding >
    ```

     <span data-ttu-id="11a4f-141"><xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> 값은 특별한 경우에 사용되며 이에 대해서는 아래에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11a4f-141">Using the <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> value is a special case, and is explained below.</span></span>

### <a name="using-transportwithmessagecredential"></a><span data-ttu-id="11a4f-142">TransportWithMessageCredential 사용</span><span class="sxs-lookup"><span data-stu-id="11a4f-142">Using TransportWithMessageCredential</span></span>

<span data-ttu-id="11a4f-143">보안 모드를 `TransportWithMessageCredential`로 설정하면 전송에서 전송 수준 보안을 제공하는 실제 메커니즘을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="11a4f-143">When setting the security mode to `TransportWithMessageCredential`, the transport determines the actual mechanism that provides the transport-level security.</span></span> <span data-ttu-id="11a4f-144">예를 들어, HTTP 프로토콜에서는 HTTP를 통한 SSL(Secure Sockets Layer)(HTTPS)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="11a4f-144">For example, the HTTP protocol uses Secure Sockets Layer (SSL) over HTTP (HTTPS).</span></span> <span data-ttu-id="11a4f-145">따라서 전송 보안 개체(예: `ClientCredentialType`)의 <xref:System.ServiceModel.HttpTransportSecurity> 속성 설정은 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="11a4f-145">Therefore, setting the `ClientCredentialType` property of any transport security object (such as <xref:System.ServiceModel.HttpTransportSecurity>) is ignored.</span></span>  <span data-ttu-id="11a4f-146">즉, 메시지 보안 개체(`ClientCredentialType` 바인딩의 경우 `WSHttpBinding` 개체)의 <xref:System.ServiceModel.NonDualMessageSecurityOverHttp>만 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11a4f-146">In other words, you can only set the `ClientCredentialType` of the message security object (for the `WSHttpBinding` binding, the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> object).</span></span>

<span data-ttu-id="11a4f-147">자세한 내용은 [방법: 전송 보안 및 메시지 자격 증명 사용](./feature-details/how-to-use-transport-security-and-message-credentials.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="11a4f-147">For more information, see [How to: Use Transport Security and Message Credentials](./feature-details/how-to-use-transport-security-and-message-credentials.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="11a4f-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="11a4f-148">See also</span></span>

- [<span data-ttu-id="11a4f-149">방법: SSL 인증서를 사용하여 포트 구성</span><span class="sxs-lookup"><span data-stu-id="11a4f-149">How to: Configure a Port with an SSL Certificate</span></span>](./feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [<span data-ttu-id="11a4f-150">방법: 전송 보안 및 메시지 자격 증명 사용</span><span class="sxs-lookup"><span data-stu-id="11a4f-150">How to: Use Transport Security and Message Credentials</span></span>](./feature-details/how-to-use-transport-security-and-message-credentials.md)
- [<span data-ttu-id="11a4f-151">전송 보안</span><span class="sxs-lookup"><span data-stu-id="11a4f-151">Transport Security</span></span>](./feature-details/transport-security.md)
- [<span data-ttu-id="11a4f-152">메시지 보안</span><span class="sxs-lookup"><span data-stu-id="11a4f-152">Message Security</span></span>](./feature-details/message-security-in-wcf.md)
- [<span data-ttu-id="11a4f-153">보안 개요</span><span class="sxs-lookup"><span data-stu-id="11a4f-153">Security Overview</span></span>](./feature-details/security-overview.md)
- [<span data-ttu-id="11a4f-154">시스템 제공 바인딩</span><span class="sxs-lookup"><span data-stu-id="11a4f-154">System-Provided Bindings</span></span>](system-provided-bindings.md)
- [\<security>](../configure-apps/file-schema/wcf/security-of-wshttpbinding.md)
- [\<security>](../configure-apps/file-schema/wcf/security-of-basichttpbinding.md)
- [\<security>](../configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
