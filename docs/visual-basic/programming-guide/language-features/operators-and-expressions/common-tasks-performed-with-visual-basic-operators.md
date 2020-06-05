---
title: Visual Basic 연산자를 사용한 일반적인 작업
ms.date: 07/20/2015
helpviewer_keywords:
- operators [Visual Basic], logical
- operators [Visual Basic], string concatenation
- operators [Visual Basic], bitwise
- operators [Visual Basic], bit-shift
- operators [Visual Basic], arithmetic
- operators [Visual Basic], string comparison
- operators [Visual Basic], concatenation
- Visual Basic code, operators
- operators [Visual Basic], comparison
- operators [Visual Basic], short-circuiting logical
ms.assetid: d181afe5-fafa-460f-a13b-81203f6f4587
ms.openlocfilehash: 62ced7f2048ae41c7ea4c9d62c0ff0a903c37856
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388922"
---
# <a name="common-tasks-performed-with-visual-basic-operators"></a><span data-ttu-id="82f20-102">Visual Basic 연산자를 사용한 일반적인 작업</span><span class="sxs-lookup"><span data-stu-id="82f20-102">Common Tasks Performed with Visual Basic Operators</span></span>
<span data-ttu-id="82f20-103">연산자는 *피연산자*라는 하나 이상의 식과 관련 된 여러 일반적인 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="82f20-103">Operators perform many common tasks involving one or more expressions called *operands*.</span></span>  
  
## <a name="arithmetic-and-bit-shift-tasks"></a><span data-ttu-id="82f20-104">산술 및 비트 시프트 작업</span><span class="sxs-lookup"><span data-stu-id="82f20-104">Arithmetic and Bit-shift Tasks</span></span>  
 <span data-ttu-id="82f20-105">다음 표에는 사용 가능한 산술 및 비트 시프트 연산이 요약 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82f20-105">The following table summarizes the available arithmetic and bit-shift operations.</span></span>  
  
|<span data-ttu-id="82f20-106">대상</span><span class="sxs-lookup"><span data-stu-id="82f20-106">To</span></span>|<span data-ttu-id="82f20-107">참조 항목</span><span class="sxs-lookup"><span data-stu-id="82f20-107">See</span></span>|  
|---|---|  
|<span data-ttu-id="82f20-108">한 숫자 값을 다른 숫자 값에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="82f20-108">Add one numeric value to another</span></span>|[<span data-ttu-id="82f20-109">+ 연산자</span><span class="sxs-lookup"><span data-stu-id="82f20-109">+ Operator</span></span>](../../../language-reference/operators/addition-operator.md)|  
|<span data-ttu-id="82f20-110">다른 숫자 값에서 한 숫자 값을 뺍니다.</span><span class="sxs-lookup"><span data-stu-id="82f20-110">Subtract one numeric value from another</span></span>|[<span data-ttu-id="82f20-111">-연산자 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82f20-111">- Operator (Visual Basic)</span></span>](../../../language-reference/operators/subtraction-operator.md)|  
|<span data-ttu-id="82f20-112">숫자 값의 부호를 반대로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="82f20-112">Reverse the sign of a numeric value</span></span>|[<span data-ttu-id="82f20-113">-연산자 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82f20-113">- Operator (Visual Basic)</span></span>](../../../language-reference/operators/subtraction-operator.md)|  
|<span data-ttu-id="82f20-114">한 숫자 값을 다른 숫자 값과 곱합니다.</span><span class="sxs-lookup"><span data-stu-id="82f20-114">Multiply one numeric value by another</span></span>|[<span data-ttu-id="82f20-115">\* 연산자</span><span class="sxs-lookup"><span data-stu-id="82f20-115">\* Operator</span></span>](../../../language-reference/operators/multiplication-operator.md)|  
|<span data-ttu-id="82f20-116">한 숫자 값을 다른 숫자 값으로 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="82f20-116">Divide one numeric value into another</span></span>|[<span data-ttu-id="82f20-117">/연산자 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82f20-117">/ Operator (Visual Basic)</span></span>](../../../language-reference/operators/floating-point-division-operator.md)|  
|<span data-ttu-id="82f20-118">한 숫자 값을 다른 값으로 나눈 값 (나머지는 제외)을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="82f20-118">Find the quotient of one numeric value divided by another (without the remainder)</span></span>|[<span data-ttu-id="82f20-119">\ 연산자 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82f20-119">\ Operator (Visual Basic)</span></span>](../../../language-reference/operators/integer-division-operator.md)|  
|<span data-ttu-id="82f20-120">하나의 숫자 값을 다른 값으로 나눈 나머지 (몫 제외)를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="82f20-120">Find the remainder of one numeric value divided by another (without the quotient)</span></span>|[<span data-ttu-id="82f20-121">Mod 연산자</span><span class="sxs-lookup"><span data-stu-id="82f20-121">Mod Operator</span></span>](../../../language-reference/operators/mod-operator.md)|  
|<span data-ttu-id="82f20-122">한 숫자 값을 다른 숫자 값으로 거듭제곱 합니다.</span><span class="sxs-lookup"><span data-stu-id="82f20-122">Raise one numeric value to the power of another</span></span>|[<span data-ttu-id="82f20-123">^ 연산자</span><span class="sxs-lookup"><span data-stu-id="82f20-123">^ Operator</span></span>](../../../language-reference/operators/exponentiation-operator.md)|  
|<span data-ttu-id="82f20-124">숫자 값의 비트 패턴을 왼쪽으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="82f20-124">Shift the bit pattern of a numeric value to the left</span></span>|[<span data-ttu-id="82f20-125"><\<연산자</span><span class="sxs-lookup"><span data-stu-id="82f20-125"><\< Operator</span></span>](../../../language-reference/operators/left-shift-operator.md)|  
|<span data-ttu-id="82f20-126">숫자 값의 비트 패턴을 오른쪽으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="82f20-126">Shift the bit pattern of a numeric value to the right</span></span>|[<span data-ttu-id="82f20-127">>> 연산자</span><span class="sxs-lookup"><span data-stu-id="82f20-127">>> Operator</span></span>](../../../language-reference/operators/right-shift-operator.md)|  
  
## <a name="comparison-tasks"></a><span data-ttu-id="82f20-128">비교 작업</span><span class="sxs-lookup"><span data-stu-id="82f20-128">Comparison Tasks</span></span>  
 <span data-ttu-id="82f20-129">다음 표에서는 사용 가능한 비교 작업을 요약 합니다.</span><span class="sxs-lookup"><span data-stu-id="82f20-129">The following table summarizes the available comparison operations.</span></span>  
  
|<span data-ttu-id="82f20-130">대상</span><span class="sxs-lookup"><span data-stu-id="82f20-130">To</span></span>|<span data-ttu-id="82f20-131">참조 항목</span><span class="sxs-lookup"><span data-stu-id="82f20-131">See</span></span>|  
|---|---|  
|<span data-ttu-id="82f20-132">두 값이 같은지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="82f20-132">Determine whether two values are equal</span></span>|<span data-ttu-id="82f20-133">`=`연산자 ([Visual Basic의 비교 연산자](comparison-operators.md))</span><span class="sxs-lookup"><span data-stu-id="82f20-133">`=` Operator ([Comparison Operators in Visual Basic](comparison-operators.md))</span></span>|  
|<span data-ttu-id="82f20-134">두 값이 같지 않은지 확인</span><span class="sxs-lookup"><span data-stu-id="82f20-134">Determine whether two values are unequal</span></span>|<span data-ttu-id="82f20-135">`<>`연산자 ([Visual Basic의 비교 연산자](comparison-operators.md))</span><span class="sxs-lookup"><span data-stu-id="82f20-135">`<>` Operator ([Comparison Operators in Visual Basic](comparison-operators.md))</span></span>|  
|<span data-ttu-id="82f20-136">한 값이 다른 값 보다 작지 않은지 확인</span><span class="sxs-lookup"><span data-stu-id="82f20-136">Determine whether one value is less than another</span></span>|<span data-ttu-id="82f20-137">`<`연산자 ([Visual Basic의 비교 연산자](comparison-operators.md))</span><span class="sxs-lookup"><span data-stu-id="82f20-137">`<` Operator ([Comparison Operators in Visual Basic](comparison-operators.md))</span></span>|  
|<span data-ttu-id="82f20-138">한 값이 다른 값 보다 큰지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="82f20-138">Determine whether one value is greater than another</span></span>|<span data-ttu-id="82f20-139">`>`연산자 ([Visual Basic의 비교 연산자](comparison-operators.md))</span><span class="sxs-lookup"><span data-stu-id="82f20-139">`>` Operator ([Comparison Operators in Visual Basic](comparison-operators.md))</span></span>|  
|<span data-ttu-id="82f20-140">한 값이 다른 값 보다 작거나 같은지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="82f20-140">Determine whether one value is less than or equal to another</span></span>|<span data-ttu-id="82f20-141">`<=`연산자 ([Visual Basic의 비교 연산자](comparison-operators.md))</span><span class="sxs-lookup"><span data-stu-id="82f20-141">`<=` Operator ([Comparison Operators in Visual Basic](comparison-operators.md))</span></span>|  
|<span data-ttu-id="82f20-142">한 값이 다른 값 보다 크거나 같은지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="82f20-142">Determine whether one value is greater than or equal to another</span></span>|<span data-ttu-id="82f20-143">`>=`연산자 ([Visual Basic의 비교 연산자](comparison-operators.md))</span><span class="sxs-lookup"><span data-stu-id="82f20-143">`>=` Operator ([Comparison Operators in Visual Basic](comparison-operators.md))</span></span>|  
|<span data-ttu-id="82f20-144">두 개체 변수가 동일한 개체 인스턴스를 참조 하는지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="82f20-144">Determine whether two object variables refer to the same object instance</span></span>|[<span data-ttu-id="82f20-145">Is 연산자</span><span class="sxs-lookup"><span data-stu-id="82f20-145">Is Operator</span></span>](../../../language-reference/operators/is-operator.md)|  
|<span data-ttu-id="82f20-146">두 개체 변수가 서로 다른 개체 인스턴스를 참조 하는지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="82f20-146">Determine whether two object variables refer to different object instances</span></span>|[<span data-ttu-id="82f20-147">IsNot 연산자</span><span class="sxs-lookup"><span data-stu-id="82f20-147">IsNot Operator</span></span>](../../../language-reference/operators/isnot-operator.md)|  
|<span data-ttu-id="82f20-148">개체가 특정 형식 인지 확인</span><span class="sxs-lookup"><span data-stu-id="82f20-148">Determine whether an object is of a specific type</span></span>|[<span data-ttu-id="82f20-149">TypeOf 연산자</span><span class="sxs-lookup"><span data-stu-id="82f20-149">TypeOf Operator</span></span>](../../../language-reference/operators/typeof-operator.md)|  
  
## <a name="concatenation-tasks"></a><span data-ttu-id="82f20-150">연결 태스크</span><span class="sxs-lookup"><span data-stu-id="82f20-150">Concatenation Tasks</span></span>  
 <span data-ttu-id="82f20-151">다음 표에서는 사용 가능한 연결 작업을 요약 합니다.</span><span class="sxs-lookup"><span data-stu-id="82f20-151">The following table summarizes the available concatenation operations.</span></span>  
  
|<span data-ttu-id="82f20-152">대상</span><span class="sxs-lookup"><span data-stu-id="82f20-152">To</span></span>|<span data-ttu-id="82f20-153">참조 항목</span><span class="sxs-lookup"><span data-stu-id="82f20-153">See</span></span>|  
|---|---|  
|<span data-ttu-id="82f20-154">여러 문자열을 단일 문자열로 조인</span><span class="sxs-lookup"><span data-stu-id="82f20-154">Join multiple strings into a single string</span></span>|<span data-ttu-id="82f20-155">`&`연산자 ([Visual Basic의 연결 연산자](concatenation-operators.md))</span><span class="sxs-lookup"><span data-stu-id="82f20-155">`&` Operator ([Concatenation Operators in Visual Basic](concatenation-operators.md))</span></span>|  
|<span data-ttu-id="82f20-156">문자열 값을 사용 하 여 숫자 값 조인</span><span class="sxs-lookup"><span data-stu-id="82f20-156">Join numeric values with string values</span></span>|<span data-ttu-id="82f20-157">`+`연산자 ([Visual Basic의 연결 연산자](concatenation-operators.md))</span><span class="sxs-lookup"><span data-stu-id="82f20-157">`+` Operator ([Concatenation Operators in Visual Basic](concatenation-operators.md))</span></span>|  
  
## <a name="logical-and-bitwise-tasks"></a><span data-ttu-id="82f20-158">논리적 and 비트 작업</span><span class="sxs-lookup"><span data-stu-id="82f20-158">Logical and Bitwise Tasks</span></span>  
 <span data-ttu-id="82f20-159">다음 표에는 사용 가능한 논리 및 비트 연산이 요약 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82f20-159">The following table summarizes the available logical and bitwise operations.</span></span>  
  
|<span data-ttu-id="82f20-160">대상</span><span class="sxs-lookup"><span data-stu-id="82f20-160">To</span></span>|<span data-ttu-id="82f20-161">참조 항목</span><span class="sxs-lookup"><span data-stu-id="82f20-161">See</span></span>|  
|---|---|  
|<span data-ttu-id="82f20-162">부울 값에 논리 부정 연산을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="82f20-162">Perform logical negation on a Boolean value</span></span>|[<span data-ttu-id="82f20-163">Not 연산자</span><span class="sxs-lookup"><span data-stu-id="82f20-163">Not Operator</span></span>](../../../language-reference/operators/not-operator.md)|  
|<span data-ttu-id="82f20-164">두 부울 값에 대해 논리 결합 수행</span><span class="sxs-lookup"><span data-stu-id="82f20-164">Perform logical conjunction on two Boolean values</span></span>|[<span data-ttu-id="82f20-165">And 연산자</span><span class="sxs-lookup"><span data-stu-id="82f20-165">And Operator</span></span>](../../../language-reference/operators/and-operator.md)|  
|<span data-ttu-id="82f20-166">두 부울 값에 대 한 포함 논리 분리를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="82f20-166">Perform inclusive logical disjunction on two Boolean values</span></span>|[<span data-ttu-id="82f20-167">Or 연산자</span><span class="sxs-lookup"><span data-stu-id="82f20-167">Or Operator</span></span>](../../../language-reference/operators/or-operator.md)|  
|<span data-ttu-id="82f20-168">두 부울 값에 배타적 논리 분리를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="82f20-168">Perform exclusive logical disjunction on two Boolean values</span></span>|[<span data-ttu-id="82f20-169">Xor 연산자</span><span class="sxs-lookup"><span data-stu-id="82f20-169">Xor Operator</span></span>](../../../language-reference/operators/xor-operator.md)|  
|<span data-ttu-id="82f20-170">두 부울 값에 대 한 짧은 short-circuit 논리 결합을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="82f20-170">Perform short-circuited logical conjunction on two Boolean values</span></span>|[<span data-ttu-id="82f20-171">AndAlso 연산자</span><span class="sxs-lookup"><span data-stu-id="82f20-171">AndAlso Operator</span></span>](../../../language-reference/operators/andalso-operator.md)|  
|<span data-ttu-id="82f20-172">두 부울 값에 대해 짧은 short-circuit 포함 논리 분리를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="82f20-172">Perform short-circuited inclusive logical disjunction on two Boolean values</span></span>|[<span data-ttu-id="82f20-173">OrElse 연산자</span><span class="sxs-lookup"><span data-stu-id="82f20-173">OrElse Operator</span></span>](../../../language-reference/operators/orelse-operator.md)|  
|<span data-ttu-id="82f20-174">두 정수 값에 비트 논리 결합 수행</span><span class="sxs-lookup"><span data-stu-id="82f20-174">Perform bit-by-bit logical conjunction on two integral values</span></span>|[<span data-ttu-id="82f20-175">And 연산자</span><span class="sxs-lookup"><span data-stu-id="82f20-175">And Operator</span></span>](../../../language-reference/operators/and-operator.md)|  
|<span data-ttu-id="82f20-176">두 정수 값에 비트 단위로 포함 된 논리 분리를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="82f20-176">Perform bit-by-bit inclusive logical disjunction on two integral values</span></span>|[<span data-ttu-id="82f20-177">Or 연산자</span><span class="sxs-lookup"><span data-stu-id="82f20-177">Or Operator</span></span>](../../../language-reference/operators/or-operator.md)|  
|<span data-ttu-id="82f20-178">두 정수 값에 비트 배타적 논리 분리를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="82f20-178">Perform bit-by-bit exclusive logical disjunction on two integral values</span></span>|[<span data-ttu-id="82f20-179">Xor 연산자</span><span class="sxs-lookup"><span data-stu-id="82f20-179">Xor Operator</span></span>](../../../language-reference/operators/xor-operator.md)|  
|<span data-ttu-id="82f20-180">정수 계열 값에 비트 논리 부정 연산을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="82f20-180">Perform bit-by-bit logical negation on an integral value</span></span>|[<span data-ttu-id="82f20-181">Not 연산자</span><span class="sxs-lookup"><span data-stu-id="82f20-181">Not Operator</span></span>](../../../language-reference/operators/not-operator.md)|  
  
## <a name="see-also"></a><span data-ttu-id="82f20-182">참고 항목</span><span class="sxs-lookup"><span data-stu-id="82f20-182">See also</span></span>

- [<span data-ttu-id="82f20-183">연산자 및 식</span><span class="sxs-lookup"><span data-stu-id="82f20-183">Operators and Expressions</span></span>](index.md)
- [<span data-ttu-id="82f20-184">기능별 연산자 목록</span><span class="sxs-lookup"><span data-stu-id="82f20-184">Operators Listed by Functionality</span></span>](../../../language-reference/operators/operators-listed-by-functionality.md)
