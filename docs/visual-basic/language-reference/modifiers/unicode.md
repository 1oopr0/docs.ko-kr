---
title: 유니코드(Unicode)
ms.date: 07/20/2015
f1_keywords:
- vb.Unicode
helpviewer_keywords:
- Unicode, external references
- Declare statement [Visual Basic], marshaling strings
- Unicode keyword [Visual Basic]
- Unicode, marshaling strings
ms.assetid: 0021d5ff-3209-444e-8497-420f3e6ee075
ms.openlocfilehash: 9b1bc40bb52244deefc0486d3a40c4b961ad1ee5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402683"
---
# <a name="unicode-visual-basic"></a><span data-ttu-id="2c320-102">Unicode(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2c320-102">Unicode (Visual Basic)</span></span>
<span data-ttu-id="2c320-103">선언 되는 외부 프로시저의 이름에 관계 없이 모든 문자열을 유니코드 값으로 마샬링하 Visual Basic 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c320-103">Specifies that Visual Basic should marshal all strings to Unicode values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="2c320-104">프로젝트 외부에서 정의 된 프로시저를 호출 하는 경우 Visual Basic 컴파일러는 프로시저를 올바르게 호출 하기 위해 가져야 하는 정보에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2c320-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have in order to call the procedure correctly.</span></span> <span data-ttu-id="2c320-105">이 정보에는 프로시저가 있는 위치, 식별 방법, 호출 시퀀스 및 반환 형식, 사용 하는 문자열 문자 집합이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c320-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="2c320-106">[Declare 문은](../statements/declare-statement.md) 외부 프로시저에 대 한 참조를 만들고이 필요한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c320-106">The [Declare Statement](../statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="2c320-107">`charsetmodifier` `Declare` 문의 부분은 외부 프로시저를 호출 하는 동안 문자열을 마샬링하는 문자 집합 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c320-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information to marshal strings during a call to the external procedure.</span></span> <span data-ttu-id="2c320-108">외부 파일에서 외부 프로시저 이름을 검색 Visual Basic는 방법에도 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2c320-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="2c320-109">`Unicode`한정자는 Visual Basic 모든 문자열을 유니코드 값으로 마샬링하고 검색 하는 동안 해당 이름을 수정 하지 않고 프로시저를 조회 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c320-109">The `Unicode` modifier specifies that Visual Basic should marshal all strings to Unicode values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="2c320-110">문자 집합 한정자가 지정 되지 않은 경우 `Ansi` 가 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="2c320-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c320-111">설명</span><span class="sxs-lookup"><span data-stu-id="2c320-111">Remarks</span></span>  
 <span data-ttu-id="2c320-112">`Unicode`이 컨텍스트에서는 한정자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c320-112">The `Unicode` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="2c320-113">Declare 문</span><span class="sxs-lookup"><span data-stu-id="2c320-113">Declare Statement</span></span>](../statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="2c320-114">스마트 디바이스 개발자 노트</span><span class="sxs-lookup"><span data-stu-id="2c320-114">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="2c320-115">이 키워드는 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2c320-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c320-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2c320-116">See also</span></span>

- [<span data-ttu-id="2c320-117">Ansi</span><span class="sxs-lookup"><span data-stu-id="2c320-117">Ansi</span></span>](ansi.md)
- [<span data-ttu-id="2c320-118">자동</span><span class="sxs-lookup"><span data-stu-id="2c320-118">Auto</span></span>](auto.md)
- [<span data-ttu-id="2c320-119">C++ 키워드</span><span class="sxs-lookup"><span data-stu-id="2c320-119">Keywords</span></span>](../keywords/index.md)
