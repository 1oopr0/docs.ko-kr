---
title: Out(제네릭 한정자)
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceOut
helpviewer_keywords:
- Out keyword [Visual Basic]
- covariance, Out keyword [Visual Basic]
ms.assetid: c4418369-1518-4a46-9a1e-054c61038eca
ms.openlocfilehash: 28ae7d6fd51170aa822072fc2f5357443f51a353
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392095"
---
# <a name="out-generic-modifier-visual-basic"></a><span data-ttu-id="9be4f-102">Out(제네릭 한정자)(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9be4f-102">Out (Generic Modifier) (Visual Basic)</span></span>

<span data-ttu-id="9be4f-103">제네릭 형식 매개 변수의 경우 `Out` 키워드는 형식이 공변 (covariant) 임을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9be4f-103">For generic type parameters, the `Out` keyword specifies that the type is covariant.</span></span>

## <a name="remarks"></a><span data-ttu-id="9be4f-104">설명</span><span class="sxs-lookup"><span data-stu-id="9be4f-104">Remarks</span></span>

<span data-ttu-id="9be4f-105">공변성(covariance)을 통해 제네릭 매개 변수에 지정된 것보다 많은 파생 형식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9be4f-105">Covariance enables you to use a more derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="9be4f-106">따라서 variant 인터페이스를 구현하는 클래스의 암시적 변환과 대리자 형식의 암시적 변환이 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9be4f-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span>

<span data-ttu-id="9be4f-107">자세한 내용은 [공변성(Covariance) 및 반공변성(Contravariance)](../../programming-guide/concepts/covariance-contravariance/index.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9be4f-107">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

## <a name="rules"></a><span data-ttu-id="9be4f-108">규칙</span><span class="sxs-lookup"><span data-stu-id="9be4f-108">Rules</span></span>

<span data-ttu-id="9be4f-109">제네릭 인터페이스 및 대리자에서 `Out` 키워드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9be4f-109">You can use the `Out` keyword in generic interfaces and delegates.</span></span>

<span data-ttu-id="9be4f-110">제네릭 인터페이스에서 형식 매개 변수가 다음 조건을 충족하는 경우 공변(covariant)으로 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9be4f-110">In a generic interface, a type parameter can be declared covariant if it satisfies the following conditions:</span></span>

- <span data-ttu-id="9be4f-111">형식 매개 변수는 인터페이스 메서드의 반환 형식으로만 사용되고 메서드 인수의 형식으로 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9be4f-111">The type parameter is used only as a return type of interface methods and not used as a type of method arguments.</span></span>

    > [!NOTE]
    > <span data-ttu-id="9be4f-112">그러나 이 규칙에는 한 가지 예외가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9be4f-112">There is one exception to this rule.</span></span> <span data-ttu-id="9be4f-113">공변(covariant) 인터페이스에 메서드 매개 변수로 반공변(contravariant) 제네릭 대리자가 있는 경우 공변(covariant) 형식을 이 대리자에 대한 제네릭 형식 매개 변수로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9be4f-113">If in a covariant interface you have a contravariant generic delegate as a method parameter, you can use the covariant type as a generic type parameter for this delegate.</span></span> <span data-ttu-id="9be4f-114">공변(covariant) 및 반공변(contravariant) 제네릭 대리자에 대한 자세한 내용은 [대리자의 가변성](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) 및 [Func 및 Action 제네릭 대리자에 가변성 사용](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9be4f-114">For more information about covariant and contravariant generic delegates, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>

- <span data-ttu-id="9be4f-115">형식 매개 변수는 인터페이스 메서드에 대한 제네릭 제약 조건으로 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9be4f-115">The type parameter is not used as a generic constraint for the interface methods.</span></span>

<span data-ttu-id="9be4f-116">제네릭 대리자에서 형식 매개 변수는 메서드 반환 형식 으로만 사용 되 고 메서드 인수에는 사용 되지 않는 경우 공변 (covariant)으로 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9be4f-116">In a generic delegate, a type parameter can be declared covariant if it is used only as a method return type and not used for method arguments.</span></span>

<span data-ttu-id="9be4f-117">공변성(Covariance) 및 반공변성(Contravariance)은 참조 형식에 대해 지원되고 값 형식에 대해서는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9be4f-117">Covariance and contravariance are supported for reference types, but they are not supported for value types.</span></span>

<span data-ttu-id="9be4f-118">Visual Basic에서는 대리자 형식을 지정 하지 않고 공변 (covariant) 인터페이스에서 이벤트를 선언할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9be4f-118">In Visual Basic, you cannot declare events in covariant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="9be4f-119">또한 공변 (covariant) 인터페이스에는 중첩 된 클래스, 열거형 또는 구조체를 사용할 수 없지만 중첩 된 인터페이스가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9be4f-119">Also, covariant interfaces cannot have nested classes, enums, or structures, but they can have nested interfaces.</span></span>

## <a name="behavior"></a><span data-ttu-id="9be4f-120">동작</span><span class="sxs-lookup"><span data-stu-id="9be4f-120">Behavior</span></span>

<span data-ttu-id="9be4f-121">공변(covariant) 형식 매개 변수가 있는 인터페이스는 해당 메서드가 형식 인터페이스에 지정된 것보다 많은 파생 형식을 반환할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="9be4f-121">An interface that has a covariant type parameter enables its methods to return more derived types than those specified by the type parameter.</span></span> <span data-ttu-id="9be4f-122">예를 들어 .NET Framework 4의 <xref:System.Collections.Generic.IEnumerable%601>에서 T 형식은 공변(covariant)이므로 특수 변환 메서드를 사용하지 않고 `IEnumerable(Of String)` 형식의 개체를 `IEnumerable(Of Object)` 형식의 개체에 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9be4f-122">For example, because in .NET Framework 4, in <xref:System.Collections.Generic.IEnumerable%601>, type T is covariant, you can assign an object of the `IEnumerable(Of String)` type to an object of the `IEnumerable(Of Object)` type without using any special conversion methods.</span></span>

<span data-ttu-id="9be4f-123">공변(covariant) 대리자에 동일한 형식의 다른 대리자를 할당할 수 있지만 더 파생된 제네릭 형식 매개 변수가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="9be4f-123">A covariant delegate can be assigned another delegate of the same type, but with a more derived generic type parameter.</span></span>

## <a name="example"></a><span data-ttu-id="9be4f-124">예제</span><span class="sxs-lookup"><span data-stu-id="9be4f-124">Example</span></span>

<span data-ttu-id="9be4f-125">다음 예제에서는 공변(covariant) 제네릭 인터페이스를 선언, 확장 및 구현하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9be4f-125">The following example shows how to declare, extend, and implement a covariant generic interface.</span></span> <span data-ttu-id="9be4f-126">또한 공변(covariant) 인터페이스를 구현하는 클래스에 대해 암시적 변환을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9be4f-126">It also shows how to use implicit conversion for classes that implement a covariant interface.</span></span>

[!code-vb[vbVarianceKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#3)]

## <a name="example"></a><span data-ttu-id="9be4f-127">예제</span><span class="sxs-lookup"><span data-stu-id="9be4f-127">Example</span></span>

<span data-ttu-id="9be4f-128">다음 예제에서는 공변(covariant) 제네릭 대리자를 선언, 인스턴스화 및 호출하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9be4f-128">The following example shows how to declare, instantiate, and invoke a covariant generic delegate.</span></span> <span data-ttu-id="9be4f-129">또한 대리자 형식에 대해 암시적 변환을 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9be4f-129">It also shows how you can use implicit conversion for delegate types.</span></span>

[!code-vb[vbVarianceKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#4)]

## <a name="see-also"></a><span data-ttu-id="9be4f-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9be4f-130">See also</span></span>

- [<span data-ttu-id="9be4f-131">제네릭 인터페이스의 가변성</span><span class="sxs-lookup"><span data-stu-id="9be4f-131">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [<span data-ttu-id="9be4f-132">진행</span><span class="sxs-lookup"><span data-stu-id="9be4f-132">In</span></span>](in-generic-modifier.md)
