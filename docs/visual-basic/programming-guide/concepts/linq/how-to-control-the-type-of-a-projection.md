---
title: '방법: 프로젝션 형식 제어'
ms.date: 07/20/2015
ms.assetid: a0171276-0b46-4817-aee5-a8d5191b12fe
ms.openlocfilehash: 6b809188f68805afcca960bd809e079d997e79c9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84357259"
---
# <a name="how-to-control-the-type-of-a-projection-visual-basic"></a><span data-ttu-id="c88d9-102">방법: 프로젝션 형식 제어 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c88d9-102">How to: Control the Type of a Projection (Visual Basic)</span></span>
<span data-ttu-id="c88d9-103">프로젝션은 데이터 집합을 하나 가져와서 필터링하고 모양을 변경하며 형식까지도 변경하는 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="c88d9-103">Projection is the process of taking one set of data, filtering it, changing its shape, and even changing its type.</span></span> <span data-ttu-id="c88d9-104">대부분의 쿼리 식은 프로젝션을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="c88d9-104">Most query expressions perform projections.</span></span> <span data-ttu-id="c88d9-105">이 단원에 나와 있는 대부분의 쿼리 식은 <xref:System.Collections.Generic.IEnumerable%601>의 <xref:System.Xml.Linq.XElement>로 확인되지만 다른 형식의 컬렉션을 만들기 위해 프로젝션의 형식을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c88d9-105">Most of the query expressions shown in this section evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, but you can control the type of the projection to create collections of other types.</span></span> <span data-ttu-id="c88d9-106">이 항목에서는 프로젝션의 형식을 제어하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c88d9-106">This topic shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c88d9-107">예제</span><span class="sxs-lookup"><span data-stu-id="c88d9-107">Example</span></span>  
 <span data-ttu-id="c88d9-108">다음 예제에서는 새 형식 `Customer`를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="c88d9-108">The following example defines a new type, `Customer`.</span></span> <span data-ttu-id="c88d9-109">쿼리 식은 `Customer` 절에서 새 `Select` 개체를 인스턴스화합니다.</span><span class="sxs-lookup"><span data-stu-id="c88d9-109">The query expression then instantiates new `Customer` objects in the `Select` clause.</span></span> <span data-ttu-id="c88d9-110">이에 따라 쿼리 식의 형식이 <xref:System.Collections.Generic.IEnumerable%601>의 `Customer`이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c88d9-110">This causes the type of the query expression to be <xref:System.Collections.Generic.IEnumerable%601> of `Customer`.</span></span>  
  
 <span data-ttu-id="c88d9-111">이 예제에서는 XML 문서 [샘플 XML 파일: 고객 및 주문(LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c88d9-111">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
```vb  
Public Class Customer  
    Private customerIDValue As String  
    Public Property CustomerID() As String  
        Get  
            Return customerIDValue  
        End Get  
        Set(ByVal value As String)  
            customerIDValue = value  
        End Set  
    End Property  
  
    Private companyNameValue As String  
    Public Property CompanyName() As String  
        Get  
            Return companyNameValue  
        End Get  
        Set(ByVal value As String)  
            companyNameValue = value  
        End Set  
    End Property  
  
    Private contactNameValue As String  
    Public Property ContactName() As String  
        Get  
            Return contactNameValue  
        End Get  
        Set(ByVal value As String)  
            contactNameValue = value  
        End Set  
    End Property  
  
    Public Sub New(ByVal customerID As String, _  
                   ByVal companyName As String, _  
                   ByVal contactName As String)  
        CustomerIDValue = customerID  
        CompanyNameValue = companyName  
        ContactNameValue = contactName  
    End Sub  
  
    Public Overrides Function ToString() As String  
        Return String.Format("{0}:{1}:{2}", Me.CustomerID, Me.CompanyName, Me.ContactName)  
    End Function  
End Class  
  
Sub Main()  
    Dim custOrd As XElement = XElement.Load("CustomersOrders.xml")  
    Dim custList As IEnumerable(Of Customer) = _  
        From el In custOrd.<Customers>.<Customer> _  
        Select New Customer( _  
            el.@<CustomerID>, _  
            el.<CompanyName>.Value, _  
            el.<ContactName>.Value _  
        )  
    For Each cust In custList  
        Console.WriteLine(cust)  
    Next  
End Sub  
```  
  
 <span data-ttu-id="c88d9-112">이 코드의 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c88d9-112">This code produces the following output:</span></span>  
  
```console  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a><span data-ttu-id="c88d9-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c88d9-113">See also</span></span>

- <xref:System.Linq.Enumerable.Select%2A>
- [<span data-ttu-id="c88d9-114">프로젝션 및 변환 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c88d9-114">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](projections-and-transformations-linq-to-xml.md)
