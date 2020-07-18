---
title: '.NET Framework 4.8, 4.7, 4.6 및 4.5 마이그레이션 가이드 '
description: 새 기능 및 애플리케이션 호환성에 대한 리소스가 포함된 최신 .NET Framework 버전으로 마이그레이션하기 위한 가이드입니다.
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- .NET Framework, migrating applications to
- migration, .NET Framework
ms.assetid: 02d55147-9b3a-4557-a45f-fa936fadae3b
ms.openlocfilehash: a5b632824efacdb5e99228727b8751dc7f17d363
ms.sourcegitcommit: 2543a78be6e246aa010a01decf58889de53d1636
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/17/2020
ms.locfileid: "86443418"
---
# <a name="migrate-to-net-framework-48-47-46-and-45"></a><span data-ttu-id="f3811-103">.NET Framework 4.8, 4.7, 4.6 및 4.5로 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="f3811-103">Migrate to .NET Framework 4.8, 4.7, 4.6, and 4.5</span></span>

<span data-ttu-id="f3811-104">이전 버전의 .NET Framework를 사용하여 앱을 만든 경우, 일반적으로 .NET Framework 4.5 및 해당 포인트 릴리스(4.5.1 및 4.5.2), .NET Framework 4.6 및 해당 포인트 릴리스(4.6.1 및 4.6.2), .NET Framework 4.7 및 해당 포인트 릴리스(4.7.1 및 4.7.2) 또는 .NET Framework 4.8로 쉽게 업그레이드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3811-104">If you created your app using an earlier version of .NET Framework, you can generally upgrade it to .NET Framework 4.5 and its point releases (4.5.1 and 4.5.2), .NET Framework 4.6 and its point releases (4.6.1 and 4.6.2), .NET Framework 4.7 and its point releases (4.7.1 and 4.7.2), or .NET Framework 4.8 easily.</span></span> <span data-ttu-id="f3811-105">Visual Studio에서 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f3811-105">Open your project in Visual Studio.</span></span> <span data-ttu-id="f3811-106">프로젝트가 이전 버전의 Visual Studio에서 만들어진 경우 **프로젝트 호환성** 대화 상자가 자동으로 열립니다.</span><span class="sxs-lookup"><span data-stu-id="f3811-106">If your project was created in an earlier version of Visual Studio, the **Project Compatibility** dialog box automatically opens.</span></span> <span data-ttu-id="f3811-107">Visual Studio에서 프로젝트를 업그레이드하는 방법에 대한 자세한 내용은 [Visual Studio 프로젝트 포팅, 마이그레이션, 업그레이드](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects) 및 [Visual Studio 2019 플랫폼 대상 지정 및 호환성](/visualstudio/releases/2019/compatibility)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f3811-107">For more information about upgrading a project in Visual Studio, see [Port, Migrate, and Upgrade Visual Studio Projects](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects) and [Visual Studio 2019 Platform Targeting and Compatibility](/visualstudio/releases/2019/compatibility).</span></span>

 <span data-ttu-id="f3811-108">그러나 .NET Framework에서 일부 사항을 변경하려면 코드를 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3811-108">However, some changes in .NET Framework require changes to your code.</span></span> <span data-ttu-id="f3811-109">.NET Framework 4.5 및 해당 포인트 릴리스, .NET Framework 4.6 및 해당 포인트 릴리스, .NET Framework 4.7 및 해당 포인트 릴리스 또는 .NET Framework 4.8의 새로운 기능을 활용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3811-109">You may also want to take advantage of functionality that is new in .NET Framework 4.5 and its point releases, in .NET Framework 4.6 and its point releases, in .NET Framework 4.7 and its point releases, or in .NET Framework 4.8.</span></span> <span data-ttu-id="f3811-110">새 버전의 .NET Framework용 앱을 변경하는 이러한 유형의 작업을 일반적으로 ‘마이그레이션’이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3811-110">Making these types of changes to your app for a new version of .NET Framework is typically referred to as *migration*.</span></span> <span data-ttu-id="f3811-111">앱을 마이그레이션할 필요가 없는 경우 다시 컴파일하지 않고 .NET Framework 4.5 이상 버전에서 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3811-111">If your app doesn't have to be migrated, you can run it in .NET Framework 4.5 or a later version without recompiling it.</span></span>

## <a name="migration-resources"></a><span data-ttu-id="f3811-112">마이그레이션 리소스</span><span class="sxs-lookup"><span data-stu-id="f3811-112">Migration resources</span></span>

<span data-ttu-id="f3811-113">이전 버전의 .NET Framework에서 버전 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2 또는 4.8로 앱을 마이그레이션하기 전에 다음 문서를 검토하세요.</span><span class="sxs-lookup"><span data-stu-id="f3811-113">Review the following documents before you migrate your app from earlier versions of .NET Framework to version 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2, or 4.8:</span></span>

- <span data-ttu-id="f3811-114">각 버전의 .NET Framework 내부에 있는 CLR 버전을 파악하고 앱을 대상으로 지정하기 위한 지침을 검토하려면 [버전 및 종속성](versions-and-dependencies.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f3811-114">See [Versions and Dependencies](versions-and-dependencies.md) to understand the CLR version underlying each version of the .NET Framework and to review guidelines for targeting your apps successfully.</span></span>

- <span data-ttu-id="f3811-115">앱에 영향을 줄 수 있는 런타임 및 대상 변경 관련 변경 내용과 이를 처리하는 방법을 알아보려면 [애플리케이션 호환성](application-compatibility.md)을 검토하십시오.</span><span class="sxs-lookup"><span data-stu-id="f3811-115">Review [Application compatibility](application-compatibility.md) to find out about runtime and retargeting changes that might affect your app and how to handle them.</span></span>

- <span data-ttu-id="f3811-116">코드에서 더 이상 사용되지 않는 형식 또는 멤버와 권장되는 대체 항목을 확인하려면 [클래스 라이브러리의 사용되지 않는 기능](../whats-new/whats-obsolete.md)을 검토하십시오.</span><span class="sxs-lookup"><span data-stu-id="f3811-116">Review [What's Obsolete in the Class Library](../whats-new/whats-obsolete.md) to determine any types or members in your code that have been made obsolete, and the recommended alternatives.</span></span>

- <span data-ttu-id="f3811-117">앱에 추가할 수 있는 새 기능에 대한 설명은 [새로운 기능](../whats-new/index.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f3811-117">See [What's New](../whats-new/index.md) for descriptions of new features that you may want to add to your app.</span></span>

## <a name="see-also"></a><span data-ttu-id="f3811-118">참조</span><span class="sxs-lookup"><span data-stu-id="f3811-118">See also</span></span>

- [<span data-ttu-id="f3811-119">애플리케이션 호환성</span><span class="sxs-lookup"><span data-stu-id="f3811-119">Application compatibility</span></span>](application-compatibility.md)
- [<span data-ttu-id="f3811-120">.NET Framework 1.1에서 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="f3811-120">Migrating from the .NET Framework 1.1</span></span>](migrating-from-the-net-framework-1-1.md)
- [<span data-ttu-id="f3811-121">버전 호환성</span><span class="sxs-lookup"><span data-stu-id="f3811-121">Version Compatibility</span></span>](version-compatibility.md)
- [<span data-ttu-id="f3811-122">버전 및 종속성</span><span class="sxs-lookup"><span data-stu-id="f3811-122">Versions and Dependencies</span></span>](versions-and-dependencies.md)
- [<span data-ttu-id="f3811-123">방법: .NET Framework 4 이상 버전을 지원하도록 앱 구성</span><span class="sxs-lookup"><span data-stu-id="f3811-123">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [<span data-ttu-id="f3811-124">새로운 기능</span><span class="sxs-lookup"><span data-stu-id="f3811-124">What's New</span></span>](../whats-new/index.md)
- [<span data-ttu-id="f3811-125">클래스 라이브러리의 사용되지 않는 기능</span><span class="sxs-lookup"><span data-stu-id="f3811-125">What's Obsolete in the Class Library</span></span>](../whats-new/whats-obsolete.md)
- [<span data-ttu-id="f3811-126">.NET Framework 공식 지원 정책</span><span class="sxs-lookup"><span data-stu-id="f3811-126">.NET Framework official support policy</span></span>](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)
- [<span data-ttu-id="f3811-127">.NET Framework 4 마이그레이션 문제</span><span class="sxs-lookup"><span data-stu-id="f3811-127">.NET Framework 4 migration issues</span></span>](net-framework-4-migration-issues.md)
