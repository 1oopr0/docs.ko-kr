---
title: 헤더 정보에 액세스하여 XML 조각을 스트리밍하는 방법(C#)
description: 헤더 정보에 액세스하여 XML 조각을 스트리밍하는 방법을 알아봅니다. 스트리밍 기술은 과도한 메모리 사용을 방지하는 데 도움이 됩니다.
ms.date: 07/20/2015
ms.assetid: 7f242770-b0c7-418d-894b-643215e1f8aa
ms.openlocfilehash: 8bfded96ea1fa6b096d56ae0736002b9062d58b6
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303220"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-c"></a><span data-ttu-id="f6342-104">헤더 정보에 액세스하여 XML 조각을 스트리밍하는 방법(C#)</span><span class="sxs-lookup"><span data-stu-id="f6342-104">How to stream XML fragments with access to header information (C#)</span></span>
<span data-ttu-id="f6342-105">예상할 수 없는 큰 크기의 XML 파일을 읽고 애플리케이션의 메모리 사용 공간이 예상 가능하도록 애플리케이션을 작성해야 하는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6342-105">Sometimes you have to read arbitrarily large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="f6342-106">XML 트리를 큰 XML 파일로 채우려는 경우 파일 크기에 비례하여 메모리가 사용되므로 메모리 사용량이 지나치게 증가하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6342-106">If you attempt to populate an XML tree with a large XML file, your memory usage will be proportional to the size of the file—that is, excessive.</span></span> <span data-ttu-id="f6342-107">따라서 스트리밍 기법을 대신 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6342-107">Therefore, you should use a streaming technique instead.</span></span>  
  
<span data-ttu-id="f6342-108">한 가지 방법은 <xref:System.Xml.XmlReader>를 사용하여 애플리케이션을 작성하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f6342-108">One option is to write your application using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="f6342-109">그러나 LINQ를 사용하여 XML 트리를 쿼리할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6342-109">However, you might want to use LINQ to query the XML tree.</span></span> <span data-ttu-id="f6342-110">이 경우에는 사용자 지정 축 메서드를 직접 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6342-110">If this is the case, you can write your own custom axis method.</span></span> <span data-ttu-id="f6342-111">자세한 내용은 [LINQ to XML 축 메서드를 작성하는 방법(C#)](./how-to-write-a-linq-to-xml-axis-method.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f6342-111">For more information, see [How to write a LINQ to XML axis method (C#)](./how-to-write-a-linq-to-xml-axis-method.md).</span></span>
  
 <span data-ttu-id="f6342-112">축 메서드를 직접 작성하려면 <xref:System.Xml.XmlReader>를 사용하여 관심이 있는 노드 중 하나에 도달할 때까지 노드를 읽는 작은 메서드를 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6342-112">To write your own axis method, you write a small method that uses the <xref:System.Xml.XmlReader> to read nodes until it reaches one of the nodes in which you are interested.</span></span> <span data-ttu-id="f6342-113">이 메서드는 <xref:System.Xml.Linq.XNode.ReadFrom%2A>에서 읽고 XML 조각을 인스턴스화하는 <xref:System.Xml.XmlReader>을 호출한 후</span><span class="sxs-lookup"><span data-stu-id="f6342-113">The method then calls <xref:System.Xml.Linq.XNode.ReadFrom%2A>, which reads from the <xref:System.Xml.XmlReader> and instantiates an XML fragment.</span></span> <span data-ttu-id="f6342-114">`yield return`을 통해 각 조각을 사용자 지정 축 메서드를 열거하는 메서드에 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="f6342-114">It then yields each fragment through `yield return` to the method that is enumerating your custom axis method.</span></span> <span data-ttu-id="f6342-115">그런 다음 사용자 지정 축 메서드에 대한 LINQ 쿼리를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6342-115">You can then write LINQ queries on your custom axis method.</span></span>  
  
 <span data-ttu-id="f6342-116">스트리밍 기법은 소스 문서를 한 번만 처리해야 하고 문서 순서의 요소를 처리할 수 있는 경우에 가장 효과적으로 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6342-116">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="f6342-117"><xref:System.Linq.Enumerable.OrderBy%2A>와 같은 특정 표준 쿼리 연산자는 자신의 소스를 반복하고 모든 데이터를 수집하여 정렬한 다음 시퀀스의 첫 번째 항목을 최종적으로 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="f6342-117">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="f6342-118">첫 번째 항목을 생성하기 전에 소스를 구체화하는 쿼리 연산자를 사용하는 경우 작은 메모리 사용 공간이 유지되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f6342-118">If you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6342-119">예제</span><span class="sxs-lookup"><span data-stu-id="f6342-119">Example</span></span>  

<span data-ttu-id="f6342-120">좀 더 흥미로운 문제가 발생하는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6342-120">Sometimes the problem gets just a little more interesting.</span></span> <span data-ttu-id="f6342-121">다음 XML 문서에서 사용자 지정 축 메서드의 소비자는 각 항목을 소유하는 고객의 이름도 알아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6342-121">In the following XML document, the consumer of your custom axis method also has to know the name of the customer that each item belongs to.</span></span>  
  
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
  
 <span data-ttu-id="f6342-122">이 예제에서 사용하는 방법은 이 헤더 정보를 확인하고 저장한 다음 헤더 정보와 열거하고 있는 세부 정보를 모두 포함하는 작은 XML 트리를 빌드하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f6342-122">The approach that this example takes is to also watch for this header information, save the header information, and then build a small XML tree that contains both the header information and the detail that you are enumerating.</span></span> <span data-ttu-id="f6342-123">축 메서드는 이 새로운 작은 XML 트리를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="f6342-123">The axis method then yields this new, small XML tree.</span></span> <span data-ttu-id="f6342-124">이 경우 쿼리는 세부 정보뿐만 아니라 헤더 정보에도 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6342-124">The query then has access to the header information as well as the detail information.</span></span>  
  
 <span data-ttu-id="f6342-125">이 방법에서는 작은 메모리 공간이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6342-125">This approach has a small memory footprint.</span></span> <span data-ttu-id="f6342-126">각 세부 XML 조각이 생성될 때 이전 조각에 대한 참조는 유지되지 않으며 가비지 수집에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6342-126">As each detail XML fragment is yielded, no references are kept to the previous fragment, and it is available for garbage collection.</span></span> <span data-ttu-id="f6342-127">이 기법을 사용하면 힙에 수명이 짧은 개체가 많이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="f6342-127">This technique creates many short lived objects on the heap.</span></span>  
  
 <span data-ttu-id="f6342-128">다음 예제에서는 URI로 지정된 파일에서 XML 조각을 스트림하는 사용자 지정 축 메서드를 구현하고 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f6342-128">The following example shows how to implement and use a custom axis method that streams XML fragments from the file specified by the URI.</span></span> <span data-ttu-id="f6342-129">이 사용자 지정 축은 문서에 `Customer`, `Name` 및 `Item` 요소가 있고 이러한 요소가 위에 있는 `Source.xml` 문서의 경우와 마찬가지로 정렬되어 있다고 가정하고 작성된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f6342-129">This custom axis is written such that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the above `Source.xml` document.</span></span> <span data-ttu-id="f6342-130">이것은 매우 단순화된 구현입니다.</span><span class="sxs-lookup"><span data-stu-id="f6342-130">It is a simplistic implementation.</span></span> <span data-ttu-id="f6342-131">더욱 강력한 구현은 잘못된 문서의 구문을 분석할 준비가 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6342-131">A more robust implementation would be prepared to parse an invalid document.</span></span>  
  
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
    XElement xmlTree = new XElement("Root",  
        from el in StreamCustomerItem("Source.xml")  
        where (int)el.Element("Key") >= 3 && (int)el.Element("Key") <= 7  
        select new XElement("Item",  
            new XElement("Customer", (string)el.Parent.Element("Name")),  
            new XElement(el.Element("Key"))  
        )  
    );  
    Console.WriteLine(xmlTree);  
}  
```  
  
 <span data-ttu-id="f6342-132">이 코드의 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f6342-132">This code produces the following output:</span></span>  
  
```xml  
<Root>  
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
</Root>  
```  
