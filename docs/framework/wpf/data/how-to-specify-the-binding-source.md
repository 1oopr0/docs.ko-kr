---
title: '방법: 바인딩 소스 지정'
description: Windows Presentation Foundation (WPF)에서이 예제를 통해 바인딩 소스를 지정 하는 방법에 대해 알아봅니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], binding sources
- data binding [WPF], binding source
- binding sources [WPF]
ms.assetid: 55d47757-2648-4a52-987f-b767953f168c
ms.openlocfilehash: 02f27da007ebe8c5985f91b83adfba7d3d00219a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621667"
---
# <a name="how-to-specify-the-binding-source"></a><span data-ttu-id="353cc-103">방법: 바인딩 소스 지정</span><span class="sxs-lookup"><span data-stu-id="353cc-103">How to: Specify the Binding Source</span></span>
<span data-ttu-id="353cc-104">데이터 바인딩에서 바인딩 소스 개체는 데이터를 가져온 개체를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="353cc-104">In data binding, the binding source object refers to the object you obtain your data from.</span></span> <span data-ttu-id="353cc-105">이 항목에서는 바인딩 소스를 지정하는 여러 가지 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="353cc-105">This topic describes the different ways of specifying the binding source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="353cc-106">예제</span><span class="sxs-lookup"><span data-stu-id="353cc-106">Example</span></span>  
 <span data-ttu-id="353cc-107">하나의 공용 소스에 여러 개의 속성을 바인딩하는 경우 `DataContext` 속성을 사용할 수 있습니다. 이 속성은 모든 데이터 바인딩된 속성이 공용 소스를 상속받게 되는 범위를 설정하는 편리한 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="353cc-107">If you are binding several properties to a common source, you want to use the `DataContext` property, which provides a convenient way to establish a scope within which all data-bound properties inherit a common source.</span></span>  
  
 <span data-ttu-id="353cc-108">다음 예제에서 데이터 컨텍스트는 애플리케이션의 루트 요소에 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="353cc-108">In the following example, the data context is established on the root element of the application.</span></span> <span data-ttu-id="353cc-109">따라서 모든 자식 요소가 해당 데이터 컨텍스트를 상속받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="353cc-109">This allows all child elements to inherit that data context.</span></span> <span data-ttu-id="353cc-110">바인딩할 데이터는 사용자 지정 데이터 클래스, 즉 매핑과 `incomeDataSource`의 지정한 리소스 키를 통해 직접 참조되는 `NetIncome`에서 옵니다.</span><span class="sxs-lookup"><span data-stu-id="353cc-110">Data for the binding comes from a custom data class, `NetIncome`, referenced directly through a mapping and given the resource key of `incomeDataSource`.</span></span>  
  
 [!code-xaml[DirectionalBinding#DataContext1](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext1)]  
[!code-xaml[DirectionalBinding#DataContext2](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext2)]  
  
 <span data-ttu-id="353cc-111">다음 예제에서는 `NetIncome` 클래스의 정의를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="353cc-111">The following example shows the definition of the `NetIncome` class.</span></span>  
  
 [!code-csharp[DirectionalBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/billsdata.cs#dataobject)]
 [!code-vb[DirectionalBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DirectionalBinding/VisualBasic/NetIncome.vb#dataobject)]  
  
> [!NOTE]
> <span data-ttu-id="353cc-112">위의 예제는 태그에서 개체를 인스턴스화하며 개체를 리소스로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="353cc-112">The above example instantiates the object in markup and uses it as a resource.</span></span> <span data-ttu-id="353cc-113">코드에서 이미 인스턴스화된 개체에 바인딩하려는 경우 `DataContext` 속성을 프로그래밍 방식으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="353cc-113">If you want to bind to an object that has already been instantiated in code, you need to set the `DataContext` property programmatically.</span></span> <span data-ttu-id="353cc-114">예제는 [XAML의 바인딩에 사용할 수 있는 데이터 만들기](how-to-make-data-available-for-binding-in-xaml.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="353cc-114">For an example, see [Make Data Available for Binding in XAML](how-to-make-data-available-for-binding-in-xaml.md).</span></span>  
  
 <span data-ttu-id="353cc-115">또는 개별 바인딩에서 소스를 명시적으로 지정하려는 경우 다음 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="353cc-115">Alternatively, if you want to specify the source on your individual bindings explicitly, you have the following options.</span></span> <span data-ttu-id="353cc-116">이러한 옵션은 상속된 데이터 컨텍스트보다 우선합니다.</span><span class="sxs-lookup"><span data-stu-id="353cc-116">These take precedence over the inherited data context.</span></span>  
  
|<span data-ttu-id="353cc-117">속성</span><span class="sxs-lookup"><span data-stu-id="353cc-117">Property</span></span>|<span data-ttu-id="353cc-118">설명</span><span class="sxs-lookup"><span data-stu-id="353cc-118">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Data.Binding.Source%2A>|<span data-ttu-id="353cc-119">이 속성을 사용하여 소스를 개체의 인스턴스로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="353cc-119">You use this property to set the source to an instance of an object.</span></span> <span data-ttu-id="353cc-120">여러 속성이 동일한 데이터 컨텍스트를 상속 하는 범위를 설정 하는 기능이 필요 하지 않은 경우 속성 대신 속성을 사용할 수 있습니다 <xref:System.Windows.Data.Binding.Source%2A> `DataContext` .</span><span class="sxs-lookup"><span data-stu-id="353cc-120">If you do not need the functionality of establishing a scope in which several properties inherit the same data context, you can use the <xref:System.Windows.Data.Binding.Source%2A> property instead of the `DataContext` property.</span></span> <span data-ttu-id="353cc-121">자세한 내용은 <xref:System.Windows.Data.Binding.Source%2A>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="353cc-121">For more information, see <xref:System.Windows.Data.Binding.Source%2A>.</span></span>|  
|<xref:System.Windows.Data.Binding.RelativeSource%2A>|<span data-ttu-id="353cc-122">이는 바인딩 대상이 있는 위치와 상대적인 소스를 지정할 때 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="353cc-122">This is useful when you want to specify the source relative to where your binding target is.</span></span> <span data-ttu-id="353cc-123">이 속성을 사용할 수 있는 몇 가지 일반 시나리오 중 요소의 한 속성을 같은 요소의 다른 속성에 바인딩하거나 스타일 또는 템플릿에서 바인딩을 정의하는 경우가 이에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="353cc-123">Some common scenarios where you may use this property is when you want to bind one property of your element to another property of the same element or if you are defining a binding in a style or a template.</span></span> <span data-ttu-id="353cc-124">자세한 내용은 <xref:System.Windows.Data.Binding.RelativeSource%2A>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="353cc-124">For more information, see <xref:System.Windows.Data.Binding.RelativeSource%2A>.</span></span>|  
|<xref:System.Windows.Data.Binding.ElementName%2A>|<span data-ttu-id="353cc-125">바인딩할 요소를 나타내는 문자열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="353cc-125">You specify a string that represents the element you want to bind to.</span></span> <span data-ttu-id="353cc-126">이는 애플리케이션에서 다른 요소의 속성에 바인딩하려고 할 때 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="353cc-126">This is useful when you want to bind to the property of another element on your application.</span></span> <span data-ttu-id="353cc-127">예를 들어 사용 하려는 경우를 <xref:System.Windows.Controls.Slider> 애플리케이션에서 다른 컨트롤의 높이 제어 하 바인딩하려는 경우 또는 <xref:System.Windows.Controls.ContentControl.Content%2A> 컨트롤을 <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> 의 속성에 <xref:System.Windows.Controls.ListBox> 컨트롤.</span><span class="sxs-lookup"><span data-stu-id="353cc-127">For example, if you want to use a <xref:System.Windows.Controls.Slider> to control the height of another control in your application, or if you want to bind the <xref:System.Windows.Controls.ContentControl.Content%2A> of your control to the <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> property of your <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="353cc-128">자세한 내용은 <xref:System.Windows.Data.Binding.ElementName%2A>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="353cc-128">For more information, see <xref:System.Windows.Data.Binding.ElementName%2A>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="353cc-129">참조</span><span class="sxs-lookup"><span data-stu-id="353cc-129">See also</span></span>

- <xref:System.Windows.FrameworkElement.DataContext%2A?displayProperty=nameWithType>
- <xref:System.Windows.FrameworkContentElement.DataContext%2A?displayProperty=nameWithType>
- [<span data-ttu-id="353cc-130">속성 값 상속</span><span class="sxs-lookup"><span data-stu-id="353cc-130">Property Value Inheritance</span></span>](../advanced/property-value-inheritance.md)
- [<span data-ttu-id="353cc-131">데이터 바인딩 개요</span><span class="sxs-lookup"><span data-stu-id="353cc-131">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="353cc-132">바인딩 선언 개요</span><span class="sxs-lookup"><span data-stu-id="353cc-132">Binding Declarations Overview</span></span>](binding-declarations-overview.md)
- [<span data-ttu-id="353cc-133">방법 도움말 항목</span><span class="sxs-lookup"><span data-stu-id="353cc-133">How-to Topics</span></span>](data-binding-how-to-topics.md)
