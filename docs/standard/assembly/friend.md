---
title: Friend 어셈블리
description: Friend 어셈블리는 다른 어셈블리의 내부(C#) 또는 Friend(Visual Basic) 형식 및 멤버에 액세스할 수 있는 .NET 어셈블리입니다.
ms.date: 08/20/2019
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
dev_langs:
- csharp
- vb
ms.openlocfilehash: 105621da2bd418c6294fa2bbec474809599cb6a5
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378929"
---
# <a name="friend-assemblies"></a><span data-ttu-id="4fa98-103">Friend 어셈블리</span><span class="sxs-lookup"><span data-stu-id="4fa98-103">Friend assemblies</span></span>

<span data-ttu-id="4fa98-104">*friend 어셈블리*는 다른 어셈블리의 [내부](../../csharp/language-reference/keywords/internal.md)(C#) 또는 [Friend](../../visual-basic/language-reference/modifiers/friend.md)(Visual Basic) 형식 및 멤버에 액세스할 수 있는 어셈블리입니다.</span><span class="sxs-lookup"><span data-stu-id="4fa98-104">A *friend assembly* is an assembly that can access another assembly's [internal](../../csharp/language-reference/keywords/internal.md) (C#) or [Friend](../../visual-basic/language-reference/modifiers/friend.md) (Visual Basic) types and members.</span></span> <span data-ttu-id="4fa98-105">어셈블리를 friend 어셈블리로 식별하는 경우 다른 어셈블리에서 액세스할 수 있도록 하기 위해 더 이상 형식 및 멤버를 public으로 표시할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4fa98-105">If you identify an assembly as a friend assembly, you no longer have to mark types and members as public in order for them to be accessed by other assemblies.</span></span> <span data-ttu-id="4fa98-106">다음과 같은 시나리오에서 특히 편리합니다.</span><span class="sxs-lookup"><span data-stu-id="4fa98-106">This is especially convenient in the following scenarios:</span></span>

- <span data-ttu-id="4fa98-107">유닛 테스트 중 테스트 코드는 별도의 어셈블리에서 실행되지만 테스트 중인 어셈블리에서 `internal`(C#) 또는 `Friend`(Visual Basic)로 표시된 멤버에 액세스해야 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="4fa98-107">During unit testing, when test code runs in a separate assembly but requires access to members in the assembly being tested that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

- <span data-ttu-id="4fa98-108">클래스 라이브러리를 개발하고 있고 라이브러리에 대한 추가 사항이 별도의 어셈블리에 포함되어 있지만, 기존 어셈블리에서 `internal`(C#) 또는 `Friend`(Visual Basic)으로 표시된 멤버에 액세스해야 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="4fa98-108">When you are developing a class library and additions to the library are contained in separate assemblies but require access to members in existing assemblies that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

## <a name="remarks"></a><span data-ttu-id="4fa98-109">설명</span><span class="sxs-lookup"><span data-stu-id="4fa98-109">Remarks</span></span>

<span data-ttu-id="4fa98-110"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 특성을 사용하여 지정된 어셈블리에 대해 하나 이상의 friend 어셈블리를 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fa98-110">You can use the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to identify one or more friend assemblies for a given assembly.</span></span> <span data-ttu-id="4fa98-111">다음 예제에서는 *어셈블리 A*에서 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 특성을 사용하고 *어셈블리 B* 어셈블리를 friend 어셈블리로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4fa98-111">The following example uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute in *Assembly A* and specifies assembly *AssemblyB* as a friend assembly.</span></span> <span data-ttu-id="4fa98-112">그러면 *어셈블리 B* 어셈블리가 *어셈블리 A*에서 `internal`(C#) 또는 `Friend`(Visual Basic)로 표시된 모든 형식 및 멤버에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fa98-112">This gives assembly *AssemblyB* access to all types and members in *Assembly A* that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

> [!NOTE]
> <span data-ttu-id="4fa98-113">‘어셈블리 A’와 같은 다른 어셈블리의 내부 형식이나 내부 멤버에 액세스하는 ‘어셈블리 B’와 같은 어셈블리를 컴파일하는 경우 **-out** 컴파일러 옵션을 사용하여 출력 파일( *.exe* 또는 *.dll*)의 이름을 명시적으로 지정해야 합니다. </span><span class="sxs-lookup"><span data-stu-id="4fa98-113">When you compile an assembly like *AssemblyB* that will access internal types or internal members of another assembly like *Assembly A*, you must explicitly specify the name of the output file (*.exe* or *.dll*) by using the **-out** compiler option.</span></span> <span data-ttu-id="4fa98-114">컴파일러가 외부 참조에 바인딩할 때 작성하고 있는 어셈블리에 대해 이름을 생성하지 않았기 때문에 이 과정이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="4fa98-114">This is required because the compiler has not yet generated the name for the assembly it is building at the time it is binding to external references.</span></span> <span data-ttu-id="4fa98-115">자세한 내용은 [-out(C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) 또는 [-out(Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4fa98-115">For more information, see [-out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span></span>

```csharp
using System.Runtime.CompilerServices;
using System;

[assembly: InternalsVisibleTo("AssemblyB")]

// The class is internal by default.
class FriendClass
{
    public void Test()
    {
        Console.WriteLine("Sample Class");
    }
}

// Public class that has an internal method.
public class ClassWithFriendMethod
{
    internal void Test()
    {
        Console.WriteLine("Sample Method");
    }

}
```

```vb
Imports System.Runtime.CompilerServices
<Assembly: InternalsVisibleTo("AssemblyB")>

' Friend class.
Friend Class FriendClass
    Public Sub Test()
        Console.WriteLine("Sample Class")
    End Sub
End Class

' Public class with a Friend method.
Public Class ClassWithFriendMethod
    Friend Sub Test()
        Console.WriteLine("Sample Method")
    End Sub
End Class
```

<span data-ttu-id="4fa98-116">friend로 명시적으로 지정하는 어셈블리만 `internal`(C#) 또는 `Friend`(Visual Basic) 형식 및 멤버에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fa98-116">Only assemblies that you explicitly specify as friends can access `internal` (C#) or `Friend` (Visual Basic) types and members.</span></span> <span data-ttu-id="4fa98-117">예를 들어 *어셈블리 B*가 *어셈블리 A*의 friend이고 *어셈블리 C*가 *어셈블리 B*를 참조하는 경우, *어셈블리 C*는 *어셈블리 A*의 `internal`(C#)또는 `Friend`(Visual Basic) 형식에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4fa98-117">For example, if *AssemblyB* is a friend of *Assembly A* and *Assembly C* references *AssemblyB*, *Assembly C* does not have access to `internal` (C#) or `Friend` (Visual Basic) types in *Assembly A*.</span></span>

<span data-ttu-id="4fa98-118">컴파일러는 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 특성에 전달된 friend 어셈블리 이름에 대해 몇 가지 기본적인 유효성 검사를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="4fa98-118">The compiler performs some basic validation of the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="4fa98-119">*어셈블리 A*가 *어셈블리 B*를 friend 어셈블리로 선언하는 경우, 유효성 검사 규칙은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4fa98-119">If *Assembly A* declares *AssemblyB* as a friend assembly, the validation rules are as follows:</span></span>

- <span data-ttu-id="4fa98-120">*어셈블리 A*에 강력한 이름을 지정한 경우 *어셈블리 B*에도 강력한 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fa98-120">If *Assembly A* is strong named, *AssemblyB* must also be strong named.</span></span> <span data-ttu-id="4fa98-121">특성에 전달되는 friend 어셈블리 이름은 어셈블리 이름과 *어셈블리 B*에 서명하는 데 사용되는 강력한 이름 키의 공개 키로 구성되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fa98-121">The friend assembly name that is passed to the attribute must consist of the assembly name and the public key of the strong-name key that is used to sign *AssemblyB*.</span></span>

     <span data-ttu-id="4fa98-122"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 특성에 전달되는 friend 어셈블리 이름은 *어셈블리 B*의 강력한 이름일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4fa98-122">The friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute cannot be the strong name of *AssemblyB*.</span></span> <span data-ttu-id="4fa98-123">어셈블리 버전, 문화권, 아키텍처 또는 공개 키 토큰을 포함하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="4fa98-123">Don't include the assembly version, culture, architecture, or public key token.</span></span>

- <span data-ttu-id="4fa98-124">*어셈블리 A*에 강력한 이름을 지정하지 않은 경우 friend 어셈블리 이름은 어셈블리 이름만으로 구성되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fa98-124">If *Assembly A* is not strong named, the friend assembly name should consist of only the assembly name.</span></span> <span data-ttu-id="4fa98-125">자세한 내용은 [방법: 서명되지 않은 friend 어셈블리 만들기](create-unsigned-friend.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4fa98-125">For more information, see [How to: Create unsigned friend assemblies](create-unsigned-friend.md).</span></span>

- <span data-ttu-id="4fa98-126">*어셈블리 B*에 강력한 이름을 지정하는 경우 프로젝트 설정이나 명령줄 `/keyfile` 컴파일러 옵션을 사용하여 *어셈블리 B*에 강력한 이름 키를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fa98-126">If *AssemblyB* is strong named, you must specify the strong-name key for *AssemblyB* by using the project setting or the command-line `/keyfile` compiler option.</span></span> <span data-ttu-id="4fa98-127">자세한 내용은 [방법: 서명된 friend 어셈블리 만들기](create-signed-friend.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4fa98-127">For more information, see [How to: Create signed friend assemblies](create-signed-friend.md).</span></span>

 <span data-ttu-id="4fa98-128"><xref:System.Security.Permissions.StrongNameIdentityPermission> 클래스도 형식을 공유하는 기능을 제공하지만 다음과 같은 차이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fa98-128">The <xref:System.Security.Permissions.StrongNameIdentityPermission> class also provides the ability to share types, with the following differences:</span></span>

- <span data-ttu-id="4fa98-129"><xref:System.Security.Permissions.StrongNameIdentityPermission>은 개별 형식에 적용되는 반면 friend 어셈블리는 전체 어셈블리에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4fa98-129"><xref:System.Security.Permissions.StrongNameIdentityPermission> applies to an individual type, while a friend assembly applies to the whole assembly.</span></span>

- <span data-ttu-id="4fa98-130">*어셈블리 A*에 *어셈블리 B*와 공유하려는 수백 개의 형식이 있는 경우 모든 형식에 <xref:System.Security.Permissions.StrongNameIdentityPermission>을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fa98-130">If there are hundreds of types in *Assembly A* that you want to share with *AssemblyB*, you have to add <xref:System.Security.Permissions.StrongNameIdentityPermission> to all of them.</span></span> <span data-ttu-id="4fa98-131">friend 어셈블리를 사용하는 경우에는 friend 관계를 한 번만 선언하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4fa98-131">If you use a friend assembly, you only need to declare the friend relationship once.</span></span>

- <span data-ttu-id="4fa98-132"><xref:System.Security.Permissions.StrongNameIdentityPermission>을 사용하는 경우 공유하려는 형식을 public으로 선언해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fa98-132">If you use <xref:System.Security.Permissions.StrongNameIdentityPermission>, the types you want to share have to be declared as public.</span></span> <span data-ttu-id="4fa98-133">friend 어셈블리를 사용하는 경우 공유 유형은 `internal`(C#) 또는 `Friend`(Visual Basic)로 선언됩니다.</span><span class="sxs-lookup"><span data-stu-id="4fa98-133">If you use a friend assembly, the shared types are declared as `internal` (C#) or `Friend` (Visual Basic).</span></span>

<span data-ttu-id="4fa98-134">모듈 파일(확장명이 *.netmodule*인 파일)에서 어셈블리의 `internal`(C#) 또는 `Friend`(Visual Basic) 형식 및 메서드에 액세스하는 방법에 대한 자세한 내용은 [-moduleassemblyname(C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) 또는 [-moduleassemblyname(Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4fa98-134">For information about how to access an assembly's `internal` (C#) or `Friend` (Visual Basic) types and methods from a module file (a file with the *.netmodule* extension), see [-moduleassemblyname (C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) or [-moduleassemblyname (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4fa98-135">참조</span><span class="sxs-lookup"><span data-stu-id="4fa98-135">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [<span data-ttu-id="4fa98-136">방법: 서명되지 않은 friend 어셈블리 만들기</span><span class="sxs-lookup"><span data-stu-id="4fa98-136">How to: Create unsigned friend assemblies</span></span>](create-unsigned-friend.md)
- [<span data-ttu-id="4fa98-137">방법: 서명된 friend 어셈블리 만들기</span><span class="sxs-lookup"><span data-stu-id="4fa98-137">How to: Create signed friend assemblies</span></span>](create-signed-friend.md)
- [<span data-ttu-id="4fa98-138">.NET 어셈블리</span><span class="sxs-lookup"><span data-stu-id="4fa98-138">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="4fa98-139">C# 프로그래밍 가이드</span><span class="sxs-lookup"><span data-stu-id="4fa98-139">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="4fa98-140">프로그래밍 개념(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4fa98-140">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
