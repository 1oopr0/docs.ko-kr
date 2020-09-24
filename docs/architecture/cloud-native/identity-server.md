---
title: 클라우드 네이티브 앱에 대 한 IdentityServer
description: Azure 용 클라우드 네이티브 .NET 앱 설계 | IdentityServer
ms.date: 05/13/2020
ms.openlocfilehash: bdf193aac348b54f2ebf5b537beef5d61a1d5a1e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91163832"
---
# <a name="identityserver-for-cloud-native-applications"></a><span data-ttu-id="88e10-103">클라우드 네이티브 응용 프로그램에 대 한 IdentityServer</span><span class="sxs-lookup"><span data-stu-id="88e10-103">IdentityServer for cloud-native applications</span></span>

<span data-ttu-id="88e10-104">IdentityServer는 ASP.NET Core에 대 한 OIDC (Openid connect Connect) 및 OAuth 2.0 표준을 구현 하는 오픈 소스 인증 서버입니다.</span><span class="sxs-lookup"><span data-stu-id="88e10-104">IdentityServer is an open-source authentication server that implements OpenID Connect (OIDC) and OAuth 2.0 standards for ASP.NET Core.</span></span> <span data-ttu-id="88e10-105">웹, 네이티브, 모바일 또는 API 끝점 인지 여부에 관계 없이 모든 응용 프로그램에 대 한 요청을 인증 하는 일반적인 방법을 제공 하도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="88e10-105">It's designed to provide a common way to authenticate requests to all of your applications, whether they're web, native, mobile, or API endpoints.</span></span> <span data-ttu-id="88e10-106">IdentityServer를 사용 하 여 여러 응용 프로그램 및 응용 프로그램 유형에 SSO (Single Sign-on)를 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88e10-106">IdentityServer can be used to implement Single Sign-On (SSO) for multiple applications and application types.</span></span> <span data-ttu-id="88e10-107">로그인 양식 및 비슷한 사용자 인터페이스를 통해 실제 사용자를 인증 하는 데 사용할 수 있으며, 일반적으로 토큰 발급, 확인 및 사용자 인터페이스 없이 갱신을 포함 하는 서비스 기반 인증에도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88e10-107">It can be used to authenticate actual users via sign-in forms and similar user interfaces as well as service-based authentication that typically involves token issuance, verification, and renewal without any user interface.</span></span> <span data-ttu-id="88e10-108">IdentityServer은 사용자 지정이 가능한 솔루션으로 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="88e10-108">IdentityServer is designed to be a customizable solution.</span></span> <span data-ttu-id="88e10-109">각 인스턴스는 일반적으로 개별 조직 및/또는 응용 프로그램의 요구 사항 집합에 맞게 사용자 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="88e10-109">Each instance is typically customized to suit an individual organization and/or set of applications' needs.</span></span>

## <a name="common-web-app-scenarios"></a><span data-ttu-id="88e10-110">일반적인 웹 앱 시나리오</span><span class="sxs-lookup"><span data-stu-id="88e10-110">Common web app scenarios</span></span>

<span data-ttu-id="88e10-111">일반적으로 응용 프로그램은 다음 시나리오 중 일부 또는 모두를 지원 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="88e10-111">Typically, applications need to support some or all of the following scenarios:</span></span>

- <span data-ttu-id="88e10-112">사용자가 브라우저를 사용 하 여 웹 응용 프로그램에 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="88e10-112">Human users accessing web applications with a browser.</span></span>
- <span data-ttu-id="88e10-113">브라우저 기반 앱에서 백 엔드 웹 Api에 액세스 하는 휴먼 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="88e10-113">Human users accessing back-end Web APIs from browser-based apps.</span></span>
- <span data-ttu-id="88e10-114">백 엔드 웹 Api에 액세스 하는 모바일/네이티브 클라이언트의 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="88e10-114">Human users on mobile/native clients accessing back-end Web APIs.</span></span>
- <span data-ttu-id="88e10-115">활성 사용자 또는 사용자 인터페이스 없이 백 엔드 웹 Api에 액세스 하는 다른 응용 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="88e10-115">Other applications accessing back-end Web APIs (without an active user or user interface).</span></span>
- <span data-ttu-id="88e10-116">모든 응용 프로그램은 자체 id를 사용 하거나 사용자의 id에 위임 하 여 다른 웹 Api와 상호 작용 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88e10-116">Any application may need to interact with other Web APIs, using its own identity or delegating to the user's identity.</span></span>

![애플리케이션 유형 및 시나리오](./media/application-types.png)

<span data-ttu-id="88e10-118">**그림 8-1**.</span><span class="sxs-lookup"><span data-stu-id="88e10-118">**Figure 8-1**.</span></span> <span data-ttu-id="88e10-119">응용 프로그램 유형 및 시나리오.</span><span class="sxs-lookup"><span data-stu-id="88e10-119">Application types and scenarios.</span></span>

<span data-ttu-id="88e10-120">이러한 각 시나리오에서 노출 된 기능을 무단 사용 으로부터 보호 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="88e10-120">In each of these scenarios, the exposed functionality needs to be secured against unauthorized use.</span></span> <span data-ttu-id="88e10-121">일반적으로이 작업은 일반적으로 리소스에 대 한 요청을 수행 하는 사용자 또는 보안 주체를 인증 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="88e10-121">At a minimum, this typically requires authenticating the user or principal making a request for a resource.</span></span> <span data-ttu-id="88e10-122">이 인증은 SAML2p, WS 또는 Openid connect Connect와 같은 몇 가지 일반적인 프로토콜 중 하나를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88e10-122">This authentication may use one of several common protocols such as SAML2p, WS-Fed, or OpenID Connect.</span></span> <span data-ttu-id="88e10-123">Api와의 통신은 일반적으로 OAuth2 프로토콜을 사용 하 고 보안 토큰에 대 한 지원을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="88e10-123">Communicating with APIs typically uses the OAuth2 protocol and its support for security tokens.</span></span> <span data-ttu-id="88e10-124">이러한 중요 한 교차를 교차 하는 보안 문제와 해당 구현 세부 사항을 응용 프로그램 자체에서 분리 하면 일관성을 유지 하 고 보안 및 유지 관리 용이성을 향상 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="88e10-124">Separating these critical cross-cutting security concerns and their implementation details from the applications themselves ensures consistency and improves security and maintainability.</span></span> <span data-ttu-id="88e10-125">이러한 문제를 IdentityServer와 같은 전용 제품으로 아웃소싱 하면 모든 응용 프로그램에서 이러한 문제를 해결 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="88e10-125">Outsourcing these concerns to a dedicated product like IdentityServer helps the requirement for every application to solve these problems itself.</span></span>

<span data-ttu-id="88e10-126">IdentityServer는 ASP.NET Core 응용 프로그램 내에서 실행 되 고 Openid connect Connect 및 OAuth2에 대 한 지원을 추가 하는 미들웨어를 제공 합니다 ( [지원 되는 사양](https://docs.identityserver.io/en/latest/intro/specs.html)참조).</span><span class="sxs-lookup"><span data-stu-id="88e10-126">IdentityServer provides middleware that runs within an ASP.NET Core application and adds support for OpenID Connect and OAuth2 (see [supported specifications](https://docs.identityserver.io/en/latest/intro/specs.html)).</span></span> <span data-ttu-id="88e10-127">조직에서는 IdentityServer 미들웨어를 사용 하 여 자체 ASP.NET Core 앱을 만들어 모든 토큰 기반 보안 프로토콜에 대 한 STS 역할을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="88e10-127">Organizations would create their own ASP.NET Core app using IdentityServer middleware to act as the STS for all of their token-based security protocols.</span></span> <span data-ttu-id="88e10-128">IdentityServer 미들웨어는 끝점을 노출 하 여 다음과 같은 표준 기능을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="88e10-128">The IdentityServer middleware exposes endpoints to support standard functionality, including:</span></span>

- <span data-ttu-id="88e10-129">권한 부여 (최종 사용자 인증)</span><span class="sxs-lookup"><span data-stu-id="88e10-129">Authorize (authenticate the end user)</span></span>
- <span data-ttu-id="88e10-130">토큰 (프로그래밍 방식으로 토큰 요청)</span><span class="sxs-lookup"><span data-stu-id="88e10-130">Token (request a token programmatically)</span></span>
- <span data-ttu-id="88e10-131">검색 (서버에 대 한 메타 데이터)</span><span class="sxs-lookup"><span data-stu-id="88e10-131">Discovery (metadata about the server)</span></span>
- <span data-ttu-id="88e10-132">사용자 정보 (유효한 액세스 토큰을 사용 하 여 사용자 정보 가져오기)</span><span class="sxs-lookup"><span data-stu-id="88e10-132">User Info (get user information with a valid access token)</span></span>
- <span data-ttu-id="88e10-133">장치 권한 부여 (장치 흐름 권한 부여를 시작 하는 데 사용 됨)</span><span class="sxs-lookup"><span data-stu-id="88e10-133">Device Authorization (used to start device flow authorization)</span></span>
- <span data-ttu-id="88e10-134">검사 (토큰 유효성 검사)</span><span class="sxs-lookup"><span data-stu-id="88e10-134">Introspection (token validation)</span></span>
- <span data-ttu-id="88e10-135">해지 (토큰 해지)</span><span class="sxs-lookup"><span data-stu-id="88e10-135">Revocation (token revocation)</span></span>
- <span data-ttu-id="88e10-136">세션 종료 (모든 앱에서 single sign-on 트리거)</span><span class="sxs-lookup"><span data-stu-id="88e10-136">End Session (trigger single sign-out across all apps)</span></span>

## <a name="getting-started"></a><span data-ttu-id="88e10-137">시작</span><span class="sxs-lookup"><span data-stu-id="88e10-137">Getting started</span></span>

<span data-ttu-id="88e10-138">IdentityServer4은 오픈 소스 이며 무료로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88e10-138">IdentityServer4 is open-source and free to use.</span></span> <span data-ttu-id="88e10-139">NuGet 패키지를 사용 하 여 응용 프로그램에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88e10-139">You can add it to your applications using its NuGet packages.</span></span> <span data-ttu-id="88e10-140">주 패키지는 400만 번 이상 다운로드 된 [IdentityServer4](https://www.nuget.org/packages/IdentityServer4/) 입니다.</span><span class="sxs-lookup"><span data-stu-id="88e10-140">The main package is [IdentityServer4](https://www.nuget.org/packages/IdentityServer4/) that has been downloaded over four million times.</span></span> <span data-ttu-id="88e10-141">기본 패키지는 사용자 인터페이스 코드를 포함 하지 않고 메모리 구성 에서만 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="88e10-141">The base package doesn't include any user interface code and only supports in memory configuration.</span></span> <span data-ttu-id="88e10-142">데이터베이스와 함께 사용 하려면 Entity Framework Core을 사용 하 여 IdentityServer에 대 한 구성 및 운영 데이터를 저장 하는 [IdentityServer4](https://www.nuget.org/packages/IdentityServer4.EntityFramework) 와 같은 데이터 공급자를 사용 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="88e10-142">To use it with a database, you'll also want a data provider like [IdentityServer4.EntityFramework](https://www.nuget.org/packages/IdentityServer4.EntityFramework) that uses Entity Framework Core to store configuration and operational data for IdentityServer.</span></span> <span data-ttu-id="88e10-143">사용자 인터페이스의 경우 IdentityServer 미들웨어를 사용 하 여 로그인 및 로그 아웃에 대 한 지원을 추가 하기 위해 [빠른 시작 UI 리포지토리에서](https://github.com/IdentityServer/IdentityServer4.Quickstart.UI) 파일을 ASP.NET Core MVC 응용 프로그램으로 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88e10-143">For user interface, you can copy files from the [Quickstart UI repository](https://github.com/IdentityServer/IdentityServer4.Quickstart.UI) into your ASP.NET Core MVC application to add support for sign in and sign out using IdentityServer middleware.</span></span>

## <a name="configuration"></a><span data-ttu-id="88e10-144">구성</span><span class="sxs-lookup"><span data-stu-id="88e10-144">Configuration</span></span>

<span data-ttu-id="88e10-145">IdentityServer는 각 사용자 지정 설치의 일부로 구성할 수 있는 다양 한 종류의 프로토콜과 소셜 인증 공급자를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="88e10-145">IdentityServer supports different kinds of protocols and social authentication providers that can be configured as part of each custom installation.</span></span> <span data-ttu-id="88e10-146">이는 일반적으로 메서드의 ASP.NET Core 응용 프로그램 클래스에서 수행 됩니다 `Startup` `ConfigureServices` .</span><span class="sxs-lookup"><span data-stu-id="88e10-146">This is typically done in the ASP.NET Core application's `Startup` class in the `ConfigureServices` method.</span></span> <span data-ttu-id="88e10-147">구성에는 지원 되는 프로토콜과 사용할 서버 및 끝점의 경로를 지정 하는 작업이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="88e10-147">The configuration involves specifying the supported protocols and the paths to the servers and endpoints that will be used.</span></span> <span data-ttu-id="88e10-148">그림 8-2에서는 IdentityServer4 빠른 시작 UI 프로젝트에서 가져온 구성 예제를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="88e10-148">Figure 8-2 shows an example configuration taken from the IdentityServer4 Quickstart UI project:</span></span>

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();

        // some details omitted
        services.AddIdentityServer();

          services.AddAuthentication()
            .AddGoogle("Google", options =>
            {
                options.SignInScheme = IdentityServerConstants.ExternalCookieAuthenticationScheme;

                options.ClientId = "<insert here>";
                options.ClientSecret = "<insert here>";
            })
            .AddOpenIdConnect("demoidsrv", "IdentityServer", options =>
            {
                options.SignInScheme = IdentityServerConstants.ExternalCookieAuthenticationScheme;
                options.SignOutScheme = IdentityServerConstants.SignoutScheme;

                options.Authority = "https://demo.identityserver.io/";
                options.ClientId = "implicit";
                options.ResponseType = "id_token";
                options.SaveTokens = true;
                options.CallbackPath = new PathString("/signin-idsrv");
                options.SignedOutCallbackPath = new PathString("/signout-callback-idsrv");
                options.RemoteSignOutPath = new PathString("/signout-idsrv");

                options.TokenValidationParameters = new TokenValidationParameters
                {
                    NameClaimType = "name",
                    RoleClaimType = "role"
                };
            });
    }
}
```

<span data-ttu-id="88e10-149">**그림 8-2**.</span><span class="sxs-lookup"><span data-stu-id="88e10-149">**Figure 8-2**.</span></span> <span data-ttu-id="88e10-150">IdentityServer 구성.</span><span class="sxs-lookup"><span data-stu-id="88e10-150">Configuring IdentityServer.</span></span>

<span data-ttu-id="88e10-151">또한 IdentityServer는 다양 한 프로토콜 및 구성을 테스트 하는 데 사용할 수 있는 공개 데모 사이트를 호스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="88e10-151">IdentityServer also hosts a public demo site that can be used to test various protocols and configurations.</span></span> <span data-ttu-id="88e10-152">이 파일은에 있으며 [https://demo.identityserver.io/](https://demo.identityserver.io/) 제공 된에 따라 동작을 구성 하는 방법에 대 한 정보를 포함 `client_id` 합니다.</span><span class="sxs-lookup"><span data-stu-id="88e10-152">It's located at [https://demo.identityserver.io/](https://demo.identityserver.io/) and includes information on how to configure its behavior based on the `client_id` provided to it.</span></span>

## <a name="javascript-clients"></a><span data-ttu-id="88e10-153">JavaScript 클라이언트</span><span class="sxs-lookup"><span data-stu-id="88e10-153">JavaScript clients</span></span>

<span data-ttu-id="88e10-154">많은 클라우드 네이티브 응용 프로그램은 프런트 엔드에서 서버 쪽 Api 및 리치 클라이언트 SPAs (단일 페이지 응용 프로그램)를 활용 합니다.</span><span class="sxs-lookup"><span data-stu-id="88e10-154">Many cloud-native applications leverage server-side APIs and rich client single page applications (SPAs) on the front end.</span></span> <span data-ttu-id="88e10-155">IdentityServer는 [JavaScript client](https://docs.identityserver.io/en/latest/quickstarts/4_javascript_client.html) `oidc-client.js` 웹 api의 로그인, 로그 아웃 및 토큰 기반 인증을 위해 IdentityServer를 사용할 수 있도록 spas에 추가할 수 있는 NPM를 통해 JavaScript 클라이언트 ()를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="88e10-155">IdentityServer ships a [JavaScript client](https://docs.identityserver.io/en/latest/quickstarts/4_javascript_client.html) (`oidc-client.js`) via NPM that can be added to SPAs to enable them to use IdentityServer for sign in, sign out, and token-based authentication of web APIs.</span></span>

## <a name="references"></a><span data-ttu-id="88e10-156">참조</span><span class="sxs-lookup"><span data-stu-id="88e10-156">References</span></span>

- [<span data-ttu-id="88e10-157">IdentityServer 설명서</span><span class="sxs-lookup"><span data-stu-id="88e10-157">IdentityServer documentation</span></span>](https://docs.identityserver.io/en/latest/)
- [<span data-ttu-id="88e10-158">애플리케이션 형식</span><span class="sxs-lookup"><span data-stu-id="88e10-158">Application types</span></span>](/azure/active-directory/develop/app-types)
- [<span data-ttu-id="88e10-159">JavaScript OIDC 클라이언트</span><span class="sxs-lookup"><span data-stu-id="88e10-159">JavaScript OIDC client</span></span>](https://docs.identityserver.io/en/latest/quickstarts/4_javascript_client.html)

>[!div class="step-by-step"]
><span data-ttu-id="88e10-160">[이전](azure-active-directory.md)
>[다음](security.md)</span><span class="sxs-lookup"><span data-stu-id="88e10-160">[Previous](azure-active-directory.md)
[Next](security.md)</span></span>
