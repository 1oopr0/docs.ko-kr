---
title: 잘못된 패턴 문자열
ms.date: 07/20/2015
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
ms.openlocfilehash: aa408f4cecc2a2774cb98cba96cd04a67afcc546
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402215"
---
# <a name="invalid-pattern-string"></a><span data-ttu-id="3bb1d-102">잘못된 패턴 문자열</span><span class="sxs-lookup"><span data-stu-id="3bb1d-102">Invalid pattern string</span></span>
<span data-ttu-id="3bb1d-103">검색의 `Like` 작업에서 지정된 패턴 문자열이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3bb1d-103">The pattern string specified in the `Like` operation of a search is invalid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3bb1d-104">이 오류를 해결하려면</span><span class="sxs-lookup"><span data-stu-id="3bb1d-104">To correct this error</span></span>  
  
1. <span data-ttu-id="3bb1d-105">목록 식에 유효한 문자를 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="3bb1d-105">Review the valid characters for list expressions.</span></span>  
  
2. <span data-ttu-id="3bb1d-106">패턴 범위에서 `[a-z]`처럼 범위 시작 문자가 범위 끝 문자보다 작은지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3bb1d-106">In the pattern range, ensure that the start range character is less than the end range character, as in `[a-z]`.</span></span>  
  
3. <span data-ttu-id="3bb1d-107">패턴 범위에서 `[a--z]`처럼 여러 하이픈이 서로 인접하지 않는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3bb1d-107">In the pattern range, ensure that there are not multiple hyphens next to each other, as in `[a--z]`.</span></span>  
  
4. <span data-ttu-id="3bb1d-108">닫는 대괄호를 사용하여 패턴 범위를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="3bb1d-108">End pattern ranges with a closing bracket.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bb1d-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3bb1d-109">See also</span></span>

- [<span data-ttu-id="3bb1d-110">Like 연산자</span><span class="sxs-lookup"><span data-stu-id="3bb1d-110">Like Operator</span></span>](../language-reference/operators/like-operator.md)
