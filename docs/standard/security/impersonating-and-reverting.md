---
title: 가장 및 되돌리기
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsIdentity objects, impersonating
- security [.NET Framework], impersonating Windows accounts
- impersonating Windows accounts
ms.assetid: b93d402c-6c28-4f50-b2bc-d9607dc3e470
ms.openlocfilehash: dbfd71830ace1eb8af9f55f06c9ce35c32d592bb
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288019"
---
# <a name="impersonating-and-reverting"></a><span data-ttu-id="4765f-102">가장 및 되돌리기</span><span class="sxs-lookup"><span data-stu-id="4765f-102">Impersonating and Reverting</span></span>
<span data-ttu-id="4765f-103">Windows 계정을 가장하기 위해 Windows 계정 토큰을 가져와야 하는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4765f-103">Sometimes you might need to obtain a Windows account token to impersonate a Windows account.</span></span> <span data-ttu-id="4765f-104">예를 들어 ASP.NET 기반 애플리케이션이 여러 사용자를 대신하여 작동해야 하는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4765f-104">For example, your ASP.NET-based application might have to act on behalf of several users at different times.</span></span> <span data-ttu-id="4765f-105">애플리케이션이 인터넷 정보 서비스(IIS)에서 관리자를 나타내는 토큰을 수락하고, 사용자를 가장하고, 작업을 수행하며, 이전 ID로 되돌릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4765f-105">Your application might accept a token that represents an administrator from Internet Information Services (IIS), impersonate that user, perform an operation, and revert to the previous identity.</span></span> <span data-ttu-id="4765f-106">그런 다음 응용 프로그램은 권한이 적은 사용자를 나타내는 IIS의 토큰을 수락하고, 일부 작업을 수행하여, 다시 되돌릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4765f-106">Next, it might accept a token from IIS that represents a user with fewer rights, perform some operation, and revert again.</span></span>  
  
 <span data-ttu-id="4765f-107">애플리케이션이 IIS에 의해 현재 스레드에 연결되지 않은 Windows 계정을 가장해야 하는 경우에는 해당 계정의 토큰을 검색하고 이 토큰을 사용하여 계정을 활성화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4765f-107">In situations where your application must impersonate a Windows account that has not been attached to the current thread by IIS, you must retrieve that account's token and use it to activate the account.</span></span> <span data-ttu-id="4765f-108">이렇게 하려면 다음과 같은 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="4765f-108">You can do this by performing the following tasks:</span></span>  
  
1. <span data-ttu-id="4765f-109">비관리 **LogonUser** 메서드를 호출하여 특정 사용자에 대한 계정 토큰을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="4765f-109">Retrieve an account token for a particular user by making a call to the unmanaged **LogonUser** method.</span></span> <span data-ttu-id="4765f-110">이 메서드는 .NET Framework 기본 클래스 라이브러리에 없지만 비관리 **advapi32.dll**에는 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4765f-110">This method is not in the .NET Framework base class library, but is located in the unmanaged **advapi32.dll**.</span></span> <span data-ttu-id="4765f-111">비관리 코드에서 메서드에 액세스하는 작업은 고급 작업이므로 이 문서에서는 다루지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4765f-111">Accessing methods in unmanaged code is an advanced operation and is beyond the scope of this discussion.</span></span> <span data-ttu-id="4765f-112">자세한 내용은 [비관리 코드 상호 운용](../../framework/interop/index.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4765f-112">For more information, see [Interoperating with Unmanaged Code](../../framework/interop/index.md).</span></span> <span data-ttu-id="4765f-113">**LogonUser** 메서드 및 **advapi32.dll**에 대한 자세한 내용은 플랫폼 SDK 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4765f-113">For more information about the **LogonUser** method and **advapi32.dll**, see the Platform SDK documentation.</span></span>  
  
2. <span data-ttu-id="4765f-114">토큰을 전달하는 **WindowsIdentity** 클래스의 새 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4765f-114">Create a new instance of the **WindowsIdentity** class, passing the token.</span></span> <span data-ttu-id="4765f-115">다음 코드는 `hToken`이 Windows 토큰을 나타내는 호출을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="4765f-115">The following code demonstrates this call, where `hToken` represents a Windows token.</span></span>  
  
    ```csharp  
    WindowsIdentity impersonatedIdentity = new WindowsIdentity(hToken);  
    ```  
  
    ```vb  
    Dim impersonatedIdentity As New WindowsIdentity(hToken)  
    ```  
  
3. <span data-ttu-id="4765f-116">다음 코드에서와 같이, <xref:System.Security.Principal.WindowsImpersonationContext> 클래스의 새 인스턴스를 만들고 초기화된 클래스의 <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> 메서드로 이 인스턴스를 초기화하여 가장을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="4765f-116">Begin impersonation by creating a new instance of the <xref:System.Security.Principal.WindowsImpersonationContext> class and initializing it with the <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> method of the initialized class, as shown in the following code.</span></span>  
  
    ```csharp  
    WindowsImpersonationContext myImpersonation = impersonatedIdentity.Impersonate();  
    ```  
  
    ```vb  
    WindowsImpersonationContext myImpersonation = impersonatedIdentity.Impersonate()  
    ```  
  
4. <span data-ttu-id="4765f-117">더 이상 가장할 필요가 없으면, 다음 코드에서와 같이 <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> 메서드를 호출하여 가장을 되돌립니다.</span><span class="sxs-lookup"><span data-stu-id="4765f-117">When you no longer need to impersonate, call the <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> method to revert the impersonation, as shown in the following code.</span></span>  
  
    ```csharp  
    myImpersonation.Undo();  
    ```  
  
    ```vb  
    myImpersonation.Undo()  
    ```  
  
 <span data-ttu-id="4765f-118">신뢰할 수 있는 코드가 개체를 스레드에 이미 연결한 경우 <xref:System.Security.Principal.WindowsPrincipal> 계정 토큰을 사용 하지 않는 인스턴스 메서드 **Impersonate**를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4765f-118">If trusted code has already attached a <xref:System.Security.Principal.WindowsPrincipal> object to the thread, you can call the instance method **Impersonate**, which does not take an account token.</span></span> <span data-ttu-id="4765f-119">이 기능은 스레드의 **WindowsPrincipal** 개체가 프로세스를 현재 실행 중인 사용자가 아닌 다른 사용자를 나타낼 때 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="4765f-119">Note that this is only useful when the **WindowsPrincipal** object on the thread represents a user other than the one under which the process is currently executing.</span></span> <span data-ttu-id="4765f-120">예를 들어, Windows 인증을 사용 설정하고 가장을 해제하여 ASP.NET을 사용할 때 이러한 상황이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4765f-120">For example, you might encounter this situation using ASP.NET with Windows authentication turned on and impersonation turned off.</span></span> <span data-ttu-id="4765f-121">이 경우, 프로세스는 인터넷 정보 서비스(IIS)에 구성된 계정에서 실행되는 반면 현재 보안 주체는 페이지에 액세스하는 Windows 사용자를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4765f-121">In this case, the process is running under an account configured in Internet Information Services (IIS) while the current principal represents the Windows user that is accessing the page.</span></span>  
  
 <span data-ttu-id="4765f-122">**Impersonate** 또는 **Undo** 는 현재 호출 컨텍스트와 연결 된 **Principal** 개체 ()를 변경 하지 않습니다 <xref:System.Security.Principal.IPrincipal> .</span><span class="sxs-lookup"><span data-stu-id="4765f-122">Note that neither **Impersonate** nor **Undo** changes the **Principal** object (<xref:System.Security.Principal.IPrincipal>)  associated with the current call context.</span></span> <span data-ttu-id="4765f-123">대신, 가장 및 되돌리기는 현재 운영 체제 프로세스와 연결된 토큰을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="4765f-123">Rather, impersonation and reverting change the token associated with the current operating system process..</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4765f-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4765f-124">See also</span></span>

- <xref:System.Security.Principal.WindowsIdentity>
- <xref:System.Security.Principal.WindowsImpersonationContext>
- [<span data-ttu-id="4765f-125">Principal 개체 및 Identity 개체</span><span class="sxs-lookup"><span data-stu-id="4765f-125">Principal and Identity Objects</span></span>](principal-and-identity-objects.md)
- [<span data-ttu-id="4765f-126">비관리 코드와의 상호 운용</span><span class="sxs-lookup"><span data-stu-id="4765f-126">Interoperating with Unmanaged Code</span></span>](../../framework/interop/index.md)
