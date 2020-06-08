---
title: '방법: 사용자 설정 변경'
ms.date: 07/20/2015
helpviewer_keywords:
- user settings [Visual Basic], changing in Visual Basic
- user settings
- My.Settings object [Visual Basic], changing user settings
- examples [Visual Basic], changing user settings
ms.assetid: 41250181-c594-4854-9988-8183b9eb03cf
ms.openlocfilehash: c9b89459f9b443c3a447edce90fee3437bbf1b6a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410181"
---
# <a name="how-to-change-user-settings-in-visual-basic"></a><span data-ttu-id="66a0b-102">방법: Visual Basic에서 사용자 설정 변경</span><span class="sxs-lookup"><span data-stu-id="66a0b-102">How to: Change User Settings in Visual Basic</span></span>

<span data-ttu-id="66a0b-103">설정의 `My.Settings` 개체에 대한 속성에 새 값을 할당하여 사용자 설정을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66a0b-103">You can change a user setting by assigning a new value to the setting's property on the `My.Settings` object.</span></span>  
  
 <span data-ttu-id="66a0b-104">`My.Settings` 개체는 각 설정을 속성으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="66a0b-104">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="66a0b-105">속성 이름은 설정 이름과 같고 속성 형식은 설정 형식과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="66a0b-105">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="66a0b-106">설정의 **범위**에서 속성이 읽기 전용 속성인지 여부를 확인합니다. **애플리케이션** 범위 설정의 속성은 읽기 전용이지만 **사용자** 범위 설정의 속성은 읽기-쓰기입니다.</span><span class="sxs-lookup"><span data-stu-id="66a0b-106">The setting's **Scope** determines if the property is read-only: The property for an **Application**-scope setting is read-only, while the property for a **User**-scope setting is read-write.</span></span> <span data-ttu-id="66a0b-107">자세한 내용은 [My.Settings 개체](../../../language-reference/objects/my-settings-object.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="66a0b-107">For more information, see [My.Settings Object](../../../language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="66a0b-108">런타임에 사용자 범위의 값을 변경하고 저장할 수 있지만 애플리케이션 범위 설정은 읽기 전용이고 프로그래밍 방식으로 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="66a0b-108">Although you can change and save the values of user-scope settings at run time, application-scope settings are read-only and cannot be changed programmatically.</span></span> <span data-ttu-id="66a0b-109">**프로젝트 디자이너**를 사용하거나 애플리케이션의 구성 파일을 편집하여 애플리케이션을 만들 때 애플리케이션 범위 설정을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66a0b-109">You can change application-scope settings when you create the application by using the **Project Designer** or by editing the application's configuration file.</span></span> <span data-ttu-id="66a0b-110">자세한 내용은 [애플리케이션 설정 관리(.NET)](/visualstudio/ide/managing-application-settings-dotnet)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="66a0b-110">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="66a0b-111">예제</span><span class="sxs-lookup"><span data-stu-id="66a0b-111">Example</span></span>  

 <span data-ttu-id="66a0b-112">이 예제에서는 `Nickname` 사용자 설정의 값을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="66a0b-112">This example changes the value of the `Nickname` user setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#7)]  
  
 <span data-ttu-id="66a0b-113">이 예제가 작동하려면 애플리케이션에 `String` 형식의 `Nickname` 사용자 설정이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="66a0b-113">For this example to work, your application must have a `Nickname` user setting, of type `String`.</span></span>  
  
 <span data-ttu-id="66a0b-114">애플리케이션이 종료될 때 사용자 설정이 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="66a0b-114">The application saves the user settings when the application shuts down.</span></span> <span data-ttu-id="66a0b-115">설정을 즉시 저장하려면 `My.Settings.Save` 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="66a0b-115">To save the settings immediately, call the `My.Settings.Save` method.</span></span> <span data-ttu-id="66a0b-116">자세한 내용은 [방법: Visual Basic에서 사용자 설정 유지](how-to-persist-user-settings.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="66a0b-116">For more information, see [How to: Persist User Settings in Visual Basic](how-to-persist-user-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66a0b-117">참조</span><span class="sxs-lookup"><span data-stu-id="66a0b-117">See also</span></span>

- [<span data-ttu-id="66a0b-118">My.Settings 개체</span><span class="sxs-lookup"><span data-stu-id="66a0b-118">My.Settings Object</span></span>](../../../language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="66a0b-119">방법: Visual Basic에서 애플리케이션 설정 읽기</span><span class="sxs-lookup"><span data-stu-id="66a0b-119">How to: Read Application Settings in Visual Basic</span></span>](how-to-read-application-settings.md)
- [<span data-ttu-id="66a0b-120">방법: Visual Basic에서 사용자 설정 유지</span><span class="sxs-lookup"><span data-stu-id="66a0b-120">How to: Persist User Settings in Visual Basic</span></span>](how-to-persist-user-settings.md)
- [<span data-ttu-id="66a0b-121">방법: Visual Basic에서 사용자 설정의 속성 표 만들기</span><span class="sxs-lookup"><span data-stu-id="66a0b-121">How to: Create Property Grids for User Settings in Visual Basic</span></span>](how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="66a0b-122">애플리케이션 설정 관리(.NET)</span><span class="sxs-lookup"><span data-stu-id="66a0b-122">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
