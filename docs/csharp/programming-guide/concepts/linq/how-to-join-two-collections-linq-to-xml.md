---
title: 두 컬렉션을 조인하는 방법(LINQ to XML)(C#)
description: 이 C# 예제에서는 LINQ to XML의 요소를 다른 요소에 조인하고 새 XML 문서를 생성합니다.
ms.date: 07/20/2015
ms.assetid: 7b817ede-911a-4cff-9dd3-639c3fc228c9
ms.openlocfilehash: 10792ed4907e778b41821c9b32574bd8fc0ab35f
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104996"
---
# <a name="how-to-join-two-collections-linq-to-xml-c"></a><span data-ttu-id="87b71-103">두 컬렉션을 조인하는 방법(LINQ to XML)(C#)</span><span class="sxs-lookup"><span data-stu-id="87b71-103">How to join two collections (LINQ to XML) (C#)</span></span>

<span data-ttu-id="87b71-104">XML 문서의 요소나 특성은 때때로 다른 요소나 특성을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87b71-104">An element or attribute in an XML document can sometimes refer to another element or attribute.</span></span> <span data-ttu-id="87b71-105">예를 들어 [샘플 XML 파일: Customers 및 Orders(LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) XML 문서에는 고객 목록과 주문 목록이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87b71-105">For example, the [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) XML document contains a list of customers and a list of orders.</span></span> <span data-ttu-id="87b71-106">각 `Customer` 요소에는 `CustomerID` 특성이 포함되어 있고,</span><span class="sxs-lookup"><span data-stu-id="87b71-106">Each `Customer` element contains a `CustomerID` attribute.</span></span> <span data-ttu-id="87b71-107">각 `Order` 요소에는 `CustomerID` 요소가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87b71-107">Each `Order` element contains a `CustomerID` element.</span></span> <span data-ttu-id="87b71-108">각 주문의 `CustomerID` 요소는 고객의 `CustomerID` 특성을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="87b71-108">The `CustomerID` element in each order refers to the `CustomerID` attribute in a customer.</span></span>

<span data-ttu-id="87b71-109">항목 [샘플 XSD 파일: Customers 및 Orders](./sample-xsd-file-customers-and-orders1.md)에는 이 문서의 유효성을 검사하는 데 사용할 수 있는 XSD가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87b71-109">The topic [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md) contains an XSD that can be used to validate this document.</span></span> <span data-ttu-id="87b71-110">이 항목에서는 XSD의 `xs:key` 및 `xs:keyref` 기능을 사용하여 `CustomerID` 요소의 `Customer` 특성을 키로 설정하고 각 `CustomerID` 요소의 `Order` 요소와 각 `CustomerID` 요소의 `Customer` 특성 간 관계를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="87b71-110">It uses the `xs:key` and `xs:keyref` features of XSD to establish that the `CustomerID` attribute of the `Customer` element is a key, and to establish a relationship between the `CustomerID` element in each `Order` element and the `CustomerID` attribute in each `Customer` element.</span></span>

<span data-ttu-id="87b71-111">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]에서는 `join` 절을 사용하여 이 관계를 이용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87b71-111">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can take advantage of this relationship by using the `join` clause.</span></span>

<span data-ttu-id="87b71-112">사용 가능한 인덱스가 없기 때문에 이러한 조인의 런타임 성능은 좋지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="87b71-112">Because there is no index available, such joining will have poor run-time performance.</span></span>

<span data-ttu-id="87b71-113">`join`에 대한 자세한 내용은 [조인 작업(C#)](./join-operations.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="87b71-113">For more detailed information about `join`, see [Join Operations (C#)](./join-operations.md).</span></span>

## <a name="example"></a><span data-ttu-id="87b71-114">예제</span><span class="sxs-lookup"><span data-stu-id="87b71-114">Example</span></span>

<span data-ttu-id="87b71-115">다음 예제에서는 `Customer` 요소와 `Order` 요소를 조인하고 주문의 `CompanyName` 요소가 포함된 새 XML 문서를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="87b71-115">The following example joins the `Customer` elements to the `Order` elements, and generates a new XML document that includes the `CompanyName` element in the orders.</span></span>

<span data-ttu-id="87b71-116">예제에서는 쿼리를 실행하기 전에 문서가 [샘플 XSD 파일: Customer 및 Order](./sample-xsd-file-customers-and-orders1.md)의 스키마를 준수하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="87b71-116">Before executing the query, the example validates that the document complies with the schema in [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span> <span data-ttu-id="87b71-117">이에 따라 조인 절이 항상 작동하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="87b71-117">This ensures that the join clause will always work.</span></span>

<span data-ttu-id="87b71-118">이 쿼리에서는 먼저 모든 `Customer` 요소를 검색하고 `Order` 요소와 조인한 다음</span><span class="sxs-lookup"><span data-stu-id="87b71-118">This query first retrieves all `Customer` elements, and then joins them to the `Order` elements.</span></span> <span data-ttu-id="87b71-119">`CustomerID`가 "K"보다 큰 고객의 주문만 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="87b71-119">It selects only the orders for customers with a `CustomerID` greater than "K".</span></span> <span data-ttu-id="87b71-120">그런 다음 각 주문의 고객 정보가 포함된 새 `Order` 요소를 프로젝션합니다.</span><span class="sxs-lookup"><span data-stu-id="87b71-120">It then projects a new `Order` element that contains the customer information within each order.</span></span>

<span data-ttu-id="87b71-121">이 예제에서는 XML 문서로을 사용합니다. [샘플 XML 파일: Customers 및 Orders(LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="87b71-121">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>

<span data-ttu-id="87b71-122">이 예제에서는 XSD 스키마을 사용합니다. [샘플 XSD 파일: Customer 및 Order](./sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="87b71-122">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span>

<span data-ttu-id="87b71-123">이런 방식의 조인은 성능이 좋지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="87b71-123">Joining in this fashion will not perform well.</span></span> <span data-ttu-id="87b71-124">조인은 선형 검색을 통해 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="87b71-124">Joins are performed via a linear search.</span></span> <span data-ttu-id="87b71-125">성능에 도움이 될 해시 테이블이나 인덱스는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="87b71-125">There are no hash tables or indexes to help with performance.</span></span>

```csharp
XmlSchemaSet schemas = new XmlSchemaSet();
schemas.Add("", "CustomersOrders.xsd");

Console.Write("Attempting to validate, ");
XDocument custOrdDoc = XDocument.Load("CustomersOrders.xml");

bool errors = false;
custOrdDoc.Validate(schemas, (o, e) =>
                     {
                         Console.WriteLine("{0}", e.Message);
                         errors = true;
                     });
Console.WriteLine("custOrdDoc {0}", errors ? "did not validate" : "validated");

if (!errors)
{
    // Join customers and orders, and create a new XML document with
    // a different shape.

    // The new document contains orders only for customers with a
    // CustomerID > 'K'
    XElement custOrd = custOrdDoc.Element("Root");
    XElement newCustOrd = new XElement("Root",
        from c in custOrd.Element("Customers").Elements("Customer")
        join o in custOrd.Element("Orders").Elements("Order")
                   on (string)c.Attribute("CustomerID") equals
                      (string)o.Element("CustomerID")
        where ((string)c.Attribute("CustomerID")).CompareTo("K") > 0
        select new XElement("Order",
            new XElement("CustomerID", (string)c.Attribute("CustomerID")),
            new XElement("CompanyName", (string)c.Element("CompanyName")),
            new XElement("ContactName", (string)c.Element("ContactName")),
            new XElement("EmployeeID", (string)o.Element("EmployeeID")),
            new XElement("OrderDate", (DateTime)o.Element("OrderDate"))
        )
    );
    Console.WriteLine(newCustOrd);
}
```

<span data-ttu-id="87b71-126">이 코드의 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="87b71-126">This code produces the following output:</span></span>

```output
Attempting to validate, custOrdDoc validated
<Root>
  <Order>
    <CustomerID>LAZYK</CustomerID>
    <CompanyName>Lazy K Kountry Store</CompanyName>
    <ContactName>John Steel</ContactName>
    <EmployeeID>1</EmployeeID>
    <OrderDate>1997-03-21T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LAZYK</CustomerID>
    <CompanyName>Lazy K Kountry Store</CompanyName>
    <ContactName>John Steel</ContactName>
    <EmployeeID>8</EmployeeID>
    <OrderDate>1997-05-22T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LETSS</CustomerID>
    <CompanyName>Let's Stop N Shop</CompanyName>
    <ContactName>Jaime Yorres</ContactName>
    <EmployeeID>1</EmployeeID>
    <OrderDate>1997-06-25T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LETSS</CustomerID>
    <CompanyName>Let's Stop N Shop</CompanyName>
    <ContactName>Jaime Yorres</ContactName>
    <EmployeeID>8</EmployeeID>
    <OrderDate>1997-10-27T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LETSS</CustomerID>
    <CompanyName>Let's Stop N Shop</CompanyName>
    <ContactName>Jaime Yorres</ContactName>
    <EmployeeID>6</EmployeeID>
    <OrderDate>1997-11-10T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LETSS</CustomerID>
    <CompanyName>Let's Stop N Shop</CompanyName>
    <ContactName>Jaime Yorres</ContactName>
    <EmployeeID>4</EmployeeID>
    <OrderDate>1998-02-12T00:00:00</OrderDate>
  </Order>
</Root>
```
