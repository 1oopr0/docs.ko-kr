---
description: private protected - C# 참조
title: private protected - C# 참조
ms.date: 11/15/2017
f1_keywords:
- privateprotected_CSharpKeyword
author: sputier
ms.openlocfilehash: d83fd2a570b735a029bd2a79ad24e30d235dc5fb
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89117963"
---
# <a name="private-protected-c-reference"></a>private protected (C# Reference)

`private protected` 키워드 조합은 멤버 액세스 한정자입니다. private protected 멤버는 포함하는 클래스에서 파생된 형식으로 액세스할 수 있지만 포함하는 어셈블리 내에서만 가능합니다. `private protected` 및 다른 액세스 한정자와 비교는 [액세스 가능성 수준](accessibility-levels.md)을 참조하세요.

> [!NOTE]
> `private protected` 액세스 한정자는 C# 7.2 버전에서 유효합니다.

## <a name="example"></a>예제

기본 클래스의 private protected 멤버는 변수의 정적 형식이 파생 클래스 형식인 경우에만 포함 어셈블리의 파생된 형식에서 액세스할 수 있습니다. 예를 들어 다음 코드 세그먼트를 고려하세요.

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

이 예제에는 `Assembly1.cs` 및 `Assembly2.cs`의 두 파일이 포함되어 있습니다.
첫 번째 파일은 공용 기본 클래스인 `BaseClass`를 포함하고 여기에서 파생된 형식인 `DerivedClass1`을 포함합니다. `BaseClass`는 `DerivedClass1`이 두 가지 방법으로 액세스를 시도하는 private protected 멤버인 `myValue`를 소유합니다. `BaseClass`의 인스턴스를 통한 `myValue` 액세스의 첫 번째 시도는 오류를 생성합니다. 그러나 `DerivedClass1`에서 상속된 멤버로 사용하려는 시도는 성공합니다.

두 번째 파일에서 `DerivedClass2`의 상속된 멤버로 `myValue`에 액세스하는 시도는 Assembly1에서 파생된 형식으로만 액세스할 수 있으므로 오류를 생성합니다.

`Assembly2` 이름을 지정하는 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>가 `Assembly1.cs`에 포함된 경우 파생 클래스 `DerivedClass1`는 `private protected`에 선언된 `BaseClass` 멤버에 액세스할 수 있습니다. `InternalsVisibleTo`는 `private protected` 멤버가 다른 어셈블리의 파생 클래스에 표시되도록 합니다.

구조체를 상속할 수 없기 때문에 구조체 멤버는 `private protected`일 수 없습니다.

## <a name="c-language-specification"></a>C# 언어 사양

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>참조

- [C# 참조](../index.md)
- [C# 프로그래밍 가이드](../../programming-guide/index.md)
- [C# 키워드](index.md)
- [액세스 한정자](access-modifiers.md)
- [액세스 수준](accessibility-levels.md)
- [한정자](index.md)
- [public](public.md)
- [private](private.md)
- [internal](internal.md)
- [internal virtual 키워드에 대한 보안 문제](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))
