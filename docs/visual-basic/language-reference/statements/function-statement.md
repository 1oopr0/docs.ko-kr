---
title: Function 문
ms.date: 05/12/2018
f1_keywords:
- vb.Function
helpviewer_keywords:
- procedures [Visual Basic], creating
- Function procedures [Visual Basic], Function statement syntax
- functions [Visual Basic], function procedures
- ParamArray keyword [Visual Basic], Function statements
- Private keyword [Visual Basic], Function statements
- declarations [Visual Basic], procedures
- procedures [Visual Basic], declaration
- Public keyword [Visual Basic], in Function statement
- ByVal keyword [Visual Basic], Function statements
- procedures [Visual Basic], recursive
- Implements keyword [Visual Basic], Function statements
- procedures [Visual Basic], returning values
- Exit statement [Visual Basic], in Function procedures
- recursive procedures
- As keyword [Visual Basic], in Function statement
- Optional keyword [Visual Basic], Function statements
- Function statement [Visual Basic]
- Visual Basic code, Function procedures
- procedures [Visual Basic], function
- ByRef keyword [Visual Basic], Function statements
- Friend keyword [Visual Basic], Function statements
- End keyword [Visual Basic], Function statements
- Handles keyword [Visual Basic], Function statements
ms.assetid: a4497077-0f46-4ede-a27f-9e8670df52b9
ms.openlocfilehash: 49cf4fead2c5594b7ac6815f82fea0dc995ea436
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404630"
---
# <a name="function-statement-visual-basic"></a><span data-ttu-id="5b219-102">Function 문(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b219-102">Function Statement (Visual Basic)</span></span>

<span data-ttu-id="5b219-103">프로시저를 정의 하는 이름, 매개 변수 및 코드를 선언 `Function` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-103">Declares the name, parameters, and code that define a `Function` procedure.</span></span>

## <a name="syntax"></a><span data-ttu-id="5b219-104">구문</span><span class="sxs-lookup"><span data-stu-id="5b219-104">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async | Iterator ]
Function name [ (Of typeparamlist) ] [ (parameterlist) ] [ As returntype ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Function ]
    [ statements ]
End Function
```

## <a name="parts"></a><span data-ttu-id="5b219-105">부분</span><span class="sxs-lookup"><span data-stu-id="5b219-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="5b219-106">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-106">Optional.</span></span> <span data-ttu-id="5b219-107">[특성 목록](attribute-list.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="5b219-107">See [Attribute List](attribute-list.md).</span></span>

- `accessmodifier`

  <span data-ttu-id="5b219-108">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-108">Optional.</span></span> <span data-ttu-id="5b219-109">다음 중 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-109">Can be one of the following:</span></span>

  - [<span data-ttu-id="5b219-110">공용</span><span class="sxs-lookup"><span data-stu-id="5b219-110">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="5b219-111">보호</span><span class="sxs-lookup"><span data-stu-id="5b219-111">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="5b219-112">Friend</span><span class="sxs-lookup"><span data-stu-id="5b219-112">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="5b219-113">프라이빗</span><span class="sxs-lookup"><span data-stu-id="5b219-113">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="5b219-114">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="5b219-114">Protected Friend</span></span>](../modifiers/protected-friend.md)

  - [<span data-ttu-id="5b219-115">개인 보호</span><span class="sxs-lookup"><span data-stu-id="5b219-115">Private Protected</span></span>](../modifiers/private-protected.md)

  <span data-ttu-id="5b219-116">[Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5b219-116">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `proceduremodifiers`

  <span data-ttu-id="5b219-117">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-117">Optional.</span></span> <span data-ttu-id="5b219-118">다음 중 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-118">Can be one of the following:</span></span>

  - [<span data-ttu-id="5b219-119">오버로드</span><span class="sxs-lookup"><span data-stu-id="5b219-119">Overloads</span></span>](../modifiers/overloads.md)

  - [<span data-ttu-id="5b219-120">재정의</span><span class="sxs-lookup"><span data-stu-id="5b219-120">Overrides</span></span>](../modifiers/overrides.md)

  - [<span data-ttu-id="5b219-121">Overrides</span><span class="sxs-lookup"><span data-stu-id="5b219-121">Overridable</span></span>](../modifiers/overridable.md)

  - [<span data-ttu-id="5b219-122">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="5b219-122">NotOverridable</span></span>](../modifiers/notoverridable.md)

  - [<span data-ttu-id="5b219-123">New</span><span class="sxs-lookup"><span data-stu-id="5b219-123">MustOverride</span></span>](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  <span data-ttu-id="5b219-124">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-124">Optional.</span></span> <span data-ttu-id="5b219-125">[공유](../modifiers/shared.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5b219-125">See [Shared](../modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="5b219-126">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-126">Optional.</span></span> <span data-ttu-id="5b219-127">[그림자](../modifiers/shadows.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5b219-127">See [Shadows](../modifiers/shadows.md).</span></span>

- `Async`

  <span data-ttu-id="5b219-128">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-128">Optional.</span></span> <span data-ttu-id="5b219-129">[Async](../modifiers/async.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5b219-129">See [Async](../modifiers/async.md).</span></span>

- `Iterator`

  <span data-ttu-id="5b219-130">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-130">Optional.</span></span> <span data-ttu-id="5b219-131">[반복기](../modifiers/iterator.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5b219-131">See [Iterator](../modifiers/iterator.md).</span></span>

- `name`

  <span data-ttu-id="5b219-132">필수 요소.</span><span class="sxs-lookup"><span data-stu-id="5b219-132">Required.</span></span> <span data-ttu-id="5b219-133">프로시저의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-133">Name of the procedure.</span></span> <span data-ttu-id="5b219-134">[Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5b219-134">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

- `typeparamlist`

  <span data-ttu-id="5b219-135">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-135">Optional.</span></span> <span data-ttu-id="5b219-136">제네릭 프로시저에 대 한 형식 매개 변수 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-136">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="5b219-137">[형식 목록](type-list.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="5b219-137">See [Type List](type-list.md).</span></span>

- `parameterlist`

  <span data-ttu-id="5b219-138">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-138">Optional.</span></span> <span data-ttu-id="5b219-139">이 프로시저의 매개 변수를 나타내는 지역 변수 이름 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-139">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="5b219-140">[매개 변수 목록](parameter-list.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5b219-140">See [Parameter List](parameter-list.md).</span></span>

- `returntype`

  <span data-ttu-id="5b219-141">필요한 경우 `Option Strict` 는 `On`합니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-141">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="5b219-142">이 프로시저에서 반환 하는 값의 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-142">Data type of the value returned by this procedure.</span></span>

- `Implements`

  <span data-ttu-id="5b219-143">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-143">Optional.</span></span> <span data-ttu-id="5b219-144">이 프로시저에서 하나 이상의 `Function` 프로시저를 구현 하 고 각각이 프로시저의 포함 하는 클래스 또는 구조체에 의해 구현 된 인터페이스에 정의 됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-144">Indicates that this procedure implements one or more `Function` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="5b219-145">[Implements 문](implements-statement.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5b219-145">See [Implements Statement](implements-statement.md).</span></span>

- `implementslist`

  <span data-ttu-id="5b219-146">`Implements`가 제공된 경우 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-146">Required if `Implements` is supplied.</span></span> <span data-ttu-id="5b219-147">구현할 `Function` 프로시저 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-147">List of `Function` procedures being implemented.</span></span>

  `implementedprocedure [ , implementedprocedure ... ]`

  <span data-ttu-id="5b219-148">각 `implementedprocedure`에는 다음과 같은 구문과 요소가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-148">Each `implementedprocedure` has the following syntax and parts:</span></span>

  `interface.definedname`

  |<span data-ttu-id="5b219-149">부분</span><span class="sxs-lookup"><span data-stu-id="5b219-149">Part</span></span>|<span data-ttu-id="5b219-150">Description</span><span class="sxs-lookup"><span data-stu-id="5b219-150">Description</span></span>|
  |---|---|
  |`interface`|<span data-ttu-id="5b219-151">필수 요소.</span><span class="sxs-lookup"><span data-stu-id="5b219-151">Required.</span></span> <span data-ttu-id="5b219-152">이 프로시저에 포함 된 클래스 또는 구조체에 의해 구현 된 인터페이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-152">Name of an interface implemented by this procedure's containing class or structure.</span></span>|
  |`definedname`|<span data-ttu-id="5b219-153">필수 요소.</span><span class="sxs-lookup"><span data-stu-id="5b219-153">Required.</span></span> <span data-ttu-id="5b219-154">프로시저가 `interface`에 정의되는 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-154">Name by which the procedure is defined in `interface`.</span></span>|

- `Handles`

  <span data-ttu-id="5b219-155">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-155">Optional.</span></span> <span data-ttu-id="5b219-156">이 프로시저가 하나 이상의 특정 이벤트를 처리할 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-156">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="5b219-157">[핸들](handles-clause.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5b219-157">See [Handles](handles-clause.md).</span></span>

- `eventlist`

  <span data-ttu-id="5b219-158">`Handles`가 제공된 경우 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-158">Required if `Handles` is supplied.</span></span> <span data-ttu-id="5b219-159">이 프로시저가 처리 하는 이벤트 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-159">List of events this procedure handles.</span></span>

  `eventspecifier [ , eventspecifier ... ]`

  <span data-ttu-id="5b219-160">각 `eventspecifier`에는 다음과 같은 구문과 요소가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-160">Each `eventspecifier` has the following syntax and parts:</span></span>

  `eventvariable.event`

  |<span data-ttu-id="5b219-161">부분</span><span class="sxs-lookup"><span data-stu-id="5b219-161">Part</span></span>|<span data-ttu-id="5b219-162">Description</span><span class="sxs-lookup"><span data-stu-id="5b219-162">Description</span></span>|
  |---|---|
  |`eventvariable`|<span data-ttu-id="5b219-163">필수 요소.</span><span class="sxs-lookup"><span data-stu-id="5b219-163">Required.</span></span> <span data-ttu-id="5b219-164">이벤트를 발생 시키는 클래스 또는 구조체의 데이터 형식으로 선언 된 개체 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-164">Object variable declared with the data type of the class or structure that raises the event.</span></span>|
  |`event`|<span data-ttu-id="5b219-165">필수 요소.</span><span class="sxs-lookup"><span data-stu-id="5b219-165">Required.</span></span> <span data-ttu-id="5b219-166">이 프로시저가 처리 하는 이벤트의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-166">Name of the event this procedure handles.</span></span>|

- `statements`

  <span data-ttu-id="5b219-167">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-167">Optional.</span></span> <span data-ttu-id="5b219-168">이 프로시저 내에서 실행할 문 블록입니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-168">Block of statements to be executed within this procedure.</span></span>

- `End Function`

  <span data-ttu-id="5b219-169">이 프로시저의 정의를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-169">Terminates the definition of this procedure.</span></span>

## <a name="remarks"></a><span data-ttu-id="5b219-170">설명</span><span class="sxs-lookup"><span data-stu-id="5b219-170">Remarks</span></span>

<span data-ttu-id="5b219-171">모든 실행 코드는 프로시저 내에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-171">All executable code must be inside a procedure.</span></span> <span data-ttu-id="5b219-172">각 프로시저는 클래스, 구조체 또는 포함 하는 클래스, 구조체 또는 모듈 이라고 하는 모듈 내에서 선언 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-172">Each procedure, in turn, is declared within a class, a structure, or a module that is referred to as the containing class, structure, or module.</span></span>

<span data-ttu-id="5b219-173">호출 코드에 값을 반환 하려면 프로시저를 사용 하 `Function` 고, 그렇지 않은 경우 프로시저를 사용 `Sub` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-173">To return a value to the calling code, use a `Function` procedure; otherwise, use a `Sub` procedure.</span></span>

## <a name="defining-a-function"></a><span data-ttu-id="5b219-174">함수 정의</span><span class="sxs-lookup"><span data-stu-id="5b219-174">Defining a Function</span></span>

<span data-ttu-id="5b219-175">`Function`모듈 수준 에서만 프로시저를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-175">You can define a `Function` procedure only at the module level.</span></span> <span data-ttu-id="5b219-176">따라서 함수의 선언 컨텍스트는 클래스, 구조체, 모듈 또는 인터페이스 여야 하며 소스 파일, 네임 스페이스, 프로시저 또는 블록일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-176">Therefore, the declaration context for a function must be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="5b219-177">자세한 내용은 [선언 컨텍스트 및 기본 액세스 수준](declaration-contexts-and-default-access-levels.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5b219-177">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="5b219-178">`Function`프로시저는 기본적으로 공용 액세스입니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-178">`Function` procedures default to public access.</span></span> <span data-ttu-id="5b219-179">액세스 한정자를 사용 하 여 액세스 수준을 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-179">You can adjust their access levels with the access modifiers.</span></span>

<span data-ttu-id="5b219-180">프로시저는 `Function` 프로시저에서 반환 하는 값의 데이터 형식을 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-180">A `Function` procedure can declare the data type of the value that the procedure returns.</span></span> <span data-ttu-id="5b219-181">모든 데이터 형식 또는 열거형, 구조체, 클래스 또는 인터페이스의 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-181">You can specify any data type or the name of an enumeration, a structure, a class, or an interface.</span></span> <span data-ttu-id="5b219-182">매개 변수를 지정 하지 않으면 `returntype` 프로시저가 반환 `Object` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-182">If you don't specify the `returntype` parameter, the procedure returns `Object`.</span></span>

<span data-ttu-id="5b219-183">이 프로시저에서 키워드를 사용 하는 경우 `Implements` 포함 하는 클래스 또는 구조체에도 `Implements` 해당 또는 문 바로 다음에 오는 문이 있어야 합니다 `Class` `Structure` .</span><span class="sxs-lookup"><span data-stu-id="5b219-183">If this procedure uses the `Implements` keyword, the containing class or structure must also have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="5b219-184">`Implements`문에는에 지정 된 각 인터페이스가 포함 되어야 합니다 `implementslist` .</span><span class="sxs-lookup"><span data-stu-id="5b219-184">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="5b219-185">그러나 인터페이스에서 (의)를 정의 하는 이름은 `Function` `definedname` 이 프로시저의 이름과 일치할 필요가 없습니다 (에서 `name` ).</span><span class="sxs-lookup"><span data-stu-id="5b219-185">However, the name by which an interface defines the `Function` (in `definedname`) doesn't need to match the name of this procedure (in `name`).</span></span>

> [!NOTE]
> <span data-ttu-id="5b219-186">람다 식을 사용 하 여 함수 식을 인라인으로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-186">You can use lambda expressions to define function expressions inline.</span></span> <span data-ttu-id="5b219-187">자세한 내용은 [함수 식](../operators/function-expression.md) 및 [람다 식](../../programming-guide/language-features/procedures/lambda-expressions.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5b219-187">For more information, see [Function Expression](../operators/function-expression.md) and [Lambda Expressions](../../programming-guide/language-features/procedures/lambda-expressions.md).</span></span>

## <a name="returning-from-a-function"></a><span data-ttu-id="5b219-188">함수에서 반환</span><span class="sxs-lookup"><span data-stu-id="5b219-188">Returning from a Function</span></span>

<span data-ttu-id="5b219-189">`Function`프로시저가 호출 코드에 반환 되 면 프로시저를 호출한 문 다음에 오는 문을 사용 하 여 실행이 계속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-189">When the `Function` procedure returns to the calling code, execution continues with the statement that follows the statement that called the procedure.</span></span>

<span data-ttu-id="5b219-190">함수에서 값을 반환 하려면 함수 이름에 값을 할당 하거나 문에 포함할 수 있습니다 `Return` .</span><span class="sxs-lookup"><span data-stu-id="5b219-190">To return a value from a function, you can either assign the value to the function name or include it in a `Return` statement.</span></span>

<span data-ttu-id="5b219-191">`Return`문은 다음 예제와 같이 반환 값을 동시에 할당 하 고 함수를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-191">The `Return` statement simultaneously assigns the return value and exits the function, as the following example shows.</span></span>

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

<span data-ttu-id="5b219-192">다음 예에서는 함수 이름에 반환 값을 할당 한 `myFunction` 다음 문을 사용 하 여를 `Exit Function` 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-192">The following example assigns the return value to the function name `myFunction` and then uses the `Exit Function` statement to return.</span></span>

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

<span data-ttu-id="5b219-193">`Exit Function`및 `Return` 문은 프로시저에서 즉각적인 종료를 발생 시킵니다 `Function` .</span><span class="sxs-lookup"><span data-stu-id="5b219-193">The `Exit Function` and `Return` statements cause an immediate exit from a `Function` procedure.</span></span> <span data-ttu-id="5b219-194">프로시저의 모든 위치에는 개수와 `Exit Function` `Return` 문이 모두 표시 될 수 있으며 `Exit Function` 문과 문을 혼합할 수 있습니다 `Return` .</span><span class="sxs-lookup"><span data-stu-id="5b219-194">Any number of `Exit Function` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Function` and `Return` statements.</span></span>

<span data-ttu-id="5b219-195">`Exit Function`에 값을 할당 하지 않고를 사용 하는 경우 `name` 프로시저는에 지정 된 데이터 형식에 대 한 기본값을 반환 합니다 `returntype` .</span><span class="sxs-lookup"><span data-stu-id="5b219-195">If you use `Exit Function` without assigning a value to `name`, the procedure returns the default value for the data type that's specified in `returntype`.</span></span> <span data-ttu-id="5b219-196">을 `returntype` 지정 하지 않으면이 프로시저는 `Nothing` 에 대 한 기본값인을 반환 합니다 `Object` .</span><span class="sxs-lookup"><span data-stu-id="5b219-196">If `returntype` isn't specified, the procedure returns `Nothing`, which is the default value for `Object`.</span></span>

## <a name="calling-a-function"></a><span data-ttu-id="5b219-197">함수 호출</span><span class="sxs-lookup"><span data-stu-id="5b219-197">Calling a Function</span></span>

<span data-ttu-id="5b219-198">프로시저 `Function` 이름을 사용 하 여 프로시저를 호출한 다음 식에서 괄호 안의 인수 목록을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-198">You call a `Function` procedure by using the procedure name, followed by the argument list in parentheses, in an expression.</span></span> <span data-ttu-id="5b219-199">인수를 제공 하지 않는 경우에만 괄호를 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-199">You can omit the parentheses only if you aren't supplying any arguments.</span></span> <span data-ttu-id="5b219-200">그러나 항상 괄호를 포함 하는 경우 코드를 더 쉽게 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-200">However, your code is more readable if you always include the parentheses.</span></span>

<span data-ttu-id="5b219-201">`Function`, 또는와 같은 라이브러리 함수를 호출 하는 것과 동일한 방식으로 프로시저를 호출 합니다 `Sqrt` `Cos` `ChrW` .</span><span class="sxs-lookup"><span data-stu-id="5b219-201">You call a `Function` procedure the same way that you call any library function such as `Sqrt`, `Cos`, or `ChrW`.</span></span>

<span data-ttu-id="5b219-202">키워드를 사용 하 여 함수를 호출할 수도 있습니다 `Call` .</span><span class="sxs-lookup"><span data-stu-id="5b219-202">You can also call a function by using the `Call` keyword.</span></span> <span data-ttu-id="5b219-203">이 경우 반환 값은 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-203">In that case, the return value is ignored.</span></span> <span data-ttu-id="5b219-204">`Call`대부분의 경우 키워드를 사용 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-204">Use of the `Call` keyword isn't recommended in most cases.</span></span> <span data-ttu-id="5b219-205">자세한 내용은 [Call 문](call-statement.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5b219-205">For more information, see [Call Statement](call-statement.md).</span></span>

<span data-ttu-id="5b219-206">때로는 산술 식을 다시 정렬 하 여 내부 효율성을 높이는 Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5b219-206">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="5b219-207">`Function`이러한 이유로 함수에서 동일한 식의 변수 값을 변경 하는 경우에는 산술 식에 프로시저를 사용 하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-207">For that reason, you shouldn't use a `Function` procedure in an arithmetic expression when the function changes the value of variables in the same expression.</span></span>

## <a name="async-functions"></a><span data-ttu-id="5b219-208">비동기 함수</span><span class="sxs-lookup"><span data-stu-id="5b219-208">Async Functions</span></span>

<span data-ttu-id="5b219-209">비동기 *기능을* 사용 하면 명시적 콜백을 사용 하거나 여러 함수 또는 람다 식에서 수동으로 코드를 분할 하지 않고도 비동기 함수를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-209">The *Async* feature allows you to invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>

<span data-ttu-id="5b219-210">[비동기](../modifiers/async.md) 한정자를 사용 하 여 함수를 표시 하는 경우 함수에서 [wait](../operators/await-operator.md) 연산자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-210">If you mark a function with the [Async](../modifiers/async.md) modifier, you can use the [Await](../operators/await-operator.md) operator in the function.</span></span> <span data-ttu-id="5b219-211">제어가 `Await` 함수에서 식에 도달 하면 `Async` 제어가 호출자에 게 반환 되 고 대기 작업이 완료 될 때까지 함수의 진행률이 일시 중단 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-211">When control reaches an `Await` expression in the `Async` function, control returns to the caller, and progress in the function is suspended until the awaited task completes.</span></span> <span data-ttu-id="5b219-212">작업이 완료 되 면 함수에서 실행을 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-212">When the task is complete, execution can resume in the function.</span></span>

> [!NOTE]
> <span data-ttu-id="5b219-213">`Async`프로시저는 아직 완료 되지 않은 첫 번째 대기 개체를 발견 하거나 프로시저 끝에 도달할 때마다 호출자에 게 반환 `Async` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-213">An `Async` procedure returns to the caller when either it encounters the first awaited object that’s not yet complete, or it gets to the end of the `Async` procedure, whichever occurs first.</span></span>

<span data-ttu-id="5b219-214">`Async`함수는 또는의 반환 형식을 사용할 수 <xref:System.Threading.Tasks.Task%601> 있습니다 <xref:System.Threading.Tasks.Task> .</span><span class="sxs-lookup"><span data-stu-id="5b219-214">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="5b219-215">`Async`반환 형식이 인 함수의 예는 <xref:System.Threading.Tasks.Task%601> 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-215">An example of an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601> is provided below.</span></span>

<span data-ttu-id="5b219-216">`Async`함수는 [ByRef](../modifiers/byref.md) 매개 변수를 선언할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-216">An `Async` function cannot declare any [ByRef](../modifiers/byref.md) parameters.</span></span>

<span data-ttu-id="5b219-217">[하위 문은](sub-statement.md) 한정자로 표시 될 수도 있습니다 `Async` .</span><span class="sxs-lookup"><span data-stu-id="5b219-217">A [Sub Statement](sub-statement.md) can also be marked with the `Async` modifier.</span></span> <span data-ttu-id="5b219-218">이는 주로 값을 반환할 수 없는 이벤트 처리기에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-218">This is primarily used for event handlers, where a value cannot be returned.</span></span> <span data-ttu-id="5b219-219">프로시저는 `Async` `Sub` 대기 수 없으며 프로시저 호출자는 `Async` `Sub` 프로시저에서 throw 된 예외를 catch 할 수 없습니다 `Sub` .</span><span class="sxs-lookup"><span data-stu-id="5b219-219">An `Async` `Sub` procedure can't be awaited, and the caller of an `Async` `Sub` procedure can't catch exceptions that are thrown by the `Sub` procedure.</span></span>

<span data-ttu-id="5b219-220">함수에 대 한 자세한 내용은 `Async` [Async 및 wait를 사용한 비동기 프로그래밍](../../programming-guide/concepts/async/index.md), [비동기 프로그램의 제어 흐름](../../programming-guide/concepts/async/control-flow-in-async-programs.md)및 [비동기 반환 형식](../../programming-guide/concepts/async/async-return-types.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5b219-220">For more information about `Async` functions, see [Asynchronous Programming with Async and Await](../../programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../programming-guide/concepts/async/async-return-types.md).</span></span>

## <a name="iterator-functions"></a><span data-ttu-id="5b219-221">반복기 함수</span><span class="sxs-lookup"><span data-stu-id="5b219-221">Iterator Functions</span></span>

<span data-ttu-id="5b219-222">*반복기* 함수는 목록 또는 배열과 같은 컬렉션에 대해 사용자 지정 반복을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-222">An *iterator* function performs a custom iteration over a collection, such as a list or array.</span></span> <span data-ttu-id="5b219-223">반복기 함수는 [Yield](yield-statement.md) 문을 사용 하 여 각 요소를 한 번에 하나씩 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-223">An iterator function uses the [Yield](yield-statement.md) statement to return each element one at a time.</span></span> <span data-ttu-id="5b219-224">[Yield](yield-statement.md) 문에 도달 하면 코드의 현재 위치가 기억 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-224">When a [Yield](yield-statement.md) statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="5b219-225">다음에 반복기 함수가 호출되면 해당 위치에서 실행이 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-225">Execution is restarted from that location the next time the iterator function is called.</span></span>

<span data-ttu-id="5b219-226">For Each ...를 사용 하 여 클라이언트 코드에서 반복기를 호출 합니다. [ 다음](for-each-next-statement.md) 문.</span><span class="sxs-lookup"><span data-stu-id="5b219-226">You call an iterator from client code by using a [For Each…Next](for-each-next-statement.md) statement.</span></span>

<span data-ttu-id="5b219-227">반복기 함수의 반환 형식은,, 또는 일 수 <xref:System.Collections.IEnumerable> 있습니다 <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.IEnumerator> <xref:System.Collections.Generic.IEnumerator%601> .</span><span class="sxs-lookup"><span data-stu-id="5b219-227">The return type of an iterator function can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="5b219-228">자세한 내용은 [반복기](../../programming-guide/concepts/iterators.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5b219-228">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>

## <a name="example"></a><span data-ttu-id="5b219-229">예제</span><span class="sxs-lookup"><span data-stu-id="5b219-229">Example</span></span>

<span data-ttu-id="5b219-230">다음 예에서는 문을 사용 하 여 `Function` 프로시저 본문을 구성 하는 이름, 매개 변수 및 코드를 선언 합니다 `Function` .</span><span class="sxs-lookup"><span data-stu-id="5b219-230">The following example uses the `Function` statement to declare the name, parameters, and code that form the body of a `Function` procedure.</span></span> <span data-ttu-id="5b219-231">`ParamArray`한정자를 사용 하면 함수에서 다양 한 수의 인수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-231">The `ParamArray` modifier enables the function to accept a variable number of arguments.</span></span>

[!code-vb[VbVbalrStatements#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#25)]

## <a name="example"></a><span data-ttu-id="5b219-232">예제</span><span class="sxs-lookup"><span data-stu-id="5b219-232">Example</span></span>

<span data-ttu-id="5b219-233">다음 예제에서는 앞의 예제에서 선언한 함수를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-233">The following example invokes the function declared in the preceding example.</span></span>

[!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]

## <a name="example"></a><span data-ttu-id="5b219-234">예제</span><span class="sxs-lookup"><span data-stu-id="5b219-234">Example</span></span>

<span data-ttu-id="5b219-235">다음 예제에서 `DelayAsync` 는 `Async` `Function` 반환 형식이 인입니다 <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="5b219-235">In the following example, `DelayAsync` is an `Async` `Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="5b219-236">`DelayAsync` 에는 정수를 반환하는 `Return` 문이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-236">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="5b219-237">따라서의 함수 선언에는 `DelayAsync` 의 반환 형식이 있어야 `Task(Of Integer)` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b219-237">Therefore the function declaration of `DelayAsync` needs to have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="5b219-238">반환 형식이 이므로 `Task(Of Integer)` `Await` 의 식 계산에서 정수를 생성 합니다 `DoSomethingAsync` .</span><span class="sxs-lookup"><span data-stu-id="5b219-238">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer.</span></span> <span data-ttu-id="5b219-239">이에 대 한 설명은 다음과 같습니다 `Dim result As Integer = Await delayTask` .</span><span class="sxs-lookup"><span data-stu-id="5b219-239">This is demonstrated in this statement: `Dim result As Integer = Await delayTask`.</span></span>

<span data-ttu-id="5b219-240">프로시저는 `startButton_Click` 프로시저의 예입니다 `Async Sub` .</span><span class="sxs-lookup"><span data-stu-id="5b219-240">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="5b219-241">는 함수 이기 때문에 `DoSomethingAsync` `Async` 에 대 한 호출에 대 한 작업은 `DoSomethingAsync` 다음 문과 같이 대기 되어야 합니다 `Await DoSomethingAsync()` ..</span><span class="sxs-lookup"><span data-stu-id="5b219-241">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement demonstrates: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="5b219-242">`startButton_Click` `Sub` 프로시저에 `Async` 식이 있으므로 한정자를 사용 하 여 프로시저를 정의 해야 합니다 `Await` .</span><span class="sxs-lookup"><span data-stu-id="5b219-242">The `startButton_Click` `Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a><span data-ttu-id="5b219-243">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5b219-243">See also</span></span>

- [<span data-ttu-id="5b219-244">Sub 문</span><span class="sxs-lookup"><span data-stu-id="5b219-244">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="5b219-245">함수 프로시저</span><span class="sxs-lookup"><span data-stu-id="5b219-245">Function Procedures</span></span>](../../programming-guide/language-features/procedures/function-procedures.md)
- [<span data-ttu-id="5b219-246">매개 변수 목록</span><span class="sxs-lookup"><span data-stu-id="5b219-246">Parameter List</span></span>](parameter-list.md)
- [<span data-ttu-id="5b219-247">Dim 문</span><span class="sxs-lookup"><span data-stu-id="5b219-247">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="5b219-248">Call 문</span><span class="sxs-lookup"><span data-stu-id="5b219-248">Call Statement</span></span>](call-statement.md)
- [<span data-ttu-id="5b219-249">으로</span><span class="sxs-lookup"><span data-stu-id="5b219-249">Of</span></span>](of-clause.md)
- [<span data-ttu-id="5b219-250">매개 변수 배열</span><span class="sxs-lookup"><span data-stu-id="5b219-250">Parameter Arrays</span></span>](../../programming-guide/language-features/procedures/parameter-arrays.md)
- [<span data-ttu-id="5b219-251">방법: 제네릭 클래스 사용</span><span class="sxs-lookup"><span data-stu-id="5b219-251">How to: Use a Generic Class</span></span>](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="5b219-252">프로시저 문제 해결</span><span class="sxs-lookup"><span data-stu-id="5b219-252">Troubleshooting Procedures</span></span>](../../programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [<span data-ttu-id="5b219-253">람다 식</span><span class="sxs-lookup"><span data-stu-id="5b219-253">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="5b219-254">함수 식</span><span class="sxs-lookup"><span data-stu-id="5b219-254">Function Expression</span></span>](../operators/function-expression.md)
