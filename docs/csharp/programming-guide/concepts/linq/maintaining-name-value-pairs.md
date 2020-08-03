---
title: 이름-값 쌍 유지 관리(C#)
description: LINQ to XML에는 이름/값 쌍을 특성 또는 자식 요소 집합으로 쉽게 유지 관리할 수 있도록 하는 메서드가 포함되어 있습니다.
ms.date: 07/20/2015
ms.assetid: 7b04b0f1-af64-42eb-8737-83f8861b5915
ms.openlocfilehash: 92a45d160cbb1ef470d93bf740d0b6f584681e72
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165281"
---
# <a name="maintaining-namevalue-pairs-c"></a><span data-ttu-id="f710c-103">이름/값 쌍 유지 관리(C#)</span><span class="sxs-lookup"><span data-stu-id="f710c-103">Maintaining Name/Value Pairs (C#)</span></span>
<span data-ttu-id="f710c-104">대부분의 애플리케이션은 이름/값 쌍으로 가장 잘 유지되는 정보를 유지 관리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f710c-104">Many applications have to maintain information that is best kept as name/value pairs.</span></span> <span data-ttu-id="f710c-105">이 정보는 구성 정보이거나 전역 설정일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f710c-105">This information might be configuration information or global settings.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="f710c-106">에는 이름/값 쌍의 집합을 쉽게 유지하는 데 사용할 수 있는 몇몇 메서드가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f710c-106">contains some methods that make it easy to keep a set of name/value pairs.</span></span> <span data-ttu-id="f710c-107">정보를 특성이나 자식 요소의 집합으로 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f710c-107">You can either keep the information as attributes or as a set of child elements.</span></span>  
  
 <span data-ttu-id="f710c-108">정보를 특성으로 유지하는 경우와 자식 요소로 유지하는 경우의 차이점은 특성에 제약 조건이 있다는 것입니다. 즉, 한 요소에 특정 이름을 가진 특성이 하나만 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f710c-108">One difference between keeping the information as attributes or as child elements is that attributes have the constraint that there can be only one attribute with a particular name for an element.</span></span> <span data-ttu-id="f710c-109">이 제한은 자식 요소에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f710c-109">This limitation does not apply to child elements.</span></span>  
  
## <a name="setattributevalue-and-setelementvalue"></a><span data-ttu-id="f710c-110">SetAttributeValue 및 SetElementValue</span><span class="sxs-lookup"><span data-stu-id="f710c-110">SetAttributeValue and SetElementValue</span></span>  
 <span data-ttu-id="f710c-111">이름/값 쌍 유지를 용이하게 하는 두 메서드는 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> 및 <xref:System.Xml.Linq.XElement.SetElementValue%2A>입니다.</span><span class="sxs-lookup"><span data-stu-id="f710c-111">The two methods that facilitate keeping name/value pairs are <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> and <xref:System.Xml.Linq.XElement.SetElementValue%2A>.</span></span> <span data-ttu-id="f710c-112">이러한 두 메서드의 의미는 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="f710c-112">These two methods have similar semantics.</span></span>  
  
 <span data-ttu-id="f710c-113"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A>는 요소의 특성을 추가, 수정 또는 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f710c-113"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A> can add, modify, or remove attributes of an element.</span></span>  
  
- <span data-ttu-id="f710c-114">존재하지 않는 특성의 이름을 사용하여 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>를 호출하면 이 메서드는 새 특성을 만들어 지정된 요소에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f710c-114">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an attribute that does not exist, the method creates a new attribute and adds it to the specified element.</span></span>  
  
- <span data-ttu-id="f710c-115">기존 특성의 이름과 지정된 내용을 사용하여 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>를 호출하면 특성의 내용이 지정된 내용으로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="f710c-115">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute and with some specified content, the contents of the attribute are replaced with the specified content.</span></span>  
  
- <span data-ttu-id="f710c-116">기존 특성의 이름을 사용하여 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>를 호출하고 내용에 null을 지정하면 특성이 부모에서 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="f710c-116">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute, and specify null for the content, the attribute is removed from its parent.</span></span>  
  
 <span data-ttu-id="f710c-117"><xref:System.Xml.Linq.XElement.SetElementValue%2A>는 요소의 자식 요소를 추가, 수정 또는 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f710c-117"><xref:System.Xml.Linq.XElement.SetElementValue%2A> can add, modify, or remove child elements of an element.</span></span>  
  
- <span data-ttu-id="f710c-118">존재하지 않는 자식 요소의 이름을 사용하여 <xref:System.Xml.Linq.XElement.SetElementValue%2A>를 호출하면 이 메서드는 새 요소를 만들어 지정된 요소에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f710c-118">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of a child element that does not exist, the method creates a new element and adds it to the specified element.</span></span>  
  
- <span data-ttu-id="f710c-119">기존 요소의 이름과 지정된 내용을 사용하여 <xref:System.Xml.Linq.XElement.SetElementValue%2A>를 호출하면 요소의 내용이 지정된 내용으로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="f710c-119">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element and with some specified content, the contents of the element are replaced with the specified content.</span></span>  
  
- <span data-ttu-id="f710c-120">기존 요소의 이름을 사용하여 <xref:System.Xml.Linq.XElement.SetElementValue%2A>를 호출하고 내용에 null을 지정하면 요소가 부모에서 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="f710c-120">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element, and specify null for the content, the element is removed from its parent.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f710c-121">예제</span><span class="sxs-lookup"><span data-stu-id="f710c-121">Example</span></span>  
 <span data-ttu-id="f710c-122">다음 예제에서는 특성 없이 요소를 만든 다음</span><span class="sxs-lookup"><span data-stu-id="f710c-122">The following example creates an element with no attributes.</span></span> <span data-ttu-id="f710c-123"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A> 메서드를 사용하여 이름/값 쌍의 목록을 만들고 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="f710c-123">It then uses the <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
```csharp  
// Create an element with no content.  
XElement root = new XElement("Root");  
  
// Add a number of name/value pairs as attributes.  
root.SetAttributeValue("Top", 22);  
root.SetAttributeValue("Left", 20);  
root.SetAttributeValue("Bottom", 122);  
root.SetAttributeValue("Right", 300);  
root.SetAttributeValue("DefaultColor", "Color.Red");  
Console.WriteLine(root);  
  
// Replace the value of Top.  
root.SetAttributeValue("Top", 10);  
Console.WriteLine(root);  
  
// Remove DefaultColor.  
root.SetAttributeValue("DefaultColor", null);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="f710c-124">이 예제는 다음과 같은 출력을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="f710c-124">This example produces the following output:</span></span>  
  
```xml  
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" />  
```  
  
## <a name="example"></a><span data-ttu-id="f710c-125">예제</span><span class="sxs-lookup"><span data-stu-id="f710c-125">Example</span></span>  
 <span data-ttu-id="f710c-126">다음 예제에서는 자식 요소 없이 요소를 만든 다음</span><span class="sxs-lookup"><span data-stu-id="f710c-126">The following example creates an element with no child elements.</span></span> <span data-ttu-id="f710c-127"><xref:System.Xml.Linq.XElement.SetElementValue%2A> 메서드를 사용하여 이름/값 쌍의 목록을 만들고 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="f710c-127">It then uses the <xref:System.Xml.Linq.XElement.SetElementValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
```csharp  
// Create an element with no content.  
XElement root = new XElement("Root");  
  
// Add a number of name/value pairs as elements.  
root.SetElementValue("Top", 22);  
root.SetElementValue("Left", 20);  
root.SetElementValue("Bottom", 122);  
root.SetElementValue("Right", 300);  
root.SetElementValue("DefaultColor", "Color.Red");  
Console.WriteLine(root);  
Console.WriteLine("----");  
  
// Replace the value of Top.  
root.SetElementValue("Top", 10);  
Console.WriteLine(root);  
Console.WriteLine("----");  
  
// Remove DefaultColor.  
root.SetElementValue("DefaultColor", null);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="f710c-128">이 예에서 생성되는 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f710c-128">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Top>22</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
  <DefaultColor>Color.Red</DefaultColor>  
</Root>  
----  
<Root>  
  <Top>10</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
  <DefaultColor>Color.Red</DefaultColor>  
</Root>  
----  
<Root>  
  <Top>10</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f710c-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f710c-129">See also</span></span>

- <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>
- <xref:System.Xml.Linq.XElement.SetElementValue%2A>
- [<span data-ttu-id="f710c-130">XML 트리 수정(LINQ to XML)(C#)</span><span class="sxs-lookup"><span data-stu-id="f710c-130">Modifying XML Trees (LINQ to XML) (C#)</span></span>](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md)
