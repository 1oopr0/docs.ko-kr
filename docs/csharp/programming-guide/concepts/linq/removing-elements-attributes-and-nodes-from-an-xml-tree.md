---
title: XML 트리에서 요소, 특성 및 노드 제거(C#)
description: XML 트리에서 요소, 특성 및 노드를 제거하는 방법을 알아봅니다. 제거 메서드 목록을 확인하고 코드 예제를 살펴봅니다.
ms.date: 07/20/2015
ms.assetid: 07dd06d6-1117-4077-bf98-9120cf51176e
ms.openlocfilehash: 4e753c3d96c4cbc050b08076ca8bff8c17b2e252
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87300048"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-c"></a><span data-ttu-id="4fc73-104">XML 트리에서 요소, 특성 및 노드 제거(C#)</span><span class="sxs-lookup"><span data-stu-id="4fc73-104">Removing Elements, Attributes, and Nodes from an XML Tree (C#)</span></span>

<span data-ttu-id="4fc73-105">XML 트리를 수정하여 요소, 특성 및 다른 형식의 노드를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fc73-105">You can modify an XML tree, removing elements, attributes, and other types of nodes.</span></span>

<span data-ttu-id="4fc73-106">XML 문서에서 요소나 특성을 하나만 제거하는 것은 간단합니다.</span><span class="sxs-lookup"><span data-stu-id="4fc73-106">Removing a single element or a single attribute from an XML document is straightforward.</span></span> <span data-ttu-id="4fc73-107">그러나 요소나 특성의 컬렉션을 제거하는 경우 먼저 컬렉션을 목록으로 구체화한 다음 요소나 특성을 목록에서 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fc73-107">However, when removing collections of elements or attributes, you should first materialize a collection into a list, and then delete the elements or attributes from the list.</span></span> <span data-ttu-id="4fc73-108">가장 좋은 방법은 이 작업을 수행하는 <xref:System.Xml.Linq.Extensions.Remove%2A> 확장 메서드를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4fc73-108">The best approach is to use the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method, which will do this for you.</span></span>

<span data-ttu-id="4fc73-109">이렇게 하는 주요 이유는 XML 트리에서 검색하는 대부분의 컬렉션이 지연된 실행을 사용하여 생성되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="4fc73-109">The main reason for doing this is that most of the collections you retrieve from an XML tree are yielded using deferred execution.</span></span> <span data-ttu-id="4fc73-110">컬렉션을 먼저 목록으로 구체화하지 않거나 확장명 메서드를 사용하지 않는 경우 특정 유형의 버그가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fc73-110">If you do not first materialize them into a list, or if you do not use the extension methods, it is possible to encounter a certain class of bugs.</span></span> <span data-ttu-id="4fc73-111">자세한 내용은 [혼합된 선언적 코드/명령적 코드 버그(LINQ to XML)(C#)](./mixed-declarative-code-imperative-code-bugs-linq-to-xml.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4fc73-111">For more information, see [Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (C#)](./mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span></span>

<span data-ttu-id="4fc73-112">다음 메서드는 XML 트리에서 노드와 특성을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="4fc73-112">The following methods remove nodes and attributes from an XML tree.</span></span>

|<span data-ttu-id="4fc73-113">메서드</span><span class="sxs-lookup"><span data-stu-id="4fc73-113">Method</span></span>|<span data-ttu-id="4fc73-114">설명</span><span class="sxs-lookup"><span data-stu-id="4fc73-114">Description</span></span>|
|------------|-----------------|
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="4fc73-115">부모에서 <xref:System.Xml.Linq.XAttribute>를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="4fc73-115">Removes an <xref:System.Xml.Linq.XAttribute> from its parent.</span></span>|
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="4fc73-116"><xref:System.Xml.Linq.XContainer>에서 자식 노드를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="4fc73-116">Removes the child nodes from an <xref:System.Xml.Linq.XContainer>.</span></span>|
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="4fc73-117"><xref:System.Xml.Linq.XElement>에서 내용과 특성을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="4fc73-117">Removes content and attributes from an <xref:System.Xml.Linq.XElement>.</span></span>|
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="4fc73-118"><xref:System.Xml.Linq.XElement>의 특성을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="4fc73-118">Removes the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="4fc73-119">값으로 `null`을 전달하면 특성을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="4fc73-119">If you pass `null` for value, then removes the attribute.</span></span>|
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="4fc73-120">값으로 `null`을 전달하면 자식 요소를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="4fc73-120">If you pass `null` for value, then removes the child element.</span></span>|
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="4fc73-121">부모에서 <xref:System.Xml.Linq.XNode>를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="4fc73-121">Removes an <xref:System.Xml.Linq.XNode> from its parent.</span></span>|
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="4fc73-122">부모 요소에서 소스 컬렉션의 모든 특성이나 요소를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="4fc73-122">Removes every attribute or element in the source collection from its parent element.</span></span>|

## <a name="example"></a><span data-ttu-id="4fc73-123">예제</span><span class="sxs-lookup"><span data-stu-id="4fc73-123">Example</span></span>

### <a name="description"></a><span data-ttu-id="4fc73-124">설명</span><span class="sxs-lookup"><span data-stu-id="4fc73-124">Description</span></span>

<span data-ttu-id="4fc73-125">이 예제에서는 요소를 제거하는 세 가지 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4fc73-125">This example demonstrates three approaches to removing elements.</span></span> <span data-ttu-id="4fc73-126">첫째, 단일 요소를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="4fc73-126">First, it removes a single element.</span></span> <span data-ttu-id="4fc73-127">둘째, 요소의 컬렉션을 검색하고 <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> 연산자를 사용하여 구체화한 다음 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="4fc73-127">Second, it retrieves a collection of elements, materializes them using the <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> operator, and removes the collection.</span></span> <span data-ttu-id="4fc73-128">마지막으로, 요소의 컬렉션을 검색하고 <xref:System.Xml.Linq.Extensions.Remove%2A> 확장 메서드를 사용하여 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="4fc73-128">Finally, it retrieves a collection of elements and removes them using the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method.</span></span>

<span data-ttu-id="4fc73-129"><xref:System.Linq.Enumerable.ToList%2A> 연산자에 대한 자세한 내용은 [데이터 형식 변환(C#)](./converting-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4fc73-129">For more information on the <xref:System.Linq.Enumerable.ToList%2A> operator, see [Converting Data Types (C#)](./converting-data-types.md).</span></span>

### <a name="code"></a><span data-ttu-id="4fc73-130">코드</span><span class="sxs-lookup"><span data-stu-id="4fc73-130">Code</span></span>

```csharp
XElement root = XElement.Parse(@"<Root>
    <Child1>
        <GrandChild1/>
        <GrandChild2/>
        <GrandChild3/>
    </Child1>
    <Child2>
        <GrandChild4/>
        <GrandChild5/>
        <GrandChild6/>
    </Child2>
    <Child3>
        <GrandChild7/>
        <GrandChild8/>
        <GrandChild9/>
    </Child3>
</Root>");
root.Element("Child1").Element("GrandChild1").Remove();
root.Element("Child2").Elements().ToList().Remove();
root.Element("Child3").Elements().Remove();
Console.WriteLine(root);
```

### <a name="comments"></a><span data-ttu-id="4fc73-131">주석</span><span class="sxs-lookup"><span data-stu-id="4fc73-131">Comments</span></span>

<span data-ttu-id="4fc73-132">이 코드의 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4fc73-132">This code produces the following output:</span></span>

```xml
<Root>
  <Child1>
    <GrandChild2 />
    <GrandChild3 />
  </Child1>
  <Child2 />
  <Child3 />
</Root>
```

<span data-ttu-id="4fc73-133">`Child1`에서는 첫 번째 손자 요소가 제거되었고,</span><span class="sxs-lookup"><span data-stu-id="4fc73-133">Notice that the first grandchild element has been removed from `Child1`.</span></span> <span data-ttu-id="4fc73-134">`Child2`와 `Child3`에서는 모든 손자 요소가 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4fc73-134">All grandchildren elements have been removed from `Child2` and from `Child3`.</span></span>
