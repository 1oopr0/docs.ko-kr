---
title: 어셈블리 만들기
description: Visual Studio 등의 IDE 또는 Windows SDK에서 제공된 컴파일러와 도구를 사용하여 단일 파일 또는 다중 파일 어셈블리를 만드는 방법을 알아봅니다.
ms.date: 08/19/2019
helpviewer_keywords:
- assemblies [.NET], multifile
- single-file assemblies
- assemblies [.NET], creating
- multifile assemblies
ms.assetid: 54832ee9-dca8-4c8b-913c-c0b9d265e9a4
ms.openlocfilehash: e1b08e40ae3b4c377cec52cb1ebf6db643af6429
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160583"
---
# <a name="create-assemblies"></a><span data-ttu-id="d5ca3-103">어셈블리 만들기</span><span class="sxs-lookup"><span data-stu-id="d5ca3-103">Create assemblies</span></span>

<span data-ttu-id="d5ca3-104">Visual Studio 등의 IDE 또는 Windows SDK에서 제공된 컴파일러와 도구를 사용하여 단일 파일 또는 다중 파일 어셈블리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-104">You can create single-file or multifile assemblies using an IDE, such as Visual Studio, or the compilers and tools provided by the Windows SDK.</span></span> <span data-ttu-id="d5ca3-105">가장 단순한 어셈블리는 간단한 이름을 가지고 단일 애플리케이션 도메인에 로드되는 단일 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-105">The simplest assembly is a single file that has a simple name and is loaded into a single application domain.</span></span> <span data-ttu-id="d5ca3-106">이 어셈블리는 애플리케이션 디렉터리 외부에 있는 다른 어셈블리가 참조할 수 없고 버전 확인이 진행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-106">This assembly cannot be referenced by other assemblies outside the application directory and does not undergo version checking.</span></span> <span data-ttu-id="d5ca3-107">어셈블리로 구성된 애플리케이션을 제거하려면 어셈블리가 있는 디렉터리를 삭제하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-107">To uninstall the application made up of the assembly, you simply delete the directory where it resides.</span></span> <span data-ttu-id="d5ca3-108">대부분 개발자의 경우 애플리케이션을 배포하는 데는 이러한 기능이 포함된 어셈블리만 있으면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-108">For many developers, an assembly with these features is all that is needed to deploy an application.</span></span>

<span data-ttu-id="d5ca3-109">여러 코드 모듈 및 리소스 파일에서 복수 파일 어셈블리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-109">You can create a multifile assembly from several code modules and resource files.</span></span> <span data-ttu-id="d5ca3-110">여러 애플리케이션에서 공유될 수 있는 어셈블리를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-110">You can also create an assembly that can be shared by multiple applications.</span></span> <span data-ttu-id="d5ca3-111">공유 어셈블리에는 강력한 이름이 있어야 하고 공유 어셈블리는 전역 어셈블리 캐시에 배포될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-111">A shared assembly must have a strong name and can be deployed in the global assembly cache.</span></span>

<span data-ttu-id="d5ca3-112">코드 모듈 및 리소스를 어셈블리로 그룹화할 경우 다음 요소에 따라 여러 가지 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-112">You have several options when grouping code modules and resources into assemblies, depending on the following factors:</span></span>

- <span data-ttu-id="d5ca3-113">버전 관리</span><span class="sxs-lookup"><span data-stu-id="d5ca3-113">Versioning</span></span>

     <span data-ttu-id="d5ca3-114">같은 버전 정보를 포함해야 하는 모듈을 그룹화합니다.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-114">Group modules that should have the same version information.</span></span>

- <span data-ttu-id="d5ca3-115">배포</span><span class="sxs-lookup"><span data-stu-id="d5ca3-115">Deployment</span></span>

     <span data-ttu-id="d5ca3-116">배포 모델을 지원하는 코드 모듈 및 리소스를 그룹화합니다.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-116">Group code modules and resources that support your model of deployment.</span></span>

- <span data-ttu-id="d5ca3-117">재사용</span><span class="sxs-lookup"><span data-stu-id="d5ca3-117">Reuse</span></span>

     <span data-ttu-id="d5ca3-118">몇 가지 목적으로 모듈이 논리적으로 함께 사용될 수 있는 경우 모듈을 그룹화합니다.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-118">Group modules if they can be logically used together for some purpose.</span></span> <span data-ttu-id="d5ca3-119">예를 들어 가끔 프로그램 유지 관리에 사용되는 형식 및 클래스로 구성되는 어셈블리는 같은 어셈블리에 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-119">For example, an assembly consisting of types and classes used infrequently for program maintenance can be put in the same assembly.</span></span> <span data-ttu-id="d5ca3-120">또한 여러 애플리케이션과 공유하려는 형식은 어셈블리로 그룹화되어야 하고 해당 어셈블리는 강력한 이름으로 서명되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-120">In addition, types that you intend to share with multiple applications should be grouped into an assembly and the assembly should be signed with a strong name.</span></span>

- <span data-ttu-id="d5ca3-121">보안</span><span class="sxs-lookup"><span data-stu-id="d5ca3-121">Security</span></span>

     <span data-ttu-id="d5ca3-122">같은 보안 권한이 필요한 형식이 포함된 모듈을 그룹화합니다.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-122">Group modules containing types that require the same security permissions.</span></span>

- <span data-ttu-id="d5ca3-123">범위 지정</span><span class="sxs-lookup"><span data-stu-id="d5ca3-123">Scoping</span></span>

     <span data-ttu-id="d5ca3-124">표시 유형을 같은 어셈블리로 제한해야 하는 형식이 포함된 모듈을 그룹화합니다.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-124">Group modules containing types whose visibility should be restricted to the same assembly.</span></span>

<span data-ttu-id="d5ca3-125">공용 언어 런타임 어셈블리를 비관리 COM 애플리케이션에서 사용할 수 있도록 하려면 특별히 고려해야 할 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-125">There are special considerations when making common language runtime assemblies available to unmanaged COM applications.</span></span> <span data-ttu-id="d5ca3-126">비관리 코드 사용에 대한 자세한 내용은 [.NET Framework 구성 요소를 COM에 노출](../../framework/interop/exposing-dotnet-components-to-com.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d5ca3-126">For more information about working with unmanaged code, see [Expose .NET Framework components to COM](../../framework/interop/exposing-dotnet-components-to-com.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d5ca3-127">참조</span><span class="sxs-lookup"><span data-stu-id="d5ca3-127">See also</span></span>

- [<span data-ttu-id="d5ca3-128">어셈블리 버전 관리</span><span class="sxs-lookup"><span data-stu-id="d5ca3-128">Assembly versioning</span></span>](versioning.md)
- [<span data-ttu-id="d5ca3-129">방법: 단일 파일 어셈블리 빌드</span><span class="sxs-lookup"><span data-stu-id="d5ca3-129">How to: Build a single-file assembly</span></span>](../../framework/app-domains/build-single-file-assembly.md)
- [<span data-ttu-id="d5ca3-130">방법: 다중 파일 어셈블리 빌드</span><span class="sxs-lookup"><span data-stu-id="d5ca3-130">How to: Build a multifile assembly</span></span>](../../framework/app-domains/build-multifile-assembly.md)
- [<span data-ttu-id="d5ca3-131">런타임에서 어셈블리를 찾는 방법</span><span class="sxs-lookup"><span data-stu-id="d5ca3-131">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="d5ca3-132">다중 파일 어셈블리</span><span class="sxs-lookup"><span data-stu-id="d5ca3-132">Multifile assemblies</span></span>](../../framework/app-domains/multifile-assemblies.md)
