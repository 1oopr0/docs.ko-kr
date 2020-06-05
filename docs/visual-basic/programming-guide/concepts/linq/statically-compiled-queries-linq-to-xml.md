---
title: 정적으로 컴파일된 쿼리(LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 3f4825c7-c3b0-48da-ba4e-8e97fb2a2f34
ms.openlocfilehash: f020c1ed8627df8c8386a059f0cea372e8df363e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406770"
---
# <a name="statically-compiled-queries-linq-to-xml-visual-basic"></a><span data-ttu-id="470fa-102">정적으로 컴파일된 쿼리 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="470fa-102">Statically Compiled Queries (LINQ to XML) (Visual Basic)</span></span>

<span data-ttu-id="470fa-103"><xref:System.Xml.XmlDocument>와는 달리 LINQ to XML의 가장 큰 성능 이점 중 하나는 LINQ to XML의 쿼리가 정적으로 컴파일된다는 점입니다. 반면 XPath 쿼리는 런타임에 해석되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="470fa-103">One of the most important performance benefits LINQ to XML, as opposed to <xref:System.Xml.XmlDocument>, is that queries in LINQ to XML are statically compiled, whereas XPath queries must be interpreted at run time.</span></span> <span data-ttu-id="470fa-104">이 기능은 LINQ to XML에 기본 제공되므로 이를 활용하기 위해 별도의 단계를 수행할 필요는 없습니다. 그러나 이 두 가지 기술 중 하나를 선택해야 하는 경우를 위해 그 차이를 알고 있는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="470fa-104">This feature is built in to LINQ to XML, so you do not have to perform extra steps to take advantage of it, but it is helpful to understand the distinction when choosing between the two technologies.</span></span> <span data-ttu-id="470fa-105">이 항목에서는 그 차이에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="470fa-105">This topic explains the difference.</span></span>

## <a name="statically-compiled-queries-vs-xpath"></a><span data-ttu-id="470fa-106">정적으로 컴파일된 쿼리와 XPath 비교</span><span class="sxs-lookup"><span data-stu-id="470fa-106">Statically Compiled Queries vs. XPath</span></span>

<span data-ttu-id="470fa-107">다음 예제에서는 지정된 이름을 가진 하위 요소와 지정된 값을 가진 특성이 포함된 하위 요소를 가져오는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="470fa-107">The following example shows how to get the descendant elements with a specified name, and with an attribute with a specified value.</span></span>

<span data-ttu-id="470fa-108">다음은 이에 해당하는 XPath 식입니다.</span><span class="sxs-lookup"><span data-stu-id="470fa-108">The following is the equivalent XPath expression:</span></span>

```vb
//Address[@Type='Shipping']
```

```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 = From el In po.Descendants("Address")
            Where el.@Type = "Shipping"

For Each el In list1
    Console.WriteLine(el)
Next
```

<span data-ttu-id="470fa-109">이 예제의 쿼리 식은 메서드 기반 쿼리 구문에 대한 컴파일러로 다시 작성되었습니다.</span><span class="sxs-lookup"><span data-stu-id="470fa-109">The query expression in this example is re-written by the compiler to method-based query syntax.</span></span> <span data-ttu-id="470fa-110">메서드 기반 쿼리 구문으로 작성된 다음 예제는 이전 쿼리에서와 같은 결과를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="470fa-110">The following example, which is written in method-based query syntax, produces the same results as the previous one:</span></span>

```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 As IEnumerable(Of XElement) = po.Descendants("Address").Where(Function(el) el.@Type = "Shipping")

For Each el In list1
    Console.WriteLine(el)
Next
```

<span data-ttu-id="470fa-111"><xref:System.Linq.Enumerable.Where%2A> 메서드는 확장 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="470fa-111">The <xref:System.Linq.Enumerable.Where%2A> method is an extension method.</span></span> <span data-ttu-id="470fa-112">자세한 내용은 [확장 메서드](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="470fa-112">For more information, see [Extension Methods](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="470fa-113"><xref:System.Linq.Enumerable.Where%2A>은 확장 메서드입니다. 위 쿼리는 다음과 같이 작성된 것처럼 컴파일됩니다.</span><span class="sxs-lookup"><span data-stu-id="470fa-113">Because <xref:System.Linq.Enumerable.Where%2A> is an extension method, the query above is compiled as though it were written as follows:</span></span>

```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 = Enumerable.Where(po.Descendants("Address"), Function(el) el.@Type = "Shipping")

For Each el In list1
    Console.WriteLine(el)
Next
```

<span data-ttu-id="470fa-114">이 예제의 결과는 위의 두 예제의 결과와 정확히 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="470fa-114">This example produces exactly the same results as the previous two examples.</span></span> <span data-ttu-id="470fa-115">이를 통해 쿼리가 정적으로 연결된 메서드 호출로 효과적으로 컴파일되었음을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="470fa-115">This illustrates the fact that queries are effectively compiled into statically linked method calls.</span></span> <span data-ttu-id="470fa-116">이 예제에서는 반복기의 지연된 실행 의미 체계를 결합하여 성능을 향상합니다.</span><span class="sxs-lookup"><span data-stu-id="470fa-116">This, combined with the deferred execution semantics of iterators, improves performance.</span></span> <span data-ttu-id="470fa-117">반복기의 지연 된 실행 의미 체계에 대 한 자세한 내용은 [LINQ to XML (Visual Basic)에서 지연 된 실행 및 지연 계산](deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="470fa-117">For more information about the deferred execution semantics of iterators, see [Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)](deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>

> [!NOTE]
> <span data-ttu-id="470fa-118">이러한 예제는 컴파일러에서 작성할 수 있는 대표적인 코드 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="470fa-118">These examples are representative of the code that the compiler might write.</span></span> <span data-ttu-id="470fa-119">실제 구현은 이러한 예제와 약간 다를 수 있으나 성능은 이러한 예제와 같거나 매우 유사할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="470fa-119">The actual implementation might differ slightly from these examples, but the performance will be the same or similar to these examples.</span></span>

## <a name="executing-xpath-expressions-with-xmldocument"></a><span data-ttu-id="470fa-120">XmlDocument를 사용하여 XPath 식 실행</span><span class="sxs-lookup"><span data-stu-id="470fa-120">Executing XPath Expressions with XmlDocument</span></span>

<span data-ttu-id="470fa-121">다음 예제에서는 <xref:System.Xml.XmlDocument>를 사용하여 위의 예제와 같은 결과를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="470fa-121">The following example uses <xref:System.Xml.XmlDocument> to accomplish the same results as the previous examples:</span></span>

```vb
Dim reader = Xml.XmlReader.Create("PurchaseOrders.xml")
Dim doc As New Xml.XmlDocument()
doc.Load(reader)
Dim nl As Xml.XmlNodeList = doc.SelectNodes(".//Address[@Type='Shipping']")
For Each n As Xml.XmlNode In nl
    Console.WriteLine(n.OuterXml)
Next
reader.Close()
```

<span data-ttu-id="470fa-122">이 쿼리에서는 LINQ to XML을 사용하는 예제와 같은 결과를 반환합니다. LINQ to XML에서는 출력되는 XML을 들여쓰지만 <xref:System.Xml.XmlDocument>는 들여쓰지 않는다는 점만 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="470fa-122">This query returns the same output as the examples that use LINQ to XML; the only difference is that LINQ to XML indents the printed XML, whereas <xref:System.Xml.XmlDocument> does not.</span></span>

<span data-ttu-id="470fa-123">그러나 <xref:System.Xml.XmlDocument> 메서드는 호출될 때마다 내부적으로 다음을 수행해야 하므로 <xref:System.Xml.XmlNode.SelectNodes%2A>는 일반적으로 LINQ to XML과 같이 효과적으로 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="470fa-123">However, the <xref:System.Xml.XmlDocument> approach generally does not perform as well as LINQ to XML, because the <xref:System.Xml.XmlNode.SelectNodes%2A> method must do the following internally every time it is called:</span></span>

- <span data-ttu-id="470fa-124">XPath 식이 포함된 문자열을 구문 분석하여 문자열을 토큰으로 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="470fa-124">It parses the string that contains the XPath expression, breaking the string into tokens.</span></span>

- <span data-ttu-id="470fa-125">XPath 식이 올바른지 확인하기 위해 토큰의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="470fa-125">It validates the tokens to make sure that the XPath expression is valid.</span></span>

- <span data-ttu-id="470fa-126">식을 내부 식 트리로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="470fa-126">It translates the expression into an internal expression tree.</span></span>

- <span data-ttu-id="470fa-127">노드를 반복하여 식 계산 결과를 기준으로 결과 집합에 맞는 노드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="470fa-127">It iterates through the nodes, appropriately selecting the nodes for the result set based on the evaluation of the expression.</span></span>

<span data-ttu-id="470fa-128">이는 이에 해당하는 LINQ to XML 쿼리에서 수행하는 작업보다 훨씬 많습니다.</span><span class="sxs-lookup"><span data-stu-id="470fa-128">This is significantly more than the work done by the corresponding LINQ to XML query.</span></span> <span data-ttu-id="470fa-129">구체적인 성능 차이는 쿼리 형식에 따라 다르지만 일반 LINQ to XML 쿼리의 경우 작업을 덜 수행하므로 <xref:System.Xml.XmlDocument>를 사용하여 XPath 식을 계산하는 것보다 성능이 더 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="470fa-129">The specific performance difference varies for different types of queries, but in general LINQ to XML queries do less work, and therefore perform better, than evaluating XPath expressions using <xref:System.Xml.XmlDocument>.</span></span>

## <a name="see-also"></a><span data-ttu-id="470fa-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="470fa-130">See also</span></span>

- [<span data-ttu-id="470fa-131">성능 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="470fa-131">Performance (LINQ to XML) (Visual Basic)</span></span>](performance-linq-to-xml.md)
