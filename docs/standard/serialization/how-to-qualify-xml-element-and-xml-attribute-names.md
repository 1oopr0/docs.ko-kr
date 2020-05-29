---
title: XML 요소 및 XML 특성 이름을 한정하는 방법
description: 이 문서에서는 XML 문서에서 XML 요소 및 XML 특성의 이름을 한정하는 방법을 보여 줍니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- qualifying XML names
- qualifying XML elements
- XML namespaces, qualifying elements and names in
ms.assetid: 44719f90-7e15-42e8-a9e2-282287e2b5bf
ms.openlocfilehash: 6c29e03d9ce28e5b0abc68a5d7e8d82f4485ac93
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378406"
---
# <a name="how-to-qualify-xml-element-and-xml-attribute-names"></a>XML 요소 및 XML 특성 이름을 한정하는 방법

클래스의 인스턴스에 의해 포함된 XML 네임스페이스는 <xref:System.Xml.Serialization.XmlSerializerNamespaces>[Namespaces in XML](https://www.w3.org/TR/REC-xml-names/)이라는 W3C(World Wide Web 컨소시엄) 사양을 따라야 합니다.

XML 네임스페이스는 XML 문서에서 XML 요소 및 XML 특성의 이름을 정규화하는 메서드를 제공합니다. 정규화된 이름은 콜론으로 구분된 접두사와 로컬 이름으로 구성됩니다. 접두사는 자리 표시자로만 기능하여 네임스페이스를 지정하는 URI에 매핑됩니다. 보편적으로 관리되는 URI 네임스페이스와 로컬 이름을 조합하면 보편적으로 고유한 이름이 만들어집니다.

`XmlSerializerNamespaces`의 인스턴스를 만들고 네임스페이스 쌍을 개체에 추가하면 XML 문서에 사용되는 접두사를 지정할 수 있습니다.

## <a name="to-create-qualified-names-in-an-xml-document"></a>XML 문서에서 정규화된 이름을 만들려면

1. `XmlSerializerNamespaces` 클래스의 인스턴스를 만듭니다.

2. 모든 접두사와 네임스페이스 쌍을 `XmlSerializerNamespaces`에 추가합니다.

3. 적절한 `System.Xml.Serialization` 특성을 <xref:System.Xml.Serialization.XmlSerializer>가 XML 문서로 serialize할 각 멤버나 클래스에 적용합니다.

    사용할 수 있는 특성은 <xref:System.Xml.Serialization.XmlAnyElementAttribute>, <xref:System.Xml.Serialization.XmlArrayAttribute>, <xref:System.Xml.Serialization.XmlArrayItemAttribute>, <xref:System.Xml.Serialization.XmlAttributeAttribute>, <xref:System.Xml.Serialization.XmlElementAttribute>, <xref:System.Xml.Serialization.XmlRootAttribute> 및 <xref:System.Xml.Serialization.XmlTypeAttribute>입니다.

4. 각 특성의 `Namespace` 속성을 `XmlSerializerNamespaces`의 네임스페이스 값 중 하나로 설정합니다.

5. `XmlSerializerNamespaces`를 `XmlSerializer`의 `Serialize` 메서드에 전달합니다.

## <a name="example"></a>예제

다음 예제에서는 `XmlSerializerNamespaces`를 만들고 두 개의 접두사와 네임스페이스 쌍을 개체에 추가합니다. 코드에서는 `XmlSerializer` 클래스의 인스턴스를 serialize하는 데 사용되는 `Books`를 만듭니다. 코드는 `Serialize`를 사용하여 `XmlSerializerNamespaces` 메서드를 호출하여 XML이 접두사가 지정된 네임스페이스를 포함할 수 있게 됩니다.

```vb
Imports System.IO
Imports System.Xml
Imports System.Xml.Serialization

Public Module Program

    Public Sub Main()
        SerializeObject("XmlNamespaces.xml")
    End Sub

    Public Sub SerializeObject(filename As String)
        Dim mySerializer As New XmlSerializer(GetType(Books))
        ' Writing a file requires a TextWriter.
        Dim myWriter As New StreamWriter(filename)

        ' Creates an XmlSerializerNamespaces and adds two
        ' prefix-namespace pairs.
        Dim myNamespaces As New XmlSerializerNamespaces()
        myNamespaces.Add("books", "http://www.cpandl.com")
        myNamespaces.Add("money", "http://www.cohowinery.com")

        ' Creates a Book.
        Dim myBook As New Book()
        myBook.TITLE = "A Book Title"
        Dim myPrice As New Price()
        myPrice.price = CDec(9.95)
        myPrice.currency = "US Dollar"
        myBook.PRICE = myPrice
        Dim myBooks As New Books()
        myBooks.Book = myBook
        mySerializer.Serialize(myWriter, myBooks, myNamespaces)
        myWriter.Close()
    End Sub
End Module

Public Class Books
    <XmlElement([Namespace] := "http://www.cohowinery.com")> _
    Public Book As Book
End Class

<XmlType([Namespace] := "http://www.cpandl.com")> _
Public Class Book
    <XmlElement([Namespace] := "http://www.cpandl.com")> _
    Public TITLE As String
    <XmlElement([Namespace] := "http://www.cohowinery.com")> _
    Public PRICE As Price
End Class

Public Class Price
    <XmlAttribute([Namespace] := "http://www.cpandl.com")> _
    Public currency As String
    <XmlElement([Namespace] := "http://www.cohowinery.com")> _
    Public price As Decimal
End Class
```

```csharp
using System;
using System.IO;
using System.Xml;
using System.Xml.Serialization;

public class Program
{
    public static void Main()
    {
        SerializeObject("XmlNamespaces.xml");
    }

    public static void SerializeObject(string filename)
    {
        var mySerializer = new XmlSerializer(typeof(Books));
        // Writing a file requires a TextWriter.
        TextWriter myWriter = new StreamWriter(filename);

        // Creates an XmlSerializerNamespaces and adds two
        // prefix-namespace pairs.
        var myNamespaces = new XmlSerializerNamespaces();
        myNamespaces.Add("books", "http://www.cpandl.com");
        myNamespaces.Add("money", "http://www.cohowinery.com");

        // Creates a Book.
        var myBook = new Book();
        myBook.TITLE = "A Book Title";
        var myPrice = new Price();
        myPrice.price = (decimal) 9.95;
        myPrice.currency = "US Dollar";
        myBook.PRICE = myPrice;
        var myBooks = new Books();
        myBooks.Book = myBook;
        mySerializer.Serialize(myWriter, myBooks, myNamespaces);
        myWriter.Close();
    }
}

public class Books
{
    [XmlElement(Namespace = "http://www.cohowinery.com")]
    public Book Book;
}

[XmlType(Namespace ="http://www.cpandl.com")]
public class Book
{
    [XmlElement(Namespace = "http://www.cpandl.com")]
    public string TITLE;
    [XmlElement(Namespace ="http://www.cohowinery.com")]
    public Price PRICE;
}

public class Price
{
    [XmlAttribute(Namespace = "http://www.cpandl.com")]
    public string currency;
    [XmlElement(Namespace = "http://www.cohowinery.com")]
    public decimal price;
}
```

## <a name="see-also"></a>참조

- <xref:System.Xml.Serialization.XmlSerializer>
- [XML 스키마 정의 도구 및 XML serialization](the-xml-schema-definition-tool-and-xml-serialization.md)
- [XML serialization 소개](introducing-xml-serialization.md)
- [XmlSerializer 클래스](xref:System.Xml.Serialization.XmlSerializer)
- [XML serialization을 제어하는 특성](attributes-that-control-xml-serialization.md)
- [방법: XML 스트림의 대체 요소 이름 지정](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)
- [방법: 개체 직렬화](how-to-serialize-an-object.md)
- [방법: 개체 역직렬화](how-to-deserialize-an-object.md)
