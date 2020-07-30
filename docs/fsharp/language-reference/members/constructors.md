---
title: 생성자
description: 'F #에서 생성자를 정의 하 고 사용 하 여 클래스 및 구조체 개체를 만들고 초기화 하는 방법에 대해 알아봅니다.'
ms.date: 05/16/2016
ms.openlocfilehash: be8fc3f1d82a9a7c778a6d094139f14150a28813
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303441"
---
# <a name="constructors"></a><span data-ttu-id="1d996-103">생성자</span><span class="sxs-lookup"><span data-stu-id="1d996-103">Constructors</span></span>

<span data-ttu-id="1d996-104">이 문서에서는 생성자를 정의 하 고 사용 하 여 클래스 및 구조체 개체를 만들고 초기화 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d996-104">This article describes how to define and use constructors to create and initialize class and structure objects.</span></span>

## <a name="construction-of-class-objects"></a><span data-ttu-id="1d996-105">클래스 개체 생성</span><span class="sxs-lookup"><span data-stu-id="1d996-105">Construction of class objects</span></span>

<span data-ttu-id="1d996-106">클래스 형식의 개체에는 생성자가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d996-106">Objects of class types have constructors.</span></span> <span data-ttu-id="1d996-107">생성자에는 두 가지 종류가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d996-107">There are two kinds of constructors.</span></span> <span data-ttu-id="1d996-108">하나는 매개 변수가 형식 이름 바로 뒤에 괄호 안에 표시 되는 기본 생성자입니다.</span><span class="sxs-lookup"><span data-stu-id="1d996-108">One is the primary constructor, whose parameters appear in parentheses just after the type name.</span></span> <span data-ttu-id="1d996-109">키워드를 사용 하 여 다른 선택적 추가 생성자를 지정 `new` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d996-109">You specify other, optional additional constructors by using the `new` keyword.</span></span> <span data-ttu-id="1d996-110">이러한 추가 생성자는 기본 생성자를 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d996-110">Any such additional constructors must call the primary constructor.</span></span>

<span data-ttu-id="1d996-111">기본 생성자에는 `let` `do` 클래스 정의의 시작 부분에 표시 되는 및 바인딩이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d996-111">The primary constructor contains `let` and `do` bindings that appear at the start of the class definition.</span></span> <span data-ttu-id="1d996-112">`let`바인딩은 클래스의 전용 필드와 메서드를 선언 하 고, `do` 바인딩은 코드를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d996-112">A `let` binding declares private fields and methods of the class; a `do` binding executes code.</span></span> <span data-ttu-id="1d996-113">`let`클래스 생성자의 바인딩에 대 한 자세한 내용은 [ `let` 클래스의 바인딩](let-bindings-in-classes.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1d996-113">For more information about `let` bindings in class constructors, see [`let` Bindings in Classes](let-bindings-in-classes.md).</span></span> <span data-ttu-id="1d996-114">생성자의 바인딩에 대 한 자세한 내용은 `do` [ `do` 클래스의 바인딩](do-bindings-in-classes.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1d996-114">For more information about `do` bindings in constructors, see [`do` Bindings in Classes](do-bindings-in-classes.md).</span></span>

<span data-ttu-id="1d996-115">호출 하려는 생성자가 기본 생성자 인지 아니면 추가 생성자 인지에 관계 없이 `new` 식을 사용 하거나 선택적 키워드를 사용 하 여 개체를 만들 수 있습니다 `new` .</span><span class="sxs-lookup"><span data-stu-id="1d996-115">Regardless of whether the constructor you want to call is a primary constructor or an additional constructor, you can create objects by using a `new` expression, with or without the optional `new` keyword.</span></span> <span data-ttu-id="1d996-116">인수를 순서 대로 나열 하 고 쉼표로 구분한 다음 괄호로 묶거나 명명 된 인수 및 값을 괄호로 묶어 생성자 인수를 사용 하 여 개체를 초기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d996-116">You initialize your objects together with constructor arguments, either by listing the arguments in order and separated by commas and enclosed in parentheses, or by using named arguments and values in parentheses.</span></span> <span data-ttu-id="1d996-117">명명 된 생성자 인수를 사용 하는 것과 같이 속성 이름을 사용 하 고 값을 할당 하 여 개체를 생성 하는 동안 개체에 대 한 속성을 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d996-117">You can also set properties on an object during the construction of the object by using the property names and assigning values just as you use named constructor arguments.</span></span>

<span data-ttu-id="1d996-118">다음 코드는 생성자를 포함 하는 클래스와 개체를 만드는 다양 한 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1d996-118">The following code illustrates a class that has a constructor and various ways of creating objects:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3501.fs)]

<span data-ttu-id="1d996-119">출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1d996-119">The output is as follows:</span></span>

```console
Initialized object that has coordinates (1, 2, 3)
Initialized object that has coordinates (4, 5, 6)
Initialized object that has coordinates (7, 8, 9)
Initialized object that has coordinates (0, 0, 0)
```

## <a name="construction-of-structures"></a><span data-ttu-id="1d996-120">구조 생성</span><span class="sxs-lookup"><span data-stu-id="1d996-120">Construction of structures</span></span>

<span data-ttu-id="1d996-121">구조체는 클래스의 모든 규칙을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="1d996-121">Structures follow all the rules of classes.</span></span> <span data-ttu-id="1d996-122">따라서 기본 생성자를 사용 하 고를 사용 하 여 추가 생성자를 제공할 수 있습니다 `new` .</span><span class="sxs-lookup"><span data-stu-id="1d996-122">Therefore, you can have a primary constructor, and you can provide additional constructors by using `new`.</span></span> <span data-ttu-id="1d996-123">그러나 구조체와 클래스 사이에는 중요 한 차이점이 있습니다. 구조체에는 기본 생성자가 정의 되지 않은 경우에도 매개 변수가 없는 생성자 (인수 없이 하나)가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d996-123">However, there is one important difference between structures and classes: structures can have a parameterless constructor (that is, one with no arguments) even if no primary constructor is defined.</span></span> <span data-ttu-id="1d996-124">매개 변수가 없는 생성자는 모든 필드를 해당 형식에 대 한 기본값 (일반적으로 0 또는 그에 해당 하는 값)으로 초기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d996-124">The parameterless constructor initializes all the fields to the default value for that type, usually zero or its equivalent.</span></span> <span data-ttu-id="1d996-125">구조체에 대해 정의 하는 모든 생성자에는 매개 변수가 없는 생성자와 충돌 하지 않도록 하나 이상의 인수가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d996-125">Any constructors that you define for structures must have at least one argument so that they do not conflict with the parameterless constructor.</span></span>

<span data-ttu-id="1d996-126">또한 구조체는 키워드를 사용 하 여 만든 필드를 포함 하는 경우가 많습니다. `val` 클래스는 이러한 필드를 포함할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d996-126">Also, structures often have fields that are created by using the `val` keyword; classes can also have these fields.</span></span> <span data-ttu-id="1d996-127">다음 코드에 표시 된 것 처럼 키워드를 사용 하 여 정의 된 필드가 있는 구조체와 클래스는 `val` 레코드 식을 사용 하 여 추가 생성자에서 초기화 될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d996-127">Structures and classes that have fields defined by using the `val` keyword can also be initialized in additional constructors by using record expressions, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3502.fs)]

<span data-ttu-id="1d996-128">자세한 내용은 [명시적 필드: `val` 키워드를](explicit-fields-the-val-keyword.md)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1d996-128">For more information, see [Explicit Fields: The `val` Keyword](explicit-fields-the-val-keyword.md).</span></span>

## <a name="executing-side-effects-in-constructors"></a><span data-ttu-id="1d996-129">생성자에서 의도 하지 않은 결과 실행</span><span class="sxs-lookup"><span data-stu-id="1d996-129">Executing side effects in constructors</span></span>

<span data-ttu-id="1d996-130">클래스의 기본 생성자는 바인딩에서 코드를 실행할 수 있습니다 `do` .</span><span class="sxs-lookup"><span data-stu-id="1d996-130">A primary constructor in a class can execute code in a `do` binding.</span></span> <span data-ttu-id="1d996-131">그러나 바인딩을 사용 하지 않고 추가 생성자에서 코드를 실행 해야 하는 경우는 어떻게 `do` 되나요?</span><span class="sxs-lookup"><span data-stu-id="1d996-131">However, what if you have to execute code in an additional constructor, without a `do` binding?</span></span> <span data-ttu-id="1d996-132">이렇게 하려면 키워드를 사용 `then` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d996-132">To do this, you use the `then` keyword.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3503.fs)]

<span data-ttu-id="1d996-133">기본 생성자의 부작용은 계속 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d996-133">The side effects of the primary constructor still execute.</span></span> <span data-ttu-id="1d996-134">따라서 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1d996-134">Therefore, the output is as follows:</span></span>

```console
Created a person object.
Created a person object.
Created an invalid person object.
```

<span data-ttu-id="1d996-135">`then`대신이 필요한 이유는 `do` 키워드에 `do` `unit` 추가 생성자의 본문에 있는 경우 반환 식을 구분 하는 표준 의미가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d996-135">The reason why `then` is required instead of another `do` is that the `do` keyword has its standard meaning of delimiting a `unit`-returning expression when present in the body of an additional constructor.</span></span> <span data-ttu-id="1d996-136">기본 생성자의 컨텍스트에서는 특별 한 의미가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d996-136">It only has special meaning in the context of primary constructors.</span></span>

## <a name="self-identifiers-in-constructors"></a><span data-ttu-id="1d996-137">생성자의 자체 식별자</span><span class="sxs-lookup"><span data-stu-id="1d996-137">Self identifiers in constructors</span></span>

<span data-ttu-id="1d996-138">다른 멤버의 경우에는 각 멤버의 정의에서 현재 개체의 이름을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d996-138">In other members, you provide a name for the current object in the definition of each member.</span></span> <span data-ttu-id="1d996-139">생성자 매개 변수 바로 뒤에 키워드를 사용 하 여 클래스 정의의 첫 번째 줄에 자체 식별자를 넣을 수도 있습니다 `as` .</span><span class="sxs-lookup"><span data-stu-id="1d996-139">You can also put the self identifier on the first line of the class definition by using the `as` keyword immediately following the constructor parameters.</span></span> <span data-ttu-id="1d996-140">다음 예제에서는이 구문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1d996-140">The following example illustrates this syntax.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3504.fs)]

<span data-ttu-id="1d996-141">추가 생성자에서 생성자 매개 변수 바로 뒤에 절을 추가 하 여 자체 식별자를 정의할 수도 있습니다 `as` .</span><span class="sxs-lookup"><span data-stu-id="1d996-141">In additional constructors, you can also define a self identifier by putting the `as` clause right after the constructor parameters.</span></span> <span data-ttu-id="1d996-142">다음 예제에서는이 구문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1d996-142">The following example illustrates this syntax:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3505.fs)]

<span data-ttu-id="1d996-143">개체를 완전히 정의 하기 전에 사용 하려고 하면 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d996-143">Problems can occur when you try to use an object before it is fully defined.</span></span> <span data-ttu-id="1d996-144">따라서 자체 식별자를 사용 하면 컴파일러에서 경고를 내보내고 추가 검사를 삽입 하 여 개체를 초기화 하기 전에 개체의 멤버에 액세스할 수 없도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d996-144">Therefore, uses of the self identifier can cause the compiler to emit a warning and insert additional checks to ensure the members of an object are not accessed before the object is initialized.</span></span> <span data-ttu-id="1d996-145">`do`기본 생성자의 바인딩이나 추가 생성자의 키워드 뒤에 있는 자체 식별자만 사용 해야 합니다 `then` .</span><span class="sxs-lookup"><span data-stu-id="1d996-145">You should only use the self identifier in the `do` bindings of the primary constructor, or after the `then` keyword in additional constructors.</span></span>

<span data-ttu-id="1d996-146">자체 식별자의 이름은 일 필요가 없습니다 `this` .</span><span class="sxs-lookup"><span data-stu-id="1d996-146">The name of the self identifier does not have to be `this`.</span></span> <span data-ttu-id="1d996-147">유효한 식별자 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d996-147">It can be any valid identifier.</span></span>

## <a name="assigning-values-to-properties-at-initialization"></a><span data-ttu-id="1d996-148">초기화할 때 속성에 값 할당</span><span class="sxs-lookup"><span data-stu-id="1d996-148">Assigning values to properties at initialization</span></span>

<span data-ttu-id="1d996-149">생성자의 인수 목록에 폼의 할당 목록을 추가 하 여 초기화 코드에서 클래스 개체의 속성에 값을 할당할 수 있습니다 `property = value` .</span><span class="sxs-lookup"><span data-stu-id="1d996-149">You can assign values to the properties of a class object in the initialization code by appending a list of assignments of the form `property = value` to the argument list for a constructor.</span></span> <span data-ttu-id="1d996-150">다음 코드 예를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1d996-150">This is shown in the following code example:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="1d996-151">이전 코드의 다음 버전에서는 단일 생성자 호출에서 일반 인수, 선택적 인수 및 속성 설정의 조합을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1d996-151">The following version of the previous code illustrates the combination of ordinary arguments, optional arguments, and property settings in one constructor call:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3507.fs)]

## <a name="constructors-in-inherited-class"></a><span data-ttu-id="1d996-152">상속 된 클래스의 생성자</span><span class="sxs-lookup"><span data-stu-id="1d996-152">Constructors in inherited class</span></span>

<span data-ttu-id="1d996-153">생성자가 있는 기본 클래스에서 상속 하는 경우 상속 절에서 해당 인수를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d996-153">When inheriting from a base class that has a constructor, you must specify its arguments in the inherit clause.</span></span> <span data-ttu-id="1d996-154">자세한 내용은 [생성자 및 상속](../inheritance.md#constructors-and-inheritance)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1d996-154">For more information, see [Constructors and inheritance](../inheritance.md#constructors-and-inheritance).</span></span>

## <a name="static-constructors-or-type-constructors"></a><span data-ttu-id="1d996-155">정적 생성자 또는 형식 생성자</span><span class="sxs-lookup"><span data-stu-id="1d996-155">Static constructors or type constructors</span></span>

<span data-ttu-id="1d996-156">개체를 만들기 위한 코드를 지정 하는 것 외에도 형식 `let` `do` 수준에서 초기화를 수행 하기 위해 형식을 처음 사용 하기 전에 실행 되는 클래스 형식으로 정적 및 바인딩을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d996-156">In addition to specifying code for creating objects, static `let` and `do` bindings can be authored in class types that execute before the type is first used to perform initialization at the type level.</span></span> <span data-ttu-id="1d996-157">자세한 내용은 클래스의 [ `let` 바인딩](let-bindings-in-classes.md) 및 [ `do` 클래스의 바인딩](do-bindings-in-classes.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1d996-157">For more information, see [`let` Bindings in Classes](let-bindings-in-classes.md) and [`do` Bindings in Classes](do-bindings-in-classes.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1d996-158">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1d996-158">See also</span></span>

- [<span data-ttu-id="1d996-159">멤버</span><span class="sxs-lookup"><span data-stu-id="1d996-159">Members</span></span>](index.md)
