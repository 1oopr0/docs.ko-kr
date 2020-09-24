---
title: 로컬 메서드 호출
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34b5012-aee9-4994-9364-1d99d12b7463
ms.openlocfilehash: 25aded1aa961e182e8d2d472fca4c5a84b501af1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166172"
---
# <a name="local-method-calls"></a><span data-ttu-id="ee4d6-102">로컬 메서드 호출</span><span class="sxs-lookup"><span data-stu-id="ee4d6-102">Local Method Calls</span></span>

<span data-ttu-id="ee4d6-103">로컬 메서드 호출은 개체 모델 내에서 실행되는 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="ee4d6-103">A local method call is one that is executed within the object model.</span></span> <span data-ttu-id="ee4d6-104">원격 메서드 호출은 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]에서 SQL로 변환하고 실행을 위해 데이터베이스 엔진으로 전송하는 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="ee4d6-104">A remote method call is one that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates to SQL and transmits to the database engine for execution.</span></span> <span data-ttu-id="ee4d6-105">로컬 메서드 호출은 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]에서 호출을 SQL로 변환할 수 없는 경우 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ee4d6-105">Local method calls are needed when [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] cannot translate the call into SQL.</span></span> <span data-ttu-id="ee4d6-106">그렇지 않으면 <xref:System.InvalidOperationException>이 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="ee4d6-106">Otherwise, an <xref:System.InvalidOperationException> is thrown.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="ee4d6-107">예 1</span><span class="sxs-lookup"><span data-stu-id="ee4d6-107">Example 1</span></span>  

 <span data-ttu-id="ee4d6-108">다음 예제에서는 `Order` 클래스를 Northwind 샘플 데이터베이스의 Orders 테이블에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="ee4d6-108">In the following example, an `Order` class is mapped to the Orders table in the Northwind sample database.</span></span> <span data-ttu-id="ee4d6-109">로컬 인스턴스 메서드가 해당 클래스에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="ee4d6-109">A local instance method has been added to the class.</span></span>  
  
 <span data-ttu-id="ee4d6-110">쿼리 1에서 `Order` 클래스의 생성자는 로컬로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="ee4d6-110">In Query 1, the constructor for the `Order` class is executed locally.</span></span> <span data-ttu-id="ee4d6-111">쿼리 2에서 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]이 `LocalInstanceMethod()`를 SQL로 변환을 시도하면 해당 시도는 실패하고 <xref:System.InvalidOperationException> 예외가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="ee4d6-111">In Query 2, if [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tried to translate `LocalInstanceMethod()`into SQL, the attempt would fail and an <xref:System.InvalidOperationException> exception would be thrown.</span></span> <span data-ttu-id="ee4d6-112">그러나 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]에서 로컬 메서드 호출을 지원하기 때문에 쿼리 2에서는 예외를 throw하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ee4d6-112">But because [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides support for local method calls, Query2 will not throw an exception.</span></span>  
  
 [!code-csharp[DlinqLocalMethodCall#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/Program.cs#1)]
 [!code-vb[DlinqLocalMethodCall#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/Module1.vb#1)]  
  
 [!code-csharp[DlinqLocalMethodCall#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/northwind.cs#2)]
 [!code-vb[DlinqLocalMethodCall#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/northwind.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="ee4d6-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ee4d6-113">See also</span></span>

- [<span data-ttu-id="ee4d6-114">배경 정보</span><span class="sxs-lookup"><span data-stu-id="ee4d6-114">Background Information</span></span>](background-information.md)
