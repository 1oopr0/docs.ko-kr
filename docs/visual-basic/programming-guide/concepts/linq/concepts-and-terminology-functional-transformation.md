---
title: 개념과 용어(함수 변환)
ms.date: 07/20/2015
ms.assetid: 24fd244d-ebae-4721-8858-89bb544aea0b
ms.openlocfilehash: 4a63630d431a0972fb1a61981306a41e6f4926e3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410866"
---
# <a name="concepts-and-terminology-functional-transformation-visual-basic"></a><span data-ttu-id="63d72-102">개념 및 용어 (함수 변환) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="63d72-102">Concepts and Terminology (Functional Transformation) (Visual Basic)</span></span>
<span data-ttu-id="63d72-103">이 항목에서는 순수 함수 변환의 개념과 용어에 대해 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="63d72-103">This topic introduces the concepts and terminology of pure functional transformations.</span></span> <span data-ttu-id="63d72-104">데이터 변환에 대한 함수 변환 방법은 전통적인 명령형 프로그래밍보다 신속하게 프로그래밍할 수 있고 표현이 다양하며 디버깅과 유지 관리가 쉬운 코드를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="63d72-104">The functional transformation approach to transforming data yields code that is often quicker to program, more expressive, and easier to debug and maintain than more traditional, imperative programming.</span></span>

<span data-ttu-id="63d72-105">이 단원의 항목에서는 함수형 프로그래밍에 대해 전체적으로 설명하지 않고</span><span class="sxs-lookup"><span data-stu-id="63d72-105">Note that the topics in this section are not intended to fully explain functional programming.</span></span> <span data-ttu-id="63d72-106">XML의 모양을 쉽게 변환하는 데 사용할 수 있는 몇 가지 함수형 프로그래밍 기능만 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="63d72-106">Instead, these topics identify some of the functional programming capabilities that make it easier to transform XML from one shape to another.</span></span>

## <a name="what-is-pure-functional-transformation"></a><span data-ttu-id="63d72-107">순수 함수 변환이란?</span><span class="sxs-lookup"><span data-stu-id="63d72-107">What Is Pure Functional Transformation?</span></span>

<span data-ttu-id="63d72-108">*순수 함수 변환*에서 *순수 함수*라는 일련의 함수는 구조화된 데이터의 집합을 원래 형태에서 다른 형태로 변환하는 방법을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="63d72-108">In *pure functional transformation*, a set of functions, called *pure functions*, define how to transform a set of structured data from its original form into another form.</span></span> <span data-ttu-id="63d72-109">"순수"라는 단어는 함수가 *구성 가능(composable)* 함을 의미합니다. 구성 가능한 함수에는 다음과 같은 특징이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63d72-109">The word "pure" indicates that the functions are *composable*, which requires that they are:</span></span>

- <span data-ttu-id="63d72-110">*자체 포함*됩니다. 프로그램의 나머지 부분과 상호 종속되거나 얽히는 일 없이 함수가 자유롭게 정렬되고 다시 정렬될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63d72-110">*Self-contained*, so that they can be freely ordered and rearranged without entanglement or interdependencies with the rest of the program.</span></span> <span data-ttu-id="63d72-111">순수 변환은 환경에 대한 지식이 없고 환경에 영향을 미치지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="63d72-111">Pure transformations have no knowledge of or effect upon their environment.</span></span> <span data-ttu-id="63d72-112">즉, 변환에 사용되는 함수가 *의도하지 않은 결과*를 발생시키지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="63d72-112">That is, the functions used in the transformation have no *side effects*.</span></span>

- <span data-ttu-id="63d72-113">*상태 비저장*입니다. 동일한 입력에 대해 동일한 함수나 특정 함수 집합을 실행하면 항상 같은 결과가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="63d72-113">*Stateless*, so that executing the same function or specific set of functions on the same input will always result in the same output.</span></span> <span data-ttu-id="63d72-114">순수 변환은 이전 사용에 대한 기록을 갖고 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="63d72-114">Pure transformations have no memory of their prior use.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="63d72-115">이 자습서의 나머지 부분에서 "순수 함수"라는 용어는 특정 언어 기능이 아니라 프로그래밍 방법을 나타내기 위해 일반적인 의미에서 사용되었습니다.</span><span class="sxs-lookup"><span data-stu-id="63d72-115">In the rest of this tutorial, the term "pure function" is used in a general sense to indicate a programming approach, and not a specific language feature.</span></span>
>
> <span data-ttu-id="63d72-116">순수 함수는 Visual Basic에서 함수로 구현 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d72-116">Note that pure functions must be implemented as functions in Visual Basic.</span></span>
>
> <span data-ttu-id="63d72-117">또한 순수 함수와 C++의 순수 가상 메서드를 혼동하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63d72-117">Also, you should not confuse pure functions with pure virtual methods in C++.</span></span> <span data-ttu-id="63d72-118">순수 가상 메서드의 경우 포함하는 클래스가 추상 클래스이고 메서드 본문이 제공되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="63d72-118">The latter indicates that the containing class is abstract and that no method body is supplied.</span></span>

### <a name="functional-programming"></a><span data-ttu-id="63d72-119">함수형 프로그래밍</span><span class="sxs-lookup"><span data-stu-id="63d72-119">Functional Programming</span></span>

<span data-ttu-id="63d72-120">*함수형 프로그래밍*은 순수 함수 변환을 직접 지원하는 프로그래밍 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="63d72-120">*Functional programming* is a programming approach that directly supports pure functional transformation.</span></span>

<span data-ttu-id="63d72-121">지금까지 ML, Scheme, Haskell 및 F#과 같은 범용 함수형 프로그래밍 언어는 주로 학계에서 관심을 가졌습니다.</span><span class="sxs-lookup"><span data-stu-id="63d72-121">Historically, general-purpose functional programming languages, such as ML, Scheme, Haskell, and F#, have been primarily of interest to the academic community.</span></span> <span data-ttu-id="63d72-122">Visual Basic에서 순수 함수 변환을 항상 작성할 수 있었지만 대부분의 프로그래머에 게 유용한 옵션을 만들 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="63d72-122">Although it has always been possible to write pure functional transformations in Visual Basic, the difficulty of doing so has not made it an attractive option to most programmers.</span></span> <span data-ttu-id="63d72-123">그러나 Visual Basic의 이후 버전에서 람다 식 및 형식 유추와 같은 새 언어 구문을 사용 하면 함수형 프로그래밍을 훨씬 쉽고 생산적으로 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63d72-123">With later versions of Visual Basic, however, new language constructs such as lambda expressions and type inference make it functional programming much easier and more productive.</span></span>

<span data-ttu-id="63d72-124">함수형 프로그래밍에 대 한 자세한 내용은 [함수형 프로그래밍 및 명령적 프로그래밍 (Visual Basic)](functional-programming-vs-imperative-programming.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="63d72-124">For more information about functional programming, see [Functional Programming vs. Imperative Programming (Visual Basic)](functional-programming-vs-imperative-programming.md).</span></span>

#### <a name="domain-specific-fp-languages"></a><span data-ttu-id="63d72-125">영역별 FP 언어</span><span class="sxs-lookup"><span data-stu-id="63d72-125">Domain-Specific FP Languages</span></span>

<span data-ttu-id="63d72-126">범용 프로그래밍 언어가 널리 채택되지는 않았지만 특정 영역별 함수형 프로그래밍 언어는 보다 성공적이었습니다.</span><span class="sxs-lookup"><span data-stu-id="63d72-126">Although general functional programming languages have not been widely adopted, specific domain-specific functional programming languages have had better success.</span></span> <span data-ttu-id="63d72-127">예를 들어, CSS 스타일시트는 많은 웹 페이지의 모양과 느낌을 결정하는 데 사용되고 XSLT(Extensible Stylesheet Language Transformation) 스타일시트는 XML 데이터 조작에서 광범위하게 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="63d72-127">For example, Cascading Style Sheets (CSS) are used to determine the look and feel of many Web pages, and Extensible Stylesheet Language Transformations (XSLT) style sheets are used extensively in XML data manipulation.</span></span> <span data-ttu-id="63d72-128">XSLT에 대한 자세한 내용은 [XSLT 변환](../../../../standard/data/xml/xslt-transformations.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="63d72-128">For more information about XSLT, see [XSLT Transformations](../../../../standard/data/xml/xslt-transformations.md).</span></span>

## <a name="terminology"></a><span data-ttu-id="63d72-129">용어</span><span class="sxs-lookup"><span data-stu-id="63d72-129">Terminology</span></span>

<span data-ttu-id="63d72-130">다음 표에는 함수 변환과 관련된 몇 가지 용어가 정의되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63d72-130">The following table defines some terms related to functional transformations.</span></span>

<span data-ttu-id="63d72-131">고차(첫 번째 클래스) 함수 </span><span class="sxs-lookup"><span data-stu-id="63d72-131">higher-order (first-class) function </span></span>\
<span data-ttu-id="63d72-132">프로그램 개체로 취급할 수 있는 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="63d72-132">A function that can be treated as a programmatic object.</span></span> <span data-ttu-id="63d72-133">예를 들어, 고차 함수는 다른 함수로 전달되거나 다른 함수에서 반환될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63d72-133">For example, a higher-order function can be passed to or returned from other functions.</span></span> <span data-ttu-id="63d72-134">Visual Basic에서 대리자와 람다 식은 고차 함수를 지 원하는 언어 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="63d72-134">In Visual Basic, delegates and lambda expressions are language features that support higher-order functions.</span></span> <span data-ttu-id="63d72-135">고차 함수를 작성하려면 하나 이상의 인수를 선언하여 대리자를 사용하며, 고차 함수를 호출할 때는 흔히 람다 식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="63d72-135">To write a higher-order function, you declare one or more arguments to take delegates, and you often use lambda expressions when calling it.</span></span> <span data-ttu-id="63d72-136">대부분의 표준 쿼리 연산자가 고차 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="63d72-136">Many of the standard query operators are higher-order functions.</span></span>

<span data-ttu-id="63d72-137">자세한 내용은 [표준 쿼리 연산자 개요 (Visual Basic)](standard-query-operators-overview.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="63d72-137">For more information, see [Standard Query Operators Overview (Visual Basic)](standard-query-operators-overview.md).</span></span>

<span data-ttu-id="63d72-138">람다 식 </span><span class="sxs-lookup"><span data-stu-id="63d72-138">lambda expression </span></span>\
<span data-ttu-id="63d72-139">대리자 형식이 예상되는 곳에서 항상 사용할 수 있는 인라인 익명 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="63d72-139">Essentially, an inline anonymous function that can be used wherever a delegate type is expected.</span></span> <span data-ttu-id="63d72-140">이는 람다 식에 대한 간략한 정의이지만 이 자습서의 목적에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="63d72-140">This is a simplified definition of lambda expressions, but it is adequate for the purposes of this tutorial.</span></span>

<span data-ttu-id="63d72-141">자세한 내용은 [람다 식](../../language-features/procedures/lambda-expressions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="63d72-141">For more information about, see [Lambda Expressions](../../language-features/procedures/lambda-expressions.md).</span></span>

<span data-ttu-id="63d72-142">컬렉션 </span><span class="sxs-lookup"><span data-stu-id="63d72-142">collection </span></span>\
<span data-ttu-id="63d72-143">대개 동일한 형식을 갖고 있는 구조화된 데이터 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="63d72-143">A structured set of data, usually of a uniform type.</span></span> <span data-ttu-id="63d72-144">LINQ와 호환되려면 컬렉션은 <xref:System.Collections.IEnumerable> 인터페이스나 <xref:System.Linq.IQueryable> 인터페이스(또는 해당하는 제네릭 항목인 <xref:System.Collections.Generic.IEnumerator%601> 또는 <xref:System.Linq.IQueryable%601> 중 하나)를 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d72-144">To be compatible with LINQ, a collection must implement the <xref:System.Collections.IEnumerable> interface or the <xref:System.Linq.IQueryable> interface (or one of their generic counterparts, <xref:System.Collections.Generic.IEnumerator%601> or <xref:System.Linq.IQueryable%601>).</span></span>

<span data-ttu-id="63d72-145">튜플(익명 형식) </span><span class="sxs-lookup"><span data-stu-id="63d72-145">tuple (anonymous types) </span></span>\
<span data-ttu-id="63d72-146">수학적 개념인 튜플은 각각 특정한 형식을 가진 개체의 유한 시퀀스입니다.</span><span class="sxs-lookup"><span data-stu-id="63d72-146">A mathematical concept, a tuple is a finite sequence of objects, each of a specific type.</span></span> <span data-ttu-id="63d72-147">튜플을 정렬된 목록이라고 하기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="63d72-147">A tuple is also known as an ordered list.</span></span> <span data-ttu-id="63d72-148">익명 형식은 이 개념을 언어에 구현한 것입니다. 익명 형식을 사용하여 명명되지 않은 클래스 형식을 선언하고 해당 형식의 개체를 동시에 인스턴스화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63d72-148">Anonymous types are a language implementation of this concept, which enable an unnamed class type to be declared and an object of that type to be instantiated at the same time.</span></span>

<span data-ttu-id="63d72-149">자세한 내용은 [무명 형식](../../language-features/objects-and-classes/anonymous-types.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="63d72-149">For more information, see  [Anonymous Types](../../language-features/objects-and-classes/anonymous-types.md).</span></span>

<span data-ttu-id="63d72-150">형식 유추(암시적 형식 지정) </span><span class="sxs-lookup"><span data-stu-id="63d72-150">type inference (implicit typing) </span></span>\
<span data-ttu-id="63d72-151">명시적 형식 선언이 없는 경우 컴파일러에서 변수의 형식을 결정하도록 하는 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="63d72-151">The ability of a compiler to determine the type of a variable in the absence of an explicit type declaration.</span></span>

<span data-ttu-id="63d72-152">자세한 내용은 [지역 형식 유추](../../language-features/variables/local-type-inference.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="63d72-152">For more information, see [Local Type Inference](../../language-features/variables/local-type-inference.md).</span></span>

<span data-ttu-id="63d72-153">지연된 실행 및 지연 계산 </span><span class="sxs-lookup"><span data-stu-id="63d72-153">deferred execution and lazy evaluation </span></span>\
<span data-ttu-id="63d72-154">확인된 값이 실제로 필요할 때까지 식의 계산을 지연하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="63d72-154">The delaying of evaluation of an expression until its resolved value is actually required.</span></span> <span data-ttu-id="63d72-155">지연된 실행은 컬렉션에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="63d72-155">Deferred execution is supported in collections.</span></span>

<span data-ttu-id="63d72-156">자세한 내용은 [LINQ to XML (Visual Basic)에서](deferred-execution-and-lazy-evaluation-in-linq-to-xml.md) [기본 쿼리 작업 (Visual Basic)](basic-query-operations.md) 및 지연 된 실행 및 지연 계산을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="63d72-156">For more information, see [Basic Query Operations (Visual Basic)](basic-query-operations.md) and [Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)](deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>

<span data-ttu-id="63d72-157">이러한 언어 기능은 이 단원 전반의 코드 샘플에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="63d72-157">These language features will be used in code samples throughout this section.</span></span>

## <a name="see-also"></a><span data-ttu-id="63d72-158">참조</span><span class="sxs-lookup"><span data-stu-id="63d72-158">See also</span></span>

- [<span data-ttu-id="63d72-159">순수 함수 변환 소개 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="63d72-159">Introduction to Pure Functional Transformations (Visual Basic)</span></span>](introduction-to-pure-functional-transformations.md)
- [<span data-ttu-id="63d72-160">함수형 프로그래밍과 명령형 프로그래밍 비교 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="63d72-160">Functional Programming vs. Imperative Programming (Visual Basic)</span></span>](functional-programming-vs-imperative-programming.md)
