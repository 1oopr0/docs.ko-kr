---
title: <exception>
ms.date: 07/20/2015
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
ms.openlocfilehash: 3a2452ec60a2182adfee365777d9824001ff006a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400126"
---
# <a name="exception-visual-basic"></a><span data-ttu-id="45faf-101">\<exception>(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45faf-101">\<exception> (Visual Basic)</span></span>
<span data-ttu-id="45faf-102">Throw 할 수 있는 예외를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="45faf-102">Specifies which exceptions can be thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45faf-103">구문</span><span class="sxs-lookup"><span data-stu-id="45faf-103">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
## <a name="parameters"></a><span data-ttu-id="45faf-104">매개 변수</span><span class="sxs-lookup"><span data-stu-id="45faf-104">Parameters</span></span>  
 `member`  
 <span data-ttu-id="45faf-105">현재 컴파일 환경에서 사용할 수 있는 예외에 대한 참조입니다.</span><span class="sxs-lookup"><span data-stu-id="45faf-105">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="45faf-106">컴파일러는 지정된 예외가 있으며 `member`를 출력 XML의 정식 요소 이름으로 변환하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="45faf-106">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="45faf-107">`member`는 큰따옴표(" ")로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45faf-107">`member` must appear within double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="45faf-108">설명</span><span class="sxs-lookup"><span data-stu-id="45faf-108">A description.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45faf-109">설명</span><span class="sxs-lookup"><span data-stu-id="45faf-109">Remarks</span></span>  
 <span data-ttu-id="45faf-110">태그를 사용 `<exception>` 하 여 throw 할 수 있는 예외를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="45faf-110">Use the `<exception>` tag to specify which exceptions can be thrown.</span></span> <span data-ttu-id="45faf-111">이 태그는 메서드 정의에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="45faf-111">This tag is applied to a method definition.</span></span>  
  
 <span data-ttu-id="45faf-112">[-Doc](../../reference/command-line-compiler/doc.md) 로 컴파일하여 문서 주석을 파일로 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="45faf-112">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45faf-113">예제</span><span class="sxs-lookup"><span data-stu-id="45faf-113">Example</span></span>  
 <span data-ttu-id="45faf-114">이 예제에서는 태그를 사용 하 여 `<exception>` `IntDivide` 함수가 throw 할 수 있는 예외를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="45faf-114">This example uses the `<exception>` tag to describe an exception that the `IntDivide` function can throw.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="45faf-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="45faf-115">See also</span></span>

- [<span data-ttu-id="45faf-116">XML 주석 태그</span><span class="sxs-lookup"><span data-stu-id="45faf-116">XML Comment Tags</span></span>](index.md)
