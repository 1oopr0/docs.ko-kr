---
title: '방법: 두 위치 경로의 합집합 찾기(XPath-LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: c82c09b4-cb0a-47ec-8cc3-a124144c2788
ms.openlocfilehash: 36528d1748d5675231f14de92dcd78734a696711
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406874"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="20c6b-102">방법: 두 위치 경로의 공용 구조체 찾기 (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20c6b-102">How to: Find a Union of Two Location Paths (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="20c6b-103">XPath를 사용하여 두 XPath 위치 경로의 통합을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20c6b-103">XPath allows you to find the union of the results of two XPath location paths.</span></span>  
  
 <span data-ttu-id="20c6b-104">XPath 식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="20c6b-104">The XPath expression is:</span></span>  
  
 `//Category|//Price`  
  
 <span data-ttu-id="20c6b-105"><xref:System.Linq.Enumerable.Concat%2A> 표준 쿼리 연산자를 사용하여 동일한 결과를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20c6b-105">You can achieve the same results by using the <xref:System.Linq.Enumerable.Concat%2A> standard query operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20c6b-106">예제</span><span class="sxs-lookup"><span data-stu-id="20c6b-106">Example</span></span>  
 <span data-ttu-id="20c6b-107">이 예제에서는 모든 `Category` 요소와 모든 `Price` 요소를 찾은 다음 단일 컬렉션으로 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="20c6b-107">This example finds all of the `Category` elements and all of the `Price` elements, and concatenates them into a single collection.</span></span> <span data-ttu-id="20c6b-108">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 쿼리는 <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A>을 호출하여 결과를 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="20c6b-108">Note that the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query calls <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> to order the results.</span></span> <span data-ttu-id="20c6b-109">XPath 식 계산의 결과도 문서 순서로 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20c6b-109">The results of the XPath expression evaluation are also in document order.</span></span>  
  
 <span data-ttu-id="20c6b-110">이 예제에서는 XML 문서 [샘플 XML 파일: 숫자 데이터(LINQ to XML)](sample-xml-file-numerical-data-linq-to-xml.md)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="20c6b-110">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```vb  
Dim data As XDocument = XDocument.Load("Data.xml")  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = _  
    data...<Category>.Concat(data...<Price>).InDocumentOrder()  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = _  
    data.XPathSelectElements("//Category|//Price")  
  
If list1.Count() = list2.Count() And _  
        list1.Intersect(list2).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="20c6b-111">이 예에서 생성되는 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="20c6b-111">This example produces the following output:</span></span>  
  
```console
Results are identical  
<Category>A</Category>  
<Price>24.50</Price>  
<Category>B</Category>  
<Price>89.99</Price>  
<Category>A</Category>  
<Price>4.95</Price>  
<Category>A</Category>  
<Price>66.00</Price>  
<Category>B</Category>  
<Price>.99</Price>  
<Category>A</Category>  
<Price>29.00</Price>  
<Category>B</Category>  
<Price>6.99</Price>  
```  
  
## <a name="see-also"></a><span data-ttu-id="20c6b-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="20c6b-112">See also</span></span>

- [<span data-ttu-id="20c6b-113">XPath 사용자에 대 한 LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20c6b-113">LINQ to XML for XPath Users (Visual Basic)</span></span>](linq-to-xml-for-xpath-users.md)
