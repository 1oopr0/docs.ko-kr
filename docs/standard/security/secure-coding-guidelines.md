---
title: .NET에 대 한 보안 코딩 지침
description: 사용할 코드를 디자인 합니다. 악의적인 코드가 데이터에 액세스 하거나 다른 작업을 수행 하지 못하도록 하는 데 도움이 되는 순 적용 권한 및 기타 적용.
ms.date: 07/15/2020
helpviewer_keywords:
- managed wrapper to native code implementation
- secure coding
- reusable components
- library code that exposes protected resources
- code, security
- code security
- secure coding, options
- components [.NET], security
- code security, options
- security-neutral code
- security [.NET], coding guidelines
ms.assetid: 4f882d94-262b-4494-b0a6-ba9ba1f5f177
ms.openlocfilehash: a05e0cec2814be88ac835d05601d5cf5f66383c3
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555958"
---
# <a name="secure-coding-guidelines"></a><span data-ttu-id="b5a4d-103">보안 코딩 지침</span><span class="sxs-lookup"><span data-stu-id="b5a4d-103">Secure coding guidelines</span></span>

<span data-ttu-id="b5a4d-104">대부분의 응용 프로그램 코드는 .NET에서 구현 된 인프라를 간단히 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5a4d-104">Most application code can simply use the infrastructure implemented by .NET.</span></span> <span data-ttu-id="b5a4d-105">경우에 따라, 보안 시스템을 확장하거나 새로운 임시 메서드를 사용하여 빌드되는 추가적인 애플리케이션 관련 보안이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b5a4d-105">In some cases, additional application-specific security is required, built either by extending the security system or by using new ad hoc methods.</span></span>

<span data-ttu-id="b5a4d-106">.NET에서 적용 한 권한 및 기타 적용을 코드에 사용 하 여 악의적인 코드가 원치 않는 다른 작업을 수행 하지 않으려는 정보에 액세스 하는 것을 방지 하기 위해 장벽을 방어 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5a4d-106">Using .NET enforced permissions and other enforcement in your code, you should erect barriers to prevent malicious code from accessing information that you don't want it to have or performing other undesirable actions.</span></span> <span data-ttu-id="b5a4d-107">또한 신뢰할 수 있는 코드를 사용하여 예상되는 모든 시나리오에서 보안과 유용성 간의 균형을 맞춰야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5a4d-107">Additionally, you must strike a balance between security and usability in all the expected scenarios using trusted code.</span></span>

<span data-ttu-id="b5a4d-108">이 개요에서는 보안 시스템에서 사용하기 위해 코드를 설계하는 여러 가지 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b5a4d-108">This overview describes the different ways code can be designed to work with the security system.</span></span>

## <a name="securing-resource-access"></a><span data-ttu-id="b5a4d-109">리소스 액세스 보안</span><span class="sxs-lookup"><span data-stu-id="b5a4d-109">Securing resource access</span></span>

<span data-ttu-id="b5a4d-110">코드를 설계하고 작성하는 경우, 특히 출처를 알 수 없는 코드를 사용하거나 호출하는 경우 코드에 부여된 리소스 액세스 권한을 보호하고 제한해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5a4d-110">When designing and writing your code, you need to protect and limit the access that code has to resources, especially when using or invoking code of unknown origin.</span></span> <span data-ttu-id="b5a4d-111">따라서 코드의 보안을 유지하도록 다음과 같은 기술을 염두에 둡니다.</span><span class="sxs-lookup"><span data-stu-id="b5a4d-111">So, keep in mind the following techniques to ensure your code is secure:</span></span>

- <span data-ttu-id="b5a4d-112">CAS(코드 액세스 보안) 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="b5a4d-112">Do not use Code Access Security (CAS).</span></span>

- <span data-ttu-id="b5a4d-113">부분적으로 신뢰할 수 있는 코드 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="b5a4d-113">Do not use partial trusted code.</span></span>

- <span data-ttu-id="b5a4d-114">[AllowPartiallyTrustedCaller](xref:System.Security.AllowPartiallyTrustedCallersAttribute) 특성 (APTCA)을 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="b5a4d-114">Do not use the [AllowPartiallyTrustedCaller](xref:System.Security.AllowPartiallyTrustedCallersAttribute) attribute (APTCA).</span></span>

- <span data-ttu-id="b5a4d-115">.NET Remoting 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="b5a4d-115">Do not use .NET Remoting.</span></span>

- <span data-ttu-id="b5a4d-116">DCOM(분산 구성 요소 개체 모델) 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="b5a4d-116">Do not use Distributed Component Object Model (DCOM).</span></span>

- <span data-ttu-id="b5a4d-117">이진 포맷터 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="b5a4d-117">Do not use binary formatters.</span></span>

<span data-ttu-id="b5a4d-118">코드 액세스 보안 및 보안 투명 코드는 부분적으로 신뢰할 수 있는 코드의 보안 경계로 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b5a4d-118">Code Access Security and Security-Transparent Code are not supported as a security boundary with partially trusted code.</span></span> <span data-ttu-id="b5a4d-119">대체 보안 조치를 적용하지 않고 출처를 알 수 없는 코드를 로드 및 실행하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b5a4d-119">We advise against loading and executing code of unknown origins without putting alternative security measures in place.</span></span> <span data-ttu-id="b5a4d-120">대체 보안 조치는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b5a4d-120">The alternative security measures are:</span></span>

- <span data-ttu-id="b5a4d-121">가상화</span><span class="sxs-lookup"><span data-stu-id="b5a4d-121">Virtualization</span></span>

- <span data-ttu-id="b5a4d-122">AppContainers</span><span class="sxs-lookup"><span data-stu-id="b5a4d-122">AppContainers</span></span>

- <span data-ttu-id="b5a4d-123">OS(운영 체제) 사용자 및 사용 권한</span><span class="sxs-lookup"><span data-stu-id="b5a4d-123">Operating system (OS) users and permissions</span></span>

- <span data-ttu-id="b5a4d-124">Hyper-V 컨테이너</span><span class="sxs-lookup"><span data-stu-id="b5a4d-124">Hyper-V containers</span></span>

## <a name="security-neutral-code"></a><span data-ttu-id="b5a4d-125">보안 중립 코드</span><span class="sxs-lookup"><span data-stu-id="b5a4d-125">Security-neutral code</span></span>

<span data-ttu-id="b5a4d-126">보안 중립 코드는 보안 시스템에서 명시적인 작업을 수행하는 것이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b5a4d-126">Security-neutral code does nothing explicit with the security system.</span></span> <span data-ttu-id="b5a4d-127">단순히 코드에 부여되는 권한을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b5a4d-127">It runs with whatever permissions it receives.</span></span> <span data-ttu-id="b5a4d-128">보호 된 작업 (예: 파일, 네트워킹 등)과 관련 된 보안 예외를 catch 하지 못하는 응용 프로그램은 처리 되지 않은 예외를 발생 시킬 수 있지만, 보안 중립 코드는 여전히 .NET의 보안 기술을 활용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5a4d-128">Although applications that fail to catch security exceptions associated with protected operations (such as using files, networking, and so on) can result in an unhandled exception, security-neutral code still takes advantage of the security technologies in .NET.</span></span>

<span data-ttu-id="b5a4d-129">보안 중립 라이브러리에는 사용자가 파악해야 하는 특징이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5a4d-129">A security-neutral library has special characteristics that you should understand.</span></span> <span data-ttu-id="b5a4d-130">라이브러리가 파일을 사용 하거나 비관리 코드를 호출 하는 API 요소를 제공 한다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5a4d-130">Suppose your library provides API elements that use files or call unmanaged code.</span></span> <span data-ttu-id="b5a4d-131">코드에 해당 권한이 없으면 설명 된 대로 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b5a4d-131">If your code doesn't have the corresponding permission, it won't run as described.</span></span> <span data-ttu-id="b5a4d-132">하지만 코드에 권한이 있더라도 이 코드를 호출하는 모든 애플리케이션이 작동하려면 동일한 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5a4d-132">However, even if the code has the permission, any application code that calls it must have the same permission in order to work.</span></span> <span data-ttu-id="b5a4d-133">호출 코드에 올바른 권한이 없으면 <xref:System.Security.SecurityException> 코드 액세스 보안 스택 워크의 결과로이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5a4d-133">If the calling code doesn't have the right permission, a <xref:System.Security.SecurityException> appears as a result of the code access security stack walk.</span></span>

## <a name="application-code-that-isnt-a-reusable-component"></a><span data-ttu-id="b5a4d-134">재사용 가능한 구성 요소가 아닌 응용 프로그램 코드</span><span class="sxs-lookup"><span data-stu-id="b5a4d-134">Application code that isn't a reusable component</span></span>

<span data-ttu-id="b5a4d-135">코드가 다른 코드에서 호출 되지 않는 응용 프로그램의 일부인 경우 보안은 단순 하며 특수 코딩이 필요 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5a4d-135">If your code is part of an application that won't be called by other code, security is simple and special coding might not be required.</span></span> <span data-ttu-id="b5a4d-136">하지만 악성 코드는 해당 코드를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5a4d-136">However, remember that malicious code can call your code.</span></span> <span data-ttu-id="b5a4d-137">코드 액세스 보안으로 악성 코드가 리소스에 액세스하는 것을 방지할 수 있지만, 이러한 코드는 중요한 정보가 들어 있을 수 있는 필드 또는 속성의 값을 판독할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5a4d-137">While code access security might stop malicious code from accessing resources, such code could still read values of your fields or properties that might contain sensitive information.</span></span>

<span data-ttu-id="b5a4d-138">또한 해당 코드가 인터넷 또는 기타 신뢰할 수 없는 소스로부터의 사용자 입력을 허용하는 경우에는 악의적인 입력에 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5a4d-138">Additionally, if your code accepts user input from the Internet or other unreliable sources, you must be careful about malicious input.</span></span>

## <a name="managed-wrapper-to-native-code-implementation"></a><span data-ttu-id="b5a4d-139">네이티브 코드 구현에 대 한 관리 되는 래퍼</span><span class="sxs-lookup"><span data-stu-id="b5a4d-139">Managed wrapper to native code implementation</span></span>

<span data-ttu-id="b5a4d-140">일반적으로 이 시나리오에서는 네이티브 코드에서 관리 코드에 사용 가능하게 하려는 몇 가지 유용한 기능을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="b5a4d-140">Typically in this scenario, some useful functionality is implemented in native code that you want to make available to managed code.</span></span> <span data-ttu-id="b5a4d-141">관리되는 래퍼는 플랫폼 호출 또는 COM interop를 사용하여 쉽게 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5a4d-141">Managed wrappers are easy to write using either platform invoke or COM interop.</span></span> <span data-ttu-id="b5a4d-142">하지만 이 작업을 성공적으로 수행하려면 래퍼 호출자에게 비관리 코드 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5a4d-142">However, if you do this, callers of your wrappers must have unmanaged code rights in order to succeed.</span></span> <span data-ttu-id="b5a4d-143">기본 정책에서이는 인트라넷 또는 인터넷에서 다운로드 된 코드가 래퍼와 작동 하지 않음을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5a4d-143">Under default policy, this means that code downloaded from an intranet or the Internet won't work with the wrappers.</span></span>

<span data-ttu-id="b5a4d-144">이러한 래퍼를 사용 하는 모든 응용 프로그램에 비관리 코드 권한을 부여 하는 대신, 래퍼 코드에만 이러한 권한을 부여 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b5a4d-144">Instead of giving unmanaged code rights to all applications that use these wrappers, it's better to give these rights only to the wrapper code.</span></span> <span data-ttu-id="b5a4d-145">기본 기능이 리소스를 노출하지 않으며 구현도 안전할 경우에는, 래퍼는 모든 코드가 이를 통해 호출할 수 있도록 해당 권한을 어셜션하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5a4d-145">If the underlying functionality exposes no resources and the implementation is likewise safe, the wrapper only needs to assert its rights, which enables any code to call through it.</span></span> <span data-ttu-id="b5a4d-146">리소스가 포함되어 있으면, 보안 코딩은 다음 섹션에 설명된 라이브러리 코드의 경우와 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5a4d-146">When resources are involved, security coding should be the same as the library code case described in the next section.</span></span> <span data-ttu-id="b5a4d-147">래퍼는 호출자를 이러한 리소스에 노출할 가능성이 있기 때문에, 네이티브 코드가 안전한지 신중하게 확인해야 하며 이는 래퍼의 책임입니다.</span><span class="sxs-lookup"><span data-stu-id="b5a4d-147">Because the wrapper is potentially exposing callers to these resources, careful verification of the safety of the native code is necessary and is the wrapper's responsibility.</span></span>

## <a name="library-code-that-exposes-protected-resources"></a><span data-ttu-id="b5a4d-148">보호 된 리소스를 노출 하는 라이브러리 코드</span><span class="sxs-lookup"><span data-stu-id="b5a4d-148">Library code that exposes protected resources</span></span>

<span data-ttu-id="b5a4d-149">다음 접근 방식은 보안 코딩을 위해 가장 강력 하 고 위험할 수 있는 (잘못 된 경우)입니다. 즉, 라이브러리는 .NET 클래스에서 사용 하는 리소스에 대 한 사용 권한을 적용 하는 것 처럼 다른 방법으로는 사용할 수 없는 특정 리소스에 액세스 하기 위해 다른 코드의 인터페이스 역할을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5a4d-149">The following approach is the most powerful and hence potentially dangerous (if done incorrectly) for security coding: your library serves as an interface for other code to access certain resources that aren't otherwise available, just as the .NET classes enforce permissions for the resources they use.</span></span> <span data-ttu-id="b5a4d-150">리소스를 노출할 경우, 먼저 코드는 리소스에 적절한 권한을 요구해야 합니다(즉, 보안 검사를 수행해야 함). 그런 다음 실제 작업을 수행할 수 있도록 해당 권한을 어설션합니다.</span><span class="sxs-lookup"><span data-stu-id="b5a4d-150">Wherever you expose a resource, your code must first demand the permission appropriate to the resource (that is, it must perform a security check) and then typically assert its rights to perform the actual operation.</span></span>

## <a name="see-also"></a><span data-ttu-id="b5a4d-151">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b5a4d-151">See also</span></span>

- [<span data-ttu-id="b5a4d-152">상태 데이터 보안</span><span class="sxs-lookup"><span data-stu-id="b5a4d-152">Securing State Data</span></span>](securing-state-data.md)
- [<span data-ttu-id="b5a4d-153">보안 및 사용자 입력</span><span class="sxs-lookup"><span data-stu-id="b5a4d-153">Security and User Input</span></span>](security-and-user-input.md)
- [<span data-ttu-id="b5a4d-154">보안 및 경합 상태</span><span class="sxs-lookup"><span data-stu-id="b5a4d-154">Security and Race Conditions</span></span>](security-and-race-conditions.md)
- [<span data-ttu-id="b5a4d-155">보안 및 빠른 코드 생성</span><span class="sxs-lookup"><span data-stu-id="b5a4d-155">Security and On-the-Fly Code Generation</span></span>](security-and-on-the-fly-code-generation.md)
- [<span data-ttu-id="b5a4d-156">역할 기반 보안</span><span class="sxs-lookup"><span data-stu-id="b5a4d-156">Role-Based Security</span></span>](role-based-security.md)
- [<span data-ttu-id="b5a4d-157">ASP.NET Core 보안</span><span class="sxs-lookup"><span data-stu-id="b5a4d-157">ASP.NET Core Security</span></span>](/aspnet/core/security/)
