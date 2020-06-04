---
title: '방법: 복합 필터링을 사용하여 쿼리 작성'
ms.date: 07/20/2015
ms.assetid: bf286ffc-7990-4b00-a4eb-ee3d70129950
ms.openlocfilehash: 18ed4379b7ec9c8007cc3c189fc45571b5161911
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397624"
---
# <a name="how-to-write-queries-with-complex-filtering-visual-basic"></a><span data-ttu-id="7c582-102">방법: 복잡 한 필터링을 사용 하 여 쿼리 작성 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7c582-102">How to: Write Queries with Complex Filtering (Visual Basic)</span></span>
<span data-ttu-id="7c582-103">복잡한 필터를 사용하여 LINQ to XML 쿼리를 작성하려는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c582-103">Sometimes you want to write LINQ to XML queries with complex filters.</span></span> <span data-ttu-id="7c582-104">예를 들어, 특정 이름과 값을 가진 자식 요소가 있는 모든 요소를 찾으려고 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c582-104">For example, you might have to find all elements that have a child element with a particular name and value.</span></span> <span data-ttu-id="7c582-105">이 항목에서는 복잡한 필터링을 사용하여 쿼리를 작성하는 예제를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7c582-105">This topic gives an example of writing a query with complex filtering.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c582-106">예제</span><span class="sxs-lookup"><span data-stu-id="7c582-106">Example</span></span>  
 <span data-ttu-id="7c582-107">이 예제에서는 `PurchaseOrder` 특성이 "Shipping"과 같고 자식 `Address` 요소가 "NY"와 같은 자식 `Type` 요소가 있는 모든 `State` 요소를 찾는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7c582-107">This example shows how to find all `PurchaseOrder` elements that have a child `Address` element that has a `Type` attribute equal to "Shipping" and a child `State` element equal to "NY".</span></span> <span data-ttu-id="7c582-108">이 예제에서는 `Where` 절에서 중첩 쿼리를 사용하며, `Any` 연산자는 컬렉션에 요소가 있는 경우 `True`를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7c582-108">It uses a nested query in the `Where` clause, and the `Any` operator returns `True` if the collection has any elements in it.</span></span>  
  
 <span data-ttu-id="7c582-109">이 예제에서는 XML 문서 [샘플 XML 파일: 여러 구매 주문(LINQ to XML)](sample-xml-file-multiple-purchase-orders-linq-to-xml.md)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7c582-109">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="7c582-110">연산자에 대 한 자세한 내용은 `Any` [수량자 작업 (Visual Basic)](quantifier-operations.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7c582-110">For more information about the `Any` operator, see [Quantifier Operations (Visual Basic)](quantifier-operations.md).</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("PurchaseOrders.xml")  
Dim purchaseOrders As IEnumerable(Of XElement) = _  
    From el In root.<PurchaseOrder> _  
    Where _  
        (From add In el.<Address> _  
        Where _  
             add.@Type = "Shipping" And _  
             add.<State>.Value = "NY" _  
        Select add) _  
    .Any() _  
    Select el  
For Each el As XElement In purchaseOrders  
    Console.WriteLine(el.@PurchaseOrderNumber)  
Next  
```  
  
 <span data-ttu-id="7c582-111">이 코드의 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7c582-111">This code produces the following output:</span></span>  
  
```console  
99505  
```  
  
## <a name="example"></a><span data-ttu-id="7c582-112">예제</span><span class="sxs-lookup"><span data-stu-id="7c582-112">Example</span></span>  
 <span data-ttu-id="7c582-113">다음 예제에서는 네임스페이스에 있는 XML에 대한 동일한 쿼리를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7c582-113">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="7c582-114">자세한 내용은 [네임 스페이스 개요 (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7c582-114">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="7c582-115">이 예제에서는 XML 문서 [샘플 XML 파일: 네임스페이스에서 여러 구매 주문](sample-xml-file-multiple-purchase-orders-in-a-namespace.md)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7c582-115">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns:aw='http://www.adventure-works.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("PurchaseOrdersInNamespace.xml")  
        Dim purchaseOrders As IEnumerable(Of XElement) = _  
            From el In root.<aw:PurchaseOrder> _  
            Where _  
                (From add In el.<aw:Address> _  
                Where _  
                     add.@aw:Type = "Shipping" And _  
                     add.<aw:State>.Value = "NY" _  
                Select add) _  
            .Any() _  
            Select el  
        For Each el As XElement In purchaseOrders  
            Console.WriteLine(el.@aw:PurchaseOrderNumber)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="7c582-116">이 코드의 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7c582-116">This code produces the following output:</span></span>  
  
```console  
99505  
```  
  
## <a name="see-also"></a><span data-ttu-id="7c582-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7c582-117">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="7c582-118">기본 쿼리 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7c582-118">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](basic-queries-linq-to-xml.md)
- [<span data-ttu-id="7c582-119">XML Child Axis Property</span><span class="sxs-lookup"><span data-stu-id="7c582-119">XML Child Axis Property</span></span>](../../../language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="7c582-120">XML Attribute Axis Property</span><span class="sxs-lookup"><span data-stu-id="7c582-120">XML Attribute Axis Property</span></span>](../../../language-reference/xml-axis/xml-attribute-axis-property.md)
- [<span data-ttu-id="7c582-121">XML 값 속성</span><span class="sxs-lookup"><span data-stu-id="7c582-121">XML Value Property</span></span>](../../../language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="7c582-122">프로젝션 작업 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7c582-122">Projection Operations (Visual Basic)</span></span>](projection-operations.md)
- [<span data-ttu-id="7c582-123">수량자 작업 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7c582-123">Quantifier Operations (Visual Basic)</span></span>](quantifier-operations.md)
