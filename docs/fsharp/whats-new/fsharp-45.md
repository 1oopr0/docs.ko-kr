---
title: 'F # 4.5의 새로운 기능-F # 가이드'
description: 'F # 4.5에서 사용할 수 있는 새로운 기능에 대 한 개요를 확인 하세요.'
ms.date: 11/27/2019
ms.openlocfilehash: 2c978c66a4bf231398508cbc1cbb8839228ea8e9
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202358"
---
# <a name="whats-new-in-f-45"></a>F # 4.5의 새로운 기능

F # 4.5은 F # 언어에 대 한 여러 향상 된 기능을 추가 합니다. 이러한 기능 중 상당수가 함께 추가 되어 F #에서 효율적인 코드를 작성 하 고이 코드를 안전 하 게 보장할 수 있습니다. 이렇게 하면 이러한 구문을 사용 하는 경우 언어에 대 한 몇 가지 개념과 많은 양의 컴파일러 분석이 추가 됩니다.

## <a name="get-started"></a>시작

F # 4.5은 모든 .NET Core 배포 및 Visual Studio 도구에서 사용할 수 있습니다. 자세한 내용은 [F #을 (](../get-started/index.md) 를) 시작 하세요.

## <a name="span-and-byref-like-structs"></a>Span 및 byref와 유사한 구조체

<xref:System.Span%601>.Net Core에 도입 된 형식을 사용 하면 강력한 형식의 버퍼를 메모리에 나타낼 수 있습니다. 이제 f #에서 f # 4.5부터 사용할 수 있습니다. 다음 예제에서는 <xref:System.Span%601> 다른 버퍼 표현을 사용 하 여에서 작동 하는 함수를 다시 사용 하는 방법을 보여 줍니다.

```fsharp
let safeSum (bytes: Span<byte>) =
    let mutable sum = 0
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    sum

// managed memory
let arrayMemory = Array.zeroCreate<byte>(100)
let arraySpan = new Span<byte>(arrayMemory)

safeSum(arraySpan) |> printfn "res = %d"

// native memory
let nativeMemory = Marshal.AllocHGlobal(100);
let nativeSpan = new Span<byte>(nativeMemory.ToPointer(), 100)

safeSum(nativeSpan) |> printfn "res = %d"
Marshal.FreeHGlobal(nativeMemory)

// stack memory
let mem = NativePtr.stackalloc<byte>(100)
let mem2 = mem |> NativePtr.toVoidPtr
let stackSpan = Span<byte>(mem2, 100)

safeSum(stackSpan) |> printfn "res = %d"
```

이에 대 한 중요 한 측면은 범위 및 기타 [byref와 비슷한 구조체](../language-reference/structures.md#byreflike-structs) 에는 예기치 않은 방식으로 사용을 제한 하는 컴파일러에서 매우 엄격한 정적 분석이 수행 된다는 것입니다. 이는 F # 4.5에 도입 된 성능, 표현을 및 보안 간의 기본적인 단점입니다.

## <a name="revamped-byrefs"></a>개선 된 byref 배열과 같은

F # 4.5 이전에 F #의 [byref 배열과 같은](../language-reference/byrefs.md) 는 여러 응용 프로그램에 대해 안전 하지 않으며 소리가 들리지 않았습니다. Byref 배열과 같은에 대 한 적합성 문제는 F # 4.5에서 해결 되었으며, 범위 및 byref와 비슷한 구조체에 대해 수행 되는 동일한 정적 분석도 적용 되었습니다.

### <a name="inreft-and-outreft"></a>inref< '> 및 outref< ' t e m>

읽기 전용, 쓰기 전용 및 읽기/쓰기 관리 되는 포인터의 개념을 나타내기 위해 F # 4.5에는 `inref<'T>` `outref<'T>` 각각 읽기 전용 및 쓰기 전용 포인터를 나타내는 형식이 도입 되었습니다. 각에는 서로 다른 의미 체계가 있습니다. 예를 들어에 쓸 수 없습니다 `inref<'T>` .

```fsharp
let f (dt: inref<DateTime>) =
    dt <- DateTime.Now // ERROR - cannot write to an inref!
```

기본적으로 형식 유추는 `inref<'T>` 변경 되지 않은 것으로 선언 된 경우를 제외 하 고는 관리 되는 포인터를 F # 코드의 변경할 수 없는 특성으로 유추 합니다. 쓰기 가능한 항목을 만들려면 해당 `mutable` 주소를 조작 하는 함수 또는 멤버에 해당 주소를 전달 하기 전에 형식을로 선언 해야 합니다. 자세히 알아보려면 [byref 배열과 같은](../language-reference/byrefs.md)를 참조 하세요.

## <a name="readonly-structs"></a>읽기 전용 구조체

F # 4.5부터 다음과 같이 구조체에 주석을 추가할 수 있습니다 <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> .

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

이렇게 하면 구조체에서 변경 가능한 멤버를 선언 하 고, F # 및 c #이 어셈블리에서 사용 될 때이를 readonly로 처리할 수 있는 메타 데이터를 내보낼 수 없습니다. 자세히 알아보려면 [ReadOnly 구조체](../language-reference/structures.md#readonly-structs)를 참조 하세요.

## <a name="void-pointers"></a>Void 포인터

`voidptr`형식은 다음 함수와 같이 F # 4.5에 추가 됩니다.

* `NativePtr.ofVoidPtr`void 포인터를 네이티브 int 포인터로 변환 하려면
* `NativePtr.toVoidPtr`네이티브 int 포인터를 void 포인터로 변환 하려면

이는 void 포인터를 사용 하는 네이티브 구성 요소와 상호 작용할 때 유용 합니다.

## <a name="the-match-keyword"></a>`match!` 키워드

`match!`키워드는 계산 식 내부에서 패턴 일치를 향상 시킵니다.

```fsharp
// Code that returns an asynchronous option
let checkBananaAsync (s: string) =
    async {
        if s = "banana" then
            return Some s
        else
            return None
    }

// Now you can use 'match!'
let funcWithString (s: string) =
    async {
        match! checkBananaAsync s with
        | Some bananaString -> printfn "It's banana!"
        | None -> printfn "%s" s
}
```

이를 통해 옵션 (또는 기타 형식)을 async와 같은 계산 식과 혼합 하는 코드를 줄일 수 있습니다. 자세히 알아보려면 [일치!](../language-reference/computation-expressions.md#match)를 참조 하세요.

## <a name="relaxed-upcasting-requirements-in-array-list-and-sequence-expressions"></a>배열, 목록 및 시퀀스 식의 완화 업캐스팅 요구 사항

배열, 목록 및 시퀀스 식의 내부에서 상속할 수 있는 형식을 혼합 하는 것은 일반적으로 또는를 사용 하 여 파생 형식을 부모 형식으로 업 캐스트 하는 데 필요 했습니다 `:>` `upcast` . 이제 다음과 같이 완화 됩니다.

```fsharp
let x0 : obj list  = [ "a" ] // ok pre-F# 4.5
let x1 : obj list  = [ "a"; "b" ] // ok pre-F# 4.5
let x2 : obj list  = [ yield "a" :> obj ] // ok pre-F# 4.5

let x3 : obj list  = [ yield "a" ] // Now ok for F# 4.5, and can replace x2
```

## <a name="indentation-relaxation-for-array-and-list-expressions"></a>배열 및 목록 식에 대 한 들여쓰기 완화

F # 4.5 이전에는 메서드 호출에 인수로 전달 될 때 배열 및 목록 식을 과도 하 게 들여쓰는 데 필요 합니다. 더 이상 필요 하지 않습니다.

```fsharp
module NoExcessiveIndenting =
    System.Console.WriteLine(format="{0}", arg = [|
        "hello"
    |])
    System.Console.WriteLine([|
        "hello"
    |])
```
