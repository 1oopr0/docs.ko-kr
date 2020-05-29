---
title: 어셈블리 지연 서명
description: 이 문서에서는 강력한 이름 서명을 위해 PE 파일에 공간을 예약하지만 실제 서명을 지연하는 지연 또는 부분 서명에 대해 설명합니다.
ms.date: 08/19/2019
helpviewer_keywords:
- deferring assembly signing
- signing assemblies
- assemblies [.NET Framework], signing
- strong-named assemblies, delaying assembly signing
- partial assembly signing
ms.assetid: 9d300e17-5bf1-4360-97da-2aa55efd9070
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 7b5c8c8463fdc573782fa457bf5671c72a7e25f7
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378498"
---
# <a name="delay-sign-an-assembly"></a><span data-ttu-id="64c98-103">어셈블리 지연 서명</span><span class="sxs-lookup"><span data-stu-id="64c98-103">Delay-sign an assembly</span></span>

<span data-ttu-id="64c98-104">조직에 개발자가 일상적으로 액세스할 수 없는 엄격하게 보호된 키 쌍이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64c98-104">An organization can have a closely guarded key pair that developers can't access on a daily basis.</span></span> <span data-ttu-id="64c98-105">대부분이 경우 퍼블릭 키를 사용할 수 있지만 프라이빗 키에 대한 액세스는 몇몇 개인만으로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="64c98-105">The public key is often available, but access to the private key is restricted to only a few individuals.</span></span> <span data-ttu-id="64c98-106">강력한 이름을 사용하여 어셈블리를 개발할 경우 강력한 이름의 대상 어셈블리를 참조하는 각 어셈블리에는 대상 어셈블리에 강력한 이름을 지정하는 데 사용되는 공개 키의 토큰이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="64c98-106">When developing assemblies with strong names, each assembly that references the strong-named target assembly contains the token of the public key used to give the target assembly a strong name.</span></span> <span data-ttu-id="64c98-107">이를 위해 개발 프로세스 중에 공개 키를 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="64c98-107">This requires that the public key be available during the development process.</span></span>

<span data-ttu-id="64c98-108">빌드 시간에 지연된 서명이나 부분 서명을 사용하여 PE(이식 가능한 실행 파일) 파일에서 강력한 이름 서명에 사용할 공간을 예약하지만 이후 단계까지(일반적으로 어셈블리를 제공하기 바로 전) 실제 서명을 연기할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64c98-108">You can use delayed or partial signing at build time to reserve space in the portable executable (PE) file for the strong name signature, but defer the actual signing until some later stage, usually just before shipping the assembly.</span></span>

<span data-ttu-id="64c98-109">어셈블리를 지연 서명하려면:</span><span class="sxs-lookup"><span data-stu-id="64c98-109">To delay-sign an assembly:</span></span>

1. <span data-ttu-id="64c98-110">최종 서명을 수행할 조직에서 키 쌍의 공개 키 부분을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="64c98-110">Get the public key portion of the key pair from the organization that will do the eventual signing.</span></span> <span data-ttu-id="64c98-111">일반적으로 이 키는 *.snk* 파일 형식으로서 Windows SDK가 제공하는 [강력한 이름 도구(Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md)를 사용하여 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64c98-111">Typically this key is in the form of an *.snk* file, which can be created using the [Strong Name tool (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) provided by the Windows SDK.</span></span>

2. <span data-ttu-id="64c98-112"><xref:System.Reflection>의 두 가지 사용자 지정 특성을 사용하여 어셈블리에 대한 소스 코드를 주석으로 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="64c98-112">Annotate the source code for the assembly with two custom attributes from <xref:System.Reflection>:</span></span>

   - <span data-ttu-id="64c98-113"><xref:System.Reflection.AssemblyKeyFileAttribute> - 매개 변수로 공개 키가 포함된 파일의 이름을 생성자에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="64c98-113"><xref:System.Reflection.AssemblyKeyFileAttribute>, which passes the name of the file containing the public key as a parameter to its constructor.</span></span>

   - <span data-ttu-id="64c98-114"><xref:System.Reflection.AssemblyDelaySignAttribute> - 매개 변수로 **true**를 생성자에 전달하여 서명 지연에 사용 중임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="64c98-114"><xref:System.Reflection.AssemblyDelaySignAttribute>, which indicates that delay signing is being used by passing **true** as a parameter to its constructor.</span></span>

   <span data-ttu-id="64c98-115">예를 들어:</span><span class="sxs-lookup"><span data-stu-id="64c98-115">For example:</span></span>

   ```cpp
   [assembly:AssemblyKeyFileAttribute("myKey.snk")];
   [assembly:AssemblyDelaySignAttribute(true)];
   ```

   ```csharp
   [assembly:AssemblyKeyFileAttribute("myKey.snk")]
   [assembly:AssemblyDelaySignAttribute(true)]
   ```

   ```vb
   <Assembly:AssemblyKeyFileAttribute("myKey.snk")>
   <Assembly:AssemblyDelaySignAttribute(True)>
   ```

3. <span data-ttu-id="64c98-116">컴파일러는 공개 키를 어셈블리 매니페스트에 삽입하고 PE 파일에서 전체 강력한 이름 시그니처에 사용할 공간을 예약합니다.</span><span class="sxs-lookup"><span data-stu-id="64c98-116">The compiler inserts the public key into the assembly manifest and reserves space in the PE file for the full strong name signature.</span></span> <span data-ttu-id="64c98-117">실제 공개 키는 어셈블리가 빌드되는 동안 저장되어야 합니다. 그래야 이 어셈블리를 참조하는 다른 어셈블리가 자체적인 어셈블리 참조에 저장할 키를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64c98-117">The real public key must be stored while the assembly is built so that other assemblies that reference this assembly can obtain the key to store in their own assembly reference.</span></span>

4. <span data-ttu-id="64c98-118">어셈블리에 유효한 강력한 이름 시그니처가 없으므로 해당 시그니처의 확인이 해제되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="64c98-118">Because the assembly does not have a valid strong name signature, the verification of that signature must be turned off.</span></span> <span data-ttu-id="64c98-119">강력한 이름 도구와 함께 **–Vr** 옵션을 사용하여 이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64c98-119">You can do this by using the **–Vr** option with the Strong Name tool.</span></span>

     <span data-ttu-id="64c98-120">다음 예제에서는 *myAssembly.dll*이라는 어셈블리에 대한 확인을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="64c98-120">The following example turns off verification for an assembly called *myAssembly.dll*.</span></span>

   ```console
   sn –Vr myAssembly.dll
   ```

   <span data-ttu-id="64c98-121">ARM(Advanced RISC Machine) 마이크로프로세서와 같은 강력한 이름 도구를 실행할 수 없는 플랫폼에서 확인을 해제하려면 **–Vk** 옵션을 사용하여 레지스트리 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="64c98-121">To turn off verification on platforms where you can’t run the Strong Name tool, such as Advanced RISC Machine (ARM) microprocessors, use the **–Vk** option to create a registry file.</span></span> <span data-ttu-id="64c98-122">확인을 해제하려는 컴퓨터의 레지스트리에 레지스트리 파일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="64c98-122">Import the registry file into the registry on the computer where you want to turn off verification.</span></span> <span data-ttu-id="64c98-123">다음 예제에서는 `myAssembly.dll`에 대한 레지스트리 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="64c98-123">The following example creates a registry file for `myAssembly.dll`.</span></span>

   ```console
   sn –Vk myRegFile.reg myAssembly.dll
   ```

   <span data-ttu-id="64c98-124">**–Vr** 또는 **–Vk** 옵션을 사용하여 테스트 키 서명에 대해 *.snk* 파일을 선택적으로 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64c98-124">With either the **–Vr** or **–Vk** option, you can optionally include an *.snk* file for test key signing.</span></span>

   > [!WARNING]
   > <span data-ttu-id="64c98-125">강력한 이름을 보안용으로 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="64c98-125">Do not rely on strong names for security.</span></span> <span data-ttu-id="64c98-126">강력한 이름은 고유한 ID를 제공할 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="64c98-126">They provide a unique identity only.</span></span>

   > [!NOTE]
   > <span data-ttu-id="64c98-127">64비트 컴퓨터에서 Visual Studio를 통해 개발하는 동안 서명 연기를 사용하고 **모든 CPU**에 대한 어셈블리를 컴파일할 경우 **-Vr** 옵션을 두 번 적용해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64c98-127">If you use delay signing during development with Visual Studio on a 64-bit computer, and you compile an assembly for **Any CPU**, you might have to apply the **-Vr** option twice.</span></span> <span data-ttu-id="64c98-128">Visual Studio에서 **모든 CPU**는 **플랫폼 대상** 빌드 속성의 값이고 명령줄에서 컴파일할 경우 기본값입니다. 애플리케이션을 명령줄 또는 파일 탐색기에서 실행하려면 [Sn.exe(강력한 이름 도구)](../../framework/tools/sn-exe-strong-name-tool.md)의 64비트 버전을 사용하여 **-Vr** 옵션을 어셈블리에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="64c98-128">(In Visual Studio, **Any CPU** is a value of the **Platform Target** build property; when you compile from the command line, it is the default.) To run your application from the command line or from File Explorer, use the 64-bit version of the [Sn.exe (Strong Name tool)](../../framework/tools/sn-exe-strong-name-tool.md) to apply the **-Vr** option to the assembly.</span></span> <span data-ttu-id="64c98-129">디자인 타임에 어셈블리를 Visual Studio에 로드하려면(예: 어셈블리에 애플리케이션의 다른 어셈블리에서 사용되는 구성 요소가 포함된 경우) 강력한 이름 도구의 32비트 버전을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="64c98-129">To load the assembly into Visual Studio at design time (for example, if the assembly contains components that are used by other assemblies in your application), use the 32-bit version of the strong-name tool.</span></span> <span data-ttu-id="64c98-130">그 이유는 JIT(Just-In-Time) 컴파일러가 명령줄에서 실행되는 어셈블리를 64비트 네이티브 코드로 컴파일하고, 디자인 타임 환경에 로드되는 어셈블리를 32비트 네이티브 코드로 컴파일하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="64c98-130">This is because the just-in-time (JIT) compiler compiles the assembly to 64-bit native code when the assembly is run from the command line, and to 32-bit native code when the assembly is loaded into the design-time environment.</span></span>

5. <span data-ttu-id="64c98-131">나중에, 일반적으로 제공하기 바로 전에 강력한 이름 도구와 함께 **–R** 옵션을 사용하여 실제 강력한 이름으로 서명하기 위해 조직의 서명 기관에 어셈블리를 제출합니다.</span><span class="sxs-lookup"><span data-stu-id="64c98-131">Later, usually just before shipping, you submit the assembly to your organization's signing authority for the actual strong name signing using the **–R** option with the Strong Name tool.</span></span>

   <span data-ttu-id="64c98-132">다음 예제에서는 *sgKey.snk* 키 쌍을 사용하여 강력한 이름으로 *myAssembly.dll*이라는 어셈블리에 서명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64c98-132">The following example signs an assembly called *myAssembly.dll* with a strong name using the *sgKey.snk* key pair.</span></span>

   ```console
   sn -R myAssembly.dll sgKey.snk
   ```

## <a name="see-also"></a><span data-ttu-id="64c98-133">참조</span><span class="sxs-lookup"><span data-stu-id="64c98-133">See also</span></span>

- [<span data-ttu-id="64c98-134">어셈블리 만들기</span><span class="sxs-lookup"><span data-stu-id="64c98-134">Create assemblies</span></span>](create.md)
- [<span data-ttu-id="64c98-135">방법: 퍼블릭/프라이빗 키 쌍 만들기</span><span class="sxs-lookup"><span data-stu-id="64c98-135">How to: Create a public-private key pair</span></span>](create-public-private-key-pair.md)
- [<span data-ttu-id="64c98-136">Sn.exe(강력한 이름 도구)</span><span class="sxs-lookup"><span data-stu-id="64c98-136">Sn.exe (Strong Name tool)</span></span>](../../framework/tools/sn-exe-strong-name-tool.md)
