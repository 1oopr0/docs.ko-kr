---
title: '방법: 문자열이 올바른 전자 메일 형식인지 확인'
description: .NET에서 정규식을 통해 문자열이 유효한 전자 메일 형식인지 확인하는 방법의 예제를 찹조하세요.
ms.date: 12/10/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, examples
- user input, examples
- Regex.IsMatch method
- regular expressions [.NET Framework], examples
- examples [Visual Basic], strings
- IsValidEmail
- validation, email strings
- input, checking
- strings [.NET Framework], examples [Visual Basic]
- email [.NET Framework], validating
- IsMatch method
ms.assetid: 7536af08-4e86-4953-98a1-a8298623df92
ms.openlocfilehash: 47ef4dedd20a2b885abaabf72c26de5f3312c66f
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768965"
---
# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a><span data-ttu-id="2c238-103">방법: 문자열이 올바른 전자 메일 형식인지 확인</span><span class="sxs-lookup"><span data-stu-id="2c238-103">How to verify that strings are in valid email format</span></span>

<span data-ttu-id="2c238-104">다음 예제에서는 정규식을 사용하여 문자열이 올바른 전자 메일 형식인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-104">The following example uses a regular expression to verify that a string is in valid email format.</span></span>

## <a name="example"></a><span data-ttu-id="2c238-105">예제</span><span class="sxs-lookup"><span data-stu-id="2c238-105">Example</span></span>

<span data-ttu-id="2c238-106">이 예제에서는 문자열에 올바른 전자 메일 주소가 포함되어 있으면 `IsValidEmail` 를 반환하고, 그렇지 않으면 `true` 를 반환하지만 다른 작업을 수행하지 않는 `false` 메서드를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-106">The example defines an `IsValidEmail` method, which returns `true` if the string contains a valid email address and `false` if it does not, but takes no other action.</span></span>

<span data-ttu-id="2c238-107">전자 메일 주소가 올바른지 확인하기 위해 `IsValidEmail` 메서드는 <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> 정규식 패턴으로 `(@)(.+)$` 메서드를 호출하여 전자 메일 주소에서 도메인 이름을 분리합니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-107">To verify that the email address is valid, the `IsValidEmail` method calls the <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> method with the `(@)(.+)$` regular expression pattern to separate the domain name from the email address.</span></span> <span data-ttu-id="2c238-108">세 번째 매개 변수는 일치하는 텍스트를 처리하고 대체하는 메서드를 나타내는 <xref:System.Text.RegularExpressions.MatchEvaluator> 대리자입니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-108">The third parameter is a <xref:System.Text.RegularExpressions.MatchEvaluator> delegate that represents the method that processes and replaces the matched text.</span></span> <span data-ttu-id="2c238-109">정규식 패턴은 다음과 같이 해석됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-109">The regular expression pattern is interpreted as follows.</span></span>

|<span data-ttu-id="2c238-110">무늬</span><span class="sxs-lookup"><span data-stu-id="2c238-110">Pattern</span></span>|<span data-ttu-id="2c238-111">설명</span><span class="sxs-lookup"><span data-stu-id="2c238-111">Description</span></span>|
|-------------|-----------------|
|`(@)`|<span data-ttu-id="2c238-112">@ 문자를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-112">Match the @ character.</span></span> <span data-ttu-id="2c238-113">이 그룹은 첫 번째 캡처링 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-113">This is the first capturing group.</span></span>|
|`(.+)`|<span data-ttu-id="2c238-114">하나 이상의 문자를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-114">Match one or more occurrences of any character.</span></span> <span data-ttu-id="2c238-115">이 그룹은 두 번째 캡처링 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-115">This is the second capturing group.</span></span>|
|`$`|<span data-ttu-id="2c238-116">문자열의 끝 부분에서 일치 항목 찾기를 끝냅니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-116">End the match at the end of the string.</span></span>|

<span data-ttu-id="2c238-117">@ 문자와 함께 도메인 이름이 `DomainMapper` 메서드로 전달됩니다. 이 메서드는 <xref:System.Globalization.IdnMapping> 클래스를 사용하여 US-ASCII 문자 범위 외부에 있는 유니코드 문자를 Punycode로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-117">The domain name along with the @ character is passed to the `DomainMapper` method, which uses the <xref:System.Globalization.IdnMapping> class to translate Unicode characters that are outside the US-ASCII character range to Punycode.</span></span> <span data-ttu-id="2c238-118">이 메서드는 `invalid` 메서드가 도메인 이름에서 잘못된 문자를 발견하는 경우 `True` 플래그를 <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-118">The method also sets the `invalid` flag to `True` if the <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> method detects any invalid characters in the domain name.</span></span> <span data-ttu-id="2c238-119">메서드는 앞에 @ 기호가 있는 Punycode 도메인 이름을 `IsValidEmail` 메서드에 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-119">The method returns the Punycode domain name preceded by the @ symbol to the `IsValidEmail` method.</span></span>

<span data-ttu-id="2c238-120">그러면 `IsValidEmail` 메서드는 <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> 메서드를 호출하여 주소가 정규식 패턴을 따르는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-120">The `IsValidEmail` method then calls the <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> method to verify that the address conforms to a regular expression pattern.</span></span>

<span data-ttu-id="2c238-121">`IsValidEmail` 메서드는 전자 메일 주소의 유효성을 검사하기 위해 인증을 수행하는 것이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-121">Note that the `IsValidEmail` method does not perform authentication to validate the email address.</span></span> <span data-ttu-id="2c238-122">단지 형식이 전자 메일 주소에 올바른지 여부만 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-122">It merely determines whether its format is valid for an email address.</span></span> <span data-ttu-id="2c238-123">또한 `IsValidEmail` 메서드는 최상위 도메인 이름이 조회 작업 시 요구되는 [IANA 루트 영역 데이터베이스](https://www.iana.org/domains/root/db)에 나열된 올바른 도메인 이름인지 확인하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-123">In addition, the `IsValidEmail` method does not verify that the top-level domain name is a valid domain name listed at the [IANA Root Zone Database](https://www.iana.org/domains/root/db), which would require a look-up operation.</span></span> <span data-ttu-id="2c238-124">대신, 정규식은 최상위 도메인 이름이 2~24개의 ASCII 문자(첫 번째 문자와 마지막 문자는 영숫자이고, 나머지 문자는 영숫자이거나 하이픈(-)임)로 구성되었는지만 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-124">Instead, the regular expression merely verifies that the top-level domain name consists of between two and twenty-four ASCII characters, with alphanumeric first and last characters and the remaining characters being either alphanumeric or a hyphen (-).</span></span>

[!code-csharp[RegularExpressions.Examples.Email#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#7)]
[!code-vb[RegularExpressions.Examples.Email#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#7)]

<span data-ttu-id="2c238-125">이 예제에서 정규식 패턴 ``^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*)(?<=[0-9a-z])@))(?(\[)(\[(\d{1,3}\.){3}\d{1,3}\])|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))$``는 다음 범례와 같이 해석됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-125">In this example, the regular expression pattern ``^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*)(?<=[0-9a-z])@))(?(\[)(\[(\d{1,3}\.){3}\d{1,3}\])|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))$`` is interpreted as shown in the following legend.</span></span> <span data-ttu-id="2c238-126">정규식은 <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> 플래그를 사용하여 컴파일됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-126">The regular expression is compiled using the <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> flag.</span></span>

<span data-ttu-id="2c238-127">`^` 패턴: 문자열의 시작 부분에서 일치 항목 찾기를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-127">Pattern `^`: Begin the match at the start of the string.</span></span>

<span data-ttu-id="2c238-128">`(?(")` 패턴: 첫 번째 문자가 따옴표인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-128">Pattern `(?(")`: Determine whether the first character is a quotation mark.</span></span> <span data-ttu-id="2c238-129">`(?(")` 는 대체 구문의 시작 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-129">`(?(")` is the beginning of an alternation construct.</span></span>

<span data-ttu-id="2c238-130">`(?(")(".+?(?<!\\)"@)` 패턴: 첫 번째 문자가 따옴표인 경우 시작 따옴표 뒤에 임의의 문자가 1개 이상 나오고 그 뒤에 끝 따옴표가 나오는 일치 항목을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-130">Pattern `(?(")(".+?(?<!\\)"@)`: If the first character is a quotation mark, match a beginning quotation mark followed by at least one occurrence of any character, followed by an ending quotation mark.</span></span> <span data-ttu-id="2c238-131">끝 따옴표는 앞에 백슬래시 문자(\\)가 없어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-131">The ending quotation mark must not be preceded by a backslash character (\\).</span></span> <span data-ttu-id="2c238-132">`(?<!` 는 너비가 0인 부정 lookbehind 어설션의 시작 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-132">`(?<!` is the beginning of a zero-width negative lookbehind assertion.</span></span> <span data-ttu-id="2c238-133">문자열은 @ 기호로 끝나야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-133">The string should conclude with an at sign (@).</span></span>

<span data-ttu-id="2c238-134">`|(([0-9a-z]` 패턴: 첫 번째 문자가 따옴표가 아니면 a-z 또는 A-Z(비교는 대/소문자를 구분하지 않음)의 영문자 또는 0-9의 숫자를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-134">Pattern `|(([0-9a-z]`: If the first character is not a quotation mark, match any alphabetic character from a to z or A to Z (the comparison is case insensitive), or any numeric character from 0 to 9.</span></span>

<span data-ttu-id="2c238-135">`(\.(?!\.))` 패턴: 다음 문자가 마침표이면 일치하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-135">Pattern `(\.(?!\.))`: If the next character is a period, match it.</span></span> <span data-ttu-id="2c238-136">마침표가 아니면 왼쪽에서 오른쪽으로 다음 문자를 검색하여 일치 항목을 계속 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-136">If it is not a period, look ahead to the next character and continue the match.</span></span> <span data-ttu-id="2c238-137">`(?!\.)` 는 메일 주소의 로컬 부분에 마침표 두 개가 연속으로 나타나지 않도록 하며 너비가 0인 부정 lookahead 어설션입니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-137">`(?!\.)` is a zero-width negative lookahead assertion that prevents two consecutive periods from appearing in the local part of an email address.</span></span>

<span data-ttu-id="2c238-138">``|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w]`` 패턴: 다음 문자가 마침표가 아니면 단어 문자 또는 -!#$%&'\*+/=?^\`{}|~ 문자 중 하나를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-138">Pattern ``|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w]``: If the next character is not a period, match any word character or one of the following characters: -!#$%&'\*+/=?^\`{}|~</span></span>

<span data-ttu-id="2c238-139">``((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*`` 패턴: 교체 패턴(마침표가 아닌 문자 또는 여러 문자 중 하나 앞에 마침표가 있는 패턴)을 0번 이상 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-139">Pattern ``((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*``: Match the alternation pattern (a period followed by a non-period, or one of a number of characters) zero or more times.</span></span>

<span data-ttu-id="2c238-140">`@` 패턴: @ 문자를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-140">Pattern `@`: Match the @ character.</span></span>

<span data-ttu-id="2c238-141">`(?<=[0-9a-z])` 패턴: @ 문자 앞의 문자가 영문자(A-Z, a-z) 또는 숫자(0-9)인 경우 일치 항목 찾기를 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-141">Pattern `(?<=[0-9a-z])`: Continue the match if the character that precedes the @ character is A through Z, a through z, or 0 through 9.</span></span> <span data-ttu-id="2c238-142">이 패턴은 너비가 0인 긍정 lookbehind 어설션을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-142">This pattern defines a zero-width positive lookbehind assertion.</span></span>

<span data-ttu-id="2c238-143">`(?(\[)` 패턴: @ 뒤의 문자가 여는 대괄호인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-143">Pattern `(?(\[)`: Check whether the character that follows @ is an opening bracket.</span></span>

<span data-ttu-id="2c238-144">`(\[(\d{1,3}\.){3}\d{1,3}\])` 패턴: 여는 대괄호이면 IP 주소(1자리에서 3자리까지의 숫자로 이루어진 4개의 집합이며 각 집합은 마침표로 구분됨)와 닫는 대괄호 앞에 있는 여는 대괄호를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-144">Pattern `(\[(\d{1,3}\.){3}\d{1,3}\])`: If it is an opening bracket, match the opening bracket followed by an IP address (four sets of one to three digits, with each set separated by a period) and a closing bracket.</span></span>

<span data-ttu-id="2c238-145">`|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+` 패턴: @ 뒤의 문자가 여는 대괄호가 아니면 영숫자(A-Z, a-z 또는 0-9) 1개, 하이픈 0개 이상, 영숫자(A-Z, a-z 또는 0-9) 0개 또는 1개와 마침표 1개로 구성된 패턴과 일치하는 항목을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-145">Pattern `|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+`: If the character that follows @ is not an opening bracket, match one alphanumeric character with a value of A-Z, a-z, or 0-9, followed by zero or more occurrences of a hyphen, followed by zero or one alphanumeric character with a value of A-Z, a-z, or 0-9, followed by a period.</span></span> <span data-ttu-id="2c238-146">이 패턴은 한 번 이상 반복될 수 있으며, 뒤에 최상위 도메인 이름이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-146">This pattern can be repeated one or more times, and must be followed by the top-level domain name.</span></span>

<span data-ttu-id="2c238-147">`[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))` 패턴: 최상위 도메인 이름은 영숫자(a-z, A-Z 및 0-9)로 시작하고 끝나야 하며,</span><span class="sxs-lookup"><span data-stu-id="2c238-147">Pattern `[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))`: The top-level domain name must begin and end with an alphanumeric character (a-z, A-Z, and 0-9).</span></span> <span data-ttu-id="2c238-148">영숫자이거나 하이픈인 0~22개의 ASCII 문자를 포함할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-148">It can also include from zero to 22 ASCII characters that are either alphanumeric or hyphens.</span></span>

<span data-ttu-id="2c238-149">`$` 패턴: 문자열의 끝 부분에서 일치 항목 찾기를 끝냅니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-149">Pattern `$`: End the match at the end of the string.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="2c238-150">코드 컴파일</span><span class="sxs-lookup"><span data-stu-id="2c238-150">Compile the code</span></span>

<span data-ttu-id="2c238-151">`IsValidEmail` 및 `DomainMapper` 메서드는 정규식 유틸리티 메서드의 라이브러리에 포함되거나 애플리케이션 클래스에서 전용 정적 또는 인스턴스 메서드로 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-151">The `IsValidEmail` and `DomainMapper` methods can be included in a library of regular expression utility methods, or they can be included as private static or instance methods in the application class.</span></span>

<span data-ttu-id="2c238-152">또한 <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> 메서드를 사용하여 정규식 라이브러리에 이 정규식을 포함시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-152">You can also use the <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> method to include this regular expression in a regular expression library.</span></span>

<span data-ttu-id="2c238-153">정규식 라이브러리에 사용될 경우 다음과 같은 코드를 사용하여 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c238-153">If they are used in a regular expression library, you can call them by using code such as the following:</span></span>

[!code-csharp[RegularExpressions.Examples.Email#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#8)]
[!code-vb[RegularExpressions.Examples.Email#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#8)]

## <a name="see-also"></a><span data-ttu-id="2c238-154">참조</span><span class="sxs-lookup"><span data-stu-id="2c238-154">See also</span></span>

- [<span data-ttu-id="2c238-155">.NET Framework 정규식</span><span class="sxs-lookup"><span data-stu-id="2c238-155">.NET Framework Regular Expressions</span></span>](regular-expressions.md)
