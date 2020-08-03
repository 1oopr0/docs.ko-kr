---
title: 큰 XML 문서의 스트리밍 변환을 수행하는 방법(C#)
description: 일부 파일에 과도한 메모리 사용을 피하기 위해 C#의 XML로 텍스트의 스트리밍을 변환하는 방법에 대해 알아봅니다.
ms.date: 07/20/2015
ms.assetid: 5f16d1f8-5370-4b55-b0c8-e497df163037
ms.openlocfilehash: e1ab2866079b2244dc764271d7ba63173349e2f3
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104860"
---
# <a name="how-to-perform-streaming-transform-of-large-xml-documents-c"></a><span data-ttu-id="1a20f-103">큰 XML 문서의 스트리밍 변환을 수행하는 방법(C#)</span><span class="sxs-lookup"><span data-stu-id="1a20f-103">How to perform streaming transform of large XML documents (C#)</span></span>
<span data-ttu-id="1a20f-104">큰 XML 파일을 변환하고 애플리케이션의 메모리 사용 공간이 예상 가능하도록 애플리케이션을 작성해야 하는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-104">Sometimes you have to transform large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="1a20f-105">XML 트리를 매우 큰 XML 파일로 채우려는 경우 메모리 사용은 파일 크기에 비례하므로 지나치게 증가하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-105">If you try to populate an XML tree with a very large XML file, your memory usage will be proportional to the size of the file (that is, excessive).</span></span> <span data-ttu-id="1a20f-106">따라서 스트리밍 기법을 대신 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-106">Therefore, you should use a streaming technique instead.</span></span>  
  
 <span data-ttu-id="1a20f-107">스트리밍 기법은 소스 문서를 한 번만 처리해야 하고 문서 순서의 요소를 처리할 수 있는 경우에 가장 효과적으로 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-107">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="1a20f-108"><xref:System.Linq.Enumerable.OrderBy%2A>와 같은 특정 표준 쿼리 연산자는 자신의 소스를 반복하고 모든 데이터를 수집하여 정렬한 다음 시퀀스의 첫 번째 항목을 최종적으로 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-108">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="1a20f-109">첫 번째 항목을 반환하기 전에 소스를 유형화하는 쿼리 연산자를 사용하는 경우 애플리케이션에 대한 작은 메모리 사용 공간이 유지되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-109">Note that if you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint for your application.</span></span>  
  
<span data-ttu-id="1a20f-110">[헤더 정보에 액세스하여 XML 조각을 스트리밍하는 방법(C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md)에 설명된 기법을 사용하는 경우에도 변환된 문서를 포함하는 XML 트리를 어셈블하려고 하면 메모리 사용 공간이 너무 커집니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-110">Even if you use the technique described in [How to stream XML fragments with access to header information (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md), if you try to assemble an XML tree that contains the transformed document, memory usage will be too great.</span></span>
  
 <span data-ttu-id="1a20f-111">두 가지 주요 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-111">There are two main approaches.</span></span> <span data-ttu-id="1a20f-112">그 중 하나는 <xref:System.Xml.Linq.XStreamingElement>의 지연된 처리 특성을 사용하는 것이고,</span><span class="sxs-lookup"><span data-stu-id="1a20f-112">One approach is to use the deferred processing characteristics of <xref:System.Xml.Linq.XStreamingElement>.</span></span> <span data-ttu-id="1a20f-113">다른 하나는 <xref:System.Xml.XmlWriter>를 만들고 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]의 기능을 사용하여 요소를 <xref:System.Xml.XmlWriter>에 쓰는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-113">Another approach is to create an <xref:System.Xml.XmlWriter>, and use the capabilities of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="1a20f-114">이 항목에서는 두 방법을 모두 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-114">This topic demonstrates both approaches.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a20f-115">예제</span><span class="sxs-lookup"><span data-stu-id="1a20f-115">Example</span></span>  
 <span data-ttu-id="1a20f-116">다음 예제는 [헤더 정보에 액세스하여 XML 조각을 스트리밍하는 방법(C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md)의 예제를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-116">The following example builds on the example in [How to stream XML fragments with access to header information (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>
  
 <span data-ttu-id="1a20f-117">이 예제에서는 <xref:System.Xml.Linq.XStreamingElement>의 지연된 실행 기능을 사용하여 출력을 스트림합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-117">This example uses the deferred execution capabilities of <xref:System.Xml.Linq.XStreamingElement> to stream the output.</span></span> <span data-ttu-id="1a20f-118">이 예제에서는 작은 메모리 사용 공간을 유지하면서도 매우 큰 문서를 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-118">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="1a20f-119">사용자 지정 축(`StreamCustomerItem`)은 문서에 `Customer`, `Name` 및 `Item` 요소가 있고 이러한 요소가 다음 Source.xml 문서의 경우와 마찬가지로 정렬되어 있다고 가정하고 작성된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-119">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="1a20f-120">그러나 더욱 강력한 구현은 잘못된 문서의 구문을 분석할 준비가 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-120">A more robust implementation, however, would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="1a20f-121">다음은 소스 문서인 Source.xml입니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-121">The following is the source document, Source.xml:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>
<Root>  
  <Customer>  
    <Name>A. Datum Corporation</Name>  
    <Item>  
      <Key>0001</Key>  
    </Item>  
    <Item>  
      <Key>0002</Key>  
    </Item>  
    <Item>  
      <Key>0003</Key>  
    </Item>  
    <Item>  
      <Key>0004</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Fabrikam, Inc.</Name>  
    <Item>  
      <Key>0005</Key>  
    </Item>  
    <Item>  
      <Key>0006</Key>  
    </Item>  
    <Item>  
      <Key>0007</Key>  
    </Item>  
    <Item>  
      <Key>0008</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Southridge Video</Name>  
    <Item>  
      <Key>0009</Key>  
    </Item>  
    <Item>  
      <Key>0010</Key>  
    </Item>  
  </Customer>  
</Root>  
```  
  
```csharp  
static IEnumerable<XElement> StreamCustomerItem(string uri)  
{  
    using (XmlReader reader = XmlReader.Create(uri))  
    {  
        XElement name = null;  
        XElement item = null;  
  
        reader.MoveToContent();  
  
        // Parse the file, save header information when encountered, and yield the  
        // Item XElement objects as they are created.  
  
        // loop through Customer elements  
        while (reader.Read())  
        {  
            if (reader.NodeType == XmlNodeType.Element  
                && reader.Name == "Customer")  
            {  
                // move to Name element  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.Element &&  
                        reader.Name == "Name")  
                    {  
                        name = XElement.ReadFrom(reader) as XElement;  
                        break;  
                    }  
                }  
  
                // loop through Item elements  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.EndElement)  
                        break;  
                    if (reader.NodeType == XmlNodeType.Element  
                        && reader.Name == "Item")  
                    {  
                        item = XElement.ReadFrom(reader) as XElement;  
                        if (item != null)  
                        {  
                            XElement tempRoot = new XElement("Root",  
                                new XElement(name)  
                            );  
                            tempRoot.Add(item);  
                            yield return item;  
                        }  
                    }  
                }  
            }  
        }  
    }  
}  
  
static void Main(string[] args)  
{  
    XStreamingElement root = new XStreamingElement("Root",  
        from el in StreamCustomerItem("Source.xml")  
        select new XElement("Item",  
            new XElement("Customer", (string)el.Parent.Element("Name")),  
            new XElement(el.Element("Key"))  
        )  
    );  
    root.Save("Test.xml");  
    Console.WriteLine(File.ReadAllText("Test.xml"));  
}  
```  
  
 <span data-ttu-id="1a20f-122">이 코드의 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-122">This code produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0001</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0002</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0003</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0004</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0005</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0006</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0007</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0008</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0009</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0010</Key>  
  </Item>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="1a20f-123">예제</span><span class="sxs-lookup"><span data-stu-id="1a20f-123">Example</span></span>  
<span data-ttu-id="1a20f-124">다음 예제도 [헤더 정보에 액세스하여 XML 조각을 스트리밍하는 방법(C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md)의 예제를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-124">The following example also builds on the example in [How to stream XML fragments with access to header information (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>
  
 <span data-ttu-id="1a20f-125">이 예제에서는 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]의 기능을 사용하여 요소를 <xref:System.Xml.XmlWriter>에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-125">This example uses the capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="1a20f-126">이 예제에서는 작은 메모리 사용 공간을 유지하면서도 매우 큰 문서를 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-126">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="1a20f-127">사용자 지정 축(`StreamCustomerItem`)은 문서에 `Customer`, `Name` 및 `Item` 요소가 있고 이러한 요소가 다음 Source.xml 문서의 경우와 마찬가지로 정렬되어 있다고 가정하고 작성된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-127">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="1a20f-128">그러나 더욱 강력한 구현은 XSD를 사용하여 소스 문서의 유효성을 검사하거나, 잘못된 문서의 구문을 분석할 준비가 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-128">A more robust implementation, however, would either validate the source document with an XSD, or would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="1a20f-129">이 예제에서는 이 항목의 이전 예제와 동일한 소스 문서인 Source.xml을 사용하고</span><span class="sxs-lookup"><span data-stu-id="1a20f-129">This example uses the same source document, Source.xml, as the previous example in this topic.</span></span> <span data-ttu-id="1a20f-130">똑같은 출력을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-130">It also produces exactly the same output.</span></span>  
  
 <span data-ttu-id="1a20f-131"><xref:System.Xml.Linq.XStreamingElement>를 사용하여 출력 XML을 스트림하는 것이 <xref:System.Xml.XmlWriter>에 쓰는 것보다 좋은 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-131">Using <xref:System.Xml.Linq.XStreamingElement> for streaming the output XML is preferred over writing to an <xref:System.Xml.XmlWriter>.</span></span>  
  
```csharp  
static IEnumerable<XElement> StreamCustomerItem(string uri)  
{  
    using (XmlReader reader = XmlReader.Create(uri))  
    {  
        XElement name = null;  
        XElement item = null;  
  
        reader.MoveToContent();  
  
        // Parse the file, save header information when encountered, and yield the  
        // Item XElement objects as they are created.  
  
        // loop through Customer elements  
        while (reader.Read())  
        {  
            if (reader.NodeType == XmlNodeType.Element  
                && reader.Name == "Customer")  
            {  
                // move to Name element  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.Element &&  
                        reader.Name == "Name")  
                    {  
                        name = XElement.ReadFrom(reader) as XElement;  
                        break;  
                    }  
                }  
  
                // loop through Item elements  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.EndElement)  
                        break;  
                    if (reader.NodeType == XmlNodeType.Element  
                        && reader.Name == "Item")  
                    {  
                        item = XElement.ReadFrom(reader) as XElement;  
                        if (item != null) {  
                            XElement tempRoot = new XElement("Root",  
                                new XElement(name)  
                            );  
                            tempRoot.Add(item);  
                            yield return item;  
                        }  
                    }  
                }  
            }  
        }  
    }  
}  
  
static void Main(string[] args)  
{  
    IEnumerable<XElement> srcTree =  
        from el in StreamCustomerItem("Source.xml")  
        select new XElement("Item",  
            new XElement("Customer", (string)el.Parent.Element("Name")),  
            new XElement(el.Element("Key"))  
        );  
    XmlWriterSettings xws = new XmlWriterSettings();  
    xws.OmitXmlDeclaration = true;  
    xws.Indent = true;  
    using (XmlWriter xw = XmlWriter.Create("Output.xml", xws)) {  
        xw.WriteStartElement("Root");  
        foreach (XElement el in srcTree)  
            el.WriteTo(xw);  
        xw.WriteEndElement();  
    }  
  
    string str = File.ReadAllText("Output.xml");  
    Console.WriteLine(str);  
}  
```  
  
 <span data-ttu-id="1a20f-132">이 코드의 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-132">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0001</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0002</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0003</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0004</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0005</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0006</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0007</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0008</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0009</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0010</Key>  
  </Item>  
</Root>  
```  
  