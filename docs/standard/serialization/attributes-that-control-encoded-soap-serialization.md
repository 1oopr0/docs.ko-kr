---
title: 인코딩된 SOAP Serialization을 제어하는 특성
description: 이 문서에는 SOAP 사양을 준수하는 데 필요한 System.Xml.Serialization 네임스페이스에 있는 특별한 특성 집합이 나열되어 있습니다.
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- XML serialization, attributes
- attributes [.NET Framework], XML serialization
- serialization, attributes
ms.assetid: 93ee258c-9c0f-4a08-897c-c10db7a00f91
ms.openlocfilehash: 9e99856c3ac70b122c0def23e36bbc3059c5891c
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378469"
---
# <a name="attributes-that-control-encoded-soap-serialization"></a>인코딩된 SOAP Serialization을 제어하는 특성

World Wide Web 컨소시엄(W3C) 문서 [SOAP(Simple Object Access Protocol) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)에는 SOAP 매개 변수를 인코딩할 수 있는 방법을 설명하는 선택적 단원(5단원)이 포함되어 있습니다. 사양의 5단원을 따르려면 <xref:System.Xml.Serialization> 네임스페이스에 속한 특별한 특성 집합을 사용해야 합니다. 이러한 특성을 클래스 및 클래스 멤버에 적절하게 적용한 다음 <xref:System.Xml.Serialization.XmlSerializer>를 사용하여 클래스의 인스턴스를 serialize합니다.

다음 표에서는 특성, 해당 특성을 적용할 수 있는 위치 및 해당 특성이 수행하는 작업을 보여 줍니다. 이러한 특성을 사용하여 XML serialization을 제어하는 방법에 대한 자세한 내용은 [방법: 개체를 SOAP 인코딩된 XML 스트림으로 직렬화](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md) 및 [방법: 인코딩된 SOAP XML Serialization 재정의](how-to-override-encoded-soap-xml-serialization.md)를 참조하세요.

특성에 대한 자세한 내용은 [특성](../../../docs/standard/attributes/index.md)을 참조하세요.

|특성|적용 대상|설명|
|---------------|----------------|---------------|
|<xref:System.Xml.Serialization.SoapAttributeAttribute>|public 필드, 속성, 매개 변수 또는 반환 값입니다.|클래스 멤버는 XML 특성으로 serialize됩니다.|
|<xref:System.Xml.Serialization.SoapElementAttribute>|public 필드, 속성, 매개 변수 또는 반환 값입니다.|클래스는 XML 요소로 serialize됩니다.|
|<xref:System.Xml.Serialization.SoapEnumAttribute>|열거형 식별자인 public 필드입니다.|열거형 멤버의 요소 이름입니다.|
|<xref:System.Xml.Serialization.SoapIgnoreAttribute>|public 속성 및 필드입니다.|속성 또는 필드는 포함 클래스가 serialize될 때 무시되어야 합니다.|
|<xref:System.Xml.Serialization.SoapIncludeAttribute>|WSDL(웹 서비스 설명 언어) 문서에 대한 공용 파생 클래스 선언 및 공용 메서드입니다.|스키마를 생성할 때 형식을 포함해야 합니다(serialize될 때 인식되도록).|
|<xref:System.Xml.Serialization.SoapTypeAttribute>|public 클래스 선언입니다.|클래스는 XML 형식으로 serialize되어야 합니다.|

## <a name="see-also"></a>참조

- [XML 및 SOAP serialization](xml-and-soap-serialization.md)
- [방법: 개체를 SOAP 인코딩된 XML 스트림으로 직렬화](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)
- [방법: 인코딩된 SOAP XML Serialization 재정의](how-to-override-encoded-soap-xml-serialization.md)
- [특성](../../../docs/standard/attributes/index.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [방법: 개체 직렬화](how-to-serialize-an-object.md)
- [방법: 개체 역직렬화](how-to-deserialize-an-object.md)
