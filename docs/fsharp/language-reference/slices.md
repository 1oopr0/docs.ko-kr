---
title: 조각
description: '기존 F # 데이터 형식에 대 한 조각을 사용 하는 방법 및 다른 데이터 형식에 대 한 사용자 고유의 조각을 정의 하는 방법을 알아봅니다.'
ms.date: 12/23/2019
ms.openlocfilehash: d3ddb2c247c36a85842f565f051372c5f2c9a9e9
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559013"
---
# <a name="slices"></a><span data-ttu-id="ee509-103">조각</span><span class="sxs-lookup"><span data-stu-id="ee509-103">Slices</span></span>

<span data-ttu-id="ee509-104">F #에서 조각은 `GetSlice` 해당 정의 또는 범위 내 [형식 확장](type-extensions.md)에서 메서드를 포함 하는 모든 데이터 형식의 하위 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="ee509-104">In F#, a slice is a subset of any data type that has a `GetSlice` method in its definition or in an in-scope [type extension](type-extensions.md).</span></span> <span data-ttu-id="ee509-105">F # 배열 및 목록과 가장 일반적으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ee509-105">It is most commonly used with F# arrays and lists.</span></span> <span data-ttu-id="ee509-106">이 문서에서는 기존 F # 형식에서 조각을 가져오는 방법 및 사용자 고유의 조각을 정의 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee509-106">This article explains how to take slices from existing F# types and how to define your own slices.</span></span>

<span data-ttu-id="ee509-107">조각은 [인덱서와](./members/indexed-properties.md)비슷하지만 기본 데이터 구조에서 단일 값을 생성 하는 대신 여러 개를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee509-107">Slices are similar to [indexers](./members/indexed-properties.md), but instead of yielding a single value from the underlying data structure, they yield multiple ones.</span></span>

<span data-ttu-id="ee509-108">F #에는 현재 조각화 문자열, 목록, 배열 및 2D 배열에 대 한 기본 지원이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee509-108">F# currently has intrinsic support for slicing strings, lists, arrays, and 2D arrays.</span></span>

## <a name="basic-slicing-with-f-lists-and-arrays"></a><span data-ttu-id="ee509-109">F # 목록 및 배열을 사용 하 여 기본 조각화</span><span class="sxs-lookup"><span data-stu-id="ee509-109">Basic slicing with F# lists and arrays</span></span>

<span data-ttu-id="ee509-110">가장 일반적으로 분리 되는 데이터 형식은 F # 목록 및 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="ee509-110">The most common data types that are sliced are F# lists and arrays.</span></span> <span data-ttu-id="ee509-111">다음 예제에서는 목록을 사용 하 여이 작업을 수행 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ee509-111">The following example demonstrates how to do this with lists:</span></span>

```fsharp
// Generate a list of 100 integers
let fullList = [ 1 .. 100 ]

// Create a slice from indices 1-5 (inclusive)
let smallSlice = fullList.[1..5]
printfn "Small slice: %A" smallSlice

// Create a slice from the beginning to index 5 (inclusive)
let unboundedBeginning = fullList.[..5]
printfn "Unbounded beginning slice: %A" unboundedBeginning

// Create a slice from an index to the end of the list
let unboundedEnd = fullList.[94..]
printfn "Unbounded end slice: %A" unboundedEnd
```

<span data-ttu-id="ee509-112">조각화 된 배열을 조각화 목록 처럼 분리 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ee509-112">Slicing arrays is just like slicing lists:</span></span>

```fsharp
// Generate an array of 100 integers
let fullArray = [| 1 .. 100 |]

// Create a slice from indices 1-5 (inclusive)
let smallSlice = fullArray.[1..5]
printfn "Small slice: %A" smallSlice

// Create a slice from the beginning to index 5 (inclusive)
let unboundedBeginning = fullArray.[..5]
printfn "Unbounded beginning slice: %A" unboundedBeginning

// Create a slice from an index to the end of the list
let unboundedEnd = fullArray.[94..]
printfn "Unbounded end slice: %A" unboundedEnd
```

## <a name="slicing-multidimensional-arrays"></a><span data-ttu-id="ee509-113">다차원 배열 조각화</span><span class="sxs-lookup"><span data-stu-id="ee509-113">Slicing multidimensional arrays</span></span>

<span data-ttu-id="ee509-114">F #은 F # 핵심 라이브러리의 다차원 배열을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee509-114">F# supports multidimensional arrays in the F# core library.</span></span> <span data-ttu-id="ee509-115">1 차원 배열과 마찬가지로 다차원 배열의 조각이 유용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee509-115">As with one-dimensional arrays, slices of multidimensional arrays can also be useful.</span></span> <span data-ttu-id="ee509-116">그러나 추가 차원의 도입은 특정 행과 열의 조각을 가져올 수 있도록 약간 다른 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee509-116">However, the introduction of additional dimensions mandates a slightly different syntax so that you can take slices of specific rows and columns.</span></span>

<span data-ttu-id="ee509-117">다음 예제에서는 2D 배열을 조각화 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ee509-117">The following examples demonstrate how to slice a 2D array:</span></span>

```fsharp
// Generate a 3x3 2D matrix
let A = array2D [[1;2;3];[4;5;6];[7;8;9]]
printfn "Full matrix:\n %A" A

// Take the first row
let row0 = A.[0,*]
printfn "Row 0: %A" row0

// Take the first column
let col0 = A.[*,0]
printfn "Column 0: %A" col0

// Take all rows but only two columns
let subA = A.[*,0..1]
printfn "%A" subA

// Take two rows and all columns
let subA' = A.[0..1,*]
printfn "%A" subA'

// Slice a 2x2 matrix out of the full 3x3 matrix
let twoByTwo = A.[0..1,0..1]
printfn "%A" twoByTwo
```

<span data-ttu-id="ee509-118">F # 핵심 라이브러리는 현재 3D 배열을 정의 하지 않습니다 `GetSlice` .</span><span class="sxs-lookup"><span data-stu-id="ee509-118">The F# core library does not currently define `GetSlice` for 3D arrays.</span></span> <span data-ttu-id="ee509-119">3D 배열 또는 다른 차원의 다른 배열을 조각화 하려는 경우 `GetSlice` 멤버를 직접 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee509-119">If you wish to slice 3D arrays or other arrays of more dimensions, define the `GetSlice` member yourself.</span></span>

## <a name="defining-slices-for-other-data-structures"></a><span data-ttu-id="ee509-120">다른 데이터 구조에 대 한 조각 정의</span><span class="sxs-lookup"><span data-stu-id="ee509-120">Defining slices for other data structures</span></span>

<span data-ttu-id="ee509-121">F # 핵심 라이브러리는 제한 된 형식 집합에 대 한 조각을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee509-121">The F# core library defines slices for a limited set of types.</span></span> <span data-ttu-id="ee509-122">더 많은 데이터 형식에 대 한 조각을 정의 하려는 경우 형식 정의 자체 나 형식 확장에서이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee509-122">If you wish to define slices for more data types, you can do so either in the type definition itself or in a type extension.</span></span>

<span data-ttu-id="ee509-123">예를 들어, <xref:System.ArraySegment%601> 편리한 데이터 조작을 허용 하기 위해 클래스의 조각을 정의 하는 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ee509-123">For example, here's how you might define slices for the <xref:System.ArraySegment%601> class to allow for convenient data manipulation:</span></span>

```fsharp
open System

type ArraySegment<'TItem> with
    member segment.GetSlice(start, finish) =
        let start = defaultArg start 0
        let finish = defaultArg finish segment.Count
        ArraySegment(segment.Array, segment.Offset + start, finish - start)

let arr = ArraySegment [| 1 .. 10 |]
let slice = arr.[2..5] //[ 3; 4; 5]
```

<span data-ttu-id="ee509-124">및 유형을 사용 하는 다른 예는 <xref:System.Span%601> <xref:System.ReadOnlySpan%601> 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ee509-124">Another example using the <xref:System.Span%601> and <xref:System.ReadOnlySpan%601> types:</span></span>

```fsharp
open System

type ReadOnlySpan<'T> with
    member sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e - s)

type Span<'T> with
    member sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e - s)

let printSpan (sp: Span<int>) =
    let arr = sp.ToArray()
    printfn "%A" arr

let sp = [| 1; 2; 3; 4; 5 |].AsSpan()
printSpan sp.[0..] // [|1; 2; 3; 4; 5|]
printSpan sp.[..5] // [|1; 2; 3; 4; 5|]
printSpan sp.[0..3] // [|1; 2; 3|]
printSpan sp.[1..3] // |2; 3|]
```

## <a name="built-in-f-slices-are-end-inclusive"></a><span data-ttu-id="ee509-125">기본 제공 F # 조각은 끝이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ee509-125">Built-in F# slices are end-inclusive</span></span>

<span data-ttu-id="ee509-126">F #의 모든 내장 조각이 끝에 포함 됩니다. 즉, 상한이 조각에 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ee509-126">All intrinsic slices in F# are end-inclusive; that is, the upper bound is included in the slice.</span></span> <span data-ttu-id="ee509-127">시작 인덱스 및 끝 인덱스를 포함 하는 지정 된 조각에 대해 `x` `y` *yth* 값이 결과 조각에 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ee509-127">For a given slice with starting index `x` and ending index `y`, the resulting slice will include the *yth* value.</span></span>

```fsharp
// Define a new list
let xs = [1 .. 10]

printfn "%A" xs.[2..5] // Includes the 5th index
```

## <a name="see-also"></a><span data-ttu-id="ee509-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ee509-128">See also</span></span>

- [<span data-ttu-id="ee509-129">인덱싱된 속성</span><span class="sxs-lookup"><span data-stu-id="ee509-129">Indexed properties</span></span>](./members/indexed-properties.md)
