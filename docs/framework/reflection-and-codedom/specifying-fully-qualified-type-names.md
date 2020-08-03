---
title: 정규화된 형식 이름 지정
description: 리플렉션 작업을 올바르게 입력하기 위해 어셈블리 이름 사양, 네임스페이스 사양 및 형식 이름이 있는 정규화된 형식 이름을 사용하세요.
ms.date: 02/21/2019
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- reflection, fully qualified type names
- names [.NET Framework], assemblies
- tokens
- BNF
- assemblies [.NET Framework], names
- languages, grammar
- fully qualified type names
- type names
- special characters
- IDENTIFIER
ms.assetid: d90b1e39-9115-4f2a-81c0-05e7e74e5580
ms.openlocfilehash: ff33b6abd31a82c6b80aa794564c5c48648cde63
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865231"
---
# <a name="specifying-fully-qualified-type-names"></a><span data-ttu-id="00dcf-103">정규화된 형식 이름 지정</span><span class="sxs-lookup"><span data-stu-id="00dcf-103">Specifying fully qualified type names</span></span>

<span data-ttu-id="00dcf-104">다양한 리플렉션 작업에 대한 유효한 입력을 포함하려면 형식 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-104">You must specify type names to have valid input to various reflection operations.</span></span> <span data-ttu-id="00dcf-105">정규화된 형식 이름은 어셈블리 이름 사양, 네임스페이스 사양, 형식 이름으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-105">A fully qualified type name consists of an assembly name specification, a namespace specification, and a type name.</span></span> <span data-ttu-id="00dcf-106">형식 이름 사양은 <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> 등의 메서드에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-106">Type name specifications are used by methods such as <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>, and <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.</span></span>

## <a name="grammar-for-type-names"></a><span data-ttu-id="00dcf-107">형식 이름의 문법</span><span class="sxs-lookup"><span data-stu-id="00dcf-107">Grammar for type names</span></span>

 <span data-ttu-id="00dcf-108">문법은 공식 언어의 구문을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-108">The grammar defines the syntax of formal languages.</span></span> <span data-ttu-id="00dcf-109">다음 표에서는 유효한 입력을 인식하는 방법을 설명하는 어휘 규칙을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-109">The following table lists lexical rules that describe how to recognize a valid input.</span></span> <span data-ttu-id="00dcf-110">터미널(더 이상 줄일 수 없는 요소)은 모두 대문자로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-110">Terminals (those elements that are not further reducible) are shown in all uppercase letters.</span></span> <span data-ttu-id="00dcf-111">비터미널(더 줄일 수 있는 요소)은 대/소문자가 혼합되어 있거나 작은따옴표가 붙은 문자열로 표시되지만 작은따옴표(')는 구문 자체에 속하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-111">Nonterminals (those elements that are further reducible) are shown in mixed-case or singly quoted strings, but the single quote (') is not a part of the syntax itself.</span></span> <span data-ttu-id="00dcf-112">파이프 문자(&#124;)는 하위 규칙이 있는 규칙을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-112">The pipe character (&#124;) denotes rules that have subrules.</span></span>

<!-- markdownlint-disable MD010 -->
```antlr
TypeSpec
    : ReferenceTypeSpec
    | SimpleTypeSpec
    ;

ReferenceTypeSpec
    : SimpleTypeSpec '&'
    ;

SimpleTypeSpec
    : PointerTypeSpec
    | GenericTypeSpec
    | TypeName
    ;

GenericTypeSpec
   : SimpleTypeSpec ` NUMBER

PointerTypeSpec
    : SimpleTypeSpec '*'
    ;

ArrayTypeSpec
    : SimpleTypeSpec '[ReflectionDimension]'
    | SimpleTypeSpec '[ReflectionEmitDimension]'
    ;

ReflectionDimension
    : '*'
    | ReflectionDimension ',' ReflectionDimension
    | NOTOKEN
    ;

ReflectionEmitDimension
    : '*'
    | Number '..' Number
    | Number '…'
    | ReflectionDimension ',' ReflectionDimension
    | NOTOKEN
    ;

Number
    : [0-9]+
    ;

TypeName
    : NamespaceTypeName
    | NamespaceTypeName ',' AssemblyNameSpec
    ;

NamespaceTypeName
    : NestedTypeName
    | NamespaceSpec '.' NestedTypeName
    ;

NestedTypeName
    : IDENTIFIER
    | NestedTypeName '+' IDENTIFIER
    ;

NamespaceSpec
    : IDENTIFIER
    | NamespaceSpec '.' IDENTIFIER
    ;

AssemblyNameSpec
    : IDENTIFIER
    | IDENTIFIER ',' AssemblyProperties
    ;

AssemblyProperties
    : AssemblyProperty
    | AssemblyProperties ',' AssemblyProperty
    ;

AssemblyProperty
    : AssemblyPropertyName '=' AssemblyPropertyValue
    ;
```
<!-- markdownlint-enable MD010 -->

## <a name="specifying-special-characters"></a><span data-ttu-id="00dcf-113">특수 문자 지정</span><span class="sxs-lookup"><span data-stu-id="00dcf-113">Specifying special characters</span></span>

<span data-ttu-id="00dcf-114">형식 이름에서 IDENTIFIER는 언어의 규칙에 따라 결정된 유효한 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-114">In a type name, IDENTIFIER is any valid name determined by the rules of a language.</span></span>

<span data-ttu-id="00dcf-115">백슬래시(\\)를 이스케이프 문자로 사용하여 IDENTIFIER의 일부로 사용된 다음 토큰을 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-115">Use the backslash (\\) as an escape character to separate the following tokens when used as part of IDENTIFIER.</span></span>

|<span data-ttu-id="00dcf-116">토큰</span><span class="sxs-lookup"><span data-stu-id="00dcf-116">Token</span></span>|<span data-ttu-id="00dcf-117">의미</span><span class="sxs-lookup"><span data-stu-id="00dcf-117">Meaning</span></span>|
|-----------|-------------|
|<span data-ttu-id="00dcf-118">\\,</span><span class="sxs-lookup"><span data-stu-id="00dcf-118">\\,</span></span>|<span data-ttu-id="00dcf-119">어셈블리 구분 기호.</span><span class="sxs-lookup"><span data-stu-id="00dcf-119">Assembly separator.</span></span>|
|\\+|<span data-ttu-id="00dcf-120">중첩된 형식 구분 기호.</span><span class="sxs-lookup"><span data-stu-id="00dcf-120">Nested type separator.</span></span>|
|\\&|<span data-ttu-id="00dcf-121">참조 형식.</span><span class="sxs-lookup"><span data-stu-id="00dcf-121">Reference type.</span></span>|
|\\*|<span data-ttu-id="00dcf-122">포인터 형식.</span><span class="sxs-lookup"><span data-stu-id="00dcf-122">Pointer type.</span></span>|
|<span data-ttu-id="00dcf-123">\\[</span><span class="sxs-lookup"><span data-stu-id="00dcf-123">\\[</span></span>|<span data-ttu-id="00dcf-124">배열 차원 구분 기호.</span><span class="sxs-lookup"><span data-stu-id="00dcf-124">Array dimension delimiter.</span></span>|
|<span data-ttu-id="00dcf-125">\\]</span><span class="sxs-lookup"><span data-stu-id="00dcf-125">\\]</span></span>|<span data-ttu-id="00dcf-126">배열 차원 구분 기호.</span><span class="sxs-lookup"><span data-stu-id="00dcf-126">Array dimension delimiter.</span></span>|
|<span data-ttu-id="00dcf-127">\\.</span><span class="sxs-lookup"><span data-stu-id="00dcf-127">\\.</span></span>|<span data-ttu-id="00dcf-128">배열 사양에서 마침표가 사용된 경우에만 마침표 앞에 백슬래시를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-128">Use the backslash before a period only if the period is used in an array specification.</span></span> <span data-ttu-id="00dcf-129">NamespaceSpec의 마침표는 백슬래시를 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-129">Periods in NamespaceSpec do not take the backslash.</span></span>|
|<span data-ttu-id="00dcf-130">\\\|필요한 경우 백슬래시를 문자열 리터럴로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-130">\\\|Backslash when needed as a string literal.</span></span>|

<span data-ttu-id="00dcf-131">AssemblyNameSpec을 제외한 모든 TypeSpec 구성 요소에서 공백은 관련이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-131">Note that in all TypeSpec components except AssemblyNameSpec, spaces are relevant.</span></span> <span data-ttu-id="00dcf-132">AssemblyNameSpec에서는 ',' 구분 기호 앞의 공백은 관련이 있지만 ',' 구분 기호 뒤의 공백은 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-132">In the AssemblyNameSpec, spaces before the ',' separator are relevant, but spaces after the ',' separator are ignored.</span></span>

<span data-ttu-id="00dcf-133"><xref:System.Type.FullName%2A?displayProperty=nameWithType> 등의 리플렉션 클래스는 `MyType.GetType(myType.FullName)`과 같이 반환된 이름을 <xref:System.Type.GetType%2A> 호출에 사용할 수 있도록 바뀐 이름을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-133">Reflection classes, such as <xref:System.Type.FullName%2A?displayProperty=nameWithType>, return the mangled name so that the returned name can be used in a call to <xref:System.Type.GetType%2A>, as in `MyType.GetType(myType.FullName)`.</span></span>

<span data-ttu-id="00dcf-134">예를 들어 형식의 정규화된 이름이 `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-134">For example, the fully qualified name for a type might be `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.</span></span>

<span data-ttu-id="00dcf-135">네임스페이스가 `Ozzy.Out+Back`이면 더하기 기호 앞에 백슬래시가 와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-135">If the namespace were `Ozzy.Out+Back`, then the plus sign must be preceded by a backslash.</span></span> <span data-ttu-id="00dcf-136">그렇지 않으면 파서가 중첩 구분 기호로 해석합니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-136">Otherwise, the parser would interpret it as a nesting separator.</span></span> <span data-ttu-id="00dcf-137">리플렉션은 이 문자열을 `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-137">Reflection emits this string as `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.</span></span>

## <a name="specifying-assembly-names"></a><span data-ttu-id="00dcf-138">어셈블리 이름 지정</span><span class="sxs-lookup"><span data-stu-id="00dcf-138">Specifying assembly names</span></span>

<span data-ttu-id="00dcf-139">어셈블리 이름 사양에 필요한 최소 정보는 어셈블리의 텍스트 이름(IDENTIFIER)입니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-139">The minimum information required in an assembly name specification is the textual name (IDENTIFIER) of the assembly.</span></span> <span data-ttu-id="00dcf-140">다음 표에 설명된 대로 속성/값 쌍의 쉼표로 구분된 목록이 IDENTIFIER 뒤에 와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-140">You can follow the IDENTIFIER by a comma-separated list of property/value pairs as described in the following table.</span></span> <span data-ttu-id="00dcf-141">IDENTIFIER 이름 지정은 파일 이름 지정 규칙을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-141">IDENTIFIER naming should follow the rules for file naming.</span></span> <span data-ttu-id="00dcf-142">IDENTIFIER는 대/소문자를 구분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-142">The IDENTIFIER is case-insensitive.</span></span>

|<span data-ttu-id="00dcf-143">속성 이름</span><span class="sxs-lookup"><span data-stu-id="00dcf-143">Property name</span></span>|<span data-ttu-id="00dcf-144">설명</span><span class="sxs-lookup"><span data-stu-id="00dcf-144">Description</span></span>|<span data-ttu-id="00dcf-145">허용 가능한 값</span><span class="sxs-lookup"><span data-stu-id="00dcf-145">Allowable values</span></span>|
|-------------------|-----------------|----------------------|
|<span data-ttu-id="00dcf-146">**버전**</span><span class="sxs-lookup"><span data-stu-id="00dcf-146">**Version**</span></span>|<span data-ttu-id="00dcf-147">어셈블리 버전 번호</span><span class="sxs-lookup"><span data-stu-id="00dcf-147">Assembly version number</span></span>|<span data-ttu-id="00dcf-148">*Major.Minor.Build.Revision*. 여기서 *Major*, *Minor*, *Build*, *Revision*은 0에서 65535 사이의 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-148">*Major.Minor.Build.Revision*, where *Major*, *Minor*, *Build*, and *Revision* are integers between 0 and 65535 inclusive.</span></span>|
|<span data-ttu-id="00dcf-149">**PublicKey**</span><span class="sxs-lookup"><span data-stu-id="00dcf-149">**PublicKey**</span></span>|<span data-ttu-id="00dcf-150">전체 공개 키</span><span class="sxs-lookup"><span data-stu-id="00dcf-150">Full public key</span></span>|<span data-ttu-id="00dcf-151">16진수 형식인 전체 공개 키의 문자열 값입니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-151">String value of full public key in hexadecimal format.</span></span> <span data-ttu-id="00dcf-152">null 참조(Visual Basic에서는 **Nothing**)를 지정하여 프라이빗 어셈블리를 명시적으로 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-152">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|
|<span data-ttu-id="00dcf-153">**PublicKeyToken**</span><span class="sxs-lookup"><span data-stu-id="00dcf-153">**PublicKeyToken**</span></span>|<span data-ttu-id="00dcf-154">공개 키 토큰(전체 공개 키의 8바이트 해시)</span><span class="sxs-lookup"><span data-stu-id="00dcf-154">Public key token (8-byte hash of the full public key)</span></span>|<span data-ttu-id="00dcf-155">16진수 형식인 공개 키 토큰의 문자열 값입니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-155">String value of public key token in hexadecimal format.</span></span> <span data-ttu-id="00dcf-156">null 참조(Visual Basic에서는 **Nothing**)를 지정하여 프라이빗 어셈블리를 명시적으로 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-156">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|
|<span data-ttu-id="00dcf-157">**문화권**</span><span class="sxs-lookup"><span data-stu-id="00dcf-157">**Culture**</span></span>|<span data-ttu-id="00dcf-158">어셈블리 문화권</span><span class="sxs-lookup"><span data-stu-id="00dcf-158">Assembly culture</span></span>|<span data-ttu-id="00dcf-159">RFC-1766 형식의 어셈블리 문화권 또는 언어 독립적인(비위성) 어셈블리의 경우 "중립"입니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-159">Culture of the assembly in RFC-1766 format, or "neutral" for language-independent (nonsatellite) assemblies.</span></span>|
|<span data-ttu-id="00dcf-160">**사용자 지정**</span><span class="sxs-lookup"><span data-stu-id="00dcf-160">**Custom**</span></span>|<span data-ttu-id="00dcf-161">사용자 지정 BLOB(Binary Large Object)입니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-161">Custom binary large object (BLOB).</span></span> <span data-ttu-id="00dcf-162">현재 [네이티브 이미지 생성기(Ngen)](../tools/ngen-exe-native-image-generator.md)에서 생성된 어셈블리에서만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-162">This is currently used only in assemblies generated by the [Native Image Generator (Ngen)](../tools/ngen-exe-native-image-generator.md).</span></span>|<span data-ttu-id="00dcf-163">설치되는 어셈블리가 네이티브 이미지이므로 네이티브 이미지 캐시에 설치해야 함을 어셈블리 캐시에 알리기 위해 네이티브 이미지 생성기 도구에서 사용하는 사용자 지정 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-163">Custom string used by the Native Image Generator tool to notify the assembly cache that the assembly being installed is a native image, and is therefore to be installed in the native image cache.</span></span> <span data-ttu-id="00dcf-164">zap 문자열이라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-164">Also called a zap string.</span></span>|

<span data-ttu-id="00dcf-165">다음 예제에서는 기본 문화권을 사용하는 단순한 이름의 어셈블리에 대한 **AssemblyName**을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-165">The following example shows an **AssemblyName** for a simply named assembly with default culture.</span></span>

```csharp
com.microsoft.crypto, Culture=""
```

<span data-ttu-id="00dcf-166">다음 예제에서는 문화권 "en"을 사용하는 강력한 이름의 어셈블리에 대한 완전히 지정된 참조를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-166">The following example shows a fully specified reference for a strongly named assembly with culture "en".</span></span>

```csharp
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,
    Version=1.0.0.0
```

<span data-ttu-id="00dcf-167">다음 예제에서는 각각 강력한 이름 또는 단순한 이름의 어셈블리에 의해 충족될 수 있는 부분적으로 지정된 **AssemblyName**을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-167">The following examples each show a partially specified **AssemblyName**, which can be satisfied by either a strong or a simply named assembly.</span></span>

```csharp
com.microsoft.crypto
com.microsoft.crypto, Culture=""
com.microsoft.crypto, Culture=en
```

<span data-ttu-id="00dcf-168">다음 예제에서는 각각 단순한 이름의 어셈블리에 의해 충족되어야 하는 부분적으로 지정된 **AssemblyName**을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-168">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a simply named assembly.</span></span>

```csharp
com.microsoft.crypto, Culture="", PublicKeyToken=null
com.microsoft.crypto, Culture=en, PublicKeyToken=null
```

<span data-ttu-id="00dcf-169">다음 예제에서는 각각 강력한 이름의 어셈블리에 의해 충족되어야 하는 부분적으로 지정된 **AssemblyName**을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-169">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a strongly named assembly.</span></span>

```csharp
com.microsoft.crypto, Culture="", PublicKeyToken=a5d015c7d5a0b012
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,
    Version=1.0.0.0
```

## <a name="specifying-generic-types"></a><span data-ttu-id="00dcf-170">제네릭 형식 지정</span><span class="sxs-lookup"><span data-stu-id="00dcf-170">Specifying generic types</span></span>

<span data-ttu-id="00dcf-171">SimpleTypeSpec\`NUMBER는 1부터 *n*까지의 제네릭 형식 매개 변수를 갖는 개방형 제네릭 형식을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-171">SimpleTypeSpec\`NUMBER represents an open generic type with from 1 to *n* generic type parameters.</span></span> <span data-ttu-id="00dcf-172">예를 들어, 개방형 제네릭 형식 List\<T> 또는 폐쇄형 제네릭 형식 List\<String>의 참조를 가져오려면 ``Type.GetType("System.Collections.Generic.List`1")``을 사용합니다. 제네릭 형식 Dictionary\<TKey,TValue>의 참조를 가져오려면 ``Type.GetType("System.Collections.Generic.Dictionary`2")``을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-172">For example, to get reference to the open generic type List\<T> or the closed generic type List\<String>, use ``Type.GetType("System.Collections.Generic.List`1")`` To get a reference to the generic type Dictionary\<TKey,TValue>, use ``Type.GetType("System.Collections.Generic.Dictionary`2")``.</span></span>

## <a name="specifying-pointers"></a><span data-ttu-id="00dcf-173">포인터 지정</span><span class="sxs-lookup"><span data-stu-id="00dcf-173">Specifying pointers</span></span>

<span data-ttu-id="00dcf-174">SimpleTypeSpec\*는 관리되지 않는 포인터를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-174">SimpleTypeSpec\* represents an unmanaged pointer.</span></span> <span data-ttu-id="00dcf-175">예를 들어 MyType 형식에 대한 포인터를 가져오려면 `Type.GetType("MyType*")`을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-175">For example, to get a pointer to type MyType, use `Type.GetType("MyType*")`.</span></span> <span data-ttu-id="00dcf-176">MyType 형식에 대한 포인터의 포인터를 가져오려면 `Type.GetType("MyType**")`을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-176">To get a pointer to a pointer to type MyType, use `Type.GetType("MyType**")`.</span></span>

## <a name="specifying-references"></a><span data-ttu-id="00dcf-177">참조 지정</span><span class="sxs-lookup"><span data-stu-id="00dcf-177">Specifying references</span></span>

<span data-ttu-id="00dcf-178">SimpleTypeSpec &은 관리되는 포인터나 참조를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-178">SimpleTypeSpec & represents a managed pointer or reference.</span></span> <span data-ttu-id="00dcf-179">예를 들어 MyType 형식에 대한 참조를 가져오려면 `Type.GetType("MyType &")`을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-179">For example, to get a reference to type MyType, use `Type.GetType("MyType &")`.</span></span> <span data-ttu-id="00dcf-180">포인터와 달리 참조는 한 수준으로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-180">Note that unlike pointers, references are limited to one level.</span></span>

## <a name="specifying-arrays"></a><span data-ttu-id="00dcf-181">배열 지정</span><span class="sxs-lookup"><span data-stu-id="00dcf-181">Specifying arrays</span></span>

<span data-ttu-id="00dcf-182">BNF 문법에서 ReflectionEmitDimension은 <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>을 사용하여 검색된 불완전한 형식 정의에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-182">In the BNF Grammar, ReflectionEmitDimension only applies to incomplete type definitions retrieved using <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="00dcf-183">불완전한 형식 정의는 <xref:System.Reflection.Emit?displayProperty=nameWithType>을 사용하여 생성되었지만 <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType>이 호출되지 않은 <xref:System.Reflection.Emit.TypeBuilder> 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-183">Incomplete type definitions are <xref:System.Reflection.Emit.TypeBuilder> objects constructed using <xref:System.Reflection.Emit?displayProperty=nameWithType> but on which <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> has not been called.</span></span> <span data-ttu-id="00dcf-184">ReflectionDimension을 사용하여 완성된 형식 정의, 즉 로드된 형식을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-184">ReflectionDimension can be used to retrieve any type definition that has been completed, that is, a type that has been loaded.</span></span>

<span data-ttu-id="00dcf-185">배열은 배열의 순위를 지정하여 리플렉션에서 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-185">Arrays are accessed in reflection by specifying the rank of the array:</span></span>

- <span data-ttu-id="00dcf-186">`Type.GetType("MyArray[]")`은 하한이 0인 1차원 배열을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-186">`Type.GetType("MyArray[]")` gets a single-dimension array with 0 lower bound.</span></span>

- <span data-ttu-id="00dcf-187">`Type.GetType("MyArray[*]")`은 하한을 알 수 없는 1차원 배열을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-187">`Type.GetType("MyArray[*]")` gets a single-dimension array with unknown lower bound.</span></span>
- <span data-ttu-id="00dcf-188">`Type.GetType("MyArray[][]")`은 2차원 배열의 배열을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-188">`Type.GetType("MyArray[][]")` gets a two-dimensional array's array.</span></span>

- <span data-ttu-id="00dcf-189">`Type.GetType("MyArray[*,*]")` 및 `Type.GetType("MyArray[,]")`은 하한을 알 수 없는 사각형 2차원 배열을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-189">`Type.GetType("MyArray[*,*]")` and `Type.GetType("MyArray[,]")` gets a rectangular two-dimensional array with unknown lower bounds.</span></span>

<span data-ttu-id="00dcf-190">런타임 관점에서는 `MyArray[] != MyArray[*]`이지만, 다차원 배열에서는 두 표기법이 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-190">Note that from a runtime point of view, `MyArray[] != MyArray[*]`, but for multidimensional arrays, the two notations are equivalent.</span></span> <span data-ttu-id="00dcf-191">즉, `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")`은 **true**입니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-191">That is, `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` evaluates to **true**.</span></span>

<span data-ttu-id="00dcf-192">**ModuleBuilder.GetType**의 경우 `MyArray[0..5]`는 크기가 6, 하한이 0인 1차원 배열을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-192">For **ModuleBuilder.GetType**, `MyArray[0..5]` indicates a single-dimension array with size 6, lower bound 0.</span></span> <span data-ttu-id="00dcf-193">`MyArray[4…]`는 크기를 알 수 없고 하한이 4인 1차원 배열을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="00dcf-193">`MyArray[4…]` indicates a single-dimension array of unknown size and lower bound 4.</span></span>

## <a name="see-also"></a><span data-ttu-id="00dcf-194">참조</span><span class="sxs-lookup"><span data-stu-id="00dcf-194">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- <xref:System.Reflection.Emit.ModuleBuilder>
- <xref:System.Reflection.Emit.TypeBuilder>
- <xref:System.Type.FullName%2A?displayProperty=nameWithType>
- <xref:System.Type.GetType%2A?displayProperty=nameWithType>
- <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>
- [<span data-ttu-id="00dcf-195">형식 정보 보기</span><span class="sxs-lookup"><span data-stu-id="00dcf-195">Viewing Type Information</span></span>](viewing-type-information.md)
