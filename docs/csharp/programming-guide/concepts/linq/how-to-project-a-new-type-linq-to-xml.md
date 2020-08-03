---
title: 새 형식을 프로젝션하는 방법(LINQ to XML)(C#)
description: 다른 예제에서 설명한 XElement, 문자열 또는 int 외에 IEnumerable<T> 형식을 반환하는 C#의 LINQ to XML로 쿼리를 만드는 방법에 대해 알아봅니다.
ms.date: 07/20/2015
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
ms.openlocfilehash: 013ea852a64b77c04ac583b4d9b71e8006cd4976
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104646"
---
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a><span data-ttu-id="0c14c-103">새 형식을 프로젝션하는 방법(LINQ to XML)(C#)</span><span class="sxs-lookup"><span data-stu-id="0c14c-103">How to project a new type (LINQ to XML) (C#)</span></span>

<span data-ttu-id="0c14c-104">이 단원의 다른 예제에서는 <xref:System.Collections.Generic.IEnumerable%601>의 <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601>의 `string` 및 <xref:System.Collections.Generic.IEnumerable%601>의 `int`로 결과를 반환하는 쿼리를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0c14c-104">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="0c14c-105">이러한 결과 형식이 일반적이지만 모든 시나리오에 적합하지는 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="0c14c-105">These are common result types, but they are not appropriate for every scenario.</span></span> <span data-ttu-id="0c14c-106">대부분의 경우 다른 형식의 <xref:System.Collections.Generic.IEnumerable%601>을 반환하는 쿼리를 작성하려고 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c14c-106">In many cases you will want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>

## <a name="example"></a><span data-ttu-id="0c14c-107">예제</span><span class="sxs-lookup"><span data-stu-id="0c14c-107">Example</span></span>

<span data-ttu-id="0c14c-108">이 예제에서는 `select` 절에서 개체를 인스턴스화하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0c14c-108">This example shows how to instantiate objects in the `select` clause.</span></span> <span data-ttu-id="0c14c-109">이 코드에서는 먼저 생성자를 사용하여 새 클래스를 정의한 다음 식이 새 클래스의 새 인스턴스이도록 `select` 문을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="0c14c-109">The code first defines a new class with a constructor, and then modifies the `select` statement so that the expression is a new instance of the new class.</span></span>

<span data-ttu-id="0c14c-110">이 예제에서는 XML 문서로을 사용합니다. [샘플 XML 파일: 일반적인 구매 주문(LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md)에서 설명하는 것과 같은 일반적인 XML 구매 주문이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c14c-110">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>

```csharp
class NameQty
{
    public string name;
    public int qty;
    public NameQty(string n, int q)
    {
        name = n;
        qty = q;
    }
};

class Program {
    public static void Main()
    {
        XElement po = XElement.Load("PurchaseOrder.xml");
  
        IEnumerable<NameQty> nqList =
            from n in po.Descendants("Item")
            select new NameQty(
                    (string)n.Element("ProductName"),
                    (int)n.Element("Quantity")
                );
  
        foreach (NameQty n in nqList)
            Console.WriteLine(n.name + ":" + n.qty);
    }
}
```

<span data-ttu-id="0c14c-111">이 예제에서는 [단일 자식 요소를 검색하는 방법(LINQ to XML)(C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md) 항목에 도입된 <xref:System.Xml.Linq.XContainer.Element%2A> 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0c14c-111">This example uses the <xref:System.Xml.Linq.XContainer.Element%2A> method that was introduced in the topic [How to retrieve a single child element (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md).</span></span> <span data-ttu-id="0c14c-112">또한, 캐스트를 사용하여 <xref:System.Xml.Linq.XContainer.Element%2A> 메서드에서 반환하는 요소의 값을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="0c14c-112">It also uses casts to retrieve the values of the elements that are returned by the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span>  

<span data-ttu-id="0c14c-113">이 예제는 다음과 같은 출력을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="0c14c-113">This example produces the following output:</span></span>

```output
Lawnmower:1
Baby Monitor:2
```
