---
title: String.Split(C# 가이드)를 사용하여 문자열을 구문 분석하는 방법
description: String.Split은 구분 기호 집합에서 분리된 문자열 배열을 반환합니다. 문자열을 구문 분석하는 쉬운 방법입니다.
ms.date: 01/03/2018
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
ms.custom: mvc
ms.openlocfilehash: 4f0056426fb29ec3d76093e57fa45e2046f27a4f
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662994"
---
# <a name="how-to-parse-strings-using-stringsplit-in-c"></a><span data-ttu-id="95416-104">C\#에서 String.Split을 사용하여 문자열을 구문 분석하는 방법</span><span class="sxs-lookup"><span data-stu-id="95416-104">How to parse strings using String.Split in C\#</span></span>

<span data-ttu-id="95416-105"><xref:System.String.Split%2A?displayProperty=nameWithType> 메서드는 하나 이상의 구분 기호를 기준으로 입력 문자열을 분할하여 부분 문자열 배열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="95416-105">The <xref:System.String.Split%2A?displayProperty=nameWithType> method creates an array of substrings by splitting the input string based on one or more delimiters.</span></span> <span data-ttu-id="95416-106">종종 단어 경계에서 문자열을 분리하는 가장 쉬운 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="95416-106">It is often the easiest way to separate a string on word boundaries.</span></span> <span data-ttu-id="95416-107">다른 특정 문자 또는 문자열에서 문자열을 분할하는 데도 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="95416-107">It is also used to split strings on other specific characters or strings.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="95416-108">다음 코드는 공통 어구를 각 단어에 대한 문자열의 배열로 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="95416-108">The following code splits a common phrase into an array of strings for each word.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet1":::

<span data-ttu-id="95416-109">구분 문자의 모든 인스턴스는 반환된 배열에 값을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="95416-109">Every instance of a separator character produces a value in the returned array.</span></span> <span data-ttu-id="95416-110">연속된 구분 문자는 반환된 배열의 값으로 빈 문자열을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="95416-110">Consecutive separator characters produce the empty string as a value in the returned array.</span></span> <span data-ttu-id="95416-111">공백 문자를 구분 기호로 사용하는 다음 예제에서 빈 문자열을 만드는 방법을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95416-111">You can see how an empty string is created in the following example, which uses the space character as a separator.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet2":::

<span data-ttu-id="95416-112">이 동작은 표 형식 데이터를 나타내는 쉼표로 구분된 값(CSV) 파일과 같은 형식을 더 쉽게 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="95416-112">This behavior makes it easier for formats like comma-separated values (CSV) files representing tabular data.</span></span> <span data-ttu-id="95416-113">연속된 쉼표는 빈 열을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="95416-113">Consecutive commas represent a blank column.</span></span>

<span data-ttu-id="95416-114">반환된 배열에 빈 문자열을 제외하기 위해 선택적인 <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> 매개 변수를 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95416-114">You can pass an optional <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parameter to exclude any empty strings in the returned array.</span></span> <span data-ttu-id="95416-115">반환된 컬렉션의 더 복잡한 처리를 위해 [LINQ](../programming-guide/concepts/linq/index.md)를 사용하여 결과 시퀀스를 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95416-115">For more complicated processing of the returned collection, you can use [LINQ](../programming-guide/concepts/linq/index.md) to manipulate the result sequence.</span></span>

<span data-ttu-id="95416-116"><xref:System.String.Split%2A?displayProperty=nameWithType>은 다중 구분 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95416-116"><xref:System.String.Split%2A?displayProperty=nameWithType> can use multiple separator characters.</span></span>
<span data-ttu-id="95416-117">다음 예제에서는 공백, 쉼표, 마침표, 콜론 및 탭을 사용하며, 모두 이러한 구분 문자를 포함하는 배열에서 <xref:System.String.Split%2A>로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="95416-117">The following example uses spaces, commas, periods, colons, and tabs, all passed in an array containing these separating characters, to <xref:System.String.Split%2A>.</span></span>
<span data-ttu-id="95416-118">코드 맨 아래의 루프는 반환된 배열의 각 단어를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="95416-118">The loop at the bottom of the code displays each of the words in the returned array.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet3":::

<span data-ttu-id="95416-119">연속되는 모든 구분 기호의 인스턴스는 출력 배열에 빈 문자열을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="95416-119">Consecutive instances of any separator produce the empty string in the output array:</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet4":::

<span data-ttu-id="95416-120"><xref:System.String.Split%2A?displayProperty=nameWithType>은 문자열 배열(단일 문자 대신 대상 문자열을 구문 분석하는 구분 기호 역할을 하는 문자 시퀀스)을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95416-120"><xref:System.String.Split%2A?displayProperty=nameWithType> can take an array of strings (character sequences that act as separators for parsing the target string, instead of single characters).</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet5":::

## <a name="see-also"></a><span data-ttu-id="95416-121">참조</span><span class="sxs-lookup"><span data-stu-id="95416-121">See also</span></span>

- [<span data-ttu-id="95416-122">C# 프로그래밍 가이드</span><span class="sxs-lookup"><span data-stu-id="95416-122">C# programming guide</span></span>](../programming-guide/index.md)
- [<span data-ttu-id="95416-123">문자열</span><span class="sxs-lookup"><span data-stu-id="95416-123">Strings</span></span>](../programming-guide/strings/index.md)
- [<span data-ttu-id="95416-124">.NET 정규식</span><span class="sxs-lookup"><span data-stu-id="95416-124">.NET regular expressions</span></span>](../../standard/base-types/regular-expressions.md)
