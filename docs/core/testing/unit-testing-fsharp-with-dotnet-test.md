---
title: dotnet 테스트 및 xUnit을 사용하여 .NET Core에서 F# 단위 테스트
description: dotnet test 및 xUnit을 사용하여 샘플 솔루션을 단계별로 빌드하는 대화형 환경을 통해 .NET Core의 F#에 대한 단위 테스트 개념을 알아봅니다.
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
ms.openlocfilehash: e0f2b6f88a650f412148f51cc0236fa46ed8c618
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656555"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-xunit"></a><span data-ttu-id="45f5c-103">dotnet test 및 xUnit을 사용하여 .NET Core에서 F# 라이브러리 유닛 테스트</span><span class="sxs-lookup"><span data-stu-id="45f5c-103">Unit testing F# libraries in .NET Core using dotnet test and xUnit</span></span>

<span data-ttu-id="45f5c-104">이 자습서에서는 샘플 솔루션을 단계별로 빌드하는 대화형 환경을 통해 단위 테스트 개념을 알아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="45f5c-105">미리 빌드된 솔루션을 사용하여 이 자습서를 진행하려는 경우 시작하기 전에 [샘플 코드를 보거나 다운로드](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp/).</span><span class="sxs-lookup"><span data-stu-id="45f5c-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp/) before you begin.</span></span> <span data-ttu-id="45f5c-106">다운로드 지침은 [샘플 및 자습서](../../samples-and-tutorials/index.md#view-and-download-samples)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="45f5c-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#view-and-download-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a><span data-ttu-id="45f5c-107">소스 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="45f5c-107">Creating the source project</span></span>

<span data-ttu-id="45f5c-108">셸 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-108">Open a shell window.</span></span> <span data-ttu-id="45f5c-109">솔루션을 저장할 *unit-testing-with-fsharp*라는 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-109">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="45f5c-110">이 새 디렉터리 내에서 `dotnet new sln`을 실행하여 새 솔루션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-110">Inside this new directory, run `dotnet new sln` to create a new solution.</span></span> <span data-ttu-id="45f5c-111">이렇게 하면 클래스 라이브러리와 단위 테스트 프로젝트를 모두 쉽게 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-111">This makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="45f5c-112">솔루션 디렉터리 내에 *MathService* 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-112">Inside the solution directory, create a *MathService* directory.</span></span> <span data-ttu-id="45f5c-113">따라서 지금까지의 디렉터리 및 파일 구조는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-113">The directory and file structure thus far is shown below:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="45f5c-114">*MathService*를 현재 디렉터리로 만들고 `dotnet new classlib -lang "F#"`을 실행하여 소스 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-114">Make *MathService* the current directory, and run `dotnet new classlib -lang "F#"` to create the source project.</span></span> <span data-ttu-id="45f5c-115">다음과 같이 수학 서비스의 실패 구현을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-115">You'll create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="45f5c-116">디렉터리를 다시 *unit-testing-with-fsharp* 디렉터리로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-116">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="45f5c-117">`dotnet sln add .\MathService\MathService.fsproj`를 실행하여 클래스 라이브러리 프로젝트를 솔루션에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-117">Run `dotnet sln add .\MathService\MathService.fsproj` to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="45f5c-118">테스트 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="45f5c-118">Creating the test project</span></span>

<span data-ttu-id="45f5c-119">다음으로 *MathService.Tests* 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-119">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="45f5c-120">다음 개요에는 디렉터리 구조가 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-120">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="45f5c-121">*MathService.Tests* 디렉터리를 현재 디렉터리로 만들고 `dotnet new xunit -lang "F#"`을 사용하여 새 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-121">Make the *MathService.Tests* directory the current directory and create a new project using `dotnet new xunit -lang "F#"`.</span></span> <span data-ttu-id="45f5c-122">xUnit을 테스트 라이브러리로 사용하는 테스트 프로젝트가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-122">This creates a test project that uses xUnit as the test library.</span></span> <span data-ttu-id="45f5c-123">생성된 템플릿은 *MathServiceTests.fsproj*에 Test Runner를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-123">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="45f5c-124">테스트 프로제트는 다른 패키지에 단위 테스트를 만들고 실행하도록 요구합니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="45f5c-125">이전 단계의 `dotnet new`는 xUnit 및 xUnit runner를 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-125">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="45f5c-126">이제 `MathService` 클래스 라이브러리를 프로젝트에 다른 종속성으로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-126">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="45f5c-127">`dotnet add reference` 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-127">Use the `dotnet add reference` command:</span></span>

```dotnetcli
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="45f5c-128">GitHub의 [샘플 리포지토리](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj)에서 전체 파일을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-128">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="45f5c-129">최종 솔루션 레이아웃은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-129">You have the following final solution layout:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
        Test Source Files
        MathServiceTests.fsproj
```

<span data-ttu-id="45f5c-130">*unit-testing-with-fsharp* 디렉터리에서 `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-130">Execute `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` in the *unit-testing-with-fsharp* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="45f5c-131">첫 번째 테스트 만들기</span><span class="sxs-lookup"><span data-stu-id="45f5c-131">Creating the first test</span></span>

<span data-ttu-id="45f5c-132">하나의 실패 테스트를 작성하고, 테스트가 성공하도록 만듭니다. 이 작업을 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-132">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="45f5c-133">*Tests.fs*를 열고 다음 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-133">Open *Tests.fs* and add the following code:</span></span>

```fsharp
[<Fact>]
let ``My test`` () =
    Assert.True(true)

[<Fact>]
let ``Fail every time`` () = Assert.True(false)
```

<span data-ttu-id="45f5c-134">`[<Fact>]` 특성은 Test Runner에서 실행하는 테스트 메서드를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-134">The `[<Fact>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="45f5c-135">*unit-testing-with-fsharp*에서 `dotnet test`를 실행하여 테스트 및 클래스 라이브러리를 빌드한 다음 테스트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-135">From the *unit-testing-with-fsharp*, execute `dotnet test` to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="45f5c-136">xUnit Test Runner에는 테스트를 실행할 프로그램 진입점이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-136">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="45f5c-137">`dotnet test`는 만든 단위 테스트 프로젝트를 사용하여 Test Runner를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-137">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="45f5c-138">이러한 두 테스트는 가장 기본적인 통과 및 실패 테스트를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-138">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="45f5c-139">`My test`는 통과하고 `Fail every time`은 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-139">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="45f5c-140">이제 `squaresOfOdds` 메서드에 대한 테스트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-140">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="45f5c-141">`squaresOfOdds` 메서드는 입력 시퀀스에 포함된 모든 홀수 정수 값 제곱의 시퀀스를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-141">The `squaresOfOdds` method returns a sequence of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="45f5c-142">이러한 모든 함수를 한 번에 작성하지 않고 기능의 유효성을 검사하는 테스트를 반복적으로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-142">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="45f5c-143">각 테스트 패스를 만들면 메서드에 필요한 기능이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-143">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="45f5c-144">작성할 수 있는 가장 간단한 테스트는 모든 짝수를 사용하여 `squaresOfOdds`를 호출하는 것입니다. 이 경우 결과는 빈 정수 시퀀스여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-144">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="45f5c-145">해당 테스트는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-145">Here's that test:</span></span>

```fsharp
[<Fact>]
let ``Sequence of Evens returns empty collection`` () =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

<span data-ttu-id="45f5c-146">테스트가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-146">Your test fails.</span></span> <span data-ttu-id="45f5c-147">구현은 아직 만들지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-147">You haven't created the implementation yet.</span></span> <span data-ttu-id="45f5c-148">`MathService` 클래스에서 작동하는 가장 간단한 코드를 작성하여 이 테스트를 통과시킵니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-148">Make this test pass by writing the simplest code in the `MathService` class that works:</span></span>

```fsharp
let squaresOfOdds xs =
    Seq.empty<int>
```

<span data-ttu-id="45f5c-149">*unit-testing-with-fsharp* 디렉터리에서 `dotnet test`를 다시 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-149">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="45f5c-150">`dotnet test` 명령은 `MathService` 프로젝트에 대한 빌드를 실행한 다음 `MathService.Tests` 프로젝트에 대한 빌드를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-150">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="45f5c-151">두 프로젝트를 모두 빌드한 후 이 단일 테스트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-151">After building both projects, it runs this single test.</span></span> <span data-ttu-id="45f5c-152">전달합니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-152">It passes.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="45f5c-153">요구 사항 완료</span><span class="sxs-lookup"><span data-stu-id="45f5c-153">Completing the requirements</span></span>

<span data-ttu-id="45f5c-154">이제 하나의 테스트를 통과했으므로 더 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-154">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="45f5c-155">다음의 단순한 사례에서는 유일한 홀수가 `1`인 시퀀스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-155">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="45f5c-156">숫자 1은 제곱이 1이므로 더 간단합니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-156">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="45f5c-157">이 테스트는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-157">Here's that next test:</span></span>

```fsharp
[<Fact>]
let ``Sequences of Ones and Evens returns Ones`` () =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

<span data-ttu-id="45f5c-158">`dotnet test`를 실행하면 테스트가 실행되고 새 테스트가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-158">Executing `dotnet test` runs your tests and shows you that the new test fails.</span></span> <span data-ttu-id="45f5c-159">이제 `squaresOfOdds` 메서드를 업데이트하여 이 새 테스트를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-159">Now, update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="45f5c-160">시퀀스에서 모든 짝수를 필터링하여 이 테스트가 통과하게 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-160">You filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="45f5c-161">이렇게 하려면 작은 필터 함수를 작성하고 `Seq.filter`를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-161">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

<span data-ttu-id="45f5c-162">한 가지 단계가 남았습니다. 즉, 각 홀수를 제곱합니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-162">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="45f5c-163">먼저 새 테스트를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-163">Start by writing a new test:</span></span>

```fsharp
[<Fact>]
let ``SquaresOfOdds works`` () =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.Equal(expected, actual)
```

<span data-ttu-id="45f5c-164">맵 작업을 통해 필터링된 시퀀스를 파이프하여 각 홀수의 제곱을 계산하는 방법으로 테스트를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-164">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
```

<span data-ttu-id="45f5c-165">작은 라이브러리 및 이 라이브러리에 대한 단위 테스트 집합을 작성했습니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-165">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="45f5c-166">새 패키지 및 테스트 추가가 정상 워크플로에 포함되도록 솔루션을 구조화했습니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-166">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="45f5c-167">애플리케이션의 목표를 해결하는 데 대부분의 시간과 노력을 들였습니다.</span><span class="sxs-lookup"><span data-stu-id="45f5c-167">You've concentrated most of your time and effort on solving the goals of the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="45f5c-168">참고 항목</span><span class="sxs-lookup"><span data-stu-id="45f5c-168">See also</span></span>

- [<span data-ttu-id="45f5c-169">dotnet new</span><span class="sxs-lookup"><span data-stu-id="45f5c-169">dotnet new</span></span>](../tools/dotnet-new.md)
- [<span data-ttu-id="45f5c-170">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="45f5c-170">dotnet sln</span></span>](../tools/dotnet-new.md)
- [<span data-ttu-id="45f5c-171">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="45f5c-171">dotnet add reference</span></span>](../tools/dotnet-add-reference.md)
- [<span data-ttu-id="45f5c-172">dotnet test</span><span class="sxs-lookup"><span data-stu-id="45f5c-172">dotnet test</span></span>](../tools/dotnet-test.md)
