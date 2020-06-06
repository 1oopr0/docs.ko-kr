---
title: <supportPortability> 요소
ms.date: 03/30/2017
helpviewer_keywords:
- supportPortability element
- <supportPortability> element
ms.assetid: 6453ef66-19b4-41f3-b712-52d0c2abc9ca
ms.openlocfilehash: 63c309a8a93c1d31ed8f73a495cf5154c3590d56
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73115649"
---
# <a name="supportportability-element"></a><span data-ttu-id="01659-102">\<supportPortability> 요소</span><span class="sxs-lookup"><span data-stu-id="01659-102">\<supportPortability> Element</span></span>
<span data-ttu-id="01659-103">애플리케이션 이식성을 위해 어셈블리를 동일하게 간주하는 기본 동작을 사용하지 않도록 설정함으로써, 애플리케이션이 .NET Framework의 서로 다른 두 구현에서 같은 어셈블리를 참조할 수 있도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="01659-103">Specifies that an application can reference the same assembly in two different implementations of the .NET Framework, by disabling the default behavior that treats the assemblies as equivalent for application portability purposes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<supportPortability>**  
  
## <a name="syntax"></a><span data-ttu-id="01659-104">구문</span><span class="sxs-lookup"><span data-stu-id="01659-104">Syntax</span></span>  
  
```xml  
<supportPortability PKT="public_key_token" enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="01659-105">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="01659-105">Attributes and Elements</span></span>  

<span data-ttu-id="01659-106">다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="01659-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="01659-107">특성</span><span class="sxs-lookup"><span data-stu-id="01659-107">Attributes</span></span>  
  
|<span data-ttu-id="01659-108">attribute</span><span class="sxs-lookup"><span data-stu-id="01659-108">Attribute</span></span>|<span data-ttu-id="01659-109">Description</span><span class="sxs-lookup"><span data-stu-id="01659-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="01659-110">PKT</span><span class="sxs-lookup"><span data-stu-id="01659-110">PKT</span></span>|<span data-ttu-id="01659-111">필수 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="01659-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="01659-112">영향을 받는 어셈블리의 공개 키 토큰을 문자열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="01659-112">Specifies the public key token of the affected assembly, as a string.</span></span>|  
|<span data-ttu-id="01659-113">사용</span><span class="sxs-lookup"><span data-stu-id="01659-113">enabled</span></span>|<span data-ttu-id="01659-114">선택적 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="01659-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="01659-115">지정 된 .NET Framework 어셈블리의 구현 간 이식성에 대 한 지원을 사용 하도록 설정할지 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="01659-115">Specifies whether support for portability between implementations of the specified .NET Framework assembly should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="01659-116">enabled 특성</span><span class="sxs-lookup"><span data-stu-id="01659-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="01659-117">값</span><span class="sxs-lookup"><span data-stu-id="01659-117">Value</span></span>|<span data-ttu-id="01659-118">Description</span><span class="sxs-lookup"><span data-stu-id="01659-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="01659-119">true</span><span class="sxs-lookup"><span data-stu-id="01659-119">true</span></span>|<span data-ttu-id="01659-120">지정 된 .NET Framework 어셈블리의 구현 간 이식성에 대 한 지원을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="01659-120">Enable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="01659-121">기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="01659-121">This is the default.</span></span>|  
|<span data-ttu-id="01659-122">false</span><span class="sxs-lookup"><span data-stu-id="01659-122">false</span></span>|<span data-ttu-id="01659-123">지정 된 .NET Framework 어셈블리의 구현 간 이식성에 대 한 지원을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="01659-123">Disable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="01659-124">이렇게 하면 응용 프로그램에서 지정 된 어셈블리의 여러 구현에 대 한 참조를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01659-124">This enables the application to have references to multiple implementations of the specified assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="01659-125">자식 요소</span><span class="sxs-lookup"><span data-stu-id="01659-125">Child Elements</span></span>  

<span data-ttu-id="01659-126">없음</span><span class="sxs-lookup"><span data-stu-id="01659-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="01659-127">부모 요소</span><span class="sxs-lookup"><span data-stu-id="01659-127">Parent Elements</span></span>  
  
|<span data-ttu-id="01659-128">요소</span><span class="sxs-lookup"><span data-stu-id="01659-128">Element</span></span>|<span data-ttu-id="01659-129">Description</span><span class="sxs-lookup"><span data-stu-id="01659-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="01659-130">공용 언어 런타임 및 .NET Framework 애플리케이션에서 사용하는 모든 구성 파일의 루트 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="01659-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="01659-131">어셈블리 바인딩 및 가비지 컬렉션에 대한 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="01659-131">Contains information about assembly binding and garbage collection.</span></span>|  
|`assemblyBinding`|<span data-ttu-id="01659-132">어셈블리 버전 리디렉션 및 어셈블리 위치에 대한 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="01659-132">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01659-133">설명</span><span class="sxs-lookup"><span data-stu-id="01659-133">Remarks</span></span>  

<span data-ttu-id="01659-134">.NET Framework 4부터 .NET Framework의 두 구현 중 하나를 사용할 수 있는 응용 프로그램에 대 한 지원이 자동으로 제공 됩니다 (예: .NET Framework 구현 또는 Silverlight 구현을 위한 .NET Framework).</span><span class="sxs-lookup"><span data-stu-id="01659-134">Beginning with the .NET Framework 4, support is automatically provided for applications that can use either of two implementations of the .NET Framework, for example either the .NET Framework implementation or the .NET Framework for Silverlight implementation.</span></span> <span data-ttu-id="01659-135">특정 .NET Framework 어셈블리의 두 구현은 어셈블리 바인더에 의해 동등 하 게 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="01659-135">The two implementations of a particular .NET Framework assembly are seen as equivalent by the assembly binder.</span></span> <span data-ttu-id="01659-136">일부 시나리오에서는이 응용 프로그램 이식성 기능으로 인해 문제가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="01659-136">In a few scenarios, this application portability feature causes problems.</span></span> <span data-ttu-id="01659-137">이러한 시나리오에서는 요소를 `<supportPortability>` 사용 하 여 기능을 사용 하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01659-137">In those scenarios, the `<supportPortability>` element can be used to disable the feature.</span></span>  
  
<span data-ttu-id="01659-138">이러한 시나리오 중 하나는 .NET Framework 구현과 특정 참조 어셈블리의 Silverlight 구현에 대 한 .NET Framework를 모두 참조 해야 하는 어셈블리입니다.</span><span class="sxs-lookup"><span data-stu-id="01659-138">One such scenario is an assembly that has to reference both the .NET Framework implementation and the .NET Framework for Silverlight implementation of a particular reference assembly.</span></span> <span data-ttu-id="01659-139">예를 들어 Windows Presentation Foundation (WPF)로 작성 된 XAML 디자이너는 WPF 데스크톱 구현, 디자이너의 사용자 인터페이스 및 Silverlight 구현에 포함 된 WPF의 하위 집합을 모두 참조 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01659-139">For example, a XAML designer written in Windows Presentation Foundation (WPF) might need to reference both the WPF Desktop implementation, for the designer's user interface, and the subset of WPF that is included in the Silverlight implementation.</span></span> <span data-ttu-id="01659-140">기본적으로, 어셈블리 바인딩 시 두 어셈블리가 동등한 것으로 간주되기 때문에 서로 다른 참조를 사용할 경우 컴파일러 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="01659-140">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span> <span data-ttu-id="01659-141">이 요소는 기본 동작을 사용 하지 않도록 설정 하 고 컴파일이 성공 하도록 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="01659-141">This element disables the default behavior, and allows compilation to succeed.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="01659-142">컴파일러가 정보를 공용 언어 런타임의 어셈블리 바인딩 논리에 전달 하도록 하려면 `/appconfig` 컴파일러 옵션을 사용 하 여이 요소를 포함 하는 app.config 파일의 위치를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="01659-142">In order for the compiler to pass the information to the common language runtime's assembly-binding logic, you must use the `/appconfig` compiler option to specify the location of the app.config file that contains this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01659-143">예제</span><span class="sxs-lookup"><span data-stu-id="01659-143">Example</span></span>  

<span data-ttu-id="01659-144">다음 예제에서는 응용 프로그램에 두 구현 모두에 존재 하는 모든 .NET Framework 어셈블리의 Silverlight 구현에 대 한 .NET Framework 구현 및 .NET Framework에 대 한 참조를 사용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="01659-144">The following example enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="01659-145">`/appconfig`이 app.config 파일의 위치를 지정 하려면 컴파일러 옵션을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="01659-145">The `/appconfig` compiler option must be used to specify the location of this app.config file.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding>  
         <supportPortability PKT="7cec85d7bea7798e" enable="false"/>  
         <supportPortability PKT="31bf3856ad364e35" enable="false"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="01659-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="01659-146">See also</span></span>

- [<span data-ttu-id="01659-147">-appconfig(C# 컴파일러 옵션)</span><span class="sxs-lookup"><span data-stu-id="01659-147">-appconfig (C# Compiler Options)</span></span>](../../../../csharp/language-reference/compiler-options/appconfig-compiler-option.md)
- <span data-ttu-id="01659-148">[.NET Framework 어셈블리 통합 개요](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/db7849ey(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="01659-148">[.NET Framework Assembly Unification Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/db7849ey(v=vs.100))</span></span>
