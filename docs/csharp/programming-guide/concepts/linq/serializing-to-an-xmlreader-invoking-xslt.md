---
title: XmlReader로 serialize(XSLT 호출)(C#)
description: C#에서 CreateReader를 사용하여 XmlReader를 만드는 방법을 알아봅니다. 이 XmlReader에서 읽는 모듈은 XML 트리에서 노드를 읽고 처리합니다.
ms.date: 07/20/2015
ms.assetid: 4cc3ee03-ef4c-429b-a408-fedd10b728cd
ms.openlocfilehash: aa5a232c74c5314cb7f1cf03c2a8875ca1cd04df
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302414"
---
# <a name="serializing-to-an-xmlreader-invoking-xslt-c"></a><span data-ttu-id="47841-104">XmlReader로 serialize(XSLT 호출)(C#)</span><span class="sxs-lookup"><span data-stu-id="47841-104">Serializing to an XmlReader (Invoking XSLT) (C#)</span></span>
<span data-ttu-id="47841-105">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]의 <xref:System.Xml?displayProperty=nameWithType> 상호 운용성 기능을 사용할 때 <xref:System.Xml.Linq.XNode.CreateReader%2A>를 사용하여 <xref:System.Xml.XmlReader>를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47841-105">When you use the <xref:System.Xml?displayProperty=nameWithType> interoperability capabilities of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can use <xref:System.Xml.Linq.XNode.CreateReader%2A> to create an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="47841-106">만들어진 <xref:System.Xml.XmlReader>에서 읽는 모듈은 XML 트리에서 노드를 읽고 적절하게 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="47841-106">The module that reads from this <xref:System.Xml.XmlReader> reads the nodes from the XML tree and processes them accordingly.</span></span>  
  
## <a name="invoking-an-xslt-transformation"></a><span data-ttu-id="47841-107">XSLT 변환 호출</span><span class="sxs-lookup"><span data-stu-id="47841-107">Invoking an XSLT Transformation</span></span>  
 <span data-ttu-id="47841-108">이 메서드를 사용할 수 있는 한 가지 경우는 XSLT 변환을 호출할 때입니다.</span><span class="sxs-lookup"><span data-stu-id="47841-108">One possible use for this method is when invoking an XSLT transformation.</span></span> <span data-ttu-id="47841-109">XML 트리를 만들고 XML 트리에서 <xref:System.Xml.XmlReader>를 만든 다음 새 문서를 만들고 새 문서에 쓸 <xref:System.Xml.XmlWriter>를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47841-109">You can create an XML tree, create an <xref:System.Xml.XmlReader> from the XML tree, create a new document, and then create an <xref:System.Xml.XmlWriter> to write into the new document.</span></span> <span data-ttu-id="47841-110">그런 다음 XSLT 변형을 호출하여 <xref:System.Xml.XmlReader> 및 <xref:System.Xml.XmlWriter>를 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47841-110">Then, you can invoke the XSLT transformation, passing in <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="47841-111">변환이 성공적으로 완료된 후 새 XML 트리가 변환의 결과로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="47841-111">After the transformation successfully completes, the new XML tree is populated with the results of the transformation.</span></span>  
  
```csharp  
string xslMarkup = @"<?xml version='1.0'?>  
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
  
XDocument xmlTree = new XDocument(  
    new XElement("Parent",  
        new XElement("Child1", "Child1 data"),  
        new XElement("Child2", "Child2 data")  
    )  
);  
  
XDocument newTree = new XDocument();  
using (XmlWriter writer = newTree.CreateWriter()) {  
    // Load the style sheet.  
    XslCompiledTransform xslt = new XslCompiledTransform();  
    xslt.Load(XmlReader.Create(new StringReader(xslMarkup)));  
  
    // Execute the transformation and output the results to a writer.  
    xslt.Transform(xmlTree.CreateReader(), writer);  
}  
  
Console.WriteLine(newTree);  
```  
  
 <span data-ttu-id="47841-112">이 예에서 생성되는 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="47841-112">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="47841-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47841-113">See also</span></span>

- [<span data-ttu-id="47841-114">XML 트리 serialize(C#)</span><span class="sxs-lookup"><span data-stu-id="47841-114">Serializing XML Trees (C#)</span></span>](serializing-to-files-textwriters-and-xmlwriters.md)
