---
title: 애니메이션 개요
description: WPF (Windows Presentation Foundation)에서 극적인 화면 전환 또는 선명한 시각적 신호로 더욱 화려하 매력적인 사용자 인터페이스를 만듭니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], animations
- animations [WPF], overview
ms.assetid: bd9ce563-725d-4385-87c9-d7ee38cf79ea
ms.openlocfilehash: d761be0c95fb8aa7eb39cb26b57979185226b8fb
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853863"
---
# <a name="animation-overview"></a>애니메이션 개요

<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]는 매력적인 사용자 인터페이스와 멋진 문서를 만들 수 있도록 하는 강력한 그래픽 및 레이아웃 기능 집합을 제공합니다. 애니메이션은 매력적인 사용자 인터페이스를 훨씬 더 화려하고 유용하게 만들어줄 수 있습니다. 배경색에 애니메이션 효과를 적용 하거나 애니메이션 효과를 적용 하 여 <xref:System.Windows.Media.Transform> 극적인 화면 전환을 만들거나 유용한 시각적 신호를 제공할 수 있습니다.

이 개요에서는 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 애니메이션 및 타이밍 시스템에 대해 소개 합니다. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Storyboard를 사용 하 여 개체의 애니메이션을 중심으로 설명 합니다.

<a name="introducinganimations"></a>

## <a name="introducing-animations"></a>애니메이션 소개

애니메이션은 마지막까지 조금씩 달라지는 일련의 이미지를 빠르게 순환하면서 만들어지는 효과입니다. 뇌는 이미지 그룹을 변화하는 하나의 영상으로 인식합니다. 영화에서는 많은 사진 또는 프레임을 초별로 기록하는 카메라를 사용하여 이러한 효과를 만듭니다. 프로젝터에서 프레임이 재생되면 청중은 동영상을 보게 됩니다.

컴퓨터의 애니메이션도 유사합니다. 예를 들어 사각형 그림을 보기에서 페이드 아웃하는 프로그램은 다음과 같이 작동할 수 있습니다.

- 프로그램이 타이머를 만듭니다.

- 프로그램이 설정된 간격으로 타이머를 확인하여 경과된 시간을 파악합니다.

- 프로그램이 타이머를 확인할 때마다 경과된 시간에 따라 사각형의 현재 불투명도 값을 계산합니다.

- 그런 다음 새 값으로 사각형을 업데이트한 후 그립니다.

이전에는 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Microsoft Windows 개발자가 자신의 타이밍 시스템을 만들고 관리 하거나 특수 한 사용자 지정 라이브러리를 사용 해야 했습니다. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]에는 관리 코드를 통해 노출 되 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 고 프레임 워크에 긴밀 하 게 통합 된 효율적인 타이밍 시스템이 포함 되어 있습니다 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] . [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 애니메이션을 사용하면 쉽게 컨트롤 및 기타 그래픽 개체에 애니메이션 효과를 줄 수 있습니다.

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]는 타이밍 시스템을 관리하고 화면을 효율적으로 다시 그리는 모든 백그라운드 작업을 처리합니다. 그뿐 아니라 이러한 효과를 달성하는 기법이 아닌, 만들려는 효과에 집중할 수 있도록 하는 타이밍 클래스를 제공합니다. 또한 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]에서는 클래스가 상속할 수 있는 애니메이션 기본 클래스를 노출하여 사용자 고유의 애니메이션을 쉽게 만들 수 있도록 하므로 애니메이션을 사용자 지정할 수 있습니다. 이러한 사용자 지정 애니메이션은 표준 애니메이션 클래스에 비해 성능상의 이점도 큽니다.

<a name="thewpftimingsystem"></a>

## <a name="wpf-property-animation-system"></a>WPF 속성 애니메이션 시스템

타이밍 시스템에 대 한 몇 가지 중요 한 개념을 이해 하는 경우 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 애니메이션을 보다 쉽게 사용할 수 있습니다. 가장 중요 한 점은에서 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 개별 속성에 애니메이션을 적용 하 여 개체에 애니메이션 효과를 주는 것입니다. 예를 들어 프레임 워크 요소가 증가 하도록 하려면 해당 및 속성에 애니메이션 효과를 적용 <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> 합니다. 뷰에서 개체의 페이드를 만들려면 해당 속성에 애니메이션 효과를 적용 <xref:System.Windows.UIElement.Opacity%2A> 합니다.

속성에 애니메이션 기능을 부여하려면 다음 세 가지 요구 사항을 충족해야 합니다.

- 종속성 속성이어야 합니다.

- 이 클래스는에서 상속 되 <xref:System.Windows.DependencyObject> 고 인터페이스를 구현 하는 클래스에 속해야 합니다 <xref:System.Windows.Media.Animation.IAnimatable> .

- 사용 가능한 호환되는 애니메이션 형식이어야 합니다. ( [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 에서 제공 하지 않는 경우 직접 만들 수 있습니다. [사용자 지정 애니메이션 개요](custom-animations-overview.md)를 참조 하세요.)

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]에는 속성이 있는 많은 개체가 포함 되어 있습니다 <xref:System.Windows.Media.Animation.IAnimatable> . <xref:System.Windows.Controls.Button>및 등의 컨트롤과 <xref:System.Windows.Controls.TabControl> <xref:System.Windows.Controls.Panel> 및 개체는 <xref:System.Windows.Shapes.Shape> 에서 상속 <xref:System.Windows.DependencyObject> 합니다. 해당 속성 대부분은 종속성 속성입니다.

스타일 및 템플릿 컨트롤을 비롯한 거의 모든 위치에서 애니메이션을 사용할 수 있습니다. 애니메이션은 시각적일 필요가 없습니다. 이 섹션에 설명된 조건을 충족하지 않을 경우 사용자 인터페이스에 속하지 않는 개체에 애니메이션 효과를 줄 수 있습니다.

<a name="storyboardwalkthrough"></a>

## <a name="example-make-an-element-fade-in-and-out-of-view"></a>예제: 보기에서 요소 페이드 인 및 페이드 아웃

이 예제에서는 애니메이션을 사용 하 여 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 종속성 속성의 값에 애니메이션 효과를 주는 방법을 보여 줍니다. 이 클래스는 <xref:System.Windows.Media.Animation.DoubleAnimation> 값을 생성 하는 애니메이션 형식인를 사용 하 여 <xref:System.Double> 의 속성에 애니메이션 효과를 적용 <xref:System.Windows.UIElement.Opacity%2A> <xref:System.Windows.Shapes.Rectangle> 합니다. 결과적으로는 <xref:System.Windows.Shapes.Rectangle> 뷰에서 페이드 인 및 페이드 아웃 됩니다.

예제의 첫 번째 부분에서는 요소를 만듭니다 <xref:System.Windows.Shapes.Rectangle> . 다음 단계에서는 애니메이션을 만들어 사각형의 속성에 적용 하는 방법을 보여 줍니다 <xref:System.Windows.UIElement.Opacity%2A> .

다음은 XAML의에서 요소를 만드는 방법을 보여 줍니다 <xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.Controls.StackPanel> .

[!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_1](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_1)]

다음은 코드에서에 요소를 만드는 방법을 보여 줍니다 <xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.Controls.StackPanel> .

[!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_1](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_1)]
[!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_1)]

<a name="opacity_animation_step1"></a>

### <a name="part-1-create-a-doubleanimation"></a>1부: DoubleAnimation 만들기

뷰에서 요소를 페이드 인 및 페이드 아웃 하는 한 가지 방법은 해당 속성에 애니메이션 효과를 주는 것입니다 <xref:System.Windows.UIElement.Opacity%2A> . 속성은 <xref:System.Windows.UIElement.Opacity%2A> 형식 이므로 <xref:System.Double> double 값을 생성 하는 애니메이션이 필요 합니다. 는 <xref:System.Windows.Media.Animation.DoubleAnimation> 이러한 애니메이션 중 하나입니다. 는 <xref:System.Windows.Media.Animation.DoubleAnimation> 두 double 값 사이에 전환을 만듭니다. 해당 시작 값을 지정 하려면 해당 속성을 설정 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> 합니다. 끝 값을 지정 하려면 해당 속성을 설정 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> 합니다.

1. 의 불투명도 값은 `1.0` 개체를 완전히 불투명 하 게 만들고,의 불투명도 값을 사용 하면 `0.0` 완전히 보이지 않게 됩니다. 에서로의 애니메이션 전환을 수행 `1.0` 하려면 `0.0` 해당 속성을로 설정 하 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> `1.0` 고 해당 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> 속성을로 설정 `0.0` 합니다. 다음은 XAML에서을 만드는 방법을 보여 줍니다 <xref:System.Windows.Media.Animation.DoubleAnimation> .

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_2](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_2)]

    다음은 코드에서를 만드는 방법을 보여 줍니다 <xref:System.Windows.Media.Animation.DoubleAnimation> .

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_2](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_2)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_2)]

2. 다음에는를 지정 해야 합니다 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> . <xref:System.Windows.Media.Animation.Timeline.Duration%2A>애니메이션의는 시작 값에서 대상 값으로 이동 하는 데 소요 되는 시간을 지정 합니다. 다음은 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> XAML에서을 5 초로 설정 하는 방법을 보여 줍니다.

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_3](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_3)]

    다음은 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 코드에서을 5 초로 설정 하는 방법을 보여 줍니다.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_3](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_3)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_3)]

3. 이전 코드에서는에서로 전환 하는 애니메이션을 보여 주었습니다 `1.0` `0.0` . 그러면 대상 요소가 완전히 불투명 하 고 완전히 보이지 않게 변합니다. 요소가 사라지는 후에도 다시 표시 되도록 하려면 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> 애니메이션의 속성을로 설정 `true` 합니다. 애니메이션을 무기한 반복 하 게 하려면 해당 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> 속성을로 설정 <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A> 합니다. 다음은 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> XAML에서 및 속성을 설정 하는 방법을 보여 줍니다 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> .

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_4](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_4)]

    다음은 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> 코드에서 및 속성을 설정 하는 방법을 보여 줍니다 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> .

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_4](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_4)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_4)]

<a name="opacity_animation_step2"></a>

### <a name="part-2-create-a-storyboard"></a>2부: Storyboard 만들기

개체에 애니메이션을 적용 하려면를 만들고 <xref:System.Windows.Media.Animation.Storyboard> 및 연결 된 속성을 사용 하 여 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> 애니메이션 효과를 적용할 개체와 속성을 지정 합니다.

1. 를 만들고 <xref:System.Windows.Media.Animation.Storyboard> 애니메이션을 자식으로 추가 합니다. 다음은 XAML에서을 만드는 방법을 보여 줍니다 <xref:System.Windows.Media.Animation.Storyboard> .

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_5](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_5)]

    <xref:System.Windows.Media.Animation.Storyboard>코드에서를 만들려면 <xref:System.Windows.Media.Animation.Storyboard> 클래스 수준에서 변수를 선언 합니다.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_100](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_100)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_100)]

    그런 다음를 초기화 <xref:System.Windows.Media.Animation.Storyboard> 하 고 애니메이션을 자식으로 추가 합니다.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_101](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_101)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_101)]

2. 는 <xref:System.Windows.Media.Animation.Storyboard> 애니메이션을 적용할 위치를 알고 있어야 합니다. 연결 된 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> 속성을 사용 하 여 애니메이션 효과를 적용할 개체를 지정 합니다. 다음에서는 XAML에서의 대상 이름을로 설정 하는 방법을 보여 줍니다 <xref:System.Windows.Media.Animation.DoubleAnimation> `MyRectangle` .

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_6](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_6)]

    다음은 코드에서의 대상 이름을로 설정 하는 방법을 보여 줍니다 <xref:System.Windows.Media.Animation.DoubleAnimation> `MyRectangle` .

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_102](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_102)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_102)]

3. 연결 된 속성을 사용 하 여 <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> 애니메이션 효과를 적용할 속성을 지정 합니다. 다음에서는 <xref:System.Windows.UIElement.Opacity%2A> XAML에서의 속성을 대상으로 하는 애니메이션을 구성 하는 방법을 보여 줍니다 <xref:System.Windows.Shapes.Rectangle> .

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_7](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_7)]

    다음은 <xref:System.Windows.UIElement.Opacity%2A> 코드에서의 속성을 대상으로 하는 애니메이션을 구성 하는 방법을 보여 줍니다 <xref:System.Windows.Shapes.Rectangle> .

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_103](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_103)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_103)]

<xref:System.Windows.Media.Animation.Storyboard.TargetProperty>구문 및 추가 예제에 대 한 자세한 내용은 [storyboard 개요](storyboards-overview.md)를 참조 하세요.

<a name="opacity_animation_step3"></a>

### <a name="part-3-xaml-associate-the-storyboard-with-a-trigger"></a>3부: Storyboard를 트리거에 연결

에서를 적용 하 고 시작 하는 가장 쉬운 방법은 <xref:System.Windows.Media.Animation.Storyboard> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 이벤트 트리거를 사용 하는 것입니다. 이 섹션에서는를 XAML의 트리거와 연결 하는 방법을 보여 줍니다 <xref:System.Windows.Media.Animation.Storyboard> .

1. 개체를 만들고 <xref:System.Windows.Media.Animation.BeginStoryboard> 스토리 보드를 연결 합니다. 는를 <xref:System.Windows.Media.Animation.BeginStoryboard> <xref:System.Windows.TriggerAction> 적용 하 고 시작 하는의 형식입니다 <xref:System.Windows.Media.Animation.Storyboard> .

    [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_3](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_3)]

2. 를 만들고를 <xref:System.Windows.EventTrigger> <xref:System.Windows.Media.Animation.BeginStoryboard> 해당 컬렉션에 추가 합니다 <xref:System.Windows.EventTrigger.Actions%2A> . <xref:System.Windows.EventTrigger.RoutedEvent%2A>의 속성을를 <xref:System.Windows.EventTrigger> 시작 하려는 라우트된 이벤트로 설정 합니다 <xref:System.Windows.Media.Animation.Storyboard> . 라우트된 이벤트에 대 한 자세한 내용은 [라우트된 이벤트 개요](../advanced/routed-events-overview.md)를 참조 하세요.

    [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_2](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_2)]

3. <xref:System.Windows.EventTrigger>사각형의 컬렉션에를 추가 합니다 <xref:System.Windows.FrameworkElement.Triggers%2A> .

    [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_1](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_1)]

<a name="opacity_animation_step3code"></a>

### <a name="part-3-code-associate-the-storyboard-with-an-event-handler"></a>3부(코드): Storyboard를 이벤트 처리기에 연결

코드에서를 적용 하 고 시작 하는 가장 쉬운 방법은 <xref:System.Windows.Media.Animation.Storyboard> 이벤트 처리기를 사용 하는 것입니다. 이 섹션에서는를 <xref:System.Windows.Media.Animation.Storyboard> 코드의 이벤트 처리기와 연결 하는 방법을 보여 줍니다.

1. <xref:System.Windows.FrameworkElement.Loaded>사각형의 이벤트를 등록 합니다.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_104](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_104)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_104)]

2. 이벤트 처리기를 선언합니다. 이벤트 처리기에서 메서드를 사용 <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> 하 여 스토리 보드를 적용 합니다.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_105](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_105)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_105](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_105)]

### <a name="complete-example"></a>전체 예제

다음은 XAML에서 뷰를 페이드 인 및 페이드 아웃 하는 사각형을 만드는 방법을 보여 줍니다.

[!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml#rectangleopacityfadeexamplexaml)]

다음에서는 코드에서 보기로부터 페이드 인 및 페이드 아웃되는 사각형을 만드는 방법을 보여 줍니다.

[!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode)]
[!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode)]

<a name="animationtypes"></a>

## <a name="animation-types"></a>애니메이션 형식

애니메이션은 속성 값을 생성하므로 속성 형식마다 다양한 애니메이션 형식이 존재합니다. 요소의 속성과 같이를 사용 하는 속성에 애니메이션 효과를 주려면 <xref:System.Double> <xref:System.Windows.FrameworkElement.Width%2A> 값을 생성 하는 애니메이션을 사용 <xref:System.Double> 합니다. 을 사용 하는 속성에 애니메이션 효과를 주려면 <xref:System.Windows.Point> 값을 생성 하는 애니메이션을 사용 하는 등의 작업을 수행 <xref:System.Windows.Point> 합니다. 속성 형식이 다르기 때문에 네임 스페이스에 몇 가지 애니메이션 클래스가 있습니다 <xref:System.Windows.Media.Animation> . 다행스럽게도 쉬운 구분을 위해 엄격한 명명 규칙을 따릅니다.

- \<*Type*>애니메이션

  "From/To/By" 또는 "basic" 애니메이션으로도 알려져 있는 이러한 클래스는 시작 값과 대상 값 사이에 애니메이션 효과를 주거나 시작 값에 오프셋 값을 추가하여 애니메이션 효과를 줍니다.

  - 시작 값을 지정하려면 애니메이션의 From 속성을 설정합니다.

  - 끝 값을 지정하려면 애니메이션의 To 속성을 설정합니다.

  - 오프셋 값을 지정하려면 애니메이션의 By 속성을 설정합니다.

  이러한 애니메이션이 가장 사용하기 쉬우므로 이 개요의 예제에서도 사용됩니다. From/to/by 애니메이션은 From/To/By 애니메이션 개요에 자세히 설명 되어 있습니다.

- \<*Type*>AnimationUsingKeyFrames

  키 프레임 애니메이션은 원하는 수의 대상 값을 지정하고 보간 방법을 제어할 수 있으므로 From/To/By 애니메이션보다 훨씬 더 강력합니다. 일부 형식은 키 프레임 애니메이션으로만 애니메이션 효과를 줄 수 있습니다. 키 프레임 애니메이션은 [키 프레임 애니메이션 개요](key-frame-animations-overview.md)에 자세히 설명 되어 있습니다.

- \<*Type*>AnimationUsingPath

  경로 애니메이션에서는 기하학적 경로를 사용하여 애니메이션 사용 값을 생성할 수 있습니다.

- \<*Type*>AnimationBase

  구현할 때 값에 애니메이션 효과를 주는 추상 클래스입니다 \<*Type*> . 이 클래스는 Animation 및 AnimationUsingKeyFrames 클래스에 대 한 기본 클래스로 사용 \<*Type*> \<*Type*> 됩니다. 사용자 고유의 사용자 지정 애니메이션을 만들려는 경우에만 이러한 클래스를 직접 처리해야 합니다. 그렇지 않으면 \<*Type*> 애니메이션 또는 키 프레임 애니메이션을 사용 \<*Type*> 합니다.

대부분의 경우 및와 같은 애니메이션 클래스를 사용 하는 것이 좋습니다 \<*Type*> <xref:System.Windows.Media.Animation.DoubleAnimation> <xref:System.Windows.Media.Animation.ColorAnimation> .

다음 표에서는 몇 가지 일반적인 애니메이션 형식 및 사용되는 일부 속성을 보여 줍니다.

|속성 형식|해당 basic(From/To/By) 애니메이션|해당 키 프레임 애니메이션|해당 경로 애니메이션|사용 예제|
|-------------------|----------------------------------------------------|---------------------------------------|----------------------------------|-------------------|
|<xref:System.Windows.Media.Color>|<xref:System.Windows.Media.Animation.ColorAnimation>|<xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>|없음|또는의에 애니메이션 효과를 적용 <xref:System.Windows.Media.SolidColorBrush.Color%2A> <xref:System.Windows.Media.SolidColorBrush> <xref:System.Windows.Media.GradientStop> 합니다.|
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimation>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|의 또는의에 애니메이션 효과를 적용 <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.Controls.Button> 합니다.|
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimation>|<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>|<xref:System.Windows.Media.Animation.PointAnimationUsingPath>|의 위치에 애니메이션 효과를 적용 <xref:System.Windows.Media.EllipseGeometry.Center%2A> <xref:System.Windows.Media.EllipseGeometry> 합니다.|
|<xref:System.String>|없음|<xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>|없음|의 또는의에 애니메이션 효과를 적용 <xref:System.Windows.Controls.TextBlock.Text%2A> <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.ContentControl.Content%2A> <xref:System.Windows.Controls.Button> 합니다.|

<a name="animationsaretimelines"></a>

### <a name="animations-are-timelines"></a>애니메이션은 타임라인임

모든 애니메이션 형식은 클래스에서 상속 <xref:System.Windows.Media.Animation.Timeline> 되므로 모든 애니메이션은 타임 라인 형식입니다. 는 <xref:System.Windows.Media.Animation.Timeline> 시간 세그먼트를 정의 합니다. 타임 라인의 *타이밍 동작* <xref:System.Windows.Media.Animation.Timeline.Duration%2A> , 반복 횟수 및 속도에 대 한 시간을 지정할 수 있습니다.

애니메이션은 이므로 <xref:System.Windows.Media.Animation.Timeline> 시간 세그먼트도 나타냅니다. 애니메이션은 지정 된 시간 (또는) 세그먼트를 통해 진행 될 때 출력 값도 계산 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 합니다. 애니메이션은 진행되거나 "재생"되면서 연결된 속성을 업데이트합니다.

자주 사용 되는 세 가지 타이밍 속성은 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> , <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> 및 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> 입니다.

#### <a name="the-duration-property"></a>Duration 속성

앞서 설명한 것처럼 타임라인은 시간 세그먼트를 나타냅니다. 이 세그먼트의 길이는 타임 라인의에 따라 결정 되며 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 일반적으로 값을 사용 하 여 지정 됩니다 <xref:System.Windows.Duration.TimeSpan%2A> . 타임라인이 기간 끝에 도달하면 반복이 완료되는 것입니다.

애니메이션은 해당 속성을 사용 하 여 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 현재 값을 확인 합니다. 애니메이션 값을 지정 하지 않으면 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 기본값인 1 초가 사용 됩니다.

다음 구문에서는 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 속성에 대 한 특성 구문의 단순화 된 버전을 보여 줍니다 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> .

*시간* `:` *분* `:` *초*

다음 표에서는 여러 <xref:System.Windows.Duration> 설정 및 그 결과 값을 보여 줍니다.

|설정|결과 값|
|-------------|---------------------|
|0:0:5.5|5.5초|
|0:30:5.5|30분 5.5초|
|1:30:5.5|1시간 30분 5.5초|

코드에서를 지정 하는 한 가지 방법은 메서드를 사용 하 여 <xref:System.Windows.Duration> <xref:System.TimeSpan.FromSeconds%2A> 을 만든 다음이를 <xref:System.TimeSpan> <xref:System.Windows.Duration> 사용 하 여 새 구조체를 선언 하는 것입니다 <xref:System.TimeSpan> .

값 및 전체 구문에 대 한 자세한 내용은 <xref:System.Windows.Duration> [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 구조체를 참조 하세요 <xref:System.Windows.Duration> .

#### <a name="autoreverse"></a>AutoReverse

<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>속성은 타임 라인이의 끝에 도달한 후 역방향으로 재생 되는지 여부를 지정 합니다 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> . 이 애니메이션 속성을로 설정 하는 경우 `true` 애니메이션은의 끝에 도달 하 고 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 끝 값부터 다시 시작 값으로 재생 된 후에 반전 됩니다. 기본적으로이 속성은 `false` 입니다.

#### <a name="repeatbehavior"></a>RepeatBehavior

<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>속성은 타임 라인이 재생 되는 횟수를 지정 합니다. 기본적으로 타임 라인의 반복 횟수는 이며 `1.0` ,이는 한 번만 재생 되 고 전혀 반복 되지 않음을 의미 합니다.

이러한 속성 및 기타 속성에 대 한 자세한 내용은 [타이밍 동작 개요](timing-behaviors-overview.md)를 참조 하세요.

<a name="applyanimationstoproperty"></a>

## <a name="applying-an-animation-to-a-property"></a>속성에 애니메이션 적용

이전 섹션에서는 다양한 애니메이션 유형 및 타이밍 속성에 대해 설명합니다. 이 섹션에서는 애니메이션 효과를 주려는 속성에 애니메이션을 적용하는 방법을 보여 줍니다. <xref:System.Windows.Media.Animation.Storyboard>개체는 속성에 애니메이션을 적용 하는 한 가지 방법을 제공 합니다. 는 <xref:System.Windows.Media.Animation.Storyboard> 포함 된 애니메이션에 대 한 대상 정보를 제공 하는 *컨테이너 타임 라인* 입니다.

### <a name="targeting-objects-and-properties"></a>개체 및 속성을 대상으로 지정

<xref:System.Windows.Media.Animation.Storyboard>클래스는 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> 및 연결 된 속성을 제공 합니다 <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> . 애니메이션에 이러한 속성을 설정하여 적용할 애니메이션을 지정합니다. 그러나 애니메이션이 개체를 대상으로 지정하려면 먼저 해당 개체에 이름을 지정해야 합니다.

에 이름을 할당 하는 것은 개체에 이름을 할당 하는 것 <xref:System.Windows.FrameworkElement> 과 다릅니다 <xref:System.Windows.Freezable> . 대부분의 컨트롤 및 패널은 프레임워크 요소입니다. 그러나 브러시, 변환, 기 하 도형 등의 순수한 그래픽 개체 대부분은 Freezable 개체입니다. 형식이 또는 인지 확실 하지 않은 경우 <xref:System.Windows.FrameworkElement> <xref:System.Windows.Freezable> 해당 참조 설명서의 **상속 계층 구조** 섹션을 참조 하세요.

- <xref:System.Windows.FrameworkElement>애니메이션 대상을 만들려면 해당 속성을 설정 하 여 이름을 지정 <xref:System.Windows.FrameworkElement.Name%2A> 합니다. 또한 코드에서 메서드를 사용 하 여 <xref:System.Windows.FrameworkElement.RegisterName%2A> 요소 이름을 포함 하는 페이지에 요소 이름을 등록 해야 합니다.

- <xref:System.Windows.Freezable>에서 개체를 애니메이션 대상으로 만들려면 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [x:Name 지시문](../../../desktop-wpf/xaml-services/xname-directive.md) 을 사용 하 여 이름을 할당 합니다. 코드에서는 메서드를 사용 하 여 <xref:System.Windows.FrameworkElement.RegisterName%2A> 개체가 속한 페이지에 개체를 등록 하기만 하면 됩니다.

다음 섹션에서는 및 코드에서 요소 이름을 지정 하는 예제를 제공 합니다 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] . 이름 지정 및 대상 지정에 대 한 자세한 내용은 [Storyboard 개요](storyboards-overview.md)를 참조 하세요.

### <a name="applying-and-starting-storyboards"></a>Storyboard 적용 및 시작

에서 storyboard를 시작 하려면 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 이를와 연결 <xref:System.Windows.EventTrigger> 합니다. 는 <xref:System.Windows.EventTrigger> 지정 된 이벤트가 발생할 때 수행할 작업을 설명 하는 개체입니다. 이러한 작업 중 하나는 <xref:System.Windows.Media.Animation.BeginStoryboard> 스토리 보드를 시작 하는 데 사용 하는 작업이 될 수 있습니다. 이벤트 트리거는 애플리케이션이 특정 이벤트에 응답하는 방법을 지정할 수 있도록 하므로 개념적으로 이벤트 처리기와 비슷합니다. 이벤트 처리기와 달리 이벤트 트리거는에 자세히 설명 되어 있으며 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 다른 코드는 필요 하지 않습니다.

코드에서를 시작 하려면를 <xref:System.Windows.Media.Animation.Storyboard> 사용 <xref:System.Windows.EventTrigger> 하거나 <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> 클래스의 메서드를 사용할 수 있습니다 <xref:System.Windows.Media.Animation.Storyboard> .

<a name="controllingstoryboards"></a>

## <a name="interactively-control-a-storyboard"></a>대화식으로 Storyboard 제어

이전 예제에서는 이벤트가 발생할 때를 시작 하는 방법을 살펴보았습니다 <xref:System.Windows.Media.Animation.Storyboard> . 를 시작한 후에 대화형으로 제어할 수도 있습니다 <xref:System.Windows.Media.Animation.Storyboard> . 일시 중지, 다시 시작, 중지, 채우기 기간으로 이동, 검색, 제거 등의 작업을 수행할 수 있습니다 <xref:System.Windows.Media.Animation.Storyboard> . 을 대화형으로 제어 하는 방법을 보여 주는 예제 및 자세한 내용은 <xref:System.Windows.Media.Animation.Storyboard> [storyboard 개요](storyboards-overview.md)를 참조 하세요.

<a name="fillbehaviorsection"></a>

## <a name="what-happens-after-an-animation-ends"></a>애니메이션이 끝난 후에 발생하는 결과

<xref:System.Windows.Media.Animation.FillBehavior>속성은 타임 라인이 종료 될 때 동작 하는 방법을 지정 합니다. 기본적으로 타임 라인은 <xref:System.Windows.Media.Animation.ClockState.Filling> 종료 될 때 시작 됩니다. 최종 출력 값을 포함 하는 애니메이션입니다 <xref:System.Windows.Media.Animation.ClockState.Filling> .

<xref:System.Windows.Media.Animation.DoubleAnimation>이전 예제의는 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> 속성이로 설정 되어 있으므로 종료 되지 않습니다 <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A> . 다음 예제에서는 유사한 애니메이션을 사용하여 사각형에 애니메이션 효과를 줍니다. 이전 예제와는 달리 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> 이 애니메이션의 및 속성은 기본값으로 남아 있습니다. 따라서 애니메이션은 5초 넘게 1에서 0으로 진행된 후 중지합니다.

[!code-xaml[animation_ovws_snippet#FillBehaviorExampleRectangleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/FillBehaviorExample.xaml#fillbehaviorexamplerectangleinline)]

[!code-csharp[animation_ovws_procedural_snip#FillBehaviorExampleRectangleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/FillBehaviorExample.cs#fillbehaviorexamplerectangleinline)]
[!code-vb[animation_ovws_procedural_snip#FillBehaviorExampleRectangleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/fillbehaviorexample.vb#fillbehaviorexamplerectangleinline)]

는 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> 기본값에서 변경 되지 않았으므로 <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd> 애니메이션은 종료 될 때 최종 값인 0을 유지 합니다. 따라서 <xref:System.Windows.UIElement.Opacity%2A> 사각형의는 애니메이션이 종료 된 후 0으로 유지 됩니다. <xref:System.Windows.UIElement.Opacity%2A>사각형의를 다른 값으로 설정 하면 애니메이션이 여전히 속성에 영향을 주므로 코드는 아무런 영향을 미치지 않습니다 <xref:System.Windows.UIElement.Opacity%2A> .

코드에서 애니메이션 속성을 다시 제어 하는 한 가지 방법은 메서드를 사용 하 <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> 고 매개 변수에 null을 지정 하는 것입니다 <xref:System.Windows.Media.Animation.AnimationTimeline> . 자세한 내용 및 예제는 [Storyboard를 사용 하 여 애니메이션 효과를 적용 한 후 속성 설정](how-to-set-a-property-after-animating-it-with-a-storyboard.md)을 참조 하세요.

또는 애니메이션을 포함 하는 속성 값을 설정 해도 아무 효과가 없는 것 처럼 보이지만 <xref:System.Windows.Media.Animation.ClockState.Active> <xref:System.Windows.Media.Animation.ClockState.Filling> 속성 값이 변경 됩니다. 자세한 내용은 [애니메이션 및 타이밍 시스템 개요](animation-and-timing-system-overview.md)를 참조 하세요.

<a name="databindingAndAnimatingAnimationsSection"></a>

## <a name="data-binding-and-animating-animations"></a>데이터 바인딩 및 애니메이션 효과 적용

대부분의 애니메이션 속성은 데이터에 바인딩하거나 애니메이션 효과를 적용할 수 있습니다. 예를 들어의 속성에 애니메이션 효과를 적용할 수 있습니다 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> <xref:System.Windows.Media.Animation.DoubleAnimation> . 그러나 타이밍 시스템이 작동하는 방식 때문에 데이터 바인딩 또는 애니메이션 효과 주기가 다른 데이터 바인딩 또는 애니메이션 개체와 다르게 동작합니다. 해당 동작을 이해하기 위해 속성에 애니메이션을 적용하는 것이 어떤 의미를 갖는지 이해하면 도움이 됩니다.

사각형의에 애니메이션 효과를 주는 방법을 보여 주는 이전 섹션의 예제를 참조 하세요 <xref:System.Windows.UIElement.Opacity%2A> . 이전 예제의 사각형이 로드 되 면 해당 이벤트 트리거가를 적용 <xref:System.Windows.Media.Animation.Storyboard> 합니다. 타이밍 시스템은 및 해당 애니메이션의 복사본을 만듭니다 <xref:System.Windows.Media.Animation.Storyboard> . 이러한 복사본은 고정 (읽기 전용 됨) 및 <xref:System.Windows.Media.Animation.Clock> 개체에서 생성 됩니다. 이러한 클록은 대상 속성에 애니메이션 효과를 주는 실제 작업을 수행합니다.

타이밍 시스템은에 대 한 clock을 만들어 <xref:System.Windows.Media.Animation.DoubleAnimation> 의 및에서 지정 하는 개체 및 속성에 적용 합니다 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> <xref:System.Windows.Media.Animation.DoubleAnimation> . 이 경우 타이밍 시스템은 <xref:System.Windows.UIElement.Opacity%2A> "MyRectangle" 이라는 개체의 속성에 clock을 적용 합니다.

에 대 한 클록도 만들어지므로 <xref:System.Windows.Media.Animation.Storyboard> 속성에는 클록이 적용 되지 않습니다. 용도는에 대해 만들어진 클록 인 자식 clock을 제어 하는 것입니다 <xref:System.Windows.Media.Animation.DoubleAnimation> .

애니메이션에 데이터 바인딩 또는 애니메이션 변경 내용을 반영하려면 해당 클록이 다시 생성되어야 합니다. 클록은 자동으로 다시 생성되지 않습니다. 애니메이션에 변경 내용이 반영 되도록 하려면 또는 메서드를 사용 하 여 해당 스토리 보드를 다시 적용 <xref:System.Windows.Media.Animation.BeginStoryboard> <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> 합니다. 이러한 메서드 중 하나를 사용하면 애니메이션이 다시 시작됩니다. 코드에서 메서드를 사용 하 여 <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> storyboard를 이전 위치로 다시 이동할 수 있습니다.

데이터 바인딩된 애니메이션의 예제는 [키 스플라인 애니메이션 샘플](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/KeySplineAnimations)을 참조 하세요. 애니메이션 및 타이밍 시스템의 작동 방식에 대 한 자세한 내용은 [애니메이션 및 타이밍 시스템 개요](animation-and-timing-system-overview.md)를 참조 하세요.

<a name="otherWaysToAnimateSection"></a>

## <a name="other-ways-to-animate"></a>애니메이션 효과를 주는 다른 방법

이 개요의 예제에서는 Storyboard를 사용하여 애니메이션 효과를 주는 방법을 보여 줍니다. 코드를 사용하면 여러 가지 방법으로 애니메이션 효과를 줄 수 있습니다. 자세한 내용은 [속성 애니메이션 기술 개요](property-animation-techniques-overview.md)를 참조 하세요.

<a name="animation_samples"></a>

## <a name="animation-samples"></a>애니메이션 샘플

다음 샘플은 애플리케이션에 애니메이션을 추가하는 데 도움이 될 수 있습니다.

- [From, To 및 By 애니메이션 대상 값 샘플](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/TargetValues)

  다른 From/To/By 설정을 보여 줍니다.

- [애니메이션 타이밍 동작 샘플](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationTiming)

  애니메이션의 타이밍 동작을 제어할 수는 여러 가지 방법을 보여 줍니다. 또한 이 샘플은 애니메이션의 대상 값에 대해 데이터 바인딩을 수행하는 방법을 보여 줍니다.

<a name="related_topics"></a>

## <a name="related-topics"></a>관련 항목

|제목|설명|
|-----------|-----------------|
|[애니메이션 및 타이밍 시스템 개요](animation-and-timing-system-overview.md)|타이밍 시스템에서 <xref:System.Windows.Media.Animation.Timeline> 및 클래스를 사용 하 여 애니메이션을 만들 수 있는 방법을 설명 합니다 <xref:System.Windows.Media.Animation.Clock> .|
|[애니메이션에 대한 유용한 정보](animation-tips-and-tricks.md)|성능 같은 애니메이션 문제 해결에 도움이 되는 유용한 정보를 나열합니다.|
|[사용자 지정 애니메이션 개요](custom-animations-overview.md)|키 프레임, 애니메이션 클래스 또는 프레임당 콜백으로 애니메이션 시스템을 확장하는 방법을 설명합니다.|
|[From/To/By 애니메이션 개요](from-to-by-animations-overview.md)|두 값 사이를 전환하는 애니메이션을 만드는 방법을 설명합니다.|
|[키 프레임 애니메이션 개요](key-frame-animations-overview.md)|보간 방법을 제어하는 기능을 포함하여 여러 대상 값을 사용하여 애니메이션을 만드는 방법을 설명합니다.|
|[감속/가속 함수](easing-functions.md)|반송 같은 실질적인 동작을 얻기 위해 애니메이션에 수학 수식을 적용하는 방법을 설명합니다.|
|[경로 애니메이션 개요](path-animations-overview.md)|복잡한 경로를 따라 개체를 이동하거나 회전하는 방법을 설명합니다.|
|[속성 애니메이션 기술 개요](property-animation-techniques-overview.md)|Storyboard, 로컬 애니메이션, 시계 및 프레임당 애니메이션을 사용하는 속성 애니메이션에 대해 설명합니다.|
|[Storyboard 개요](storyboards-overview.md)|여러 개의 타임라인을 갖는 Storyboard를 사용하여 복잡한 애니메이션을 만드는 방법을 설명 합니다.|
|[타이밍 동작 개요](timing-behaviors-overview.md)|<xref:System.Windows.Media.Animation.Timeline>애니메이션에 사용 되는 형식 및 속성을 설명 합니다.|
|[타이밍 이벤트 개요](timing-events-overview.md)|<xref:System.Windows.Media.Animation.Timeline> <xref:System.Windows.Media.Animation.Clock> 시작, 일시 중지, 다시 시작, 건너뛰기 또는 중지와 같이 타임 라인의 지점에서 코드를 실행 하기 위해 및 개체에서 사용할 수 있는 이벤트에 대해 설명 합니다.|
|[방법 도움말 항목](animation-and-timing-how-to-topics.md)|애플리케이션에서 애니메이션 및 타임라인을 사용하기 위한 코드 예제가 포함되어 있습니다.|
|[Clock 방법 항목](clocks-how-to-topics.md)|응용 프로그램에서 개체를 사용 하기 위한 코드 예제가 포함 되어 있습니다 <xref:System.Windows.Media.Animation.Clock> .|
|[키 프레임 방법 항목](key-frame-animation-how-to-topics.md)|애플리케이션에서 키 프레임 애니메이션을 사용하기 위한 코드 예제가 포함되어 있습니다.|
|[경로 애니메이션 방법 항목](path-animation-how-to-topics.md)|애플리케이션에서 경로 애니메이션을 사용하기 위한 코드 예제가 포함되어 있습니다.|

<a name="reference"></a>

## <a name="reference"></a>참고

- <xref:System.Windows.Media.Animation.Timeline>

- <xref:System.Windows.Media.Animation.Storyboard>

- <xref:System.Windows.Media.Animation.BeginStoryboard>

- <xref:System.Windows.Media.Animation.Clock>
