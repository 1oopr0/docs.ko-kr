---
title: Char 데이터 형식
ms.date: 07/20/2015
f1_keywords:
- vb.Char
helpviewer_keywords:
- literal type characters [Visual Basic], C
- Char data type
- C literal type character [Visual Basic]
- data types [Visual Basic], assigning
- Char data type [Visual Basic], character literals
ms.assetid: cd7547a9-7855-4e8e-b216-35d74a362657
ms.openlocfilehash: 3dbbf9f6a2c4079775e05f5d2dcd8704c1ec4259
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387480"
---
# <a name="char-data-type-visual-basic"></a><span data-ttu-id="807ca-102">Char 데이터 형식(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="807ca-102">Char Data Type (Visual Basic)</span></span>

<span data-ttu-id="807ca-103">0에서 65535 사이의 값에 해당 하는 부호 없는 16 비트 (2 바이트) 코드 요소를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="807ca-103">Holds unsigned 16-bit (2-byte) code points ranging in value from 0 through 65535.</span></span> <span data-ttu-id="807ca-104">각 *코드 포인트*또는 문자 코드는 단일 유니코드 문자를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="807ca-104">Each *code point*, or character code, represents a single Unicode character.</span></span>

## <a name="remarks"></a><span data-ttu-id="807ca-105">설명</span><span class="sxs-lookup"><span data-stu-id="807ca-105">Remarks</span></span>

<span data-ttu-id="807ca-106">`Char`단일 문자만 포함 해야 하며의 오버 헤드가 필요 하지 않은 경우 데이터 형식을 사용 합니다 `String` .</span><span class="sxs-lookup"><span data-stu-id="807ca-106">Use the `Char` data type when you need to hold only a single character and do not need the overhead of `String`.</span></span> <span data-ttu-id="807ca-107">일부 경우에는 `Char()` 요소의 배열을 사용 `Char` 하 여 여러 문자를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="807ca-107">In some cases you can use `Char()`, an array of `Char` elements, to hold multiple characters.</span></span>

<span data-ttu-id="807ca-108">의 기본값은 `Char` 코드 포인트가 0 인 문자입니다.</span><span class="sxs-lookup"><span data-stu-id="807ca-108">The default value of `Char` is the character with a code point of 0.</span></span>

## <a name="unicode-characters"></a><span data-ttu-id="807ca-109">유니코드 문자</span><span class="sxs-lookup"><span data-stu-id="807ca-109">Unicode Characters</span></span>

<span data-ttu-id="807ca-110">유니코드의 처음 128 코드 요소 (0 – 127)는 표준 미국 키보드의 문자 및 기호에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="807ca-110">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span></span> <span data-ttu-id="807ca-111">이러한 첫 번째 128 코드 포인트가 ASCII 문자 집합에서 정의 하는 것과 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="807ca-111">These first 128 code points are the same as those the ASCII character set defines.</span></span> <span data-ttu-id="807ca-112">두 번째 128 코드 요소 (128-255)는 특수 문자 (예: 라틴어 기반 영문자, 악센트, 통화 기호 및 분수)를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="807ca-112">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span></span> <span data-ttu-id="807ca-113">유니코드는 전 세계 텍스트 문자, 분음 부호, 수학 및 기술 기호를 비롯 한 다양 한 기호에 대해 나머지 코드 요소 (256-65535)를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="807ca-113">Unicode uses the remaining code points (256-65535) for a wide variety of symbols, including worldwide textual characters, diacritics, and mathematical and technical symbols.</span></span>

<span data-ttu-id="807ca-114"><xref:System.Char.IsDigit%2A>변수에서 및와 같은 메서드 <xref:System.Char.IsPunctuation%2A> 를 사용 `Char` 하 여 유니코드 분류를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="807ca-114">You can use methods like <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on a `Char` variable to determine its Unicode classification.</span></span>

## <a name="type-conversions"></a><span data-ttu-id="807ca-115">형식 변환</span><span class="sxs-lookup"><span data-stu-id="807ca-115">Type Conversions</span></span>

<span data-ttu-id="807ca-116">Visual Basic는와 숫자 형식 사이에서 직접 변환 되지 않습니다 `Char` .</span><span class="sxs-lookup"><span data-stu-id="807ca-116">Visual Basic does not convert directly between `Char` and the numeric types.</span></span> <span data-ttu-id="807ca-117">또는 함수를 사용 하 여 <xref:Microsoft.VisualBasic.Strings.Asc%2A> <xref:Microsoft.VisualBasic.Strings.AscW%2A> `Char` 값을 `Integer` 해당 코드 포인트를 나타내는로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="807ca-117">You can use the <xref:Microsoft.VisualBasic.Strings.Asc%2A> or <xref:Microsoft.VisualBasic.Strings.AscW%2A> function to convert a `Char` value to an `Integer` that represents its code point.</span></span> <span data-ttu-id="807ca-118">또는 함수를 사용 하 여 <xref:Microsoft.VisualBasic.Strings.Chr%2A> <xref:Microsoft.VisualBasic.Strings.ChrW%2A> 값을 `Integer` `Char` 해당 코드 포인트가 있는로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="807ca-118">You can use the <xref:Microsoft.VisualBasic.Strings.Chr%2A> or <xref:Microsoft.VisualBasic.Strings.ChrW%2A> function to convert an `Integer` value to a `Char` that has that code point.</span></span>

<span data-ttu-id="807ca-119">형식 검사 스위치 ( [Option Strict 문](../statements/option-strict-statement.md))가 on 인 경우 리터럴 형식 문자를 데이터 형식으로 식별 하는 단일 문자 문자열 리터럴에 추가 해야 합니다 `Char` .</span><span class="sxs-lookup"><span data-stu-id="807ca-119">If the type checking switch (the [Option Strict Statement](../statements/option-strict-statement.md)) is on, you must append the literal type character to a single-character string literal to identify it as the `Char` data type.</span></span> <span data-ttu-id="807ca-120">다음은 이에 대한 예입니다.</span><span class="sxs-lookup"><span data-stu-id="807ca-120">The following example illustrates this.</span></span> <span data-ttu-id="807ca-121">가 on 이므로 변수에 대 한 첫 번째 할당은 `charVar` 컴파일러 오류 [BC30512](../../misc/bc30512.md) 를 생성 합니다 `Option Strict` .</span><span class="sxs-lookup"><span data-stu-id="807ca-121">The first assignment to the `charVar` variable generates compiler error [BC30512](../../misc/bc30512.md) because `Option Strict` is on.</span></span> <span data-ttu-id="807ca-122">`c`리터럴 형식 문자는 리터럴을 값으로 식별 하기 때문에 두 번째는 성공적으로 컴파일됩니다 `Char` .</span><span class="sxs-lookup"><span data-stu-id="807ca-122">The second compiles successfully because the `c` literal type character identifies the literal as a `Char` value.</span></span>

```vb
Option Strict On

Module CharType
    Public Sub Main()
        Dim charVar As Char

        ' This statement generates compiler error BC30512 because Option Strict is On.  
        charVar = "Z"  

        ' The following statement succeeds because it specifies a Char literal.  
        charVar = "Z"c
    End Sub
End Module
```

## <a name="programming-tips"></a><span data-ttu-id="807ca-123">프로그래밍 팁</span><span class="sxs-lookup"><span data-stu-id="807ca-123">Programming Tips</span></span>

- <span data-ttu-id="807ca-124">**음수.**</span><span class="sxs-lookup"><span data-stu-id="807ca-124">**Negative Numbers.**</span></span> <span data-ttu-id="807ca-125">`Char`는 부호 없는 형식이 며 음수 값을 나타낼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="807ca-125">`Char` is an unsigned type and cannot represent a negative value.</span></span> <span data-ttu-id="807ca-126">어떤 경우에는를 사용 하 여 `Char` 숫자 값을 포함 하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="807ca-126">In any case, you should not use `Char` to hold numeric values.</span></span>

- <span data-ttu-id="807ca-127">**Interop 고려 사항.**</span><span class="sxs-lookup"><span data-stu-id="807ca-127">**Interop Considerations.**</span></span> <span data-ttu-id="807ca-128">.NET Framework 용으로 작성 되지 않은 구성 요소 (예: Automation 또는 COM 개체)와 상호 작용 하는 경우에는 다른 환경에서 문자 형식의 데이터 너비 (8 비트)가 서로 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="807ca-128">If you interface with components not written for the .NET Framework, for example Automation or COM objects, remember that character types have a different data width (8 bits) in other environments.</span></span> <span data-ttu-id="807ca-129">이러한 구성 요소에 8 비트 인수를 전달 하는 경우 `Byte` `Char` 새 Visual Basic 코드에서 대신로 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="807ca-129">If you pass an 8-bit argument to such a component, declare it as `Byte` instead of `Char` in your new Visual Basic code.</span></span>

- <span data-ttu-id="807ca-130">**넓혀.**</span><span class="sxs-lookup"><span data-stu-id="807ca-130">**Widening.**</span></span> <span data-ttu-id="807ca-131">`Char`데이터 형식이로 확대 `String` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="807ca-131">The `Char` data type widens to `String`.</span></span> <span data-ttu-id="807ca-132">즉,로 변환할 수 `Char` `String` 있으며이 발생 하지 않습니다 <xref:System.OverflowException?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="807ca-132">This means you can convert `Char` to `String` and will not encounter a <xref:System.OverflowException?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="807ca-133">**문자를 입력 합니다.**</span><span class="sxs-lookup"><span data-stu-id="807ca-133">**Type Characters.**</span></span> <span data-ttu-id="807ca-134">리터럴 형식 문자를 `C` 단일 문자 문자열 리터럴에 추가 하면 `Char` 데이터 형식이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="807ca-134">Appending the literal type character `C` to a single-character string literal forces it to the `Char` data type.</span></span> <span data-ttu-id="807ca-135">`Char`에는 식별자 형식 문자가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="807ca-135">`Char` has no identifier type character.</span></span>

- <span data-ttu-id="807ca-136">**Framework 형식.**</span><span class="sxs-lookup"><span data-stu-id="807ca-136">**Framework Type.**</span></span> <span data-ttu-id="807ca-137">.NET Framework에서 해당하는 형식은 <xref:System.Char?displayProperty=nameWithType> 구조체입니다.</span><span class="sxs-lookup"><span data-stu-id="807ca-137">The corresponding type in the .NET Framework is the <xref:System.Char?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="807ca-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="807ca-138">See also</span></span>

- <xref:System.Char?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [<span data-ttu-id="807ca-139">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="807ca-139">Data Types</span></span>](index.md)
- [<span data-ttu-id="807ca-140">문자열 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="807ca-140">String Data Type</span></span>](string-data-type.md)
- [<span data-ttu-id="807ca-141">형식 변환 함수</span><span class="sxs-lookup"><span data-stu-id="807ca-141">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="807ca-142">변환 요약</span><span class="sxs-lookup"><span data-stu-id="807ca-142">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="807ca-143">방법: 부호 없는 형식을 사용하는 Windows 함수 호출</span><span class="sxs-lookup"><span data-stu-id="807ca-143">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="807ca-144">데이터 형식의 효율적 사용</span><span class="sxs-lookup"><span data-stu-id="807ca-144">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
