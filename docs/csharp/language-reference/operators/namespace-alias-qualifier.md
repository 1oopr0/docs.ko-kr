---
title: ':: 연산자 - C# 참조'
ms.date: 08/09/2019
f1_keywords:
- ::_CSharpKeyword
- global_CSharpKeyword
- global
helpviewer_keywords:
- ':: operator [C#]'
- namespace alias qualifier [C#]
- namespace [C#]
- global keyword [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: f91287ed281a2c6b10bed93cff10b08972a8445e
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855129"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="c31ce-102">:: 연산자(C# 참조)</span><span class="sxs-lookup"><span data-stu-id="c31ce-102">:: operator (C# reference)</span></span>

<span data-ttu-id="c31ce-103">네임스페이스 별칭 한정자(`::`)를 사용하여 별칭이 지정된 네임스페이스의 구성원에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="c31ce-103">Use the namespace alias qualifier `::` to access a member of an aliased namespace.</span></span> <span data-ttu-id="c31ce-104">두 식별자 사이에 `::` 한정사만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c31ce-104">You can use the `::` qualifier only between two identifiers.</span></span> <span data-ttu-id="c31ce-105">왼쪽 식별자는 다음 별칭 중 하나를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c31ce-105">The left-hand identifier can be any of the following aliases:</span></span>

- <span data-ttu-id="c31ce-106">[별칭 지시문을 사용](../keywords/using-directive.md)하여 만든 네임스페이스 별칭:</span><span class="sxs-lookup"><span data-stu-id="c31ce-106">A namespace alias created with a [using alias directive](../keywords/using-directive.md):</span></span>

  ```csharp
  using forwinforms = System.Drawing;
  using forwpf = System.Windows;
  
  public class Converters
  {
      public static forwpf::Point Convert(forwinforms::Point point) => new forwpf::Point(point.X, point.Y);
  }
  ```

- <span data-ttu-id="c31ce-107">[extern 별칭](../keywords/extern-alias.md)</span><span class="sxs-lookup"><span data-stu-id="c31ce-107">An [extern alias](../keywords/extern-alias.md).</span></span>
- <span data-ttu-id="c31ce-108">전역 네임스페이스 별칭인 `global` 별칭.</span><span class="sxs-lookup"><span data-stu-id="c31ce-108">The `global` alias, which is the global namespace alias.</span></span> <span data-ttu-id="c31ce-109">전역 네임스페이스는 명명된 네임스페이스 내에 선언되지 않은 네임스페이스와 형식을 포함하는 네임스페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="c31ce-109">The global namespace is the namespace that contains namespaces and types that are not declared inside a named namespace.</span></span> <span data-ttu-id="c31ce-110">`::` 한정자와 함께 사용하는 경우 `global` 별칭은 사용자 정의 `global` 네임 스페이스 별칭이 있더라도 항상 전역 네임 스페이스를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="c31ce-110">When used with the `::` qualifier, the `global` alias always references the global namespace, even if there is the user-defined `global` namespace alias.</span></span>

  <span data-ttu-id="c31ce-111">다음 예제에서는 `global` 별칭을 사용하여 전역 네임스페이스의 구성원인 .NET <xref:System> 네임 스페이스에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="c31ce-111">The following example uses the `global` alias to access the .NET <xref:System> namespace, which is a member of the global namespace.</span></span> <span data-ttu-id="c31ce-112">`global` 별칭을 사용하지 않으면 `MyCompany.MyProduct` 네임스페이스의 구성원인 사용자 정의 `System` 네임스페이스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c31ce-112">Without the `global` alias, the user-defined `System` namespace, which is a member of the `MyCompany.MyProduct` namespace, would be accessed:</span></span>

  ```csharp
  namespace MyCompany.MyProduct.System
  {
      class Program
      {
          static void Main() => global::System.Console.WriteLine("Using global alias");
      }

      class Console
      {
          string Suggestion => "Consider renaming this class";
      }
  }
  ```

  > [!NOTE]
  > <span data-ttu-id="c31ce-113">`global` 키워드는 `::` 한정자의 왼쪽 식별자인 경우에만 전역 네임 스페이스 별칭입니다.</span><span class="sxs-lookup"><span data-stu-id="c31ce-113">The `global` keyword is the global namespace alias only when it's the left-hand identifier of the `::` qualifier.</span></span>

<span data-ttu-id="c31ce-114">[`.` 토큰](member-access-operators.md#member-access-expression-)을 사용하여 별칭이 지정된 네임스페이스의 멤버에 액세스할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c31ce-114">You can also use the [`.` token](member-access-operators.md#member-access-expression-) to access a member of an aliased namespace.</span></span> <span data-ttu-id="c31ce-115">그러나 `.` 토큰은 형식 멤버에 액세스하는 데도 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c31ce-115">However, the `.` token is also used to access a type member.</span></span> <span data-ttu-id="c31ce-116">`::` 한정자는 이름이 같은 형식 또는 네임 스페이스가 있는 경우에도 해당 왼쪽 식별자가 항상 네임스페이스 별칭을 참조하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c31ce-116">The `::` qualifier ensures that its left-hand identifier always references a namespace alias, even if there exists a type or namespace with the same name.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c31ce-117">C# 언어 사양</span><span class="sxs-lookup"><span data-stu-id="c31ce-117">C# language specification</span></span>

<span data-ttu-id="c31ce-118">자세한 내용은 [C# 언어 사양](~/_csharplang/spec/introduction.md)의 [네임스페이스 별칭 한정자](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c31ce-118">For more information, see the [Namespace alias qualifiers](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c31ce-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c31ce-119">See also</span></span>

- [<span data-ttu-id="c31ce-120">C# 참조</span><span class="sxs-lookup"><span data-stu-id="c31ce-120">C# reference</span></span>](../index.md)
- [<span data-ttu-id="c31ce-121">C# 연산자 및 식</span><span class="sxs-lookup"><span data-stu-id="c31ce-121">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="c31ce-122">네임스페이스 사용</span><span class="sxs-lookup"><span data-stu-id="c31ce-122">Using namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
