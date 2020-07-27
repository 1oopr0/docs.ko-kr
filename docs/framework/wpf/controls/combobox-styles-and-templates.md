---
title: ComboBox 스타일 및 템플릿
description: Windows Presentation Foundation ComboBox 컨트롤의 스타일 및 템플릿에 대해 알아봅니다. ControlTemplate를 수정 하 여 컨트롤에 고유한 모양을 제공 합니다.
ms.date: 03/30/2017
helpviewer_keywords:
- ComboBox [WPF], styles and templates
- states [WPF], ComboBox
- ControlTemplate [WPF], ComboBox
- styles [WPF], ComboBox
- templates [WPF], ComboBox
- parts [WPF], ComboBox
ms.assetid: b0662fa1-16d7-4320-b26b-c1804e565a44
ms.openlocfilehash: 5e929bafeaf849b4b5682a17ca51cb0aab963613
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165910"
---
# <a name="combobox-styles-and-templates"></a>ComboBox 스타일 및 템플릿
이 항목에서는 컨트롤의 스타일 및 템플릿에 대해 설명 합니다 <xref:System.Windows.Controls.ComboBox> . 기본값을 수정할 수 있습니다 <xref:System.Windows.Controls.ControlTemplate> 고유한 모양을 제어할 수 있습니다. 자세한 내용은 [컨트롤에 대 한 템플릿 만들기](../../../desktop-wpf/themes/how-to-create-apply-template.md)를 참조 하세요.  
  
## <a name="combobox-parts"></a>ComboBox 파트  
 다음 표에서는 컨트롤의 명명 된 파트를 나열 합니다 <xref:System.Windows.Controls.ComboBox> .  
  
|부분|Type|Description|  
|-|-|-|  
|PART_EditableTextBox|<xref:System.Windows.Controls.TextBox>|의 텍스트를 포함 합니다 <xref:System.Windows.Controls.ComboBox> .|  
|PART_Popup|<xref:System.Windows.Controls.Primitives.Popup>|콤보 상자의 항목이 들어 있는 드롭다운입니다.|  
  
 에 대해를 만들 때 <xref:System.Windows.Controls.ControlTemplate> 템플릿에는 내에 <xref:System.Windows.Controls.ComboBox> 이 포함 될 수 있습니다 <xref:System.Windows.Controls.ItemsPresenter> <xref:System.Windows.Controls.ScrollViewer> . 는의 <xref:System.Windows.Controls.ItemsPresenter> 각 항목을 표시 하 <xref:System.Windows.Controls.ComboBox> 고,는 <xref:System.Windows.Controls.ScrollViewer> 컨트롤 내에서 스크롤할 수 있도록 합니다.  <xref:System.Windows.Controls.ItemsPresenter>이의 직계 자식이 아닌 경우 <xref:System.Windows.Controls.ScrollViewer> 이름을 지정 해야 합니다 <xref:System.Windows.Controls.ItemsPresenter> `ItemsPresenter` .  
  
## <a name="combobox-states"></a>ComboBox 상태  
 다음 표에서는 컨트롤의 상태를 보여 줍니다 <xref:System.Windows.Controls.ComboBox> .  
  
|VisualState 이름|VisualStateGroup 이름|설명|  
|-|-|-|  
|보통|CommonStates|기본 상태입니다.|  
|사용 안 함|CommonStates|컨트롤이 비활성화되었습니다.|  
|MouseOver|CommonStates|마우스 포인터가 <xref:System.Windows.Controls.ComboBox> 컨트롤 위에 있습니다.|  
|포커스 있음|FocusStates|컨트롤에 포커스가 있습니다.|  
|포커스 없음|FocusStates|컨트롤에 포커스가 없습니다.|  
|FocusedDropDown|FocusStates|의 드롭다운에 <xref:System.Windows.Controls.ComboBox> 포커스가 있습니다.|  
|Valid|ValidationStates|컨트롤은 클래스를 사용 하 <xref:System.Windows.Controls.Validation> 고 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 연결 된 속성은 `false` 입니다.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>연결 된 속성이이 `true` 고 컨트롤에 포커스가 있습니다.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>연결 된 속성이이 `true` 고 컨트롤에 포커스가 없는 경우|  
|Editable|EditStates|<xref:System.Windows.Controls.ComboBox.IsEditable%2A> 속성은 `true`입니다.|  
|편집할 수 없는|EditStates|<xref:System.Windows.Controls.ComboBox.IsEditable%2A> 속성은 `false`입니다.|  
  
## <a name="comboboxitem-parts"></a>ComboBoxItem 파트  
 <xref:System.Windows.Controls.ComboBoxItem>컨트롤에 명명 된 파트가 없습니다.  
  
## <a name="comboboxitem-states"></a>ComboBoxItem 상태  
 다음 표에서는 컨트롤의 상태를 보여 줍니다 <xref:System.Windows.Controls.ComboBoxItem> .  
  
|VisualState 이름|VisualStateGroup 이름|설명|  
|-|-|-|  
|보통|CommonStates|기본 상태입니다.|  
|사용 안 함|CommonStates|컨트롤이 비활성화되었습니다.|  
|MouseOver|CommonStates|마우스 포인터가 <xref:System.Windows.Controls.ComboBoxItem> 컨트롤 위에 있습니다.|  
|포커스 있음|FocusStates|컨트롤에 포커스가 있습니다.|  
|포커스 없음|FocusStates|컨트롤에 포커스가 없습니다.|  
|선택|SelectionStates|항목이 현재 선택 되어 있습니다.|  
|선택 취소|SelectionStates|항목이 선택되어 있지 않습니다.|  
|SelectedUnfocused|SelectionStates|항목이 선택되었지만 항목에 포커스가 없습니다.|  
|Valid|ValidationStates|컨트롤은 클래스를 사용 하 <xref:System.Windows.Controls.Validation> 고 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 연결 된 속성은 `false` 입니다.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>연결 된 속성이이 `true` 고 컨트롤에 포커스가 있습니다.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>연결 된 속성이이 `true` 고 컨트롤에 포커스가 없는 경우|  
  
## <a name="combobox-controltemplate-example"></a>ComboBox ControlTemplate 예제  
 다음 예제에서는 <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.ComboBox> 컨트롤 및 관련 형식에 대 한을 정의 하는 방법을 보여 줍니다.  
  
 [!code-xaml[ControlTemplateExamples#ComboBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#combobox)]  
  
 앞의 예제에서는 다음 리소스를 하나 이상 사용합니다.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 전체 샘플을 보려면 [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)(ControlTemplate으로 스타일 지정 샘플)을 참조하세요.  
  
## <a name="see-also"></a>참고 항목

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Control 스타일 및 템플릿](control-styles-and-templates.md)
- [컨트롤 사용자 지정](control-customization.md)
- [스타일 지정 및 템플릿](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [컨트롤의 템플릿 만들기](../../../desktop-wpf/themes/how-to-create-apply-template.md)
