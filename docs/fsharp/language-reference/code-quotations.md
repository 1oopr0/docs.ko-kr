---
title: 코드 인용
description: '프로그래밍 방식으로 F # 코드 식을 생성 하 고 사용할 수 있도록 하는 언어 기능인 F # 코드 인용에 대해 알아봅니다.'
ms.date: 08/13/2020
ms.openlocfilehash: dc37fdbd6cd29e5ee94e5c0186dfe2bfeb666f32
ms.sourcegitcommit: f99115e12a5eb75638abe45072e023a3ce3351ac
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94557196"
---
# <a name="code-quotations"></a>코드 인용

이 문서에서는 F # 코드 식을 프로그래밍 방식으로 생성 하 고 사용할 수 있도록 하는 언어 기능인 *코드 인용* 을 설명 합니다. 이 기능을 사용 하면 F # 코드를 나타내는 추상 구문 트리를 생성할 수 있습니다. 그런 다음 응용 프로그램의 필요에 따라 추상 구문 트리를 트래버스 하 고 처리할 수 있습니다. 예를 들어, 트리를 사용 하 여 F # 코드를 생성 하거나 다른 언어로 코드를 생성할 수 있습니다.

## <a name="quoted-expressions"></a>따옴표 붙은 식

*따옴표 붙은 식은* 프로그램의 일부로 컴파일되지 않고 f # 식을 나타내는 개체로 컴파일되는 방식으로 구분 되는 코드의 f # 식입니다 (예: 다음 두 가지 방법 중 하나를 사용 하 여 따옴표 붙은 식을 표시할 수 있습니다. 형식 정보를 사용 하거나 형식 정보를 포함 하지 않습니다. 형식 정보를 포함 하려는 경우 기호를 사용 하 여 `<@` `@>` 따옴표 붙은 식을 구분 합니다. 형식 정보가 필요 하지 않은 경우에는 기호와를 사용 `<@@` `@@>` 합니다. 다음 코드는 형식화 된 및 형식화 되지 않은 따옴표를 보여 줍니다.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet501.fs)]

형식 정보를 포함 하지 않는 경우에는 긴 식 트리를 더 빠르게 트래버스할 수 있습니다. 형식화 된 기호로 묶은 식의 결과 형식은입니다 `Expr<'T>` . 여기서 형식 매개 변수는 F # 컴파일러의 형식 유추 알고리즘에 의해 결정 된 식의 형식입니다. 형식 정보 없이 코드 따옴표를 사용 하는 경우 따옴표 붙은 식의 형식은 제네릭이 아닌 형식 [Expr](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-fsharpexpr.html)입니다. 형식화 된 클래스에 대해 [Raw](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-fsharpexpr-1.html#Raw) 속성을 호출 `Expr` 하 여 형식화 되지 않은 개체를 가져올 수 있습니다 `Expr` .

`Expr`따옴표로 묶인 식을 사용 하지 않고도 클래스에서 프로그래밍 방식으로 F # 식 개체를 생성할 수 있도록 하는 다양 한 정적 메서드가 있습니다.

코드 인용에는 전체 식이 포함 되어야 합니다. 예를 들어 바인딩의 경우 바인딩 `let` 이름 및 바인딩을 사용 하는 추가 식의 정의가 모두 필요 합니다. 자세한 구문에서 키워드 뒤에 오는 식입니다 `in` . 모듈의 최상위 수준에서이는 모듈의 다음 식일 뿐 아니라 따옴표 안에 명시적으로 필요 합니다.

따라서 다음 식은 유효 하지 않습니다.

```fsharp
// Not valid:
// <@ let f x = x + 1 @>
```

그러나 다음 식은 유효 합니다.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet502.fs)]

F # 따옴표를 계산 하려면 [f # 따옴표 계산기](https://github.com/fsprojects/FSharp.Quotations.Evaluator)를 사용 해야 합니다. F # 식 개체를 평가 하 고 실행 하는 기능을 지원 합니다.

또한 F # 인용구는 형식 제약 조건 정보를 유지 합니다. 다음 예제를 참조하세요.

```fsharp
open FSharp.Linq.RuntimeHelpers

let eval q = LeafExpressionConverter.EvaluateQuotation q

let inline negate x = -x
// val inline negate: x: ^a ->  ^a when  ^a : (static member ( ~- ) :  ^a ->  ^a)

<@ negate 1.0 @>  |> eval
```

함수에서 생성 된 제약 조건은 `inline` 코드 qutoation 유지 됩니다. `negate`이제 함수의 quotated 폼을 평가할 수 있습니다.

## <a name="expr-type"></a>Expr 형식

형식의 인스턴스는 `Expr` F # 식을 나타냅니다. 제네릭 및 제네릭이 아닌 `Expr` 형식은 모두 F # 라이브러리 설명서에 설명 되어 있습니다. 자세한 내용은 [Fsharp.core 네임 스페이스](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations.html) 및 [인용구 클래스](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-fsharpexpr.html)를 참조 하세요.

## <a name="splicing-operators"></a>스플라이스 연산자

스플라이스를 사용 하면 프로그래밍 방식으로 또는 다른 코드 인용에서 만든 식과 리터럴 코드 따옴표를 결합할 수 있습니다. `%`및 `%%` 연산자를 사용 하 여 코드 인용에 F # 식 개체를 추가할 수 있습니다. 연산자를 사용 하 여 형식화 `%` 된 식 개체를 형식화 된 따옴표로 삽입 합니다. 연산자를 사용 하 여 형식화 되지 `%%` 않은 식 개체를 형식화 되지 않은 따옴표로 삽입 합니다. 두 연산자는 단항 전위 연산자입니다. 따라서 `expr` 가 형식의 형식화 되지 않은 식인 경우에는 `Expr` 다음 코드를 사용할 수 있습니다.

```fsharp
<@@ 1 + %%expr @@>
```

`expr`가 형식의 형식화 된 인용 인 경우 `Expr<int>` 다음 코드는 유효 합니다.

```fsharp
<@ 1 + %expr @>
```

## <a name="example"></a>예제

### <a name="description"></a>Description

다음 예제에서는 코드 인용을 사용 하 여 F # 코드를 식 개체에 배치한 다음 식을 나타내는 F # 코드를 인쇄 하는 방법을 보여 줍니다. `println` `print` F # 식 개체 (형식 `Expr` )를 친숙 한 형식으로 표시 하는 재귀 함수를 포함 하는 함수가 정의 되었습니다. [Fsharp.core](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-patternsmodule.html) 및 [fsharp.core](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-derivedpatternsmodule.html) 모듈에는 식 개체를 분석 하는 데 사용할 수 있는 여러 가지 활성 패턴이 있습니다. 이 예제에는 F # 식에 나타날 수 있는 모든 패턴이 포함 되지 않습니다. 인식할 수 없는 모든 패턴은 와일드 카드 패턴 ()에 대 한 일치를 트리거하고 `_` 메서드를 사용 하 여 렌더링 됩니다 .이 메서드를 사용 하면 해당 `ToString` `Expr` 형식에서 일치 식에 추가할 활성 패턴을 알 수 있습니다.

### <a name="code"></a>코드

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet601.fs)]

### <a name="output"></a>출력

```fsharp
fun (x:System.Int32) -> x + 1
a + 1
let f = fun (x:System.Int32) -> x + 10 in f 10
```

## <a name="example"></a>예제

### <a name="description"></a>Description

[Exprshape.rebuildshapecombination 모듈](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-exprshapemodule.html) 의 세 가지 활성 패턴을 사용 하 여 활성 패턴이 적을수록 식 트리를 트래버스할 수도 있습니다. 이러한 활성 패턴은 트리를 트래버스 하려고 하지만 대부분의 노드에 모든 정보가 필요 하지 않은 경우에 유용할 수 있습니다. 이러한 패턴을 사용 하는 경우 모든 F # 식은 `ShapeVar` 식이 변수인 경우, 식이 `ShapeLambda` 람다 식인 경우 또는 `ShapeCombination` 식이 다른 것 인 경우에는 다음 세 가지 패턴 중 하 나와 일치 합니다. 이전 코드 예제와 같이 활성 패턴을 사용 하 여 식 트리를 트래버스하는 경우에는 더 많은 패턴을 사용 하 여 가능한 모든 F # 식 형식을 처리 해야 하며 코드는 더 복잡 합니다. 자세한 내용은 [exprshape.rebuildshapecombination. ShapeVar&#124;ShapeLambda&#124;ShapeCombination Active Pattern](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-exprshapemodule.html#(%20|ShapeVar|ShapeLambda|ShapeCombination|%20))을 참조 하세요.

다음 코드 예제는 보다 복잡 한 순회를 위한 기준으로 사용할 수 있습니다. 이 코드에서는 함수 호출를 포함 하는 식에 대해 식 트리가 생성 됩니다 `add` . [SpecificCall](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-derivedpatternsmodule.html#(%20|SpecificCall|_|%20)) 활성 패턴은 식 트리에서에 대 한 호출을 검색 하는 데 사용 됩니다 `add` . 이 활성 패턴은 호출의 인수를 값에 할당 합니다 `exprList` . 이 경우에는 두 개만 있으므로이를 끌어올 수 있으며 함수는 인수에서 재귀적으로 호출 됩니다. 결과는 `mul` splice 연산자 ()를 사용 하 여에 대 한 호출을 나타내는 코드 따옴표로 삽입 됩니다 `%%` . `println`이전 예제의 함수는 결과를 표시 하는 데 사용 됩니다.

다른 활성 패턴 분기의 코드는 동일한 식 트리를 다시 생성 하므로 결과 식의 변경 내용만에서로 변경 됩니다 `add` `mul` .

### <a name="code"></a>코드

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet701.fs)]

### <a name="output"></a>출력

```fsharp
1 + Module1.add(2,Module1.add(3,4))
1 + Module1.mul(2,Module1.mul(3,4))
```

## <a name="see-also"></a>참조

- [F# 언어 참조](index.md)
