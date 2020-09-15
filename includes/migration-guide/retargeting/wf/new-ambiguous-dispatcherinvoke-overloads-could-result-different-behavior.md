---
ms.openlocfilehash: 80e61d4dd5b8d4754a39e95e37475fefff57fcbd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617171"
---
### <a name="new-ambiguous-dispatcherinvoke-overloads-could-result-in-different-behavior"></a><span data-ttu-id="b4bc0-101">(모호한) 새 Dispatcher.Invoke 오버로드는 다른 동작을 발생시킬 수 있습니다</span><span class="sxs-lookup"><span data-stu-id="b4bc0-101">New (ambiguous) Dispatcher.Invoke overloads could result in different behavior</span></span>

#### <a name="details"></a><span data-ttu-id="b4bc0-102">설명</span><span class="sxs-lookup"><span data-stu-id="b4bc0-102">Details</span></span>

<span data-ttu-id="b4bc0-103">.NET Framework 4.5는 <xref:System.Action> 형식의 매개 변수를 포함하는 새 오버로드를 <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=nameWithType>에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b4bc0-103">The .NET Framework 4.5 adds new overloads to <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=nameWithType> that include a parameter of type <xref:System.Action>.</span></span> <span data-ttu-id="b4bc0-104">기존 코드를 다시 컴파일하면 컴파일러는 <xref:System.Delegate> 매개 변수를 가진 Dispatcher.Invoke 메서드에 대한 호출로서 <xref:System.Action> 매개 변수를 갖는 Dispatcher.Invoke 메서드에 대한 호출을 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4bc0-104">When existing code is recompiled, compilers may resolve calls to Dispatcher.Invoke methods that have a <xref:System.Delegate> parameter as calls to Dispatcher.Invoke methods with an <xref:System.Action> parameter.</span></span> <span data-ttu-id="b4bc0-105"><xref:System.Delegate> 매개 변수를 가진 Dispatcher.Invoke 오버로드를 호출함으로써 해결된 <xref:System.Action> 매개 변수를 가진 Dispatcher.Invoke 오버로드를 호출하는 경우, 다음과 같은 동작 차이가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4bc0-105">If a call to a Dispatcher.Invoke overload with a  <xref:System.Delegate> parameter is resolved as a call to a Dispatcher.Invoke overload with an <xref:System.Action> parameter, the following differences in behavior may occur:</span></span>

- <span data-ttu-id="b4bc0-106">예외가 발생하는 경우 <xref:System.Windows.Threading.Dispatcher.UnhandledExceptionFilter> 및 <xref:System.Windows.Threading.Dispatcher.UnhandledException> 이벤트가 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b4bc0-106">If an exception occurs, the <xref:System.Windows.Threading.Dispatcher.UnhandledExceptionFilter> and <xref:System.Windows.Threading.Dispatcher.UnhandledException> events are not raised.</span></span> <span data-ttu-id="b4bc0-107">대신 예외는 <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=fullName> 이벤트에 의해 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4bc0-107">Instead, exceptions are handled by the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=fullName> event.</span></span>
- <span data-ttu-id="b4bc0-108"><xref:System.Windows.Threading.DispatcherOperation.Result>와 같은 일부 멤버에 대한 호출은 작업이 완료될 때까지 차단됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4bc0-108">Calls to some members, such as <xref:System.Windows.Threading.DispatcherOperation.Result>, block until the operation has completed.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b4bc0-109">제안 해결 방법</span><span class="sxs-lookup"><span data-stu-id="b4bc0-109">Suggestion</span></span>

<span data-ttu-id="b4bc0-110">모호성 (및 예외를 처리하거나 동작을 차단하는 잠재적인 문제)을 방지하려면 Dispatcher.Invoke를 호출하는 코드가 빈 개체를 두 번째 매개 변수로 Invoke 호출에 전달하여 .NET Framework 4.0 메서드 오버로드를 확인하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4bc0-110">To avoid ambiguity (and potential differences in exception handling or blocking behaviors), code calling Dispatcher.Invoke can pass an empty object[] as a second parameter to the Invoke call to be sure of resolving to the .NET Framework 4.0 method overload.</span></span>

| <span data-ttu-id="b4bc0-111">이름</span><span class="sxs-lookup"><span data-stu-id="b4bc0-111">Name</span></span>    | <span data-ttu-id="b4bc0-112">값</span><span class="sxs-lookup"><span data-stu-id="b4bc0-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b4bc0-113">Scope</span><span class="sxs-lookup"><span data-stu-id="b4bc0-113">Scope</span></span>   | <span data-ttu-id="b4bc0-114">부</span><span class="sxs-lookup"><span data-stu-id="b4bc0-114">Minor</span></span>       |
| <span data-ttu-id="b4bc0-115">버전</span><span class="sxs-lookup"><span data-stu-id="b4bc0-115">Version</span></span> | <span data-ttu-id="b4bc0-116">4.5</span><span class="sxs-lookup"><span data-stu-id="b4bc0-116">4.5</span></span>         |
| <span data-ttu-id="b4bc0-117">형식</span><span class="sxs-lookup"><span data-stu-id="b4bc0-117">Type</span></span>    | <span data-ttu-id="b4bc0-118">대상 변경</span><span class="sxs-lookup"><span data-stu-id="b4bc0-118">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="b4bc0-119">영향을 받는 API</span><span class="sxs-lookup"><span data-stu-id="b4bc0-119">Affected APIs</span></span>

- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.Object[])?displayProperty=nameWithType>
- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.TimeSpan,System.Object[])?displayProperty=nameWithType>
- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.TimeSpan,System.Windows.Threading.DispatcherPriority,System.Object[])?displayProperty=nameWithType>
- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.Windows.Threading.DispatcherPriority,System.Object[])?displayProperty=nameWithType>
