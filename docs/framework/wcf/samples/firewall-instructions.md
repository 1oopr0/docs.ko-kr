---
title: 방화벽 지침
description: WCF 샘플에 대 한 방화벽에서 포트 또는 프로그램을 사용 하도록 설정 하는 방법을 알아봅니다. 요구 사항 및 보안 환경에 따라 다음 절차 중 하나를 사용 합니다.
ms.date: 03/30/2017
ms.assetid: a7dc429f-65ac-4faf-974a-77d5fb977fe1
ms.openlocfilehash: de55d067960b8f2096c129f6feaf037219e06a96
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246144"
---
# <a name="firewall-instructions"></a><span data-ttu-id="e9b04-104">방화벽 지침</span><span class="sxs-lookup"><span data-stu-id="e9b04-104">Firewall instructions</span></span>

<span data-ttu-id="e9b04-105">WCF (Windows Communication Foundation) 샘플이 작동할 수 있도록 방화벽에서 몇 가지 포트나 프로그램을 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-105">You must enable several ports or programs in the firewall so that the Windows Communication Foundation (WCF) samples can function.</span></span> <span data-ttu-id="e9b04-106">대부분의 샘플은 8000-8003 범위의 포트와 포트 9000을 사용하여 통신합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-106">Many of the samples communicate by using ports in the range 8000-8003, and port 9000.</span></span> <span data-ttu-id="e9b04-107">방화벽은 기본적으로 켜져 있어 이러한 포트에 액세스하지 못하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-107">The firewall is turned on by default and prevents access to these ports.</span></span> <span data-ttu-id="e9b04-108">샘플에 대해 방화벽을 사용하려면 요구 사항 및 보안 환경에 따라 다음 절차 중 하나를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-108">To enable the firewall for the samples, complete one of the following procedures, depending on your requirements and security environment:</span></span>

- <span data-ttu-id="e9b04-109">옵션 1: 샘플을 실행하는 동안 대화형으로 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-109">Option 1: Interactively enable samples while running.</span></span> <span data-ttu-id="e9b04-110">방화벽 구성을 미리 변경하지 않고 샘플의 빌드 및 실행을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-110">Make no advance changes to your firewall configuration and proceed to start building and running the samples.</span></span> <span data-ttu-id="e9b04-111">샘플을 실행 하면 **Windows 보안 경고** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-111">When a sample is run, a **Windows Security Alert** dialog box appears.</span></span> <span data-ttu-id="e9b04-112">그런 다음 문제가 되는 샘플 프로그램을 차단 해제 목록에 대화형으로 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-112">The sample program in question can then be added interactively to an unblocked list.</span></span> <span data-ttu-id="e9b04-113">이 절차를 사용하면 샘플을 다시 시작해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-113">With this procedure, you may have to then restart the sample.</span></span>

- <span data-ttu-id="e9b04-114">옵션 2: 미리 샘플 프로그램을 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-114">Option 2: Enable sample programs in advance.</span></span> <span data-ttu-id="e9b04-115">**Windows 방화벽 제어판** 애플릿을 시작 하 고 실행 하려는 샘플 프로그램을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-115">Start the **Windows Firewall Control Panel** applet and enable the sample programs you plan to run.</span></span> <span data-ttu-id="e9b04-116">프로그램을 먼저 빌드해야만 실행 파일이 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-116">You must build the programs first so the executable files exist.</span></span> <span data-ttu-id="e9b04-117">다음 절차에서는 자세한 지침을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-117">You can find more detailed instructions in the following procedure.</span></span>

- <span data-ttu-id="e9b04-118">옵션 3: 미리 포트 범위를 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-118">Option 3: Enable a port range in advance.</span></span> <span data-ttu-id="e9b04-119">**Windows 방화벽 제어판** 애플릿을 시작 하 고 샘플에서 사용 하는 포트 80, 443, 8000-8003 및 9000을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-119">Start the **Windows Firewall Control Panel** applet and enable ports 80, 443, 8000-8003 and 9000, which are used by the samples.</span></span> <span data-ttu-id="e9b04-120">다음 절차에서는 자세한 지침을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-120">You can find more detailed instructions in the following procedure.</span></span> <span data-ttu-id="e9b04-121">이 옵션의 경우 샘플뿐 아니라 모든 프로그램에서 이러한 포트를 사용할 수 있기 때문에 다른 옵션에 비해 보안이 취약합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-121">This option is less secure than the others because it allows any program to use these ports, not just the samples.</span></span>

<span data-ttu-id="e9b04-122">사용하기에 적합한 절차를 잘 모르는 경우 첫 번째 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-122">If you are unsure of which procedure to use, choose the first option.</span></span> <span data-ttu-id="e9b04-123">다른 공급업체의 방화벽을 실행 중인 경우에도 이와 유사하게 변경해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-123">If you are running a firewall from another vendor, you might need to make similar changes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e9b04-124">방화벽 구성을 변경하면 보안에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-124">Changing your firewall configuration affects your security.</span></span> <span data-ttu-id="e9b04-125">변경한 내용을 기록하고, 샘플 작업을 완료한 후에 변경 내용을 제거하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-125">It is recommended that you record the changes you make and remove them when you are finished working with the samples.</span></span>

## <a name="enable-samples-programs-in-advance"></a><span data-ttu-id="e9b04-126">미리 샘플 프로그램 사용</span><span class="sxs-lookup"><span data-stu-id="e9b04-126">Enable samples programs in advance</span></span>

1. <span data-ttu-id="e9b04-127">샘플을 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-127">Build the sample.</span></span>

2. <span data-ttu-id="e9b04-128">**시작**  >  **실행**을 선택 하 고을 입력 `firewall.cpl` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-128">Choose **Start** > **Run**, and enter `firewall.cpl`.</span></span> <span data-ttu-id="e9b04-129">그러면 **Windows 방화벽 제어판** 애플릿이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-129">This opens the **Windows Firewall Control Panel** applet.</span></span>

    > [!NOTE]
    > <span data-ttu-id="e9b04-130">Windows 방화벽을 통해 통신할 수 있어야 하는 샘플을 실행하려면 방화벽 설정을 변경할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-130">You must have permission to change the Firewall settings to run samples that require the ability to communicate through the Windows Firewall.</span></span> <span data-ttu-id="e9b04-131">일부 방화벽 설정을 사용할 수 없고 컴퓨터가 도메인에 연결되어 있는 경우 시스템 관리자가 그룹 정책을 통해 이러한 설정을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-131">If some firewall settings are unavailable and your computer is connected to a domain, your system administrator might be controlling these settings through Group Policy.</span></span>

3. <span data-ttu-id="e9b04-132">Windows 방화벽을 통해 프로그램을 허용 하는 다음과 같은 운영 관련 단계 중 하나를 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-132">Complete one of the following operating-specific steps to allow a program through the Windows Firewall:</span></span>

    - <span data-ttu-id="e9b04-133">Windows 7 또는 Windows Server 2008 r 2에서 **Windows 방화벽을 통해 프로그램 또는 기능 허용**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-133">On Windows 7 or Windows Server 2008 R2, click **Allow a program or feature through Windows Firewall**.</span></span> <span data-ttu-id="e9b04-134">**설정 변경**  >  **다른 프로그램 허용**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-134">Click **Change Settings** > **Allow Another Program**.</span></span>

    - <span data-ttu-id="e9b04-135">Windows Vista 또는 Windows Server 2008에서 **Windows 방화벽을 통해 프로그램 허용**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-135">On Windows Vista or Windows Server 2008, click **Allow a program through Windows Firewall**.</span></span>

4. <span data-ttu-id="e9b04-136">**예외** 탭에서 **프로그램 추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-136">On the **Exceptions** tab, click **Add Program**.</span></span>

5. <span data-ttu-id="e9b04-137">**찾아보기** 단추를 클릭 하 고 실행 하려는 샘플의 실행 파일을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-137">Click the **Browse** button and select the executable file of the sample you plan to run.</span></span>

6. <span data-ttu-id="e9b04-138">실행 하려는 모든 샘플의 실행 파일을 추가할 때까지 4 단계와 5 단계를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-138">Repeat steps 4 and 5 until you have added the executable files of all the samples you plan to run.</span></span>

7. <span data-ttu-id="e9b04-139">**확인** 을 클릭 하 여 방화벽 애플릿을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-139">Click **OK** to close the firewall applet.</span></span>

## <a name="enable-a-port-range-in-advance"></a><span data-ttu-id="e9b04-140">포트 범위를 미리 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="e9b04-140">Enable a port range in advance</span></span>

1. <span data-ttu-id="e9b04-141">**시작**  >  **실행**을 선택 하 고을 입력 `firewall.cpl` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-141">Choose **Start** > **Run**, and enter `firewall.cpl`.</span></span> <span data-ttu-id="e9b04-142">그러면 **Windows 방화벽 제어판** 애플릿이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-142">This opens the **Windows Firewall Control Panel** applet.</span></span>

2. <span data-ttu-id="e9b04-143">Windows 7 또는 Windows Server 2008 R2의 경우 다음 단계를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-143">On Windows 7 or Windows Server 2008 R2, follow these steps.</span></span>

    1. <span data-ttu-id="e9b04-144">Windows 방화벽 창의 왼쪽 열에서 **고급 설정** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-144">Click **Advanced settings** in the left column of the Windows Firewall window.</span></span>

    2. <span data-ttu-id="e9b04-145">왼쪽 열에서 **인바운드 규칙** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-145">Click **Inbound Rules** in the left column.</span></span>

    3. <span data-ttu-id="e9b04-146">오른쪽 열에서 **새 규칙** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-146">Click **New Rules** in the right column.</span></span>

    4. <span data-ttu-id="e9b04-147">**포트** 를 선택 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-147">Select **Port** and click **next**.</span></span>

    5. <span data-ttu-id="e9b04-148">**TCP** 를 선택 하 고 `8000, 8001, 8002, 8003, 9000, 80, 443` **특정 로컬 포트** 필드에를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-148">Select **TCP** and enter `8000, 8001, 8002, 8003, 9000, 80, 443` in the **Specific local ports** field.</span></span>

    6. <span data-ttu-id="e9b04-149">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-149">Click **Next**.</span></span>

    7. <span data-ttu-id="e9b04-150">**연결 허용**을 선택 하 고 **다음** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-150">Select **Allow the connection**, and click **Next** .</span></span>

    8. <span data-ttu-id="e9b04-151">**도메인** 및 **개인**을 선택 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-151">Select **Domain** and **Private**, and click **Next**.</span></span>

    9. <span data-ttu-id="e9b04-152">이 규칙 `WCF-WF 4.0 Samples` 의 이름을로, **마침**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-152">Name this rule `WCF-WF 4.0 Samples`, and click **Finish**.</span></span>

    10. <span data-ttu-id="e9b04-153">**아웃 바운드 규칙** 을 클릭 하 고 c ~ h 단계를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-153">Click **Outbound Rules** and repeat steps c to h.</span></span>

3. <span data-ttu-id="e9b04-154">Windows Vista 또는 Windows Server 2008에서 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-154">On Windows Vista or Windows Server 2008, follow these steps.</span></span>

    1. <span data-ttu-id="e9b04-155">**Windows 방화벽을 통한 프로그램 실행 허용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-155">Click **Allow a program through Windows Firewall**.</span></span>

    2. <span data-ttu-id="e9b04-156">**예외** 탭에서 **포트 추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-156">On the **Exceptions** tab, click **Add Port**.</span></span>

    3. <span data-ttu-id="e9b04-157">이름을 입력 하 고 포트 번호로 8000를 입력 한 다음 **TCP** 옵션을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-157">Enter a name, enter 8000 as the port number, and select the **TCP** option.</span></span>

    4. <span data-ttu-id="e9b04-158">**범위 변경** 단추를 클릭 하 고 **내 네트워크** (서브넷)만 옵션을 선택한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-158">Click the **Change Scope** button, select the **My Network** (subnet) only option, and click **OK**.</span></span>

    5. <span data-ttu-id="e9b04-159">포트 8001, 8002, 8003, 9000, 80 및 443에 대해 b-d단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-159">Repeat steps b to d for ports 8001, 8002, 8003, 9000, 80, and 443.</span></span>

4. <span data-ttu-id="e9b04-160">**확인** 을 클릭 하 여 방화벽 애플릿을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-160">Click **OK** to close the firewall applet.</span></span>

> [!NOTE]
> <span data-ttu-id="e9b04-161">샘플 작업을 완료한 후 방화벽 예외를 모두 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-161">Remove any firewall exceptions when you are finished working with the samples.</span></span> <span data-ttu-id="e9b04-162">이렇게 하려면 **Windows 방화벽 제어판** 애플릿을 열고 이전 절차에서 추가한 모든 프로그램 또는 포트 항목을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b04-162">To do so, open the **Windows Firewall Control Panel** applet and remove any programs or port entries that were added by the previous procedures.</span></span>
