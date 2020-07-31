---
title: 축 메서드 호출을 연결하는 방법(LINQ to XML)(C#)
description: C#의 이러한 LINQ to XML 예제에서는 트리의 특정 깊이에서 지정된 이름의 모든 요소를 찾도록 두 축에 대한 호출을 시연합니다.
ms.date: 07/20/2015
ms.assetid: 067e6da2-ee32-486d-803c-e611b328e39a
ms.openlocfilehash: f26efd2ca918fd36916eb4f01462af70066219a0
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105387"
---
# <a name="how-to-chain-axis-method-calls-linq-to-xml-c"></a><span data-ttu-id="72f73-103">축 메서드 호출을 연결하는 방법(LINQ to XML)(C#)</span><span class="sxs-lookup"><span data-stu-id="72f73-103">How to chain axis method calls (LINQ to XML) (C#)</span></span>
<span data-ttu-id="72f73-104">코드에 사용할 수 있는 일반적인 방법은 축 메서드를 호출한 다음 확장명 메서드 축 중 하나를 호출하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="72f73-104">A common pattern that you will use in your code is to call an axis method, then call one of the extension method axes.</span></span>  
  
 <span data-ttu-id="72f73-105">요소의 컬렉션을 반환하며 `Elements`의 이름이 포함된 두 축인 <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> 메서드와 <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> 메서드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72f73-105">There are two axes with the name of `Elements` that return a collection of elements: the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method and the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="72f73-106">이러한 두 축을 결합하여 트리의 특정 깊이에서 지정된 이름의 모든 요소를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72f73-106">You can combine these two axes to find all elements of a specified name at a given depth in the tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72f73-107">예제</span><span class="sxs-lookup"><span data-stu-id="72f73-107">Example</span></span>  
 <span data-ttu-id="72f73-108">이 예제에서는 <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> 및 <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType>를 사용하여 모든 `Name` 요소의 모든 `Address` 요소에 있는 모든 `PurchaseOrder` 요소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="72f73-108">This example uses <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> and <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> to find all `Name` elements in all `Address` elements in all `PurchaseOrder` elements.</span></span>  
  
 <span data-ttu-id="72f73-109">이 예제에서는 XML 문서로을 사용합니다. [샘플 XML 파일: 여러 구매 주문(LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="72f73-109">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```csharp  
XElement purchaseOrders = XElement.Load("PurchaseOrders.xml");  
IEnumerable<XElement> names =  
    from el in purchaseOrders  
        .Elements("PurchaseOrder")  
        .Elements("Address")  
        .Elements("Name")  
    select el;  
foreach (XElement e in names)  
    Console.WriteLine(e);  
```  
  
 <span data-ttu-id="72f73-110">이 예제는 다음과 같은 출력을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="72f73-110">This example produces the following output:</span></span>  
  
```xml  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
 <span data-ttu-id="72f73-111">이는 `Elements` 축의 구현 중 하나가 <xref:System.Collections.Generic.IEnumerable%601>의 <xref:System.Xml.Linq.XContainer>에 대한 확장 메서드이기 때문에 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="72f73-111">This works because one of the implementations of the `Elements` axis is as an extension method on <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="72f73-112"><xref:System.Xml.Linq.XElement>는 <xref:System.Xml.Linq.XContainer>에서 파생되므로 <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> 메서드에 대한 호출의 결과에 대해 <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> 메서드를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72f73-112"><xref:System.Xml.Linq.XElement> derives from <xref:System.Xml.Linq.XContainer>, so you can call the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method on the results of a call to the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72f73-113">예제</span><span class="sxs-lookup"><span data-stu-id="72f73-113">Example</span></span>  
 <span data-ttu-id="72f73-114">중간에 상위 요소가 있을 수도 있고 없을 수도 있는 특정 요소 깊이에서 모든 요소를 검색하려는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72f73-114">Sometimes you want to retrieve all elements at a particular element depth when there might or might not be intervening ancestors.</span></span> <span data-ttu-id="72f73-115">예를 들어, 다음 문서에서 `ConfigParameter` 요소의 자식인 모든 `Customer` 요소를 검색하고 `ConfigParameter` 요소의 자식인 `Root`는 검색하지 않으려고 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72f73-115">For example, in the following document, you might want to retrieve all the `ConfigParameter` elements that are children of the `Customer` element, but not the `ConfigParameter` that is a child of the `Root` element.</span></span>  
  
```xml  
<Root>  
  <ConfigParameter>RootConfigParameter</ConfigParameter>  
  <Customer>  
    <Name>Frank</Name>  
    <Config>  
      <ConfigParameter>FirstConfigParameter</ConfigParameter>  
    </Config>  
  </Customer>  
  <Customer>  
    <Name>Bob</Name>  
    <!--This customer doesn't have a Config element-->  
  </Customer>  
  <Customer>  
    <Name>Bill</Name>  
    <Config>  
      <ConfigParameter>SecondConfigParameter</ConfigParameter>  
    </Config>  
  </Customer>  
</Root>  
```  
  
 <span data-ttu-id="72f73-116">이렇게 하려면 <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> 축을 다음과 같이 사용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="72f73-116">To do this, you can use the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> axis, as follows:</span></span>  
  
```csharp  
XElement root = XElement.Load("Irregular.xml");  
IEnumerable<XElement> configParameters =
    root.Elements("Customer").Elements("Config").  
    Elements("ConfigParameter");  
foreach (XElement cp in configParameters)  
    Console.WriteLine(cp);  
```  
  
 <span data-ttu-id="72f73-117">이 예제는 다음과 같은 출력을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="72f73-117">This example produces the following output:</span></span>  
  
```xml  
<ConfigParameter>FirstConfigParameter</ConfigParameter>  
<ConfigParameter>SecondConfigParameter</ConfigParameter>  
```  
  
## <a name="example"></a><span data-ttu-id="72f73-118">예제</span><span class="sxs-lookup"><span data-stu-id="72f73-118">Example</span></span>  
 <span data-ttu-id="72f73-119">다음 예제에서는 네임스페이스에 있는 XML에 대한 동일한 기법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="72f73-119">The following example shows the same technique for XML that is in a namespace.</span></span> <span data-ttu-id="72f73-120">자세한 내용은 [네임스페이스 개요(LINQ to XML)(C#)](namespaces-overview-linq-to-xml.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="72f73-120">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="72f73-121">이 예제에서는 XML 문서로을 사용합니다. [샘플 XML 파일: 네임스페이스에서 여러 구매 주문](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="72f73-121">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement purchaseOrders = XElement.Load("PurchaseOrdersInNamespace.xml");  
IEnumerable<XElement> names =  
    from el in purchaseOrders  
        .Elements(aw + "PurchaseOrder")  
        .Elements(aw + "Address")  
        .Elements(aw + "Name")  
    select el;  
foreach (XElement e in names)  
    Console.WriteLine(e);  
```  
  
 <span data-ttu-id="72f73-122">이 예에서 생성되는 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="72f73-122">This example produces the following output:</span></span>  
  
```xml  
<aw:Name xmlns:aw="http://www.adventure-works.com">Ellen Adams</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Tai Yee</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
```  
  
## <a name="see-also"></a><span data-ttu-id="72f73-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="72f73-123">See also</span></span>

- [<span data-ttu-id="72f73-124">LINQ to XML 축(C#)</span><span class="sxs-lookup"><span data-stu-id="72f73-124">LINQ to XML Axes (C#)</span></span>](linq-to-xml-axes-overview.md)
