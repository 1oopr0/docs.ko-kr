---
title: Configuration Editor 도구(SvcConfigEditor.exe)
description: Wcf 서비스 구성 편집기를 사용 하 여 WCF 바인딩, 동작, 서비스 및 진단에 대 한 설정을 관리 하는 방법을 알아봅니다.
ms.date: 03/30/2017
helpviewer_keywords:
- configuration files, creating
- configuration files
- Configuration file
- configuration file schema
ms.assetid: 2db21a57-5f64-426f-89df-fb0dc2d2def5
ms.openlocfilehash: 258437ff616b969d40feabbfff364ad2cc6b25bc
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247651"
---
# <a name="configuration-editor-tool-svcconfigeditorexe"></a><span data-ttu-id="4567f-103">Configuration Editor 도구(SvcConfigEditor.exe)</span><span class="sxs-lookup"><span data-stu-id="4567f-103">Configuration Editor Tool (SvcConfigEditor.exe)</span></span>

<span data-ttu-id="4567f-104">WCF(Windows Communication Foundation) 서비스 구성 편집기(SvcConfigEditor.exe)를 사용하면 관리자와 개발자가 그래픽 사용자 인터페이스를 사용하여 WCF 서비스에 대한 구성 설정을 만들고 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-104">The Windows Communication Foundation (WCF) Service Configuration Editor (SvcConfigEditor.exe) allows administrators and developers to create and modify configuration settings for WCF services using a graphical user interface.</span></span> <span data-ttu-id="4567f-105">이 도구를 사용하면 XML 구성 파일을 직접 편집하지 않고도 WCF 바인딩, 동작, 서비스 및 진단에 대한 설정을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-105">With this tool, you can manage settings for WCF bindings, behaviors, services, and diagnostics without having to directly edit XML configuration files.</span></span>

<span data-ttu-id="4567f-106">서비스 구성 편집기는 C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin 폴더에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-106">Service Configuration Editor can be found in the C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin folder.</span></span>

## <a name="the-wcf-configuration-editor"></a><span data-ttu-id="4567f-107">WCF Configuration Editor</span><span class="sxs-lookup"><span data-stu-id="4567f-107">The WCF Configuration Editor</span></span>

<span data-ttu-id="4567f-108">서비스 구성 편집기는 WCF 서비스 또는 클라이언트를 구성하는 모든 단계를 안내하는 마법사와 함께 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-108">Service Configuration Editor comes with a wizard that guides you through all the steps in configuring a WCF service or client.</span></span> <span data-ttu-id="4567f-109">편집기를 직접 사용하는 대신 마법사를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-109">You are strongly advised to use the wizard instead of the editor directly.</span></span>

<span data-ttu-id="4567f-110">표준 System.Configuration 스키마를 따르는 일부 구성 파일이 이미 있으면 사용자 인터페이스로 바인딩, 동작, 서비스 및 진단에 대한 특정 설정을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-110">If you already have some configuration files that comply with the standard System.Configuration schema, you can manage specific settings for bindings, behavior, services, and diagnostics with the user interface.</span></span> <span data-ttu-id="4567f-111">서비스 구성 편집기를 사용하면 실행 파일, COM+ 서비스 및 웹 호스팅 서비스뿐 아니라 기존 WCF 구성 파일에 대한 설정을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-111">The Service Configuration Editor enables you to manage the settings for existing WCF configuration files as well as executable files, COM+ services, and Web-hosted services.</span></span> <span data-ttu-id="4567f-112">서비스 구성 편집기를 사용하여 웹 호스팅 서비스를 열면 서비스의 자체 구성과 상위 수준 노드의 상속된 구성 섹션이 모두 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-112">When opening a Web-hosted service with Service Configuration Editor, both the service’s own configuration and inherited configurations sections of upper level nodes are shown.</span></span>

<span data-ttu-id="4567f-113">WCF 구성 설정이 구성 파일의 `<system.serviceModel>` 섹션에 있으므로 편집기는 이 요소의 내용에 대해서만 작동하고 같은 파일의 다른 요소에 액세스하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-113">Because WCF configuration settings are located in the `<system.serviceModel>` section of the configuration file, the editor operates exclusively on the content of this element and does not access other elements in the same file.</span></span> <span data-ttu-id="4567f-114">기존 구성 파일을 직접 찾거나 서비스, 가상 디렉터리 또는 COM+ 서비스가 포함된 어셈블리를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-114">You can navigate to existing configuration files directly or you can select an assembly that contains a service, virtual directory, or COM+ service.</span></span> <span data-ttu-id="4567f-115">편집기는 특정 서비스의 구성 파일을 로드하여 구성 파일의 `<system.serviceModel>` 섹션에 중첩된 기존 요소를 편집하거나 새 요소를 추가할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-115">The editor loads the configuration file for that particular service and allows the user to either add new elements or edit existing elements nested in the `<system.serviceModel>` section of the configuration file.</span></span>

<span data-ttu-id="4567f-116">편집기는 IntelliSense를 지원하며 스키마를 준수하도록 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-116">The editor supports IntelliSense and enforces schema compliance.</span></span> <span data-ttu-id="4567f-117">결과 출력은 구성 파일의 스키마를 준수하고 올바른 구문의 데이터 값을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-117">The resulting output is guaranteed to comply with the schema of the configuration file and to have syntactically correct data values.</span></span> <span data-ttu-id="4567f-118">그러나 편집기를 사용해도 구성 파일의 의미가 유효하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-118">However, the editor does not guarantee that the configuration file is semantically valid.</span></span> <span data-ttu-id="4567f-119">즉, 편집기를 사용해도 구성 파일이 해당 구성 파일을 구성하는 서비스에서 작동하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-119">In other words, the editor does not guarantee that the configuration file can work with the service it configures.</span></span>

> [!CAUTION]
> <span data-ttu-id="4567f-120">요소를 수정하면 편집기에서는 구성 파일의 구성 요소를 제거할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-120">The editor cannot purge a configuration element from the configuration file once you have modified the element.</span></span> <span data-ttu-id="4567f-121">예를 들어,편집기를 사용하여 엔드포인트 이름을 비어 있지 않은 문자열로 설정한 후 저장하면 다음 예제와 같이 구성 파일에 다음 내용이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-121">For example, if you use the editor to set the endpoint name to a non-empty string and save it, the configuration file has the following content, as shown in the following example.</span></span>
>
> `<endpoint binding="basicHttpBinding" name="somename" />`
>
> <span data-ttu-id="4567f-122">이름을 빈 문자열로 설정하여 해당 이름을 제거한 후 파일을 저장해도 다음 예제와 같이 구성 파일에 `name` 특성이 여전히 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-122">If you attempt to remove the name by setting it to an empty string and save the file, the configuration file still contains the `name` attribute, as shown in the following example.</span></span>
>
> `<endpoint binding="basicHttpBinding" name="" />`
>
> <span data-ttu-id="4567f-123">이 특성을 제거하려면 다른 텍스트 편집기를 사용하여 요소를 수동으로 편집해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-123">To purge the attribute, you must manually edit the element using another text editor.</span></span>
>
> <span data-ttu-id="4567f-124">ph x="1" /&gt; 엔드포인트 동작의 `clientCredential` 요소를 사용하는 경우 이 문제에 특히 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-124">You should be especially careful with this issue when you use the `issueToken` element of the `clientCredential` Endpoint behavior.</span></span> <span data-ttu-id="4567f-125">특히 `address` 하위 요소의 `localIssuer` 특성은 빈 문자열이 아니어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-125">Specifically, the `address` attribute of its `localIssuer` sub-element must not be an empty string.</span></span> <span data-ttu-id="4567f-126">구성 편집기를 사용하여 `address` 특성을 수정한 경우 해당 특성을 완전히 제거하려면 이 편집기 이외의 도구를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-126">If you have modified the `address` attribute using the Configuration Editor and want to remove it completely, you should do so using a tool other than the Editor.</span></span> <span data-ttu-id="4567f-127">이렇게 하지 않으면 특성에 빈 문자열이 포함되어 애플리케이션에서 예외가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-127">Otherwise, the attribute contains an empty string and your application throws an exception.</span></span>

## <a name="using-the-configuration-editor"></a><span data-ttu-id="4567f-128">Configuration Editor 사용</span><span class="sxs-lookup"><span data-stu-id="4567f-128">Using the Configuration Editor</span></span>

<span data-ttu-id="4567f-129">서비스 구성 편집기는 다음 Windows SDK 설치 위치에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-129">The Service Configuration Editor can be found at the following Windows SDK installation location:</span></span>

<span data-ttu-id="4567f-130">C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin\SvcConfigEditor.exe</span><span class="sxs-lookup"><span data-stu-id="4567f-130">C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin\SvcConfigEditor.exe</span></span>

<span data-ttu-id="4567f-131">서비스 구성 편집기를 시작한 후에는 **파일/열기** 메뉴를 사용 하 여 관리 하려는 서비스 또는 어셈블리를 찾아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-131">After you launch the Service Configuration Editor, you can use the **File/Open** menu to browse for the service or assembly you want to manage.</span></span> <span data-ttu-id="4567f-132">구성 파일을 직접 열고 WCF /COM+ 서비스를 찾아 웹 호스팅 서비스의 구성 파일을 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-132">You can open configuration files directly, browse for WCF /COM+ services, and open configuration files for Web-hosted services.</span></span>

<span data-ttu-id="4567f-133">Service Configuration Editor 사용자 인터페이스는 다음 영역으로 나뉩니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-133">The Service Configuration Editor's user interface is divided into the following areas:</span></span>

- <span data-ttu-id="4567f-134">왼쪽에 있는 트리 구조의 구성 요소를 표시하는 트리 뷰 창.</span><span class="sxs-lookup"><span data-stu-id="4567f-134">Tree View Pane, which displays configuration elements in a tree structure on the left.</span></span> <span data-ttu-id="4567f-135">노드를 오른쪽 단추로 클릭하여 트리에서 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-135">You can perform operations in the tree by right-clicking the nodes.</span></span>

- <span data-ttu-id="4567f-136">창의 왼쪽 아래에 있는 현재 요소에 대한 일반 작업을 표시하는 작업 창</span><span class="sxs-lookup"><span data-stu-id="4567f-136">Task Pane, which displays common tasks for current elements on the lower-left of the window</span></span>

- <span data-ttu-id="4567f-137">오른쪽에 있는 트리 뷰에서 선택된 구성 노드의 세부적인 설정을 표시하는 세부 정보 창</span><span class="sxs-lookup"><span data-stu-id="4567f-137">Detail Pane, which displays detailed settings of the configuration node selected in the Tree View on the right.</span></span>

### <a name="opening-a-configuration-file"></a><span data-ttu-id="4567f-138">구성 파일 열기</span><span class="sxs-lookup"><span data-stu-id="4567f-138">Opening a Configuration File</span></span>

1. <span data-ttu-id="4567f-139">명령 창을 사용 하 여 서비스 구성 편집기를 시작 하 여 WCF 설치 위치로 이동한 다음를 입력 `SvcConfigEditor.exe` 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-139">Start Service Configuration Editor by using a command window to navigate to your WCF installation location, and then type `SvcConfigEditor.exe`.</span></span>

2. <span data-ttu-id="4567f-140">**파일** 메뉴에서 **열기** 를 선택 하 고 관리 하려는 파일의 유형을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-140">From the **File** menu, select **Open** and click the type of file you want to manage.</span></span>

3. <span data-ttu-id="4567f-141">**열기** 대화 상자에서 관리 하려는 특정 파일로 이동 하 고 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-141">In the **Open** dialog box, navigate to the specific file you want to manage and double-click it.</span></span>

<span data-ttu-id="4567f-142">뷰어는 구성 병합 경로를 자동으로 따르며 병합된 구성의 뷰를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-142">The viewer automatically follows the configuration merge path and creates a view of the merged configuration.</span></span> <span data-ttu-id="4567f-143">예를 들어, 호스팅되지 않은 서비스의 실제 구성은 Machine.config와 App.config의 조합입니다. 모든 변경 내용은 SvcConfigEditor의 활성 파일에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-143">For example, the actual configuration of a non-hosted service is a combination of Machine.config and App.config. Any changes are applied to the active file in the SvcConfigEditor.</span></span> <span data-ttu-id="4567f-144">구성 병합 경로에서 특정 파일을 편집하려면 해당 파일을 직접 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-144">If you want to edit a specific file in the configuration merge path, you should open it directly.</span></span>

> [!NOTE]
> <span data-ttu-id="4567f-145">편집기 외부에서 해당 특정 파일을 수정한 경우 Configuration Editor는 현재 열린 구성 파일을 다시 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-145">Configuration Editor reloads the currently opened configuration file when the latter has been modified outside the Editor.</span></span> <span data-ttu-id="4567f-146">이 경우 편집기 내부에 영구적으로 저장되지 않은 모든 변경 내용이 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-146">When this happens, all the changes that are not durably saved inside the Editor are lost.</span></span> <span data-ttu-id="4567f-147">다시 로드가 계속해서 발생하는 가장 일반적인 원인은 백그라운드에서 실행하는 바이러스 백신 소프트웨어와 같이 구성 파일에 반복해서 액세스하는 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-147">If reloading happens consistently, the most likely cause is a service that constantly accesses the configuration file, for example, an antivirus software running in the background.</span></span> <span data-ttu-id="4567f-148">이 문제를 해결하려면 파일을 열 때 해당 파일에 액세스할 수 있는 유일한 프로세스가 Configuration Editor인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-148">To resolve this, ensure that Configuration Editor is the only process that can access the file when it is opened.</span></span>

### <a name="services"></a><span data-ttu-id="4567f-149">서비스</span><span class="sxs-lookup"><span data-stu-id="4567f-149">Services</span></span>

<span data-ttu-id="4567f-150">**서비스** 노드는 구성 파일에 현재 할당 된 모든 서비스를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-150">The **Services** node displays all of the services currently assigned in the configuration file.</span></span> <span data-ttu-id="4567f-151">트리의 각 하위 노드는 `services` 구성 파일에 있는 <> 요소의 하위 요소에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-151">Each sub-node in the tree corresponds to a sub-element of the <`services`> element in the configuration file.</span></span>

<span data-ttu-id="4567f-152">**서비스** 노드를 클릭 하면 **세부 정보** 창의 서비스 요약 페이지에서 작업을 보거나 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-152">When you click the **Services** node, you can view or perform tasks on the service Summary Page in the **Detail** Pane.</span></span>

#### <a name="creating-a-new-service-configuration"></a><span data-ttu-id="4567f-153">새 서비스 구성 만들기</span><span class="sxs-lookup"><span data-stu-id="4567f-153">Creating a new Service Configuration</span></span>

<span data-ttu-id="4567f-154">다음 방법으로 새 서비스 구성을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-154">You can create a new service configuration in the following ways:</span></span>

- <span data-ttu-id="4567f-155">마법사 사용: **새 서비스 만들기** 링크를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-155">Using a Wizard: Click the link **Create a New Service…**</span></span> <span data-ttu-id="4567f-156">작업 창 또는 요약 페이지에서 마법사를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-156">on the Task Pane or Summary Page to launch the wizard.</span></span> <span data-ttu-id="4567f-157">**파일** 메뉴에서 **새 항목 추가**> 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-157">You can also do so in the **File** menu -> **Add New Item**.</span></span>

- <span data-ttu-id="4567f-158">수동으로 만들기: **서비스** 노드를 마우스 오른쪽 단추로 클릭 하 고 **새 서비스**를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-158">Create manually: You can right-click the **Services** node and choose **New Service**.</span></span>

#### <a name="creating-a-new-service-endpoint-configuration"></a><span data-ttu-id="4567f-159">새 서비스 엔드포인트 구성 만들기</span><span class="sxs-lookup"><span data-stu-id="4567f-159">Creating a new Service Endpoint Configuration</span></span>

<span data-ttu-id="4567f-160">다음 방법으로 새 서비스 엔드포인트 구성을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-160">You can create a new service endpoint configuration in the following ways:</span></span>

- <span data-ttu-id="4567f-161">마법사를 사용 하 여 만들기: **새 서비스 끝점 만들기** 링크를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-161">Create using a Wizard: click the link **Create a New Service Endpoint…**</span></span> <span data-ttu-id="4567f-162">작업 창 또는 요약 페이지에서 마법사를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-162">on the Task Pane or Summary Page to launch the wizard.</span></span> <span data-ttu-id="4567f-163">**파일** 메뉴에서 **새 항목 추가**> 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-163">You can also do so in the **File** menu -> **Add New Item**.</span></span>

- <span data-ttu-id="4567f-164">수동으로 만들기: 서비스를 만든 후에는 **끝점** 노드를 마우스 오른쪽 단추로 클릭 하 고 "**새 서비스 엔드포인트**"를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-164">Create manually: Once you created a Service, you can right-click the **Endpoints** node and choose "**New Service Endpoint**".</span></span>

#### <a name="editing-a-service-configuration"></a><span data-ttu-id="4567f-165">서비스 구성 편집</span><span class="sxs-lookup"><span data-stu-id="4567f-165">Editing a Service Configuration</span></span>

1. <span data-ttu-id="4567f-166">**서비스** 노드를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-166">Click a **Service** node.</span></span>

2. <span data-ttu-id="4567f-167">속성 표에서 설정을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-167">Edit the settings in the property grids.</span></span>

#### <a name="editing-a-service-endpoint-configuration"></a><span data-ttu-id="4567f-168">서비스 엔드포인트 구성 편집</span><span class="sxs-lookup"><span data-stu-id="4567f-168">Editing a Service Endpoint Configuration</span></span>

1. <span data-ttu-id="4567f-169">**서비스 끝점** 노드를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-169">Click a **Service Endpoint** node.</span></span>

2. <span data-ttu-id="4567f-170">속성 표에서 설정을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-170">Edit the settings in the property grids.</span></span>

#### <a name="adding-a-base-address"></a><span data-ttu-id="4567f-171">기본 주소 추가</span><span class="sxs-lookup"><span data-stu-id="4567f-171">Adding a Base Address</span></span>

1. <span data-ttu-id="4567f-172">**호스트** 노드를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-172">Click the **Host** node.</span></span>

2. <span data-ttu-id="4567f-173">**새로 만들기...** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-173">Click the **New…**</span></span> <span data-ttu-id="4567f-174">단추 **를 클릭** 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-174">button in the **Base Addresses** section.</span></span>

3. <span data-ttu-id="4567f-175">대화 상자에 기본 주소 URI를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-175">Type in the base address URI in the dialog box.</span></span>

4. <span data-ttu-id="4567f-176">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-176">Click **OK**.</span></span>

> [!NOTE]
> <span data-ttu-id="4567f-177">이 도구 내에서는의 값을 편집할 수 없습니다 [\<baseAddressPrefixFilters>](../configure-apps/file-schema/wcf/baseaddressprefixfilters.md) .</span><span class="sxs-lookup"><span data-stu-id="4567f-177">You cannot edit the value of [\<baseAddressPrefixFilters>](../configure-apps/file-schema/wcf/baseaddressprefixfilters.md) inside this tool.</span></span> <span data-ttu-id="4567f-178">이 요소를 추가하거나 수정하려면 텍스트 편집기 또는 Visual Studio를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-178">To add or modify this element, you should use a text editor or Visual Studio.</span></span>

### <a name="client"></a><span data-ttu-id="4567f-179">Client</span><span class="sxs-lookup"><span data-stu-id="4567f-179">Client</span></span>

<span data-ttu-id="4567f-180">**클라이언트** 노드는 구성 파일에 있는 모든 클라이언트 끝점을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-180">The **Client** node displays all of the client endpoints in the configuration file.</span></span> <span data-ttu-id="4567f-181">트리의 모든 하위 노드는 `client` 구성 파일에 있는 <> 요소의 하위 요소에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-181">Every sub-node in the tree corresponds to a sub-element of the <`client`> element in the configuration file.</span></span>

<span data-ttu-id="4567f-182">**클라이언트** 노드를 클릭 하면 **세부 정보 창의**클라이언트 **요약 페이지** 에서 작업을 보거나 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-182">When you click the **Client** node, you can view or perform tasks on the client **Summary Page** in the **Detail Pane**.</span></span>

#### <a name="creating-a-new-client-endpoint-configuration"></a><span data-ttu-id="4567f-183">새 클라이언트 엔드포인트 구성 만들기</span><span class="sxs-lookup"><span data-stu-id="4567f-183">Creating a new Client Endpoint Configuration</span></span>

<span data-ttu-id="4567f-184">다음 방법으로 새 클라이언트 엔드포인트 구성을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-184">You can create a new client endpoint configuration in the following ways:</span></span>

- <span data-ttu-id="4567f-185">마법사로 만들기: **새 클라이언트 만들기** 링크를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-185">Create by Wizard: Click the link **Create a New Client…**</span></span> <span data-ttu-id="4567f-186">창의 왼쪽 아래에 있는 **작업 창** 또는 **요약 페이지** 에서 마법사를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-186">on the **Task Pane** on the lower-left of the window, or **Summary Page** to launch the wizard.</span></span> <span data-ttu-id="4567f-187">**파일** 메뉴에서 **새 항목 추가**> 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-187">You can also do so in the **File** menu -> **Add New Item**.</span></span> <span data-ttu-id="4567f-188">마법사에서 클라이언트 구성이 생성되는 서비스 구성의 위치를 지정하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-188">The wizard prompts you to point to the location of the service configuration, from which the client configuration is generated.</span></span> <span data-ttu-id="4567f-189">그러면 연결할 서비스 엔드포인트를 선택하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-189">You can then choose the service endpoint to connect to.</span></span>

- <span data-ttu-id="4567f-190">수동으로 만들기: **클라이언트**아래의 **끝점** 노드를 마우스 오른쪽 단추로 클릭 하 고 **새 클라이언트 끝점**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-190">Create manually: Right-click the **Endpoints** node under **Client**, and choose **New Client Endpoint**.</span></span>

#### <a name="editing-a-client-endpoint-configuration"></a><span data-ttu-id="4567f-191">클라이언트 엔드포인트 구성 편집</span><span class="sxs-lookup"><span data-stu-id="4567f-191">Editing a Client Endpoint Configuration</span></span>

1. <span data-ttu-id="4567f-192">**클라이언트 끝점** 노드를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-192">Click a **Client Endpoint** node.</span></span>

2. <span data-ttu-id="4567f-193">속성 표에서 설정을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-193">Edit the settings in the property grids.</span></span>

### <a name="standard-endpoint"></a><span data-ttu-id="4567f-194">표준 엔드포인트</span><span class="sxs-lookup"><span data-stu-id="4567f-194">Standard Endpoint</span></span>

<span data-ttu-id="4567f-195">표준 엔드포인트는 주소, 계약 및 바인딩의 측면 하나 이상이 기본값으로 설정된 특수 엔드포인트입니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-195">Standard endpoints are specialized endpoints that have one or more aspects of the address, contract and binding set to default values.</span></span>

<span data-ttu-id="4567f-196">이러한 구성 설정은 **표준 끝점** 노드에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-196">Such configuration settings are stored in the **Standard Endpoint** node.</span></span> <span data-ttu-id="4567f-197">**표준 끝점** 노드는 구성 파일의 모든 표준 끝점 설정을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-197">The **Standard Endpoint** node displays all of the standard endpoint settings in the configuration file.</span></span> <span data-ttu-id="4567f-198">트리의 모든 하위 노드는 구성 파일의 요소에 있는 하위 요소에 해당 `<standardEndpoints>` 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-198">Every sub-node in the tree corresponds to a sub-element in the `<standardEndpoints>` element in the configuration file.</span></span>

<span data-ttu-id="4567f-199">**표준 끝점** 노드를 클릭 하면 **세부 정보 창의**표준 끝점 **요약 페이지** 에서 작업을 보거나 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-199">When you click the **Standard Endpoint** node, you can view or perform tasks on the standard endpoint **Summary Page** in the **Detail Pane**.</span></span>

#### <a name="creating-a-new-standard-endpoint-configuration"></a><span data-ttu-id="4567f-200">새 표준 엔드포인트 구성 만들기</span><span class="sxs-lookup"><span data-stu-id="4567f-200">Creating a New Standard Endpoint Configuration</span></span>

<span data-ttu-id="4567f-201">다음 방법으로 새 표준 엔드포인트 구성을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-201">You can create a new standard endpoint configuration in the following ways:</span></span>

- <span data-ttu-id="4567f-202">**표준 끝점** 노드를 마우스 오른쪽 단추로 클릭 하 고 **새 표준 끝점 구성** ...을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-202">Right-click the **Standard Endpoint** node and select **New Standard Endpoint Configuration…**</span></span> <span data-ttu-id="4567f-203">대화 상자에서 바인딩 유형을 선택 하 고 **확인을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-203">Select the binding type in the dialog box and click **OK**.</span></span>

- <span data-ttu-id="4567f-204">**표준 끝점** 노드를 선택 하 고 **새 표준 끝점 구성** ...을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-204">Select the **Standard Endpoint** node and click **New Standard Endpoint Configuration…**</span></span> <span data-ttu-id="4567f-205">창의 왼쪽 아래에 있는 **작업 창** 에서</span><span class="sxs-lookup"><span data-stu-id="4567f-205">in the **Task Pane** on the lower-left of the window.</span></span>

<span data-ttu-id="4567f-206">**새 표준 끝점 만들기** 대화 상자에 등록 된 모든 표준 끝점 형식이 표시 되 고 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-206">The **Creating a New Standard Endpoint** dialog box displays and lists all registered standard endpoint types.</span></span>

#### <a name="viewing-and-editing-a-standard-endpoint-configuration"></a><span data-ttu-id="4567f-207">표준 엔드포인트 구성 보기 및 편집</span><span class="sxs-lookup"><span data-stu-id="4567f-207">Viewing and Editing a Standard Endpoint Configuration</span></span>

<span data-ttu-id="4567f-208">다음 방법으로 표준 엔드포인트 구성을 열어서 보거나 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-208">You can open a standard endpoint configuration for viewing and editing in the following ways:</span></span>

- <span data-ttu-id="4567f-209">**표준 끝점** 노드를 클릭 하 여 확장 하 고 해당 끝점 하위 노드를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-209">Click to expand the **Standard Endpoint** node and click the respective endpoint sub-node.</span></span>

- <span data-ttu-id="4567f-210">**표준 끝점** 노드를 클릭 하 고 세부 정보 창에서 해당 끝점을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-210">Click the **Standard Endpoint** node and click the respective endpoint on the Detail pane.</span></span>

<span data-ttu-id="4567f-211">엔드포인트의 특성이 편집할 수 있도록 오른쪽 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-211">Attributes for the endpoint are shown in the right pane for editing.</span></span>

#### <a name="deleting-a-standard-endpoint-configuration"></a><span data-ttu-id="4567f-212">표준 엔드포인트 구성 삭제</span><span class="sxs-lookup"><span data-stu-id="4567f-212">Deleting a Standard Endpoint Configuration</span></span>

<span data-ttu-id="4567f-213">다음 방법으로 표준 엔드포인트 구성을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-213">You can delete a standard endpoint configuration in the following ways:</span></span>

- <span data-ttu-id="4567f-214">**표준 끝점** 노드를 클릭 하 여 확장 하 고 해당 끝점 하위 노드를 마우스 오른쪽 단추로 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-214">Click to expand the **Standard Endpoint** node and right-click the respective endpoint sub-node.</span></span> <span data-ttu-id="4567f-215">컨텍스트 명령 **표준 끝점 구성 삭제** 를 사용 하 여 끝점을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-215">Use the context command **Delete Standard Endpoint Configuration** to delete the endpoint.</span></span>

- <span data-ttu-id="4567f-216">**표준 끝점** 노드를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-216">Click the **Standard Endpoint** node.</span></span> <span data-ttu-id="4567f-217">**작업** 창에서 **표준 끝점 구성 삭제**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-217">In the **Task** pane, click **Delete Standard Endpoint Configuration**.</span></span>

<span data-ttu-id="4567f-218">표준 끝점이 사용 중인 경우 표준 끝점을 삭제 하려고 하면 경고 메시지가 표시 됩니다. **표준 끝점이 사용 중입니다. 지금 삭제 하는 경우 구성의 다른 부분 (예: 서비스 끝점 또는 클라이언트 끝점)에서 해당 참조를 모두 삭제 해야 합니다. 그렇지 않으면 구성이 잘못 되어 다음 번에 열 수 없습니다. 표준 끝점을 삭제 하 시겠습니까? "**</span><span class="sxs-lookup"><span data-stu-id="4567f-218">If the standard endpoint is in used, a warning message is displayed when you attempt to delete it: **The standard endpoint is in use. If you delete it now, please be sure to delete all of its references in other parts of the configuration (for example, in the service endpoint or client endpoint). Otherwise, the configuration will be invalid and cannot be opened next time. Are you sure you want to delete the standard endpoint?"**</span></span>

### <a name="binding"></a><span data-ttu-id="4567f-219">바인딩</span><span class="sxs-lookup"><span data-stu-id="4567f-219">Binding</span></span>

<span data-ttu-id="4567f-220">바인딩 구성은 엔드포인트에서 바인딩을 구성하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-220">Binding configurations are used to configure bindings on endpoints.</span></span> <span data-ttu-id="4567f-221">이러한 구성 설정은 **바인딩** 노드에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-221">Such configuration settings are stored in the **Binding** node.</span></span> <span data-ttu-id="4567f-222">엔드포인트는 이름별로 바인딩 구성을 참조하며 여러 엔드포인트가 단일 바인딩 구성을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-222">Endpoints reference binding configurations by name and multiple endpoints can reference a single binding configuration.</span></span>

<span data-ttu-id="4567f-223">바인딩 **노드는** 구성 파일의 모든 바인딩 설정을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-223">The **Bindings** node displays all of the binding settings in the configuration file.</span></span> <span data-ttu-id="4567f-224">트리의 모든 하위 노드는 구성 파일의 <> 요소에 있는 하위 요소에 해당 `bindings` 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-224">Every sub-node in the tree corresponds to a sub-element in the <`bindings`> element in the configuration file.</span></span>

<span data-ttu-id="4567f-225">**바인딩 노드를** 클릭 하면 **세부 정보 창의**바인딩 **요약 페이지** 에서 작업을 보거나 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-225">When you click the **Bindings** node, you can view or perform tasks on the binding **Summary Page** in the **Detail Pane**.</span></span>

#### <a name="creating-a-new-binding-configuration"></a><span data-ttu-id="4567f-226">새 바인딩 구성 만들기</span><span class="sxs-lookup"><span data-stu-id="4567f-226">Creating a New Binding Configuration</span></span>

<span data-ttu-id="4567f-227">다음 방법으로 새 바인딩 구성을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-227">You can create a new binding configuration in the following ways.</span></span>

- <span data-ttu-id="4567f-228">**바인딩** 노드를 마우스 오른쪽 단추로 클릭 하 고 **새 바인딩 구성**...을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-228">Right-click the **Bindings** node and select **New Binding Configuration**…</span></span> <span data-ttu-id="4567f-229">대화 상자에서 바인딩 유형을 선택 하 고 **확인을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-229">Select the binding type in the dialog box and click **OK**.</span></span>

- <span data-ttu-id="4567f-230">**바인딩** 노드를 선택 하 고 **새 바인딩 구성**...을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-230">Select the **Bindings** node and click **New Binding Configuration**…</span></span> <span data-ttu-id="4567f-231">창의 왼쪽 아래에 있는 **작업 창** 에서</span><span class="sxs-lookup"><span data-stu-id="4567f-231">in the **Task Pane** on the lower-left of the window.</span></span>

- <span data-ttu-id="4567f-232">서비스 또는 클라이언트 요약 페이지에서 **바인딩 구성** 필드에 **만들기를 클릭 하** 여 해당 끝점에 대 한 바인딩 구성을 만듭니다 .를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-232">In the service or client summary page, click **Click to Create** in the **Binding Configuration** field to create a binding configuration for the corresponding endpoint.</span></span>

#### <a name="adding-binding-element-extensions-to-a-custom-binding"></a><span data-ttu-id="4567f-233">바인딩 요소 확장을 사용자 지정 바인딩에 추가</span><span class="sxs-lookup"><span data-stu-id="4567f-233">Adding Binding Element Extensions to a Custom Binding</span></span>

1. <span data-ttu-id="4567f-234">확장 요소를 추가할 바인딩을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-234">Select the binding you want to add an extension element to.</span></span>

2. <span data-ttu-id="4567f-235">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-235">Click **Add**.</span></span>

3. <span data-ttu-id="4567f-236">사용 가능한 확장 목록에서 추가하려는 바인딩 요소 확장을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-236">From the list of available extensions, select the binding element extension you want to add.</span></span> <span data-ttu-id="4567f-237">여러 항목을 선택하려면 Ctrl 키를 누른 상태로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-237">To select multiple items, press the CTRL key simultaneously.</span></span>

4. <span data-ttu-id="4567f-238">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-238">Click **Add**.</span></span>

#### <a name="adjusting-the-extension-position-in-a-custom-binding"></a><span data-ttu-id="4567f-239">사용자 지정 바인딩에서 확장명 위치 조정</span><span class="sxs-lookup"><span data-stu-id="4567f-239">Adjusting the Extension Position in a Custom Binding</span></span>

<span data-ttu-id="4567f-240">사용자 지정 바인딩은 스택을 형성하는 바인딩 요소의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-240">A custom binding is a collection of binding elements that form a stack.</span></span> <span data-ttu-id="4567f-241">스택의 바인딩 요소는 각각 자체 구성 설정을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-241">Each binding element on the stack has its own configuration settings.</span></span> <span data-ttu-id="4567f-242">사용자 지정 바인딩의 바인딩 요소 확장 순서는 스택의 해당 위치를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-242">The order of the binding element extensions in a custom binding indicates their positions in the stack.</span></span> <span data-ttu-id="4567f-243">스택의 맨 위에 있는 요소가 처음으로 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-243">Elements at the top of the stack are applied first.</span></span> <span data-ttu-id="4567f-244">순서를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="4567f-244">To change the ordering:</span></span>

1. <span data-ttu-id="4567f-245">사용자 지정 바인딩 노드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-245">Select the custom binding node.</span></span>

2. <span data-ttu-id="4567f-246">**바인딩 요소 확장 위치** 섹션에서 바인딩 확장 요소 하나를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-246">Select one binding extension element in the **Binding Element Extension Position** section.</span></span>

3. <span data-ttu-id="4567f-247">목록의 왼쪽에 있는 **위로** 또는 **아래로** 단추를 사용 하 여 선택한 요소의 위치를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-247">Use the **Up** or **Down** button on the left side of the list to change the position of the selected element.</span></span>

#### <a name="editing-the-configuration-of-binding-element-extensions-in-a-custom-binding"></a><span data-ttu-id="4567f-248">사용자 지정 바인딩에서 바인딩 요소 확장의 구성 편집</span><span class="sxs-lookup"><span data-stu-id="4567f-248">Editing the Configuration of Binding Element Extensions in a Custom Binding</span></span>

1. <span data-ttu-id="4567f-249">트리에서 바인딩 노드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-249">Select the binding node in the tree.</span></span>

2. <span data-ttu-id="4567f-250">편집하려는 요소가 포함된 사용자 지정 바인딩을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-250">Select the custom binding that contains the element you want to edit.</span></span>

3. <span data-ttu-id="4567f-251">편집하려는 바인딩 요소 확장을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-251">Select the binding element extension you want to edit.</span></span> <span data-ttu-id="4567f-252">요소의 설정이 편집 가능한 오른쪽 창에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-252">The settings of the element appear in the right pane, where they can be edited.</span></span>

### <a name="diagnostics"></a><span data-ttu-id="4567f-253">진단</span><span class="sxs-lookup"><span data-stu-id="4567f-253">Diagnostics</span></span>

<span data-ttu-id="4567f-254">**진단** 노드는 구성 파일의 모든 진단 설정을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-254">The **Diagnostics** node displays all of the diagnostic settings in the configuration file.</span></span> <span data-ttu-id="4567f-255">이를 통해 성능 카운터를 설정 또는 해제 하 고, WMI (WMI(Windows Management Instrumentation))를 사용 하거나 사용 하지 않도록 설정 하 고, WCF 추적을 구성 하 고, WCF 메시지 로깅을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-255">It enables you to turn performance counters on or off, enable or disable Windows Management Instrumentation (WMI), configure WCF tracing, and configure WCF message logging.</span></span> <span data-ttu-id="4567f-256">**진단** 노드의 설정은 `system.diagnostics` `<diagnostics>` `<system.serviceModel>` 구성 파일의에 있는 <> 섹션 및 섹션에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-256">The settings in the **Diagnostics** node correspond to the <`system.diagnostics`> section, and `<diagnostics>` section in `<system.serviceModel>` in the configuration file.</span></span>

<span data-ttu-id="4567f-257">**진단** 노드를 클릭 하면 **세부 정보 창의**진단 **요약 페이지** 에서 작업을 보거나 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-257">When you click the **Diagnostics** node, you can view or perform tasks on the diagnostics **Summary Page** in the **Detail Pane**.</span></span>

#### <a name="configuring-performance-counters-and-wmi"></a><span data-ttu-id="4567f-258">성능 카운터 및 WMI 구성</span><span class="sxs-lookup"><span data-stu-id="4567f-258">Configuring performance counters and WMI</span></span>

1. <span data-ttu-id="4567f-259">**진단** 노드를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-259">Click the **Diagnostics** node.</span></span>

2. <span data-ttu-id="4567f-260">**성능 카운터 설정/해제**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-260">Click **Toggle Performance Counters**.</span></span> <span data-ttu-id="4567f-261">성능 카운터는 Off(기본값), ServiceOnly, All 세 가지 상태를 가집니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-261">The performance counter has three states: Off (default), ServiceOnly, and All.</span></span> <span data-ttu-id="4567f-262">링크를 클릭하면 이러한 세 가지 상태 간에 설정이 전환됩니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-262">Clicking the link toggles the setting among these three states.</span></span>

#### <a name="configuring-wmi-provider"></a><span data-ttu-id="4567f-263">WMI 공급자 구성</span><span class="sxs-lookup"><span data-stu-id="4567f-263">Configuring WMI Provider</span></span>

1. <span data-ttu-id="4567f-264">**진단** 노드를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-264">Click the **Diagnostics** node.</span></span>

2. <span data-ttu-id="4567f-265">WMI 공급자를 사용 하도록 설정 하려면 **Wmi 공급자 사용** 링크를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-265">To enable WMI provider, click the **Enable WMI Provider** link.</span></span>

#### <a name="enabling-wcf-tracing"></a><span data-ttu-id="4567f-266">WCF 추적 사용</span><span class="sxs-lookup"><span data-stu-id="4567f-266">Enabling WCF Tracing</span></span>

<span data-ttu-id="4567f-267">표준 속성으로 WCF 추적 파일을 만들거나 사용자 지정 추적 파일을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-267">You can create a WCF trace file with standard properties or set up a custom trace file.</span></span>

1. <span data-ttu-id="4567f-268">**진단** 노드를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-268">Click the **Diagnostics** node.</span></span>

2. <span data-ttu-id="4567f-269">**추적 사용**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-269">Click **Enable Tracing**.</span></span>

3. <span data-ttu-id="4567f-270">**추적 수준 링크를** 클릭 하 여 추적 수준을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-270">Click the **Trace Level** link to adjust the trace level.</span></span> <span data-ttu-id="4567f-271">추적 수준에는 Off, Critical, Error, Warning, Information 및 Verbose 여섯 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-271">There are six trace levels: Off, Critical, Error, Warning, Information, and Verbose.</span></span> <span data-ttu-id="4567f-272">**활동 추적** 및 **전파 활동** 옵션을 사용 하면 WCF 활동 추적 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-272">The **Activity Tracing** and **Propagate Activity** option enable you to use the WCF activity tracing feature.</span></span>

4. <span data-ttu-id="4567f-273">추적 파일 및 옵션을 지정하려면 추적 수신기 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-273">Click the trace listener name to specify the trace file and options.</span></span>

#### <a name="enabling-wcf-logging"></a><span data-ttu-id="4567f-274">WCF 로깅 사용</span><span class="sxs-lookup"><span data-stu-id="4567f-274">Enabling WCF Logging</span></span>

<span data-ttu-id="4567f-275">표준 속성으로 WCF 추적 파일을 만들거나 사용자 지정 추적 파일을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-275">You can create a WCF trace file with standard properties or set up a custom trace file.</span></span>

1. <span data-ttu-id="4567f-276">**진단** 노드를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-276">Click the **Diagnostics** node.</span></span>

2. <span data-ttu-id="4567f-277">**메시지 로깅 사용**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-277">Click **Enable Message Logging**.</span></span>

3. <span data-ttu-id="4567f-278">**로그 수준 링크를** 클릭 하 여 로그 수준을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-278">Click the **Log Level** link to adjust the log level.</span></span> <span data-ttu-id="4567f-279">로그 수준에는 Malformed, Service 및 Transport 세 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-279">There are three log levels: Malformed, Service, and Transport.</span></span>

4. <span data-ttu-id="4567f-280">로그 파일 및 옵션을 지정하려면 수신기 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-280">Click the listener name to specify the log file and options.</span></span>

> [!NOTE]
> <span data-ttu-id="4567f-281">응용 프로그램을 닫을 때 추적 및 메시지 로그가 자동으로 플러시되 게 하려면 **자동 플러시** 옵션을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-281">If you want the trace and message logs to be flushed automatically when your application is closed, enable the **Auto Flush** option.</span></span>

<span data-ttu-id="4567f-282">**진단** **요약 페이지** 에서는 진단 구성에서 가장 일반적인 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-282">The **Diagnostics** **Summary Page** enables you to accomplish the most common tasks in configuring diagnostics.</span></span> <span data-ttu-id="4567f-283">그러나 수신기 및 소스 설정을 수동으로 편집 하려면 **진단** 노드를 확장 하 고 **메시지 로깅**, **수신기** 및 **원본** 노드의 설정을 편집 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-283">However, if you want to manually edit the Listeners and Sources settings, you must expand the **Diagnostics** node and edit settings in **Message Logging**, **Listeners** and **Sources** node.</span></span>

#### <a name="enabling-wcf-custom-tracing-or-message-logging"></a><span data-ttu-id="4567f-284">WCF 사용자 지정 추적 또는 메시지 로깅 사용</span><span class="sxs-lookup"><span data-stu-id="4567f-284">Enabling WCF Custom Tracing or Message Logging</span></span>

1. <span data-ttu-id="4567f-285">**진단** 노드를 클릭 하 고 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-285">Click the **Diagnostics** node, and expand it.</span></span>

2. <span data-ttu-id="4567f-286">**수신기** 노드를 마우스 오른쪽 단추로 클릭 하 고 **새 수신기**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-286">Right-click the **Listeners** node and select **New Listener**.</span></span>

3. <span data-ttu-id="4567f-287">**InitData** 필드에 추적 파일 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-287">Type in the trace file name in the **InitData** field.</span></span> <span data-ttu-id="4567f-288">"..."를 클릭 하 여 단추를 클릭 하 여 경로를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-288">You can click the "…" button to browse to a path.</span></span>

4. <span data-ttu-id="4567f-289">**TypeName** 줄을 클릭 하면 "..."가 표시 됩니다. 단추만.</span><span class="sxs-lookup"><span data-stu-id="4567f-289">Clicking the **TypeName** line displays a "…" button.</span></span> <span data-ttu-id="4567f-290">이 단추를 클릭 하 여 이미 설치 된 미리 구성 된 추적 수신기를 찾는 데 사용할 수 있는 **추적 수신기 형식 브라우저**를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-290">Click this button to open the **Trace Listener Type Browser**, which you can use to find pre-configured trace listeners that are already installed.</span></span>

5. <span data-ttu-id="4567f-291">**원본** 섹션을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-291">Note the **Source** section.</span></span> <span data-ttu-id="4567f-292">이 섹션에서 **추가** 를 클릭 하 여 사용 가능한 추적 소스를 나열 하는 드롭다운 메뉴가 있는 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-292">Click **Add** in this section to open a dialog box with a drop-down menu, which lists available tracing sources.</span></span> <span data-ttu-id="4567f-293">추적 소스를 선택 하 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-293">Select a tracing source and click **OK**.</span></span>

6. <span data-ttu-id="4567f-294">메시지 로깅 설정을 편집 하려면 **메시지 로깅** 노드를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-294">To edit Message Logging settings, click the **Message Logging** node.</span></span> <span data-ttu-id="4567f-295">속성 표에서 설정을 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-295">You can edit the settings in the property grid.</span></span>

### <a name="advanced"></a><span data-ttu-id="4567f-296">고급</span><span class="sxs-lookup"><span data-stu-id="4567f-296">Advanced</span></span>

#### <a name="behaviors"></a><span data-ttu-id="4567f-297">동작</span><span class="sxs-lookup"><span data-stu-id="4567f-297">Behaviors</span></span>

<span data-ttu-id="4567f-298">**동작** 노드는 구성 파일에 현재 정의 되어 있는 동작을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-298">The **Behaviors** node displays the behaviors that are currently defined in the configuration file.</span></span>

<span data-ttu-id="4567f-299">동작 구성은 엔드포인트 및 서비스의 동작을 구성하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-299">Behavior configurations are used to configure behaviors of endpoints and services.</span></span> <span data-ttu-id="4567f-300">이러한 구성 설정은 **고급** 노드에 **서비스 동작** 및 **끝점 동작**아래에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-300">Such configuration settings are stored in the **Advanced** node under **Service Behaviors** and **Endpoint Behaviors**.</span></span> <span data-ttu-id="4567f-301">서비스 동작은 서비스에 의해 사용되는 반면 엔드포인트 동작은 엔드포인트에 의해 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-301">Service behaviors are used by services; whereas endpoint behaviors by endpoints.</span></span>

<span data-ttu-id="4567f-302">동작은 스택을 형성하는 확장명 요소의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-302">Behaviors are a collection of extension elements that for a stack.</span></span> <span data-ttu-id="4567f-303">스택의 맨 위에 있는 요소가 처음으로 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-303">The element at the top of the stack is applied first.</span></span> <span data-ttu-id="4567f-304">각 확장 요소는 자체 구성을 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-304">Each extension element can have its own configuration.</span></span>

##### <a name="creating-a-new-behavior-configuration"></a><span data-ttu-id="4567f-305">새 동작 구성 만들기</span><span class="sxs-lookup"><span data-stu-id="4567f-305">Creating a new Behavior Configuration</span></span>

<span data-ttu-id="4567f-306">다음 두 가지 방법으로 새 동작 구성을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-306">You can create a new behavior configuration in two ways.</span></span>

- <span data-ttu-id="4567f-307">동작 노드 중 하나를 마우스 오른쪽 단추로 클릭 하 고 "**새 동작 구성** ..."을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-307">Right-click one of the behavior nodes and select "**New Behavior Configuration…**</span></span>

- <span data-ttu-id="4567f-308">동작 노드 중 하나를 선택 하 고 **새 동작 구성**...을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-308">Select one of the behavior nodes and click the **New Behavior Configuration**…</span></span> <span data-ttu-id="4567f-309">창의 왼쪽 아래에 있는 **작업 창** 에서</span><span class="sxs-lookup"><span data-stu-id="4567f-309">in the **Task Pane** on the lower-left of the window.</span></span>

##### <a name="adding-behavior-element-extensions-to-a-behavior"></a><span data-ttu-id="4567f-310">동작 요소 확장을 동작에 추가</span><span class="sxs-lookup"><span data-stu-id="4567f-310">Adding Behavior Element Extensions to a Behavior</span></span>

1. <span data-ttu-id="4567f-311">동작 노드 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-311">Select one of the behavior nodes.</span></span>

2. <span data-ttu-id="4567f-312">편집하려는 동작을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-312">Select the behavior you want edit.</span></span>

3. <span data-ttu-id="4567f-313">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-313">Click **Add**.</span></span>

4. <span data-ttu-id="4567f-314">사용 가능한 확장 목록에서 추가하려는 동작 요소 확장을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-314">From the list of available extensions, select the behavior element extension you want to add.</span></span>

5. <span data-ttu-id="4567f-315">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-315">Click **Add**.</span></span>

##### <a name="adjusting-the-extension-position-in-a-behavior"></a><span data-ttu-id="4567f-316">동작에서 확장명 위치 조정</span><span class="sxs-lookup"><span data-stu-id="4567f-316">Adjusting the Extension Position in a Behavior</span></span>

<span data-ttu-id="4567f-317">동작은 스택을 형성하는 요소의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-317">Behaviors are collections of elements that form a stack.</span></span> <span data-ttu-id="4567f-318">스택의 각 요소는 자체 구성을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-318">Each element on the stack has its own configuration.</span></span> <span data-ttu-id="4567f-319">동작에서 동작 요소 확장명 순서는 스택의 해당 위치를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-319">The order of the behavior element extensions in a behavior indicates their positions in the stack.</span></span> <span data-ttu-id="4567f-320">스택의 맨 위에 있는 요소가 처음으로 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-320">Elements at the top of the stack are applied first.</span></span> <span data-ttu-id="4567f-321">순서를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="4567f-321">To change the ordering:</span></span>

1. <span data-ttu-id="4567f-322">동작 노드 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-322">Select one of the behavior nodes.</span></span>

2. <span data-ttu-id="4567f-323">편집하려는 동작을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-323">Select the behavior you want edit.</span></span>

3. <span data-ttu-id="4567f-324">**동작 요소 확장 위치** 섹션에서 동작 확장 요소를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-324">Select a behavior extension element in the **Behavior Element Extension Position** section.</span></span>

4. <span data-ttu-id="4567f-325">목록의 왼쪽에 있는 **위로** 또는 **아래로** 단추를 사용 하 여 선택한 요소의 위치를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-325">Use the **Up** or **Down** button on the left side of the list to change the position of the selected element.</span></span>

##### <a name="editing-the-configuration-of-behavior-element-extensions"></a><span data-ttu-id="4567f-326">동작 요소 확장의 구성 편집</span><span class="sxs-lookup"><span data-stu-id="4567f-326">Editing the Configuration of Behavior Element Extensions</span></span>

1. <span data-ttu-id="4567f-327">트리에서 동작 노드 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-327">Select one of the behavior nodes in the tree.</span></span>

2. <span data-ttu-id="4567f-328">편집하려는 요소가 포함된 동작을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-328">Select the behavior that contains the element you want to edit.</span></span>

3. <span data-ttu-id="4567f-329">편집하려는 동작 요소 확장을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-329">Select the behavior element extension you want to edit.</span></span> <span data-ttu-id="4567f-330">요소의 설정이 편집 가능한 오른쪽 창에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-330">The settings of the element appear in the right pane where they can be edited.</span></span>

#### <a name="protocolmapping"></a><span data-ttu-id="4567f-331">ProtocolMapping</span><span class="sxs-lookup"><span data-stu-id="4567f-331">ProtocolMapping</span></span>

<span data-ttu-id="4567f-332">이 섹션에서는 프로토콜 주소 체계와 가능한 바인딩 간의 정의된 매핑을 통해 http, tcp, MSMQ, net.pipe 등의 여러 가지 프로토콜에 대한 기본 바인딩 형식을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-332">This section allows you to set default binding types for different protocols such as http, tcp, MSMQ or net.pipe through defined mapping between protocol address schemes and the possible bindings.</span></span> <span data-ttu-id="4567f-333">또한 다른 프로토콜에 대한 매핑을 새로 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-333">You can also add new mappings to other protocols.</span></span>

#### <a name="extensions"></a><span data-ttu-id="4567f-334">확장</span><span class="sxs-lookup"><span data-stu-id="4567f-334">Extensions</span></span>

<span data-ttu-id="4567f-335">WCF 구성에서 사용 하기 위해 새 바인딩 확장, 바인딩 요소 확장, 표준 끝점 확장 및 동작 확장을 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-335">New binding extensions, binding element extensions, standard endpoint extensions and behavior extensions can be registered for use in WCF configuration.</span></span> <span data-ttu-id="4567f-336">확장은 이름/형식 쌍입니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-336">Extensions are name/type pairs.</span></span> <span data-ttu-id="4567f-337">이름은 구성의 확장명 이름을 정의하는 반면 형식은 확장을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-337">The name defines the name of the extension in configuration, whereas the type implements the extension.</span></span> <span data-ttu-id="4567f-338">확장에는 네 가지 형식이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-338">There are four types of extensions:</span></span>

- <span data-ttu-id="4567f-339">바인딩 확장은 전체 바인딩 형식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-339">Binding extensions define an entire binding type.</span></span> <span data-ttu-id="4567f-340">예: `basicHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="4567f-340">Example: `basicHttpBinding`.</span></span>

- <span data-ttu-id="4567f-341">바인딩 요소 확장은 바인딩의 요소를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-341">Binding element extensions define an element of a binding.</span></span> <span data-ttu-id="4567f-342">예: `textMessageEncoding`.</span><span class="sxs-lookup"><span data-stu-id="4567f-342">Example: `textMessageEncoding`.</span></span>

- <span data-ttu-id="4567f-343">표준 엔드포인트 확장은 전체 표준 엔드포인트를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-343">Standard endpoint extensions define an entire standard endpoint.</span></span> <span data-ttu-id="4567f-344">예: `discoveryEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="4567f-344">Example: `discoveryEndpoint`.</span></span>

- <span data-ttu-id="4567f-345">동작 요소 확장은 동작의 요소를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-345">Behavior element extensions define an element of a behavior.</span></span> <span data-ttu-id="4567f-346">예: `clientVia`.</span><span class="sxs-lookup"><span data-stu-id="4567f-346">Example: `clientVia`.</span></span>

 <span data-ttu-id="4567f-347">구성에 등록된 확장은 같은 형식의 다른 모든 WCF 구성 요소와 같이 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-347">Extensions that have been registered in configuration can be used like any other WCF component of the same type.</span></span>

##### <a name="adding-a-new-extension"></a><span data-ttu-id="4567f-348">새 확장 추가</span><span class="sxs-lookup"><span data-stu-id="4567f-348">Adding a new extension</span></span>

<span data-ttu-id="4567f-349">고급 노드에서 확장 노드 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-349">Select one of the extension nodes in the advanced nodes:</span></span>

1. <span data-ttu-id="4567f-350">**새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-350">Click **New**.</span></span>

2. <span data-ttu-id="4567f-351">이름 및 형식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-351">Enter a name and type.</span></span>

3. <span data-ttu-id="4567f-352">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-352">Click **OK**.</span></span>

4. <span data-ttu-id="4567f-353">이제 확장이 편집기의 적당한 위치에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-353">The extension now appears in the appropriate place in the Editor.</span></span> <span data-ttu-id="4567f-354">예를 들어, 동작 요소 확장을 추가하면 사용 가능한 확장의 목록에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-354">For example, if you add a behavior element extension, it appears in the list of available extensions.</span></span>

#### <a name="hosting-environment"></a><span data-ttu-id="4567f-355">호스팅 환경</span><span class="sxs-lookup"><span data-stu-id="4567f-355">Hosting Environment</span></span>

<span data-ttu-id="4567f-356">이 섹션에서는 서비스 호스팅 환경에 대한 인스턴스화 설정을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-356">This section allows you to define instantiation settings for the service hosting environment.</span></span>

### <a name="creating-a-configuration-file-using-the-wizard"></a><span data-ttu-id="4567f-357">마법사를 사용하여 구성 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="4567f-357">Creating a Configuration File Using the Wizard</span></span>

<span data-ttu-id="4567f-358">새 구성 파일을 만드는 한 가지 방법은 새 서비스 요소 마법사를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-358">One way to create a new configuration file is to use the New Service Element Wizard.</span></span> <span data-ttu-id="4567f-359">마법사는 COM + 및 웹 호스팅 가상 디렉터리를 포함 하 여, 설치 된 서비스 형식 및 컴퓨터의 WCF와 호환 되는 기타 요소를 찾고,이를 로드 하 여 구성을 훨씬 더 효율적으로 만들 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-359">The wizard finds the installed service types and other elements compatible with WCF on the computer, including COM+ and Web-hosted virtual directories, and loads them to make creating the configuration much more streamlined.</span></span>

#### <a name="creating-a-configuration-file"></a><span data-ttu-id="4567f-360">구성 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="4567f-360">Creating a Configuration File</span></span>

1. <span data-ttu-id="4567f-361">명령 창을 사용 하 여 서비스 구성 편집기를 시작 하 여 WCF 설치 위치로 이동한 다음를 입력 `SvcConfigEditor.exe` 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-361">Start Service Configuration Editor by using a command window to navigate to your WCF installation location, and then type `SvcConfigEditor.exe`.</span></span>

2. <span data-ttu-id="4567f-362">**파일** 메뉴에서 **열기** 를 선택 하 고 만들려는 구성 파일의 형식에 따라 **실행 파일**, **com + 서비스**또는 **webhosted 서비스**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-362">From the **File** menu, select **Open** and click **Executable**, **COM+ Service**, or **WebHosted Service**, depending on the type of configuration file you want to create.</span></span>

3. <span data-ttu-id="4567f-363">**열기** 대화 상자에서 구성 파일을 만들려는 특정 파일로 이동 하 여 해당 파일을 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-363">In the **Open** dialog box, navigate to the specific file you want to create a configuration file for and double-click it.</span></span>

4. <span data-ttu-id="4567f-364">**파일** 메뉴에서 **새 항목 추가** 를 가리킨 다음 **서비스**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-364">In the **File** menu, point to **Add New Item** and click **Service**.</span></span> <span data-ttu-id="4567f-365">그러면 새 서비스 요소 마법사가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-365">The New Service Element Wizard opens.</span></span>

5. <span data-ttu-id="4567f-366">새 서비스를 만들려면 마법사의 단계를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-366">Follow the steps in the wizard to create the new service.</span></span>

> [!NOTE]
> <span data-ttu-id="4567f-367">마법사에서 생성한 구성 파일에서 NetPeerTcpBinding을 사용하려면 바인딩 구성 요소를 수동으로 추가하여 `mode` 요소의 `security` 특성을 "None"으로 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-367">If you want to use the NetPeerTcpBinding from the configuration file generated by the Wizard, you have to manually add a binding configuration element and modify the `mode` attribute of its `security` element to "None".</span></span>

## <a name="configuring-com"></a><span data-ttu-id="4567f-368">COM+ 구성</span><span class="sxs-lookup"><span data-stu-id="4567f-368">Configuring COM+</span></span>

<span data-ttu-id="4567f-369">Service Configuration Editor를 사용하여 기존 COM+ 애플리케이션에 대한 새 구성 파일을 만들거나 기존 COM+ 구성을 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-369">The Service Configuration Editor enables you to create a new configuration file for an existing COM+ application, or edit an existing COM+ configuration.</span></span> <span data-ttu-id="4567f-370">**COM 계약** 노드는 <`comContract`> 섹션이 구성 파일에 있는 경우에만 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-370">The **COM Contract** node is only visible when the <`comContract`> section exists in the configuration file.</span></span>

### <a name="creating-a-new-com-configuration"></a><span data-ttu-id="4567f-371">새 COM+ 구성 만들기</span><span class="sxs-lookup"><span data-stu-id="4567f-371">Creating a New COM+ Configuration</span></span>

<span data-ttu-id="4567f-372">새 COM+ 구성을 만들기 전에 COM+ 애플리케이션이 구성 요소 서비스에 설치되어 있고 GAC(전역 어셈블리 캐시)에 등록되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-372">Before creating a new COM+ configuration, make sure that your COM+ application is installed in Component Services, and registered in the Global Assembly Cache (GAC).</span></span>

1. <span data-ttu-id="4567f-373">**파일** 메뉴를 선택 하 **Integrate**>  ->  **com + 응용 프로그램** 통합을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-373">Select **File** menu -> **Integrate** -> **COM+ Application.**</span></span> <span data-ttu-id="4567f-374">이 작업을 수행하면 현재 열려 있는 파일이 닫힙니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-374">This operation closes the current opened file.</span></span> <span data-ttu-id="4567f-375">현재 파일에 저장되지 않은 데이터가 있으면 저장 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-375">If there is unsaved data in the current file, a Save dialog appears.</span></span> <span data-ttu-id="4567f-376">그런 다음 **Com + 통합 마법사** 가 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-376">The **COM+ Integration Wizard** is then launched.</span></span>

2. <span data-ttu-id="4567f-377">첫 페이지의 트리에서 COM+ 애플리케이션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-377">In the first page, select the COM+ application from the tree.</span></span> <span data-ttu-id="4567f-378">트리에서 COM+ 애플리케이션을 찾을 수 없으면 구성 요소 서비스에 설치되어 있고 GAC(전역 어셈블리 캐시)에 등록되어 있는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="4567f-378">If you cannot find your COM+ application in the tree, verify that it is installed in the Component Services and registered in the Global Assembly Cache (GAC).</span></span>

3. <span data-ttu-id="4567f-379">다음 페이지에서는 WCF 서비스로 노출하려는 메서드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-379">In the next page, select which method(s) you want to expose as WCF services.</span></span> <span data-ttu-id="4567f-380">COM+ 애플리케이션에서 지원되는 모든 메서드가 기본적으로 표시되고 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-380">All the supported methods in the COM+ application are displayed and selected by default.</span></span>

4. <span data-ttu-id="4567f-381">호스팅 메서드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-381">Choose a hosting method.</span></span>

5. <span data-ttu-id="4567f-382">마법사의 안내에 따라 기타 설정을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-382">Configure other settings according to the guides in the wizard.</span></span>

6. <span data-ttu-id="4567f-383">Service Configuration Editor는 백그라운드에서 ComSvcConfig.exe를 활용하여 구성 파일을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-383">Service Configuration Editor utilizes ComSvcConfig.exe in the background to generate configuration file.</span></span> <span data-ttu-id="4567f-384">이 작업이 완료되면 요약을 보고 마법사를 끝낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-384">After this is completed, you can view a summary and exit the wizard.</span></span> <span data-ttu-id="4567f-385">생성된 구성 파일을 열어 직접 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-385">The generated configuration file is opened so that you can edit it directly.</span></span>

### <a name="editing-an-existing-com-configuration"></a><span data-ttu-id="4567f-386">기존 COM+ 구성 편집</span><span class="sxs-lookup"><span data-stu-id="4567f-386">Editing an Existing COM+ Configuration</span></span>

1. <span data-ttu-id="4567f-387">**파일** 메뉴를 선택 하 **Open**>  ->  **com + 서비스**를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-387">Select **File** menu -> **Open** -> **COM+ Service**…</span></span>

2. <span data-ttu-id="4567f-388">목록에서 편집할 COM+ 서비스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-388">Select the COM+ Service you want to edit from the list.</span></span>

3. <span data-ttu-id="4567f-389">**COM 계약** 노드에서 구성 설정을 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-389">Edit configuration settings in the **COM Contracts** node.</span></span>

    > [!NOTE]
    > <span data-ttu-id="4567f-390">COM 계약이 포함된 구성 파일을 직접 열어 편집할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-390">You can also directly open and edit a configuration file that contains COM contracts.</span></span>

## <a name="security"></a><span data-ttu-id="4567f-391">보안</span><span class="sxs-lookup"><span data-stu-id="4567f-391">Security</span></span>

<span data-ttu-id="4567f-392">구성 편집기에서 생성한 서비스 구성 파일은 보안되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-392">A service configuration file generated by the Configuration Editor is not guaranteed to be secure.</span></span> <span data-ttu-id="4567f-393">WCF 서비스를 보호 하는 방법을 알아보려면 [보안](./feature-details/security.md) 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4567f-393">Please refer to the [Security](./feature-details/security.md) documentation to find out how to secure your WCF services.</span></span>

<span data-ttu-id="4567f-394">또한 구성 편집기는 유효한 WCF 구성 요소를 읽고 쓰는 데만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-394">In addition, the Configuration Editor can only be used to read and write valid WCF configuration elements.</span></span> <span data-ttu-id="4567f-395">이 도구는 스키마 규격의 사용자 정의 요소를 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-395">The tool ignores schema-compliant, user-defined elements.</span></span> <span data-ttu-id="4567f-396">또한 이러한 요소를 구성 파일에서 제거하지 않고 알려진 WCF 요소에 대한 영향을 확인하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-396">It also does not attempt remove these elements from the configuration file or determine their effects on the known WCF elements.</span></span> <span data-ttu-id="4567f-397">이러한 요소가 애플리케이션이나 시스템에 위협을 야기하는지 여부는 사용자가 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4567f-397">It is the user’s responsibility to determine whether these elements pose a threat to the application or the system.</span></span>
