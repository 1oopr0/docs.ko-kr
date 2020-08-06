---
title: 예외 사용 - C# 프로그래밍 가이드
description: 예외를 사용하는 방법을 알아봅니다. 오류가 발생하는 코드에서 예외를 throw하고, 오류를 수정하는 코드에서 예외를 catch합니다.
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], about exceptions
ms.assetid: 71472c62-320a-470a-97d2-67995180389d
ms.openlocfilehash: fb45381f1c6cfa2f27d036ead8e662b7a0d8d924
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303376"
---
# <a name="use-exceptions-c-programming-guide"></a><span data-ttu-id="7ce14-104">예외 사용(C# 프로그래밍 가이드)</span><span class="sxs-lookup"><span data-stu-id="7ce14-104">Use exceptions (C# programming guide)</span></span>

<span data-ttu-id="7ce14-105">C#에서는 런타임 시 프로그램의 오류가 예외라는 메커니즘을 사용하여 프로그램 전체에 전파됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ce14-105">In C#, errors in the program at run time are propagated through the program by using a mechanism called exceptions.</span></span> <span data-ttu-id="7ce14-106">오류가 발생하는 코드에서 예외를 throw하고, 오류를 수정할 수 있는 코드에서 예외를 catch합니다.</span><span class="sxs-lookup"><span data-stu-id="7ce14-106">Exceptions are thrown by code that encounters an error and caught by code that can correct the error.</span></span> <span data-ttu-id="7ce14-107">.NET 런타임이나 프로그램의 코드에서 예외를 throw할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ce14-107">Exceptions can be thrown by the .NET runtime or by code in a program.</span></span> <span data-ttu-id="7ce14-108">예외가 throw되면 예외에 대한 `catch` 문이 발견될 때까지 호출 스택이 전파됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ce14-108">Once an exception is thrown, it propagates up the call stack until a `catch` statement for the exception is found.</span></span> <span data-ttu-id="7ce14-109">Catch되지 않은 예외는 대화 상자를 표시하는 시스템에서 제공하는 제네릭 예외 처리기에 의해 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ce14-109">Uncaught exceptions are handled by a generic exception handler provided by the system that displays a dialog box.</span></span>  
  
 <span data-ttu-id="7ce14-110">예외는 <xref:System.Exception>에서 파생된 클래스로 표현됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ce14-110">Exceptions are represented by classes derived from <xref:System.Exception>.</span></span> <span data-ttu-id="7ce14-111">이 클래스는 예외의 형식을 식별하며 예외에 대한 세부 정보가 들어 있는 속성을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="7ce14-111">This class identifies the type of exception and contains properties that have details about the exception.</span></span> <span data-ttu-id="7ce14-112">예외를 throw하는 것에는 예외에서 파생된 클래스의 인스턴스를 만드는 것, 선택적으로 예외의 속성을 구성하는 것, 그리고 `throw` 키워드를 사용하여 개체를 throw하는 것이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ce14-112">Throwing an exception involves creating an instance of an exception-derived class, optionally configuring properties of the exception, and then throwing the object by using the `throw` keyword.</span></span> <span data-ttu-id="7ce14-113">예를 들어:</span><span class="sxs-lookup"><span data-stu-id="7ce14-113">For example:</span></span>  
  
 [!code-csharp[csProgGuideExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#1)]  
  
 <span data-ttu-id="7ce14-114">예외가 throw되면 런타임은 현재 문을 확인하여 `try` 블록 내에 있는지 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="7ce14-114">After an exception is thrown, the runtime checks the current statement to see whether it is within a `try` block.</span></span> <span data-ttu-id="7ce14-115">있는 경우, `try` 블록과 연결된 `catch` 블록을 확인하여 예외를 catch할 수 있는지 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="7ce14-115">If it is, any `catch` blocks associated with the `try` block are checked to see whether they can catch the exception.</span></span> <span data-ttu-id="7ce14-116">`Catch` 블록은 일반적으로 예외 형식을 지정합니다. `catch` 블록의 형식이 예외와 동일한 형식이거나 예외의 기본 클래스인 경우 `catch` 블록이 메서드를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ce14-116">`Catch` blocks typically specify exception types; if the type of the `catch` block is the same type as the exception, or a base class of the exception, the `catch` block can handle the method.</span></span> <span data-ttu-id="7ce14-117">예를 들어:</span><span class="sxs-lookup"><span data-stu-id="7ce14-117">For example:</span></span>  
  
 [!code-csharp[csProgGuideExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#2)]  
  
 <span data-ttu-id="7ce14-118">예외를 throw하는 문이 `try` 블록 내에 없거나 이를 감싸는 `try` 블록에 일치하는 `catch` 블록이 없는 경우 런타임은 호출 메서드에서 `try` 문과 `catch` 블록을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7ce14-118">If the statement that throws an exception is not within a `try` block or if the `try` block that encloses it has no matching `catch` block, the runtime checks the calling method for a `try` statement and `catch` blocks.</span></span> <span data-ttu-id="7ce14-119">런타임은 호출 스택까지 계속 확인하여 호환되는 `catch` 블록을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="7ce14-119">The runtime continues up the calling stack, searching for a compatible `catch` block.</span></span> <span data-ttu-id="7ce14-120">`catch` 블록을 찾아서 실행한 후에는 해당 `catch` 블록 다음의 문으로 제어가 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ce14-120">After the `catch` block is found and executed, control is passed to the next statement after that `catch` block.</span></span>  
  
 <span data-ttu-id="7ce14-121">`try` 문은 `catch` 블록을 둘 이상 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ce14-121">A `try` statement can contain more than one `catch` block.</span></span> <span data-ttu-id="7ce14-122">예외를 처리할 수 있는 첫 번째 `catch` 문이 실행됩니다. 그 뒤의 `catch` 문은 호환되더라도 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ce14-122">The first `catch` statement that can handle the exception is executed; any following `catch` statements, even if they are compatible, are ignored.</span></span> <span data-ttu-id="7ce14-123">따라서 catch 블록은 가장 구체적인 것(또는 가장 많이 파생된 것)에서 가장 덜 구체적인 것 순으로 정렬해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ce14-123">Therefore, catch blocks should always be ordered from most specific (or most-derived) to least specific.</span></span> <span data-ttu-id="7ce14-124">예를 들어:</span><span class="sxs-lookup"><span data-stu-id="7ce14-124">For example:</span></span>  
  
 [!code-csharp[csProgGuideExceptions#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#3)]  
  
 <span data-ttu-id="7ce14-125">`catch` 블록이 실행되기 전에 런타임은 `finally` 블록을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7ce14-125">Before the `catch` block is executed, the runtime checks for `finally` blocks.</span></span> <span data-ttu-id="7ce14-126">프로그래머는 `Finally` 블록을 사용해 중단된 `try` 블록으로부터 남겨질 수 있는 모호한 상태를 정리하거나, 런타임 시 가비지 수집기를 기다리지 않은 채 외부 리소스(예: 그래픽 핸들, 데이터베이스 연결 또는 파일 스트림)를 해제하여 개체를 마무리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ce14-126">`Finally` blocks enable the programmer to clean up any ambiguous state that could be left over from an aborted `try` block, or to release any external resources (such as graphics handles, database connections or file streams) without waiting for the garbage collector in the runtime to finalize the objects.</span></span> <span data-ttu-id="7ce14-127">예를 들어:</span><span class="sxs-lookup"><span data-stu-id="7ce14-127">For example:</span></span>  
  
 [!code-csharp[csProgGuideExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#4)]  
  
 <span data-ttu-id="7ce14-128">`WriteByte()`에서 예외를 throw한 경우, `file.Close()`가 호출되지 않으면 파일을 다시 열려고 시도하는 두 번째 `try` 블록이 실패하고 파일이 잠금 상태로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ce14-128">If `WriteByte()` threw an exception, the code in the second `try` block that tries to reopen the file would fail if `file.Close()` is not called, and the file would remain locked.</span></span> <span data-ttu-id="7ce14-129">`finally` 블록은 예외가 throw되도 실행되므로, 이전 예제의 `finally` 블록을 통해 파일을 정확히 닫고 오류를 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ce14-129">Because `finally` blocks are executed even if an exception is thrown, the `finally` block in the previous example allows for the file to be closed correctly and helps avoid an error.</span></span>  
  
 <span data-ttu-id="7ce14-130">예외가 throw된 후 호출 스택에서 호환되는 `catch` 블록을 찾지 못하면 다음 세 가지 중 하나가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="7ce14-130">If no compatible `catch` block is found on the call stack after an exception is thrown, one of three things occurs:</span></span>  
  
- <span data-ttu-id="7ce14-131">예외가 종료자 내부에 있으면 종료자가 중단되고 기본 종료자(있는 경우)가 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ce14-131">If the exception is within a finalizer, the finalizer is aborted and the base finalizer, if any, is called.</span></span>  
  
- <span data-ttu-id="7ce14-132">호출 스택에 정적 생성자 또는 정적 필드 이니셜라이저가 포함된 경우 새 예외의 <xref:System.Exception.InnerException%2A> 속성에 할당된 원래 예외와 함께 <xref:System.TypeInitializationException>이 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ce14-132">If the call stack contains a static constructor, or a static field initializer, a <xref:System.TypeInitializationException> is thrown, with the original exception assigned to the <xref:System.Exception.InnerException%2A> property of the new exception.</span></span>  
  
- <span data-ttu-id="7ce14-133">스레드의 시작에 도달하면 스레드가 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ce14-133">If the start of the thread is reached, the thread is terminated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ce14-134">참조</span><span class="sxs-lookup"><span data-stu-id="7ce14-134">See also</span></span>

- [<span data-ttu-id="7ce14-135">C# 프로그래밍 가이드</span><span class="sxs-lookup"><span data-stu-id="7ce14-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="7ce14-136">예외 및 예외 처리</span><span class="sxs-lookup"><span data-stu-id="7ce14-136">Exceptions and Exception Handling</span></span>](./index.md)
