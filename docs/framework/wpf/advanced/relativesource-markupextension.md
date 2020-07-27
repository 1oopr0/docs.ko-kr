---
title: RelativeSource MarkupExtension
description: 바인딩 태그 확장 내에서 RelativeSource 바인딩 소스의 속성을 지정 하거나 XAML에서 바인딩의 RelativeSource 속성을 설정할 때 지정 합니다.
ms.date: 03/30/2017
f1_keywords:
- RelativeSource
helpviewer_keywords:
- RelativeSource markup extensions [WPF]
- XAML [WPF], RelativeSource markup extension
ms.assetid: 26be4721-49b5-4717-a92e-7d54ad0d3a81
ms.openlocfilehash: 2da702d23413651a85b45404e088f6708546cc25
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165941"
---
# <a name="relativesource-markupextension"></a>RelativeSource MarkupExtension

바인딩 <xref:System.Windows.Data.RelativeSource> [태그 확장](binding-markup-extension.md)내에서 사용 되거나 <xref:System.Windows.Data.Binding.RelativeSource%2A> <xref:System.Windows.Data.Binding> XAML로 설정 된 요소의 속성을 설정할 때 사용 되는 바인딩 소스의 속성을 지정 합니다.

## <a name="xaml-attribute-usage"></a>XAML 특성 사용

```xml
<Binding RelativeSource="{RelativeSource modeEnumValue}" ... />
```

## <a name="xaml-attribute-usage-nested-within-binding-extension"></a>XAML 특성 사용(Binding 확장 내에 중첩)

```xml
<object property="{Binding RelativeSource={RelativeSource modeEnumValue} ...}" ... />
```

## <a name="xaml-object-element-usage"></a>XAML 개체 요소 사용

```xml
<Binding>
  <Binding.RelativeSource>
    <RelativeSource Mode="modeEnumValue"/>
  </Binding.RelativeSource>
</Binding>
```

또는

```xml
<Binding>
  <Binding.RelativeSource>
    <RelativeSource
      Mode="FindAncestor"
      AncestorType="{x:Type typeName}"
      AncestorLevel="intLevel"
    />
  </Binding.RelativeSource>
</Binding>
```

## <a name="xaml-values"></a>XAML 값

|||
|-|-|
|`modeEnumValue`|다음 중 하나<br /><br /> -문자열 토큰은 `Self` <xref:System.Windows.Data.RelativeSource> <xref:System.Windows.Data.RelativeSource.Mode%2A> 속성을로 설정 하 여 생성 된에 해당 합니다 <xref:System.Windows.Data.RelativeSourceMode.Self> .<br />-문자열 토큰은 `TemplatedParent` <xref:System.Windows.Data.RelativeSource> <xref:System.Windows.Data.RelativeSource.Mode%2A> 속성을로 설정 하 여 생성 된에 해당 합니다 <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent> .<br />-문자열 토큰은 `PreviousData` <xref:System.Windows.Data.RelativeSource> <xref:System.Windows.Data.RelativeSource.Mode%2A> 속성을로 설정 하 여 생성 된에 해당 합니다 <xref:System.Windows.Data.RelativeSourceMode.PreviousData> .<br />-모드에 대 한 자세한 내용은 아래를 참조 하세요 `FindAncestor` .|
|`FindAncestor`|토큰 문자열 `FindAncestor`입니다. 이 토큰을 사용하면 `RelativeSource`가 상위 항목 형식과 상위 수준(선택 사항)을 지정하는 모드로 들어갑니다. 이것은 <xref:System.Windows.Data.RelativeSource> 속성을 <xref:System.Windows.Data.RelativeSource.Mode%2A>로 설정하여 생성한 <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>에 해당합니다.|
|`typeName`|`FindAncestor` 모드에 필수적인 요소입니다. <xref:System.Windows.Data.RelativeSource.AncestorType%2A> 속성을 채우는 형식의 이름입니다.|
|`intLevel`|`FindAncestor` 모드에서는 선택적으로 사용할 수 있습니다. 논리 트리에서 부모 방향 쪽으로 계산되는 상위 수준입니다.|

## <a name="remarks"></a>설명

`{RelativeSource TemplatedParent}`바인딩 사용은 컨트롤의 UI와 컨트롤의 논리를 구분 하는 더 큰 개념을 해결 하는 주요 기술입니다. 이를 통해 템플릿 정의 내에서 템플릿 기반 부모(템플릿이 적용되는 런타임 개체 인스턴스)로 바인딩할 수 있습니다. 이 경우 [TemplateBinding 태그 확장](templatebinding-markup-extension.md) 은 실제로 다음 바인딩 식에 대 한 축약형 `{Binding RelativeSource={RelativeSource TemplatedParent}}` 입니다. `TemplateBinding`또는 사용 `{RelativeSource TemplatedParent}` 은 모두 템플릿을 정의 하는 XAML 내 에서만 관련이 있습니다. 자세한 내용은 [TemplateBinding 태그 확장](templatebinding-markup-extension.md)을 참조 하세요.

`{RelativeSource FindAncestor}`는 컨트롤이 항상 특정 상위 형식의 시각적 트리에 있을 것으로 예상 되는 경우 컨트롤 템플릿 또는 예측 가능한 자체 포함 UI 컴포지션에 사용 됩니다. 예를 들어, 항목 컨트롤의 항목은 `FindAncestor`를 사용하여 항목 컨트롤 부모 상위 항목의 속성에 바인딩할 수 있습니다. 또는 템플릿에 컨트롤 컴퍼지션의 일부인 요소에서 `FindAncestor` 바인딩을 동일한 컴퍼지션 구조에서 상위 요소로 사용할 수 있습니다.

XAML 구문 섹션에 표시된 `FindAncestor` 모드에 대한 개체 요소 구문에서 `FindAncestor` 모드의 경우에는 특히 두 번째 개체 요소 구문이 사용됩니다. `FindAncestor` 모드에는 <xref:System.Windows.Data.RelativeSource.AncestorType%2A> 값이 필요합니다. <xref:System.Windows.Data.RelativeSource.AncestorType%2A>찾을 상위 항목의 형식에 대 한 [X:Type 태그 확장](../../../desktop-wpf/xaml-services/xtype-markup-extension.md) 참조를 사용 하 여를 특성으로 설정 해야 합니다. 바인딩 요청이 실시간으로 처리될 때 <xref:System.Windows.Data.RelativeSource.AncestorType%2A> 값이 사용됩니다.

`FindAncestor` 모드의 경우 선택적 속성인 <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A>을 사용하면 요소 트리에 같은 형식의 상위 항목이 둘 이상 있을 때 상위 항목을 쉽게 구분할 수 있습니다.

`FindAncestor` 모드를 사용하는 방법에 대한 자세한 내용은 <xref:System.Windows.Data.RelativeSource>를 참조하십시오.

`{RelativeSource Self}`는 인스턴스의 한 속성이 같은 인스턴스의 다른 속성 값에 종속 되어야 하 고 이러한 두 속성 간에 일반 종속성 속성 관계 (예: 강제 변환)가 이미 존재 하는 시나리오에 유용 합니다. 값이 동일 하 게 (그리고 동일 하 게 형식화 됨) 개체에 두 속성이 존재 하지는 않지만 `Converter` ,를 포함 하는 바인딩에 매개 변수를 적용 하 `{RelativeSource Self}` 고 변환기를 사용 하 여 소스와 대상 형식 사이를 변환할 수도 있습니다. 의 다른 시나리오 `{RelativeSource Self}` 는의 일부입니다 <xref:System.Windows.MultiDataTrigger> .

예를 들어, 다음 XAML은 <xref:System.Windows.Shapes.Rectangle>에 어떤 값이 입력되더라도 <xref:System.Windows.FrameworkElement.Width%2A>은 항상 사각형이 되도록 <xref:System.Windows.Shapes.Rectangle> 요소를 정의합니다. `<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`

`{RelativeSource PreviousData}`는 데이터 템플릿 또는 바인딩에서 컬렉션을 데이터 원본으로 사용 하는 경우에 유용 합니다. `{RelativeSource PreviousData}`를 사용 하 여 컬렉션의 인접 데이터 항목 간 관계를 강조 표시할 수 있습니다. 관련된 기술은 데이터 소스에 있는 현재 항목과 이전 항목 사이에 <xref:System.Windows.Data.MultiBinding>을 구축하고 해당 바인딩에서 변환기를 사용하여 두 항목 사이의 차이점과 해당 속성을 확인하는 것입니다.

다음 예제에서 항목 템플릿의 첫 번째 <xref:System.Windows.Controls.TextBlock>은 현재 번호를 표시합니다. 두 번째 <xref:System.Windows.Controls.TextBlock> 바인딩은 <xref:System.Windows.Data.MultiBinding> 명목상에 <xref:System.Windows.Data.Binding> 현재 레코드와를 사용 하 여 의도적으로 이전 데이터 레코드를 사용 하는 바인딩의 두 가지 구성 요소를 포함 하는 `{RelativeSource PreviousData}` 입니다. 그런 다음, <xref:System.Windows.Data.MultiBinding>의 변환기가 차이를 계산하고 이를 바인딩으로 반환합니다.

```xml
<ListBox Name="fibolist">
    <ListBox.ItemTemplate>
        <DataTemplate>
            <StackPanel Orientation="Horizontal">
            <TextBlock Text="{Binding}"/>
            <TextBlock>, difference = </TextBlock>
                <TextBlock>
                    <TextBlock.Text>
                        <MultiBinding Converter="{StaticResource DiffConverter}">
                            <Binding/>
                            <Binding RelativeSource="{RelativeSource PreviousData}"/>
                        </MultiBinding>
                    </TextBlock.Text>
                </TextBlock>
            </StackPanel>
        </DataTemplate>
    </ListBox.ItemTemplate>
</ListBox>
```

데이터 바인딩에 대 한 개념 설명은 여기에서 다루지 않습니다. [데이터 바인딩 개요](../../../desktop-wpf/data/data-binding-overview.md)를 참조 하세요.

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]XAML 프로세서 구현에서이 태그 확장에 대 한 처리는 클래스에 의해 정의 됩니다 <xref:System.Windows.Data.RelativeSource> .

`RelativeSource`은 태그 확장입니다. 태그 확장은 특성 값을 리터럴 값 또는 처리기 이름이 아닌 다른 값이 되도록 이스케이프해야 하는 요구 사항이 있는 경우 일반적으로 구현되며 이러한 요구 사항은 특정 형식 또는 속성에 형식 변환기를 배치하는 것보다 더 포괄적입니다. XAML의 모든 태그 확장은 `{` `}` 특성 구문에서 및 문자를 사용 합니다 .이는 xaml 프로세서에서 태그 확장이 특성을 처리 해야 함을 인식 하는 데 사용 되는 규칙입니다. 자세한 내용은 [태그 확장 및 WPF XAML](markup-extensions-and-wpf-xaml.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

- <xref:System.Windows.Data.Binding>
- [스타일 지정 및 템플릿](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [XAML 개요(WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [태그 확장명 및 WPF XAML](markup-extensions-and-wpf-xaml.md)
- [데이터 바인딩 개요](../../../desktop-wpf/data/data-binding-overview.md)
- [바인딩 선언 개요](../data/binding-declarations-overview.md)
- [x:Type 태그 확장](../../../desktop-wpf/xaml-services/xtype-markup-extension.md)
