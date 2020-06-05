---
title: Visual Basic2의 XML 리터럴 소개
ms.date: 07/20/2015
ms.assetid: 94fc0e03-978e-4c08-ab6c-0dc3c1e64f10
ms.openlocfilehash: 8b92d22727c50274d57a5e407a0ca42807de3a94
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397586"
---
# <a name="introduction-to-xml-literals-in-visual-basic"></a><span data-ttu-id="00589-102">Visual Basic의 XML 리터럴 소개</span><span class="sxs-lookup"><span data-stu-id="00589-102">Introduction to XML Literals in Visual Basic</span></span>
<span data-ttu-id="00589-103">이 섹션에서는 Visual Basic에서 XML 트리를 만드는 방법에 대 한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="00589-103">This section provides information about creating XML trees in Visual Basic.</span></span>  
  
 <span data-ttu-id="00589-104">LINQ 쿼리의 결과를 XML 트리의 콘텐츠로 사용 하는 방법에 대 한 자세한 내용은 [함수 생성 (LINQ to XML) (Visual Basic)](functional-construction-linq-to-xml.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="00589-104">For information about using the results of LINQ queries as the content for an XML tree, see [Functional Construction (LINQ to XML) (Visual Basic)](functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="00589-105">Visual Basic의 XML 리터럴에 대 한 자세한 내용은 Visual Basic의 [LINQ to XML 개요](../../language-features/xml/overview-of-linq-to-xml.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="00589-105">For more information on XML literals in Visual Basic, see [Overview of LINQ to XML in Visual Basic](../../language-features/xml/overview-of-linq-to-xml.md).</span></span>  
  
## <a name="creating-xml-trees"></a><span data-ttu-id="00589-106">XML 트리 만들기</span><span class="sxs-lookup"><span data-stu-id="00589-106">Creating XML Trees</span></span>  
 <span data-ttu-id="00589-107">다음 예제에서는 <xref:System.Xml.Linq.XElement>(이 경우에는 `contacts`)를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="00589-107">The following example shows how to create an <xref:System.Xml.Linq.XElement>, in this case `contacts`:</span></span>  
  
```vb  
Dim contacts As XElement = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone>206-555-0144</Phone>  
            <Address>  
                <Street1>123 Main St</Street1>  
                <City>Mercer Island</City>  
                <State>WA</State>  
                <Postal>68042</Postal>  
            </Address>  
        </Contact>  
    </Contacts>  
```  
  
### <a name="creating-an-xelement-with-simple-content"></a><span data-ttu-id="00589-108">단순 내용을 사용하여 XElement 만들기</span><span class="sxs-lookup"><span data-stu-id="00589-108">Creating an XElement with Simple Content</span></span>  
 <span data-ttu-id="00589-109">다음과 같이 단순 내용이 포함된 <xref:System.Xml.Linq.XElement>를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00589-109">You can create an <xref:System.Xml.Linq.XElement> that contains simple content, as follows:</span></span>  
  
```vb  
Dim n as XElement = <Customer>Adventure Works</Customer>  
Console.WriteLine(n)
```  
  
 <span data-ttu-id="00589-110">이 예제는 다음과 같은 출력을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="00589-110">This example produces the following output:</span></span>  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
### <a name="creating-an-empty-element"></a><span data-ttu-id="00589-111">빈 요소 만들기</span><span class="sxs-lookup"><span data-stu-id="00589-111">Creating an Empty Element</span></span>  
 <span data-ttu-id="00589-112">다음과 같이 빈 <xref:System.Xml.Linq.XElement>를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00589-112">You can create an empty <xref:System.Xml.Linq.XElement>, as follows:</span></span>  
  
```vb  
Dim n As XElement = <Customer/>  
Console.WriteLine(n)  
```  
  
 <span data-ttu-id="00589-113">이 예제는 다음과 같은 출력을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="00589-113">This example produces the following output:</span></span>  
  
```xml  
<Customer />  
```  
  
### <a name="using-embedded-expressions"></a><span data-ttu-id="00589-114">포함 식 사용</span><span class="sxs-lookup"><span data-stu-id="00589-114">Using Embedded Expressions</span></span>  
 <span data-ttu-id="00589-115">XML 리터럴의 중요한 특징은 포함 식을 허용한다는 점입니다.</span><span class="sxs-lookup"><span data-stu-id="00589-115">An important feature of XML literals is that they allow embedded expressions.</span></span> <span data-ttu-id="00589-116">포함 식을 통해 식을 계산하고 식의 결과를 XML 트리에 삽입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00589-116">Embedded expressions enable you to evaluate an expression and insert the results of the expression into the XML tree.</span></span> <span data-ttu-id="00589-117">식이 <xref:System.Xml.Linq.XElement> 형식으로 계산되면 요소가 트리에 삽입되고,</span><span class="sxs-lookup"><span data-stu-id="00589-117">If the expression evaluates to a type of <xref:System.Xml.Linq.XElement>, an element is inserted into the tree.</span></span> <span data-ttu-id="00589-118">식이 <xref:System.Xml.Linq.XAttribute> 형식으로 계산되면 특성이 트리에 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="00589-118">If the expression evaluates to a type of <xref:System.Xml.Linq.XAttribute>, an attribute is inserted into the tree.</span></span> <span data-ttu-id="00589-119">유효한 경우에만 요소와 특성을 트리에 삽입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00589-119">You can insert elements and attributes into the tree only where they are valid.</span></span>  
  
 <span data-ttu-id="00589-120">단일 식만 포함 식에 들어갈 수 있는 점을 명심해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00589-120">It is important to note that only a single expression can go into an embedded expression.</span></span> <span data-ttu-id="00589-121">여러 문을 포함할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="00589-121">You cannot embed multiple statements.</span></span> <span data-ttu-id="00589-122">식이 한 줄을 넘으면 줄 연속 문자를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00589-122">If an expression extends beyond a single line, you must use the line continuation character.</span></span>  
  
 <span data-ttu-id="00589-123">포함 식을 사용하여 기존 노드(요소 포함)와 특성을 새 XML 트리에 추가하는 경우 기존 노드에 이미 부모가 있으면 노드가 복제됩니다.</span><span class="sxs-lookup"><span data-stu-id="00589-123">If you use an embedded expression to add existing nodes (including elements) and attributes to a new XML tree and if the existing nodes are already parented, the nodes are cloned.</span></span> <span data-ttu-id="00589-124">새로 복제된 노드는 새 XML 트리에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="00589-124">The newly cloned nodes are attached to the new XML tree.</span></span> <span data-ttu-id="00589-125">기존 노드에 부모가 없으면 노드가 새 XML 트리에 추가되기만 합니다.</span><span class="sxs-lookup"><span data-stu-id="00589-125">If the existing nodes are not parented, the nodes are simply attached to the new XML tree.</span></span> <span data-ttu-id="00589-126">이 항목의 마지막 예제에서는 이에 대해 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="00589-126">The last example in this topic demonstrates this.</span></span>  
  
 <span data-ttu-id="00589-127">다음 예제에서는 포함 식을 사용하여 요소를 트리에 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="00589-127">The following example uses an embedded expression to insert an element into the tree:</span></span>  
  
```vb  
xmlTree1 As XElement = _  
    <Root>  
        <Child>Contents</Child>  
    </Root>  
Dim xmlTree2 As XElement = _  
    <Root>  
        <%= xmlTree1.<Child> %>  
    </Root>  
Console.WriteLine(xmlTree2)  
```  
  
 <span data-ttu-id="00589-128">이 예제는 다음과 같은 출력을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="00589-128">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>Contents</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-content"></a><span data-ttu-id="00589-129">내용에 대해 포함 식 사용</span><span class="sxs-lookup"><span data-stu-id="00589-129">Using Embedded Expressions for Content</span></span>  
 <span data-ttu-id="00589-130">포함 식을 사용하여 요소의 내용을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00589-130">You can use an embedded expression to supply the content of an element:</span></span>  
  
```vb  
Dim str As String  
str = "Some content"  
Dim root As XElement = <Root><%= str %></Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="00589-131">이 예제는 다음과 같은 출력을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="00589-131">This example produces the following output:</span></span>  
  
```xml  
<Root>Some content</Root>  
```  
  
### <a name="using-a-linq-query-in-an-embedded-expression"></a><span data-ttu-id="00589-132">포함 식에서 LINQ 쿼리 사용</span><span class="sxs-lookup"><span data-stu-id="00589-132">Using a LINQ Query in an Embedded Expression</span></span>  
 <span data-ttu-id="00589-133">LINQ 쿼리의 결과를 요소의 내용으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00589-133">You can use the results of a LINQ query for the content of an element:</span></span>  
  
```vb  
Dim arr As Integer() = {1, 2, 3}  
  
Dim n As XElement = _  
    <Root>  
        <%= From i In arr Select <Child><%= i %></Child> %>  
    </Root>  
  
Console.WriteLine(n)  
```  
  
 <span data-ttu-id="00589-134">이 예제는 다음과 같은 출력을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="00589-134">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Child>3</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-node-names"></a><span data-ttu-id="00589-135">노드 이름에 대해 포함 식 사용</span><span class="sxs-lookup"><span data-stu-id="00589-135">Using Embedded Expressions for Node Names</span></span>  
 <span data-ttu-id="00589-136">포함 식을 사용하여 특성 이름, 특성 값, 요소 이름 및 요소 값을 계산할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00589-136">You can also use embedded expressions to calculate attribute names, attribute values, element names, and element values:</span></span>  
  
```vb  
Dim eleName As String = "ele"  
Dim attName As String = "att"  
Dim attValue As String = "aValue"  
Dim eleValue As String = "eValue"  
Dim n As XElement = _  
    <Root <%= attName %>=<%= attValue %>>  
        <<%= eleName %>>  
            <%= eleValue %>  
        </>  
    </Root>  
Console.WriteLine(n)  
```  
  
 <span data-ttu-id="00589-137">이 예제는 다음과 같은 출력을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="00589-137">This example produces the following output:</span></span>  
  
```xml  
<Root att="aValue">  
  <ele>eValue</ele>  
</Root>  
```  
  
### <a name="cloning-vs-attaching"></a><span data-ttu-id="00589-138">복제와 연결 비교</span><span class="sxs-lookup"><span data-stu-id="00589-138">Cloning vs. Attaching</span></span>  
 <span data-ttu-id="00589-139">앞에서 설명했듯이 포함 식을 사용하여 기존 노드(요소 포함)와 특성을 새 XML 트리에 추가하는 경우 기존 노드에 이미 부모가 있으면 노드가 복제되고 새로 복제된 노드가 새 XML 트리에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="00589-139">As mentioned earlier, if you use an embedded expression to add existing nodes (including elements) and attributes to a new XML tree, if the existing nodes are already parented, the nodes are cloned and the newly cloned nodes are attached to the new XML tree.</span></span> <span data-ttu-id="00589-140">기존 노드에 부모가 없으면 노드가 새 XML 트리에 추가되기만 합니다.</span><span class="sxs-lookup"><span data-stu-id="00589-140">If the existing nodes are not parented, they are simply attached to the new XML tree.</span></span>  
  
```vb  
' Create a tree with a child element.  
Dim xmlTree1 As XElement = _  
    <Root>  
        <Child1>1</Child1>  
    </Root>  
  
' Create an element that is not parented.  
Dim child2 As XElement = <Child2>2</Child2>  
  
' Create a tree and add Child1 and Child2 to it.  
Dim xmlTree2 As XElement = _  
    <Root>  
        <%= xmlTree1.<Child1>(0) %>  
        <%= child2 %>  
    </Root>  
  
' Compare Child1 identity.  
Console.WriteLine("Child1 was {0}", _  
    IIf(xmlTree1.Element("Child1") Is xmlTree2.Element("Child1"), _  
    "attached", "cloned"))  
  
' Compare Child2 identity.  
Console.WriteLine("Child2 was {0}", _  
    IIf(child2 Is xmlTree2.Element("Child2"), _  
    "attached", "cloned"))  
```  
  
 <span data-ttu-id="00589-141">이 예에서 생성되는 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="00589-141">This example produces the following output:</span></span>  
  
```console  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a><span data-ttu-id="00589-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="00589-142">See also</span></span>

- [<span data-ttu-id="00589-143">XML 트리 만들기 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="00589-143">Creating XML Trees (Visual Basic)</span></span>](creating-xml-trees.md)
