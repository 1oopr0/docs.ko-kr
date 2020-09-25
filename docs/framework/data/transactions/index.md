---
title: '트랜잭션 처리 '
description: .NET에서 트랜잭션 처리를 검토 합니다. 트랜잭션은 모든 작업이 성공적으로 완료 되지 않는 한 데이터 지향 리소스가 영구적으로 업데이트 되지 않도록 합니다.
ms.date: 03/30/2017
ms.assetid: effdc8e6-accf-41eb-98a5-431603ba218b
ms.openlocfilehash: bbf2448128da7df8af415ff5dea7e3cd8af24d1e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186811"
---
# <a name="transaction-processing"></a><span data-ttu-id="27f48-104">트랜잭션 처리</span><span class="sxs-lookup"><span data-stu-id="27f48-104">Transaction Processing</span></span>

<span data-ttu-id="27f48-105">온라인 서점에서 책을 구입하는 경우 책과 교환하여 신용 지불 형식으로 돈을 지불합니다.</span><span class="sxs-lookup"><span data-stu-id="27f48-105">When you purchase a book from an online bookstore, you exchange money (in the form of credit) for a book.</span></span> <span data-ttu-id="27f48-106">신용이 좋으면 일련의 관련된 작업을 통해 책을 구입할 수 있으며 서점은 돈을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27f48-106">If your credit is good, a series of related operations ensures that you get the book and the bookstore gets your money.</span></span> <span data-ttu-id="27f48-107">그러나 교환 중에 시리즈 중 하나의 작업이 실패하면 전체 교환이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="27f48-107">However, if a single operation in the series fails during the exchange, the entire exchange fails.</span></span> <span data-ttu-id="27f48-108">책을 구입할 수 없고 서점도 돈을 받을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="27f48-108">You do not get the book and the bookstore does not get your money.</span></span>  
  
 <span data-ttu-id="27f48-109">이러한 교환의 균형과 예측 가능성을 유지하는 기술을 트랜잭션 처리라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="27f48-109">The technology responsible for making the exchange balanced and predictable is called transaction processing.</span></span> <span data-ttu-id="27f48-110">트랜잭션은 트랜잭션 단위 내의 모든 작업이 성공적으로 완료될 때까지 데이터 지향 리소스가 영구적으로 업데이트되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="27f48-110">Transactions ensure that data-oriented resources are not permanently updated unless all operations within the transactional unit complete successfully.</span></span> <span data-ttu-id="27f48-111">관련된 작업 집합을 완전히 성공하거나 완전히 실패하는 하나의 단위로 결합하면 오류 복구를 단순화하고 애플리케이션의 안정성을 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27f48-111">By combining a set of related operations into a unit that either completely succeeds or completely fails, you can simplify error recovery and make your application more reliable.</span></span>  
  
 <span data-ttu-id="27f48-112">트랜잭션 처리 시스템은 업무 수행에 필요한 일상적인 트랜잭션을 수행하는 트랜잭션 지향 애플리케이션을 호스팅하는 컴퓨터 하드웨어 및 소프트웨어로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="27f48-112">Transaction processing systems consist of computer hardware and software hosting a transaction-oriented application that performs the routine transactions necessary to conduct business.</span></span> <span data-ttu-id="27f48-113">예를 들어 판매 주문 항목, 항공권 예약, 급여, 직원 레코드, 제조 및 운송을 관리하는 시스템이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27f48-113">Examples include systems that manage sales order entry, airline reservations, payroll, employee records, manufacturing, and shipping.</span></span>  
  
 <span data-ttu-id="27f48-114">이 섹션에서는 트랜잭션 처리에 대한 일반 정보와 Microsoft .NET Framework를 사용하여 트랜잭션 애플리케이션과 리소스 관리자를 작성하는 방법과 관련된 정보를 모두 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="27f48-114">This section provides both general information on transaction processing, and specific information on how to write transactional applications and resource managers using the Microsoft .NET Framework.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="27f48-115">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="27f48-115">In This Section</span></span>  

 [<span data-ttu-id="27f48-116">트랜잭션 기본 사항</span><span class="sxs-lookup"><span data-stu-id="27f48-116">Transaction Fundamentals</span></span>](transaction-fundamentals.md)  
 <span data-ttu-id="27f48-117">기본적인 트랜잭션 처리 용어와 개념을 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="27f48-117">Introduces basic transaction processing terms and concepts.</span></span>  
  
 [<span data-ttu-id="27f48-118">System.Transactions에서 제공하는 기능</span><span class="sxs-lookup"><span data-stu-id="27f48-118">Features Provided by System.Transactions</span></span>](features-provided-by-system-transactions.md)  
 <span data-ttu-id="27f48-119">System.Transactions의 기능을 사용하여 고유한 트랜잭션 애플리케이션을 작성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="27f48-119">Discusses how you can use features in System.Transactions to write your own transactional application.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="27f48-120">참조</span><span class="sxs-lookup"><span data-stu-id="27f48-120">Reference</span></span>  

 <xref:System.Transactions>  
 <span data-ttu-id="27f48-121">코드가 트랜잭션에 참여할 수 있도록 하는 클래스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="27f48-121">Provides classes that allow your code to participate in transactions.</span></span> <span data-ttu-id="27f48-122">이 클래스는 분산된 여러 참가자, 여러 단계의 알림 및 지속적인 인리스트먼트가 있는 트랜잭션을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="27f48-122">The classes support transactions with multiple distributed participants, multiple phase notifications, and durable enlistments.</span></span>
