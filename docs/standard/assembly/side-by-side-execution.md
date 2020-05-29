---
title: 어셈블리 및 Side-by-Side 실행
description: 같은 컴퓨터에 여러 버전의 애플리케이션 또는 구성 요소를 저장하고 실행할 수 있는 기능인 Side-by-Side 실행에 대해 알아봅니다.
ms.date: 08/20/2019
helpviewer_keywords:
- side-by-side execution [.NET Framework]
- assemblies [.NET Framework], side-by-side execution
ms.assetid: e42036ee-7590-47d1-b884-cc856e39bd5d
ms.openlocfilehash: 74b5710c7e8ad60873fb83a3699ce3992ead6e07
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378636"
---
# <a name="assemblies-and-side-by-side-execution"></a><span data-ttu-id="91d91-103">어셈블리 및 Side-by-Side 실행</span><span class="sxs-lookup"><span data-stu-id="91d91-103">Assemblies and side-by-side execution</span></span>

<span data-ttu-id="91d91-104">Side-by-side 실행은 같은 컴퓨터에 여러 버전의 애플리케이션이나 구성 요소를 저장하고 실행할 수 있는 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="91d91-104">Side-by-side execution is the ability to store and execute multiple versions of an application or component on the same computer.</span></span> <span data-ttu-id="91d91-105">다시 말해 동시에 같은 컴퓨터에서 여러 런타임 버전을 사용할 수 있으며 특정 런타임 버전을 바탕으로 하는 여러 버전의 애플리케이션 및 구성 요소를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91d91-105">This means that you can have multiple versions of the runtime, and multiple versions of applications and components that use a version of the runtime, on the same computer at the same time.</span></span> <span data-ttu-id="91d91-106">Side-by-Side 실행을 사용하면 애플리케이션이 바인딩되는 구성 요소 버전과 애플리케이션에서 사용되는 런타임 버전을 보다 효과적으로 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91d91-106">Side-by-side execution gives you more control over what versions of a component an application binds to, and more control over what version of the runtime an application uses.</span></span>  
  
<span data-ttu-id="91d91-107">동일한 어셈블리의 서로 다른 버전을 side-by-side 방식으로 스토리지하고 실행하는 기능은 강력한 이름 지정의 매우 중요한 부분으로서, 런타임의 인프라에 빌드됩니다.</span><span class="sxs-lookup"><span data-stu-id="91d91-107">Support for side-by-side storage and execution of different versions of the same assembly is an integral part of strong naming and is built into the infrastructure of the runtime.</span></span> <span data-ttu-id="91d91-108">강력한 이름의 어셈블리 버전 번호는 어셈블리 ID의 일부이기 때문에 런타임에서는 동일한 어셈블리의 여러 버전을 전역 어셈블리 캐시에 저장하고 이들 어셈블리를 런타임에 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91d91-108">Because the strong-named assembly's version number is part of its identity, the runtime can store multiple versions of the same assembly in the global assembly cache and load those assemblies at run time.</span></span>  
  
<span data-ttu-id="91d91-109">런타임에서는 동시 애플리케이션을 만들 수 있는 기능을 제공하지만, Side-by-Side 실행 기능을 자동으로 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="91d91-109">Although the runtime provides you with the ability to create side-by-side applications, side-by-side execution is not automatic.</span></span> <span data-ttu-id="91d91-110">Side-by-Side 실행용 애플리케이션을 만드는 방법에 대한 자세한 내용은 [Side-by-Side 실행용 구성 요소를 만들기 위한 지침](../../framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="91d91-110">For more information on creating applications for side-by-side execution, see [Guidelines for creating components for side-by-side execution](../../framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91d91-111">참조</span><span class="sxs-lookup"><span data-stu-id="91d91-111">See also</span></span>

- [<span data-ttu-id="91d91-112">런타임에서 어셈블리를 찾는 방법</span><span class="sxs-lookup"><span data-stu-id="91d91-112">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="91d91-113">.NET 어셈블리</span><span class="sxs-lookup"><span data-stu-id="91d91-113">Assemblies in .NET</span></span>](index.md)
