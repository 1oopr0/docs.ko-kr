---
title: 형식
description: 'F #에서 사용 되는 형식과 F # 형식의 이름을 지정 하 고 설명 하는 방법에 대해 알아봅니다.'
ms.date: 08/15/2020
ms.openlocfilehash: a86d8e8f672d8399b02bb193ae04e1f0d46720b6
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812070"
---
# <a name="f-types"></a>F# 형식

이 항목에서는 F #에서 사용 되는 형식과 F # 형식의 이름을 지정 하 고 설명 하는 방법에 대해 설명 합니다.

## <a name="summary-of-f-types"></a>F # 형식 요약

일부 형식은 부울 형식 *primitive types* `bool` 및 다양 한 크기의 정수 계열 및 부동 소수점 형식과 같은 기본 형식으로 간주 됩니다. 여기에는 바이트 및 문자에 대 한 형식이 포함 됩니다. 이러한 형식은 [기본 형식](basic-types.md)에 설명 되어 있습니다.

언어에 기본 제공 되는 다른 형식에는 튜플, 목록, 배열, 시퀀스, 레코드 및 구분 된 공용 구조체가 포함 됩니다. 다른 .NET 언어를 사용 하 고 있으며 F #을 학습 하는 경우 이러한 각 형식에 대 한 항목을 읽어야 합니다. 이러한 F # 관련 형식은 함수형 프로그래밍 언어에 공통적인 프로그래밍 스타일을 지원 합니다. 이러한 형식에는 이러한 형식에 대 한 일반 작업을 지 원하는 F # 라이브러리의 연결 된 모듈이 있습니다.

함수의 형식에는 매개 변수 형식 및 반환 형식에 대 한 정보가 포함 됩니다.

.NET Framework는 개체 형식, 인터페이스 형식, 대리자 형식 및 기타의 소스입니다. 다른 .NET 언어에서와 마찬가지로 고유한 개체 형식을 정의할 수 있습니다.

또한 F # 코드는 형식의 대체 이름인 명명 된 *형식 약어*인 별칭을 정의할 수 있습니다. 형식이 나중에 변경 될 수 있으며 형식에 종속 되는 코드를 변경 하지 않으려는 경우 형식 약어를 사용할 수 있습니다. 또는 형식 약어를 코드를 보다 쉽게 읽고 이해할 수 있도록 하는 형식에 대 한 친숙 한 이름으로 사용할 수 있습니다.

F #은 함수형 프로그래밍을 고려 하 여 디자인 된 유용한 컬렉션 형식을 제공 합니다. 이러한 컬렉션 형식을 사용 하면 스타일에서 더 많은 기능을 갖춘 코드를 작성할 수 있습니다. 자세한 내용은 [F # 컬렉션 형식](fsharp-collection-types.md)을 참조 하세요.

## <a name="syntax-for-types"></a>형식에 대 한 구문

F # 코드에서 형식의 이름을 작성 해야 하는 경우가 많습니다. 모든 형식에는 구문 형식이 있으며 형식 주석, 추상 메서드 선언, 대리자 선언, 서명 및 기타 구문에서 이러한 구문 형식을 사용 합니다. 인터프리터에서 새 프로그램 구문을 선언할 때마다 인터프리터는 구문의 이름과 해당 형식에 대 한 구문을 출력 합니다. 이 구문은 또는의 경우와 같이 사용자 정의 형식 또는 기본 제공 식별자에 대 한 식별자 일 수 `int` `string` 있지만 더 복잡 한 형식의 구문은 더 복잡 합니다.

다음 표에서는 F # 형식에 대 한 형식 구문의 여러 측면을 보여 줍니다.

|형식|형식 구문|예제|
|----|-----------|--------|
|기본 형식|*유형-이름*|`int`<br /><br />`float`<br /><br />`string`|
|집계 형식 (클래스, 구조체, 공용 구조체, 레코드, 열거형 등)|*유형-이름*|`System.DateTime`<br /><br />`Color`|
|형식 약어|*유형-약어-이름*|`bigint`|
|정규화 된 형식|*네임 스페이스. 형식-이름*<br /><br />또는<br /><br />*modules. 형식-name*<br /><br />또는<br /><br />*네임 스페이스. modules. 형식-name*|`System.IO.StreamWriter`|
|array|*유형-name*[] 또는<br /><br />*형식-이름* 배열|`int[]`<br /><br />`array<int>`<br /><br />`int array`|
|2 차원 배열|*유형-이름*[,]|`int[,]`<br /><br />`float[,]`|
|3 차원 배열|*유형-이름*[,,]|`float[,,]`|
|tuple|*형식-name1* &#42; *type-name2* ...|예를 들어, `(1,'b',3)` 형식에 `int * char * int`|
|제네릭 형식(generic type)|*유형-매개 변수* *일반 유형-이름*<br /><br />또는<br /><br />*제네릭 형식 이름* &lt; *유형-매개 변수 목록*&gt;|`'a list`<br /><br />`list<'a>`<br /><br />`Dictionary<'key, 'value>`|
|생성 된 형식 (특정 형식 인수를 제공 하는 제네릭 형식)|*형식 인수* *제네릭 형식-name*<br /><br />또는<br /><br />*제네릭 형식 이름* &lt; *형식-인수 목록*&gt;|`int option`<br /><br />`string list`<br /><br />`int ref`<br /><br />`option<int>`<br /><br />`list<string>`<br /><br />`ref<int>`<br /><br />`Dictionary<int, string>`|
|단일 매개 변수를 포함 하는 함수 형식|*매개 변수-type1*  - &gt; *반환 형식*|를 사용 하 `int` 고를 반환 하는 함수는 `string``int -> string`|
|여러 매개 변수를 포함 하는 함수 형식|*매개 변수-type1*  - &gt; *매개 변수-type2*  - &gt; ...- &gt; *반환 형식*|`int`및를 사용 하 `float` 고를 반환 `string` 하는 함수는`int -> float -> string`|
|매개 변수로 고차 함수|(*함수 형식*)|`List.map` 형식 있음 `('a -> 'b) -> 'a list -> 'b list`|
|대리자(delegate)|*함수 형식의* 대리자|`delegate of unit -> int`|
|유연한 형식|#*유형-이름*|`#System.Windows.Forms.Control`<br /><br />`#seq<int>`|

## <a name="related-topics"></a>관련 항목

|항목|Description|
|-----|-----------|
|[기본 유형](basic-types.md)|정수 형식, 부울 형식 및 문자 형식과 같은 기본 제공 단순 형식을 설명 합니다.|
|[단위 형식](unit-type.md)|`unit`()로 표시 되는 형식, 값이 하나 있고 ()로 표시 되는 형식에 대해 설명 합니다. `void` c #의 및 Visual Basic와 동일 `Nothing` 합니다.|
|[튜플](tuples.md)|쌍, 삼중 쌍, quadruples 등으로 그룹화 된 모든 형식의 연결 된 값으로 구성 된 형식인 튜플 형식을 설명 합니다.|
|[Options](options.md)|값을 포함 하거나 비워 둘 수 있는 형식인 옵션 유형을 설명 합니다.|
|[목록](lists.md)|동일한 형식으로 정렬 된 변경 불가능 한 일련의 요소를 보여 줍니다.|
|[배열](arrays.md)|연속 메모리 블록을 차지 하 고 크기가 고정 된 동일한 형식의 변경 가능한 요소 집합을 정렬 하는 배열에 대해 설명 합니다.|
|[시퀀스](sequences.md)|값의 논리적 계열을 나타내는 시퀀스 유형을 설명 합니다. 개별 값은 필요한 경우에만 계산 됩니다.|
|[레코드](records.md)|명명 된 값의 작은 집계 인 레코드 형식을 설명 합니다.|
|[구별된 공용 구조체](discriminated-unions.md)|값이 가능한 형식 집합 중 하나일 수 있는 형식인 구별 된 공용 구조체 형식을 설명 합니다.|
|[함수](./functions/index.md)|함수 값에 대해 설명 합니다.|
|[클래스](classes.md)|.NET 참조 형식에 해당 하는 개체 형식인 클래스 형식을 설명 합니다. 클래스 형식에는 멤버, 속성, 구현 된 인터페이스 및 기본 형식이 포함 될 수 있습니다.|
|[구조체](structures.md)|`struct`.Net 값 형식에 해당 하는 개체 형식인 형식을 설명 합니다. `struct`형식은 일반적으로 작은 데이터 집계를 나타냅니다.|
|[인터페이스](interfaces.md)|특정 기능을 제공 하지만 데이터를 포함 하지 않는 멤버 집합을 나타내는 형식인 인터페이스 형식에 대해 설명 합니다. 인터페이스 형식은 유용한 개체 형식에 의해 구현 되어야 합니다.|
|[대리자](delegates.md)|함수를 개체로 나타내는 대리자 형식을 설명 합니다.|
|[열거형](enumerations.md)|값이 명명 된 값 집합에 속하는 열거형 형식에 대해 설명 합니다.|
|[특성](attributes.md)|다른 형식에 대 한 메타 데이터를 지정 하는 데 사용 되는 특성을 설명 합니다.|
|[예외 형식](./exception-handling/exception-types.md)|오류 정보를 지정 하는 예외를 설명 합니다.|
