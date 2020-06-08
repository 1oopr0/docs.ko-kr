---
title: '방법: 개체를 SOAP 인코딩된 XML 스트림으로 직렬화'
description: 개체를 SOAP 인코딩된 XML 스트림으로 직렬화하는 방법을 알아봅니다. XmlSerializer 클래스를 사용하여 클래스를 직렬화하고 인코딩된 SOAP 메시지를 생성할 수 있습니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
ms.assetid: af406e0a-fa3a-46dd-a7ba-c80731eba3a0
ms.openlocfilehash: 1d38c4e334439ef41b4d4429e52cff04c6463573
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/06/2020
ms.locfileid: "84291567"
---
# <a name="how-to-serialize-an-object-as-a-soap-encoded-xml-stream"></a><span data-ttu-id="8ac59-104">방법: 개체를 SOAP 인코딩된 XML 스트림으로 직렬화</span><span class="sxs-lookup"><span data-stu-id="8ac59-104">How to: Serialize an Object as a SOAP-Encoded XML Stream</span></span>
  
 <span data-ttu-id="8ac59-105">SOAP 메시지는 XML을 사용하여 생성되므로 <xref:System.Xml.Serialization.XmlSerializer> 클래스를 사용하여 클래스를 직렬화하고 인코딩된 SOAP 메시지를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ac59-105">Because a SOAP message is built using XML, the <xref:System.Xml.Serialization.XmlSerializer> class can be used to serialize classes and generate encoded SOAP messages.</span></span> <span data-ttu-id="8ac59-106">결과 XML은 [World Wide Web 컨소시엄 문서의 5단원 “SOAP(Simple Object Access Protocol) 1.1”](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512)을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="8ac59-106">The resulting XML conforms to [section 5 of the World Wide Web Consortium document "Simple Object Access Protocol (SOAP) 1.1"](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512).</span></span> <span data-ttu-id="8ac59-107">SOAP 메시지를 통해 통신하는 XML Web services를 만들 때는 특별한 SOAP 특성 집합을 클래스와 클래스 멤버에 적용하여 XML 스트림을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ac59-107">When you are creating an XML Web service that communicates through SOAP messages, you can customize the XML stream by applying a set of special SOAP attributes to classes and members of classes.</span></span> <span data-ttu-id="8ac59-108">특성 목록을 보려면 [인코딩된 SOAP serialization을 제어하는 특성](attributes-that-control-encoded-soap-serialization.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8ac59-108">For a list of attributes, see [Attributes That Control Encoded SOAP Serialization](attributes-that-control-encoded-soap-serialization.md).</span></span>  
  
### <a name="to-serialize-an-object-as-a-soap-encoded-xml-stream"></a><span data-ttu-id="8ac59-109">개체를 SOAP 인코딩된 XML 스트림으로 serialize하려면</span><span class="sxs-lookup"><span data-stu-id="8ac59-109">To serialize an object as a SOAP-encoded XML stream</span></span>  
  
1. <span data-ttu-id="8ac59-110">[XML 스키마 정의 도구(Xsd.exe)](xml-schema-definition-tool-xsd-exe.md)를 사용하여 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8ac59-110">Create the class using the [XML Schema Definition Tool (Xsd.exe)](xml-schema-definition-tool-xsd-exe.md).</span></span>  
  
2. <span data-ttu-id="8ac59-111">`System.Xml.Serialization`에 있는 하나 이상의 특수 특성을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="8ac59-111">Apply one or more of the special attributes found in `System.Xml.Serialization`.</span></span> <span data-ttu-id="8ac59-112">"인코딩된 SOAP serialization을 제어하는 특성"의 목록을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8ac59-112">See the list in "Attributes That Control Encoded SOAP Serialization."</span></span>  
  
3. <span data-ttu-id="8ac59-113">새 `XmlTypeMapping`를 만들고 serialize된 클래스의 형식으로 `SoapReflectionImporter` 메서드를 호출하여 `ImportTypeMapping`을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8ac59-113">Create an `XmlTypeMapping` by creating a new `SoapReflectionImporter`, and invoking the `ImportTypeMapping` method with the type of the serialized class.</span></span>  
  
     <span data-ttu-id="8ac59-114">다음 코드 예제에서는 `SoapReflectionImporter` 클래스의 `ImportTypeMapping` 메서드를 호출하여 `XmlTypeMapping`을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8ac59-114">The following code example calls the `ImportTypeMapping` method of the `SoapReflectionImporter` class to create an `XmlTypeMapping`.</span></span>  
  
    ```vb  
    ' Serializes a class named Group as a SOAP message.  
    Dim myTypeMapping As XmlTypeMapping =
        New SoapReflectionImporter().ImportTypeMapping(GetType(Group))  
    ```  
  
    ```csharp  
    // Serializes a class named Group as a SOAP message.  
    XmlTypeMapping myTypeMapping =
        new SoapReflectionImporter().ImportTypeMapping(typeof(Group));
    ```  
  
4. <span data-ttu-id="8ac59-115">`XmlSerializer`을 `XmlTypeMapping` 생성자로 전달하여 <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8ac59-115">Create an instance of the `XmlSerializer` class by passing the `XmlTypeMapping` to the <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29> constructor.</span></span>  
  
    ```vb  
    Dim mySerializer As XmlSerializer = New XmlSerializer(myTypeMapping)  
    ```  
  
    ```csharp  
    XmlSerializer mySerializer = new XmlSerializer(myTypeMapping);  
    ```  
  
5. <span data-ttu-id="8ac59-116">`Serialize` 또는 `Deserialize` 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="8ac59-116">Call the `Serialize` or `Deserialize` method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ac59-117">예제</span><span class="sxs-lookup"><span data-stu-id="8ac59-117">Example</span></span>  
  
```vb  
' Serializes a class named Group as a SOAP message.  
Dim myTypeMapping As XmlTypeMapping =
    New SoapReflectionImporter().ImportTypeMapping(GetType(Group))
Dim mySerializer As XmlSerializer = New XmlSerializer(myTypeMapping)  
```  
  
```csharp  
// Serializes a class named Group as a SOAP message.  
XmlTypeMapping myTypeMapping =
    new SoapReflectionImporter().ImportTypeMapping(typeof(Group));
XmlSerializer mySerializer = new XmlSerializer(myTypeMapping);  
```  
  
## <a name="see-also"></a><span data-ttu-id="8ac59-118">참조</span><span class="sxs-lookup"><span data-stu-id="8ac59-118">See also</span></span>

- [<span data-ttu-id="8ac59-119">XML 및 SOAP serialization</span><span class="sxs-lookup"><span data-stu-id="8ac59-119">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
- [<span data-ttu-id="8ac59-120">인코딩된 SOAP serialization을 제어하는 특성</span><span class="sxs-lookup"><span data-stu-id="8ac59-120">Attributes That Control Encoded SOAP Serialization</span></span>](attributes-that-control-encoded-soap-serialization.md)
- [<span data-ttu-id="8ac59-121">XML Web Services의 XML serialization</span><span class="sxs-lookup"><span data-stu-id="8ac59-121">XML Serialization with XML Web Services</span></span>](xml-serialization-with-xml-web-services.md)
- [<span data-ttu-id="8ac59-122">방법: 개체 직렬화</span><span class="sxs-lookup"><span data-stu-id="8ac59-122">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
- [<span data-ttu-id="8ac59-123">방법: 개체 역직렬화</span><span class="sxs-lookup"><span data-stu-id="8ac59-123">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)
- [<span data-ttu-id="8ac59-124">방법: 인코딩된 SOAP XML Serialization 재정의</span><span class="sxs-lookup"><span data-stu-id="8ac59-124">How to: Override Encoded SOAP XML Serialization</span></span>](how-to-override-encoded-soap-xml-serialization.md)
