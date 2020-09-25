---
title: '방법: 관련 데이터 필터링'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec8b8f97-5d01-4f31-9b97-d1556df6a4bc
ms.openlocfilehash: e12bab55b03fac3383b98b8ee1c56ab1954ff978
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173460"
---
# <a name="how-to-filter-related-data"></a><span data-ttu-id="e7817-102">방법: 관련 데이터 필터링</span><span class="sxs-lookup"><span data-stu-id="e7817-102">How to: Filter Related Data</span></span>

<span data-ttu-id="e7817-103"><xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> 메서드를 사용하여 검색된 데이터의 양을 제한하기 위한 하위 쿼리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e7817-103">Use the <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method to specify sub-queries to limit the amount of retrieved data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7817-104">예제</span><span class="sxs-lookup"><span data-stu-id="e7817-104">Example</span></span>  

 <span data-ttu-id="e7817-105">다음 예제에서 <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> 메서드는 `Orders`를 오늘 선적되지 되지 않은 것으로 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="e7817-105">In the following example, the <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method limits the `Orders` retrieved to those that have not been shipped today.</span></span> <span data-ttu-id="e7817-106">이 방법을 사용하지 않을 경우 한 개의 하위 집합만 필요한 경우에도 모든 `Orders`가 검색됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7817-106">Without this approach, all `Orders` would have been retrieved even though only a subset is desired.</span></span>  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e7817-107">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e7817-107">See also</span></span>

- [<span data-ttu-id="e7817-108">데이터베이스 쿼리</span><span class="sxs-lookup"><span data-stu-id="e7817-108">Querying the Database</span></span>](querying-the-database.md)
