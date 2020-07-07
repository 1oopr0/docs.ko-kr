---
title: 형식 라이브러리를 어셈블리로 가져오기
description: COM 형식 정의를 포함하는 형식 라이브러리를 어셈블리로 가져옵니다. 형식 라이브러리에서 메타데이터를 만들어 Interop 어셈블리가 생성되도록 하는 방법을 알아봅니다.
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- type metadata
- custom wrappers
- metadata
- exposing COM components to .NET Framework
- Type Library Importer
- interoperation with unmanaged code, importing type library
- interoperation with unmanaged code, exposing COM components
- type libraries
- TypeLibConverter class, importing type library as assembly
- COM interop, importing type library
- COM interop, exposing COM components
ms.assetid: d1898229-cd40-426e-a275-f3eb65fbc79f
ms.openlocfilehash: e5187e3c2ce533f25a38e93bc3715dd3e2e47c11
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622720"
---
# <a name="importing-a-type-library-as-an-assembly"></a><span data-ttu-id="03872-104">형식 라이브러리를 어셈블리로 가져오기</span><span class="sxs-lookup"><span data-stu-id="03872-104">Importing a Type Library as an Assembly</span></span>

<span data-ttu-id="03872-105">COM 형식 정의는 일반적으로 형식 라이브러리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03872-105">COM type definitions usually reside in a type library.</span></span> <span data-ttu-id="03872-106">반면 CLS 규격 컴파일러는 어셈블리에서 형식 메타데이터를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="03872-106">In contrast, CLS-compliant compilers produce type metadata in an assembly.</span></span> <span data-ttu-id="03872-107">형식 정보의 두 가지 소스는 약간 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="03872-107">The two sources of type information are quite different.</span></span> <span data-ttu-id="03872-108">이 항목에서는 형식 라이브러리에서 메타데이터를 생성하기 위한 기술을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="03872-108">This topic describes techniques for generating metadata from a type library.</span></span> <span data-ttu-id="03872-109">결과 어셈블리를 interop 어셈블리라고 하고 포함된 형식 정보를 통해 .NET Framework 애플리케이션이 COM 형식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03872-109">The resulting assembly is called an interop assembly, and the type information it contains enables .NET Framework applications to use COM types.</span></span>

<span data-ttu-id="03872-110">이 형식 정보를 애플리케이션에서 사용할 수 있도록 설정하는 두 가지 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03872-110">There are two ways to make this type information available to your application:</span></span>

- <span data-ttu-id="03872-111">디자인 타임 전용 interop 어셈블리 사용: .NET Framework 4부터 interop 어셈블리의 형식 정보를 실행 파일에 포함하도록 컴파일러에 지시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03872-111">Using design-time-only interop assemblies: Beginning with the .NET Framework 4, you can instruct the compiler to embed type information from the interop assembly into your executable.</span></span> <span data-ttu-id="03872-112">컴파일러는 애플리케이션에서 사용하는 형식 정보만 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="03872-112">The compiler embeds only the type information that your application uses.</span></span> <span data-ttu-id="03872-113">Interop 어셈블리를 애플리케이션에 배포할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="03872-113">You do not have to deploy the interop assembly with your application.</span></span> <span data-ttu-id="03872-114">이것이 권장되는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="03872-114">This is the recommended technique.</span></span>

- <span data-ttu-id="03872-115">interop 어셈블리 배포: interop 어셈블리에 대한 표준 참조를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03872-115">Deploying interop assemblies: You can create a standard reference to the interop assembly.</span></span> <span data-ttu-id="03872-116">이 경우 interop 어셈블리를 애플리케이션에 배포해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="03872-116">In this case, the interop assembly must be deployed with your application.</span></span> <span data-ttu-id="03872-117">이 방법을 적용하는데 전용 COM 구성 요소를 사용하지 않을 경우 관리 코드에 통합하려는 COM 구성 요소의 작성자가 게시한 PIA(주 interop 어셈블리)를 항상 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="03872-117">If you employ this technique, and you are not using a private COM component, always reference the primary interop assembly (PIA) published by the author of the COM component you intend to incorporate in your managed code.</span></span> <span data-ttu-id="03872-118">주 interop 어셈블리를 생성 및 사용하는 방법에 대한 자세한 내용은 [주 Interop 어셈블리](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100))를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="03872-118">For more information about producing and using primary interop assemblies, see [Primary Interop Assemblies](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).</span></span>

<span data-ttu-id="03872-119">디자인 타임 전용 interop 어셈블리를 사용할 경우 COM 구성 요소의 작성자가 게시한 주 interop 어셈블리의 형식 정보를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03872-119">When you use design-time-only interop assemblies, you can embed type information from the primary interop assembly published by the author of the COM component.</span></span> <span data-ttu-id="03872-120">그러나 주 interop 어셈블리를 애플리케이션에 배포할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="03872-120">However, you do not have to deploy the primary interop assembly with your application.</span></span>

<span data-ttu-id="03872-121">대부분의 애플리케이션에서는 COM 구성 요소의 일부 기능을 사용하지 않으므로 디자인 타임 전용 interop 어셈블리를 사용하면 애플리케이션 크기가 감소합니다.</span><span class="sxs-lookup"><span data-stu-id="03872-121">Using design-time-only interop assemblies reduces the size of your application, because most applications do not use all the features of a COM component.</span></span> <span data-ttu-id="03872-122">컴파일러가 형식 정보를 포함하면 매우 효율적으로 작동합니다. 애플리케이션이 COM 인터페이스에서 일부 메서드만 사용할 경우 컴파일러는 사용되지 않는 메서드를 포함하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="03872-122">The compiler is very efficient when it embeds type information; if your application uses only some of the methods on a COM interface, the compiler does not embed the unused methods.</span></span> <span data-ttu-id="03872-123">형식 정보가 포함된 애플리케이션이 이와 같은 다른 애플리케이션과 상호 작용하거나 주 interop 어셈블리를 사용하는 애플리케이션과 상호 작용하면 공용 언어 런타임은 형식 동등성 규칙을 사용하여 같은 이름의 두 가지 형식이 동일한 COM 형식을 나타내는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="03872-123">When an application that has embedded type information interacts with another such application, or interacts with an application that uses a primary interop assembly, the common language runtime uses type equivalence rules to determine whether two types with the same name represent the same COM type.</span></span> <span data-ttu-id="03872-124">COM 개체를 사용하기 위해 이러한 규칙을 알 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="03872-124">You do not have to know these rules to use COM objects.</span></span> <span data-ttu-id="03872-125">그러나 규칙에 관심이 있다면 [형식 동등성 및 포함된 Interop 형식](type-equivalence-and-embedded-interop-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="03872-125">However, if you are interested in the rules, see [Type Equivalence and Embedded Interop Types](type-equivalence-and-embedded-interop-types.md).</span></span>

## <a name="generating-metadata"></a><span data-ttu-id="03872-126">메타데이터 생성</span><span class="sxs-lookup"><span data-stu-id="03872-126">Generating Metadata</span></span>

<span data-ttu-id="03872-127">COM 형식 라이브러리는 확장명이 .tlb인 독립 실행형 파일일 수 있습니다(예: Loanlib.tlb).</span><span class="sxs-lookup"><span data-stu-id="03872-127">COM type libraries can be stand-alone files that have a .tlb extension, such as Loanlib.tlb.</span></span> <span data-ttu-id="03872-128">일부 형식 라이브러리는 .dll 또는 .exe 파일의 리소스 섹션에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="03872-128">Some type libraries are embedded in the resource section of a .dll or .exe file.</span></span> <span data-ttu-id="03872-129">형식 라이브러리 정보의 기타 소스는 .olb 및 .ocx 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="03872-129">Other sources of type library information are .olb and .ocx files.</span></span>

<span data-ttu-id="03872-130">대상 COM 형식의 구현이 포함된 형식 라이브러리를 찾은 후 다음 옵션을 사용하여 형식 메타데이터가 포함된 interop 어셈블리를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="03872-130">After you locate the type library that contains the implementation of your target COM type, you have the following options for generating an interop assembly containing type metadata:</span></span>

- <span data-ttu-id="03872-131">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="03872-131">Visual Studio</span></span>

  <span data-ttu-id="03872-132">Visual Studio는 형식 라이브러리의 COM 형식을 어셈블리의 메타데이터로 자동으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="03872-132">Visual Studio automatically converts COM types in a type library to metadata in an assembly.</span></span> <span data-ttu-id="03872-133">자세한 내용은 [방법: 형식 라이브러리에 참조 추가](how-to-add-references-to-type-libraries.md).</span><span class="sxs-lookup"><span data-stu-id="03872-133">For instructions, see [How to: Add References to Type Libraries](how-to-add-references-to-type-libraries.md).</span></span>

- [<span data-ttu-id="03872-134">형식 라이브러리 가져오기(Tlbimp.exe)</span><span class="sxs-lookup"><span data-stu-id="03872-134">Type Library Importer (Tlbimp.exe)</span></span>](../tools/tlbimp-exe-type-library-importer.md)

  <span data-ttu-id="03872-135">형식 라이브러리 가져오기는 결과 interop 파일에서 메타데이터를 조정하고, 기존 형식 라이브러리에서 형식을 가져오고, interop 어셈블리 및 네임스페이스를 생성하기 위한 명령줄 옵션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="03872-135">The Type Library Importer provides command-line options to adjust metadata in the resulting interop file, imports types from an existing type library, and generates an interop assembly and a namespace.</span></span> <span data-ttu-id="03872-136">자세한 내용은 [방법: 형식 라이브러리에서 Interop 어셈블리 생성](how-to-generate-interop-assemblies-from-type-libraries.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="03872-136">For instructions, see [How to: Generate Interop Assemblies from Type Libraries](how-to-generate-interop-assemblies-from-type-libraries.md).</span></span>

- <span data-ttu-id="03872-137"><xref:System.Runtime.InteropServices.TypeLibConverter?displayProperty=nameWithType> 클래스</span><span class="sxs-lookup"><span data-stu-id="03872-137"><xref:System.Runtime.InteropServices.TypeLibConverter?displayProperty=nameWithType> class</span></span>

  <span data-ttu-id="03872-138">이 클래스는 형식 라이브러리의 coclass 및 인터페이스를 어셈블리 내의 메타데이터로 변환하기 위한 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="03872-138">This class provides methods to convert coclasses and interfaces in a type library to metadata within an assembly.</span></span> <span data-ttu-id="03872-139">이 클래스는 Tlbimp.exe와 동일한 메타데이터 출력을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="03872-139">It produces the same metadata output as Tlbimp.exe.</span></span> <span data-ttu-id="03872-140">그러나 Tlbimp.exe와 달리 <xref:System.Runtime.InteropServices.TypeLibConverter> 클래스는 메모리 내 형식 라이브러리를 메타데이터로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03872-140">However, unlike Tlbimp.exe, the <xref:System.Runtime.InteropServices.TypeLibConverter> class can convert an in-memory type library to metadata.</span></span>

- <span data-ttu-id="03872-141">사용자 지정 래퍼</span><span class="sxs-lookup"><span data-stu-id="03872-141">Custom wrappers</span></span>

  <span data-ttu-id="03872-142">형식 라이브러리가 사용 불가능하거나 잘못된 경우 한 가지 옵션은 관리 소스 코드에서 클래스 또는 인터페이스에 대한 중복 정의를 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="03872-142">When a type library is unavailable or incorrect, one option is to create a duplicate definition of the class or interface in managed source code.</span></span> <span data-ttu-id="03872-143">그런 다음 런타임을 대상으로 하는 컴파일러로 소스 코드를 컴파일하여 어셈블리에서 메타데이터를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="03872-143">You then compile the source code with a compiler that targets the runtime to produce metadata in an assembly.</span></span>

  <span data-ttu-id="03872-144">COM 형식을 수동으로 정의하려면 다음 항목에 액세스할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="03872-144">To define COM types manually, you must have access to the following items:</span></span>

  - <span data-ttu-id="03872-145">정의되는 coclass 및 인터페이스에 대한 자세한 설명.</span><span class="sxs-lookup"><span data-stu-id="03872-145">Precise descriptions of the coclasses and interfaces being defined.</span></span>

  - <span data-ttu-id="03872-146">해당하는 .NET Framework 클래스 정의를 생성할 수 있는 컴파일러(예: C# 컴파일러).</span><span class="sxs-lookup"><span data-stu-id="03872-146">A compiler, such as the C# compiler, that can generate the appropriate .NET Framework class definitions.</span></span>

  - <span data-ttu-id="03872-147">형식 라이브러리-어셈블리 변환 규칙에 대한 이해.</span><span class="sxs-lookup"><span data-stu-id="03872-147">Knowledge of the type library-to-assembly conversion rules.</span></span>

  <span data-ttu-id="03872-148">사용자 지정 래퍼를 작성하는 것은 고급 기술입니다.</span><span class="sxs-lookup"><span data-stu-id="03872-148">Writing a custom wrapper is an advanced technique.</span></span> <span data-ttu-id="03872-149">사용자 지정 래퍼를 생성하는 방법에 대한 자세한 내용은 [표준 래퍼 사용자 지정](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="03872-149">For additional information about how to generate a custom wrapper, see [Customizing Standard Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100)).</span></span>

 <span data-ttu-id="03872-150">COM interop 가져오기 프로세스에 대한 자세한 내용은 [형식 라이브러리를 어셈블리로 변환 요약](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="03872-150">For more information about the COM interop import process, see [Type Library to Assembly Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100)).</span></span>

## <a name="see-also"></a><span data-ttu-id="03872-151">참조</span><span class="sxs-lookup"><span data-stu-id="03872-151">See also</span></span>

- <xref:System.Runtime.InteropServices.TypeLibConverter>
- [<span data-ttu-id="03872-152">.NET Framework에 COM 구성 요소 노출</span><span class="sxs-lookup"><span data-stu-id="03872-152">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
- <span data-ttu-id="03872-153">[형식 라이브러리를 어셈블리로 변환 요약](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="03872-153">[Type Library to Assembly Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span></span>
- [<span data-ttu-id="03872-154">Tlbimp.exe(형식 라이브러리 가져오기)</span><span class="sxs-lookup"><span data-stu-id="03872-154">Tlbimp.exe (Type Library Importer)</span></span>](../tools/tlbimp-exe-type-library-importer.md)
- <span data-ttu-id="03872-155">[표준 래퍼 사용자 지정](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="03872-155">[Customizing Standard Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))</span></span>
- <span data-ttu-id="03872-156">[관리 코드에서 COM 형식 사용](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="03872-156">[Using COM Types in Managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span></span>
- [<span data-ttu-id="03872-157">Interop 프로젝트 컴파일</span><span class="sxs-lookup"><span data-stu-id="03872-157">Compiling an Interop Project</span></span>](compiling-an-interop-project.md)
- [<span data-ttu-id="03872-158">Interop 애플리케이션 배포</span><span class="sxs-lookup"><span data-stu-id="03872-158">Deploying an Interop Application</span></span>](deploying-an-interop-application.md)
- [<span data-ttu-id="03872-159">방법: 형식 라이브러리에 참조 추가</span><span class="sxs-lookup"><span data-stu-id="03872-159">How to: Add References to Type Libraries</span></span>](how-to-add-references-to-type-libraries.md)
- [<span data-ttu-id="03872-160">방법: 형식 라이브러리에서 Interop 어셈블리 생성</span><span class="sxs-lookup"><span data-stu-id="03872-160">How to: Generate Interop Assemblies from Type Libraries</span></span>](how-to-generate-interop-assemblies-from-type-libraries.md)
