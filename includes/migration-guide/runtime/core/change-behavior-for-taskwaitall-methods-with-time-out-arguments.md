---
ms.openlocfilehash: 52406f1e4ea4eda417909e52cf6529631cb0ae33
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620219"
---
### <a name="change-in-behavior-for-taskwaitall-methods-with-time-out-arguments"></a>제한 시간 인수가 있는 Task.WaitAll 메서드에 대한 동작 변경

#### <a name="details"></a>설명

.NET Framework 4.5에서 <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType> 동작의 일관성이 높아졌습니다. .NET Framework 4에서는 이러한 메서드가 일관되지 않게 동작했었습니다. 제한 시간이 만료되고 메서드 호출 전에 하나 이상의 작업이 완료되거나 취소되면 이 메서드는 <xref:System.AggregateException?displayProperty=fullName> 예외를 throw합니다. 제한 시간이 만료되고 메서드 호출 전에 완료되거나 취소된 작업은 없지만 메서드 호출 후에 하나 이상의 작업이 완료되거나 취소되면 이 메서드는 false를 반환합니다.<br/><br/>.NET Framework 4.5에서, 시간 제한 간격이 만료될 때 모든 작업이 아직 실행되고 있는 경우 이러한 메서드 오버로드에서 이제 false를 반환하고, 입력 작업이 취소되고(메서드 호출 전후 여부와 상관없이) 다른 작업이 실행되고 있지 않은 경우에만 <xref:System.AggregateException?displayProperty=fullName> 예외를 throw합니다.

#### <a name="suggestion"></a>제안 해결 방법

.NET Framework 4.6은 대기된 모든 작업이 시간 제한 전에 완료되어야 throw하기 때문에 <xref:System.Threading.Tasks.Task.WaitAll%2A>이 호출되기 전에 취소된 작업을 탐지하는 방법으로 <xref:System.AggregateException?displayProperty=fullName>이 catch된 경우 해당 코드는 대신 <xref:System.Threading.Tasks.Task.IsCanceled%2A> 속성(예: .Any(t = &gt; t.IsCanceled))을 통해 동일한 탐지를 해야 합니다.

| 이름    | 값       |
|:--------|:------------|
| Scope   |부|
|버전|4.5|
|형식|런타임

#### <a name="affected-apis"></a>영향을 받는 API

-<xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32,System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.TimeSpan)?displayProperty=nameWithType></li></ul>|
