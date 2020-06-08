---
title: '방법: 애플리케이션 설정 읽기'
ms.date: 07/20/2015
helpviewer_keywords:
- reading application settings
- My.Settings object [Visual Basic], reading application settings
- application settings [Visual Basic], reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
ms.openlocfilehash: 9b326341c54d652479776e3ab93a2b140f4531e0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410142"
---
# <a name="how-to-read-application-settings-in-visual-basic"></a><span data-ttu-id="fe114-102">방법: Visual Basic에서 애플리케이션 설정 읽기</span><span class="sxs-lookup"><span data-stu-id="fe114-102">How to: Read Application Settings in Visual Basic</span></span>

<span data-ttu-id="fe114-103">`My.Settings` 개체에서 설정의 속성에 액세스하여 사용자 설정을 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe114-103">You can read a user setting by accessing the setting's property on the `My.Settings` object.</span></span>  
  
 <span data-ttu-id="fe114-104">`My.Settings` 개체는 각 설정을 속성으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="fe114-104">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="fe114-105">속성 이름은 설정 이름과 같고 속성 형식은 설정 형식과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fe114-105">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="fe114-106">설정의 **범위**는 속성이 읽기 전용인지 여부를 나타냅니다. **애플리케이션** 범위 설정의 속성은 읽기 전용이지만 **사용자** 범위 설정의 속성은 읽기-쓰기입니다.</span><span class="sxs-lookup"><span data-stu-id="fe114-106">The setting's **Scope** indicates if the property is read-only; the property for an **Application** scope setting is read-only, while the property for a **User** scope setting is read-write.</span></span> <span data-ttu-id="fe114-107">자세한 내용은 [My.Settings 개체](../../../language-reference/objects/my-settings-object.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fe114-107">For more information, see [My.Settings Object](../../../language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe114-108">예제</span><span class="sxs-lookup"><span data-stu-id="fe114-108">Example</span></span>  

 <span data-ttu-id="fe114-109">이 예제에서는 `Nickname` 설정의 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="fe114-109">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 <span data-ttu-id="fe114-110">이 예제가 작동하려면 애플리케이션에 `String` 형식의 `Nickname` 설정이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe114-110">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span> <span data-ttu-id="fe114-111">자세한 내용은 [애플리케이션 설정 관리(.NET)](/visualstudio/ide/managing-application-settings-dotnet)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fe114-111">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe114-112">참조</span><span class="sxs-lookup"><span data-stu-id="fe114-112">See also</span></span>

- [<span data-ttu-id="fe114-113">My.Settings 개체</span><span class="sxs-lookup"><span data-stu-id="fe114-113">My.Settings Object</span></span>](../../../language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="fe114-114">방법: Visual Basic에서 사용자 설정 변경</span><span class="sxs-lookup"><span data-stu-id="fe114-114">How to: Change User Settings in Visual Basic</span></span>](how-to-change-user-settings.md)
- [<span data-ttu-id="fe114-115">방법: Visual Basic에서 사용자 설정 유지</span><span class="sxs-lookup"><span data-stu-id="fe114-115">How to: Persist User Settings in Visual Basic</span></span>](how-to-persist-user-settings.md)
- [<span data-ttu-id="fe114-116">방법: Visual Basic에서 사용자 설정의 속성 표 만들기</span><span class="sxs-lookup"><span data-stu-id="fe114-116">How to: Create Property Grids for User Settings in Visual Basic</span></span>](how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="fe114-117">애플리케이션 설정 관리(.NET)</span><span class="sxs-lookup"><span data-stu-id="fe114-117">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
