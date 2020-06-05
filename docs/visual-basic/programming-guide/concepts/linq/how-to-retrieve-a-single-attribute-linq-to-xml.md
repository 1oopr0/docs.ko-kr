---
title: '방법: 단일 특성 검색(LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 11b938d7-c011-4048-900e-8b9183c41c94
ms.openlocfilehash: 34c390fbffc1aea68a2fd8ae64b17d2637a1f4f1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397858"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-visual-basic"></a><span data-ttu-id="88479-102">방법: 단일 특성 검색 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="88479-102">How to: Retrieve a Single Attribute (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="88479-103">이 항목에서는 특성 이름이 제공되는 경우 요소의 단일 특성을 검색하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="88479-103">This topic explains how to retrieve a single attribute of an element, given the attribute name.</span></span> <span data-ttu-id="88479-104">이 방법은 특정 특성을 가진 요소를 찾으려는 경우 쿼리 식을 작성하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="88479-104">This is useful for writing query expressions where you want to find an element that has a particular attribute.</span></span>  
  
 <span data-ttu-id="88479-105"><xref:System.Xml.Linq.XElement.Attribute%2A> 클래스의 <xref:System.Xml.Linq.XElement> 메서드는 지정된 이름을 가진 <xref:System.Xml.Linq.XAttribute>를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="88479-105">The <xref:System.Xml.Linq.XElement.Attribute%2A> method of the <xref:System.Xml.Linq.XElement> class returns the <xref:System.Xml.Linq.XAttribute> with the specified name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88479-106">예제</span><span class="sxs-lookup"><span data-stu-id="88479-106">Example</span></span>  
 <span data-ttu-id="88479-107">다음 예제에서는 <xref:System.Xml.Linq.XElement.Attribute%2A> 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="88479-107">The following example uses the <xref:System.Xml.Linq.XElement.Attribute%2A> method.</span></span>  
  
```vb  
Dim cust As XElement = <PhoneNumbers>  
                           <Phone type="home">555-555-5555</Phone>  
                           <Phone type="work">555-555-6666</Phone>  
                       </PhoneNumbers>  
Dim elList = From el In cust...<Phone>  
For Each e As XElement In elList  
    Console.WriteLine(e.@type)  
Next  
```  
  
 <span data-ttu-id="88479-108">이 예제에서는 트리에서 이름이 `Phone`인 하위 요소를 모두 찾은 다음 이름이 `type`인 특성을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="88479-108">This example finds all the descendants in the tree named `Phone`, and then finds the attribute named `type`.</span></span>  
  
 <span data-ttu-id="88479-109">이 코드의 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="88479-109">This code produces the following output:</span></span>  
  
```console  
home  
work  
```  
  
## <a name="example"></a><span data-ttu-id="88479-110">예제</span><span class="sxs-lookup"><span data-stu-id="88479-110">Example</span></span>  
 <span data-ttu-id="88479-111">특성의 값을 검색하려면 <xref:System.Xml.Linq.XElement> 개체의 경우와 마찬가지로 특성을 캐스팅하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="88479-111">If you want to retrieve the value of the attribute, you can cast it, just as you do for with <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="88479-112">다음은 이에 대한 예입니다.</span><span class="sxs-lookup"><span data-stu-id="88479-112">The following example demonstrates this.</span></span>  
  
```vb  
Dim cust As XElement = <PhoneNumbers>  
                           <Phone type="home">555-555-5555</Phone>  
                           <Phone type="work">555-555-6666</Phone>  
                       </PhoneNumbers>  
Dim elList As IEnumerable(Of XElement) = _  
    From el In cust...<Phone> _  
    Select el  
For Each el As XElement In elList  
    Console.WriteLine(el.@type)  
Next  
```  
  
 <span data-ttu-id="88479-113">이 코드의 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="88479-113">This code produces the following output:</span></span>  
  
```console  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="88479-114">에서는 <xref:System.Xml.Linq.XAttribute> 클래스를 `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, `GUID?`로 캐스팅할 수 있는 명시적 캐스트 연산자를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="88479-114">provides explicit cast operators for the <xref:System.Xml.Linq.XAttribute> class to `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88479-115">예제</span><span class="sxs-lookup"><span data-stu-id="88479-115">Example</span></span>  
 <span data-ttu-id="88479-116">다음 예제에서는 네임스페이스에 있는 특성에 대한 동일한 코드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="88479-116">The following example shows the same code for an attribute that is in a namespace.</span></span> <span data-ttu-id="88479-117">자세한 내용은 [네임 스페이스 개요 (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="88479-117">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim cust As XElement = _  
            <aw:PhoneNumbers>  
                <aw:Phone aw:type="home">555-555-5555</aw:Phone>  
                <aw:Phone aw:type="work">555-555-6666</aw:Phone>  
            </aw:PhoneNumbers>  
        Dim elList As IEnumerable(Of XElement) = _  
            From el In cust...<aw:Phone> _  
            Select el  
        For Each el As XElement In elList  
            Console.WriteLine(el.@aw:type)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="88479-118">이 코드의 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="88479-118">This code produces the following output:</span></span>  
  
```console  
home  
work  
```  
  
## <a name="see-also"></a><span data-ttu-id="88479-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="88479-119">See also</span></span>

- [<span data-ttu-id="88479-120">LINQ to XML 축(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="88479-120">LINQ to XML Axes (Visual Basic)</span></span>](linq-to-xml-axes.md)
