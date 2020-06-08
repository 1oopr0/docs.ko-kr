---
title: -subsystemversion
ms.date: 03/13/2018
helpviewer_keywords:
- /subsystemversion compiler option [Visual Basic]
- -subsystemversion compiler option [Visual Basic]
- subsystemversion compiler option [Visual Basic]
ms.assetid: 08be22b2-f447-4cd3-8203-120b1b920b54
ms.openlocfilehash: 09ddc4bb735b645e09d34198c66dff78183592bf
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403085"
---
# <a name="-subsystemversion-visual-basic"></a><span data-ttu-id="7cfae-102">-subsystemversion(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7cfae-102">-subsystemversion (Visual Basic)</span></span>

<span data-ttu-id="7cfae-103">생성된 실행 파일을 실행할 수 있는 하위 시스템의 최소 버전을 지정하여 실행 파일을 실행할 수 있는 Windows 버전을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="7cfae-103">Specifies the minimum version of the subsystem on which the generated executable file can run, thereby determining the versions of Windows on which the executable file can run.</span></span> <span data-ttu-id="7cfae-104">가장 일반적으로, 이 옵션은 실행 파일이 이전 버전의 Windows에서 사용할 수 없는 특정 보안 기능을 활용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cfae-104">Most commonly, this option ensures that the executable file can leverage particular security features that aren’t available with older versions of Windows.</span></span>

> [!NOTE]
> <span data-ttu-id="7cfae-105">하위 시스템 자체를 지정하려면 [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) 컴파일러 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7cfae-105">To specify the subsystem itself, use the [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) compiler option.</span></span>

## <a name="syntax"></a><span data-ttu-id="7cfae-106">구문</span><span class="sxs-lookup"><span data-stu-id="7cfae-106">Syntax</span></span>

```vb
-subsystemversion:major.minor
```

## <a name="parameters"></a><span data-ttu-id="7cfae-107">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7cfae-107">Parameters</span></span>

`major.minor`

<span data-ttu-id="7cfae-108">주 버전과 부 버전의 점 표기법으로 표현된 필수 최소 버전의 하위 시스템입니다.</span><span class="sxs-lookup"><span data-stu-id="7cfae-108">The minimum required version of the subsystem, as expressed in a dot notation for major and minor versions.</span></span> <span data-ttu-id="7cfae-109">예를 들어 이 항목의 뒷부분에 나오는 표의 설명에 따라 이 옵션의 값을 6.01로 설정하는 경우 Windows 7 이전 운영 체제에서는 애플리케이션을 실행할 수 없도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cfae-109">For example, you can specify that an application can't run on an operating system that's older than Windows 7 if you set the value of this option to 6.01, as the table later in this topic describes.</span></span> <span data-ttu-id="7cfae-110">`major` 및 `minor`의 값을 정수로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cfae-110">You must specify the values for `major` and `minor` as integers.</span></span>

<span data-ttu-id="7cfae-111">`minor` 버전에서 선행 0은 버전을 변경하지 않지만 후행 0은 버전을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="7cfae-111">Leading zeroes in the `minor` version don't change the version, but trailing zeroes do.</span></span> <span data-ttu-id="7cfae-112">예를 들어 6.1과 6.01은 동일한 버전을 가리키지만 6.10은 다른 버전을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="7cfae-112">For example, 6.1 and 6.01 refer to the same version, but 6.10 refers to a different version.</span></span> <span data-ttu-id="7cfae-113">혼동을 피하기 위해 부 버전을 두 자리로 표현하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7cfae-113">We recommend expressing the minor version as two digits to avoid confusion.</span></span>

## <a name="remarks"></a><span data-ttu-id="7cfae-114">설명</span><span class="sxs-lookup"><span data-stu-id="7cfae-114">Remarks</span></span>

<span data-ttu-id="7cfae-115">다음 표에는 Windows의 일반적인 하위 시스템 버전이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cfae-115">The following table lists common subsystem versions of Windows.</span></span>

|<span data-ttu-id="7cfae-116">Windows 버전</span><span class="sxs-lookup"><span data-stu-id="7cfae-116">Windows version</span></span>|<span data-ttu-id="7cfae-117">하위 시스템 버전</span><span class="sxs-lookup"><span data-stu-id="7cfae-117">Subsystem version</span></span>|
|---------------------|-----------------------|
|<span data-ttu-id="7cfae-118">Windows 2000</span><span class="sxs-lookup"><span data-stu-id="7cfae-118">Windows 2000</span></span>|<span data-ttu-id="7cfae-119">5.00</span><span class="sxs-lookup"><span data-stu-id="7cfae-119">5.00</span></span>|
|<span data-ttu-id="7cfae-120">Windows XP</span><span class="sxs-lookup"><span data-stu-id="7cfae-120">Windows XP</span></span>|<span data-ttu-id="7cfae-121">5.01</span><span class="sxs-lookup"><span data-stu-id="7cfae-121">5.01</span></span>|
|<span data-ttu-id="7cfae-122">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="7cfae-122">Windows Server 2003</span></span>|<span data-ttu-id="7cfae-123">5.02</span><span class="sxs-lookup"><span data-stu-id="7cfae-123">5.02</span></span>|
|<span data-ttu-id="7cfae-124">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="7cfae-124">Windows Vista</span></span>|<span data-ttu-id="7cfae-125">6.00</span><span class="sxs-lookup"><span data-stu-id="7cfae-125">6.00</span></span>|
|<span data-ttu-id="7cfae-126">Windows 7</span><span class="sxs-lookup"><span data-stu-id="7cfae-126">Windows 7</span></span>|<span data-ttu-id="7cfae-127">6.01</span><span class="sxs-lookup"><span data-stu-id="7cfae-127">6.01</span></span>|
|<span data-ttu-id="7cfae-128">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="7cfae-128">Windows Server 2008</span></span>|<span data-ttu-id="7cfae-129">6.01</span><span class="sxs-lookup"><span data-stu-id="7cfae-129">6.01</span></span>|
|<span data-ttu-id="7cfae-130">Windows 8</span><span class="sxs-lookup"><span data-stu-id="7cfae-130">Windows 8</span></span>|<span data-ttu-id="7cfae-131">6.02</span><span class="sxs-lookup"><span data-stu-id="7cfae-131">6.02</span></span>|

## <a name="default-values"></a><span data-ttu-id="7cfae-132">기본값</span><span class="sxs-lookup"><span data-stu-id="7cfae-132">Default values</span></span>

<span data-ttu-id="7cfae-133">**-subsystemversion** 컴파일러 옵션의 기본값은 다음 목록의 조건에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="7cfae-133">The default value of the **-subsystemversion** compiler option depends on the conditions in the following list:</span></span>

- <span data-ttu-id="7cfae-134">다음 목록의 컴파일러 옵션이 설정된 경우 기본값은 6.02입니다.</span><span class="sxs-lookup"><span data-stu-id="7cfae-134">The default value is 6.02 if any compiler option in the following list is set:</span></span>

  - [<span data-ttu-id="7cfae-135">/target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="7cfae-135">-target:appcontainerexe</span></span>](target.md)

  - [<span data-ttu-id="7cfae-136">/target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="7cfae-136">-target:winmdobj</span></span>](target.md)

  - [<span data-ttu-id="7cfae-137">-platform:arm</span><span class="sxs-lookup"><span data-stu-id="7cfae-137">-platform:arm</span></span>](platform.md)

- <span data-ttu-id="7cfae-138">MSBuild를 사용하고 .NET Framework 4.5를 대상으로 하며, 이 목록의 앞에서 지정된 컴파일러 옵션 중 하나를 설정하지 않은 경우 기본값은 6.00입니다.</span><span class="sxs-lookup"><span data-stu-id="7cfae-138">The default value is 6.00 if you're using MSBuild, you're targeting .NET Framework 4.5, and you haven't set any of the compiler options that were specified earlier in this list.</span></span>

- <span data-ttu-id="7cfae-139">앞의 조건이 하나도 true가 아닌 경우 기본값은 4.00입니다.</span><span class="sxs-lookup"><span data-stu-id="7cfae-139">The default value is 4.00 if none of the previous conditions is true.</span></span>

## <a name="setting-this-option"></a><span data-ttu-id="7cfae-140">이 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="7cfae-140">Setting this option</span></span>

<span data-ttu-id="7cfae-141">Visual Studio에서 **-subsystemversion** 컴파일러 옵션을 설정하려면 .vbproj 파일을 열고 MSBuild XML에서 `SubsystemVersion` 속성의 값을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cfae-141">To set the **-subsystemversion** compiler option in Visual Studio, you must open the .vbproj file and specify a value for the `SubsystemVersion` property in the MSBuild XML.</span></span> <span data-ttu-id="7cfae-142">Visual Studio IDE에서는 이 옵션을 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7cfae-142">You can't set this option in the Visual Studio IDE.</span></span> <span data-ttu-id="7cfae-143">자세한 내용은 이 항목의 앞부분에 나오는 "기본값"이나 [일반적인 MSBuild 프로젝트 속성](/visualstudio/msbuild/common-msbuild-project-properties)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7cfae-143">For more information, see "Default values" earlier in this topic or [Common MSBuild Project Properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="see-also"></a><span data-ttu-id="7cfae-144">참조</span><span class="sxs-lookup"><span data-stu-id="7cfae-144">See also</span></span>

- [<span data-ttu-id="7cfae-145">Visual Basic 명령줄 컴파일러</span><span class="sxs-lookup"><span data-stu-id="7cfae-145">Visual Basic Command-Line Compiler</span></span>](index.md)

- [<span data-ttu-id="7cfae-146">MSBuild 속성</span><span class="sxs-lookup"><span data-stu-id="7cfae-146">MSBuild Properties</span></span>](/visualstudio/msbuild/msbuild-properties)
