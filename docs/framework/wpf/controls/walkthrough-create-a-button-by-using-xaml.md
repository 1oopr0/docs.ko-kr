---
title: '연습: XAML을 사용하여 단추 만들기'
description: 이 연습을 사용 하면 XAML을 사용 하 여 Windows Presentation Foundation 응용 프로그램에서 사용 하기 위한 애니메이션 단추를 만드는 방법을 배울 수 있습니다.
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [WPF]
ms.assetid: 138c41c4-1759-4bbf-8d77-77031a06a8a0
ms.openlocfilehash: 136d1ad5d6fefd70f0d977e5287ae75f06c52d36
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164846"
---
# <a name="walkthrough-create-a-button-by-using-xaml"></a><span data-ttu-id="86d32-103">연습: XAML을 사용하여 단추 만들기</span><span class="sxs-lookup"><span data-stu-id="86d32-103">Walkthrough: Create a Button by Using XAML</span></span>

<span data-ttu-id="86d32-104">이 연습의 목표는 Windows Presentation Foundation (WPF) 응용 프로그램에서 사용 하기 위한 애니메이션 된 단추를 만드는 방법을 설명 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-104">The objective of this walkthrough is to learn how to create an animated button for use in a Windows Presentation Foundation (WPF) application.</span></span> <span data-ttu-id="86d32-105">이 연습에서는 스타일 및 템플릿을 사용 하 여 단추 선언에서 코드를 다시 사용 하 고 단추 논리를 분리 하는 데 사용할 수 있는 사용자 지정 된 단추 리소스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-105">This walkthrough uses styles and a template to create a customized button resource that allows reuse of code and separation of button logic from the button declaration.</span></span> <span data-ttu-id="86d32-106">이 연습은 전체에 작성 됩니다 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="86d32-106">This walkthrough is written entirely in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>

> [!IMPORTANT]
> <span data-ttu-id="86d32-107">이 연습에서는 Visual Studio에 입력 하거나 복사 하 여 붙여 넣는 방법으로 응용 프로그램을 만드는 단계를 안내 합니다 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="86d32-107">This walkthrough guides you through the steps for creating the application by typing or copying and pasting [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] into Visual Studio.</span></span> <span data-ttu-id="86d32-108">디자이너를 사용 하 여 동일한 응용 프로그램을 만드는 방법에 대해 알아보려면 [Microsoft Expression Blend를 사용 하 여 단추 만들기](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="86d32-108">If you would prefer to learn how to use a designer to create the same application, see [Create a Button by Using Microsoft Expression Blend](walkthrough-create-a-button-by-using-microsoft-expression-blend.md).</span></span>

<span data-ttu-id="86d32-109">다음 그림에서는 완료 된 단추를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-109">The following figure shows the finished buttons.</span></span>

<span data-ttu-id="86d32-110">![XAML을 사용 하 여 만든 사용자 지정 단추](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span><span class="sxs-lookup"><span data-stu-id="86d32-110">![Custom buttons that were created by using XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span></span>

## <a name="create-basic-buttons"></a><span data-ttu-id="86d32-111">기본 단추 만들기</span><span class="sxs-lookup"><span data-stu-id="86d32-111">Create Basic Buttons</span></span>

<span data-ttu-id="86d32-112">먼저 새 프로젝트를 만들고 창에 몇 가지 단추를 추가 해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-112">Let's start by creating a new project and adding a few buttons to the window.</span></span>

### <a name="to-create-a-new-wpf-project-and-add-buttons-to-the-window"></a><span data-ttu-id="86d32-113">새 WPF 프로젝트를 만들고 창에 단추를 추가 하려면</span><span class="sxs-lookup"><span data-stu-id="86d32-113">To create a new WPF project and add buttons to the window</span></span>

1. <span data-ttu-id="86d32-114">Visual Studio를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-114">Start Visual Studio.</span></span>

2. <span data-ttu-id="86d32-115">**새 WPF 프로젝트를 만듭니다.** **파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-115">**Create a new WPF project:** On the **File** menu, point to **New**, and then click **Project**.</span></span> <span data-ttu-id="86d32-116">**Windows 응용 프로그램 (WPF)** 템플릿을 찾고 프로젝트 이름을 "AnimatedButton"로 합니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-116">Find the **Windows Application (WPF)** template and name the project "AnimatedButton".</span></span> <span data-ttu-id="86d32-117">그러면 응용 프로그램에 대 한 해골을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-117">This will create the skeleton for the application.</span></span>

3. <span data-ttu-id="86d32-118">**기본 기본 단추 추가:** 이 연습에 필요한 모든 파일은 템플릿에서 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-118">**Add basic default buttons:** All the files you need for this walkthrough are provided by the template.</span></span> <span data-ttu-id="86d32-119">솔루션 탐색기에서 두 번 클릭 하 여 Window1 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-119">Open the Window1.xaml file by double clicking it in Solution Explorer.</span></span> <span data-ttu-id="86d32-120">기본적으로 <xref:System.Windows.Controls.Grid> Window1에는 요소가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-120">By default, there is a <xref:System.Windows.Controls.Grid> element in Window1.xaml.</span></span> <span data-ttu-id="86d32-121">요소를 제거 <xref:System.Windows.Controls.Grid> 하 고 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 다음 강조 표시 된 코드를 Window1에 입력 하거나 복사 하 여 페이지에 몇 가지 단추를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-121">Remove the <xref:System.Windows.Controls.Grid> element and add a few buttons to the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page by typing or copy and pasting the following highlighted code to Window1.xaml:</span></span>

    ```xaml
    <Window x:Class="AnimatedButton.Window1"
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
      Title="AnimatedButton" Height="300" Width="300"
      Background="Black">
      <!-- Buttons arranged vertically inside a StackPanel. -->
      <StackPanel HorizontalAlignment="Left">
          <Button>Button 1</Button>
          <Button>Button 2</Button>
          <Button>Button 3</Button>
      </StackPanel>
    </Window>
    ```

     <span data-ttu-id="86d32-122">F5 키를 눌러 응용 프로그램을 실행 합니다. 다음 그림과 같은 단추 집합이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-122">Press F5 to run the application; you should see a set of buttons that looks like the following figure.</span></span>

     <span data-ttu-id="86d32-123">![세 개의 기본 단추](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")</span><span class="sxs-lookup"><span data-stu-id="86d32-123">![Three basic buttons](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")</span></span>

     <span data-ttu-id="86d32-124">이제 기본 단추를 만들었으므로 Window1 .xaml 파일에서 작업을 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-124">Now that you have created the basic buttons, you are finished working in the Window1.xaml file.</span></span> <span data-ttu-id="86d32-125">연습의 나머지 부분에서는 app.xaml 파일에 중점을 두고 단추에 대 한 스타일 및 템플릿을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-125">The rest of the walkthrough focuses on the app.xaml file, defining styles and a template for the buttons.</span></span>

## <a name="set-basic-properties"></a><span data-ttu-id="86d32-126">기본 속성 설정</span><span class="sxs-lookup"><span data-stu-id="86d32-126">Set Basic Properties</span></span>

<span data-ttu-id="86d32-127">다음으로 이러한 단추의 몇 가지 속성을 설정 하 여 단추 모양과 레이아웃을 제어 해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-127">Next, let's set some properties on these buttons to control the button appearance and layout.</span></span> <span data-ttu-id="86d32-128">단추에 대해 개별적으로 속성을 설정 하는 대신 리소스를 사용 하 여 전체 응용 프로그램에 대 한 단추 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-128">Rather than setting properties on the buttons individually, you will use resources to define button properties for the entire application.</span></span> <span data-ttu-id="86d32-129">응용 프로그램 리소스는 웹 페이지에 대 한 CSS (외부 CSS 스타일시트)와 개념적으로 유사 합니다. 그러나이 연습의 끝에서 볼 수 있듯이 리소스는 CSS (CSS 스타일시트) 보다 훨씬 더 강력 합니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-129">Application resources are conceptually similar to external Cascading Style Sheets (CSS) for Web pages; however, resources are much more powerful than Cascading Style Sheets (CSS), as you will see by the end of this walkthrough.</span></span> <span data-ttu-id="86d32-130">리소스에 대해 자세히 알아보려면 [XAML 리소스](../../../desktop-wpf/fundamentals/xaml-resources-define.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="86d32-130">To learn more about resources, see [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>

### <a name="to-use-styles-to-set-basic-properties-on-the-buttons"></a><span data-ttu-id="86d32-131">스타일을 사용 하 여 단추에 대 한 기본 속성을 설정 하려면</span><span class="sxs-lookup"><span data-stu-id="86d32-131">To use styles to set basic properties on the buttons</span></span>

1. <span data-ttu-id="86d32-132">**응용 프로그램 리소스 블록을 정의 합니다** . App.xaml을 열고 다음 강조 표시 된 태그를 추가 합니다 (아직 없는 경우).</span><span class="sxs-lookup"><span data-stu-id="86d32-132">**Define an Application.Resources block:** Open app.xaml and add the following highlighted markup if it is not already there:</span></span>

    ```xaml
    <Application x:Class="AnimatedButton.App"
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
      StartupUri="Window1.xaml"
      >
      <Application.Resources>
        <!-- Resources for the entire application can be defined here. -->
      </Application.Resources>
    </Application>
    ```

     <span data-ttu-id="86d32-133">리소스 범위는 리소스를 정의 하는 위치에 따라 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-133">Resource scope is determined by where you define the resource.</span></span> <span data-ttu-id="86d32-134">`Application.Resources`앱 .xaml 파일의에서 리소스를 정의 하면 응용 프로그램의 어디에서 나 리소스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-134">Defining resources in `Application.Resources` in the app.xaml file enables the resource to be used from anywhere in the application.</span></span> <span data-ttu-id="86d32-135">리소스의 범위를 정의 하는 방법에 대 한 자세한 내용은 [XAML 리소스](../../../desktop-wpf/fundamentals/xaml-resources-define.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="86d32-135">To learn more about defining the scope of your resources, see [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>

2. <span data-ttu-id="86d32-136">**스타일을 만들고 기본 속성 값을 정의 합니다.** 블록에 다음 태그를 추가 합니다 `Application.Resources` .</span><span class="sxs-lookup"><span data-stu-id="86d32-136">**Create a style and define basic property values with it:** Add the following markup to the `Application.Resources` block.</span></span> <span data-ttu-id="86d32-137">이 태그는 <xref:System.Windows.Style> 응용 프로그램의 모든 단추에 적용 되는를 만들고 단추의를 90으로 설정 하 <xref:System.Windows.FrameworkElement.Width%2A> 고을 10으로 설정 합니다 <xref:System.Windows.FrameworkElement.Margin%2A> .</span><span class="sxs-lookup"><span data-stu-id="86d32-137">This markup creates a <xref:System.Windows.Style> that applies to all buttons in the application, setting the <xref:System.Windows.FrameworkElement.Width%2A> of the buttons to 90 and the <xref:System.Windows.FrameworkElement.Margin%2A> to 10:</span></span>

    ```xaml
    <Application.Resources>
      <Style TargetType="Button">
        <Setter Property="Width" Value="90" />
        <Setter Property="Margin" Value="10" />
      </Style>
    </Application.Resources>
    ```

     <span data-ttu-id="86d32-138"><xref:System.Windows.Style.TargetType%2A>속성은 형식의 모든 개체에 스타일을 적용 하도록 지정 합니다 <xref:System.Windows.Controls.Button> .</span><span class="sxs-lookup"><span data-stu-id="86d32-138">The <xref:System.Windows.Style.TargetType%2A> property specifies that the style applies to all objects of type <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="86d32-139">각각 <xref:System.Windows.Setter> 에 대해 서로 다른 속성 값을 설정 <xref:System.Windows.Style> 합니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-139">Each <xref:System.Windows.Setter> sets a different property value for the <xref:System.Windows.Style>.</span></span> <span data-ttu-id="86d32-140">따라서이 시점에서 응용 프로그램의 모든 단추 너비는 90이 고 여백은 10입니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-140">Therefore, at this point every button in the application has a width of 90 and a margin of 10.</span></span>  <span data-ttu-id="86d32-141">F5 키를 눌러 응용 프로그램을 실행 하면 다음 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-141">If you press F5 to run the application, you see the following window.</span></span>

     <span data-ttu-id="86d32-142">![너비 90, 여백 10의 단추](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")</span><span class="sxs-lookup"><span data-stu-id="86d32-142">![Buttons with a width of 90 and a margin of 10](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")</span></span>

     <span data-ttu-id="86d32-143">대상 개체를 미세 조정 하 고, 복잡 한 속성 값을 지정 하 고, 다른 스타일의 입력으로 스타일을 사용 하는 다양 한 방법을 포함 하 여 스타일을 사용 하 여 더 많은 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-143">There is much more you can do with styles, including a variety of ways to fine-tune what objects are targeted, specifying complex property values, and even using styles as input for other styles.</span></span> <span data-ttu-id="86d32-144">자세한 내용은 [스타일 지정 및 템플릿](../../../desktop-wpf/fundamentals/styles-templates-overview.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="86d32-144">For more information, see [Styling and Templating](../../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

3. <span data-ttu-id="86d32-145">**스타일 속성 값을 리소스에 설정 합니다.** 리소스를 사용 하면 일반적으로 정의 된 개체 및 값을 다시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-145">**Set a style property value to a resource:** Resources enable a simple way to reuse commonly defined objects and values.</span></span> <span data-ttu-id="86d32-146">코드를 모듈식으로 만들기 위해 리소스를 사용 하 여 복잡 한 값을 정의 하는 데 특히 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-146">It is especially useful to define complex values using resources to make your code more modular.</span></span> <span data-ttu-id="86d32-147">다음 강조 표시 된 태그를 app.xaml에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-147">Add the following highlighted markup to app.xaml.</span></span>

    ```xaml
    <Application.Resources>
      <LinearGradientBrush x:Key="GrayBlueGradientBrush" StartPoint="0,0" EndPoint="1,1">
        <GradientStop Color="DarkGray" Offset="0" />
        <GradientStop Color="#CCCCFF" Offset="0.5" />
        <GradientStop Color="DarkGray" Offset="1" />
      </LinearGradientBrush>
      <Style TargetType="{x:Type Button}">
        <Setter Property="Background" Value="{StaticResource GrayBlueGradientBrush}" />
        <Setter Property="Width" Value="80" />
        <Setter Property="Margin" Value="10" />
      </Style>
    </Application.Resources>
    ```

     <span data-ttu-id="86d32-148">블록 바로 아래 `Application.Resources` 에 "GrayBlueGradientBrush" 이라는 리소스를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-148">Directly under the `Application.Resources` block, you created a resource called "GrayBlueGradientBrush".</span></span> <span data-ttu-id="86d32-149">이 리소스는 가로 그라데이션을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-149">This resource defines a horizontal gradient.</span></span> <span data-ttu-id="86d32-150">이 리소스는 속성에 대 한 단추 스타일 setter 내부를 포함 하 여 응용 프로그램의 어디에서 나 속성 값으로 사용할 수 있습니다 <xref:System.Windows.Controls.Control.Background%2A> .</span><span class="sxs-lookup"><span data-stu-id="86d32-150">This resource can be used as a property value from anywhere in the application, including inside the button style setter for the <xref:System.Windows.Controls.Control.Background%2A> property.</span></span> <span data-ttu-id="86d32-151">이제 모든 단추에 <xref:System.Windows.Controls.Control.Background%2A> 이 그라데이션의 속성 값이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-151">Now, all the buttons have a <xref:System.Windows.Controls.Control.Background%2A> property value of this gradient.</span></span>

     <span data-ttu-id="86d32-152">F5 키를 눌러 애플리케이션을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-152">Press F5 to run the application.</span></span> <span data-ttu-id="86d32-153">다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-153">It should look like the following.</span></span>

     <span data-ttu-id="86d32-154">![그라데이션 배경이 있는 단추](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")</span><span class="sxs-lookup"><span data-stu-id="86d32-154">![Buttons with a gradient background](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")</span></span>

## <a name="create-a-template-that-defines-the-look-of-the-button"></a><span data-ttu-id="86d32-155">단추의 모양을 정의 하는 템플릿을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-155">Create a Template That Defines the Look of the Button</span></span>

<span data-ttu-id="86d32-156">이 섹션에서는 단추의 모양 (표시)을 사용자 지정 하는 템플릿을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-156">In this section, you create a template that customizes the appearance (presentation) of the button.</span></span> <span data-ttu-id="86d32-157">단추 프레젠테이션은 사각형 및 기타 구성 요소를 비롯 한 여러 개체로 구성 되어 단추에 고유한 모양을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-157">The button presentation is made up of several objects including rectangles and other components to give the button a unique look.</span></span>

<span data-ttu-id="86d32-158">지금까지 응용 프로그램에서 단추가 표시 되는 방식에 대 한 제어는 단추의 속성을 변경 하는 것으로 제한 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-158">So far, the control of how buttons look in the application has been confined to changing properties of the button.</span></span> <span data-ttu-id="86d32-159">단추의 모양을 크게 변경 하려면 어떻게 해야 하나요?</span><span class="sxs-lookup"><span data-stu-id="86d32-159">What if you want to make more radical changes to the button's appearance?</span></span> <span data-ttu-id="86d32-160">템플릿을 사용 하면 개체의 표시를 효과적으로 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-160">Templates enable powerful control over the presentation of an object.</span></span> <span data-ttu-id="86d32-161">템플릿은 스타일 내에서 사용할 수 있으므로 스타일이 적용 되는 모든 개체에 템플릿을 적용할 수 있습니다 (이 연습에서는 단추).</span><span class="sxs-lookup"><span data-stu-id="86d32-161">Because templates can be used within styles, you can apply a template to all objects that the style applies to (in this walkthrough, the button).</span></span>

### <a name="to-use-the-template-to-define-the-look-of-the-button"></a><span data-ttu-id="86d32-162">템플릿을 사용 하 여 단추의 모양을 정의 하려면</span><span class="sxs-lookup"><span data-stu-id="86d32-162">To use the template to define the look of the button</span></span>

1. <span data-ttu-id="86d32-163">**템플릿 설정:** 와 같은 컨트롤에는 속성이 있으므로를 <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Control.Template%2A> 사용 하 여에서 설정한 다른 속성 값과 마찬가지로 템플릿 속성 값을 정의할 수 있습니다 <xref:System.Windows.Style> <xref:System.Windows.Setter> .</span><span class="sxs-lookup"><span data-stu-id="86d32-163">**Set up the template:** Because controls like <xref:System.Windows.Controls.Button> have a <xref:System.Windows.Controls.Control.Template%2A> property, you can define the template property value just like the other property values we have set in a <xref:System.Windows.Style> using a <xref:System.Windows.Setter>.</span></span> <span data-ttu-id="86d32-164">다음 강조 표시 된 태그를 단추 스타일에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-164">Add the following highlighted markup to your button style.</span></span>

    ```xaml
    <Application.Resources>
      <LinearGradientBrush x:Key="GrayBlueGradientBrush"
        StartPoint="0,0" EndPoint="1,1">
        <GradientStop Color="DarkGray" Offset="0" />
        <GradientStop Color="#CCCCFF" Offset="0.5" />
        <GradientStop Color="DarkGray" Offset="1" />
      </LinearGradientBrush>
      <Style TargetType="{x:Type Button}">
        <Setter Property="Background" Value="{StaticResource GrayBlueGradientBrush}" />
        <Setter Property="Width" Value="80" />
        <Setter Property="Margin" Value="10" />
        <Setter Property="Template">
          <Setter.Value>
            <!-- The button template is defined here. -->
          </Setter.Value>
        </Setter>
      </Style>
    </Application.Resources>
    ```

2. <span data-ttu-id="86d32-165">**변경 단추 프레젠테이션:** 이 시점에서 템플릿을 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-165">**Alter button presentation:** At this point, you need to define the template.</span></span> <span data-ttu-id="86d32-166">다음 강조 표시 된 태그를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-166">Add the following highlighted markup.</span></span> <span data-ttu-id="86d32-167">이 태그 <xref:System.Windows.Shapes.Rectangle> 는 모서리가 둥근 모퉁이가 있는 두 요소를 지정 합니다 <xref:System.Windows.Controls.DockPanel> .</span><span class="sxs-lookup"><span data-stu-id="86d32-167">This markup specifies two <xref:System.Windows.Shapes.Rectangle> elements with rounded edges, followed by a <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="86d32-168">는 <xref:System.Windows.Controls.DockPanel> 단추의를 호스트 하는 데 사용 됩니다 <xref:System.Windows.Controls.ContentPresenter> .</span><span class="sxs-lookup"><span data-stu-id="86d32-168">The <xref:System.Windows.Controls.DockPanel> is used to host the <xref:System.Windows.Controls.ContentPresenter> of the button.</span></span> <span data-ttu-id="86d32-169">는 <xref:System.Windows.Controls.ContentPresenter> 단추의 내용을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-169">A <xref:System.Windows.Controls.ContentPresenter> displays the content of the button.</span></span> <span data-ttu-id="86d32-170">이 연습에서는 콘텐츠가 텍스트 ("Button 1", "Button 2", "Button 3")입니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-170">In this walkthrough, the content is text ("Button 1", "Button 2", "Button 3").</span></span> <span data-ttu-id="86d32-171">모든 템플릿 구성 요소 (사각형 및 <xref:System.Windows.Controls.DockPanel> )는 내에 배치 됩니다 <xref:System.Windows.Controls.Grid> .</span><span class="sxs-lookup"><span data-stu-id="86d32-171">All of the template components (the rectangles and the <xref:System.Windows.Controls.DockPanel>) are laid out inside of a <xref:System.Windows.Controls.Grid>.</span></span>

    ```xaml
    <Setter.Value>
      <ControlTemplate TargetType="Button">
        <Grid Width="{TemplateBinding Width}" Height="{TemplateBinding Height}" ClipToBounds="True">
          <!-- Outer Rectangle with rounded corners. -->
          <Rectangle x:Name="outerRectangle" HorizontalAlignment="Stretch" VerticalAlignment="Stretch" Stroke="{TemplateBinding Background}" RadiusX="20" RadiusY="20" StrokeThickness="5" Fill="Transparent" />
          <!-- Inner Rectangle with rounded corners. -->
          <Rectangle x:Name="innerRectangle" HorizontalAlignment="Stretch" VerticalAlignment="Stretch" Stroke="Transparent" StrokeThickness="20" Fill="{TemplateBinding Background}" RadiusX="20" RadiusY="20" />
          <!-- Present Content (text) of the button. -->
          <DockPanel Name="myContentPresenterDockPanel">
            <ContentPresenter x:Name="myContentPresenter" Margin="20" Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />
          </DockPanel>
        </Grid>
      </ControlTemplate>
    </Setter.Value>
    ```

     <span data-ttu-id="86d32-172">F5 키를 눌러 애플리케이션을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-172">Press F5 to run the application.</span></span> <span data-ttu-id="86d32-173">다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-173">It should look like the following.</span></span>

     ![3 개의 단추가 있는 창](./media/custom-button-animatedbutton-4.gif)

3. <span data-ttu-id="86d32-175">**템플릿에 glasseffect를 추가 합니다.** 다음에는 유리를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-175">**Add a glasseffect to the template:** Next you will add the glass.</span></span> <span data-ttu-id="86d32-176">먼저 투명 효과 그라데이션 효과를 만드는 일부 리소스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-176">First you create some resources that create a glass gradient effect.</span></span> <span data-ttu-id="86d32-177">블록 내의 아무 곳에 나 다음과 같은 그라데이션 리소스를 추가 합니다 `Application.Resources` .</span><span class="sxs-lookup"><span data-stu-id="86d32-177">Add these gradient resources anywhere within the `Application.Resources` block:</span></span>

    ```xaml
    <Application.Resources>
      <GradientStopCollection x:Key="MyGlassGradientStopsResource">
        <GradientStop Color="WhiteSmoke" Offset="0.2" />
        <GradientStop Color="Transparent" Offset="0.4" />
        <GradientStop Color="WhiteSmoke" Offset="0.5" />
        <GradientStop Color="Transparent" Offset="0.75" />
        <GradientStop Color="WhiteSmoke" Offset="0.9" />
        <GradientStop Color="Transparent" Offset="1" />
      </GradientStopCollection>
      <LinearGradientBrush x:Key="MyGlassBrushResource"
        StartPoint="0,0" EndPoint="1,1" Opacity="0.75"
        GradientStops="{StaticResource MyGlassGradientStopsResource}" />
    <!-- Styles and other resources below here. -->
    ```

     <span data-ttu-id="86d32-178">이러한 리소스는 <xref:System.Windows.Shapes.Shape.Fill%2A> 단추 템플릿의에 삽입 하는 사각형의로 사용 됩니다 <xref:System.Windows.Controls.Grid> .</span><span class="sxs-lookup"><span data-stu-id="86d32-178">These resources are used as the <xref:System.Windows.Shapes.Shape.Fill%2A> for a rectangle that we insert into the <xref:System.Windows.Controls.Grid> of the button template.</span></span> <span data-ttu-id="86d32-179">템플릿에 다음 강조 표시 된 태그를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-179">Add the following highlighted markup to the template.</span></span>

    ```xaml
    <Setter.Value>
      <ControlTemplate TargetType="{x:Type Button}">
        <Grid Width="{TemplateBinding Width}" Height="{TemplateBinding Height}"
          ClipToBounds="True">

        <!-- Outer Rectangle with rounded corners. -->
        <Rectangle x:Name="outerRectangle" HorizontalAlignment="Stretch"
          VerticalAlignment="Stretch" Stroke="{TemplateBinding Background}"
          RadiusX="20" RadiusY="20" StrokeThickness="5" Fill="Transparent" />

        <!-- Inner Rectangle with rounded corners. -->
        <Rectangle x:Name="innerRectangle" HorizontalAlignment="Stretch"
          VerticalAlignment="Stretch" Stroke="Transparent" StrokeThickness="20"
          Fill="{TemplateBinding Background}" RadiusX="20" RadiusY="20" />

        <!-- Glass Rectangle -->
        <Rectangle x:Name="glassCube" HorizontalAlignment="Stretch"
          VerticalAlignment="Stretch"
          StrokeThickness="2" RadiusX="10" RadiusY="10" Opacity="0"
          Fill="{StaticResource MyGlassBrushResource}"
          RenderTransformOrigin="0.5,0.5">
          <Rectangle.Stroke>
            <LinearGradientBrush StartPoint="0.5,0" EndPoint="0.5,1">
              <LinearGradientBrush.GradientStops>
                <GradientStop Offset="0.0" Color="LightBlue" />
                <GradientStop Offset="1.0" Color="Gray" />
              </LinearGradientBrush.GradientStops>
            </LinearGradientBrush>
          </Rectangle.Stroke>
          <!-- These transforms have no effect as they are declared here.
          The reason the transforms are included is to be targets
          for animation (see later). -->
          <Rectangle.RenderTransform>
            <TransformGroup>
              <ScaleTransform />
              <RotateTransform />
            </TransformGroup>
          </Rectangle.RenderTransform>
          <!-- A BevelBitmapEffect is applied to give the button a "Beveled" look. -->
          <Rectangle.BitmapEffect>
            <BevelBitmapEffect />
          </Rectangle.BitmapEffect>
        </Rectangle>

        <!-- Present Text of the button. -->
        <DockPanel Name="myContentPresenterDockPanel">
          <ContentPresenter x:Name="myContentPresenter" Margin="20"
            Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />
        </DockPanel>
      </Grid>
    </ControlTemplate>
    </Setter.Value>
    ```

     <span data-ttu-id="86d32-180"><xref:System.Windows.UIElement.Opacity%2A>"GlassCube" 속성을 사용 하는 사각형의는 `x:Name` 0 이므로 샘플을 실행 하면 위쪽에 투명 한 투명 직사각형이 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-180">Notice that the <xref:System.Windows.UIElement.Opacity%2A> of the rectangle with the `x:Name` property of "glassCube" is 0, so when you run the sample, you do not see the glass rectangle overlaid on top.</span></span> <span data-ttu-id="86d32-181">이는 나중에 사용자가 단추를 사용 하 여 상호 작용할 때 템플릿에 트리거를 추가 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-181">This is because we will later add triggers to the template for when the user interacts with the button.</span></span> <span data-ttu-id="86d32-182">그러나 <xref:System.Windows.UIElement.Opacity%2A> 값을 1로 변경 하 고 응용 프로그램을 실행 하 여 이제 단추가 어떻게 표시 되는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-182">However, you can see what the button looks like now by changing the <xref:System.Windows.UIElement.Opacity%2A> value to 1 and running the application.</span></span> <span data-ttu-id="86d32-183">다음 그림을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="86d32-183">See the following figure.</span></span> <span data-ttu-id="86d32-184">다음 단계로 진행 하기 전에을 <xref:System.Windows.UIElement.Opacity%2A> 다시 0으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-184">Before proceeding to the next step, change the <xref:System.Windows.UIElement.Opacity%2A> back to 0.</span></span>

     <span data-ttu-id="86d32-185">![XAML을 사용 하 여 만든 사용자 지정 단추](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span><span class="sxs-lookup"><span data-stu-id="86d32-185">![Custom buttons that were created by using XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span></span>

## <a name="create-button-interactivity"></a><span data-ttu-id="86d32-186">단추 대화형 작업 만들기</span><span class="sxs-lookup"><span data-stu-id="86d32-186">Create Button Interactivity</span></span>

<span data-ttu-id="86d32-187">이 섹션에서는 속성 트리거와 이벤트 트리거를 만들어 속성 값을 변경 하 고 단추 위로 마우스 포인터를 이동 하 고를 클릭 하는 등의 사용자 동작에 대 한 응답으로 애니메이션을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-187">In this section, you will create property triggers and event triggers to change property values and run animations in response to user actions such as moving the mouse pointer over the button and clicking.</span></span>

<span data-ttu-id="86d32-188">대화형 작업을 추가 하는 쉬운 방법 (마우스 위로, 마우스-leave, 클릭 등)은 템플릿 또는 스타일 내에서 트리거를 정의 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-188">An easy way to add interactivity (mouse-over, mouse-leave, click, and so on) is to define triggers within your template or style.</span></span> <span data-ttu-id="86d32-189">을 만들려면 <xref:System.Windows.Trigger> 단추 <xref:System.Windows.UIElement.IsMouseOver%2A> 속성 값이와 같은 "condition" 속성을 정의 합니다. `true`</span><span class="sxs-lookup"><span data-stu-id="86d32-189">To create a <xref:System.Windows.Trigger>, you define a property "condition" such as: The button <xref:System.Windows.UIElement.IsMouseOver%2A> property value is equal to `true`.</span></span> <span data-ttu-id="86d32-190">그런 다음 트리거 조건이 true 일 때 발생 하는 setter (동작)를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-190">You then define setters (actions) that take place when the trigger condition is true.</span></span>

### <a name="to-create-button-interactivity"></a><span data-ttu-id="86d32-191">단추 대화형 작업을 만들려면</span><span class="sxs-lookup"><span data-stu-id="86d32-191">To create button interactivity</span></span>

1. <span data-ttu-id="86d32-192">**템플릿 트리거 추가:** 강조 표시 된 태그를 템플릿에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-192">**Add template triggers:** Add the highlighted markup to your template.</span></span>

    ```xaml
    <Setter.Value>
      <ControlTemplate TargetType="{x:Type Button}">
        <Grid Width="{TemplateBinding Width}"
          Height="{TemplateBinding Height}" ClipToBounds="True">

          <!-- Outer Rectangle with rounded corners. -->
          <Rectangle x:Name="outerRectangle" HorizontalAlignment="Stretch"
          VerticalAlignment="Stretch" Stroke="{TemplateBinding Background}"
          RadiusX="20" RadiusY="20" StrokeThickness="5" Fill="Transparent" />

          <!-- Inner Rectangle with rounded corners. -->
          <Rectangle x:Name="innerRectangle" HorizontalAlignment="Stretch"
            VerticalAlignment="Stretch" Stroke="Transparent"
            StrokeThickness="20"
            Fill="{TemplateBinding Background}" RadiusX="20" RadiusY="20"
          />

          <!-- Glass Rectangle -->
          <Rectangle x:Name="glassCube" HorizontalAlignment="Stretch"
            VerticalAlignment="Stretch"
            StrokeThickness="2" RadiusX="10" RadiusY="10" Opacity="0"
            Fill="{StaticResource MyGlassBrushResource}"
            RenderTransformOrigin="0.5,0.5">
            <Rectangle.Stroke>
              <LinearGradientBrush StartPoint="0.5,0" EndPoint="0.5,1">
                <LinearGradientBrush.GradientStops>
                  <GradientStop Offset="0.0" Color="LightBlue" />
                  <GradientStop Offset="1.0" Color="Gray" />
                </LinearGradientBrush.GradientStops>
              </LinearGradientBrush>
            </Rectangle.Stroke>

            <!-- These transforms have no effect as they
                 are declared here.
                 The reason the transforms are included is to be targets
                 for animation (see later). -->
            <Rectangle.RenderTransform>
              <TransformGroup>
                <ScaleTransform />
                <RotateTransform />
              </TransformGroup>
            </Rectangle.RenderTransform>

              <!-- A BevelBitmapEffect is applied to give the button a
                   "Beveled" look. -->
            <Rectangle.BitmapEffect>
              <BevelBitmapEffect />
            </Rectangle.BitmapEffect>
          </Rectangle>

          <!-- Present Text of the button. -->
          <DockPanel Name="myContentPresenterDockPanel">
            <ContentPresenter x:Name="myContentPresenter" Margin="20"
              Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />
          </DockPanel>
        </Grid>

        <ControlTemplate.Triggers>       <!-- Set action triggers for the buttons and define            what the button does in response to those triggers. -->     </ControlTemplate.Triggers>
      </ControlTemplate>
    </Setter.Value>
    ```

2. <span data-ttu-id="86d32-193">**속성 트리거 추가:** 강조 표시 된 태그를 블록에 추가 합니다 `ControlTemplate.Triggers` .</span><span class="sxs-lookup"><span data-stu-id="86d32-193">**Add property triggers:** Add the highlighted markup to the `ControlTemplate.Triggers` block:</span></span>

    ```xaml
    <ControlTemplate.Triggers>

      <!-- Set properties when mouse pointer is over the button. -->   <Trigger Property="IsMouseOver" Value="True">     <!-- Below are three property settings that occur when the           condition is met (user mouses over button).  -->     <!-- Change the color of the outer rectangle when user           mouses over it. -->     <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <!-- Sets the glass opacity to 1, therefore, the           glass "appears" when user mouses over it. -->     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />     <!-- Makes the text slightly blurry as though you           were looking at it through blurry glass. -->     <Setter Property="ContentPresenter.BitmapEffect"        TargetName="myContentPresenter">       <Setter.Value>         <BlurBitmapEffect Radius="1" />       </Setter.Value>     </Setter>   </Trigger>

    <ControlTemplate.Triggers/>
    ```

     <span data-ttu-id="86d32-194">F5 키를 눌러 응용 프로그램을 실행 하 고 단추 위에 마우스 포인터를 놓으면 효과를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-194">Press F5 to run the application and see the effect as you run the mouse pointer over the buttons.</span></span>

3. <span data-ttu-id="86d32-195">**포커스 트리거를 추가 합니다.** 다음으로, 단추에 포커스가 있을 때 (예: 사용자가 클릭 한 후) 사례를 처리 하는 비슷한 setter를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-195">**Add a focus trigger:** Next, we'll add some similar setters to handle the case when the button has focus (for example, after the user clicks it).</span></span>

    ```xaml
    <ControlTemplate.Triggers>

      <!-- Set properties when mouse pointer is over the button. -->
      <Trigger Property="IsMouseOver" Value="True">

        <!-- Below are three property settings that occur when the
             condition is met (user mouses over button).  -->
        <!-- Change the color of the outer rectangle when user          mouses over it. -->
        <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"
          Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />

        <!-- Sets the glass opacity to 1, therefore, the          glass "appears" when user mouses over it. -->
        <Setter Property="Rectangle.Opacity" Value="1"       TargetName="glassCube" />

        <!-- Makes the text slightly blurry as though you were          looking at it through blurry glass. -->
        <Setter Property="ContentPresenter.BitmapEffect"       TargetName="myContentPresenter">
          <Setter.Value>
            <BlurBitmapEffect Radius="1" />
          </Setter.Value>
        </Setter>
      </Trigger>
      <!-- Set properties when button has focus. -->   <Trigger Property="IsFocused" Value="true">     <Setter Property="Rectangle.Opacity" Value="1"       TargetName="glassCube" />     <Setter Property="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />   </Trigger>

    </ControlTemplate.Triggers>
    ```

     <span data-ttu-id="86d32-196">F5 키를 눌러 응용 프로그램을 실행 하 고 단추 중 하나를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-196">Press F5 to run the application and click on one of the buttons.</span></span> <span data-ttu-id="86d32-197">단추는 여전히 포커스를 가지 므로 클릭 하면 강조 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-197">Notice that the button stays highlighted after you click it because it still has focus.</span></span> <span data-ttu-id="86d32-198">다른 단추를 클릭 하면 마지막 단추를 클릭 하면 포커스가 사라집니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-198">If you click another button, the new button gains focus while the last one loses it.</span></span>

4. <span data-ttu-id="86d32-199">**애니메이션 추가** <xref:System.Windows.UIElement.MouseEnter> **및** <xref:System.Windows.UIElement.MouseLeave> **:** 다음으로 트리거에 일부 애니메이션을 추가 합니다.  </span><span class="sxs-lookup"><span data-stu-id="86d32-199">**Add animations for**  <xref:System.Windows.UIElement.MouseEnter> **and** <xref:System.Windows.UIElement.MouseLeave> **:** Next we add some animations to the triggers.</span></span> <span data-ttu-id="86d32-200">블록 내부에서 다음 태그를 추가 합니다 `ControlTemplate.Triggers` .</span><span class="sxs-lookup"><span data-stu-id="86d32-200">Add the following markup anywhere inside of the `ControlTemplate.Triggers` block.</span></span>

    ```xaml
    <!-- Animations that start when mouse enters and leaves button. -->
    <EventTrigger RoutedEvent="Mouse.MouseEnter">
      <EventTrigger.Actions>
        <BeginStoryboard Name="mouseEnterBeginStoryboard">
          <Storyboard>
          <!-- This animation makes the glass rectangle shrink in the X direction. -->
            <DoubleAnimation Storyboard.TargetName="glassCube"
              Storyboard.TargetProperty=
              "(Rectangle.RenderTransform).(TransformGroup.Children)[0].(ScaleTransform.ScaleX)"
              By="-0.1" Duration="0:0:0.5" />
            <!-- This animation makes the glass rectangle shrink in the Y direction. -->
            <DoubleAnimation
            Storyboard.TargetName="glassCube"
              Storyboard.TargetProperty=
              "(Rectangle.RenderTransform).(TransformGroup.Children)[0].(ScaleTransform.ScaleY)"
              By="-0.1" Duration="0:0:0.5" />
          </Storyboard>
        </BeginStoryboard>
      </EventTrigger.Actions>
    </EventTrigger>
    <EventTrigger RoutedEvent="Mouse.MouseLeave">
      <EventTrigger.Actions>
        <!-- Stopping the storyboard sets all animated properties back to default. -->
        <StopStoryboard BeginStoryboardName="mouseEnterBeginStoryboard" />
      </EventTrigger.Actions>
    </EventTrigger>
    ```

     <span data-ttu-id="86d32-201">마우스 포인터를 단추 위로 이동할 때 투명 효과 사각형이 축소 되 고 포인터가 벗어나면 정상 크기로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-201">The glass rectangle shrinks when the mouse pointer moves over the button and returns back to normal size when the pointer leaves.</span></span>

     <span data-ttu-id="86d32-202">포인터가 단추 위로 이동할 때 트리거되는 두 개의 애니메이션 (이벤트가 발생 하는 경우)이 있습니다 <xref:System.Windows.UIElement.MouseEnter> .</span><span class="sxs-lookup"><span data-stu-id="86d32-202">There are two animations that are triggered when the pointer goes over the button (<xref:System.Windows.UIElement.MouseEnter> event is raised).</span></span> <span data-ttu-id="86d32-203">이러한 애니메이션은 X 및 Y 축을 따라 투명 효과 사각형을 축소 합니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-203">These animations shrink the glass rectangle along the X and Y axis.</span></span> <span data-ttu-id="86d32-204">요소에 대 한 속성 및를 확인 합니다 <xref:System.Windows.Media.Animation.DoubleAnimation> <xref:System.Windows.Media.Animation.Timeline.Duration%2A> <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> .</span><span class="sxs-lookup"><span data-stu-id="86d32-204">Notice the properties on the <xref:System.Windows.Media.Animation.DoubleAnimation> elements — <xref:System.Windows.Media.Animation.Timeline.Duration%2A> and <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.</span></span> <span data-ttu-id="86d32-205">는 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 애니메이션이 0.5 초 이상 발생 하도록 지정 하 고 <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> 투명 효과를 10% 씩 축소 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-205">The <xref:System.Windows.Media.Animation.Timeline.Duration%2A> specifies that the animation occurs over half a second, and <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> specifies that the glass shrinks by 10%.</span></span>

     <span data-ttu-id="86d32-206">두 번째 이벤트 트리거 ( <xref:System.Windows.UIElement.MouseLeave> )는 첫 번째 트리거를 중지 하기만 합니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-206">The second event trigger (<xref:System.Windows.UIElement.MouseLeave>) simply stops the first one.</span></span> <span data-ttu-id="86d32-207">를 중지 하면 <xref:System.Windows.Media.Animation.Storyboard> 애니메이션을 적용 하는 모든 속성이 해당 기본값으로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-207">When you stop a <xref:System.Windows.Media.Animation.Storyboard>, all the animated properties return to their default values.</span></span> <span data-ttu-id="86d32-208">따라서 사용자가 포인터를 단추 밖으로 움직이면 단추가 단추 위로 마우스 포인터를 이동 하기 전의 상태로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-208">Therefore, when the user moves the pointer off the button, the button goes back to the way it was before the mouse pointer moved over the button.</span></span> <span data-ttu-id="86d32-209">애니메이션에 대 한 자세한 내용은 [애니메이션 개요](../graphics-multimedia/animation-overview.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="86d32-209">For more information about animations, see [Animation Overview](../graphics-multimedia/animation-overview.md).</span></span>

5. <span data-ttu-id="86d32-210">**단추를 클릭 하면에 대 한 애니메이션을 추가 합니다.** 마지막 단계는 사용자가 단추를 클릭할 때에 대 한 트리거를 추가 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-210">**Add an animation for when the button is clicked:** The final step is to add a trigger for when the user clicks the button.</span></span> <span data-ttu-id="86d32-211">블록 내부에서 다음 태그를 추가 합니다 `ControlTemplate.Triggers` .</span><span class="sxs-lookup"><span data-stu-id="86d32-211">Add the following markup anywhere inside of the `ControlTemplate.Triggers` block:</span></span>

    ```xaml
    <!-- Animation fires when button is clicked, causing glass to spin.  -->
    <EventTrigger RoutedEvent="Button.Click">
      <EventTrigger.Actions>
        <BeginStoryboard>
          <Storyboard>
            <DoubleAnimation Storyboard.TargetName="glassCube"
              Storyboard.TargetProperty=
              "(Rectangle.RenderTransform).(TransformGroup.Children)[1].(RotateTransform.Angle)"
              By="360" Duration="0:0:0.5" />
          </Storyboard>
        </BeginStoryboard>
      </EventTrigger.Actions>
    </EventTrigger>
    ```

     <span data-ttu-id="86d32-212">F5 키를 눌러 응용 프로그램을 실행 하 고 단추 중 하나를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-212">Press F5 to run the application, and click one of the buttons.</span></span> <span data-ttu-id="86d32-213">단추를 클릭 하면 투명 직사각형이 회전 합니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-213">When you click a button, the glass rectangle spins around.</span></span>

## <a name="summary"></a><span data-ttu-id="86d32-214">요약</span><span class="sxs-lookup"><span data-stu-id="86d32-214">Summary</span></span>
 <span data-ttu-id="86d32-215">이 연습에서는 다음 연습을 수행 했습니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-215">In this walkthrough, you performed the following exercises:</span></span>

- <span data-ttu-id="86d32-216"><xref:System.Windows.Style>개체 형식 ()에 대 한 대상 <xref:System.Windows.Controls.Button> 입니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-216">Targeted a <xref:System.Windows.Style> to an object type (<xref:System.Windows.Controls.Button>).</span></span>

- <span data-ttu-id="86d32-217">를 사용 하 여 전체 응용 프로그램의 단추 기본 속성을 제어 <xref:System.Windows.Style> 합니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-217">Controlled basic properties of the buttons in the entire application using the <xref:System.Windows.Style>.</span></span>

- <span data-ttu-id="86d32-218">Setter의 속성 값에 사용할 그라데이션과 같은 리소스를 만들었습니다 <xref:System.Windows.Style> .</span><span class="sxs-lookup"><span data-stu-id="86d32-218">Created resources like gradients to use for property values of the <xref:System.Windows.Style> setters.</span></span>

- <span data-ttu-id="86d32-219">단추에 템플릿을 적용 하 여 전체 응용 프로그램에서 단추의 모양을 사용자 지정 했습니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-219">Customized the look of buttons in the entire application by applying a template to the buttons.</span></span>

- <span data-ttu-id="86d32-220"><xref:System.Windows.UIElement.MouseEnter> <xref:System.Windows.UIElement.MouseLeave> 애니메이션 효과를 포함 하는 사용자 작업 (예:, 및)에 대 한 응답으로 단추에 대 한 사용자 지정 동작 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 입니다.</span><span class="sxs-lookup"><span data-stu-id="86d32-220">Customized behavior for the buttons in response to user actions (such as <xref:System.Windows.UIElement.MouseEnter>, <xref:System.Windows.UIElement.MouseLeave>, and <xref:System.Windows.Controls.Primitives.ButtonBase.Click>) that included animation effects.</span></span>

## <a name="see-also"></a><span data-ttu-id="86d32-221">참조</span><span class="sxs-lookup"><span data-stu-id="86d32-221">See also</span></span>

- [<span data-ttu-id="86d32-222">Microsoft Expression Blend를 사용하여 단추 만들기</span><span class="sxs-lookup"><span data-stu-id="86d32-222">Create a Button by Using Microsoft Expression Blend</span></span>](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)
- [<span data-ttu-id="86d32-223">스타일 지정 및 템플릿</span><span class="sxs-lookup"><span data-stu-id="86d32-223">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="86d32-224">애니메이션 개요</span><span class="sxs-lookup"><span data-stu-id="86d32-224">Animation Overview</span></span>](../graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="86d32-225">단색 및 그라데이션을 사용한 그리기 개요</span><span class="sxs-lookup"><span data-stu-id="86d32-225">Painting with Solid Colors and Gradients Overview</span></span>](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="86d32-226">비트맵 효과 개요</span><span class="sxs-lookup"><span data-stu-id="86d32-226">Bitmap Effects Overview</span></span>](../graphics-multimedia/bitmap-effects-overview.md)
