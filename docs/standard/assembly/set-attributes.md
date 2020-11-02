---
title: 어셈블리 특성 설정
description: 어셈블리 ID, 정보, 어셈블리 매니페스트 및 강력한 이름 특성을 포함하여 .NET 어셈블리에 어셈블리 특성을 설정할 수 있습니다.
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET], attributes
- assembly binding, attributes
- assembly manifest, attributes
ms.assetid: 36a98a81-b5b5-4c19-912a-11f91eff7f4e
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 32318d647dee8f3f397e3497e7c2da640bd492d0
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687678"
---
# <a name="set-assembly-attributes"></a><span data-ttu-id="67bd6-103">어셈블리 특성 설정</span><span class="sxs-lookup"><span data-stu-id="67bd6-103">Set assembly attributes</span></span>

<span data-ttu-id="67bd6-104">어셈블리 특성은 어셈블리에 대한 정보를 제공하는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-104">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="67bd6-105">특성은 다음과 같은 정보 집합으로 나뉩니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-105">The attributes are divided into the following sets of information:</span></span>

- <span data-ttu-id="67bd6-106">어셈블리 ID 특성</span><span class="sxs-lookup"><span data-stu-id="67bd6-106">Assembly identity attributes</span></span>

- <span data-ttu-id="67bd6-107">정보 특성</span><span class="sxs-lookup"><span data-stu-id="67bd6-107">Informational attributes</span></span>

- <span data-ttu-id="67bd6-108">어셈블리 매니페스트 특성</span><span class="sxs-lookup"><span data-stu-id="67bd6-108">Assembly manifest attributes</span></span>

- <span data-ttu-id="67bd6-109">강력한 이름 특성</span><span class="sxs-lookup"><span data-stu-id="67bd6-109">Strong name attributes</span></span>

## <a name="assembly-identity-attributes"></a><span data-ttu-id="67bd6-110">어셈블리 ID 특성</span><span class="sxs-lookup"><span data-stu-id="67bd6-110">Assembly identity attributes</span></span>

<span data-ttu-id="67bd6-111">강력한 이름(해당하는 경우)과 더불어 name, version 및 culture의 세 가지 특성이 어셈블리의 ID를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-111">Three attributes, together with a strong name (if applicable), determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="67bd6-112">이러한 특성은 어셈블리의 전체 이름을 구성하며 코드에서 어셈블리를 참조할 때 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-112">These attributes form the full name of the assembly and are required when referencing the assembly in code.</span></span> <span data-ttu-id="67bd6-113">특성을 사용하여 어셈블리의 버전 및 문화권을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-113">You can use attributes to set an assembly's version and culture.</span></span> <span data-ttu-id="67bd6-114">컴파일러 또는 [어셈블리 링커(Al.exe)](../../framework/tools/al-exe-assembly-linker.md) 는 어셈블리 매니페스트를 포함하는 파일에 따라 어셈블리가 만들어질 때 이름 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-114">The compiler or the [Assembly Linker (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) sets the name value when the assembly is created, based on the file containing the assembly manifest.</span></span>

<span data-ttu-id="67bd6-115">다음 표에서는 version 및 culture 특성에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-115">The following table describes the version and culture attributes.</span></span>

|<span data-ttu-id="67bd6-116">어셈블리 ID 특성</span><span class="sxs-lookup"><span data-stu-id="67bd6-116">Assembly identity attribute</span></span>|<span data-ttu-id="67bd6-117">설명</span><span class="sxs-lookup"><span data-stu-id="67bd6-117">Description</span></span>|
|---------------------------------|-----------------|
|<xref:System.Reflection.AssemblyCultureAttribute>|<span data-ttu-id="67bd6-118">어셈블리에서 지원하는 문화권을 나타내는 열거형 필드입니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-118">Enumerated field indicating the culture that the assembly supports.</span></span> <span data-ttu-id="67bd6-119">어셈블리는 기본 문화권에 대한 리소스가 포함되어 있음을 나타내는 문화권 독립성을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-119">An assembly can also specify culture independence, indicating that it contains the resources for the default culture.</span></span> <span data-ttu-id="67bd6-120">**참고:**  런타임은 culture 특성이 null로 설정되어 있지 않은 모든 어셈블리를 위성 어셈블리로 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-120">**Note:**  The runtime treats any assembly that does not have the culture attribute set to null as a satellite assembly.</span></span> <span data-ttu-id="67bd6-121">이러한 어셈블리에는 위성 어셈블리 바인딩 규칙이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-121">Such assemblies are subject to satellite assembly binding rules.</span></span> <span data-ttu-id="67bd6-122">자세한 내용은 [런타임에서 어셈블리를 찾는 방법](../../framework/deployment/how-the-runtime-locates-assemblies.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="67bd6-122">For more information, see [How the runtime locates assemblies](../../framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>|
|<xref:System.Reflection.AssemblyFlagsAttribute>|<span data-ttu-id="67bd6-123">어셈블리를 병렬로 실행할 수 있는지 여부와 같은 어셈블리 특성을 설정하는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-123">Value that sets assembly attributes, such as whether the assembly can be run side by side.</span></span>|
|<xref:System.Reflection.AssemblyVersionAttribute>|<span data-ttu-id="67bd6-124">*major* . *minor* . *build* . *revision* 형식의 숫자 값입니다(예: 2.4.0.0).</span><span class="sxs-lookup"><span data-stu-id="67bd6-124">Numeric value in the format *major* . *minor* . *build* . *revision* (for example, 2.4.0.0).</span></span> <span data-ttu-id="67bd6-125">공용 언어 런타임은 이 값을 사용하여 강력한 이름의 어셈블리에서 바인딩 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-125">The common language runtime uses this value to perform binding operations in strong-named assemblies.</span></span> <span data-ttu-id="67bd6-126">**참고:**  <xref:System.Reflection.AssemblyInformationalVersionAttribute> 특성이 어셈블리에 적용되어 있지 않은 경우 <xref:System.Reflection.AssemblyVersionAttribute> 특성으로 지정된 버전 번호가 <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType>, <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> 및 <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> 속성에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-126">**Note:**  If the <xref:System.Reflection.AssemblyInformationalVersionAttribute> attribute is not applied to an assembly, the version number specified by the <xref:System.Reflection.AssemblyVersionAttribute> attribute is used by the <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType>, <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType>, and <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> properties.</span></span>|

<span data-ttu-id="67bd6-127">다음 코드 예제에서는 어셈블리에 version 및 culture 특성을 적용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-127">The following code example shows how to apply the version and culture attributes to an assembly.</span></span>

```cpp
// Set version number for the assembly.
[assembly:AssemblyVersionAttribute("4.3.2.1")];
// Set culture as German.
[assembly:AssemblyCultureAttribute("de")];
```

```csharp
// Set version number for the assembly.
[assembly:AssemblyVersionAttribute("4.3.2.1")]
// Set culture as German.
[assembly:AssemblyCultureAttribute("de")]
```

```vb
' Set version number for the assembly.
<Assembly:AssemblyVersionAttribute("4.3.2.1")>
' Set culture as German.
<Assembly:AssemblyCultureAttribute("de")>
```

## <a name="informational-attributes"></a><span data-ttu-id="67bd6-128">정보 특성</span><span class="sxs-lookup"><span data-stu-id="67bd6-128">Informational attributes</span></span>

<span data-ttu-id="67bd6-129">정보 특성을 사용하여 어셈블리와 연관된 회사 또는 제품에 대한 추가적인 정보를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-129">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="67bd6-130">다음 표에서는 어셈블리에 적용할 수 있는 정보 특성에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-130">The following table describes the informational attributes you can apply to an assembly.</span></span>

|<span data-ttu-id="67bd6-131">정보 특성</span><span class="sxs-lookup"><span data-stu-id="67bd6-131">Informational attribute</span></span>|<span data-ttu-id="67bd6-132">설명</span><span class="sxs-lookup"><span data-stu-id="67bd6-132">Description</span></span>|
|-----------------------------|-----------------|
|<xref:System.Reflection.AssemblyCompanyAttribute>|<span data-ttu-id="67bd6-133">회사 이름을 지정하는 문자열 값입니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-133">String value specifying a company name.</span></span>|
|<xref:System.Reflection.AssemblyCopyrightAttribute>|<span data-ttu-id="67bd6-134">저작권 정보를 지정하는 문자열 값입니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-134">String value specifying copyright information.</span></span>|
|<xref:System.Reflection.AssemblyFileVersionAttribute>|<span data-ttu-id="67bd6-135">Win32 파일 버전 번호를 지정하는 문자열 값입니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-135">String value specifying the Win32 file version number.</span></span> <span data-ttu-id="67bd6-136">기본값은 일반적으로 어셈블리 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-136">This normally defaults to the assembly version.</span></span>|
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|<span data-ttu-id="67bd6-137">전체 제품 버전 번호와 같이 공용 언어 런타임에서 사용되지 않는 버전 정보를 지정하는 문자열 값입니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-137">String value specifying version information that is not used by the common language runtime, such as a full product version number.</span></span> <span data-ttu-id="67bd6-138">**참고:**  이 특성이 어셈블리에 적용된 경우 <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType> 속성을 사용하여 런타임에 지정하는 문자열을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-138">**Note:**  If this attribute is applied to an assembly, the string it specifies can be obtained at run time by using the <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="67bd6-139">문자열은 <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> 및 <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> 속성이 제공하는 경로 및 레지스트리 키에서도 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-139">The string is also used in the path and registry key provided by the <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> and <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> properties.</span></span>|
|<xref:System.Reflection.AssemblyProductAttribute>|<span data-ttu-id="67bd6-140">제품 정보를 지정하는 문자열 값입니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-140">String value specifying product information.</span></span>|
|<xref:System.Reflection.AssemblyTrademarkAttribute>|<span data-ttu-id="67bd6-141">상표 정보를 지정하는 문자열 값입니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-141">String value specifying trademark information.</span></span>|

<span data-ttu-id="67bd6-142">이러한 특성은 어셈블리의 Windows 속성 페이지에 표시될 수 있거나, **/win32res** 컴파일러 옵션을 통해 사용자 고유의 Win32 리소스 파일을 지정하여 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-142">These attributes can appear on the Windows Properties page of the assembly, or they can be overridden using the **/win32res** compiler option to specify your own Win32 resource file.</span></span>

## <a name="assembly-manifest-attributes"></a><span data-ttu-id="67bd6-143">어셈블리 매니페스트 특성</span><span class="sxs-lookup"><span data-stu-id="67bd6-143">Assembly manifest attributes</span></span>

<span data-ttu-id="67bd6-144">어셈블리 매니페스트 특성을 사용하여 제목, 설명, 기본 별칭 및 구성을 비롯한 어셈블리 매니페스트의 정보를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-144">You can use assembly manifest attributes to provide information in the assembly manifest, including title, description, the default alias, and configuration.</span></span> <span data-ttu-id="67bd6-145">다음 표에서는 어셈블리 매니페스트 특성에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-145">The following table describes the assembly manifest attributes.</span></span>

|<span data-ttu-id="67bd6-146">어셈블리 매니페스트 특성</span><span class="sxs-lookup"><span data-stu-id="67bd6-146">Assembly manifest attribute</span></span>|<span data-ttu-id="67bd6-147">설명</span><span class="sxs-lookup"><span data-stu-id="67bd6-147">Description</span></span>|
|---------------------------------|-----------------|
|<xref:System.Reflection.AssemblyConfigurationAttribute>|<span data-ttu-id="67bd6-148">일반 정품 또는 디버그와 같은 어셈블리 구성을 나타내는 문자열 값입니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-148">String value indicating the configuration of the assembly, such as Retail or Debug.</span></span> <span data-ttu-id="67bd6-149">런타임에서는 이 값을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-149">The runtime does not use this value.</span></span>|
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|<span data-ttu-id="67bd6-150">어셈블리를 참조하여 사용할 기본 별칭을 지정하는 문자열 값입니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-150">String value specifying a default alias to be used by referencing assemblies.</span></span> <span data-ttu-id="67bd6-151">이 값은 어셈블리 이름 자체가 친숙하지 않은 경우(예: GUID 값) 친숙한 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-151">This value provides a friendly name when the name of the assembly itself is not friendly (such as a GUID value).</span></span> <span data-ttu-id="67bd6-152">이 값을 전체 어셈블리 이름의 짧은 형태로 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-152">This value can also be used as a short form of the full assembly name.</span></span>|
|<xref:System.Reflection.AssemblyDescriptionAttribute>|<span data-ttu-id="67bd6-153">어셈블리의 특성과 용도를 요약하는 간단한 설명을 지정하는 문자열 값입니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-153">String value specifying a short description that summarizes the nature and purpose of the assembly.</span></span>|
|<xref:System.Reflection.AssemblyTitleAttribute>|<span data-ttu-id="67bd6-154">어셈블리에 대한 친숙한 이름을 지정하는 문자열 값입니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-154">String value specifying a friendly name for the assembly.</span></span> <span data-ttu-id="67bd6-155">예를 들어 *comdlg* 라는 어셈블리에 Microsoft 공용 대화 상자 컨트롤이라는 제목이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-155">For example, an assembly named *comdlg* might have the title Microsoft Common Dialog Control.</span></span>|

## <a name="strong-name-attributes"></a><span data-ttu-id="67bd6-156">강력한 이름 특성</span><span class="sxs-lookup"><span data-stu-id="67bd6-156">Strong name attributes</span></span>

<span data-ttu-id="67bd6-157">강력한 이름 특성을 사용하여 어셈블리에 대한 강력한 이름을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-157">You can use strong name attributes to set a strong name for an assembly.</span></span> <span data-ttu-id="67bd6-158">다음 표에서는 강력한 이름 특성에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-158">The following table describes the strong name attributes.</span></span>

|<span data-ttu-id="67bd6-159">강력한 이름 특성</span><span class="sxs-lookup"><span data-stu-id="67bd6-159">Strong name attribute</span></span>|<span data-ttu-id="67bd6-160">설명</span><span class="sxs-lookup"><span data-stu-id="67bd6-160">Description</span></span>|
|----------------------------|-----------------|
|<xref:System.Reflection.AssemblyDelaySignAttribute>|<span data-ttu-id="67bd6-161">서명 연기가 사용되고 있음을 나타내는 부울 값입니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-161">Boolean value indicating that delay signing is being used.</span></span>|
|<xref:System.Reflection.AssemblyKeyFileAttribute>|<span data-ttu-id="67bd6-162">이 특성의 생성자에 매개 변수로 전달되는 퍼블릭 키(서명 연기를 사용하는 경우) 또는 퍼블릭 키와 프라이빗 키 둘 다의 이름을 포함하는 파일의 이름을 나타내는 문자열 값입니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-162">String value indicating the name of the file that contains either the public key (if using delay signing) or both the public and private keys passed as a parameter to the constructor of this attribute.</span></span> <span data-ttu-id="67bd6-163">파일 이름은 원본 파일 경로가 아니라 출력 파일 경로( *.exe* 또는 *.dll* )를 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-163">Note that the file name is relative to the output file path (the *.exe* or *.dll* ), not the source file path.</span></span>|
|<xref:System.Reflection.AssemblyKeyNameAttribute>|<span data-ttu-id="67bd6-164">이 특성의 생성자에 매개 변수로 전달되는 키 쌍을 포함하는 키 컨테이너를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-164">Indicates the key container that contains the key pair passed as a parameter to the constructor of this attribute.</span></span>|

<span data-ttu-id="67bd6-165">다음 코드 예제에서는 *myKey.snk* 라는 공개 키 파일과 함께 지연 서명을 사용하여 강력한 이름의 어셈블리를 만들 때 적용할 특성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="67bd6-165">The following code example shows the attributes to apply when using delay signing to create a strong-named assembly with a public key file called *myKey.snk* .</span></span>

```cpp
[assembly:AssemblyKeyFileAttribute("myKey.snk")];
[assembly:AssemblyDelaySignAttribute(true)];
```

```csharp
[assembly:AssemblyKeyFileAttribute("myKey.snk")]
[assembly:AssemblyDelaySignAttribute(true)]
```

```vb
<Assembly:AssemblyKeyFileAttribute("myKey.snk")>
<Assembly:AssemblyDelaySignAttribute(True)>
```

## <a name="see-also"></a><span data-ttu-id="67bd6-166">참조</span><span class="sxs-lookup"><span data-stu-id="67bd6-166">See also</span></span>

- [<span data-ttu-id="67bd6-167">어셈블리 만들기</span><span class="sxs-lookup"><span data-stu-id="67bd6-167">Create assemblies</span></span>](create.md)
