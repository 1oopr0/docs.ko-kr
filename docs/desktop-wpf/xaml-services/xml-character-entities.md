---
title: XML 문자 엔터티 및 XAML
ms.date: 03/30/2017
f1_keywords:
- '&'
- '&amp'
- '&gt'
- '&lt'
helpviewer_keywords:
- XAML [XAML Services], special characters
- ampersand (&) [XAML Services]
- special characters [XAML Services]
- apostrophe (') [XAML Services]
- greater-than (>) character [XAML Services]
- XAML [XAML Services], quotation mark (")
- XAML [XAML Services], apostrophe (')
- '& (ampersand) [XAML Services]'
- XAML [XAML Services], & (ampersand)
- XAML [XAML Services], escape sequence
- quotation mark (") [XAML Services]
- less-than (<) character [XAML Services]
ms.assetid: 6896d0ce-74f7-420a-9ab4-de9bbf390e8d
ms.openlocfilehash: 1ba99cda512bc5e18c646b09f26672a39c1cf53c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548194"
---
# <a name="xml-character-entities-and-xaml"></a>XML 문자 엔터티 및 XAML

XAML은 특수 문자를 위해 XML에 정의된 문자 엔터티를 사용합니다. 이 항목에서는 일부 특정 문자 엔터티 및 XAML의 다른 XML 개념에 대한 일반적인 고려 사항을 설명합니다.

## <a name="character-entities-and-escaping-issues-that-are-unique-to-xaml"></a>XAML에 고유한 문자 엔터티 및 이스케이프 문제

XAML 태그는 일반적으로 XML에 정의된 것과 동일한 문자 엔터티 및 이스케이프 시퀀스를 사용합니다.

가장 큰 차이점은, 중괄호({ })는 중괄호로 묶인 문자 시퀀스를 태그 확장으로 해석해야 한다고 XAML 프로세서에 알리기 때문에 XAML에서는 중괄호가 상당한 의미를 가진다는 것입니다. 태그 확장에 대한 자세한 내용은 [Markup Extensions for XAML Overview](markup-extensions-overview.md)를 참조하세요.

하지만 XML이 아니라 XAML에 특정한 이스케이프 시퀀스를 사용하여 중괄호를 리터럴 문자로 표시할 수는 있습니다. 자세한 내용은 [ {} 이스케이프 시퀀스 태그 확장명](escape-sequence-markup-extension.md)을 참조 하세요.

백슬래시 ( \\ )는 문자열로 처리 될 때 이스케이프 시퀀스가 필요 하지 않습니다.

## <a name="xml-character-entities"></a>XML 문자 엔터티

앞서 언급했듯이, 대부분의 문자 엔터티 및 XAML 태그 작성에 일반적으로 사용되는 이스케이프 시퀀스는 XML에 의해 정의됩니다. 이 항목에서는 이러한 엔터티의 전체 목록을 제공하지는 않습니다. 이 엔터티에 대한 자세한 참조 정보는 외부 설명서(예: XML 사양)에서 찾을 수 있습니다. 그러나 편의상, 이 항목에서는 XAML 태그에 일반적으로 사용되는 특정 XML 문자 엔터티 중 일부를 제시합니다.

|문자|엔터티|메모|
|---------------|------------|-----------|
|& (앰퍼샌드)|\&amp;|특성 값 및 요소의 콘텐츠에 대해 모두 사용해야 합니다.|
|> (보다 큼 문자)|\&gt;|특성 값에 대해 사용 해야 하지만 >은 < 앞에 오지 않는 한 요소의 콘텐츠로 허용 됩니다.|
|< (보다 작음 문자)|\&lt;|는 특성 값에 사용 해야 하지만 뒤에 \< is acceptable as the content of an element as long as > 오는 것은 아닙니다.|
|"(곧은 따옴표)|\&quot;|특성 값에 대해 사용해야 하지만 곧은 따옴표(")는 요소의 콘텐츠로 허용됩니다. 특성 값을 곧은 작은따옴표(')나 곧은 큰따옴표(")로 묶을 수 있습니다. 둘 중 어느 것이 먼저 나오든 이들 문자는 특성 값 포함을 정의하며, 대체 따옴표를 값 내부 리터럴로 사용할 수 있습니다.|
|'(곧은 작은따옴표)|\&apos;|특성 값에 대해 사용해야 하지만 곧은 작은따옴표(')는 요소의 콘텐츠로 허용됩니다. 특성 값을 곧은 작은따옴표(')나 곧은 큰따옴표(")로 묶을 수 있습니다. 둘 중 어느 것이 먼저 나오든 이들 문자는 특성 값 포함을 정의하며, 대체 따옴표를 값 내부 리터럴로 사용할 수 있습니다.|
|(숫자 매핑)|&#*[integer]*; 또는 & # x *[hex]*;|XAML은 활성화된 인코딩에 대한 숫자 매핑을 지원합니다.|
|(줄 바꿈하지 않는 공백)|&\#160; (UTF-8 인코딩 가정)|유동 문서 요소 또는 WPF <xref:System.Windows.Controls.TextBox> 등의 텍스트를 사용하는 요소의 경우, 줄 바꿈하지 않는 공백은 `xml:space="default"`의 경우에도 태그 외부에서 정규화되지 않습니다. (자세한 내용은 [XAML의 공백 처리](white-space-processing.md)를 참조 하세요.)|

## <a name="xml-comment-format"></a>XML 주석 형식

XAML은 XML 주석 형식을 사용합니다. 즉, 주석의 시작은 `<!--`이고 주석의 끝은 `-->,`이며 주석 내에서 `--` 시퀀스가 발생해서는 안 됩니다.

## <a name="xml-processing-instructions"></a>XML 처리 명령

XAML은 XML 처리 명령을 XML 사양에 따라 처리합니다. 이 사양에서는 이 명령을 거쳐야 한다고 지정합니다. .NET XAML 서비스의 XAML 처리에서는 처리 명령을 사용 하지 않습니다. XAML을 사용하는 다른 기존 프레임워크에서도 XAML의 처리 명령을 사용하지 않습니다.

## <a name="see-also"></a>참조

- [XAML 개요(WPF)](../fundamentals/xaml.md)
- [태그 확장명 및 WPF XAML](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml)
- [XamlName 문법](xamlname-grammar.md)
- [XAML의 공백 처리](white-space-processing.md)
