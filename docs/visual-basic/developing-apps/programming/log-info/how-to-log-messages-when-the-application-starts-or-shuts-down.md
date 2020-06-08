---
title: '방법: 애플리케이션이 시작 또는 종료될 때 메시지 기록'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, shutdown
- My.Application.Log object, logging
- Startup event [Visual Basic]
- event logs, startup
- Shutdown event [Visual Basic]
- My.Log object, logging
ms.assetid: 67624d05-cddf-48b7-8c36-5c99baa4c621
ms.openlocfilehash: ac5fb17e527bcbcb55f98ec0ced06c152555ce6c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410077"
---
# <a name="how-to-log-messages-when-the-application-starts-or-shuts-down-visual-basic"></a><span data-ttu-id="8a1be-102">방법: 애플리케이션이 시작 또는 종료될 때 메시지 기록(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a1be-102">How to: Log Messages When the Application Starts or Shuts Down (Visual Basic)</span></span>

<span data-ttu-id="8a1be-103">`My.Application.Log` 및 `My.Log` 개체를 사용하여 애플리케이션에서 발생하는 이벤트에 대한 정보를 기록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a1be-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="8a1be-104">이 예제에서는 `My.Application.Log.WriteEntry` 및 `Startup` 이벤트에 `Shutdown` 메서드를 사용하여 추적 정보를 쓰는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8a1be-104">This example shows how to use the `My.Application.Log.WriteEntry` method with the `Startup` and `Shutdown` events to write tracing information.</span></span>  
  
### <a name="to-access-the-applications-event-handler-code"></a><span data-ttu-id="8a1be-105">애플리케이션의 이벤트 처리기 코드에 액세스하려면</span><span class="sxs-lookup"><span data-stu-id="8a1be-105">To access the application's event-handler code</span></span>  
  
1. <span data-ttu-id="8a1be-106">**솔루션 탐색기**에서 프로젝트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8a1be-106">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="8a1be-107">**프로젝트** 메뉴에서 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8a1be-107">On the **Project** menu, choose **Properties**.</span></span>  
  
2. <span data-ttu-id="8a1be-108">**애플리케이션** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8a1be-108">Click the **Application** tab.</span></span>  
  
3. <span data-ttu-id="8a1be-109">**애플리케이션 이벤트 보기** 단추를 클릭하여 코드 편집기를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8a1be-109">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="8a1be-110">그러면 ApplicationEvents.vb 파일이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="8a1be-110">This opens the ApplicationEvents.vb file.</span></span>  
  
### <a name="to-log-messages-when-the-application-starts"></a><span data-ttu-id="8a1be-111">애플리케이션이 시작될 때 메시지를 기록하려면</span><span class="sxs-lookup"><span data-stu-id="8a1be-111">To log messages when the application starts</span></span>  
  
1. <span data-ttu-id="8a1be-112">코드 편집기에서 ApplicationEvents.vb 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8a1be-112">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="8a1be-113">**일반** 메뉴에서 **MyApplication 이벤트**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8a1be-113">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2. <span data-ttu-id="8a1be-114">**선언** 메뉴에서 **Startup**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8a1be-114">On the **Declarations** menu, choose **Startup**.</span></span>  
  
     <span data-ttu-id="8a1be-115">주 애플리케이션이 실행되기 전에 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> 이벤트가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="8a1be-115">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> event before the main application runs.</span></span>  
  
3. <span data-ttu-id="8a1be-116">`My.Application.Log.WriteEntry` 이벤트 처리기에 `Startup` 메서드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8a1be-116">Add the `My.Application.Log.WriteEntry` method to the `Startup` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#1)]  
  
### <a name="to-log-messages-when-the-application-shuts-down"></a><span data-ttu-id="8a1be-117">애플리케이션이 종료될 때 메시지를 기록하려면</span><span class="sxs-lookup"><span data-stu-id="8a1be-117">To log messages when the application shuts down</span></span>  
  
1. <span data-ttu-id="8a1be-118">코드 편집기에서 ApplicationEvents.vb 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8a1be-118">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="8a1be-119">**일반** 메뉴에서 **MyApplication 이벤트**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8a1be-119">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2. <span data-ttu-id="8a1be-120">**선언** 메뉴에서 **Shutdown**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8a1be-120">On the **Declarations** menu, choose **Shutdown**.</span></span>  
  
     <span data-ttu-id="8a1be-121">주 애플리케이션이 실행된 후 종료되기 전에 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> 이벤트가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="8a1be-121">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> event after the main application runs, but before it shuts down.</span></span>  
  
3. <span data-ttu-id="8a1be-122">`My.Application.Log.WriteEntry` 이벤트 처리기에 `Shutdown` 메서드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8a1be-122">Add the `My.Application.Log.WriteEntry` method to the `Shutdown` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="8a1be-123">예제</span><span class="sxs-lookup"><span data-stu-id="8a1be-123">Example</span></span>  

 <span data-ttu-id="8a1be-124">**프로젝트 디자이너** 를 사용하여 코드 편집기에서 애플리케이션 이벤트에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a1be-124">You can use the **Project Designer** to access the application events in the Code Editor.</span></span> <span data-ttu-id="8a1be-125">자세한 내용은 [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8a1be-125">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
 [!code-vb[VbVbalrMyApplicationLog#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="8a1be-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8a1be-126">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="8a1be-127">프로젝트 디자이너, 애플리케이션 페이지(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a1be-127">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [<span data-ttu-id="8a1be-128">애플리케이션 로그 작업</span><span class="sxs-lookup"><span data-stu-id="8a1be-128">Working with Application Logs</span></span>](working-with-application-logs.md)
