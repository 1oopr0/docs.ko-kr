---
title: private protected - C# 참조
ms.date: 11/15/2017
f1_keywords:
- privateprotected_CSharpKeyword
author: sputier
ms.openlocfilehash: 94ef55d7e13841f81b036f52659b215e22a3a0d7
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301803"
---
# <a name="private-protected-c-reference"></a><span data-ttu-id="523d8-102">private protected (C# Reference)</span><span class="sxs-lookup"><span data-stu-id="523d8-102">private protected (C# Reference)</span></span>

<span data-ttu-id="523d8-103">`private protected` 키워드 조합은 멤버 액세스 한정자입니다.</span><span class="sxs-lookup"><span data-stu-id="523d8-103">The `private protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="523d8-104">private protected 멤버는 포함하는 클래스에서 파생된 형식으로 액세스할 수 있지만 포함하는 어셈블리 내에서만 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="523d8-104">A private protected member is accessible by types derived from the containing class, but only within its containing assembly.</span></span> <span data-ttu-id="523d8-105">`private protected` 및 다른 액세스 한정자와 비교는 [액세스 가능성 수준](accessibility-levels.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="523d8-105">For a comparison of `private protected` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

> [!NOTE]
> <span data-ttu-id="523d8-106">`private protected` 액세스 한정자는 C# 7.2 버전에서 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="523d8-106">The `private protected` access modifier is valid in C# version 7.2 and later.</span></span>

## <a name="example"></a><span data-ttu-id="523d8-107">예제</span><span class="sxs-lookup"><span data-stu-id="523d8-107">Example</span></span>

<span data-ttu-id="523d8-108">기본 클래스의 private protected 멤버는 변수의 정적 형식이 파생 클래스 형식인 경우에만 포함 어셈블리의 파생된 형식에서 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="523d8-108">A private protected member of a base class is accessible from derived types in its containing assembly only if the static type of the variable is the derived class type.</span></span> <span data-ttu-id="523d8-109">예를 들어 다음 코드 세그먼트를 고려하세요.</span><span class="sxs-lookup"><span data-stu-id="523d8-109">For example, consider the following code segment:</span></span>

```csharp
public class BaseClass
{
    private protected int myValue = 0;
}

public class DerivedClass1 : BaseClass
{
    void Access()
    {
        var baseObject = new BaseClass();

        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 5;

        // OK, accessed through the current derived class instance
        myValue = 5;
    }
}
```

```csharp
// Assembly2.cs
// Compile with: /reference:Assembly1.dll
class DerivedClass2 : BaseClass
{
    void Access()
    {
        // Error CS0122, because myValue can only be
        // accessed by types in Assembly1
        // myValue = 10;
    }
}
```

<span data-ttu-id="523d8-110">이 예제에는 `Assembly1.cs` 및 `Assembly2.cs`의 두 파일이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="523d8-110">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span>
<span data-ttu-id="523d8-111">첫 번째 파일은 공용 기본 클래스인 `BaseClass`를 포함하고 여기에서 파생된 형식인 `DerivedClass1`을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="523d8-111">The first file contains a public base class, `BaseClass`, and a type derived from it, `DerivedClass1`.</span></span> <span data-ttu-id="523d8-112">`BaseClass`는 `DerivedClass1`이 두 가지 방법으로 액세스를 시도하는 private protected 멤버인 `myValue`를 소유합니다.</span><span class="sxs-lookup"><span data-stu-id="523d8-112">`BaseClass` owns a private protected member, `myValue`, which `DerivedClass1` tries to access in two ways.</span></span> <span data-ttu-id="523d8-113">`BaseClass`의 인스턴스를 통한 `myValue` 액세스의 첫 번째 시도는 오류를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="523d8-113">The first attempt to access `myValue` through an instance of `BaseClass` will produce an error.</span></span> <span data-ttu-id="523d8-114">그러나 `DerivedClass1`에서 상속된 멤버로 사용하려는 시도는 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="523d8-114">However, the attempt to use it as an inherited member in `DerivedClass1` will succeed.</span></span>

<span data-ttu-id="523d8-115">두 번째 파일에서 `DerivedClass2`의 상속된 멤버로 `myValue`에 액세스하는 시도는 Assembly1에서 파생된 형식으로만 액세스할 수 있으므로 오류를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="523d8-115">In the second file, an attempt to access `myValue` as an inherited member of `DerivedClass2` will produce an error, as it is only accessible by derived types in Assembly1.</span></span>

<span data-ttu-id="523d8-116">`Assembly2` 이름을 지정하는 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>가 `Assembly1.cs`에 포함된 경우 파생 클래스 `DerivedClass1`는 `private protected`에 선언된 `BaseClass` 멤버에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="523d8-116">If `Assembly1.cs` contains an <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> that names `Assembly2`, the derived class `DerivedClass1` will have access to `private protected` members declared in `BaseClass`.</span></span> <span data-ttu-id="523d8-117">`InternalsVisibleTo`는 `private protected` 멤버가 다른 어셈블리의 파생 클래스에 표시되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="523d8-117">`InternalsVisibleTo` makes `private protected` members visible to derived classes in other assemblies.</span></span>

<span data-ttu-id="523d8-118">구조체를 상속할 수 없기 때문에 구조체 멤버는 `private protected`일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="523d8-118">Struct members cannot be `private protected` because the struct cannot be inherited.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="523d8-119">C# 언어 사양</span><span class="sxs-lookup"><span data-stu-id="523d8-119">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="523d8-120">참조</span><span class="sxs-lookup"><span data-stu-id="523d8-120">See also</span></span>

- [<span data-ttu-id="523d8-121">C# 참조</span><span class="sxs-lookup"><span data-stu-id="523d8-121">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="523d8-122">C# 프로그래밍 가이드</span><span class="sxs-lookup"><span data-stu-id="523d8-122">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="523d8-123">C# 키워드</span><span class="sxs-lookup"><span data-stu-id="523d8-123">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="523d8-124">액세스 한정자</span><span class="sxs-lookup"><span data-stu-id="523d8-124">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="523d8-125">액세스 수준</span><span class="sxs-lookup"><span data-stu-id="523d8-125">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="523d8-126">한정자</span><span class="sxs-lookup"><span data-stu-id="523d8-126">Modifiers</span></span>](index.md)
- [<span data-ttu-id="523d8-127">public</span><span class="sxs-lookup"><span data-stu-id="523d8-127">public</span></span>](public.md)
- [<span data-ttu-id="523d8-128">private</span><span class="sxs-lookup"><span data-stu-id="523d8-128">private</span></span>](private.md)
- [<span data-ttu-id="523d8-129">internal</span><span class="sxs-lookup"><span data-stu-id="523d8-129">internal</span></span>](internal.md)
- <span data-ttu-id="523d8-130">[internal virtual 키워드에 대한 보안 문제](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="523d8-130">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
