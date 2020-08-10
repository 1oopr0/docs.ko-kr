---
title: finally를 사용하여 정리 코드를 실행하는 방법 - C# 프로그래밍 가이드
description: "'finally' 문을 사용하여 정리 코드를 실행하는 방법을 알아봅니다. Finally 문은 필요한 개체 정리가 즉시 발생하도록 합니다."
ms.date: 07/20/2015
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: 148c1f9fba67659a07c667bb15619d6f3f7c3b2f
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302024"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a><span data-ttu-id="1048f-104">finally를 사용하여 정리 코드를 실행하는 방법(C# 프로그래밍 가이드)</span><span class="sxs-lookup"><span data-stu-id="1048f-104">How to execute cleanup code using finally (C# Programming Guide)</span></span>
<span data-ttu-id="1048f-105">`finally` 문은 예외가 throw된 경우에도 개체, 일반적으로 외부 리소스를 포함하는 개체의 필요한 정리가 즉시 수행되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="1048f-105">The purpose of a `finally` statement is to ensure that the necessary cleanup of objects, usually objects that are holding external resources, occurs immediately, even if an exception is thrown.</span></span> <span data-ttu-id="1048f-106">이러한 정리 작업의 한 가지 예로 다음과 같이 개체가 공용 언어 런타임에 의해 수집될 때까지 기다리지 않고 사용 후 즉시 <xref:System.IO.FileStream>에서 <xref:System.IO.Stream.Close%2A>를 호출하는 것을 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1048f-106">One example of such cleanup is calling <xref:System.IO.Stream.Close%2A> on a <xref:System.IO.FileStream> immediately after use instead of waiting for the object to be garbage collected by the common language runtime, as follows:</span></span>  
  
 [!code-csharp[csProgGuideExceptions#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#16)]  
  
## <a name="example"></a><span data-ttu-id="1048f-107">예제</span><span class="sxs-lookup"><span data-stu-id="1048f-107">Example</span></span>  
 <span data-ttu-id="1048f-108">이전 코드를 `try-catch-finally` 문으로 바꾸려면 다음과 같이 정리 코드와 작업 코드를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="1048f-108">To turn the previous code into a `try-catch-finally` statement, the cleanup code is separated from the working code, as follows.</span></span>  
  
 [!code-csharp[csProgGuideExceptions#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#17)]  
  
 <span data-ttu-id="1048f-109">`OpenWrite()` 호출 또는 `OpenWrite()` 호출 자체가 실패하기 전에 `try` 블록 내에서 언제든지 예외가 발생할 수 있으므로 파일을 닫으려고 할 때 열려 있다는 보장은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1048f-109">Because an exception can occur at any time within the `try` block before the `OpenWrite()` call, or the `OpenWrite()` call itself could fail, we are not guaranteed that the file is open when we try to close it.</span></span> <span data-ttu-id="1048f-110">`finally` 블록은 검사를 추가하여 <xref:System.IO.Stream.Close%2A> 메서드를 호출하기 전에 <xref:System.IO.FileStream> 개체가 `null`이 아닌지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="1048f-110">The `finally` block adds a check to make sure that the <xref:System.IO.FileStream> object is not `null` before you call the <xref:System.IO.Stream.Close%2A> method.</span></span> <span data-ttu-id="1048f-111">`null` 검사가 없으면 `finally` 블록에서 고유한 <xref:System.NullReferenceException>을 throw할 수 있지만 가능하면 `finally` 블록에서 예외를 throw하지 않도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1048f-111">Without the `null` check, the `finally` block could throw its own <xref:System.NullReferenceException>, but throwing exceptions in `finally` blocks should be avoided if it is possible.</span></span>  
  
 <span data-ttu-id="1048f-112">데이터베이스 연결은 `finally` 블록에서 닫기에 적합한 또 다른 후보입니다.</span><span class="sxs-lookup"><span data-stu-id="1048f-112">A database connection is another good candidate for being closed in a `finally` block.</span></span> <span data-ttu-id="1048f-113">데이터베이스 서버에 허용되는 연결 수가 제한된 경우도 있으므로 최대한 빨리 데이터베이스 연결을 닫아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1048f-113">Because the number of connections allowed to a database server is sometimes limited, you should close database connections as quickly as possible.</span></span> <span data-ttu-id="1048f-114">연결을 닫기 전에 예외가 throw되는 경우에도 `finally` 블록 사용이 가비지 수집을 기다리는 것보다 더 낫습니다.</span><span class="sxs-lookup"><span data-stu-id="1048f-114">If an exception is thrown before you can close your connection, this is another case where using the `finally` block is better than waiting for garbage collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1048f-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1048f-115">See also</span></span>

- [<span data-ttu-id="1048f-116">C# 프로그래밍 가이드</span><span class="sxs-lookup"><span data-stu-id="1048f-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1048f-117">예외 및 예외 처리</span><span class="sxs-lookup"><span data-stu-id="1048f-117">Exceptions and Exception Handling</span></span>](./index.md)
- [<span data-ttu-id="1048f-118">예외 처리</span><span class="sxs-lookup"><span data-stu-id="1048f-118">Exception Handling</span></span>](./exception-handling.md)
- [<span data-ttu-id="1048f-119">using 문</span><span class="sxs-lookup"><span data-stu-id="1048f-119">using Statement</span></span>](../../language-reference/keywords/using-statement.md)
- [<span data-ttu-id="1048f-120">try-catch</span><span class="sxs-lookup"><span data-stu-id="1048f-120">try-catch</span></span>](../../language-reference/keywords/try-catch.md)
- [<span data-ttu-id="1048f-121">try-finally</span><span class="sxs-lookup"><span data-stu-id="1048f-121">try-finally</span></span>](../../language-reference/keywords/try-finally.md)
- [<span data-ttu-id="1048f-122">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="1048f-122">try-catch-finally</span></span>](../../language-reference/keywords/try-catch-finally.md)
