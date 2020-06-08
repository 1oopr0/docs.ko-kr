---
title: 포인터를 사용하여 바이트 배열을 복사하는 방법 - C# 프로그래밍 가이드
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 8c1afc06fb567a923d604ad53dc26f94178a8d60
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397417"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes-c-programming-guide"></a><span data-ttu-id="b0b19-102">포인터를 사용하여 바이트 배열을 복사하는 방법(C# 프로그래밍 가이드)</span><span class="sxs-lookup"><span data-stu-id="b0b19-102">How to use pointers to copy an array of bytes (C# Programming Guide)</span></span>

<span data-ttu-id="b0b19-103">다음 예제에서는 포인터를 사용하여 배열 간에 바이트를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="b0b19-103">The following example uses pointers to copy bytes from one array to another.</span></span>

<span data-ttu-id="b0b19-104">이 예제에서는 `Copy` 메서드에서 포인터를 사용할 수 있도록 하는 [unsafe](../../language-reference/keywords/unsafe.md) 키워드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b0b19-104">This example uses the [unsafe](../../language-reference/keywords/unsafe.md) keyword, which enables you to use pointers in the `Copy` method.</span></span> <span data-ttu-id="b0b19-105">[fixed](../../language-reference/keywords/fixed-statement.md) 문은 소스 및 대상 배열에 대한 포인터를 선언하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b0b19-105">The [fixed](../../language-reference/keywords/fixed-statement.md) statement is used to declare pointers to the source and destination arrays.</span></span> <span data-ttu-id="b0b19-106">`fixed` 명령문은 소스 및 대상 배열의 위치가 메모리에 *고정*되므로 가비지 수집에 의해 이동되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b0b19-106">The `fixed` statement *pins* the location of the source and destination arrays in memory so that they will not be moved by garbage collection.</span></span> <span data-ttu-id="b0b19-107">`fixed` 블록이 완료되면 배열에 대한 메모리 블록이 고정 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="b0b19-107">The memory blocks for the arrays are unpinned when the `fixed` block is completed.</span></span> <span data-ttu-id="b0b19-108">이 예제의 `Copy` 메서드는 `unsafe` 키워드를 사용하기 때문에 [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) 컴파일러 옵션으로 컴파일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0b19-108">Because the `Copy` method in this example uses the `unsafe` keyword, it must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>

<span data-ttu-id="b0b19-109">이 예제에서는 두 번째 관리되지 않는 포인터보다는 인덱스를 사용하여 두 배열의 요소에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="b0b19-109">This example accesses the elements of both arrays using indices rather than a second unmanaged pointer.</span></span> <span data-ttu-id="b0b19-110">`pSource` 및 `pTarget` 포인터의 선언은 배열을 고정합니다.</span><span class="sxs-lookup"><span data-stu-id="b0b19-110">The declaration of the `pSource` and `pTarget` pointers pins the arrays.</span></span> <span data-ttu-id="b0b19-111">이 기능은 C# 7.3부터 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0b19-111">This feature is available starting with C# 7.3.</span></span>

## <a name="example"></a><span data-ttu-id="b0b19-112">예제</span><span class="sxs-lookup"><span data-stu-id="b0b19-112">Example</span></span>

[!code-csharp[Struct with embedded inline array](snippets/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a><span data-ttu-id="b0b19-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b0b19-113">See also</span></span>

- [<span data-ttu-id="b0b19-114">C# 프로그래밍 가이드</span><span class="sxs-lookup"><span data-stu-id="b0b19-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b0b19-115">안전하지 않은 코드 및 포인터</span><span class="sxs-lookup"><span data-stu-id="b0b19-115">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="b0b19-116">-unsafe(C# 컴파일러 옵션)</span><span class="sxs-lookup"><span data-stu-id="b0b19-116">-unsafe (C# Compiler Options)</span></span>](../../language-reference/compiler-options/unsafe-compiler-option.md)
- [<span data-ttu-id="b0b19-117">가비지 수집</span><span class="sxs-lookup"><span data-stu-id="b0b19-117">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
