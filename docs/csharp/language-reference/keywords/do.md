---
description: do - C# 참조
title: do - C# 참조
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 601231f23a58e8af8339a733677f0bbd92bb4ffc
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89126959"
---
# <a name="do-c-reference"></a><span data-ttu-id="dfedc-103">do(C# 참조)</span><span class="sxs-lookup"><span data-stu-id="dfedc-103">do (C# Reference)</span></span>

<span data-ttu-id="dfedc-104">`do` 문은 지정된 부울 식이 `true`로 계산되는 동안 문 또는 문 블록을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="dfedc-104">The `do` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="dfedc-105">이 식은 각 루프 실행 후 평가되기 때문에 `do-while` 루프가 한 번 이상 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfedc-105">Because that expression is evaluated after each execution of the loop, a `do-while` loop executes one or more times.</span></span> <span data-ttu-id="dfedc-106">이는 0번 이상 실행되는 [while](while.md) 루프와 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="dfedc-106">This differs from the [while](while.md) loop, which executes zero or more times.</span></span>

<span data-ttu-id="dfedc-107">`do` 문 블록 내의 어느 지점에서나 [break](break.md) 문을 사용하여 루프를 중단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfedc-107">At any point within the `do` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="dfedc-108">[continue](continue.md) 문을 사용하여 `while` 식의 계산을 직접 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfedc-108">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="dfedc-109">식이 `true`로 계산될 경우 루프의 첫 번째 문에서 계속 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfedc-109">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="dfedc-110">그렇지 않으면 실행은 루프 뒤에 나오는 첫 번째 문에서 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfedc-110">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="dfedc-111">[goto](goto.md), [return](return.md) 또는 [throw](throw.md) 문으로 `do-while` 루프를 종료할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfedc-111">You can also exit a `do-while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="dfedc-112">예제</span><span class="sxs-lookup"><span data-stu-id="dfedc-112">Example</span></span>

<span data-ttu-id="dfedc-113">다음 예제에서는 `do` 문의 사용법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="dfedc-113">The following example shows the usage of the `do` statement.</span></span> <span data-ttu-id="dfedc-114">**Run**을 선택하여 예제 코드를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="dfedc-114">Select **Run** to run the example code.</span></span> <span data-ttu-id="dfedc-115">그런 다음, 코드를 수정하고 다시 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfedc-115">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[do loop example](snippets/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="dfedc-116">C# 언어 사양</span><span class="sxs-lookup"><span data-stu-id="dfedc-116">C# language specification</span></span>

<span data-ttu-id="dfedc-117">자세한 내용은 [C# 언어 사양](/dotnet/csharp/language-reference/language-specification/introduction)의 [do 문](~/_csharplang/spec/statements.md#the-do-statement) 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dfedc-117">For more information, see [The do statement](~/_csharplang/spec/statements.md#the-do-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="dfedc-118">참조</span><span class="sxs-lookup"><span data-stu-id="dfedc-118">See also</span></span>

- [<span data-ttu-id="dfedc-119">C# 참조</span><span class="sxs-lookup"><span data-stu-id="dfedc-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="dfedc-120">C# 프로그래밍 가이드</span><span class="sxs-lookup"><span data-stu-id="dfedc-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="dfedc-121">C# 키워드</span><span class="sxs-lookup"><span data-stu-id="dfedc-121">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="dfedc-122">while 문</span><span class="sxs-lookup"><span data-stu-id="dfedc-122">while statement</span></span>](while.md)
