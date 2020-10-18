---
title: "'Extension' 특성은 'Module', 'Sub' 또는 'Function' 선언에만 적용할 수 있습니다."
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: bd4d14721b93800831dbce897535b4f5956fe9c7
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160752"
---
# <a name="bc36550-extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations"></a><span data-ttu-id="6da0d-102">BC36550: ' Extension ' 특성은 ' Module ', ' Sub ' 또는 ' Function ' 선언에만 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6da0d-102">BC36550: 'Extension' attribute can be applied only to 'Module', 'Sub', or 'Function' declarations</span></span>

<span data-ttu-id="6da0d-103">Visual Basic에서 데이터 형식을 확장 하는 유일한 방법은 표준 모듈 내에 확장 메서드를 정의 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6da0d-103">The only way to extend a data type in Visual Basic is to define an extension method inside a standard module.</span></span> <span data-ttu-id="6da0d-104">확장 메서드는 `Sub` 프로시저 또는 프로시저일 수 있습니다 `Function` .</span><span class="sxs-lookup"><span data-stu-id="6da0d-104">The extension method can be a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="6da0d-105">모든 확장 메서드는 `<Extension()>` 네임 스페이스에서 확장 특성으로 표시 되어야 합니다 <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6da0d-105">All extension methods must be marked with the extension attribute, `<Extension()>`, from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="6da0d-106">필요에 따라 확장 메서드를 포함 하는 모듈을 동일한 방식으로 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6da0d-106">Optionally, a module that contains an extension method may be marked in the same way.</span></span> <span data-ttu-id="6da0d-107">확장 특성은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6da0d-107">No other use of the extension attribute is valid.</span></span>

<span data-ttu-id="6da0d-108">**오류 ID:** BC36550</span><span class="sxs-lookup"><span data-stu-id="6da0d-108">**Error ID:** BC36550</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="6da0d-109">이 오류를 해결하려면</span><span class="sxs-lookup"><span data-stu-id="6da0d-109">To correct this error</span></span>

- <span data-ttu-id="6da0d-110">확장 특성을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="6da0d-110">Remove the extension attribute.</span></span>

- <span data-ttu-id="6da0d-111">바깥쪽 모듈에 정의 된 메서드로 확장을 다시 디자인 합니다.</span><span class="sxs-lookup"><span data-stu-id="6da0d-111">Redesign your extension as a method, defined in an enclosing module.</span></span>

## <a name="example"></a><span data-ttu-id="6da0d-112">예제</span><span class="sxs-lookup"><span data-stu-id="6da0d-112">Example</span></span>

<span data-ttu-id="6da0d-113">다음 예제에서는 `Print` 데이터 형식에 대 한 메서드를 정의 합니다 `String` .</span><span class="sxs-lookup"><span data-stu-id="6da0d-113">The following example defines a `Print` method for the `String` data type.</span></span>

```vb
Imports StringUtility
Imports System.Runtime.CompilerServices
Namespace StringUtility
    <Extension()>
    Module StringExtensions
        <Extension()>
        Public Sub Print (ByVal str As String)
            Console.WriteLine(str)
        End Sub
    End Module
End Namespace
```

## <a name="see-also"></a><span data-ttu-id="6da0d-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6da0d-114">See also</span></span>

- [<span data-ttu-id="6da0d-115">특성 개요</span><span class="sxs-lookup"><span data-stu-id="6da0d-115">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="6da0d-116">확장명 메서드</span><span class="sxs-lookup"><span data-stu-id="6da0d-116">Extension Methods</span></span>](../../programming-guide/language-features/procedures/extension-methods.md)
- [<span data-ttu-id="6da0d-117">Module 문</span><span class="sxs-lookup"><span data-stu-id="6da0d-117">Module Statement</span></span>](../statements/module-statement.md)
