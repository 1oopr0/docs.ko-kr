---
title: x:Name 지시문
ms.date: 03/30/2017
f1_keywords:
- x:Name
- xName
- Name
helpviewer_keywords:
- x:Name attribute [XAML Services]
- XAML [XAML Services], x:Name attribute
- Name attribute in XAML [XAML Services]
ms.assetid: b7e61222-e8cf-48d2-acd0-6df3b7685d48
ms.openlocfilehash: ddaa35b18d1c632fc49b18dabf0d992dc1c78fcc
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90549485"
---
# <a name="xname-directive"></a>x:Name 지시문

Xaml 이름 범위에서 XAML로 정의 된 요소를 고유 하 게 식별 합니다. 프레임 워크는 런타임에 Api를 제공 하거나 XAML로 생성 된 개체 그래프에 액세스 하는 동작을 구현할 때 XAML 이름 범위와 해당 고유성 모델을 인스턴스화된 개체에 적용할 수 있습니다.

## <a name="xaml-attribute-usage"></a>XAML 특성 사용

```xaml
<object x:Name="XAMLNameValue".../>
```

## <a name="xaml-values"></a>XAML 값

|||
|-|-|
|`XAMLNameValue`|[XamlName 문법](xamlname-grammar.md)의 제한 사항을 준수 하는 문자열입니다.|

## <a name="remarks"></a>설명

`x:Name`가 프레임 워크의 지원 프로그래밍 모델에 적용 된 후에는 이름이 개체 참조 또는 생성자에서 반환 된 인스턴스를 보유 하는 변수와 같습니다.

지시문 사용의 값은 `x:Name` xaml 이름 범위 내에서 고유 해야 합니다. 기본적으로 .NET XAML 서비스 API에서 사용 하는 경우 기본 XAML 이름 범위는 단일 XAML 프로덕션의 XAML 루트 요소에 정의 되 고 해당 XAML 프로덕션에 포함 된 요소를 포함 합니다. 단일 XAML 프로덕션 내에서 발생할 수 있는 추가 불연속 XAML 이름 범위는 특정 시나리오를 해결 하기 위해 프레임 워크에서 정의 될 수 있습니다. 예를 들어 WPF에서 새 XAML 이름 범위는 해당 XAML 프로덕션에도 정의 된 모든 템플릿에서 정의 되 고 생성 됩니다. XAML 이름 범위에 대 한 자세한 내용은 (WPF 용으로 작성 되었지만 많은 XAML 이름 범위 개념과 관련 됨) [WPF XAML 이름 범위](/dotnet/desktop/wpf/advanced/wpf-xaml-namescopes)를 참조 하세요.

일반적으로를 `x:Name` 사용 하는 경우에는를 적용 하면 안 됩니다 `x:Key` . 특정 기존 프레임 워크에의 한 XAML 구현은 및 간의 대체 개념을 도입 했지만이 방법은 `x:Key` `x:Name` 권장 되지 않습니다. .NET XAML 서비스는 또는와 같은 이름/키 정보를 처리할 때 이러한 대체 개념을 지원 하지 않습니다 <xref:System.Windows.Markup.INameScope> <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute> .

Permittance에 대 한 규칙 `x:Name` 및 이름 고유성 적용은 특정 구현 프레임 워크에 의해 정의 될 수 있습니다. 그러나 .NET XAML 서비스에서 사용할 수 있도록 하려면 XAML 이름 범위 고유성의 프레임 워크 정의가 <xref:System.Windows.Markup.INameScope> 이 설명서의 정보 정의와 일치 해야 하며, 정보가 적용 되는 위치와 동일한 규칙을 사용 해야 합니다. 예를 들어 [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] 구현은 다양 한 태그 요소를 <xref:System.Windows.NameScope> 리소스 사전, 페이지 수준 XAML, 템플릿 및 기타 지연 된 콘텐츠에서 만든 논리 트리와 같은 별도의 범위로 나눈 다음 이러한 각 xaml 이름 범위 내에서 xaml 이름 고유성을 적용 합니다.

.NET XAML 서비스 XAML 개체 작성기를 사용 하는 사용자 지정 형식의 경우 형식에 매핑되는 속성을 `x:Name` 설정 하거나 변경할 수 있습니다. 형식 정의 코드에서와 매핑할 속성의 이름을 참조 하 여이 동작을 정의 <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> 합니다.  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> 는 형식 수준 특성입니다.

Using.NET XAML 서비스, XAML 이름 범위 지원에 대 한 지원 논리는 인터페이스를 구현 하 여 프레임 워크 중립적인 방식으로 정의할 수 있습니다 <xref:System.Windows.Markup.INameScope> .

## <a name="wpf-usage-notes"></a>WPF 사용 정보

[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]XAML, 부분 클래스 및 코드를 사용 하는 응용 프로그램에 대 한 표준 빌드 구성에서 지정 된은 `x:Name` 태그 컴파일 빌드 작업에서를 처리할 때 기본 코드에서 생성 되는 필드 이름이 되 [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] 고, 해당 필드에는 개체에 대 한 참조가 포함 됩니다. 기본적으로 생성 된 필드는 내부 필드입니다. [X:FieldModifier 특성](xfieldmodifier-directive.md)을 지정 하 여 필드 액세스를 변경할 수 있습니다. WPF 및 Silverlight에서 시퀀스는 태그 컴파일에 의해 partial 클래스의 필드 이름을 정의 하 고 이름을 변경 하지만 처음에는 값이 비어 있습니다. 그런 다음 클래스 생성자 내에서 이라는 생성 된 메서드를 `InitializeComponent` 호출 합니다. `InitializeComponent``FindName` `x:Name` 부분 클래스의 XAML 정의 부분에 있는 각 값을 입력 문자열로 사용 하는 호출로 구성 됩니다. 그런 다음 반환 값은 이름이 같은 필드 참조에 할당 되어 XAML 구문 분석에서 만든 개체를 사용 하 여 필드 값을 채웁니다. 를 실행 하면 `InitializeComponent` `x:Name` `FindName` XAML 정의 개체에 대 한 참조가 필요한 경우를 명시적으로 호출 하지 않고/필드 이름을 직접 사용 하 여 런타임 개체 그래프를 참조할 수 있습니다.

Microsoft Visual Basic 대상을 사용 하 고 빌드 작업이 포함 된 XAML 파일을 포함 하는 WPF 응용 프로그램의 경우 `Page` `WithEvents` `x:Name` `Handles` 이벤트 처리기 대리자에 대 한 구문을 지원 하기 위해를 포함 하는 모든 요소에 키워드를 추가 하는 별도의 참조 속성이 생성 됩니다. 이 속성은 항상 public입니다. 자세한 내용은 [Visual Basic 및 WPF 이벤트 처리](/dotnet/desktop/wpf/advanced/visual-basic-and-wpf-event-handling)를 참조하세요.

`x:Name` 는 빌드 작업 (예: 리소스 사전의 느슨한 XAML)에서 페이지가 태그 컴파일되지 않는 경우를 포함 하 여, 로드 시 WPF XAML 프로세서에서 이름을 XAML 이름 범위에 등록 하는 데 사용 됩니다. 이 동작의 한 가지 이유는가 바인딩에 필요할 수 있기 때문입니다 `x:Name` <xref:System.Windows.Data.Binding.ElementName%2A> . 자세한 내용은 [데이터 바인딩 개요](../data/data-binding-overview.md)를 참조 하세요.

앞에서 설명한 것 처럼를 `x:Name` `Name` 사용 하는 상황에서는 또는를 적용 하면 안 됩니다 `x:Key` . 에는 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.ResourceDictionary> 자체를 XAML 이름 범위로 정의 하지만 <xref:System.Windows.Markup.INameScope> 이 동작을 적용 하는 방법으로 Api에 대해 구현 되지 않음 또는 null 값을 반환 하는 특별 한 동작이 있습니다. WPF XAML 파서가 `Name` 또는 xaml 정의에서 발생 하는 경우에는 `x:Name` <xref:System.Windows.ResourceDictionary> 이름이 xaml 이름 범위에 추가 되지 않습니다. 모든 XAML 이름 범위에서 해당 이름을 찾으려고 했지만 `FindName` 메서드에서 올바른 결과를 반환 하지 않습니다.

### <a name="xname-and-name"></a>x:Name 및 이름

대부분의 WPF 응용 프로그램 시나리오에서는 등의 `x:Name` `Name` 중요 한 기본 클래스에 대 한 기본 XAML 네임 스페이스에 지정 된 종속성 속성이 이와 <xref:System.Windows.FrameworkElement> 동일한 용도를 충족 하기 때문에 특성을 사용 하지 않을 수 있습니다 <xref:System.Windows.FrameworkContentElement> . 프레임 워크 수준에서 속성이 없는 요소에 대 한 코드 액세스가 중요 한 몇 가지 일반적인 XAML 및 WPF 시나리오도 있습니다 `Name` . 예를 들어 특정 애니메이션 및 storyboard 지원 클래스는 속성을 지원 하지 `Name` 않지만 애니메이션을 제어 하기 위해 코드에서 참조 해야 하는 경우가 많습니다. `x:Name`나중에 코드에서 참조 하려는 경우 XAML에서 만든 타임 라인 및 변환에 대 한 특성으로를 지정 해야 합니다.

를 <xref:System.Windows.FrameworkElement.Name%2A> 클래스의 속성으로 사용할 수 있는 경우 <xref:System.Windows.FrameworkElement.Name%2A> 및를 `x:Name` 특성으로 사용할 수 있지만 둘 다 동일한 요소에 지정 된 경우 구문 분석 예외가 발생 합니다. XAML이 태그 컴파일 인 경우 태그 컴파일 시 예외가 발생 합니다. 그렇지 않으면 로드 시 발생 합니다.

<xref:System.Windows.FrameworkElement.Name%2A> 는 XAML 특성 구문을 사용 하 여 설정할 수 있고를 사용 하는 코드에서 설정할 수 있습니다 <xref:System.Windows.DependencyObject.SetValue%2A> . 그러나 <xref:System.Windows.FrameworkElement.Name%2A> xaml이 이미 로드 된 대부분의 경우 코드에서 속성을 설정 해도 xaml 이름 범위 내에 대표 필드 참조가 생성 되지 않습니다. 코드에서를 설정 하는 대신 <xref:System.Windows.FrameworkElement.Name%2A> <xref:System.Windows.NameScope> 적절 한 이름 범위에 대해 코드의 메서드를 사용 합니다.

<xref:System.Windows.FrameworkElement.Name%2A> 는 내부 텍스트와 함께 속성 요소 구문을 사용 하 여 설정할 수도 있지만 일반적이 지 않습니다. 이와 달리는 `x:Name` XAML 속성 요소 구문이 나를 사용 하는 코드에서 설정할 수 없습니다 <xref:System.Windows.DependencyObject.SetValue%2A> . 지시문 이므로 개체에 대 한 특성 구문만 사용 하 여 설정할 수 있습니다.

## <a name="silverlight-usage-notes"></a>Silverlight 사용 메모

`x:Name` Silverlight의는 별도로 설명 됩니다. 자세한 내용은 [XAML 네임 스페이스 (x:)를 참조 하세요. 언어 기능 (Silverlight)](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95)).

## <a name="see-also"></a>참조

- <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>
- <xref:System.Windows.FrameworkContentElement.Name%2A?displayProperty=nameWithType>
- [WPF의 트리](/dotnet/desktop/wpf/advanced/trees-in-wpf)
