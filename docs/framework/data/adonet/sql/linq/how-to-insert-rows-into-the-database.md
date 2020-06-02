---
title: '방법: 데이터베이스에 행 삽입'
description: 테이블 관련 컬렉션에 LINQ to SQL 개체를 추가 하 여 데이터베이스에 행을 삽입 하는 방법에 대해 알아봅니다. LINQ to SQL는 추가 내용을 SQL INSERT 명령으로 변환 합니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 44d99680-69c7-4879-a732-f6771b334211
ms.openlocfilehash: 39eee6edf59d2adb7de41efd88899050fbe69fd8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286354"
---
# <a name="how-to-insert-rows-into-the-database"></a><span data-ttu-id="7296a-104">방법: 데이터베이스에 행 삽입</span><span class="sxs-lookup"><span data-stu-id="7296a-104">How to: Insert Rows Into the Database</span></span>

<span data-ttu-id="7296a-105">연결 된 컬렉션에 개체를 추가한 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> 다음 변경 내용을 데이터베이스에 전송 하 여 데이터베이스에 행을 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="7296a-105">You insert rows into a database by adding objects to the associated [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> collection and then submitting the changes to the database.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="7296a-106">변경 내용을 적절 한 SQL 명령으로 변환 `INSERT` 합니다.</span><span class="sxs-lookup"><span data-stu-id="7296a-106">translates your changes into the appropriate SQL `INSERT` commands.</span></span>

> [!NOTE]
> <span data-ttu-id="7296a-107">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], `Insert` 및 `Update` 데이터베이스 작업에 대한 `Delete` 기본 메서드를 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7296a-107">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="7296a-108">자세한 내용은 [삽입, 업데이트 및 삭제 작업 사용자 지정](customizing-insert-update-and-delete-operations.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7296a-108">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>
>
> <span data-ttu-id="7296a-109">Visual Studio를 사용 하는 개발자는 개체 관계형 디자이너을 사용 하 여 동일한 목적으로 저장 프로시저를 개발할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7296a-109">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>

<span data-ttu-id="7296a-110">다음 단계에서는 올바른 <xref:System.Data.Linq.DataContext>를 사용하여 사용자가 Northwind 데이터베이스에 연결되는 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="7296a-110">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="7296a-111">자세한 내용은 [방법: 데이터베이스에 연결](how-to-connect-to-a-database.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7296a-111">For more information, see [How to: Connect to a Database](how-to-connect-to-a-database.md).</span></span>

### <a name="to-insert-a-row-into-the-database"></a><span data-ttu-id="7296a-112">데이터베이스에 행을 삽입하려면</span><span class="sxs-lookup"><span data-stu-id="7296a-112">To insert a row into the database</span></span>

1. <span data-ttu-id="7296a-113">전송할 행 데이터가 있는 새 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7296a-113">Create a new object that includes the column data to be submitted.</span></span>

2. <span data-ttu-id="7296a-114">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` 데이터베이스의 대상 테이블과 연결 된 컬렉션에 새 개체를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="7296a-114">Add the new object to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` collection associated with the target table in the database.</span></span>

3. <span data-ttu-id="7296a-115">데이터베이스에 변경 내용을 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="7296a-115">Submit the change to the database.</span></span>

## <a name="example"></a><span data-ttu-id="7296a-116">예제</span><span class="sxs-lookup"><span data-stu-id="7296a-116">Example</span></span>

<span data-ttu-id="7296a-117">다음 코드 예제에서는 `Order` 형식의 새 개체를 만들어 적절한 값을 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="7296a-117">The following code example creates a new object of type `Order` and populates it with appropriate values.</span></span> <span data-ttu-id="7296a-118">그런 다음 새 개체를 `Order` 컬렉션에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7296a-118">It then adds the new object to the `Order` collection.</span></span> <span data-ttu-id="7296a-119">마지막으로 변경 내용을 `Orders` 테이블의 새 행으로 데이터베이스에 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="7296a-119">Finally, it submits the change to the database as a new row in the `Orders` table.</span></span>

[!code-csharp[System.Data.Linq.Table#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#1)]
[!code-vb[System.Data.Linq.Table#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="7296a-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7296a-120">See also</span></span>

- [<span data-ttu-id="7296a-121">방법: 변경 충돌 관리</span><span class="sxs-lookup"><span data-stu-id="7296a-121">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="7296a-122">DataContext 메서드 (O/R 디자이너)</span><span class="sxs-lookup"><span data-stu-id="7296a-122">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="7296a-123">방법: 저장 프로시저를 할당 하 여 업데이트, 삽입 및 삭제 수행 (O/R 디자이너)</span><span class="sxs-lookup"><span data-stu-id="7296a-123">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [<span data-ttu-id="7296a-124">데이터 변경 및 변경 내용 전송</span><span class="sxs-lookup"><span data-stu-id="7296a-124">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
