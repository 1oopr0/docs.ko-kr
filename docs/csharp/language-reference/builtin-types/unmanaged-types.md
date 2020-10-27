---
description: C#의 관리되지 않는 형식에 관한 자세한 정보
title: 비관리형 형식 - C# 참조
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 4374872af13c94e1a1af6b9f2c431f076c6f7dff
ms.sourcegitcommit: 870bc4b4087510f6fba3c7b1c0d391f02bcc1f3e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2020
ms.locfileid: "92471801"
---
# <a name="unmanaged-types-c-reference"></a><span data-ttu-id="029a1-103">비관리형 형식(C# 참조)</span><span class="sxs-lookup"><span data-stu-id="029a1-103">Unmanaged types (C# reference)</span></span>

<span data-ttu-id="029a1-104">형식이 다음 형식 중 하나인 경우에는 **관리되지 않는 형식** 입니다.</span><span class="sxs-lookup"><span data-stu-id="029a1-104">A type is an **unmanaged type** if it's any of the following types:</span></span>

- <span data-ttu-id="029a1-105">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal` 또는 `bool`</span><span class="sxs-lookup"><span data-stu-id="029a1-105">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal`, or `bool`</span></span>
- <span data-ttu-id="029a1-106">임의의 [열거형](enum.md) 형식</span><span class="sxs-lookup"><span data-stu-id="029a1-106">Any [enum](enum.md) type</span></span>
- <span data-ttu-id="029a1-107">임의의 [포인터](../../programming-guide/unsafe-code-pointers/pointer-types.md) 형식</span><span class="sxs-lookup"><span data-stu-id="029a1-107">Any [pointer](../../programming-guide/unsafe-code-pointers/pointer-types.md) type</span></span>
- <span data-ttu-id="029a1-108">관리되지 않는 형식의 필드만 포함하고 C# 7.3 및 이전 버전에서 사용자 정의된 [구조체](struct.md) 형식은 생성 형식(하나 이상의 형식 인수를 포함하는 형식)이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="029a1-108">Any user-defined [struct](struct.md) type that contains fields of unmanaged types only and, in C# 7.3 and earlier, is not a constructed type (a type that includes at least one type argument)</span></span>

<span data-ttu-id="029a1-109">C# 7.3부터 [`unmanaged` 제약 조건](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint)을 사용하여 형식 매개 변수가 nullable이 아니며 비포인터 및 비관리형 형식임을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="029a1-109">Beginning with C# 7.3, you can use the [`unmanaged` constraint](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to specify that a type parameter is a non-pointer, non-nullable unmanaged type.</span></span>

<span data-ttu-id="029a1-110">C# 8.0부터는 다음 예와 같이 관리되지 않는 형식의 필드만 포함하는 *생성된* 구조체 형식도 관리되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="029a1-110">Beginning with C# 8.0, a *constructed* struct type that contains fields of unmanaged types only is also unmanaged, as the following example shows:</span></span>

[!code-csharp[unmanaged constructed types](snippets/shared/UnmanagedTypes.cs#ProgramExample)]

<span data-ttu-id="029a1-111">제네릭 구조체는 관리되는 구조체 및 관리되지 않는 구조체 형식 모두의 원본일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="029a1-111">A generic struct may be the source of both unmanaged and not unmanaged constructed types.</span></span> <span data-ttu-id="029a1-112">위의 예에서는 제네릭 구조체 `Coords<T>`를 정의하고 관리되지 않는 생성 형식의 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="029a1-112">The preceding example defines a generic struct `Coords<T>` and presents the examples of unmanaged constructed types.</span></span> <span data-ttu-id="029a1-113">관리되지 않는 형식이 아닌 예는 `Coords<object>`입니다.</span><span class="sxs-lookup"><span data-stu-id="029a1-113">The example of not an unmanaged type is `Coords<object>`.</span></span> <span data-ttu-id="029a1-114">관리되지 않는 `object` 형식의 필드가 있기 때문에 관리되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="029a1-114">It's not unmanaged because it has the fields of the `object` type, which is not unmanaged.</span></span> <span data-ttu-id="029a1-115">*모든* 생성 형식을 관리되지 않는 형식으로 하려면 제네릭 구조체의 정의에서 `unmanaged` 제약 조건을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="029a1-115">If you want *all* constructed types to be unmanaged types, use the `unmanaged` constraint in the definition of a generic struct:</span></span>

[!code-csharp[unmanaged constraint in type definition](snippets/shared/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a><span data-ttu-id="029a1-116">C# 언어 사양</span><span class="sxs-lookup"><span data-stu-id="029a1-116">C# language specification</span></span>

<span data-ttu-id="029a1-117">자세한 내용은 [C# 언어 사양](~/_csharplang/spec/introduction.md)의 [포인터 형식](~/_csharplang/spec/unsafe-code.md#pointer-types) 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="029a1-117">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="029a1-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="029a1-118">See also</span></span>

- [<span data-ttu-id="029a1-119">C# 참조</span><span class="sxs-lookup"><span data-stu-id="029a1-119">C# reference</span></span>](../index.md)
- [<span data-ttu-id="029a1-120">포인터 형식</span><span class="sxs-lookup"><span data-stu-id="029a1-120">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="029a1-121">메모리 및 범위 관련 형식</span><span class="sxs-lookup"><span data-stu-id="029a1-121">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="029a1-122">sizeof 연산자</span><span class="sxs-lookup"><span data-stu-id="029a1-122">sizeof operator</span></span>](../operators/sizeof.md)
- [<span data-ttu-id="029a1-123">stackalloc</span><span class="sxs-lookup"><span data-stu-id="029a1-123">stackalloc</span></span>](../operators/stackalloc.md)
