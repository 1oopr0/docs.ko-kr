---
title: XmlReader에서 XML 조각을 스트리밍하는 방법(C#)
description: XmlReader에서 XML 조각을 스트리밍하는 방법을 알아봅니다. 이 방법은 대량 XML 파일을 처리하는 데 사용됩니다.
ms.date: 07/20/2015
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
ms.openlocfilehash: e35322724712816180d48c1957719cf87079aedd
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301023"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a><span data-ttu-id="770a2-104">XmlReader에서 XML 조각을 스트리밍하는 방법(C#)</span><span class="sxs-lookup"><span data-stu-id="770a2-104">How to stream XML fragments from an XmlReader (C#)</span></span>

<span data-ttu-id="770a2-105">큰 XML 파일을 처리해야 하는 경우 전체 XML 트리를 메모리에 로드하는 것이 가능하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="770a2-105">When you have to process large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="770a2-106">이 항목에서는 <xref:System.Xml.XmlReader>를 사용하여 조각을 스트림하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="770a2-106">This topic shows how to stream fragments using an <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="770a2-107"><xref:System.Xml.XmlReader>를 사용하여 <xref:System.Xml.Linq.XElement> 개체를 읽는 가장 효과적인 방법 중 하나는 사용자 지정 축 메서드를 직접 작성하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="770a2-107">One of the most effective ways to use an <xref:System.Xml.XmlReader> to read <xref:System.Xml.Linq.XElement> objects is to write your own custom axis method.</span></span> <span data-ttu-id="770a2-108">일반적으로 축 메서드는 이 항목의 예제에 나와 있는 대로 <xref:System.Collections.Generic.IEnumerable%601>의 <xref:System.Xml.Linq.XElement>과 같은 컬렉션을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="770a2-108">An axis method typically returns a collection such as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, as shown in the example in this topic.</span></span> <span data-ttu-id="770a2-109">사용자 지정 축 메서드에서는 <xref:System.Xml.Linq.XNode.ReadFrom%2A> 메서드를 호출하여 XML 조각을 만든 후 `yield return`을 사용하여 컬렉션을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="770a2-109">In the custom axis method, after you create the XML fragment by calling the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method, return the collection using `yield return`.</span></span> <span data-ttu-id="770a2-110">이것은 사용자 지정 축 메서드에 지연된 실행 의미를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="770a2-110">This provides deferred execution semantics to your custom axis method.</span></span>  
  
 <span data-ttu-id="770a2-111"><xref:System.Xml.XmlReader> 개체에서 XML 트리를 만드는 경우 <xref:System.Xml.XmlReader>가 요소에 배치되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="770a2-111">When you create an XML tree from an <xref:System.Xml.XmlReader> object, the <xref:System.Xml.XmlReader> must be positioned on an element.</span></span> <span data-ttu-id="770a2-112"><xref:System.Xml.Linq.XNode.ReadFrom%2A> 메서드는 요소의 닫는 태그를 읽을 때까지 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="770a2-112">The <xref:System.Xml.Linq.XNode.ReadFrom%2A> method does not return until it has read the close tag of the element.</span></span>  
  
 <span data-ttu-id="770a2-113">부분 트리를 만들려는 경우 <xref:System.Xml.XmlReader>를 인스턴스화하고 <xref:System.Xml.Linq.XElement> 트리로 변환할 노드에 판독기를 배치한 다음 <xref:System.Xml.Linq.XElement> 개체를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="770a2-113">If you want to create a partial tree, you can instantiate an <xref:System.Xml.XmlReader>, position the reader on the node that you want to convert to an <xref:System.Xml.Linq.XElement> tree, and then create the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
<span data-ttu-id="770a2-114">[헤더 정보에 액세스하여 XML 조각을 스트리밍하는 방법(C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md) 항목에는 더 복잡한 문서를 스트림하는 방법에 대한 정보와 예제가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="770a2-114">The topic [How to stream XML fragments with access to header information (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md) contains information and an example on how to stream a more complex document.</span></span>
  
 <span data-ttu-id="770a2-115">[큰 XML 문서의 스트리밍 변환을 수행하는 방법(C#)](./how-to-perform-streaming-transform-of-large-xml-documents.md) 항목에는 LINQ to XML을 사용하여 작은 메모리 사용 공간을 유지하면서 매우 큰 XML 문서를 변환하는 예제가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="770a2-115">The topic [How to perform streaming transform of large XML documents (C#)](./how-to-perform-streaming-transform-of-large-xml-documents.md) contains an example of using LINQ to XML to transform extremely large XML documents while maintaining a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="770a2-116">예제</span><span class="sxs-lookup"><span data-stu-id="770a2-116">Example</span></span>  
 <span data-ttu-id="770a2-117">이 예제에서는 사용자 지정 축 메서드를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="770a2-117">This example creates a custom axis method.</span></span> <span data-ttu-id="770a2-118">LINQ 쿼리를 사용하여 이 메서드를 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="770a2-118">You can query it by using a LINQ query.</span></span> <span data-ttu-id="770a2-119">사용자 지정 축 메서드 `StreamRootChildDoc`는 반복되는 `Child` 요소가 있는 문서를 읽도록 특정하게 디자인된 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="770a2-119">The custom axis method, `StreamRootChildDoc`, is a method that is designed specifically to read a document that has a repeating `Child` element.</span></span>  
  
```csharp  
static IEnumerable<XElement> StreamRootChildDoc(StringReader stringReader)  
{  
    using (XmlReader reader = XmlReader.Create(stringReader))  
    {  
        reader.MoveToContent();  
        // Parse the file and display each of the nodes.  
        while (reader.Read())  
        {  
            switch (reader.NodeType)  
            {  
                case XmlNodeType.Element:  
                    if (reader.Name == "Child") {  
                        XElement el = XElement.ReadFrom(reader) as XElement;  
                        if (el != null)  
                            yield return el;  
                    }  
                    break;  
            }  
        }  
    }  
}  
  
static void Main(string[] args)  
{  
    string markup = @"<Root>  
      <Child Key=""01"">  
        <GrandChild>aaa</GrandChild>  
      </Child>  
      <Child Key=""02"">  
        <GrandChild>bbb</GrandChild>  
      </Child>  
      <Child Key=""03"">  
        <GrandChild>ccc</GrandChild>  
      </Child>  
    </Root>";  
  
    IEnumerable<string> grandChildData =  
        from el in StreamRootChildDoc(new StringReader(markup))  
        where (int)el.Attribute("Key") > 1  
        select (string)el.Element("GrandChild");  
  
    foreach (string str in grandChildData) {  
        Console.WriteLine(str);  
    }  
}  
```  
  
 <span data-ttu-id="770a2-120">이 예제는 다음과 같은 출력을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="770a2-120">This example produces the following output:</span></span>  
  
```output  
bbb  
ccc  
```  
  
 <span data-ttu-id="770a2-121">이 예제의 소스 문서는 매우 작습니다.</span><span class="sxs-lookup"><span data-stu-id="770a2-121">In this example, the source document is very small.</span></span> <span data-ttu-id="770a2-122">`Child` 요소가 수백만 있더라도 이 예제에서는 여전히 작은 메모리 공간만 사용할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="770a2-122">However, even if there were millions of `Child` elements, this example would still have a small memory footprint.</span></span>  
