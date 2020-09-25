---
title: '쿼리 식 구문 예제: 제한(LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1daf42c2-c9f4-4cda-b291-7641b9c6d3fe
ms.openlocfilehash: 92ffc3a36137281688ee3918828df111ac6707e9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172764"
---
# <a name="query-expression-syntax-examples-restriction-linq-to-dataset"></a><span data-ttu-id="bada8-102">쿼리 식 구문 예제: 제한(LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="bada8-102">Query Expression Syntax Examples: Restriction (LINQ to DataSet)</span></span>

<span data-ttu-id="bada8-103">이 항목의 예제에서는 <xref:System.Linq.Enumerable.Where%2A> 메서드에서 쿼리 식 구문을 사용하여 <xref:System.Data.DataSet>을 쿼리하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bada8-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Where%2A> method to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="bada8-104">이러한 예제에서 사용되는 `FillDataSet` 메서드는 [데이터집합에 데이터를 로드](loading-data-into-a-dataset.md)하는데 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="bada8-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="bada8-105">이 항목의 예제에서는 AdventureWorks 샘플 데이터베이스의 Contact, Address, Product, SalesOrderHeader 및 SalesOrderDetail 테이블을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bada8-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="bada8-106">이 항목의 예제에서는 다음 문을 사용 합니다 `using` / `Imports` .</span><span class="sxs-lookup"><span data-stu-id="bada8-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
[!code-csharp[DP LINQ to DataSetExamples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
  
 <span data-ttu-id="bada8-107">자세한 내용은 [방법: Visual Studio에서 LINQ to DataSet 프로젝트 만들기](how-to-create-a-linq-to-dataset-project-in-vs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bada8-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="where"></a><span data-ttu-id="bada8-108">Where</span><span class="sxs-lookup"><span data-stu-id="bada8-108">Where</span></span>  
  
### <a name="example"></a><span data-ttu-id="bada8-109">예제</span><span class="sxs-lookup"><span data-stu-id="bada8-109">Example</span></span>  

 <span data-ttu-id="bada8-110">이 예제에서는 모든 온라인 주문을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bada8-110">This example returns all online orders.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where1)]  
 [!code-vb[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where1)]
  
### <a name="example"></a><span data-ttu-id="bada8-111">예제</span><span class="sxs-lookup"><span data-stu-id="bada8-111">Example</span></span>  

 <span data-ttu-id="bada8-112">이 예제에서는 주문 수량이 2보다 크고 6보다 작은 주문을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bada8-112">This example returns the orders where the order quantity is greater than 2 and less than 6.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where2)]  
 [!code-vb[DP LINQ to DataSet Examples#Where2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where2)]
  
### <a name="example"></a><span data-ttu-id="bada8-113">예제</span><span class="sxs-lookup"><span data-stu-id="bada8-113">Example</span></span>  

 <span data-ttu-id="bada8-114">이 예제에서는 모든 빨간색 제품을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bada8-114">This example returns all red colored products.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where3)]  
 [!code-vb[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where3)]
  
### <a name="example"></a><span data-ttu-id="bada8-115">예제</span><span class="sxs-lookup"><span data-stu-id="bada8-115">Example</span></span>  

 <span data-ttu-id="bada8-116">이 예제에서는 <xref:System.Linq.Enumerable.Where%2A> 메서드를 사용하여 2002년 12월 1일 이후 주문을 찾은 다음 <xref:System.Data.DataRow.GetChildRows%2A> 메서드를 사용하여 각 주문의 세부 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bada8-116">This example uses the <xref:System.Linq.Enumerable.Where%2A> method to find orders that were made after December 1, 2002 and then uses the <xref:System.Data.DataRow.GetChildRows%2A> method to get the details for each order.</span></span>  
  
 [!code-csharp[DP LINQ to DataSetExamples#WhereDrillDown](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#wheredrilldown)]
 [!code-vb[DP LINQ to DataSet Examples#WhereDrillDown](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#wheredrilldown)]  
  
## <a name="see-also"></a><span data-ttu-id="bada8-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bada8-117">See also</span></span>

- [<span data-ttu-id="bada8-118">데이터를 데이터 세트에 로드</span><span class="sxs-lookup"><span data-stu-id="bada8-118">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="bada8-119">LINQ to DataSet 예제</span><span class="sxs-lookup"><span data-stu-id="bada8-119">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="bada8-120">표준 쿼리 연산자 개요(C#)</span><span class="sxs-lookup"><span data-stu-id="bada8-120">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="bada8-121">표준 쿼리 연산자 개요(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bada8-121">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
