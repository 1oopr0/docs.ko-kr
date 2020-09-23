---
title: 상수 개요
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic]
ms.assetid: 29016fe8-78b3-4dc8-90b8-1cfec2fa8ac9
ms.openlocfilehash: 7f2a2dc140352588246d80a7feb46ce1f609b358
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086285"
---
# <a name="constants-overview-visual-basic"></a><span data-ttu-id="47806-102">상수 개요(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="47806-102">Constants Overview (Visual Basic)</span></span>

<span data-ttu-id="47806-103">상수는 변경 되지 않는 숫자 또는 문자열을 대신 사용 하는 의미 있는 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="47806-103">A constant is a meaningful name that takes the place of a number or string that does not change.</span></span> <span data-ttu-id="47806-104">상수는 이름이 암시 하는 것 처럼 응용 프로그램 실행 전체에서 동일 하 게 유지 되는 값을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="47806-104">Constants store values that, as the name implies, remain the same throughout the execution of an application.</span></span> <span data-ttu-id="47806-105">코드의 가독성을 크게 향상 시키고 상수를 사용 하 여 더 쉽게 유지 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47806-105">You can greatly improve the readability of your code and make it easier to maintain by using constants.</span></span> <span data-ttu-id="47806-106">이러한 값을 포함 하는 코드에서 사용 하거나, 기억할 수 없는 특정 숫자에 따라 달라 지는 코드 또는 분명 한 의미가 없는 코드에서 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="47806-106">Use them in code that contains values that reappear or that depends on certain numbers that are difficult to remember or have no obvious meaning.</span></span>  
  
## <a name="how-to-create-and-use-constants"></a><span data-ttu-id="47806-107">상수를 만들고 사용 하는 방법</span><span class="sxs-lookup"><span data-stu-id="47806-107">How to Create and Use Constants</span></span>  

 <span data-ttu-id="47806-108">Visual Basic에는 인쇄 및 표시를 위해 주로 사용 되는 미리 정의 된 여러 상수가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47806-108">Visual Basic contains a number of predefined constants, mainly using for printing and displaying.</span></span> <span data-ttu-id="47806-109">`Const`변수 이름을 만드는 것과 동일한 지침을 사용 하 여 문을 사용 하 여 사용자 고유의 상수를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47806-109">You can also create your own constants with the `Const` statement, using the same guidelines you would for creating a variable name.</span></span> <span data-ttu-id="47806-110">`Option Strict`가 이면 `On` 상수 형식을 명시적으로 선언 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47806-110">If `Option Strict` is `On`, you must explicitly declare the constant type.</span></span>  
  
 <span data-ttu-id="47806-111">이름을 한정 하지 않고이를 참조할 수 있는 모든 코드 집합인 상수 범위는 동일한 위치에 선언 된 변수의 변수와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="47806-111">A constant's scope, which is the set of all code that can refer to it without qualifying its name, is the same as that of a variable declared in the same location.</span></span> <span data-ttu-id="47806-112">특정 프로시저의 범위 내에 있는 상수를 만들려면 해당 프로시저 내에서 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="47806-112">To create a constant that exists within the scope of a particular procedure, declare it inside that procedure.</span></span> <span data-ttu-id="47806-113">응용 프로그램 전체에서 사용할 수 있는 상수를 만들려면 `Public` 클래스의 선언 섹션에서 키워드를 사용 하 여 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="47806-113">To create a constant that is available throughout an application, declare it using the `Public` keyword in the declarations section of the class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="47806-114">상수는 변수와 유사 하지만 변수를 수정할 수 있는 값으로 변경 하거나 새 값을 할당할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47806-114">Although constants somewhat resemble variables, you cannot modify them or assign new values to them as you can to variables.</span></span>  
  
 <span data-ttu-id="47806-115">사용자가 작업 하는 컨트롤 또는 구성 요소에 대 한 개체 모델을 사용 하 여 코드에서 사용 하는 상수를 정의 하거나 사용자가 직접 만든 상수를 사용자가 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47806-115">The constants you use in your code can be defined by the object model for controls or components you work with, or they can be user-defined (that is, those you create yourself).</span></span>  
  
## <a name="compile-time-and-run-time-constants"></a><span data-ttu-id="47806-116">컴파일 시간 및 런타임 상수</span><span class="sxs-lookup"><span data-stu-id="47806-116">Compile-time and Run-time Constants</span></span>  

 <span data-ttu-id="47806-117">컴파일 타임 상수는 코드를 컴파일할 때 계산 되지만 런타임 상수는 응용 프로그램이 실행 되는 동안에만 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47806-117">A compile-time constant is computed at the time the code is compiled, while a run-time constant can only be computed while the application is running.</span></span> <span data-ttu-id="47806-118">컴파일 타임 상수는 응용 프로그램이 실행 될 때마다 동일한 값을 갖게 되지만 런타임 상수는 매번 변경 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47806-118">A compile-time constant will have the same value each time an application runs, while a run-time constant may change each time.</span></span> <span data-ttu-id="47806-119">배열 범위, case 식 또는 열거자 이니셜라이저와 같은 경우에는 컴파일 시간 상수가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="47806-119">Compile-time constants are required for cases such as array bounds, case expressions, or enumerator initializers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="47806-120">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="47806-120">In This Section</span></span>  
  
|<span data-ttu-id="47806-121">정의</span><span class="sxs-lookup"><span data-stu-id="47806-121">Definition</span></span>|<span data-ttu-id="47806-122">용어</span><span class="sxs-lookup"><span data-stu-id="47806-122">Term</span></span>|  
|---|---|  
|[<span data-ttu-id="47806-123">방법: 상수 선언</span><span class="sxs-lookup"><span data-stu-id="47806-123">How to: Declare A Constant</span></span>](how-to-declare-a-constant.md)|<span data-ttu-id="47806-124">문을 사용 하 여 상수를 선언 하 고 값을 설정 하는 방법을 설명 합니다 `Const` . 상수를 선언 하 여 값에 의미 있는 이름을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="47806-124">Explains how to use the `Const` statement to declare a constant and set its value; by declaring a constant, you assign a meaningful name to the value.</span></span>|  
|[<span data-ttu-id="47806-125">사용자 정의 상수</span><span class="sxs-lookup"><span data-stu-id="47806-125">User-Defined Constants</span></span>](user-defined-constants.md)|<span data-ttu-id="47806-126">범위 지정 및 순환 참조를 방지 하는 방법에 대 한 정보를 포함 하 여 고유한 상수를 만드는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="47806-126">Describes how to create your own constants, including information on scoping and how to avoid circular references.</span></span>|  
|[<span data-ttu-id="47806-127">상수 및 리터럴 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="47806-127">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)|<span data-ttu-id="47806-128">가 해제 될 때 Visual Basic 컴파일러가 상수를 초기화 하는 방법에 대 한 정보를 제공 합니다 `Option Explicit` .</span><span class="sxs-lookup"><span data-stu-id="47806-128">Provides information on how the Visual Basic compiler initializes constants when `Option Explicit` is turned off.</span></span>|  
|[<span data-ttu-id="47806-129">방법: 관련 상수 값 그룹화</span><span class="sxs-lookup"><span data-stu-id="47806-129">How to: Group Related Constant Values Together</span></span>](how-to-group-related-constant-values-together.md)|<span data-ttu-id="47806-130">관련 된 상수 값을 그룹화 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="47806-130">Demonstrates how to group constant values that are related.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="47806-131">참조</span><span class="sxs-lookup"><span data-stu-id="47806-131">Reference</span></span>  
  
|<span data-ttu-id="47806-132">정의</span><span class="sxs-lookup"><span data-stu-id="47806-132">Definition</span></span>|<span data-ttu-id="47806-133">용어</span><span class="sxs-lookup"><span data-stu-id="47806-133">Term</span></span>|  
|---|---|  
|[<span data-ttu-id="47806-134">상수 및 열거형</span><span class="sxs-lookup"><span data-stu-id="47806-134">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)|<span data-ttu-id="47806-135">Visual Basic에서 미리 정의 된 상수를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="47806-135">Lists the constants predefined by Visual Basic.</span></span>|  
|[<span data-ttu-id="47806-136">Const 문</span><span class="sxs-lookup"><span data-stu-id="47806-136">Const Statement</span></span>](../../../language-reference/statements/const-statement.md)|<span data-ttu-id="47806-137">문과 사용에 대해 설명 합니다 `Const` .</span><span class="sxs-lookup"><span data-stu-id="47806-137">Describes the `Const` statement and its use.</span></span>|  
|[<span data-ttu-id="47806-138">Option Strict 문</span><span class="sxs-lookup"><span data-stu-id="47806-138">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)|<span data-ttu-id="47806-139">문과 사용에 대해 설명 합니다 `Option Strict` .</span><span class="sxs-lookup"><span data-stu-id="47806-139">Describes the `Option Strict` statement and its use.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="47806-140">참조</span><span class="sxs-lookup"><span data-stu-id="47806-140">See also</span></span>

- [<span data-ttu-id="47806-141">열거형 개요</span><span class="sxs-lookup"><span data-stu-id="47806-141">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="47806-142">방법: Visual Basic에서 배열 변수 초기화</span><span class="sxs-lookup"><span data-stu-id="47806-142">How to: Initialize an Array Variable in Visual Basic</span></span>](../arrays/how-to-initialize-an-array-variable.md)
