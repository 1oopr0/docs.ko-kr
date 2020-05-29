---
title: 분기 및 루프 - C# 소개 자습서
description: 분기 및 루프에 관한 이 자습서에서는 C# 코드를 작성하여 문을 반복적으로 실행하기 위한 조건부 분기 및 루프를 지원하는 언어 구문을 살펴봅니다.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: d67cfe359634783bb542e9ac34df52a095b45c20
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396874"
---
# <a name="learn-conditional-logic-with-branch-and-loop-statements"></a><span data-ttu-id="a5d94-103">분기 및 루프 문이 포함된 조건부 논리 알아보기</span><span class="sxs-lookup"><span data-stu-id="a5d94-103">Learn conditional logic with branch and loop statements</span></span>

<span data-ttu-id="a5d94-104">이 자습서에서는 변수를 검사하고 해당 변수에 따라 실행 경로를 변경하는 코드를 작성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-104">This tutorial teaches you how to write code that examines variables and changes the execution path based on those variables.</span></span> <span data-ttu-id="a5d94-105">C# 코드를 작성하고 컴파일 및 실행 결과를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="a5d94-106">이 자습서에는 C#에서 분기 및 루프 구문을 살펴보는 일련의 단원이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-106">The tutorial contains a series of lessons that explore branching and looping constructs in C#.</span></span> <span data-ttu-id="a5d94-107">이러한 단원에서는 C# 언어의 기본 사항을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="a5d94-108">이 자습서에서는 개발에 사용할 수 있는 머신이 있다고 예상합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-108">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="a5d94-109">.NET 자습서 [Hello World 10분 완성](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro)에는 Windows, Linux 또는 macOS의 로컬 개발 환경 설정에 대한 지침이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-109">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="a5d94-110">사용할 명령에 대한 간단한 개요는 [개발 도구 익히기](local-environment.md)에 자세한 정보의 링크와 함께 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-110">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="make-decisions-using-the-if-statement"></a><span data-ttu-id="a5d94-111">`if` 문을 사용하여 결정하기</span><span class="sxs-lookup"><span data-stu-id="a5d94-111">Make decisions using the `if` statement</span></span>

<span data-ttu-id="a5d94-112">*branches-tutorial*이라는 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-112">Create a directory named *branches-tutorial*.</span></span> <span data-ttu-id="a5d94-113">현재 디렉터리로 만들고 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-113">Make that the current directory and run the following command:</span></span>

```dotnetcli
dotnet new console -n BranchesAndLoops -o .
```

<span data-ttu-id="a5d94-114">이 명령은 현재 디렉터리에 새 .NET Core 콘솔 애플리케이션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-114">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="a5d94-115">원하는 편집기에서 *Program.cs*를 열고 `Console.WriteLine("Hello World!");` 줄을 다음 코드로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-115">Open *Program.cs* in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code:</span></span>

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

<span data-ttu-id="a5d94-116">콘솔 창에 `dotnet run`을 입력하여 이 코드를 사용해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-116">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="a5d94-117">“The answer is greater than 10.”(답은 10보다 큽니다.)이라는 메시지가</span><span class="sxs-lookup"><span data-stu-id="a5d94-117">You should see the message "The answer is greater than 10."</span></span> <span data-ttu-id="a5d94-118">콘솔에 출력되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-118">printed to your console.</span></span>

<span data-ttu-id="a5d94-119">합계가 10보다 작도록 `b`의 선언을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-119">Modify the declaration of `b` so that the sum is less than 10:</span></span>

```csharp
int b = 3;
```

<span data-ttu-id="a5d94-120">`dotnet run`을 다시 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-120">Type `dotnet run` again.</span></span> <span data-ttu-id="a5d94-121">답이 10보다 작기 때문에 아무것도 출력되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-121">Because the answer is less than 10, nothing is printed.</span></span> <span data-ttu-id="a5d94-122">테스트하는 **조건**은 false입니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-122">The **condition** you're testing is false.</span></span> <span data-ttu-id="a5d94-123">`if` 문에 대해 가능한 분기 중 하나(true 분기)만 작성했기 때문에 실행할 코드가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-123">You don't have any code to execute because you've only written one of the possible branches for an `if` statement: the true branch.</span></span>

> [!TIP]
> <span data-ttu-id="a5d94-124">C# (또는 다른 프로그래밍 언어)를 살펴보면서 코드를 작성할 때 실수를 하게 될 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-124">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="a5d94-125">컴파일러가 오류를 찾아 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-125">The compiler will find and report the errors.</span></span> <span data-ttu-id="a5d94-126">오류 출력 및 오류를 생성한 코드를 자세히 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-126">Look closely at the error output and the code that generated the error.</span></span> <span data-ttu-id="a5d94-127">일반적으로 컴파일러 오류는 문제를 찾는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-127">The compiler error can usually help you find the problem.</span></span>

<span data-ttu-id="a5d94-128">이 첫 번째 샘플에서는 `if`의 기능과 부울 형식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-128">This first sample shows the power of `if` and Boolean types.</span></span> <span data-ttu-id="a5d94-129">*부울*은 `true` 또는 `false`의 두 값 중 하나를 가질 수 있는 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-129">A *Boolean* is a variable that can have one of two values: `true` or `false`.</span></span> <span data-ttu-id="a5d94-130">C#은 부울 변수에 대한 특수 형식 `bool`을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-130">C# defines a special type, `bool` for Boolean variables.</span></span> <span data-ttu-id="a5d94-131">`if` 문은 `bool`의 값을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-131">The `if` statement checks the value of a `bool`.</span></span> <span data-ttu-id="a5d94-132">값이 `true`인 경우 `if` 뒤의 문이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-132">When the value is `true`, the statement following the `if` executes.</span></span> <span data-ttu-id="a5d94-133">그렇지 않으면 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-133">Otherwise, it's skipped.</span></span>

<span data-ttu-id="a5d94-134">조건을 확인하고 해당 조건에 따라 문을 실행하는 이 프로세스는 강력합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-134">This process of checking conditions and executing statements based on those conditions is powerful.</span></span>

## <a name="make-if-and-else-work-together"></a><span data-ttu-id="a5d94-135">if와 else를 함께 사용하기</span><span class="sxs-lookup"><span data-stu-id="a5d94-135">Make if and else work together</span></span>

<span data-ttu-id="a5d94-136">true 분기와 false 분기의 여러 코드를 실행하려면 조건이 false일 때 실행되는 `else` 분기를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-136">To execute different code in both the true and false branches, you create an `else` branch that executes when the condition is false.</span></span> <span data-ttu-id="a5d94-137">다음과 같이 해보세요.</span><span class="sxs-lookup"><span data-stu-id="a5d94-137">Try this.</span></span> <span data-ttu-id="a5d94-138">아래 코드의 마지막 두 줄을 `Main` 메서드에 추가합니다(이미 처음 네 줄은 있음).</span><span class="sxs-lookup"><span data-stu-id="a5d94-138">Add the last two lines in the code below to your `Main` method (you should already have the first four):</span></span>

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

<span data-ttu-id="a5d94-139">`else` 키워드 뒤의 문은 테스트하는 조건이 `false`인 경우에만 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-139">The statement following the `else` keyword executes only when the condition being tested is `false`.</span></span> <span data-ttu-id="a5d94-140">`if` 및 `else`를 부울 조건과 결합하면 `true`와 `false` 조건을 모두 처리하는 데 필요한 모든 기능이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-140">Combining `if` and `else` with Boolean conditions provides all the power you need to handle both a `true` and a `false` condition.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a5d94-141">`if` 및 `else` 문 아래의 들여쓰기는 사용자가 보기 편하도록 하기 위함입니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-141">The indentation under the `if` and `else` statements is for human readers.</span></span>
> <span data-ttu-id="a5d94-142">C# 언어는 들여쓰기 또는 공백을 중요하게 취급하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-142">The C# language doesn't treat indentation or white space as significant.</span></span>
> <span data-ttu-id="a5d94-143">`if` 또는 `else` 키워드 뒤의 문은 조건에 따라 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-143">The statement following the `if` or `else` keyword will be executed based on the condition.</span></span> <span data-ttu-id="a5d94-144">이 자습서의 모든 샘플에서는 문의 제어 흐름을 기준으로 줄을 들여쓰는 일반적인 방법을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-144">All the samples in this tutorial follow a common practice to indent lines based on the control flow of statements.</span></span>

<span data-ttu-id="a5d94-145">들여쓰기는 중요하지 않기 때문에 `{` 및 `}`를 사용하여 두 개 이상의 문이 조건부로 실행되는 블록의 일부가 되는 시기를 나타내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-145">Because indentation isn't significant, you need to use `{` and `}` to indicate when you want more than one statement to be part of the block that executes conditionally.</span></span> <span data-ttu-id="a5d94-146">C# 프로그래머는 일반적으로 모든 `if` 및 `else` 절에서 중괄호를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-146">C# programmers typically use those braces on all `if` and `else` clauses.</span></span> <span data-ttu-id="a5d94-147">다음 예제는 앞서 작성한 코드와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-147">The following example is the same as the one you created.</span></span> <span data-ttu-id="a5d94-148">다음 코드와 일치하도록 위의 코드를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-148">Modify your code above to match the following code:</span></span>

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
{
    Console.WriteLine("The answer is greater than 10");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
}
```

> [!TIP]
> <span data-ttu-id="a5d94-149">이 자습서의 나머지 부분에서 코드 샘플에는 일반적인 방법에 따라 모두 중괄호가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-149">Through the rest of this tutorial, the code samples all include the braces, following accepted practices.</span></span>

<span data-ttu-id="a5d94-150">더 복잡한 조건을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-150">You can test more complicated conditions.</span></span> <span data-ttu-id="a5d94-151">`Main` 메서드에서 지금까지 작성한 코드 뒤에 다음 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-151">Add the following code in your `Main` method after the code you've written so far:</span></span>

```csharp
int c = 4;
if ((a + b + c > 10) && (a == b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("And the first number is equal to the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("Or the first number is not equal to the second");
}
```

<span data-ttu-id="a5d94-152">`==` 기호는 같음을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-152">The `==` symbol tests for *equality*.</span></span> <span data-ttu-id="a5d94-153">`==`을 사용하면 같음 테스트가 `a = 5`에서 확인한 할당과 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-153">Using `==` distinguishes the test for equality from assignment, which you saw in `a = 5`.</span></span>

<span data-ttu-id="a5d94-154">`&&`는 “and”를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-154">The `&&` represents "and".</span></span> <span data-ttu-id="a5d94-155">true 분기에서 문을 실행하려면 두 조건이 모두 true여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-155">It means both conditions must be true to execute the statement in the true branch.</span></span>  <span data-ttu-id="a5d94-156">이러한 예제에서는 `{` 및 `}`로 문을 묶으면 각 조건부 분기에 여러 문을 가질 수 있음도 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-156">These examples also show that you can have multiple statements in each conditional branch, provided you enclose them in `{` and `}`.</span></span>

<span data-ttu-id="a5d94-157">`||`을 사용하여 “or”를 나타낼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-157">You can also use  `||` to represent "or".</span></span> <span data-ttu-id="a5d94-158">지금까지 작성한 코드 뒤에 다음 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-158">Add the following code after what you've written so far:</span></span>

```csharp
if ((a + b + c > 10) || (a == b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("Or the first number is equal to the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("And the first number is not equal to the second");
}
```

<span data-ttu-id="a5d94-159">`a`, `b` 및 `c`의 값을 수정하고 `&&` 및 `||` 간에 전환하여 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-159">Modify the values of `a`, `b`, and `c` and switch between `&&` and `||` to explore.</span></span> <span data-ttu-id="a5d94-160">`&&` 및 `||` 연산자가 어떻게 작동하는지 더 잘 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-160">You'll gain more understanding of how the `&&` and `||` operators work.</span></span>

<span data-ttu-id="a5d94-161">첫 번째 단계를 완료했습니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-161">You've finished the first step.</span></span> <span data-ttu-id="a5d94-162">다음 섹션을 시작하기 전에 현재 코드를 별도의 메서드로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-162">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="a5d94-163">이렇게 하면 새 예제 작업을 쉽게 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-163">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="a5d94-164">`Main` 메서드의 이름을 `ExploreIf`로 바꾸고 `ExploreIf`를 호출하는 새 `Main` 메서드를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-164">Rename your `Main` method to `ExploreIf` and write a new `Main` method that calls `ExploreIf`.</span></span> <span data-ttu-id="a5d94-165">작업을 마치면 코드가 다음과 같이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-165">When you've finished, your code should look like this:</span></span>

```csharp
using System;

namespace BranchesAndLoops
{
    class Program
    {
        static void ExploreIf()
        {
            int a = 5;
            int b = 3;
            if (a + b > 10)
            {
                Console.WriteLine("The answer is greater than 10");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
            }

            int c = 4;
            if ((a + b + c > 10) && (a > b))
            {
                Console.WriteLine("The answer is greater than 10");
                Console.WriteLine("And the first number is greater than the second");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
                Console.WriteLine("Or the first number is not greater than the second");
            }

            if ((a + b + c > 10) || (a > b))
            {
                Console.WriteLine("The answer is greater than 10");
                Console.WriteLine("Or the first number is greater than the second");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
                Console.WriteLine("And the first number is not greater than the second");
            }
        }

        static void Main(string[] args)
        {
            ExploreIf();
        }
    }
}
```

<span data-ttu-id="a5d94-166">`ExploreIf()`에 대한 호출을 주석으로 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-166">Comment out the call to `ExploreIf()`.</span></span> <span data-ttu-id="a5d94-167">그러면 이 섹션에서 작업할 때 출력이 덜 복잡해집니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-167">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//ExploreIf();
```

<span data-ttu-id="a5d94-168">`//`는 C#에서 **주석**을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-168">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="a5d94-169">주석은 소스 코드에 유지하되 코드로 실행하지는 않으려는 모든 텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-169">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="a5d94-170">컴파일러는 주석에서 실행 코드를 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-170">The compiler doesn't generate any executable code from comments.</span></span>

## <a name="use-loops-to-repeat-operations"></a><span data-ttu-id="a5d94-171">루프를 사용하여 작업 반복</span><span class="sxs-lookup"><span data-stu-id="a5d94-171">Use loops to repeat operations</span></span>

<span data-ttu-id="a5d94-172">이 섹션에서는 **루프**를 사용하여 문을 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-172">In this section, you use **loops** to repeat statements.</span></span> <span data-ttu-id="a5d94-173">`Main` 메서드에 다음 코드를 사용해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-173">Try this code in your `Main` method:</span></span>

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

<span data-ttu-id="a5d94-174">`while` 문은 조건을 검사하고 `while` 뒤에 있는 문 또는 문 블록을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-174">The `while` statement checks a condition and executes the statement or statement block following the `while`.</span></span> <span data-ttu-id="a5d94-175">조건이 false가 될 때까지 반복적으로 조건을 확인하고 해당 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-175">It repeatedly checks the condition and executing those statements until the condition is false.</span></span>

<span data-ttu-id="a5d94-176">이 예제에서는 다른 새 연산자가 하나 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-176">There's one other new operator in this example.</span></span> <span data-ttu-id="a5d94-177">`counter` 변수 뒤의 `++`는 **증가** 연산자입니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-177">The `++` after the `counter` variable is the **increment** operator.</span></span> <span data-ttu-id="a5d94-178">이 연산자는 `counter`의 값에 1을 더하고 해당 값을 `counter` 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-178">It adds 1 to the value of `counter` and stores that value in the `counter` variable.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a5d94-179">코드를 실행할 때 `while` 루프 조건이 false로 바뀌는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-179">Make sure that the `while` loop condition changes to false as you execute the code.</span></span> <span data-ttu-id="a5d94-180">그러하지 않으면 프로그램이 종료되지 않는 **무한 루프**를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-180">Otherwise, you create an **infinite loop** where your program never ends.</span></span> <span data-ttu-id="a5d94-181">이러한 내용이 이 샘플에 설명되어 있지는 않은데, **CTRL-C** 또는 다른 방법을 사용하여 프로그램을 강제 종료해야 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-181">That is not demonstrated in this sample, because you have to force your program to quit using **CTRL-C** or other means.</span></span>

<span data-ttu-id="a5d94-182">`while` 루프는 `while` 뒤에 코드를 실행하기 전에 조건을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-182">The `while` loop tests the condition before executing the code following the `while`.</span></span> <span data-ttu-id="a5d94-183">`do` ... `while` 루프는 코드를 먼저 실행한 후 조건을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-183">The `do` ... `while` loop executes the code first, and then checks the condition.</span></span> <span data-ttu-id="a5d94-184">*do while* 루프는 다음 코드에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-184">The *do while* loop is shown in the following code:</span></span>

```csharp
int counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

<span data-ttu-id="a5d94-185">이 `do` 루프 및 이전 `while` 루프는 같은 출력을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-185">This `do` loop and the earlier `while` loop produce the same output.</span></span>

## <a name="work-with-the-for-loop"></a><span data-ttu-id="a5d94-186">for 루프 작업</span><span class="sxs-lookup"><span data-stu-id="a5d94-186">Work with the for loop</span></span>

<span data-ttu-id="a5d94-187">C#에서는 일반적으로 **for** 루프가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-187">The **for** loop is commonly used in C#.</span></span> <span data-ttu-id="a5d94-188">Main() 메서드에 다음 코드를 사용해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-188">Try this code in your Main() method:</span></span>

```csharp
for (int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
}
```

<span data-ttu-id="a5d94-189">이전 코드는 `while` 루프 및 이미 사용한 `do` 루프와 동일한 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-189">The previous code does the same work as the `while` loop and the `do` loop you've already used.</span></span> <span data-ttu-id="a5d94-190">`for` 문에는 작동 방식을 제어하는 세 부분이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-190">The `for` statement has three parts that control how it works.</span></span>

<span data-ttu-id="a5d94-191">첫 번째 부분은 **for 이니셜라이저입니다**. `int index = 0;`은 `index`가 루프 변수임을 선언하고 첫 번째 값을 `0`으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-191">The first part is the **for initializer**: `int index = 0;` declares that `index` is the loop variable, and sets its initial value to `0`.</span></span>

<span data-ttu-id="a5d94-192">중간 부분은 **for 조건입니다**. `index < 10`은 이 `for` 루프가 카운터 값이 10보다 작으면 계속 실행됨을 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-192">The middle part is the **for condition**: `index < 10` declares that this `for` loop continues to execute as long as the value of counter is less than 10.</span></span>

<span data-ttu-id="a5d94-193">마지막 부분은 **for 반복기입니다**. `index++`는 `for` 문 다음의 블록을 실행한 후 루프 변수를 수정하는 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-193">The final part is the **for iterator**: `index++` specifies how to modify the loop variable after executing the block following the `for` statement.</span></span> <span data-ttu-id="a5d94-194">여기서 `index`는 블록이 실행될 때마다 1씩 증가하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-194">Here, it specifies that `index` should be incremented by 1 each time the block executes.</span></span>

<span data-ttu-id="a5d94-195">직접 실험해 보세요.</span><span class="sxs-lookup"><span data-stu-id="a5d94-195">Experiment yourself.</span></span> <span data-ttu-id="a5d94-196">다음 변형을 각각 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-196">Try each of the following variations:</span></span>

- <span data-ttu-id="a5d94-197">다른 값으로 시작하도록 이니셜라이저를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-197">Change the initializer to start at a different value.</span></span>
- <span data-ttu-id="a5d94-198">다른 값에서 중지하도록 조건을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-198">Change the condition to stop at a different value.</span></span>

<span data-ttu-id="a5d94-199">완료하면, 학습한 내용을 토대로 직접 코드를 작성해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-199">When you're done, let's move on to write some code yourself to use what you've learned.</span></span>

<span data-ttu-id="a5d94-200">이 자습서에서 다루지 않은 다른 반복 문이 하나 있는데, `foreach` 문이 그것입니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-200">There's one other looping statement that isn't covered in this tutorial: the `foreach` statement.</span></span> <span data-ttu-id="a5d94-201">`foreach` 문은 항목 시퀀스의 모든 항목에 대해 해당 문을 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-201">The `foreach` statement repeats its statement for every item in a sequence of items.</span></span> <span data-ttu-id="a5d94-202">컬렉션과 함께 사용되는 경우가 가장 많으므로 다음 자습서에서 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-202">It's most often used with *collections*, so it's covered in the next tutorial.</span></span>

## <a name="created-nested-loops"></a><span data-ttu-id="a5d94-203">중첩 루프 만들기</span><span class="sxs-lookup"><span data-stu-id="a5d94-203">Created nested loops</span></span>

<span data-ttu-id="a5d94-204">`while`, `do` 또는 `for` 루프를 다른 루프 내에 중첩하여 내부 루프에 있는 각 항목과 외부 루프에 있는 각 항목의 조합을 사용하여 행렬을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-204">A `while`, `do`, or `for` loop can be nested inside another loop to create a matrix using the combination of each item in the outer loop with each item in the inner loop.</span></span> <span data-ttu-id="a5d94-205">행과 열을 나타내는 영숫자 쌍 세트를 작성하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-205">Let's do that to build a set of alphanumeric pairs to represent rows and columns.</span></span>

<span data-ttu-id="a5d94-206">하나의 `for` 루프가 행을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-206">One `for` loop can generate the rows:</span></span>

```csharp
for (int row = 1; row < 11; row++)
{
    Console.WriteLine($"The row is {row}");
}
```

<span data-ttu-id="a5d94-207">다른 루프는 열을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-207">Another loop can generate the columns:</span></span>

```csharp
for (char column = 'a'; column < 'k'; column++)
{
    Console.WriteLine($"The column is {column}");
}
```

<span data-ttu-id="a5d94-208">한 루프를 다른 루프 안에 중첩하여 쌍을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-208">You can nest one loop inside the other to form pairs:</span></span>

```csharp
for (int row = 1; row < 11; row++)
{
    for (char column = 'a'; column < 'k'; column++)
    {
        Console.WriteLine($"The cell is ({row}, {column})");
    }
}
```

<span data-ttu-id="a5d94-209">내부 루프의 전체 실행마다 외부 루프가 한 번씩 증가하는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-209">You can see that the outer loop increments once for each full run of the inner loop.</span></span> <span data-ttu-id="a5d94-210">행과 열 중첩을 반대로 바꾸고 변경 내용을 직접 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="a5d94-210">Reverse the row and column nesting, and see the changes for yourself.</span></span>

## <a name="combine-branches-and-loops"></a><span data-ttu-id="a5d94-211">분기 및 루프 결합</span><span class="sxs-lookup"><span data-stu-id="a5d94-211">Combine branches and loops</span></span>

<span data-ttu-id="a5d94-212">이제 C# 언어로 된 `if` 문과 루프 구조를 확인했습니다. C# 코드를 작성하여 3으로 나눌 수 있는, 1에서 20까지의 모든 정수의 합계를 찾을 수 있는지 확인해 보세요.</span><span class="sxs-lookup"><span data-stu-id="a5d94-212">Now that you've seen the `if` statement and the looping constructs in the C# language, see if you can write C# code to find the sum of all integers 1 through 20 that are divisible by 3.</span></span>  <span data-ttu-id="a5d94-213">다음은 몇 가지 힌트입니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-213">Here are a few hints:</span></span>

- <span data-ttu-id="a5d94-214">`%` 연산자는 나누기 연산의 나머지를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-214">The `%` operator gives you the remainder of a division operation.</span></span>
- <span data-ttu-id="a5d94-215">`if` 문은 숫자가 합계의 일부여야 하는지를 확인하는 조건을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-215">The `if` statement gives you the condition to see if a number should be part of the sum.</span></span>
- <span data-ttu-id="a5d94-216">`for` 루프는 1에서 20까지의 모든 숫자에 대해 일련의 단계를 반복하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-216">The `for` loop can help you repeat a series of steps for all the numbers 1 through 20.</span></span>

<span data-ttu-id="a5d94-217">직접 시도해 보세요.</span><span class="sxs-lookup"><span data-stu-id="a5d94-217">Try it yourself.</span></span> <span data-ttu-id="a5d94-218">그런 다음 어떻게 했는지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="a5d94-218">Then check how you did.</span></span> <span data-ttu-id="a5d94-219">답으로 63을 받아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-219">You should get 63 for an answer.</span></span> <span data-ttu-id="a5d94-220">[GitHub에서 완성된 코드를 보고](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54) 가능한 한 가지 답을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-220">You can see one possible answer by [viewing the completed code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).</span></span>

<span data-ttu-id="a5d94-221">“분기 및 루프” 자습서를 완료했습니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-221">You've completed the "branches and loops" tutorial.</span></span>

<span data-ttu-id="a5d94-222">자체 개발 환경에서 [배열 및 컬렉션](arrays-and-collections.md) 자습서를 계속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-222">You can continue with the [Arrays and collections](arrays-and-collections.md) tutorial in your own development environment.</span></span>

<span data-ttu-id="a5d94-223">다음 문서에서 이러한 개념을 더 자세히 알아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5d94-223">You can learn more about these concepts in these articles:</span></span>

- [<span data-ttu-id="a5d94-224">If 및 else 문</span><span class="sxs-lookup"><span data-stu-id="a5d94-224">If and else statement</span></span>](../../language-reference/keywords/if-else.md)
- [<span data-ttu-id="a5d94-225">While 문</span><span class="sxs-lookup"><span data-stu-id="a5d94-225">While statement</span></span>](../../language-reference/keywords/while.md)
- [<span data-ttu-id="a5d94-226">Do 문</span><span class="sxs-lookup"><span data-stu-id="a5d94-226">Do statement</span></span>](../../language-reference/keywords/do.md)
- [<span data-ttu-id="a5d94-227">For 문</span><span class="sxs-lookup"><span data-stu-id="a5d94-227">For statement</span></span>](../../language-reference/keywords/for.md)
