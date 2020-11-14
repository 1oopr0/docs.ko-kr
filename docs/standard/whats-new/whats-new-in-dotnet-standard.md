---
title: .NET Standard의 새로운 기능
description: 이 문서에는 .NET Standard의 각 새 버전에 있는 새로운 기능과 향상된 기능이 요약되어 있습니다.
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.technology: dotnet-standard
ms.openlocfilehash: 419988901923b890aaf0a540d155775214e62c52
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282105"
---
# <a name="whats-new-in-net-standard"></a><span data-ttu-id="e5b40-103">.NET Standard의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="e5b40-103">What's new in .NET Standard</span></span>

<span data-ttu-id="e5b40-104">.NET Standard는 해당 버전의 표준에 부합하는 .NET 구현체에서 사용할 수 있어야 하는 버전이 지정된 API 세트를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="e5b40-104">.NET Standard is a formal specification that defines a versioned set of APIs that must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="e5b40-105">.NET Standard는 라이브러리 개발자에서 대상으로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5b40-105">.NET Standard is targeted at library developers.</span></span> <span data-ttu-id="e5b40-106">.NET Standard 버전을 대상으로 하는 라이브러리는 Standard의 해당 버전을 지원하는 모든 .NET Framework, .NET Core 또는 Xamarin 구현체에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5b40-106">A library that targets a .NET Standard version can be used on any .NET Framework, .NET Core, or Xamarin implementation that supports that version of the standard.</span></span>

<span data-ttu-id="e5b40-107">.NET Standard는 .NET Core 워크로드를 선택하는 경우 Visual Studio뿐만 아니라 .NET Core SDK에도 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5b40-107">.NET Standard is included with the .NET Core SDK, as well as with Visual Studio when you select the .NET Core workload.</span></span>

## <a name="supported-net-implementations"></a><span data-ttu-id="e5b40-108">지원되는 .NET 구현체</span><span class="sxs-lookup"><span data-stu-id="e5b40-108">Supported .NET implementations</span></span>

<span data-ttu-id="e5b40-109">.NET Standard 2.0은 다음 .NET 구현체에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5b40-109">.NET Standard 2.0 is supported by the following .NET implementations:</span></span>

- <span data-ttu-id="e5b40-110">.NET Core 2.0 이상</span><span class="sxs-lookup"><span data-stu-id="e5b40-110">.NET Core 2.0 or later</span></span>
- <span data-ttu-id="e5b40-111">.NET Framework 4.6.1 이상</span><span class="sxs-lookup"><span data-stu-id="e5b40-111">.NET Framework 4.6.1 or later</span></span>
- <span data-ttu-id="e5b40-112">Mono 5.4 이상</span><span class="sxs-lookup"><span data-stu-id="e5b40-112">Mono 5.4 or later</span></span>
- <span data-ttu-id="e5b40-113">Xamarin.iOS 10.14 이상</span><span class="sxs-lookup"><span data-stu-id="e5b40-113">Xamarin.iOS 10.14 or later</span></span>
- <span data-ttu-id="e5b40-114">Xamarin.Mac 3.8 이상</span><span class="sxs-lookup"><span data-stu-id="e5b40-114">Xamarin.Mac 3.8 or later</span></span>
- <span data-ttu-id="e5b40-115">Xamarin.Android 8.0 이상</span><span class="sxs-lookup"><span data-stu-id="e5b40-115">Xamarin.Android 8.0 or later</span></span>
- <span data-ttu-id="e5b40-116">유니버설 Windows 플랫폼 10.0.16299 이상</span><span class="sxs-lookup"><span data-stu-id="e5b40-116">Universal Windows Platform 10.0.16299 or later</span></span>

## <a name="whats-new-in-net-standard-20"></a><span data-ttu-id="e5b40-117">.NET Standard 2.0의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="e5b40-117">What's new in .NET Standard 2.0</span></span>

<span data-ttu-id="e5b40-118">.NET Standard 2.0에는 다음과 같은 새로운 기능이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5b40-118">.NET Standard 2.0 includes the following new features:</span></span>

### <a name="a-vastly-expanded-set-of-apis"></a><span data-ttu-id="e5b40-119">매우 폭넓은 API 집합</span><span class="sxs-lookup"><span data-stu-id="e5b40-119">A vastly expanded set of APIs</span></span>

<span data-ttu-id="e5b40-120">버전 1.6에는 비교적 적은 .NET Standard API가 포함되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e5b40-120">Through version 1.6, .NET Standard included a comparatively small subset of APIs.</span></span> <span data-ttu-id="e5b40-121">여기에는 .NET Framework 또는 Xamarin에서 일반적으로 사용된 많은 API가 제외되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e5b40-121">Among those excluded were many APIs that were commonly used in .NET Framework or Xamarin.</span></span> <span data-ttu-id="e5b40-122">이로 인해 개발이 복잡해집니다. 개발자들이 여러 .NET 구현을 대상으로 하는 애플리케이션과 라이브러리를 개발할 때 친숙한 API에 대한 적합한 대체 API를 찾아야 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="e5b40-122">This complicates development, since it requires that developers find suitable replacements for familiar APIs when they develop applications and libraries that target multiple .NET implementations.</span></span> <span data-ttu-id="e5b40-123">.NET Standard 2.0은 이전 Standard 버전인 .NET Standard 1.6에서 제공된 것보다 20,000개 더 많은 API를 추가하여 이 제약 사항을 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="e5b40-123">.NET Standard 2.0 addresses this limitation by adding over 20,000 more APIs than were available in .NET Standard 1.6, the previous version of the standard.</span></span> <span data-ttu-id="e5b40-124">.NET Standard 2.0에 추가된 API의 목록은 [.NET Standard 2.0 및 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e5b40-124">For a list of the APIs that have been added to .NET Standard 2.0, see [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span>

<span data-ttu-id="e5b40-125">.NET Standard 2.0에서 <xref:System> 네임스페이스에 대해 추가된 기능의 일부는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e5b40-125">Some of the additions to the <xref:System> namespace in .NET Standard 2.0 include:</span></span>

- <span data-ttu-id="e5b40-126"><xref:System.AppDomain> 클래스에 대한 지원.</span><span class="sxs-lookup"><span data-stu-id="e5b40-126">Support for the <xref:System.AppDomain> class.</span></span>
- <span data-ttu-id="e5b40-127"><xref:System.Array> 클래스에 있는 추가 멤버의 배열을 사용하기 위한 향상된 지원.</span><span class="sxs-lookup"><span data-stu-id="e5b40-127">Better support for working with arrays from additional members in the <xref:System.Array> class.</span></span>
- <span data-ttu-id="e5b40-128"><xref:System.Attribute> 클래스에 있는 추가 멤버의 속성을 사용하기 위한 향상된 지원.</span><span class="sxs-lookup"><span data-stu-id="e5b40-128">Better support for working with attributes from additional members in the <xref:System.Attribute> class.</span></span>
- <span data-ttu-id="e5b40-129"><xref:System.DateTime> 값에 대한 향상된 달력 지원 및 추가 서식 옵션.</span><span class="sxs-lookup"><span data-stu-id="e5b40-129">Better calendar support and additional formatting options for <xref:System.DateTime> values.</span></span>
- <span data-ttu-id="e5b40-130">추가 <xref:System.Decimal> 반올림 기능.</span><span class="sxs-lookup"><span data-stu-id="e5b40-130">Additional <xref:System.Decimal> rounding functionality.</span></span>
- <span data-ttu-id="e5b40-131"><xref:System.Environment> 클래스의 추가 기능.</span><span class="sxs-lookup"><span data-stu-id="e5b40-131">Additional functionality in the <xref:System.Environment> class.</span></span>
- <span data-ttu-id="e5b40-132"><xref:System.GC> 클래스를 통해 가비지 수집기 제어 강화.</span><span class="sxs-lookup"><span data-stu-id="e5b40-132">Enhanced control over the garbage collector through the <xref:System.GC> class.</span></span>
- <span data-ttu-id="e5b40-133"><xref:System.String> 클래스의 문자열 비교, 열거 및 정규화를 위한 향상된 지원.</span><span class="sxs-lookup"><span data-stu-id="e5b40-133">Enhanced support for string comparison, enumeration, and normalization in the <xref:System.String> class.</span></span>
- <span data-ttu-id="e5b40-134"><xref:System.TimeZoneInfo.AdjustmentRule> 및 <xref:System.TimeZoneInfo.TransitionTime> 클래스의 일광 절약 조정 및 전환 시간에 대한 지원.</span><span class="sxs-lookup"><span data-stu-id="e5b40-134">Support for daylight saving adjustments and transition times in the <xref:System.TimeZoneInfo.AdjustmentRule> and <xref:System.TimeZoneInfo.TransitionTime> classes.</span></span>
- <span data-ttu-id="e5b40-135"><xref:System.Type> 클래스의 크게 향상된 기능.</span><span class="sxs-lookup"><span data-stu-id="e5b40-135">Significantly enhanced functionality in the <xref:System.Type> class.</span></span>
- <span data-ttu-id="e5b40-136"><xref:System.Runtime.Serialization.SerializationInfo> 및 <xref:System.Runtime.Serialization.StreamingContext> 매개 변수를 통해 예외 생성자를 추가하여 예외 개체를 역직렬화하는 기능에 대한 향상된 지원.</span><span class="sxs-lookup"><span data-stu-id="e5b40-136">Better support for deserialization of exception objects by adding an exception constructor with <xref:System.Runtime.Serialization.SerializationInfo> and <xref:System.Runtime.Serialization.StreamingContext> parameters.</span></span>

### <a name="support-for-net-framework-libraries"></a><span data-ttu-id="e5b40-137">.NET Framework 라이브러리에 대한 지원</span><span class="sxs-lookup"><span data-stu-id="e5b40-137">Support for .NET Framework libraries</span></span>

<span data-ttu-id="e5b40-138">많은 라이브러리는 .NET Standard가 아닌 .NET Framework를 대상으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5b40-138">Many libraries target .NET Framework rather than .NET Standard.</span></span> <span data-ttu-id="e5b40-139">그러나 이러한 라이브러리에서 대부분의 호출은 .NET Standard 2.0에 포함된 API를 대상으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5b40-139">However, most of the calls in those libraries are to APIs that are included in .NET Standard 2.0.</span></span> <span data-ttu-id="e5b40-140">.NET Standard 2.0부터는 [호환성 shim](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification)을 사용하여 .NET Standard 라이브러리에서 .NET Framework 라이브러리에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5b40-140">Starting with .NET Standard 2.0, you can access .NET Framework libraries from a .NET Standard library by using a [compatibility shim](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification).</span></span> <span data-ttu-id="e5b40-141">이 호환성 레이어는 개발자에게 투명하며, .NET Framework 라이브러리를 이용하기 위해 아무것도 할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e5b40-141">This compatibility layer is transparent to developers; you don't have to do anything to take advantage of .NET Framework libraries.</span></span>

<span data-ttu-id="e5b40-142">한 가지 요구 사항은 .NET Framework 클래스 라이브러리에서 호출하는 API가 .NET Standard 2.0에 포함되어야 한다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e5b40-142">The single requirement is that the APIs called by the .NET Framework class library must be included in .NET Standard 2.0.</span></span>

### <a name="support-for-visual-basic"></a><span data-ttu-id="e5b40-143">Visual Basic에 대한 지원</span><span class="sxs-lookup"><span data-stu-id="e5b40-143">Support for Visual Basic</span></span>

<span data-ttu-id="e5b40-144">이제 Visual Basic에서 .NET Standard 라이브러리를 개발할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5b40-144">You can now develop .NET Standard libraries in Visual Basic.</span></span> <span data-ttu-id="e5b40-145">.NET Core 워크로드가 설치된 Visual Studio 2019 및 Visual Studio 2017 버전 15.3 이상에는 .NET Standard 클래스 라이브러리 템플릿이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5b40-145">Visual Studio 2019 and Visual Studio 2017 version 15.3 or later with the .NET Core workload installed include a .NET Standard Class Library template.</span></span> <span data-ttu-id="e5b40-146">다른 개발 도구와 환경을 사용하는 Visual Basic 개발자의 경우 [dotnet new](../../core/tools/dotnet-new.md) 명령을 사용하여 .NET Standard 라이브러리 프로젝트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5b40-146">For Visual Basic developers who use other development tools and environments, you can use the [dotnet new](../../core/tools/dotnet-new.md) command to create a .NET Standard Library project.</span></span> <span data-ttu-id="e5b40-147">자세한 내용은 [.NET Standard 라이브러리에 대한 도구 지원](#tooling-support-for-net-standard-libraries)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e5b40-147">For more information, see the [Tooling support for .NET Standard libraries](#tooling-support-for-net-standard-libraries).</span></span>

### <a name="tooling-support-for-net-standard-libraries"></a><span data-ttu-id="e5b40-148">.NET Standard 라이브러리의 도구 지원</span><span class="sxs-lookup"><span data-stu-id="e5b40-148">Tooling support for .NET Standard libraries</span></span>

<span data-ttu-id="e5b40-149">.NET Core 2.0과 .NET Standard 2.0 릴리스에서는 Visual Studio 2017과 [.NET Core CLI](../../core/tools/index.md)에서 NET Standard 라이브러리를 만들기 위한 도구가 모두 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5b40-149">With the release of .NET Core 2.0 and .NET Standard 2.0, both Visual Studio 2017 and the [.NET Core CLI](../../core/tools/index.md) include tooling support for creating .NET Standard libraries.</span></span>

<span data-ttu-id="e5b40-150">**.NET Core 플랫폼 간 개발** 워크로드를 통해 Visual Studio를 설치하는 경우 다음 그림과 같이 프로젝트 템플릿을 사용하여 .NET Standard 2.0 라이브러리 프로젝트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5b40-150">If you install Visual Studio with the **.NET Core cross-platform development** workload, you can create a .NET Standard 2.0 library project by using a project template, as the following figure shows:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[<span data-ttu-id="e5b40-151">C#</span><span class="sxs-lookup"><span data-stu-id="e5b40-151">C#</span></span>](#tab/csharp)

![새 .NET Standard 라이브러리 프로젝트 추가](./media/std-project-cs.png)

<span data-ttu-id="e5b40-153">.NET Core CLI를 사용하는 경우 다음과 같이 [dotnet new](../../core/tools/dotnet-new.md) 명령을 통해 .NET Standard 2.0을 대상으로 하는 클래스 라이브러리 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e5b40-153">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets .NET Standard 2.0:</span></span>

```dotnetcli
dotnet new classlib
```

# <a name="visual-basic"></a>[<span data-ttu-id="e5b40-154">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e5b40-154">Visual Basic</span></span>](#tab/vb)

![새 .NET Standard 라이브러리 프로젝트 추가](./media/std-project-vb.png)

<span data-ttu-id="e5b40-156">.NET Core CLI를 사용하는 경우 다음과 같이 [dotnet new](../../core/tools/dotnet-new.md) 명령을 통해 .NET Standard 2.0을 대상으로 하는 클래스 라이브러리 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e5b40-156">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets .NET Standard 2.0:</span></span>

```dotnetcli
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a><span data-ttu-id="e5b40-157">참조</span><span class="sxs-lookup"><span data-stu-id="e5b40-157">See also</span></span>

- [<span data-ttu-id="e5b40-158">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="e5b40-158">.NET Standard</span></span>](../net-standard.md)
- [<span data-ttu-id="e5b40-159">.NET Standard 소개</span><span class="sxs-lookup"><span data-stu-id="e5b40-159">Introducing .NET Standard</span></span>](https://devblogs.microsoft.com/dotnet/introducing-net-standard/)
