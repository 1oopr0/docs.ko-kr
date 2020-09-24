---
title: 의
ms.date: 09/08/2020
description: 트랜잭션을 사용하는 방법을 알아봅니다.
ms.openlocfilehash: 50c4cd1023eac892cafc3ae4395e9168bd8e9f36
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90678864"
---
# <a name="transactions"></a><span data-ttu-id="bc4b8-103">의</span><span class="sxs-lookup"><span data-stu-id="bc4b8-103">Transactions</span></span>

<span data-ttu-id="bc4b8-104">트랜잭션을 사용하면 여러 SQL 문을 하나의 원자 단위로 데이터베이스에 커밋된 단일 작업 단위로 그룹화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc4b8-104">Transactions let you group multiple SQL statements into a single unit of work that is committed to the database as one atomic unit.</span></span> <span data-ttu-id="bc4b8-105">트랜잭션의 명령문이 실패하면 이전 명령문에서 변경한 내용을 롤백할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc4b8-105">If any statement in the transaction fails, changes made by the previous statements can be rolled back.</span></span> <span data-ttu-id="bc4b8-106">트랜잭션이 시작될 때 데이터베이스의 초기 상태는 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc4b8-106">The initial state of the database when the transaction was started is preserved.</span></span> <span data-ttu-id="bc4b8-107">트랜잭션을 사용하면 데이터베이스를 동시에 여러 번 변경할 때 SQLite의 성능을 개선할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc4b8-107">Using a transaction can also improve performance on SQLite when making numerous changes to the database at once.</span></span>

## <a name="concurrency"></a><span data-ttu-id="bc4b8-108">동시성</span><span class="sxs-lookup"><span data-stu-id="bc4b8-108">Concurrency</span></span>

<span data-ttu-id="bc4b8-109">SQLite에서는 한 번에 하나의 트랜잭션만 데이터베이스에 보류 중인 변경 내용을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc4b8-109">In SQLite, only one transaction is allowed to have changes pending in the database at a time.</span></span> <span data-ttu-id="bc4b8-110">이로 인해 다른 트랜잭션을 완료하는 데 시간이 너무 오래 걸리면 <xref:Microsoft.Data.Sqlite.SqliteConnection.BeginTransaction%2A> 및 <xref:Microsoft.Data.Sqlite.SqliteCommand>의 `Execute` 메서드에 대한 호출이 시간 초과될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc4b8-110">Because of this, calls to <xref:Microsoft.Data.Sqlite.SqliteConnection.BeginTransaction%2A> and the `Execute` methods on <xref:Microsoft.Data.Sqlite.SqliteCommand> may time out if another transaction takes too long to complete.</span></span>

<span data-ttu-id="bc4b8-111">잠금, 다시 시도 및 시간 제한에 대한 자세한 내용은 [데이터 베이스 오류](database-errors.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bc4b8-111">For more information about locking, retries, and timeouts, see [Database errors](database-errors.md).</span></span>

## <a name="isolation-levels"></a><span data-ttu-id="bc4b8-112">격리 수준</span><span class="sxs-lookup"><span data-stu-id="bc4b8-112">Isolation levels</span></span>

<span data-ttu-id="bc4b8-113">트랜잭션은 기본적으로 SQLite에서 **직렬화 가능**입니다.</span><span class="sxs-lookup"><span data-stu-id="bc4b8-113">Transactions are **serializable** by default in SQLite.</span></span> <span data-ttu-id="bc4b8-114">이 격리 수준은 트랜잭션 내에서 수행된 모든 변경 내용이 완전히 격리되도록 보장합니다.</span><span class="sxs-lookup"><span data-stu-id="bc4b8-114">This isolation level guarantees that any changes made within a transaction are completely isolated.</span></span> <span data-ttu-id="bc4b8-115">트랜잭션 외부에서 실행된 다른 명령문은 트랜잭션의 변경 내용에 의해 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bc4b8-115">Other statements executed outside of the transaction aren't affected by the transaction's changes.</span></span>

<span data-ttu-id="bc4b8-116">SQLite는 공유 캐시를 사용할 때 **커밋되지 않은 읽기**도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="bc4b8-116">SQLite also supports **read uncommitted** when using a shared cache.</span></span> <span data-ttu-id="bc4b8-117">이 수준은 커밋되지 않은 데이터 읽기, 반복되지 않는 읽기 및 팬텀을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="bc4b8-117">This level allows dirty reads, nonrepeatable reads, and phantoms:</span></span>

- <span data-ttu-id="bc4b8-118">한 트랜잭션에서 보류 중인 변경 내용이 트랜잭션 외부의 쿼리에 의해 반환될 때 *커밋되지 않은 데이터 읽기*가 발생하지만 트랜잭션의 변경 내용은 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc4b8-118">A *dirty read* occurs when changes pending in one transaction are returned by a query outside of the transaction, but the changes in the transaction are rolled back.</span></span> <span data-ttu-id="bc4b8-119">결과에는 실제로 데이터베이스에 커밋되지 않은 데이터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc4b8-119">The results contain data that was never actually committed to the database.</span></span>

- <span data-ttu-id="bc4b8-120">*반복되지 않는 읽기*는 트랜잭션이 동일한 행을 두 번 쿼리할 때 발생하지만 다른 트랜잭션에 의해 두 쿼리 간에 변경되었기 때문에 결과가 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="bc4b8-120">A *nonrepeatable read* occurs when a transaction queries same row twice, but the results are different because it was changed between the two queries by another transaction.</span></span>

- <span data-ttu-id="bc4b8-121">*팬텀*은 트랜잭션 중에 쿼리의 where 절을 충족하기 위해 변경되거나 추가되는 행입니다.</span><span class="sxs-lookup"><span data-stu-id="bc4b8-121">*Phantoms* are rows that get changed or added to meet the where clause of a query during a transaction.</span></span> <span data-ttu-id="bc4b8-122">허용되는 경우 동일한 트랜잭션에서 두 번 실행될 때 동일한 쿼리가 다른 행을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc4b8-122">If allowed, the same query could return different rows when executed twice in the same transaction.</span></span>

<span data-ttu-id="bc4b8-123">Microsoft.Data.Sqlite는 <xref:Microsoft.Data.Sqlite.SqliteConnection.BeginTransaction%2A>에 전달된 IsolationLevel을 최소 수준으로 취급합니다.</span><span class="sxs-lookup"><span data-stu-id="bc4b8-123">Microsoft.Data.Sqlite treats the IsolationLevel passed to <xref:Microsoft.Data.Sqlite.SqliteConnection.BeginTransaction%2A> as a minimum level.</span></span> <span data-ttu-id="bc4b8-124">실제 격리 수준은 커밋되지 않은 읽기 또는 직렬화 가능 수준으로 승격됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc4b8-124">The actual isolation level will be promoted to either read uncommitted or serializable.</span></span>

<span data-ttu-id="bc4b8-125">다음 코드는 커밋되지 않은 데이터 읽기를 시뮬레이션합니다.</span><span class="sxs-lookup"><span data-stu-id="bc4b8-125">The following code simulates a dirty read.</span></span> <span data-ttu-id="bc4b8-126">참고: 연결 문자열에는 `Cache=Shared`가 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc4b8-126">Note, the connection string must include `Cache=Shared`.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DirtyReadSample/Program.cs?name=snippet_DirtyRead)]

## <a name="deferred-transactions"></a><span data-ttu-id="bc4b8-127">지연된 트랜잭션</span><span class="sxs-lookup"><span data-stu-id="bc4b8-127">Deferred transactions</span></span>

<span data-ttu-id="bc4b8-128">Microsoft.Data.Sqlite 버전 5.0부터는 트랜잭션이 지연될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc4b8-128">Starting with Microsoft.Data.Sqlite version 5.0, transactions can be deferred.</span></span> <span data-ttu-id="bc4b8-129">이렇게 되면 첫 번째 명령이 실행될 때까지 데이터베이스에서 실제 트랜잭션 생성이 지연됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc4b8-129">This defers the creation of the actual transaction in the database until the first command is executed.</span></span> <span data-ttu-id="bc4b8-130">또한 해당 명령에서 필요한 경우 트랜잭션이 점진적으로 읽기 트랜잭선에서 쓰기 트랜잭션으로 업그레이드됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc4b8-130">It also causes the transaction to gradually upgrade from a read transaction to a write transaction as needed by its commands.</span></span> <span data-ttu-id="bc4b8-131">트랜잭션 도중에 데이터베이스에 대한 동시 액세스를 사용하도록 설정하는 데 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc4b8-131">This can be useful for enabling concurrent access to the database during the transaction.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DeferredTransactionSample/Program.cs?name=snippet_DeferredTransaction)]

> [!WARNING]
> <span data-ttu-id="bc4b8-132">데이터베이스가 잠겨 있는 동안 트랜잭션이 읽기 트랜잭션에서 쓰기 트랜잭션으로 업그레이드되는 경우 지연된 트랜잭션 내의 명령이 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc4b8-132">Commands inside a deferred transaction can fail if they cause the transaction to be upgraded from a read transaction to a write transaction while the database is locked.</span></span> <span data-ttu-id="bc4b8-133">이 경우 애플리케이션은 전체 트랜잭션을 다시 시도해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc4b8-133">When this happens, the application will need to retry the entire transaction.</span></span>
