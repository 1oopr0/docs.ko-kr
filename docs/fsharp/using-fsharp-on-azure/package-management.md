---
title: 'Azure 용 F #과 함께 패키지 관리 사용'
description: 'Paket 또는 Nuget을 사용 하 여 F # Azure 종속성 관리'
author: sylvanc
ms.date: 09/20/2016
ms.custom: devx-track-fsharp
ms.openlocfilehash: 011a363b264079599e8b7d402fe9896045b1fe04
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91100115"
---
# <a name="package-management-for-f-azure-dependencies"></a><span data-ttu-id="d3208-103">F# Azure 종속성에 대한 패키지 관리</span><span class="sxs-lookup"><span data-stu-id="d3208-103">Package Management for F# Azure Dependencies</span></span>

<span data-ttu-id="d3208-104">패키지 관리자를 사용 하면 Azure 개발용 패키지를 쉽게 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3208-104">Obtaining packages for Azure development is easy when you use a package manager.</span></span> <span data-ttu-id="d3208-105">두 옵션은 [Paket](https://fsprojects.github.io/Paket/) 및 [NuGet](https://www.nuget.org/)입니다.</span><span class="sxs-lookup"><span data-stu-id="d3208-105">The two options are [Paket](https://fsprojects.github.io/Paket/) and [NuGet](https://www.nuget.org/).</span></span>

## <a name="using-paket"></a><span data-ttu-id="d3208-106">Paket 사용</span><span class="sxs-lookup"><span data-stu-id="d3208-106">Using Paket</span></span>

<span data-ttu-id="d3208-107">[Paket](https://fsprojects.github.io/Paket/) 를 종속성 관리자로 사용 하는 경우 도구를 사용 하 여 `paket.exe` Azure 종속성을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3208-107">If you're using [Paket](https://fsprojects.github.io/Paket/) as your dependency manager, you can use the `paket.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="d3208-108">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="d3208-108">For example:</span></span>

```console
> paket add nuget WindowsAzure.Storage
```

<span data-ttu-id="d3208-109">또는 플랫폼 간 .NET 개발에 [Mono](https://www.mono-project.com/) 를 사용 하는 경우:</span><span class="sxs-lookup"><span data-stu-id="d3208-109">Or, if you're using [Mono](https://www.mono-project.com/) for cross-platform .NET development:</span></span>

```console
> mono paket.exe add nuget WindowsAzure.Storage
```

<span data-ttu-id="d3208-110">이렇게 하면 `WindowsAzure.Storage` 현재 디렉터리에 있는 프로젝트에 대 한 패키지 종속성 집합에 추가 되 `paket.dependencies` 고, 파일을 수정 하 고, 패키지를 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3208-110">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, modify the `paket.dependencies` file, and download the package.</span></span> <span data-ttu-id="d3208-111">이전에 종속성을 설정 했거나 다른 개발자가 종속성을 설정한 프로젝트를 사용 하는 경우 다음과 같이 종속성을 로컬로 해결 하 고 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3208-111">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

```console
> paket install
```

<span data-ttu-id="d3208-112">또는 Mono 개발용:</span><span class="sxs-lookup"><span data-stu-id="d3208-112">Or, for Mono development:</span></span>

```console
> mono paket.exe install
```

<span data-ttu-id="d3208-113">모든 패키지 종속성을 다음과 같은 최신 버전으로 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3208-113">You can update all your package dependencies to the latest version like this:</span></span>

```console
> paket update
```

<span data-ttu-id="d3208-114">또는 Mono 개발용:</span><span class="sxs-lookup"><span data-stu-id="d3208-114">Or, for Mono development:</span></span>

```console
> mono paket.exe update
```

## <a name="using-nuget"></a><span data-ttu-id="d3208-115">Nuget 사용</span><span class="sxs-lookup"><span data-stu-id="d3208-115">Using Nuget</span></span>

<span data-ttu-id="d3208-116">[NuGet](https://www.nuget.org/) 을 종속성 관리자로 사용 하는 경우 도구를 사용 하 여 `nuget.exe` Azure 종속성을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3208-116">If you're using [NuGet](https://www.nuget.org/) as your dependency manager, you can use the `nuget.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="d3208-117">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="d3208-117">For example:</span></span>

```console
> nuget install WindowsAzure.Storage -ExcludeVersion
```

<span data-ttu-id="d3208-118">또는 Mono 개발용:</span><span class="sxs-lookup"><span data-stu-id="d3208-118">Or, for Mono development:</span></span>

```console
> mono nuget.exe install WindowsAzure.Storage -ExcludeVersion
```

<span data-ttu-id="d3208-119">이렇게 하면 `WindowsAzure.Storage` 현재 디렉터리에 있는 프로젝트에 대 한 패키지 종속성 집합에 추가 되 고 패키지가 다운로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3208-119">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, and download the package.</span></span> <span data-ttu-id="d3208-120">이전에 종속성을 설정 했거나 다른 개발자가 종속성을 설정한 프로젝트를 사용 하는 경우 다음과 같이 종속성을 로컬로 해결 하 고 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3208-120">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

```console
> nuget restore
```

<span data-ttu-id="d3208-121">또는 Mono 개발용:</span><span class="sxs-lookup"><span data-stu-id="d3208-121">Or, for Mono development:</span></span>

```console
> mono nuget.exe restore
```

<span data-ttu-id="d3208-122">모든 패키지 종속성을 다음과 같은 최신 버전으로 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3208-122">You can update all your package dependencies to the latest version like this:</span></span>

```console
> nuget update
```

<span data-ttu-id="d3208-123">또는 Mono 개발용:</span><span class="sxs-lookup"><span data-stu-id="d3208-123">Or, for Mono development:</span></span>

```console
> mono nuget.exe update
```

## <a name="referencing-assemblies"></a><span data-ttu-id="d3208-124">어셈블리 참조</span><span class="sxs-lookup"><span data-stu-id="d3208-124">Referencing Assemblies</span></span>

<span data-ttu-id="d3208-125">F # 스크립트에서 패키지를 사용 하려면 지시문을 사용 하 여 패키지에 포함 된 어셈블리를 참조 해야 합니다 `#r` .</span><span class="sxs-lookup"><span data-stu-id="d3208-125">In order to use your packages in your F# script, you need to reference the assemblies included in the packages using a `#r` directive.</span></span> <span data-ttu-id="d3208-126">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="d3208-126">For example:</span></span>

```fsharp
> #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"
```

<span data-ttu-id="d3208-127">여기에서 볼 수 있듯이 DLL에 대 한 상대 경로와 전체 DLL 이름을 지정 해야 합니다 .이 이름은 패키지 이름과 정확 하 게 일치 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3208-127">As you can see, you'll need to specify the relative path to the DLL and the full DLL name, which may not be exactly the same as the package name.</span></span> <span data-ttu-id="d3208-128">경로에는 프레임 워크 버전 및 패키지 버전 번호가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3208-128">The path will include a framework version and possibly a package version number.</span></span> <span data-ttu-id="d3208-129">설치 된 모든 어셈블리를 찾으려면 Windows 명령줄에서 다음과 같이 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3208-129">To find all the installed assemblies, you can use something like this on a Windows command line:</span></span>

```console
> cd packages/WindowsAzure.Storage
> dir /s/b *.dll
```

<span data-ttu-id="d3208-130">또는 Unix 셸에서 다음과 같은 항목이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3208-130">Or in a Unix shell, something like this:</span></span>

```console
> find packages/WindowsAzure.Storage -name "*.dll"
```

<span data-ttu-id="d3208-131">이렇게 하면 설치 된 어셈블리에 대 한 경로가 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3208-131">This will give you the paths to the installed assemblies.</span></span> <span data-ttu-id="d3208-132">여기에서 프레임 워크 버전에 대 한 올바른 경로를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3208-132">From there, you can select the correct path for your framework version.</span></span>
