---
title: '방법: 명시적으로 예외 Throw'
description: C# throw 문이나 Visual Basic Throw 문을 사용하여 .NET에서 명시적으로 예외를 throw하는 방법을 알아봅니다.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- exceptions, try/catch blocks
- FileNotFoundException class
- try/catch blocks
- exceptions, throwing
- implicitly throwing exceptions
ms.assetid: 72bdd157-caa9-4478-9ee3-cb4500b84528
ms.openlocfilehash: 2dd939f9edd58ba91ea74df5d6930087849f0560
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662786"
---
# <a name="how-to-explicitly-throw-exceptions"></a><span data-ttu-id="52f0b-103">명시적으로 예외를 throw하는 방법</span><span class="sxs-lookup"><span data-stu-id="52f0b-103">How to explicitly throw exceptions</span></span>

<span data-ttu-id="52f0b-104">C# [`throw`](../../csharp/language-reference/keywords/throw.md) 또는 Visual Basic [`Throw`](../../visual-basic/language-reference/statements/throw-statement.md) 문을 사용하여 명시적으로 예외를 throw할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52f0b-104">You can explicitly throw an exception using the C# [`throw`](../../csharp/language-reference/keywords/throw.md) or the Visual Basic [`Throw`](../../visual-basic/language-reference/statements/throw-statement.md) statement.</span></span> <span data-ttu-id="52f0b-105">`throw` 문을 사용하여 catch된 예외를 다시 throw할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52f0b-105">You can also throw a caught exception again using the `throw` statement.</span></span> <span data-ttu-id="52f0b-106">디버그 시 자세한 정보를 제공하기 위해 다시 throw되는 예외에 정보를 추가하는 것은 좋은 코딩 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="52f0b-106">It is good coding practice to add information to an exception that is re-thrown to provide more information when debugging.</span></span>

<span data-ttu-id="52f0b-107">다음 코드 예제에서는 `try`/`catch` 블록을 사용하여 가능한 <xref:System.IO.FileNotFoundException>을 catch합니다.</span><span class="sxs-lookup"><span data-stu-id="52f0b-107">The following code example uses a `try`/`catch` block to catch a possible <xref:System.IO.FileNotFoundException>.</span></span> <span data-ttu-id="52f0b-108">`try` 블록 뒤에는 <xref:System.IO.FileNotFoundException>을 catch하고 데이터 파일을 찾을 수 없는 경우 콘솔에 메시지를 쓰는 `catch` 블록이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52f0b-108">Following the `try` block is a `catch` block that catches the <xref:System.IO.FileNotFoundException> and writes a message to the console if the data file is not found.</span></span> <span data-ttu-id="52f0b-109">다음 문은 새 <xref:System.IO.FileNotFoundException>을 throw하고 예외에 텍스트 정보를 추가하는 `throw` 문입니다.</span><span class="sxs-lookup"><span data-stu-id="52f0b-109">The next statement is the `throw` statement that throws a new <xref:System.IO.FileNotFoundException> and adds text information to the exception.</span></span>

[!code-csharp[Exception.Throwing#1](~/samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a><span data-ttu-id="52f0b-110">참조</span><span class="sxs-lookup"><span data-stu-id="52f0b-110">See also</span></span>

- [<span data-ttu-id="52f0b-111">예외</span><span class="sxs-lookup"><span data-stu-id="52f0b-111">Exceptions</span></span>](index.md)
