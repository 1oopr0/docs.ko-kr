---
title: '방법: 정규화 경로가 긴 개체에 대한 액세스 속도 개선'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
ms.openlocfilehash: fe93e7bac2a21f1060d1f93765eb35e1ad0c7eb0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410414"
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a><span data-ttu-id="cf736-102">방법: 정규화 경로가 긴 개체에 대한 액세스 속도 개선(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf736-102">How to: Speed Up Access to an Object with a Long Qualification Path (Visual Basic)</span></span>

<span data-ttu-id="cf736-103">여러 메서드 및 속성의 정규화 경로를 필요로 하는 개체에 자주 액세스 하는 경우 한정 경로를 반복 하지 않고 코드 속도를 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf736-103">If you frequently access an object that requires a qualification path of several methods and properties, you can speed up your code by not repeating the qualification path.</span></span>

<span data-ttu-id="cf736-104">두 가지 방법으로 한정 경로를 반복 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf736-104">There are two ways you can avoid repeating the qualification path.</span></span> <span data-ttu-id="cf736-105">개체를 변수에 할당 하거나 ... 블록에서 사용할 수 있습니다. `With` `End With`</span><span class="sxs-lookup"><span data-stu-id="cf736-105">You can assign the object to a variable, or you can use it in a `With`...`End With` block.</span></span>

### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a><span data-ttu-id="cf736-106">변수에 할당 하 여 높은 정규화 된 개체에 대 한 액세스 속도를 높이려면</span><span class="sxs-lookup"><span data-stu-id="cf736-106">To speed up access to a heavily qualified object by assigning it to a variable</span></span>

1. <span data-ttu-id="cf736-107">자주 액세스 하는 개체의 형식에 대 한 변수를 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf736-107">Declare a variable of the type of the object that you are accessing frequently.</span></span> <span data-ttu-id="cf736-108">선언의 초기화 부분에서 한정 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf736-108">Specify the qualification path in the initialization part of the declaration.</span></span>

    ```vb
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl
    ```

2. <span data-ttu-id="cf736-109">변수를 사용 하 여 개체의 멤버에 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf736-109">Use the variable to access the object's members.</span></span>

    ```vb
    ctrlActv.Text = "Test"
    ctrlActv.Location = New Point(100, 100)
    ctrlActv.Show()
    ```

### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a><span data-ttu-id="cf736-110">을 사용 하 여 높은 정규화 된 개체에 대 한 액세스 속도를 높이려면 ... 블록으로 끝</span><span class="sxs-lookup"><span data-stu-id="cf736-110">To speed up access to a heavily qualified object by using a With...End With block</span></span>

1. <span data-ttu-id="cf736-111">문에 한정 경로를 넣습니다 `With` .</span><span class="sxs-lookup"><span data-stu-id="cf736-111">Put the qualification path in a `With` statement.</span></span>

    ```vb
    With someForm.ActiveForm.ActiveControl
    ```

2. <span data-ttu-id="cf736-112">문 앞의 블록 내에서 개체의 멤버에 액세스 합니다 `With` `End With` .</span><span class="sxs-lookup"><span data-stu-id="cf736-112">Access the object's members inside the `With` block, before the `End With` statement.</span></span>

    ```vb
        .Text = "Test"
        .Location = New Point(100, 100)
        .Show()
    End With
    ```

## <a name="see-also"></a><span data-ttu-id="cf736-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cf736-113">See also</span></span>

- [<span data-ttu-id="cf736-114">개체 변수</span><span class="sxs-lookup"><span data-stu-id="cf736-114">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="cf736-115">With...End With 문</span><span class="sxs-lookup"><span data-stu-id="cf736-115">With...End With Statement</span></span>](../../../language-reference/statements/with-end-with-statement.md)
