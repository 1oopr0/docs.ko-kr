---
title: Override 및 New 키워드를 사용해야 하는 경우 - C# 프로그래밍 가이드
description: C#에서 new 및 override 키워드를 사용하여 기본 및 파생 클래스에서 이름이 동일한 메서드가 상호 작용하는 방식을 지정합니다.
ms.date: 07/20/2015
helpviewer_keywords:
- override keyword [C#]
- new keyword [C#]
- polymorphism [C#], using override and new [C#]
ms.assetid: 323db184-b136-46fc-8839-007886e7e8b0
ms.openlocfilehash: 732a37c08b4c7bb998a7cc5dcfbd00d4e706b06c
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864542"
---
# <a name="knowing-when-to-use-override-and-new-keywords-c-programming-guide"></a><span data-ttu-id="a72ff-103">Override 및 New 키워드를 사용해야 하는 경우(C# 프로그래밍 가이드)</span><span class="sxs-lookup"><span data-stu-id="a72ff-103">Knowing When to Use Override and New Keywords (C# Programming Guide)</span></span>

<span data-ttu-id="a72ff-104">C#에서는 파생 클래스의 메서드가 기본 클래스의 메서드와 동일한 이름을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-104">In C#, a method in a derived class can have the same name as a method in the base class.</span></span> <span data-ttu-id="a72ff-105">[new](../../language-reference/keywords/new-modifier.md) 및 [override](../../language-reference/keywords/override.md) 키워드를 사용하여 메서드가 상호 작용하는 방식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-105">You can specify how the methods interact by using the [new](../../language-reference/keywords/new-modifier.md) and [override](../../language-reference/keywords/override.md) keywords.</span></span> <span data-ttu-id="a72ff-106">`override` 한정자는 기본 클래스 `virtual` 메서드를 *확장*하고, `new` 한정자는 기본 클래스 메서드를 *숨깁니다*.</span><span class="sxs-lookup"><span data-stu-id="a72ff-106">The `override` modifier *extends* the base class `virtual` method, and the `new` modifier *hides* an accessible base class method.</span></span> <span data-ttu-id="a72ff-107">이 항목의 예제에서는 차이점을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-107">The difference is illustrated in the examples in this topic.</span></span>  
  
 <span data-ttu-id="a72ff-108">콘솔 애플리케이션에서 `BaseClass` 및 `DerivedClass`라는 두 클래스를 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-108">In a console application, declare the following two classes, `BaseClass` and `DerivedClass`.</span></span> <span data-ttu-id="a72ff-109">`DerivedClass`는 `BaseClass`에서 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-109">`DerivedClass` inherits from `BaseClass`.</span></span>  
  
```csharp  
class BaseClass  
{  
    public void Method1()  
    {  
        Console.WriteLine("Base - Method1");  
    }  
}  
  
class DerivedClass : BaseClass  
{  
    public void Method2()  
    {  
        Console.WriteLine("Derived - Method2");  
    }  
}  
```  
  
 <span data-ttu-id="a72ff-110">`Main` 메서드에서 `bc`, `dc` 및 `bcdc` 변수를 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-110">In the `Main` method, declare variables `bc`, `dc`, and `bcdc`.</span></span>  
  
- <span data-ttu-id="a72ff-111">`bc`는 `BaseClass` 형식이고, 해당 값은 `BaseClass` 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-111">`bc` is of type `BaseClass`, and its value is of type `BaseClass`.</span></span>  
  
- <span data-ttu-id="a72ff-112">`dc`는 `DerivedClass` 형식이고, 해당 값은 `DerivedClass` 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-112">`dc` is of type `DerivedClass`, and its value is of type `DerivedClass`.</span></span>  
  
- <span data-ttu-id="a72ff-113">`bcdc`는 `BaseClass` 형식이고, 해당 값은 `DerivedClass` 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-113">`bcdc` is of type `BaseClass`, and its value is of type `DerivedClass`.</span></span> <span data-ttu-id="a72ff-114">이 변수에 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-114">This is the variable to pay attention to.</span></span>  
  
 <span data-ttu-id="a72ff-115">`bc` 및 `bcdc`는 `BaseClass` 형식이기 때문에 캐스팅을 사용하지 않는 경우 `Method1`에 직접 액세스할 수만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-115">Because `bc` and `bcdc` have type `BaseClass`, they can only directly access `Method1`, unless you use casting.</span></span> <span data-ttu-id="a72ff-116">`dc` 변수는 `Method1` 및 `Method2` 둘 다에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-116">Variable `dc` can access both `Method1` and `Method2`.</span></span> <span data-ttu-id="a72ff-117">이러한 관계는 다음 코드에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-117">These relationships are shown in the following code.</span></span>  
  
```csharp  
class Program  
{  
    static void Main(string[] args)  
    {  
        BaseClass bc = new BaseClass();  
        DerivedClass dc = new DerivedClass();  
        BaseClass bcdc = new DerivedClass();  
  
        bc.Method1();  
        dc.Method1();  
        dc.Method2();  
        bcdc.Method1();  
    }  
    // Output:  
    // Base - Method1  
    // Base - Method1  
    // Derived - Method2  
    // Base - Method1  
}  
```  
  
 <span data-ttu-id="a72ff-118">다음 `Method2` 메서드를 `BaseClass`에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-118">Next, add the following `Method2` method to `BaseClass`.</span></span> <span data-ttu-id="a72ff-119">이 메서드의 시그니처는 `DerivedClass`에 있는 `Method2` 메서드의 시그니처와 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-119">The signature of this method matches the signature of the `Method2` method in `DerivedClass`.</span></span>  
  
```csharp  
public void Method2()  
{  
    Console.WriteLine("Base - Method2");  
}  
```  
  
 <span data-ttu-id="a72ff-120">이제 `BaseClass`에 `Method2` 메서드가 있으므로 다음 코드와 같이 `BaseClass` 변수 `bc` 및 `bcdc`에 대해 두 번째 호출 문을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-120">Because `BaseClass` now has a `Method2` method, a second calling statement can be added for `BaseClass` variables `bc` and `bcdc`, as shown in the following code.</span></span>  
  
```csharp  
bc.Method1();  
bc.Method2();  
dc.Method1();  
dc.Method2();  
bcdc.Method1();  
bcdc.Method2();  
```  
  
 <span data-ttu-id="a72ff-121">프로젝트를 빌드할 때 `BaseClass`에 `Method2` 메서드를 추가하면 경고가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-121">When you build the project, you see that the addition of the `Method2` method in `BaseClass` causes a warning.</span></span> <span data-ttu-id="a72ff-122">`DerivedClass`의 `Method2` 메서드가 `BaseClass`의 `Method2` 메서드를 숨긴다는 경고가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-122">The warning says that the `Method2` method in `DerivedClass` hides the `Method2` method in `BaseClass`.</span></span> <span data-ttu-id="a72ff-123">이러한 결과를 원한다면 `Method2` 정의에 `new` 키워드를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-123">You are advised to use the `new` keyword in the `Method2` definition if you intend to cause that result.</span></span> <span data-ttu-id="a72ff-124">또는 `Method2` 메서드 중 하나의 이름을 바꿔 경고를 해결할 수 있지만 이 방법이 항상 실현 가능한 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-124">Alternatively, you could rename one of the `Method2` methods to resolve the warning, but that is not always practical.</span></span>  
  
 <span data-ttu-id="a72ff-125">`new`를 추가하기 전에 프로그램을 실행하여 추가 호출 문에서 생성되는 출력을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-125">Before adding `new`, run the program to see the output produced by the additional calling statements.</span></span> <span data-ttu-id="a72ff-126">다음과 같은 결과가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-126">The following results are displayed.</span></span>  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Base - Method1  
// Derived - Method2  
// Base - Method1  
// Base - Method2  
```  
  
 <span data-ttu-id="a72ff-127">`new` 키워드는 해당 출력을 생성하는 관계를 유지하지만 경고는 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-127">The `new` keyword preserves the relationships that produce that output, but it suppresses the warning.</span></span> <span data-ttu-id="a72ff-128">`BaseClass` 형식인 변수는 계속해서 `BaseClass`의 멤버에 액세스하고, `DerivedClass` 형식인 변수는 계속해서 `DerivedClass`의 멤버에 먼저 액세스한 다음 `BaseClass`에서 상속된 멤버를 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-128">The variables that have type `BaseClass` continue to access the members of `BaseClass`, and the variable that has type `DerivedClass` continues to access members in `DerivedClass` first, and then to consider members inherited from `BaseClass`.</span></span>  
  
 <span data-ttu-id="a72ff-129">경고를 표시하지 않으려면 다음 코드와 같이 `DerivedClass`에 있는 `Method2`의 정의에 `new` 한정자를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-129">To suppress the warning, add the `new` modifier to the definition of `Method2` in `DerivedClass`, as shown in the following code.</span></span> <span data-ttu-id="a72ff-130">`public` 앞이나 뒤에 한정자를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-130">The modifier can be added before or after `public`.</span></span>  
  
```csharp  
public new void Method2()  
{  
    Console.WriteLine("Derived - Method2");  
}  
```  
  
 <span data-ttu-id="a72ff-131">프로그램을 다시 실행하여 출력이 변경되지 않았는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-131">Run the program again to verify that the output has not changed.</span></span> <span data-ttu-id="a72ff-132">또한 경고가 더 이상 나타나지 않는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-132">Also verify that the warning no longer appears.</span></span> <span data-ttu-id="a72ff-133">`new`를 사용하면 수정하는 멤버가 기본 클래스에서 상속된 멤버를 숨김을 인식하고 있다고 어설션하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-133">By using `new`, you are asserting that you are aware that the member that it modifies hides a member that is inherited from the base class.</span></span> <span data-ttu-id="a72ff-134">상속을 통한 이름 숨기기에 대한 자세한 내용은 [new 한정자](../../language-reference/keywords/new-modifier.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a72ff-134">For more information about name hiding through inheritance, see [new Modifier](../../language-reference/keywords/new-modifier.md).</span></span>  
  
 <span data-ttu-id="a72ff-135">이 동작을 `override`를 사용할 경우의 효과와 비교하려면 다음 메서드를 `DerivedClass`에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-135">To contrast this behavior to the effects of using `override`, add the following method to `DerivedClass`.</span></span> <span data-ttu-id="a72ff-136">`public` 앞이나 뒤에 `override` 한정자를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-136">The `override` modifier can be added before or after `public`.</span></span>  
  
```csharp  
public override void Method1()  
{  
    Console.WriteLine("Derived - Method1");  
}  
```  
  
 <span data-ttu-id="a72ff-137">`BaseClass`에 있는 `Method1`의 정의에 `virtual` 한정자를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-137">Add the `virtual` modifier to the definition of `Method1` in `BaseClass`.</span></span> <span data-ttu-id="a72ff-138">`public` 앞이나 뒤에 `virtual` 한정자를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-138">The `virtual` modifier can be added before or after `public`.</span></span>  
  
```csharp  
public virtual void Method1()  
{  
    Console.WriteLine("Base - Method1");  
}  
```  
  
 <span data-ttu-id="a72ff-139">프로젝트를 다시 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-139">Run the project again.</span></span> <span data-ttu-id="a72ff-140">특히 다음 출력의 마지막 두 줄을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-140">Notice especially the last two lines of the following output.</span></span>  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Derived - Method1  
// Derived - Method2  
// Derived - Method1  
// Base - Method2  
```  
  
 <span data-ttu-id="a72ff-141">`override` 한정자를 사용하면 `bcdc`가 `DerivedClass`에 정의된 `Method1` 메서드에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-141">The use of the `override` modifier enables `bcdc` to access the `Method1` method that is defined in `DerivedClass`.</span></span> <span data-ttu-id="a72ff-142">일반적으로 이는 상속 계층 구조에서 원하는 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-142">Typically, that is the desired behavior in inheritance hierarchies.</span></span> <span data-ttu-id="a72ff-143">파생 클래스에서 생성된 값을 가진 개체에 파생 클래스에서 정의된 메서드를 사용하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-143">You want objects that have values that are created from the derived class to use the methods that are defined in the derived class.</span></span> <span data-ttu-id="a72ff-144">이 동작을 위해 `override`를 사용하여 기본 클래스 메서드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-144">You achieve that behavior by using `override` to extend the base class method.</span></span>  
  
 <span data-ttu-id="a72ff-145">다음 코드에는 전체 예제가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-145">The following code contains the full example.</span></span>  
  
```csharp  
using System;  
using System.Text;  
  
namespace OverrideAndNew  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            BaseClass bc = new BaseClass();  
            DerivedClass dc = new DerivedClass();  
            BaseClass bcdc = new DerivedClass();  
  
            // The following two calls do what you would expect. They call  
            // the methods that are defined in BaseClass.  
            bc.Method1();  
            bc.Method2();  
            // Output:  
            // Base - Method1  
            // Base - Method2  
  
            // The following two calls do what you would expect. They call  
            // the methods that are defined in DerivedClass.  
            dc.Method1();  
            dc.Method2();  
            // Output:  
            // Derived - Method1  
            // Derived - Method2  
  
            // The following two calls produce different results, depending
            // on whether override (Method1) or new (Method2) is used.  
            bcdc.Method1();  
            bcdc.Method2();  
            // Output:  
            // Derived - Method1  
            // Base - Method2  
        }  
    }  
  
    class BaseClass  
    {  
        public virtual void Method1()  
        {  
            Console.WriteLine("Base - Method1");  
        }  
  
        public virtual void Method2()  
        {  
            Console.WriteLine("Base - Method2");  
        }  
    }  
  
    class DerivedClass : BaseClass  
    {  
        public override void Method1()  
        {  
            Console.WriteLine("Derived - Method1");  
        }  
  
        public new void Method2()  
        {  
            Console.WriteLine("Derived - Method2");  
        }  
    }  
}  
```  
  
 <span data-ttu-id="a72ff-146">다음 예제에서는 다른 컨텍스트의 비슷한 동작을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-146">The following example illustrates similar behavior in a different context.</span></span> <span data-ttu-id="a72ff-147">이 예제에서는 `Car`라는 기본 클래스 하나와 이 클래스에서 파생된 두 클래스 `ConvertibleCar` 및 `Minivan`을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-147">The example defines three classes: a base class named `Car` and two classes that are derived from it, `ConvertibleCar` and `Minivan`.</span></span> <span data-ttu-id="a72ff-148">기본 클래스에는 `DescribeCar` 메서드가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-148">The base class contains a `DescribeCar` method.</span></span> <span data-ttu-id="a72ff-149">이 메서드는 자동차에 대한 기본 설명을 표시한 다음 `ShowDetails`를 호출하여 추가 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-149">The method displays a basic description of a car, and then calls `ShowDetails` to provide additional information.</span></span> <span data-ttu-id="a72ff-150">세 클래스는 각각 `ShowDetails` 메서드를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-150">Each of the three classes defines a `ShowDetails` method.</span></span> <span data-ttu-id="a72ff-151">`new` 한정자는 `ConvertibleCar` 클래스의 `ShowDetails`를 정의하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-151">The `new` modifier is used to define `ShowDetails` in the `ConvertibleCar` class.</span></span> <span data-ttu-id="a72ff-152">`override` 한정자는 `Minivan` 클래스의 `ShowDetails`를 정의하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-152">The `override` modifier is used to define `ShowDetails` in the `Minivan` class.</span></span>  
  
```csharp  
// Define the base class, Car. The class defines two methods,  
// DescribeCar and ShowDetails. DescribeCar calls ShowDetails, and each derived  
// class also defines a ShowDetails method. The example tests which version of  
// ShowDetails is selected, the base class method or the derived class method.  
class Car  
{  
    public void DescribeCar()  
    {  
        System.Console.WriteLine("Four wheels and an engine.");  
        ShowDetails();  
    }  
  
    public virtual void ShowDetails()  
    {  
        System.Console.WriteLine("Standard transportation.");  
    }  
}  
  
// Define the derived classes.  
  
// Class ConvertibleCar uses the new modifier to acknowledge that ShowDetails  
// hides the base class method.  
class ConvertibleCar : Car  
{  
    public new void ShowDetails()  
    {  
        System.Console.WriteLine("A roof that opens up.");  
    }  
}  
  
// Class Minivan uses the override modifier to specify that ShowDetails  
// extends the base class method.  
class Minivan : Car  
{  
    public override void ShowDetails()  
    {  
        System.Console.WriteLine("Carries seven people.");  
    }  
}  
```  
  
 <span data-ttu-id="a72ff-153">예제에서는 호출되는 `ShowDetails` 버전을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-153">The example tests which version of `ShowDetails` is called.</span></span> <span data-ttu-id="a72ff-154">다음 메서드 `TestCars1`은 각 클래스의 인스턴스를 선언한 다음 각 인스턴스에서 `DescribeCar`를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-154">The following method, `TestCars1`, declares an instance of each class, and then calls `DescribeCar` on each instance.</span></span>  
  
```csharp  
public static void TestCars1()  
{  
    System.Console.WriteLine("\nTestCars1");  
    System.Console.WriteLine("----------");  
  
    Car car1 = new Car();  
    car1.DescribeCar();  
    System.Console.WriteLine("----------");  
  
    // Notice the output from this test case. The new modifier is  
    // used in the definition of ShowDetails in the ConvertibleCar  
    // class.
  
    ConvertibleCar car2 = new ConvertibleCar();  
    car2.DescribeCar();  
    System.Console.WriteLine("----------");  
  
    Minivan car3 = new Minivan();  
    car3.DescribeCar();  
    System.Console.WriteLine("----------");  
}  
```  
  
 <span data-ttu-id="a72ff-155">`TestCars1`은 다음 출력을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-155">`TestCars1` produces the following output.</span></span> <span data-ttu-id="a72ff-156">특히 예상과 다를 수 있는 `car2`의 결과를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-156">Notice especially the results for `car2`, which probably are not what you expected.</span></span> <span data-ttu-id="a72ff-157">개체 형식은 `ConvertibleCar`이지만 `DescribeCar`는 `ConvertibleCar` 클래스에 정의된 `ShowDetails` 버전에 액세스하지 않습니다. 해당 메서드는 `override` 한정자가 아니라 `new` 한정자로 선언되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-157">The type of the object is `ConvertibleCar`, but `DescribeCar` does not access the version of `ShowDetails` that is defined in the `ConvertibleCar` class because that method is declared with the `new` modifier, not the `override` modifier.</span></span> <span data-ttu-id="a72ff-158">결과적으로 `ConvertibleCar` 개체는 `Car` 개체와 동일한 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-158">As a result, a `ConvertibleCar` object displays the same description as a `Car` object.</span></span> <span data-ttu-id="a72ff-159">`Minivan` 개체인 `car3`의 결과와 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-159">Contrast the results for `car3`, which is a `Minivan` object.</span></span> <span data-ttu-id="a72ff-160">이 경우 `Minivan` 클래스에서 선언된 `ShowDetails` 메서드가 `Car` 클래스에서 선언된 `ShowDetails` 메서드를 재정의하고, 표시되는 설명은 미니밴에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-160">In this case, the `ShowDetails` method that is declared in the `Minivan` class overrides the `ShowDetails` method that is declared in the `Car` class, and the description that is displayed describes a minivan.</span></span>  
  
```csharp  
// TestCars1  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Carries seven people.  
// ----------  
```  
  
 <span data-ttu-id="a72ff-161">`TestCars2`는 `Car` 형식인 개체 목록을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-161">`TestCars2` creates a list of objects that have type `Car`.</span></span> <span data-ttu-id="a72ff-162">개체의 값은 `Car`, `ConvertibleCar` 및 `Minivan` 클래스에서 인스턴스화됩니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-162">The values of the objects are instantiated from the `Car`, `ConvertibleCar`, and `Minivan` classes.</span></span> <span data-ttu-id="a72ff-163">목록의 각 요소에 대해 `DescribeCar`가 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-163">`DescribeCar` is called on each element of the list.</span></span> <span data-ttu-id="a72ff-164">다음 코드에서는 `TestCars2`의 정의를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-164">The following code shows the definition of `TestCars2`.</span></span>  
  
```csharp  
public static void TestCars2()  
{  
    System.Console.WriteLine("\nTestCars2");  
    System.Console.WriteLine("----------");  
  
    var cars = new List<Car> { new Car(), new ConvertibleCar(),
        new Minivan() };  
  
    foreach (var car in cars)  
    {  
        car.DescribeCar();  
        System.Console.WriteLine("----------");  
    }  
}  
```  
  
 <span data-ttu-id="a72ff-165">다음 출력이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-165">The following output is displayed.</span></span> <span data-ttu-id="a72ff-166">이 출력은 `TestCars1`이 표시하는 출력과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-166">Notice that it is the same as the output that is displayed by `TestCars1`.</span></span> <span data-ttu-id="a72ff-167">개체의 형식이 `ConvertibleCar`(`TestCars1`) 또는 `Car`(`TestCars2`)이든 관계없이 `ConvertibleCar` 클래스의 `ShowDetails` 메서드는 호출되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-167">The `ShowDetails` method of the `ConvertibleCar` class is not called, regardless of whether the type of the object is `ConvertibleCar`, as in `TestCars1`, or `Car`, as in `TestCars2`.</span></span> <span data-ttu-id="a72ff-168">한편, `car3`은 `Minivan` 형식 또는 `Car` 형식이든 관계없이 두 경우 모두 `Minivan` 클래스에서 `ShowDetails` 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-168">Conversely, `car3` calls the `ShowDetails` method from the `Minivan` class in both cases, whether it has type `Minivan` or type `Car`.</span></span>  
  
```csharp  
// TestCars2  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Carries seven people.  
// ----------  
```  
  
 <span data-ttu-id="a72ff-169">`TestCars3` 및 `TestCars4` 메서드가 예제를 완성합니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-169">Methods `TestCars3` and `TestCars4` complete the example.</span></span> <span data-ttu-id="a72ff-170">이러한 메서드는 `ConvertibleCar` 및 `Minivan`(`TestCars3`) 형식으로 선언된 개체와 `Car`(`TestCars4`) 형식으로 선언된 개체에서 차례로 `ShowDetails`를 직접 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-170">These methods call `ShowDetails` directly, first from objects declared to have type `ConvertibleCar` and `Minivan` (`TestCars3`), then from objects declared to have type `Car` (`TestCars4`).</span></span> <span data-ttu-id="a72ff-171">다음 코드에서는 이러한 두 메서드를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-171">The following code defines these two methods.</span></span>  
  
```csharp  
public static void TestCars3()  
{  
    System.Console.WriteLine("\nTestCars3");  
    System.Console.WriteLine("----------");  
    ConvertibleCar car2 = new ConvertibleCar();  
    Minivan car3 = new Minivan();  
    car2.ShowDetails();  
    car3.ShowDetails();  
}  
  
public static void TestCars4()  
{  
    System.Console.WriteLine("\nTestCars4");  
    System.Console.WriteLine("----------");  
    Car car2 = new ConvertibleCar();  
    Car car3 = new Minivan();  
    car2.ShowDetails();  
    car3.ShowDetails();  
}  
```  
  
 <span data-ttu-id="a72ff-172">메서드는 이 항목에 있는 첫 번째 예제의 결과에 해당하는 다음 출력을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-172">The methods produce the following output, which corresponds to the results from the first example in this topic.</span></span>  
  
```csharp  
// TestCars3  
// ----------  
// A roof that opens up.  
// Carries seven people.  
  
// TestCars4  
// ----------  
// Standard transportation.  
// Carries seven people.  
```  
  
 <span data-ttu-id="a72ff-173">다음 코드에서는 전체 프로젝트와 해당 출력을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a72ff-173">The following code shows the complete project and its output.</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
  
namespace OverrideAndNew2  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // Declare objects of the derived classes and test which version  
            // of ShowDetails is run, base or derived.  
            TestCars1();  
  
            // Declare objects of the base class, instantiated with the  
            // derived classes, and repeat the tests.  
            TestCars2();  
  
            // Declare objects of the derived classes and call ShowDetails  
            // directly.  
            TestCars3();  
  
            // Declare objects of the base class, instantiated with the  
            // derived classes, and repeat the tests.  
            TestCars4();  
        }  
  
        public static void TestCars1()  
        {  
            System.Console.WriteLine("\nTestCars1");  
            System.Console.WriteLine("----------");  
  
            Car car1 = new Car();  
            car1.DescribeCar();  
            System.Console.WriteLine("----------");  
  
            // Notice the output from this test case. The new modifier is  
            // used in the definition of ShowDetails in the ConvertibleCar  
            // class.
            ConvertibleCar car2 = new ConvertibleCar();  
            car2.DescribeCar();  
            System.Console.WriteLine("----------");  
  
            Minivan car3 = new Minivan();  
            car3.DescribeCar();  
            System.Console.WriteLine("----------");  
        }  
        // Output:  
        // TestCars1  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Carries seven people.  
        // ----------  
  
        public static void TestCars2()  
        {  
            System.Console.WriteLine("\nTestCars2");  
            System.Console.WriteLine("----------");  
  
            var cars = new List<Car> { new Car(), new ConvertibleCar(),
                new Minivan() };  
  
            foreach (var car in cars)  
            {  
                car.DescribeCar();  
                System.Console.WriteLine("----------");  
            }  
        }  
        // Output:  
        // TestCars2  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Carries seven people.  
        // ----------  
  
        public static void TestCars3()  
        {  
            System.Console.WriteLine("\nTestCars3");  
            System.Console.WriteLine("----------");  
            ConvertibleCar car2 = new ConvertibleCar();  
            Minivan car3 = new Minivan();  
            car2.ShowDetails();  
            car3.ShowDetails();  
        }  
        // Output:  
        // TestCars3  
        // ----------  
        // A roof that opens up.  
        // Carries seven people.  
  
        public static void TestCars4()  
        {  
            System.Console.WriteLine("\nTestCars4");  
            System.Console.WriteLine("----------");  
            Car car2 = new ConvertibleCar();  
            Car car3 = new Minivan();  
            car2.ShowDetails();  
            car3.ShowDetails();  
        }  
        // Output:  
        // TestCars4  
        // ----------  
        // Standard transportation.  
        // Carries seven people.  
    }  
  
    // Define the base class, Car. The class defines two virtual methods,  
    // DescribeCar and ShowDetails. DescribeCar calls ShowDetails, and each derived  
    // class also defines a ShowDetails method. The example tests which version of  
    // ShowDetails is used, the base class method or the derived class method.  
    class Car  
    {  
        public virtual void DescribeCar()  
        {  
            System.Console.WriteLine("Four wheels and an engine.");  
            ShowDetails();  
        }  
  
        public virtual void ShowDetails()  
        {  
            System.Console.WriteLine("Standard transportation.");  
        }  
    }  
  
    // Define the derived classes.  
  
    // Class ConvertibleCar uses the new modifier to acknowledge that ShowDetails  
    // hides the base class method.  
    class ConvertibleCar : Car  
    {  
        public new void ShowDetails()  
        {  
            System.Console.WriteLine("A roof that opens up.");  
        }  
    }  
  
    // Class Minivan uses the override modifier to specify that ShowDetails  
    // extends the base class method.  
    class Minivan : Car  
    {  
        public override void ShowDetails()  
        {  
            System.Console.WriteLine("Carries seven people.");  
        }  
    }  
  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a72ff-174">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a72ff-174">See also</span></span>

- [<span data-ttu-id="a72ff-175">C# 프로그래밍 가이드</span><span class="sxs-lookup"><span data-stu-id="a72ff-175">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a72ff-176">클래스 및 구조체</span><span class="sxs-lookup"><span data-stu-id="a72ff-176">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="a72ff-177">Override 및 New 키워드를 사용하여 버전 관리</span><span class="sxs-lookup"><span data-stu-id="a72ff-177">Versioning with the Override and New Keywords</span></span>](./versioning-with-the-override-and-new-keywords.md)
- [<span data-ttu-id="a72ff-178">base</span><span class="sxs-lookup"><span data-stu-id="a72ff-178">base</span></span>](../../language-reference/keywords/base.md)
- [<span data-ttu-id="a72ff-179">abstract</span><span class="sxs-lookup"><span data-stu-id="a72ff-179">abstract</span></span>](../../language-reference/keywords/abstract.md)
