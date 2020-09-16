---
title: x:Type 태그 확장
ms.date: 03/30/2017
f1_keywords:
- x:TypeExtension
- Type
- x:Type
- xType
- TypeExtension
helpviewer_keywords:
- x:Type markup extension [XAML Services]
- XAML [XAML Services], x:Type markup extension
- XAML [XAML Services], TargetType attribute
- TargetType attribute [XAML Services]
- Type markup extension in XAML [XAML Services]
ms.assetid: e0e0ce6f-e873-49c7-8ad7-8b840eb353ec
ms.openlocfilehash: 00e6684f6ad1eb8d96f72f49bd5e0d211c8166c3
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559072"
---
# <a name="xtype-markup-extension"></a>x:Type 태그 확장

<xref:System.Type>지정 된 XAML 형식에 대 한 기본 형식인 CLR 개체를 제공 합니다.

## <a name="xaml-attribute-usage"></a>XAML 특성 사용

```xaml
<object property="{x:Type prefix:typeNameValue}" .../>
```

## <a name="xaml-object-element-usage"></a>XAML 개체 요소 사용

```xaml
<x:Type TypeName="prefix:typeNameValue"/>
```

## <a name="xaml-values"></a>XAML 값

|||
|-|-|
|`prefix`|선택 사항입니다. 기본이 아닌 XAML 네임 스페이스를 매핑하는 접두사입니다. 접두사는 반드시 지정 해야 하는 경우가 많습니다. 설명 부분을 참조하세요.|
|`typeNameValue`|필수 요소. 현재 기본 XAML 네임 스페이스에 대해 확인할 수 있는 형식 이름입니다. 또는가 제공 된 경우 지정 된 매핑된 접두사입니다 `prefix` .|

## <a name="remarks"></a>설명

`x:Type`태그 확장은 `typeof()` c #의 연산자 또는 Microsoft Visual Basic의 연산자와 유사한 함수를 포함 `GetType` 합니다.

`x:Type`태그 확장은 형식을 사용 하는 속성에 대 한 문자열 변환 동작을 제공 합니다 <xref:System.Type> . 입력이 XAML 형식입니다. 입력 XAML 형식과 출력 CLR의 관계는 <xref:System.Type> <xref:System.Type> <xref:System.Xaml.XamlType.UnderlyingType%2A> <xref:System.Xaml.XamlType> <xref:System.Xaml.XamlType> xaml 스키마 컨텍스트 및 <xref:System.Windows.Markup.IXamlTypeResolver> 컨텍스트가 제공 하는 서비스를 기반으로 하 여 필요한를 조회 한 후 출력이 입력의입니다.

.NET XAML 서비스에서이 태그 확장에 대 한 처리는 클래스에 의해 정의 됩니다 <xref:System.Windows.Markup.TypeExtension> .

특정 프레임 워크 구현에서 값으로 사용 되는 일부 속성은 <xref:System.Type> 직접 형식의 이름을 사용할 수 있습니다 (형식의 문자열 값 `Name` ). 그러나이 동작을 구현 하는 것은 복잡 한 시나리오입니다. 예제는 다음에 나오는 "WPF 사용 정보" 섹션을 참조 하세요.

특성 구문은 이러한 태그 확장에 가장 많이 사용되는 구문입니다. `x:Type` 식별자 문자열 다음에 나오는 문자열 토큰은 기본 <xref:System.Windows.Markup.TypeExtension.TypeName%2A> 확장명 클래스의 <xref:System.Windows.Markup.TypeExtension> 값으로 할당됩니다. CLR 형식을 기반으로 하는 .NET XAML 서비스에 대 한 기본 XAML 스키마 컨텍스트 아래에서이 특성의 값은 <xref:System.Reflection.MemberInfo.Name%2A> 원하는 형식의 이거나 <xref:System.Reflection.MemberInfo.Name%2A> 기본이 아닌 XAML 네임 스페이스 매핑의 접두사 앞에 포함 된를 포함 합니다.

`x:Type`태그 확장은 개체 요소 구문에서 사용할 수 있습니다. 이 경우 <xref:System.Windows.Markup.TypeExtension.TypeName%2A> 확장을 제대로 초기화 하려면 속성 값을 지정 해야 합니다.

`x:Type`태그 확장을 자세한 정보 특성으로 사용할 수도 있지만이 사용은 일반적이 지 않습니다.`<object property="{x:Type TypeName=typeNameValue}" .../>`

## <a name="wpf-usage-notes"></a>WPF 사용 정보

### <a name="default-xaml-namespace-and-type-mapping"></a>기본 XAML 네임 스페이스 및 형식 매핑

WPF 프로그래밍에 대 한 기본 XAML 네임 스페이스에는 일반적인 XAML 시나리오에 필요한 대부분의 XAML 형식이 포함 되어 있습니다. 따라서 XAML 형식 값을 참조할 때 접두사를 사용 하지 않는 경우가 종종 있습니다. 사용자 지정 어셈블리의 형식 또는 WPF 어셈블리에 있지만 기본 XAML 네임 스페이스에 매핑되지 않은 CLR 네임 스페이스의 형식을 참조 하는 경우에는 접두사를 매핑해야 할 수 있습니다. 접두사, XAML 네임 스페이스 및 매핑 CLR 네임 스페이스에 대 한 자세한 내용은 [WPF xaml을 위한 Xaml 네임 스페이스 및 네임 스페이스 매핑](/dotnet/desktop/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml)을 참조 하세요.

### <a name="type-properties-that-support-typename-as-string"></a>Typename을 문자열로 지 원하는 형식 속성

WPF는 <xref:System.Type> 태그 확장 사용을 요구 하지 않고 형식의 일부 속성 값을 지정할 수 있는 기술을 지원 `x:Type` 합니다. 대신 형식의 이름을 지정 하는 문자열로 값을 지정할 수 있습니다. 이에 대 한 예는 <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> 및 <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType> 입니다. 형식 변환기 또는 태그 확장을 통해서는이 동작에 대 한 지원을 제공 하지 않습니다. 대신이는를 통해 구현 되는 지연 동작입니다 <xref:System.Windows.FrameworkElementFactory> .

Silverlight는 비슷한 규칙을 지원 합니다. 실제로 Silverlight는 `{x:Type}` XAML 언어 지원을 지원 하지 않으며 `{x:Type}` WPF-Silverlight XAML 마이그레이션을 지원 하기 위한 몇 가지 상황 외의 사용을 허용 하지 않습니다. 따라서 typename으로 문자열 동작이 모든 Silverlight 네이티브 속성 계산에 기본 제공 됩니다. 여기서는 <xref:System.Type> 값입니다.

## <a name="xaml-2009"></a>XAML 2009

XAML 2009은 제네릭 형식에 대 한 추가 지원을 제공 하 고, 및의 기능 동작 `x:TypeArguments` `x:Type` 을 수정 하 여이 지원을 제공 합니다.

- `x:TypeArguments` 제네릭 개체 인스턴스화에 대 한 연결 된 개체 요소는 루트 이외의 요소에 있을 수 있습니다. 자세한 내용은 [X:TypeArguments 지시문](xtypearguments-directive.md)의 "XAML 2009" 섹션을 참조 하세요.

- XAML 2009은 태그에서 제네릭 형식의 제약 조건을 지정 하는 구문을 지원 합니다. 이는 `x:TypeArguments` , `x:Type` 또는 두 가지 기능 조합에서 사용할 수 있습니다.

- XAML 2009 for load를 처리할 때 WPF XAML 구현에서는 형식을 사용 하는 특정 프레임 워크 속성의 암시적 형식 변환 동작에도이 기능을 추가 합니다 <xref:System.Type> .

WPF에서는 XAML 2009 기능을 사용할 수 있지만 느슨한 XAML (태그 컴파일되지 않은 XAML)에 대해서만 사용할 수 있습니다. WPF에 대한 태그로 컴파일된 XAML 및 BAML 형식의 XAML은 현재 XAML 2009 키워드 및 기능을 지원하지 않습니다.

## <a name="see-also"></a>참조

- <xref:System.Windows.Style>
- [스타일 지정 및 템플릿](../fundamentals/styles-templates-overview.md)
- [XAML 개요(WPF)](../fundamentals/xaml.md)
- [태그 확장명 및 WPF XAML](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml)
