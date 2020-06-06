---
title: <section> element
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/section
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup/section
helpviewer_keywords:
- section Element
- <section> Element
ms.assetid: ec7d4110-2403-47ac-8218-499bfe9d5ddb
ms.openlocfilehash: 88f74c02ef627e9136e4437ffa150c36445266a3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153734"
---
# <a name="section-element"></a><span data-ttu-id="1387b-102">\<section> 요소</span><span class="sxs-lookup"><span data-stu-id="1387b-102">\<section> element</span></span>

<span data-ttu-id="1387b-103">구성 섹션 선언을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="1387b-103">Contains a configuration section declaration.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup>**](sectiongroup-element-for-configsections.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**

## <a name="syntax"></a><span data-ttu-id="1387b-104">구문</span><span class="sxs-lookup"><span data-stu-id="1387b-104">Syntax</span></span>

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication"
         allowLocation="true|false" />
```

## <a name="required-attributes"></a><span data-ttu-id="1387b-105">필수 특성</span><span class="sxs-lookup"><span data-stu-id="1387b-105">Required attributes</span></span>

|           | <span data-ttu-id="1387b-106">Description</span><span class="sxs-lookup"><span data-stu-id="1387b-106">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="1387b-107">**name**</span><span class="sxs-lookup"><span data-stu-id="1387b-107">**name**</span></span>  | <span data-ttu-id="1387b-108">구성 섹션의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1387b-108">Specifies the name of the configuration section.</span></span> |
| <span data-ttu-id="1387b-109">**type**</span><span class="sxs-lookup"><span data-stu-id="1387b-109">**type**</span></span>  | <span data-ttu-id="1387b-110">구성 파일에서 섹션을 읽는 구성 섹션 처리기 클래스의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1387b-110">Specifies the name of the configuration section handler class that reads the section from the configuration file.</span></span> <span data-ttu-id="1387b-111">형식 값의 구문은 "정규화 된 섹션-클래스 이름, 단순 어셈블리 이름"입니다.</span><span class="sxs-lookup"><span data-stu-id="1387b-111">The type value has the syntax "fully-qualified-section-handler-class-name, simple-assembly-name".</span></span> <span data-ttu-id="1387b-112">단순 어셈블리 이름은 *.dll* 파일 확장명이 없는 루트 파일 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="1387b-112">The simple assembly name is the root filename without the *.dll* file extension.</span></span> |

## <a name="optional-attributes"></a><span data-ttu-id="1387b-113">선택적 특성</span><span class="sxs-lookup"><span data-stu-id="1387b-113">Optional attributes</span></span>

<span data-ttu-id="1387b-114">다음 특성은 ASP.NET 응용 프로그램에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1387b-114">The following attributes are applicable only for ASP.NET applications.</span></span> <span data-ttu-id="1387b-115">구성 시스템에서는 다른 응용 프로그램 유형에 대 한 이러한 특성을 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="1387b-115">The configuration system ignores these attributes for other application types.</span></span>

|                     | <span data-ttu-id="1387b-116">Description</span><span class="sxs-lookup"><span data-stu-id="1387b-116">Description</span></span> |
| ------------------- | ----------- |
| <span data-ttu-id="1387b-117">**allowDefinition**</span><span class="sxs-lookup"><span data-stu-id="1387b-117">**allowDefinition**</span></span> | <span data-ttu-id="1387b-118">섹션을 사용할 수 있는 구성 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1387b-118">Specifies which configuration file the section can be used in.</span></span> <span data-ttu-id="1387b-119">다음 값 중 하나를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1387b-119">Use one of the following values:</span></span><br><br><span data-ttu-id="1387b-120">**모든 범위**</span><span class="sxs-lookup"><span data-stu-id="1387b-120">**Everywhere**</span></span><br><span data-ttu-id="1387b-121">섹션을 모든 구성 파일에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1387b-121">Allows the section to be used in any configuration file.</span></span> <span data-ttu-id="1387b-122">기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="1387b-122">This is the default.</span></span><br><span data-ttu-id="1387b-123">**MachineOnly**</span><span class="sxs-lookup"><span data-stu-id="1387b-123">**MachineOnly**</span></span><br><span data-ttu-id="1387b-124">*컴퓨터 구성 파일 (machine.config*) 에서만 섹션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1387b-124">Allows the section to be used only in the machine configuration file (*Machine.config*).</span></span><br><span data-ttu-id="1387b-125">**MachineToApplication**</span><span class="sxs-lookup"><span data-stu-id="1387b-125">**MachineToApplication**</span></span><br><span data-ttu-id="1387b-126">컴퓨터 구성 파일 또는 응용 프로그램 구성 파일에서 섹션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1387b-126">Allows the section to be used in the machine configuration file or the application configuration file.</span></span> |
| <span data-ttu-id="1387b-127">**allowLocation**</span><span class="sxs-lookup"><span data-stu-id="1387b-127">**allowLocation**</span></span>   | <span data-ttu-id="1387b-128">요소 내에서 섹션을 사용할 수 있는지 여부를 확인 **\<location>** 합니다.</span><span class="sxs-lookup"><span data-stu-id="1387b-128">Determines whether the section can be used within the **\<location>** element.</span></span> <span data-ttu-id="1387b-129">다음 값 중 하나를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1387b-129">Use one of the following values:</span></span><br><br><span data-ttu-id="1387b-130">**true**</span><span class="sxs-lookup"><span data-stu-id="1387b-130">**true**</span></span><br><span data-ttu-id="1387b-131">요소 내에 섹션을 사용할 수 있습니다 **\<location>** .</span><span class="sxs-lookup"><span data-stu-id="1387b-131">Allows the section to be used within the **\<location>** element.</span></span> <span data-ttu-id="1387b-132">기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="1387b-132">This is the default.</span></span><br><span data-ttu-id="1387b-133">**false**</span><span class="sxs-lookup"><span data-stu-id="1387b-133">**false**</span></span><br><span data-ttu-id="1387b-134">에서는 요소 내에 섹션을 사용할 수 없습니다 **\<location>** .</span><span class="sxs-lookup"><span data-stu-id="1387b-134">Does not allow the section to be used within the **\<location>** element.</span></span> |

## <a name="parent-elements"></a><span data-ttu-id="1387b-135">부모 요소</span><span class="sxs-lookup"><span data-stu-id="1387b-135">Parent elements</span></span>

|     | <span data-ttu-id="1387b-136">Description</span><span class="sxs-lookup"><span data-stu-id="1387b-136">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="1387b-137">**\<configSections>** 요소인</span><span class="sxs-lookup"><span data-stu-id="1387b-137">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="1387b-138">구성 섹션과 네임 스페이스 선언을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="1387b-138">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="1387b-139">**\<sectionGroup>** 요소인</span><span class="sxs-lookup"><span data-stu-id="1387b-139">**\<sectionGroup>** Element</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="1387b-140">구성 섹션에 대 한 네임 스페이스를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1387b-140">Defines a namespace for configuration sections.</span></span> |

> [!NOTE]
> <span data-ttu-id="1387b-141">**\<section>** 요소는 또는 중 하나 **\<configSections>** 또는 둘 다의 자식 요소입니다 **\<sectionGroup>** .</span><span class="sxs-lookup"><span data-stu-id="1387b-141">A **\<section>** element is a child element of either **\<configSections>** or **\<sectionGroup>** but not both.</span></span>

## <a name="child-elements"></a><span data-ttu-id="1387b-142">자식 요소</span><span class="sxs-lookup"><span data-stu-id="1387b-142">Child elements</span></span>

<span data-ttu-id="1387b-143">None</span><span class="sxs-lookup"><span data-stu-id="1387b-143">None</span></span>

## <a name="remarks"></a><span data-ttu-id="1387b-144">설명</span><span class="sxs-lookup"><span data-stu-id="1387b-144">Remarks</span></span>

<span data-ttu-id="1387b-145">구성 섹션을 선언 하는 것은 기본적으로 구성 파일에 대 한 새 요소를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1387b-145">Declaring a configuration section essentially defines a new element for the configuration file.</span></span> <span data-ttu-id="1387b-146">새 요소는 구성 섹션 처리기 (즉, 인터페이스를 구현 하는 클래스)가 읽는 설정을 포함 합니다 <xref:System.Configuration.IConfigurationSectionHandler> .</span><span class="sxs-lookup"><span data-stu-id="1387b-146">The new element contains settings that a configuration section handler (that is, a class that implements the <xref:System.Configuration.IConfigurationSectionHandler> interface) reads.</span></span> <span data-ttu-id="1387b-147">사용자가 정의 하는 섹션의 특성 및 자식 요소는 설정을 읽는 데 사용 하는 섹션 처리기에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="1387b-147">The attributes and child elements of a section you define depend on the section handler you use to read your settings.</span></span>

<span data-ttu-id="1387b-148">*Machine.config 파일에서* 구성 섹션 처리기를 선언 하면 **allowDefinition** 특성이 달리 지정 되지 않는 한 해당 컴퓨터의 모든 응용 프로그램 구성 파일에서 구성 섹션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1387b-148">Declaring a configuration section handler in the *Machine.config* file enables you to use the configuration section in any application configuration file on that computer, unless the **allowDefinition** attribute specifies otherwise.</span></span>

## <a name="example"></a><span data-ttu-id="1387b-149">예제</span><span class="sxs-lookup"><span data-stu-id="1387b-149">Example</span></span>

<span data-ttu-id="1387b-150">다음 예제에서는 구성 섹션을 정의 하 고 해당 섹션에 대 한 설정을 정의 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1387b-150">The following example shows how to define a configuration section and define settings for that section:</span></span>

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler"
             allowLocation="false" />
  </configSections>
  <sampleSection setting1="Value1"
                 setting2="value two"
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="1387b-151">구성 파일</span><span class="sxs-lookup"><span data-stu-id="1387b-151">Configuration file</span></span>

<span data-ttu-id="1387b-152">이 요소는 응용 프로그램 구성 파일 *, 컴퓨터 구성 파일 (machine.config*) 및 응용 프로그램 디렉터리 수준에 없는 *web.config 파일* 에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1387b-152">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="1387b-153">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1387b-153">See also</span></span>

- [<span data-ttu-id="1387b-154">.NET Framework의 구성 파일 스키마</span><span class="sxs-lookup"><span data-stu-id="1387b-154">Configuration file schema for the .NET Framework</span></span>](index.md)
