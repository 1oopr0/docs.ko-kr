---
title: Short 데이터 형식
ms.date: 01/31/2018
f1_keywords:
- vb.Short
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- S literal type character [Visual Basic]
- Short data type
- literal type characters [Visual Basic], S
ms.assetid: 65fcbcf3-a841-400e-885e-301497729a8b
ms.openlocfilehash: 176d27c86127dac1d9c9c0231790f7a5c2a2fefc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415559"
---
# <a name="short-data-type-visual-basic"></a><span data-ttu-id="de465-102">Short 데이터 형식 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="de465-102">Short data type (Visual Basic)</span></span>

<span data-ttu-id="de465-103">-32768부터 32767 까지의 값 범위에 해당 하는 부호 있는 16 비트 (2 바이트) 정수를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="de465-103">Holds signed 16-bit (2-byte) integers that range in value from -32,768 through 32,767.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de465-104">설명</span><span class="sxs-lookup"><span data-stu-id="de465-104">Remarks</span></span>  

 <span data-ttu-id="de465-105">`Short`데이터 형식을 사용 하 여의 전체 데이터 너비를 요구 하지 않는 정수 값을 포함 합니다 `Integer` .</span><span class="sxs-lookup"><span data-stu-id="de465-105">Use the `Short` data type to contain integer values that do not require the full data width of `Integer`.</span></span> <span data-ttu-id="de465-106">경우에 따라 공용 언어 런타임에서는 변수를 긴밀 하 게 압축 `Short` 하 고 메모리 사용을 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de465-106">In some cases, the common language runtime can pack your `Short` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="de465-107">`Short`의 기본값은 0입니다.</span><span class="sxs-lookup"><span data-stu-id="de465-107">The default value of `Short` is 0.</span></span>  
  
## <a name="literal-assignments"></a><span data-ttu-id="de465-108">리터럴 할당</span><span class="sxs-lookup"><span data-stu-id="de465-108">Literal assignments</span></span>

<span data-ttu-id="de465-109">`Short`10 진수 리터럴, 16 진수 리터럴, 8 진수 리터럴 또는 (Visual Basic 2017부터) 이진 리터럴을 할당 하 여 변수를 선언 하 고 초기화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de465-109">You can declare and initialize a `Short` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="de465-110">정수 리터럴이 `Short` 범위를 벗어나는 경우(즉 <xref:System.Int16.MinValue?displayProperty=nameWithType>보다 작거나 <xref:System.Int16.MaxValue?displayProperty=nameWithType>보다 큰 경우) 컴파일 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="de465-110">If the integer literal is outside the range of `Short` (that is, if it is less than <xref:System.Int16.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="de465-111">다음 예제에서는 10 진수, 16 진수 및 이진 리터럴로 표현 된 1034와 동일한 정수를 암시적으로 [정수](integer-data-type.md) 에서 값으로 변환 `Short` 합니다.</span><span class="sxs-lookup"><span data-stu-id="de465-111">In the following example, integers equal to 1,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `Short` values.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> <span data-ttu-id="de465-112">접두사 또는를 사용 하 여 `&h` `&H` 16 진수 리터럴을 표시 하거나, 접두사 또는을 사용 하 여 이진 리터럴을 표시 하 고, 접두사 또는를 사용 하 여 `&b` `&B` `&o` `&O` 8 진수 리터럴을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="de465-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="de465-113">10진수 리터럴에는 접두사가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="de465-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="de465-114">Visual Basic 2017부터 `_` 다음 예제와 같이 밑줄 문자를 자릿수 구분 기호로 사용 하 여 가독성을 높일 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de465-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

<span data-ttu-id="de465-115">Visual Basic 15.5부터 `_` 접두사와 16 진수, 이진 또는 8 진수 숫자 사이의 선행 구분 기호로 밑줄 문자 ()를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de465-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="de465-116">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="de465-116">For example:</span></span>

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="de465-117">`S`다음 예제와 같이 숫자 리터럴은 [형식 문자](../../programming-guide/language-features/data-types/type-characters.md) 를 포함 하 여 데이터 형식을 나타낼 수도 있습니다 `Short` .</span><span class="sxs-lookup"><span data-stu-id="de465-117">Numeric literals can also include the `S` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `Short` data type, as the following example shows.</span></span>

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a><span data-ttu-id="de465-118">프로그래밍 팁</span><span class="sxs-lookup"><span data-stu-id="de465-118">Programming tips</span></span>

- <span data-ttu-id="de465-119">**넓혀.**</span><span class="sxs-lookup"><span data-stu-id="de465-119">**Widening.**</span></span> <span data-ttu-id="de465-120">`Short`데이터 형식은,,, 또는로 확대 변환 `Integer` `Long` `Decimal` `Single` `Double` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="de465-120">The `Short` data type widens to `Integer`, `Long`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="de465-121">이는 `Short` 오류 발생 없이 <xref:System.OverflowException?displayProperty=nameWithType>를 이러한 형식 중 하나로 변환할 수 있음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="de465-121">This means you can convert `Short` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="de465-122">**문자를 입력 합니다.**</span><span class="sxs-lookup"><span data-stu-id="de465-122">**Type Characters.**</span></span> <span data-ttu-id="de465-123">리터럴 형식 문자 `S`를 리터럴에 추가하면 `Short` 데이터 형식이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="de465-123">Appending the literal type character `S` to a literal forces it to the `Short` data type.</span></span> <span data-ttu-id="de465-124">`Short`에는 식별자 형식 문자가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="de465-124">`Short` has no identifier type character.</span></span>  
  
- <span data-ttu-id="de465-125">**Framework 형식.**</span><span class="sxs-lookup"><span data-stu-id="de465-125">**Framework Type.**</span></span> <span data-ttu-id="de465-126">.NET Framework에서 해당하는 형식은 <xref:System.Int16?displayProperty=nameWithType> 구조체입니다.</span><span class="sxs-lookup"><span data-stu-id="de465-126">The corresponding type in the .NET Framework is the <xref:System.Int16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de465-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="de465-127">See also</span></span>

- <xref:System.Int16?displayProperty=nameWithType>
- [<span data-ttu-id="de465-128">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="de465-128">Data Types</span></span>](index.md)
- [<span data-ttu-id="de465-129">형식 변환 함수</span><span class="sxs-lookup"><span data-stu-id="de465-129">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="de465-130">변환 요약</span><span class="sxs-lookup"><span data-stu-id="de465-130">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="de465-131">Integer 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="de465-131">Integer Data Type</span></span>](integer-data-type.md)
- [<span data-ttu-id="de465-132">Long 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="de465-132">Long Data Type</span></span>](long-data-type.md)
- [<span data-ttu-id="de465-133">데이터 형식의 효율적 사용</span><span class="sxs-lookup"><span data-stu-id="de465-133">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
