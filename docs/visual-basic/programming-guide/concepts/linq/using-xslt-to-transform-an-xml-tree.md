---
title: XSLT를 사용하여 XML 트리 변환
ms.date: 07/20/2015
ms.assetid: 3390ca68-c270-4e1d-b64b-6a063a77017c
ms.openlocfilehash: 5332eb0a4fa8a2bd855421d674fe9f0de2ccb5f3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364437"
---
# <a name="using-xslt-to-transform-an-xml-tree-visual-basic"></a><span data-ttu-id="c2e37-102">XSLT를 사용 하 여 XML 트리 변환 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2e37-102">Using XSLT to Transform an XML Tree (Visual Basic)</span></span>

<span data-ttu-id="c2e37-103">XML 트리를 만들고 XML 트리에서 <xref:System.Xml.XmlReader>를 만든 다음 새 문서를 만들고 새 문서에 쓸 <xref:System.Xml.XmlWriter>를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2e37-103">You can create an XML tree, create an <xref:System.Xml.XmlReader> from the XML tree, create a new document, and create an <xref:System.Xml.XmlWriter> that will write into the new document.</span></span> <span data-ttu-id="c2e37-104">그런 다음 <xref:System.Xml.XmlReader> 및 <xref:System.Xml.XmlWriter>를 변환에 전달하여 XSLT 변환을 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2e37-104">Then, you can invoke the XSLT transformation, passing the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> to the transformation.</span></span> <span data-ttu-id="c2e37-105">변환이 성공적으로 완료된 후 새 XML 트리가 변환의 결과로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="c2e37-105">After the transformation successfully completes, the new XML tree is populated with the results of the transform.</span></span>

## <a name="example"></a><span data-ttu-id="c2e37-106">예제</span><span class="sxs-lookup"><span data-stu-id="c2e37-106">Example</span></span>

```vb
Dim xslMarkup As XDocument = _
    <?xml version='1.0'?>
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
    </xsl:stylesheet>

Dim xmlTree As XElement = _
    <Parent>
        <Child1>Child1 data</Child1>
        <Child2>Child2 data</Child2>
    </Parent>

Dim newTree As XDocument = New XDocument()

Using writer As XmlWriter = newTree.CreateWriter()
    ' Load the style sheet.
    Dim xslt As XslCompiledTransform = _
        New XslCompiledTransform()
    xslt.Load(xslMarkup.CreateReader())

    ' Execute the transform and output the results to a writer.
    xslt.Transform(xmlTree.CreateReader(), writer)
End Using

Console.WriteLine(newTree)
```

<span data-ttu-id="c2e37-107">이 예제는 다음과 같은 출력을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="c2e37-107">This example produces the following output:</span></span>

```xml
<Root>
  <C1>Child1 data</C1>
  <C2>Child2 data</C2>
</Root>
```

## <a name="see-also"></a><span data-ttu-id="c2e37-108">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c2e37-108">See also</span></span>

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.CreateReader%2A?displayProperty=nameWithType>
- [<span data-ttu-id="c2e37-109">Visual Basic (Advanced LINQ to XML 프로그래밍)</span><span class="sxs-lookup"><span data-stu-id="c2e37-109">Advanced LINQ to XML Programming (Visual Basic)</span></span>](advanced-linq-to-xml-programming.md)
