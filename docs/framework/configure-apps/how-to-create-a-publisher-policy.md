---
title: '방법: 게시자 정책 만들기'
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
ms.openlocfilehash: 7c36f6126f0d779a43a22fc11e647ba2d3b03a30
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/06/2020
ms.locfileid: "81646050"
---
# <a name="how-to-create-a-publisher-policy"></a><span data-ttu-id="1fa87-102">방법: 게시자 정책 만들기</span><span class="sxs-lookup"><span data-stu-id="1fa87-102">How to: Create a Publisher Policy</span></span>

<span data-ttu-id="1fa87-103">어셈블리 공급 업체는 응용 프로그램에서 업그레이드 된 어셈블리와 함께 게시자 정책 파일을 포함 하 여 최신 버전의 어셈블리를 사용 해야 하는 상태를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1fa87-103">Vendors of assemblies can state that applications should use a newer version of an assembly by including a publisher policy file with the upgraded assembly.</span></span> <span data-ttu-id="1fa87-104">게시자 정책 파일은 어셈블리 리디렉션과 코드 베이스 설정을 지정 하 고 응용 프로그램 구성 파일과 동일한 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fa87-104">The publisher policy file specifies assembly redirection and code base settings, and uses the same format as an application configuration file.</span></span> <span data-ttu-id="1fa87-105">게시자 정책 파일은 어셈블리로 컴파일되고 전역 어셈블리 캐시에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1fa87-105">The publisher policy file is compiled into an assembly and placed in the global assembly cache.</span></span>

<span data-ttu-id="1fa87-106">게시자 정책을 만드는 데는 다음과 같은 세 가지 단계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1fa87-106">There are three steps involved in creating a publisher policy:</span></span>

1. <span data-ttu-id="1fa87-107">게시자 정책 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1fa87-107">Create a publisher policy file.</span></span>

2. <span data-ttu-id="1fa87-108">게시자 정책 어셈블리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1fa87-108">Create a publisher policy assembly.</span></span>

3. <span data-ttu-id="1fa87-109">전역 어셈블리 캐시에 게시자 정책 어셈블리를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fa87-109">Add the publisher policy assembly to the global assembly cache.</span></span>

<span data-ttu-id="1fa87-110">게시자 정책에 대 한 스키마는 [어셈블리 버전 리디렉션](redirect-assembly-versions.md)에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1fa87-110">The schema for publisher policy is described in [Redirecting Assembly Versions](redirect-assembly-versions.md).</span></span> <span data-ttu-id="1fa87-111">다음 예에서는의 한 버전을 다른 버전으로 리디렉션하는 게시자 정책 파일을 보여 줍니다 `myAssembly` .</span><span class="sxs-lookup"><span data-stu-id="1fa87-111">The following example shows a publisher policy file that redirects one version of `myAssembly` to another.</span></span>

```xml
<configuration>
   <runtime>
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
       <dependentAssembly>
         <assemblyIdentity name="myAssembly"
                           publicKeyToken="32ab4ba45e0a69a1"
                           culture="en-us" />
         <!-- Redirecting to version 2.0.0.0 of the assembly. -->
         <bindingRedirect oldVersion="1.0.0.0"
                          newVersion="2.0.0.0"/>
       </dependentAssembly>
      </assemblyBinding>
   </runtime>
</configuration>
```

<span data-ttu-id="1fa87-112">코드 베이스를 지정 하는 방법에 대 한 자세한 내용은 [어셈블리 위치 지정](specify-assembly-location.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1fa87-112">To learn how to specify a code base, see [Specifying an Assembly's Location](specify-assembly-location.md).</span></span>

## <a name="creating-the-publisher-policy-assembly"></a><span data-ttu-id="1fa87-113">게시자 정책 어셈블리 만들기</span><span class="sxs-lookup"><span data-stu-id="1fa87-113">Creating the Publisher Policy Assembly</span></span>

<span data-ttu-id="1fa87-114">[어셈블리 링커 (al.exe)](../tools/al-exe-assembly-linker.md) 를 사용 하 여 게시자 정책 어셈블리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1fa87-114">Use the [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) to create the publisher policy assembly.</span></span>

#### <a name="to-create-a-publisher-policy-assembly"></a><span data-ttu-id="1fa87-115">게시자 정책 어셈블리를 만들려면</span><span class="sxs-lookup"><span data-stu-id="1fa87-115">To create a publisher policy assembly</span></span>

<span data-ttu-id="1fa87-116">명령 프롬프트에서 다음 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1fa87-116">Type the following command at the command prompt:</span></span>

```console
al /link:publisherPolicyFile /out:publisherPolicyAssemblyFile /keyfile:keyPairFile /platform:processorArchitecture
```

<span data-ttu-id="1fa87-117">이 명령에서 다음이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1fa87-117">In this command:</span></span>

- <span data-ttu-id="1fa87-118">`publisherPolicyFile`인수는 게시자 정책 파일의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="1fa87-118">The `publisherPolicyFile` argument is the name of the publisher policy file.</span></span>

- <span data-ttu-id="1fa87-119">`publisherPolicyAssemblyFile`인수는이 명령에서 생성 되는 게시자 정책 어셈블리의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="1fa87-119">The `publisherPolicyAssemblyFile` argument is the name of the publisher policy assembly that results from this command.</span></span> <span data-ttu-id="1fa87-120">어셈블리 파일 이름은 다음 형식을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fa87-120">The assembly file name must follow the format:</span></span>

  <span data-ttu-id="1fa87-121">' majorNumber. minorNumber '</span><span class="sxs-lookup"><span data-stu-id="1fa87-121">\`policy.majorNumber.minorNumber.mainAssemblyName.dll'</span></span>

- <span data-ttu-id="1fa87-122">`keyPairFile`인수는 키 쌍을 포함 하는 파일의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="1fa87-122">The `keyPairFile` argument is the name of the file containing the key pair.</span></span> <span data-ttu-id="1fa87-123">동일한 키 쌍을 사용 하 여 어셈블리 및 게시자 정책 어셈블리에 서명 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fa87-123">You must sign the assembly and publisher policy assembly with the same key pair.</span></span>

- <span data-ttu-id="1fa87-124">`processorArchitecture`인수는 프로세서별 어셈블리에서 대상으로 지정 된 플랫폼을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fa87-124">The `processorArchitecture` argument identifies the platform targeted by a processor-specific assembly.</span></span>

  > [!NOTE]
  > <span data-ttu-id="1fa87-125">특정 프로세서 아키텍처를 대상으로 하는 기능은 .NET Framework 2.0부터 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1fa87-125">The ability to target a specific processor architecture is available starting with .NET Framework 2.0.</span></span>

<span data-ttu-id="1fa87-126">특정 프로세서 아키텍처를 대상으로 하는 기능은 .NET Framework 2.0부터 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1fa87-126">The ability to target a specific processor architecture is available starting with .NET Framework 2.0.</span></span> <span data-ttu-id="1fa87-127">다음 명령을 사용 하 여 라는 게시자 정책 파일에서 라는 게시자 정책 어셈블리를 만들고 `policy.1.0.myAssembly` `pub.config` , 파일의 키 쌍을 사용 하 여 어셈블리에 강력한 이름을 할당 하 `sgKey.snk` 고, 어셈블리가 x86 프로세서 아키텍처를 대상으로 지정 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fa87-127">The following command creates a publisher policy assembly called `policy.1.0.myAssembly` from a publisher policy file called `pub.config`, assigns a strong name to the assembly using the key pair in the `sgKey.snk` file, and specifies that the assembly targets the x86 processor architecture.</span></span>

```console
al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86
```

<span data-ttu-id="1fa87-128">게시자 정책 어셈블리는 적용 되는 어셈블리의 프로세서 아키텍처와 일치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fa87-128">The publisher policy assembly must match the processor architecture of the assembly that it applies to.</span></span> <span data-ttu-id="1fa87-129">따라서 어셈블리 <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> 의 값이 <xref:System.Reflection.ProcessorArchitecture.MSIL> 인 경우 해당 어셈블리에 대 한 게시자 정책 어셈블리는를 사용 하 여 만들어야 합니다 `/platform:anycpu` .</span><span class="sxs-lookup"><span data-stu-id="1fa87-129">Thus, if your assembly has a <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> value of <xref:System.Reflection.ProcessorArchitecture.MSIL>, the publisher policy assembly for that assembly must be created with `/platform:anycpu`.</span></span> <span data-ttu-id="1fa87-130">각 프로세서별 어셈블리에 대해 별도의 게시자 정책 어셈블리를 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fa87-130">You must provide a separate publisher policy assembly for each processor-specific assembly.</span></span>

<span data-ttu-id="1fa87-131">이 규칙의 결과는 어셈블리에 대 한 프로세서 아키텍처를 변경 하기 위해 올바른 프로세서 아키텍처를 사용 하 여 새 게시자 정책 어셈블리를 제공할 수 있도록 버전 번호의 주 또는 부 구성 요소를 변경 해야 한다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1fa87-131">A consequence of this rule is that in order to change the processor architecture for an assembly, you must change the major or minor component of the version number, so that you can supply a new publisher policy assembly with the correct processor architecture.</span></span> <span data-ttu-id="1fa87-132">어셈블리에 다른 프로세서 아키텍처가 있으면 이전 게시자 정책 어셈블리에서 어셈블리를 서비스 할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1fa87-132">The old publisher policy assembly cannot service your assembly once your assembly has a different processor architecture.</span></span>

<span data-ttu-id="1fa87-133">다른 결과는 항상 프로세서 아키텍처를 지정 하기 때문에 버전 2.0 링커를 사용 하 여 이전 버전의 .NET Framework을 사용 하 여 컴파일된 어셈블리에 대 한 게시자 정책 어셈블리를 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1fa87-133">Another consequence is that the version 2.0 linker cannot be used to create a publisher policy assembly for an assembly compiled using earlier versions of the .NET Framework, because it always specifies processor architecture.</span></span>

## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="1fa87-134">전역 어셈블리 캐시에 게시자 정책 어셈블리 추가</span><span class="sxs-lookup"><span data-stu-id="1fa87-134">Adding the Publisher Policy Assembly to the Global Assembly Cache</span></span>

<span data-ttu-id="1fa87-135">전역 [어셈블리 캐시 도구 (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) 를 사용 하 여 전역 어셈블리 캐시에 게시자 정책 어셈블리를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fa87-135">Use the [Global Assembly Cache tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add the publisher policy assembly to the global assembly cache.</span></span>

### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="1fa87-136">전역 어셈블리 캐시에 게시자 정책 어셈블리를 추가 하려면</span><span class="sxs-lookup"><span data-stu-id="1fa87-136">To add the publisher policy assembly to the global assembly cache</span></span>

<span data-ttu-id="1fa87-137">명령 프롬프트에서 다음 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1fa87-137">Type the following command at the command prompt:</span></span>

```console
gacutil /i publisherPolicyAssemblyFile
```

<span data-ttu-id="1fa87-138">다음 명령은 `policy.1.0.myAssembly.dll` 전역 어셈블리 캐시에를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fa87-138">The following command adds `policy.1.0.myAssembly.dll` to the global assembly cache.</span></span>

```console
gacutil /i policy.1.0.myAssembly.dll
```

> [!IMPORTANT]
> <span data-ttu-id="1fa87-139">인수에 지정 된 원래 게시자 정책 파일이 `/link` 어셈블리와 동일한 디렉터리에 있는 경우가 아니면 게시자 정책 어셈블리를 전역 어셈블리 캐시에 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1fa87-139">The publisher policy assembly cannot be added to the global assembly cache unless the original publisher policy file specified in the `/link` argument is located in the same directory as the assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="1fa87-140">참조</span><span class="sxs-lookup"><span data-stu-id="1fa87-140">See also</span></span>

- [<span data-ttu-id="1fa87-141">어셈블리를 사용한 프로그래밍</span><span class="sxs-lookup"><span data-stu-id="1fa87-141">Programming with Assemblies</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="1fa87-142">런타임에서 어셈블리를 찾는 방법</span><span class="sxs-lookup"><span data-stu-id="1fa87-142">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="1fa87-143">구성 파일을 사용하여 앱 구성</span><span class="sxs-lookup"><span data-stu-id="1fa87-143">Configuring Apps by using Configuration Files</span></span>](index.md)
- [<span data-ttu-id="1fa87-144">런타임 설정 스키마</span><span class="sxs-lookup"><span data-stu-id="1fa87-144">Runtime Settings Schema</span></span>](./file-schema/runtime/index.md)
- [<span data-ttu-id="1fa87-145">구성 파일 스키마</span><span class="sxs-lookup"><span data-stu-id="1fa87-145">Configuration File Schema</span></span>](./file-schema/index.md)
- [<span data-ttu-id="1fa87-146">어셈블리 버전 리디렉션</span><span class="sxs-lookup"><span data-stu-id="1fa87-146">Redirecting Assembly Versions</span></span>](redirect-assembly-versions.md)
