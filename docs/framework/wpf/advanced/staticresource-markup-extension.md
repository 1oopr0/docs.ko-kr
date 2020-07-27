---
title: StaticResource 태그 확장
description: 이미 정의 된 리소스에 대 한 참조를 조회 하 여 모든 XAML 속성 특성에 대 한 값을 제공 합니다.
ms.date: 03/30/2017
f1_keywords:
- StaticResource
- StaticResourceExtension
helpviewer_keywords:
- XAML [WPF], StaticResource markup extension
- StaticResource markup extensions [WPF]
ms.assetid: 97af044c-71f1-4617-9a94-9064b68185d2
ms.openlocfilehash: 77396c1867dcbe279d7ba158ed9e6f5f833f17b5
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164683"
---
# <a name="staticresource-markup-extension"></a><span data-ttu-id="457c5-103">StaticResource 태그 확장</span><span class="sxs-lookup"><span data-stu-id="457c5-103">StaticResource Markup Extension</span></span>
<span data-ttu-id="457c5-104">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]이미 정의 된 리소스에 대 한 참조를 조회 하 여 모든 속성 특성에 대 한 값을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="457c5-104">Provides a value for any [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] property attribute by looking up a reference to an already defined resource.</span></span> <span data-ttu-id="457c5-105">해당 리소스에 대 한 조회 동작은 로드 시간 조회와 비슷하며, 이전에는 다른 응용 프로그램 소스 뿐만 아니라 현재 페이지의 태그에서 로드 된 리소스를 검색 하 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 고 해당 리소스 값을 런타임 개체의 속성 값으로 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="457c5-105">Lookup behavior for that resource is analogous to load-time lookup, which will look for resources that were previously loaded from the markup of the current [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page as well as other application sources, and will generate that resource value as the property value in the run-time objects.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="457c5-106">XAML 특성 사용</span><span class="sxs-lookup"><span data-stu-id="457c5-106">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{StaticResource key}" ... />  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="457c5-107">XAML 개체 요소 사용</span><span class="sxs-lookup"><span data-stu-id="457c5-107">XAML Object Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
<StaticResource ResourceKey="key" ... />  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="457c5-108">XAML 값</span><span class="sxs-lookup"><span data-stu-id="457c5-108">XAML Values</span></span>  
  
|||  
|-|-|  
|`key`|<span data-ttu-id="457c5-109">요청한 리소스의 키입니다.</span><span class="sxs-lookup"><span data-stu-id="457c5-109">The key for the requested resource.</span></span> <span data-ttu-id="457c5-110">리소스를 태그에서 만들었거나 [x:Key Directive](../../../desktop-wpf/xaml-services/xkey-directive.md) `key` <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> 코드에서 리소스를 만든 경우를 호출할 때 매개 변수로 제공 된 경우이 키는 처음에 x:Key 지시문에 의해 할당 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="457c5-110">This key was initially assigned by the [x:Key Directive](../../../desktop-wpf/xaml-services/xkey-directive.md) if a resource was created in markup, or was provided as the `key` parameter when calling <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> if the resource was created in code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="457c5-111">설명</span><span class="sxs-lookup"><span data-stu-id="457c5-111">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="457c5-112">는 `StaticResource` 파일 내에서 어휘 적으로 정의 된 리소스에 대 한 전방 참조를 만들려고 해서는 안 됩니다 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="457c5-112">A `StaticResource` must not attempt to make a forward reference to a resource that is defined lexically further within the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="457c5-113">이 작업을 수행 하는 것은 지원 되지 않으며 이러한 참조가 실패 하더라도를 나타내는 내부 해시 테이블이 검색 되 면 전방 참조를 시도 하면 로드 시 성능 저하가 발생 합니다 <xref:System.Windows.ResourceDictionary> .</span><span class="sxs-lookup"><span data-stu-id="457c5-113">Attempting to do so is not supported, and even if such a reference does not fail, attempting the forward reference will incur a load time performance penalty when the internal hash tables representing a <xref:System.Windows.ResourceDictionary> are searched.</span></span> <span data-ttu-id="457c5-114">최상의 결과를 위해 전방 참조를 피할 수 있도록 리소스 사전의 컴퍼지션을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="457c5-114">For best results, adjust the composition of your resource dictionaries such that forward references can be avoided.</span></span> <span data-ttu-id="457c5-115">전방 참조를 방지할 수 없는 경우 [DynamicResource 태그 확장](dynamicresource-markup-extension.md) 을 대신 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="457c5-115">If you cannot avoid a forward reference, use [DynamicResource Markup Extension](dynamicresource-markup-extension.md) instead.</span></span>  
  
 <span data-ttu-id="457c5-116">지정 된는 <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> 페이지, 응용 프로그램, 사용 가능한 컨트롤 테마 및 외부 리소스 또는 시스템 리소스의 특정 수준에서 [x:Key 지시문](../../../desktop-wpf/xaml-services/xkey-directive.md) 으로 식별 되는 기존 리소스와 일치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="457c5-116">The specified <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> should correspond to an existing resource, identified with an [x:Key Directive](../../../desktop-wpf/xaml-services/xkey-directive.md) at some level in your page, application, the available control themes and external resources, or system resources.</span></span> <span data-ttu-id="457c5-117">리소스 조회는 해당 순서로 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="457c5-117">The resource lookup occurs in that order.</span></span> <span data-ttu-id="457c5-118">정적 및 동적 리소스의 리소스 조회 동작에 대 한 자세한 내용은 [XAML 리소스](../../../desktop-wpf/fundamentals/xaml-resources-define.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="457c5-118">For more information about resource lookup behavior for static and dynamic resources, see [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>  
  
 <span data-ttu-id="457c5-119">리소스 키는 [XamlName 문법](../../../desktop-wpf/xaml-services/xamlname-grammar.md)에 정의 된 임의의 문자열일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="457c5-119">A resource key can be any string defined in the [XamlName Grammar](../../../desktop-wpf/xaml-services/xamlname-grammar.md).</span></span> <span data-ttu-id="457c5-120">리소스 키는 등의 다른 개체 형식일 수도 있습니다 <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="457c5-120">A resource key can also be other object types, such as a <xref:System.Type>.</span></span> <span data-ttu-id="457c5-121"><xref:System.Type>키는 암시적 스타일 키를 통해 컨트롤을 테마에 따라 스타일을 지정 하는 방법에 대 한 기본입니다.</span><span class="sxs-lookup"><span data-stu-id="457c5-121">A <xref:System.Type> key is fundamental to how controls can be styled by themes, through an implicit style key.</span></span> <span data-ttu-id="457c5-122">자세한 내용은 [컨트롤 제작 개요](../controls/control-authoring-overview.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="457c5-122">For more information, see [Control Authoring Overview](../controls/control-authoring-overview.md).</span></span>  
  
 <span data-ttu-id="457c5-123">리소스를 참조 하는 다른 선언적 방법은 [DynamicResource 태그 확장](dynamicresource-markup-extension.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="457c5-123">The alternative declarative means of referencing a resource is as a [DynamicResource Markup Extension](dynamicresource-markup-extension.md).</span></span>  
  
 <span data-ttu-id="457c5-124">특성 구문은 이러한 태그 확장에 가장 많이 사용되는 구문입니다.</span><span class="sxs-lookup"><span data-stu-id="457c5-124">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="457c5-125">`StaticResource` 식별자 문자열 다음에 나오는 문자열 토큰은 기본 <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> 확장명 클래스의 <xref:System.Windows.StaticResourceExtension> 값으로 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="457c5-125">The string token provided after the `StaticResource` identifier string is assigned as the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> value of the underlying <xref:System.Windows.StaticResourceExtension> extension class.</span></span>  
  
 <span data-ttu-id="457c5-126">`StaticResource`개체 요소 구문에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="457c5-126">`StaticResource` can be used in object element syntax.</span></span> <span data-ttu-id="457c5-127">이 경우 속성의 값을 지정 <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="457c5-127">In this case, specifying the value of the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> property is required.</span></span>  
  
 <span data-ttu-id="457c5-128">`StaticResource` 속성을 다음과 같이 속성=값 쌍으로 지정하는 자세한 특성 사용 구문에도 <xref:System.Windows.StaticResourceExtension.ResourceKey%2A>을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="457c5-128">`StaticResource` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{StaticResource ResourceKey=key}" ... />  
```  
  
 <span data-ttu-id="457c5-129">자세한 정보 표시는 대개 설정 가능한 속성이 둘 이상이거나 일부 속성이 선택 사항인 확장의 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="457c5-129">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="457c5-130">`StaticResource`에는 설정 가능한 속성이 하나뿐이고 이 속성은 필수적 속성이므로 자세한 정보 표시를 사용하지 않는 것이 일반적입니다.</span><span class="sxs-lookup"><span data-stu-id="457c5-130">Because `StaticResource` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="457c5-131">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 프로세서 구현에서이 태그 확장에 대 한 처리는 클래스에 의해 정의 됩니다 <xref:System.Windows.StaticResourceExtension> .</span><span class="sxs-lookup"><span data-stu-id="457c5-131">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.StaticResourceExtension> class.</span></span>  
  
 <span data-ttu-id="457c5-132">`StaticResource`은 태그 확장입니다.</span><span class="sxs-lookup"><span data-stu-id="457c5-132">`StaticResource` is a markup extension.</span></span> <span data-ttu-id="457c5-133">태그 확장은 특성 값을 리터럴 값 또는 처리기 이름이 아닌 다른 값이 되도록 이스케이프해야 하는 요구 사항이 있는 경우 일반적으로 구현되며 이러한 요구 사항은 특정 형식 또는 속성에 형식 변환기를 배치하는 것보다 더 포괄적입니다.</span><span class="sxs-lookup"><span data-stu-id="457c5-133">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="457c5-134">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]의 모든 태그 확장은 특성 구문에서 { 및 } 문자를 사용합니다. 이러한 문자는 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 프로세서가 태그 확장이 특성을 처리해야 함을 인식하는 데 사용되는 규칙입니다.</span><span class="sxs-lookup"><span data-stu-id="457c5-134">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="457c5-135">자세한 내용은 [태그 확장 및 WPF XAML](markup-extensions-and-wpf-xaml.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="457c5-135">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="457c5-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="457c5-136">See also</span></span>

- [<span data-ttu-id="457c5-137">스타일 지정 및 템플릿</span><span class="sxs-lookup"><span data-stu-id="457c5-137">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="457c5-138">XAML 개요(WPF)</span><span class="sxs-lookup"><span data-stu-id="457c5-138">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="457c5-139">태그 확장명 및 WPF XAML</span><span class="sxs-lookup"><span data-stu-id="457c5-139">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="457c5-140">XAML 리소스</span><span class="sxs-lookup"><span data-stu-id="457c5-140">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="457c5-141">리소스 및 코드</span><span class="sxs-lookup"><span data-stu-id="457c5-141">Resources and Code</span></span>](resources-and-code.md)
