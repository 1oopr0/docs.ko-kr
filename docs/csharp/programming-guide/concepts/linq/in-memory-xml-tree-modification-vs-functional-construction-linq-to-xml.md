---
title: 메모리 내 XML 트리 수정과 함수 생성(LINQ to XML)(C#)
description: 이러한 예제에서는 XML 문서를 현재 위치에서 수정하고 C#에서 LINQ to XML 함수 생성을 사용하여 XML 문서의 모양을 변경합니다.
ms.date: 07/20/2015
ms.assetid: b5afc31d-a325-4ec6-bf17-0ff90a20ffca
ms.openlocfilehash: 7a2e3d2ddcd452cf6a58e9d5cc886f3e8b8dd325
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165783"
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml-c"></a><span data-ttu-id="bca33-103">메모리 내 XML 트리 수정과 함수 생성(LINQ to XML)(C#)</span><span class="sxs-lookup"><span data-stu-id="bca33-103">In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (C#)</span></span>
<span data-ttu-id="bca33-104">메모리 내 XML 트리 수정은 XML 문서의 모양을 변경하는 일반적인 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="bca33-104">Modifying an XML tree in place is a traditional approach to changing the shape of an XML document.</span></span> <span data-ttu-id="bca33-105">일반적인 애플리케이션에서는 문서를 DOM 또는 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]과 같은 데이터 저장소로 로드하고 프로그래밍 인터페이스를 사용하여 노드를 삽입 또는 삭제하거나 노드의 내용을 변경한 다음 XML을 파일에 저장하거나 네트워크를 통해 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="bca33-105">A typical application loads a document into a data store such as DOM or [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]; uses a programming interface to insert nodes, delete nodes, or change the content of nodes; and then saves the XML to a file or transmits it over a network.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="bca33-106">에서는 대부분의 경우에 유용한 *함수 생성*이라는 다른 방법을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bca33-106">enables another approach that is useful in many scenarios: *functional construction*.</span></span> <span data-ttu-id="bca33-107">함수 생성은 데이터 수정을 데이터 저장소의 세부 조작이 아니라 변환 문제로 취급합니다.</span><span class="sxs-lookup"><span data-stu-id="bca33-107">Functional construction treats modifying data as a problem of transformation, rather than as detailed manipulation of a data store.</span></span> <span data-ttu-id="bca33-108">데이터 표현을 가져온 다음 효율적으로 한 형태에서 다른 형태로 변환할 수 있는 경우 결과는 하나의 데이터 저장소를 가져와서 다른 모양을 갖도록 조작하는 경우와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="bca33-108">If you can take a representation of data and transform it efficiently from one form to another, the result is the same as if you took one data store and manipulated it in some way to take another shape.</span></span> <span data-ttu-id="bca33-109">함수 생성 방법의 핵심은 쿼리의 결과를 <xref:System.Xml.Linq.XDocument> 및 <xref:System.Xml.Linq.XElement> 생성자에 전달하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="bca33-109">A key to the functional construction approach is to pass the results of queries to <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement> constructors.</span></span>  
  
 <span data-ttu-id="bca33-110">대부분의 경우에 데이터 저장소를 조작하는 데 걸리는 시간 내에 변환 코드를 작성할 수 있으며 해당 코드는 더욱 강력하고 유지하기 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="bca33-110">In many cases you can write the transformational code in a fraction of the time that it would take to manipulate the data store, and that code is more robust and easier to maintain.</span></span> <span data-ttu-id="bca33-111">이러한 경우에 변환 방법은 더욱 강력한 처리 능력을 필요로 할 수 있지만 데이터를 보다 효율적으로 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="bca33-111">In these cases, even though the transformational approach can take more processing power, it is a more effective way to modify data.</span></span> <span data-ttu-id="bca33-112">개발자가 함수 방법에 익숙하면 생성되는 코드를 이해하기가 더 쉬운 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="bca33-112">If a developer is familiar with the functional approach, the resulting code in many cases is easier to understand.</span></span> <span data-ttu-id="bca33-113">각 트리 부분을 수정하는 코드를 찾는 것도 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="bca33-113">It is easy to find the code that modifies each part of the tree.</span></span>  
  
 <span data-ttu-id="bca33-114">메모리 내 XML 트리를 수정하는 방법이 대부분의 DOM 프로그래머에게 익숙한 반면, 함수 방법을 사용하여 작성된 코드는 이 방법을 이해하지 못하는 개발자에게 낯설게 보일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bca33-114">The approach where you modify an XML tree in-place is more familiar to many DOM programmers, whereas code written using the functional approach might look unfamiliar to a developer who doesn't yet understand that approach.</span></span> <span data-ttu-id="bca33-115">큰 XML 트리의 적은 부분만 수정해야 하는 경우 대개 트리를 수정하는 방법이 CPU를 적게 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bca33-115">If you have to only make a small modification to a large XML tree, the approach where you modify a tree in place in many cases will take less CPU time.</span></span>  
  
 <span data-ttu-id="bca33-116">이 항목에서는 두 방법으로 구현된 예제를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bca33-116">This topic provides an example that is implemented with both approaches.</span></span>  
  
## <a name="transforming-attributes-into-elements"></a><span data-ttu-id="bca33-117">특성을 요소로 변환</span><span class="sxs-lookup"><span data-stu-id="bca33-117">Transforming Attributes into Elements</span></span>  
 <span data-ttu-id="bca33-118">이 예제에서는 특성이 요소가 되는 다음과 같은 간단한 XML 문서를 수정하려고 한다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="bca33-118">For this example, suppose you want to modify the following simple XML document so that the attributes become elements.</span></span> <span data-ttu-id="bca33-119">이 항목에서는 먼저 일반적인 메모리 내 수정 방법을 제공한 다음</span><span class="sxs-lookup"><span data-stu-id="bca33-119">This topic first presents the traditional in-place modification approach.</span></span> <span data-ttu-id="bca33-120">함수 생성 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bca33-120">It then shows the functional construction approach.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root Data1="123" Data2="456">  
  <Child1>Content</Child1>  
</Root>  
```  
  
### <a name="modifying-the-xml-tree"></a><span data-ttu-id="bca33-121">XML 트리 수정</span><span class="sxs-lookup"><span data-stu-id="bca33-121">Modifying the XML Tree</span></span>  
 <span data-ttu-id="bca33-122">특성에서 요소를 만든 다음 특성을 삭제하는 절차적 코드를 다음과 같이 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bca33-122">You can write some procedural code to create elements from the attributes, and then delete the attributes, as follows:</span></span>  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
foreach (XAttribute att in root.Attributes()) {  
    root.Add(new XElement(att.Name, (string)att));  
}  
root.Attributes().Remove();  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="bca33-123">이 코드의 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bca33-123">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>Content</Child1>  
  <Data1>123</Data1>  
  <Data2>456</Data2>  
</Root>  
```  
  
### <a name="functional-construction-approach"></a><span data-ttu-id="bca33-124">함수 생성 방법</span><span class="sxs-lookup"><span data-stu-id="bca33-124">Functional Construction Approach</span></span>  
 <span data-ttu-id="bca33-125">위의 방법과 달리, 함수 방법은 새 트리를 형성하고 소스 트리에서 요소와 특성을 선택한 다음 새 트리에 추가할 때 적절하게 변환하는 코드로 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bca33-125">By contrast, a functional approach consists of code to form a new tree, picking and choosing elements and attributes from the source tree, and transforming them as appropriate as they are added to the new tree.</span></span> <span data-ttu-id="bca33-126">함수 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bca33-126">The functional approach looks like the following:</span></span>  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
XElement newTree = new XElement("Root",  
    root.Element("Child1"),  
    from att in root.Attributes()  
    select new XElement(att.Name, (string)att)  
);  
Console.WriteLine(newTree);  
```  
  
 <span data-ttu-id="bca33-127">이 예제에서 출력되는 XML은 첫 번째 예제에서 출력되는 XML과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="bca33-127">This example outputs the same XML as the first example.</span></span> <span data-ttu-id="bca33-128">그러나 함수 방법에서는 생성되는 새 XML의 구조를 실제로 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bca33-128">However, notice that you can actually see the resulting structure of the new XML in the functional approach.</span></span> <span data-ttu-id="bca33-129">`Root` 요소의 생성, 소스 트리에서 `Child1` 요소를 가져오는 코드 및 소스 트리의 특성을 새 트리의 요소로 변환하는 코드를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bca33-129">You can see the creation of the `Root` element, the code that pulls the `Child1` element from the source tree, and the code that transforms the attributes from the source tree to elements in the new tree.</span></span>  
  
 <span data-ttu-id="bca33-130">이 경우의 함수 예제는 첫 번째 예제보다 짧지 않으며 실제로 더 간단하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bca33-130">The functional example in this case is not any shorter than the first example, and it is not really any simpler.</span></span> <span data-ttu-id="bca33-131">그러나 XML 트리를 많이 변경해야 하는 경우 함수 방법 이외의 방법은 꽤 복잡하고 다소 이해하기 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="bca33-131">However, if you have many changes to make to an XML tree, the non functional approach will become quite complex and somewhat obtuse.</span></span> <span data-ttu-id="bca33-132">이와 반대로 함수 방법을 사용할 때는 원하는 XML을 형성하고 쿼리와 식을 적절하게 포함하여 원하는 내용을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bca33-132">In contrast, when using the functional approach, you still just form the desired XML, embedding queries and expressions as appropriate, to pull in the desired content.</span></span> <span data-ttu-id="bca33-133">함수 방법은 유지 관리하기가 더 쉬운 코드를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="bca33-133">The functional approach yields code that is easier to maintain.</span></span>  
  
 <span data-ttu-id="bca33-134">이 경우 함수 방법의 성능은 트리 조작 방법의 성능보다 낮을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bca33-134">Notice that in this case the functional approach probably would not perform quite as well as the tree manipulation approach.</span></span> <span data-ttu-id="bca33-135">주요 문제는 함수 방법을 사용하는 경우 수명이 짧은 개체가 더 만들어지는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="bca33-135">The main issue is that the functional approach creates more short lived objects.</span></span> <span data-ttu-id="bca33-136">그러나 함수 방법을 사용하면 프로그래머 생산성이 높아지는 장점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bca33-136">However, the tradeoff is an effective one if using the functional approach allows for greater programmer productivity.</span></span>  
  
 <span data-ttu-id="bca33-137">이 예제는 매우 간단하지만 두 방법에 대한 개념의 차이를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bca33-137">This is a very simple example, but it serves to show the difference in philosophy between the two approaches.</span></span> <span data-ttu-id="bca33-138">함수 방법의 경우 큰 XML 문서를 변환할 때 생산성이 더 높습니다.</span><span class="sxs-lookup"><span data-stu-id="bca33-138">The functional approach yields greater productivity gains for transforming larger XML documents.</span></span>  
  