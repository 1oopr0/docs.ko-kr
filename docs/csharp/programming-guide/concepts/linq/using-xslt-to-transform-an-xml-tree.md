---
title: XSLT를 사용하여 XML 트리 변환(C#)
description: XmlReader 및 XmlWriter 인스턴스에서 XSLT 변형을 호출하여 C#에서 XSLT를 사용해 XML 트리를 변환하는 방법을 알아봅니다.
ms.date: 07/20/2015
ms.assetid: 373a2699-d4c5-471b-9bda-c1f0ab73b477
ms.openlocfilehash: bce92136850aeef52e5b17cd7bc658b85fe70604
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302271"
---
# <a name="using-xslt-to-transform-an-xml-tree-c"></a><span data-ttu-id="e8771-103">XSLT를 사용하여 XML 트리 변환(C#)</span><span class="sxs-lookup"><span data-stu-id="e8771-103">Using XSLT to Transform an XML Tree (C#)</span></span>
<span data-ttu-id="e8771-104">XML 트리를 만들고 XML 트리에서 <xref:System.Xml.XmlReader>를 만든 다음 새 문서를 만들고 새 문서에 쓸 <xref:System.Xml.XmlWriter>를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8771-104">You can create an XML tree, create an <xref:System.Xml.XmlReader> from the XML tree, create a new document, and create an <xref:System.Xml.XmlWriter> that will write into the new document.</span></span> <span data-ttu-id="e8771-105">그런 다음 <xref:System.Xml.XmlReader> 및 <xref:System.Xml.XmlWriter>를 변환에 전달하여 XSLT 변환을 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8771-105">Then, you can invoke the XSLT transformation, passing the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> to the transformation.</span></span> <span data-ttu-id="e8771-106">변환이 성공적으로 완료된 후 새 XML 트리가 변환의 결과로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="e8771-106">After the transformation successfully completes, the new XML tree is populated with the results of the transform.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8771-107">예제</span><span class="sxs-lookup"><span data-stu-id="e8771-107">Example</span></span>  
  
```csharp  
string xslt = @"<?xml version='1.0'?>  
    <xsl:stylesheet xmlns:xsl='http://www.w3.org/1999/XSL/Transform' version='1.0'>  
        <xsl:template match='/Parent'>  
            <Root>  
                <C1>  
                <xsl:value-of select='Child1'/>  
                </C1>  
                <C2>  
                <xsl:value-of select='Child2'/>  
                </C2>  
            </Root>  
        </xsl:template>  
    </xsl:stylesheet>";

var oldDocument = new XDocument(
    new XElement("Parent",
        new XElement("Child1", "Child1 data"),
        new XElement("Child2", "Child2 data")
    )
);

var newDocument = new XDocument();

using (var stringReader = new StringReader(xslt))
{
    using (XmlReader xsltReader = XmlReader.Create(stringReader))
    {
        var transformer = new XslCompiledTransform();
        transformer.Load(xsltReader);
        using (XmlReader oldDocumentReader = oldDocument.CreateReader())
        {
            using (XmlWriter newDocumentWriter = newDocument.CreateWriter())
            {
                transformer.Transform(oldDocumentReader, newDocumentWriter);
            }
        }
    }
}

string result = newDocument.ToString();
Console.WriteLine(result);
```  
  
 <span data-ttu-id="e8771-108">이 예에서 생성되는 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e8771-108">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e8771-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e8771-109">See also</span></span>

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.CreateReader%2A?displayProperty=nameWithType>
