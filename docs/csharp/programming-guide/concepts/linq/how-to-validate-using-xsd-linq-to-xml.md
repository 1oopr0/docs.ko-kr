---
title: XSD를 사용하여 유효성을 검사하는 방법(LINQ to XML)(C#)
description: XSD(XML 스키마 정의 언어) 파일에 대해 XML 트리의 유효성을 검사하는 방법을 알아봅니다. 코드 예제를 살펴보고 추가 리소스를 확인합니다.
ms.date: 07/20/2015
ms.assetid: 6a7f83a9-2d74-4c2b-8417-0a8595879516
ms.openlocfilehash: 3b4d2137d511efbe20e4d31ad27e4975d5444ec9
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302635"
---
# <a name="how-to-validate-using-xsd-linq-to-xml-c"></a><span data-ttu-id="6a17d-104">XSD를 사용하여 유효성을 검사하는 방법(LINQ to XML)(C#)</span><span class="sxs-lookup"><span data-stu-id="6a17d-104">How to validate using XSD (LINQ to XML) (C#)</span></span>
<span data-ttu-id="6a17d-105"><xref:System.Xml.Schema> 네임스페이스에는 XSD(XML 스키마 정의 언어) 파일에 대해 XML 트리의 유효성을 쉽게 검사할 수 있도록 하는 확장 메서드가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a17d-105">The <xref:System.Xml.Schema> namespace contains extension methods that make it easy to validate an XML tree against an XML Schema Definition Language (XSD) file.</span></span> <span data-ttu-id="6a17d-106">자세한 내용은 <xref:System.Xml.Schema.Extensions.Validate%2A> 메서드 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6a17d-106">For more information, see the <xref:System.Xml.Schema.Extensions.Validate%2A> method documentation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a17d-107">예제</span><span class="sxs-lookup"><span data-stu-id="6a17d-107">Example</span></span>  
 <span data-ttu-id="6a17d-108">다음 예제에서는 <xref:System.Xml.Schema.XmlSchemaSet>을 만든 다음 스키마 집합에 대해 두 <xref:System.Xml.Linq.XDocument> 개체의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="6a17d-108">The following example creates an <xref:System.Xml.Schema.XmlSchemaSet>, then validates two <xref:System.Xml.Linq.XDocument> objects against the schema set.</span></span> <span data-ttu-id="6a17d-109">문서 중 하나는 유효하고 다른 하나는 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6a17d-109">One of the documents is valid, the other is not.</span></span>  
  
```csharp  
string xsdMarkup =  
    @"<xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'>  
       <xsd:element name='Root'>  
        <xsd:complexType>  
         <xsd:sequence>  
          <xsd:element name='Child1' minOccurs='1' maxOccurs='1'/>  
          <xsd:element name='Child2' minOccurs='1' maxOccurs='1'/>  
         </xsd:sequence>  
        </xsd:complexType>  
       </xsd:element>  
      </xsd:schema>";  
XmlSchemaSet schemas = new XmlSchemaSet();  
schemas.Add("", XmlReader.Create(new StringReader(xsdMarkup)));  
  
XDocument doc1 = new XDocument(  
    new XElement("Root",  
        new XElement("Child1", "content1"),  
        new XElement("Child2", "content1")  
    )  
);  
  
XDocument doc2 = new XDocument(  
    new XElement("Root",  
        new XElement("Child1", "content1"),  
        new XElement("Child3", "content1")  
    )  
);  
  
Console.WriteLine("Validating doc1");  
bool errors = false;  
doc1.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("doc1 {0}", errors ? "did not validate" : "validated");  
  
Console.WriteLine();  
Console.WriteLine("Validating doc2");  
errors = false;  
doc2.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("doc2 {0}", errors ? "did not validate" : "validated");  
```  
  
 <span data-ttu-id="6a17d-110">이 예제는 다음과 같은 출력을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="6a17d-110">This example produces the following output:</span></span>  
  
```output  
Validating doc1  
doc1 validated  
  
Validating doc2  
The element 'Root' has invalid child element 'Child3'. List of possible elements expected: 'Child2'.  
doc2 did not validate  
```  
  
## <a name="example"></a><span data-ttu-id="6a17d-111">예제</span><span class="sxs-lookup"><span data-stu-id="6a17d-111">Example</span></span>  
 <span data-ttu-id="6a17d-112">다음 예제에서는 [샘플 XML 파일: Customers 및 Orders(LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md)의 XML 문서가 [샘플 XSD 파일: Customers 및 Orders](./sample-xsd-file-customers-and-orders1.md)의 스키마별로 유효한지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6a17d-112">The following example validates that the XML document from [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) is valid per the schema from [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span> <span data-ttu-id="6a17d-113">소스 XML 문서를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="6a17d-113">It then modifies the source XML document.</span></span> <span data-ttu-id="6a17d-114">여기에서는 첫 번째 고객에 대한 `CustomerID` 특성을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="6a17d-114">It changes the `CustomerID` attribute on the first customer.</span></span> <span data-ttu-id="6a17d-115">변경한 후에는 주문이 존재하지 않는 고객을 참조하게 되므로 XML 문서가 더 이상 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6a17d-115">After the change, orders will then refer to a customer that does not exist, so the XML document will no longer validate.</span></span>  
  
 <span data-ttu-id="6a17d-116">이 예제에서는 XML 문서로을 사용합니다. [샘플 XML 파일: Customers 및 Orders(LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="6a17d-116">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
 <span data-ttu-id="6a17d-117">이 예제에서는 XSD 스키마을 사용합니다. [샘플 XSD 파일: Customer 및 Order](./sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="6a17d-117">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span>  
  
```csharp  
XmlSchemaSet schemas = new XmlSchemaSet();  
schemas.Add("", "CustomersOrders.xsd");  
  
Console.WriteLine("Attempting to validate");  
XDocument custOrdDoc = XDocument.Load("CustomersOrders.xml");  
bool errors = false;  
custOrdDoc.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("custOrdDoc {0}", errors ? "did not validate" : "validated");  
  
Console.WriteLine();  
// Modify the source document so that it will not validate.  
custOrdDoc.Root.Element("Orders").Element("Order").Element("CustomerID").Value = "AAAAA";  
Console.WriteLine("Attempting to validate after modification");  
errors = false;  
custOrdDoc.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("custOrdDoc {0}", errors ? "did not validate" : "validated");  
```  
  
 <span data-ttu-id="6a17d-118">이 예에서 생성되는 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6a17d-118">This example produces the following output:</span></span>  
  
```output  
Attempting to validate  
custOrdDoc validated  
  
Attempting to validate after modification  
The key sequence 'AAAAA' in Keyref fails to refer to some key.  
custOrdDoc did not validate  
```  
  
## <a name="see-also"></a><span data-ttu-id="6a17d-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6a17d-119">See also</span></span>

- <xref:System.Xml.Schema.Extensions.Validate%2A>
- [<span data-ttu-id="6a17d-120">XML 트리 만들기(C#)</span><span class="sxs-lookup"><span data-stu-id="6a17d-120">Creating XML Trees (C#)</span></span>](creating-xml-trees-linq-to-xml-2.md)
