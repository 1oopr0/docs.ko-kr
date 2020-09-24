---
title: '방법: 엔터티 충돌 정보 검색'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9a02b608-e7bb-4041-a452-a7fed26fd008
ms.openlocfilehash: e8c548ac632454d9c488ebd5f7b471f6759418fb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155876"
---
# <a name="how-to-retrieve-entity-conflict-information"></a><span data-ttu-id="28fab-102">방법: 엔터티 충돌 정보 검색</span><span class="sxs-lookup"><span data-stu-id="28fab-102">How to: Retrieve Entity Conflict Information</span></span>

<span data-ttu-id="28fab-103"><xref:System.Data.Linq.ObjectChangeConflict> 클래스의 개체를 사용하여 <xref:System.Data.Linq.ChangeConflictException> 예외로 인해 발생한 충돌에 대한 정보를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28fab-103">You can use objects of the <xref:System.Data.Linq.ObjectChangeConflict> class to provide information about conflicts revealed by <xref:System.Data.Linq.ChangeConflictException> exceptions.</span></span> <span data-ttu-id="28fab-104">자세한 내용은 [낙관적 동시성: 개요](optimistic-concurrency-overview.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="28fab-104">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="28fab-105">예제</span><span class="sxs-lookup"><span data-stu-id="28fab-105">Example</span></span>  

 <span data-ttu-id="28fab-106">다음 예제에서는 누적된 충돌 목록을 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="28fab-106">The following example iterates through a list of accumulated conflicts.</span></span>  
  
 [!code-csharp[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.objectchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.objectchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="28fab-107">참고 항목</span><span class="sxs-lookup"><span data-stu-id="28fab-107">See also</span></span>

- [<span data-ttu-id="28fab-108">방법: 변경 충돌 관리</span><span class="sxs-lookup"><span data-stu-id="28fab-108">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
