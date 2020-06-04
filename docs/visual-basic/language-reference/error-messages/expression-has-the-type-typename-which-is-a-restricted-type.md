---
title: 식에 있는 '<typename>' 형식은 제한된 형식이므로 'Object' 또는 'ValueType'에서 상속된 멤버에 액세스하는 데 사용할 수 없습니다.
ms.date: 07/20/2015
f1_keywords:
- bc31393
- vbc31393
helpviewer_keywords:
- BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
ms.openlocfilehash: 0eb30488312cc7519f39a6b819aea15489f2f70a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409522"
---
# <a name="expression-has-the-type-typename-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-object-or-valuetype"></a><span data-ttu-id="53737-102">식에 있는 '\<typename>' 형식은 제한된 형식이므로 'Object' 또는 'ValueType'에서 상속된 멤버에 액세스하는 데 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="53737-102">Expression has the type '\<typename>' which is a restricted type and cannot be used to access members inherited from 'Object' or 'ValueType'</span></span>
<span data-ttu-id="53737-103">식이 CLR (공용 언어 런타임)에 의해 boxing 될 수 없는 형식으로 계산 되지만 boxing이 필요한 멤버에 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="53737-103">An expression evaluates to a type that cannot be boxed by the common language runtime (CLR) but accesses a member that requires boxing.</span></span>  
  
 <span data-ttu-id="53737-104">*Boxing* 은 형식을 경우에 따라 `Object` 또는 <xref:System.ValueType>으로 변환하는 데 필요한 처리를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="53737-104">*Boxing* refers to the processing necessary to convert a type to `Object` or, on occasion, to <xref:System.ValueType>.</span></span> <span data-ttu-id="53737-105">공용 언어 런타임에서는 특정 구조체 형식 (예:, 및)을 box 할 수 없습니다 <xref:System.ArgIterator> <xref:System.RuntimeArgumentHandle> <xref:System.TypedReference> .</span><span class="sxs-lookup"><span data-stu-id="53737-105">The common language runtime cannot box certain structure types, for example <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, and <xref:System.TypedReference>.</span></span>  
  
 <span data-ttu-id="53737-106">이 식은 또는와 같이 제한 된 형식을 사용 하 여 또는에서 상속 된 메서드를 호출 하려고 <xref:System.Object> <xref:System.ValueType> <xref:System.Object.GetHashCode%2A> <xref:System.Object.ToString%2A> 합니다.</span><span class="sxs-lookup"><span data-stu-id="53737-106">This expression attempts to use the restricted type to call a method inherited from <xref:System.Object> or <xref:System.ValueType>, such as <xref:System.Object.GetHashCode%2A> or <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="53737-107">이 메서드에 액세스 하기 위해 Visual Basic에서이 오류를 발생 시키는 암시적 boxing 변환을 시도 했습니다.</span><span class="sxs-lookup"><span data-stu-id="53737-107">To access this method, Visual Basic has attempted an implicit boxing conversion that causes this error.</span></span>  
  
 <span data-ttu-id="53737-108">**오류 ID:** BC31393</span><span class="sxs-lookup"><span data-stu-id="53737-108">**Error ID:** BC31393</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="53737-109">이 오류를 해결하려면</span><span class="sxs-lookup"><span data-stu-id="53737-109">To correct this error</span></span>  
  
1. <span data-ttu-id="53737-110">제시된 형식으로 계산되는 식을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="53737-110">Locate the expression that evaluates to the cited type.</span></span>  
  
2. <span data-ttu-id="53737-111">또는에서 상속 된 메서드를 호출 하려고 하는 문의 일부를 찾습니다 <xref:System.Object> <xref:System.ValueType> .</span><span class="sxs-lookup"><span data-stu-id="53737-111">Locate the part of your statement that attempts to call the method inherited from <xref:System.Object> or <xref:System.ValueType>.</span></span>  
  
3. <span data-ttu-id="53737-112">메서드 호출을 방지 하려면 문을 다시 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="53737-112">Rewrite the statement to avoid the method call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53737-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="53737-113">See also</span></span>

- [<span data-ttu-id="53737-114">암시적 변환과 명시적 변환</span><span class="sxs-lookup"><span data-stu-id="53737-114">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
