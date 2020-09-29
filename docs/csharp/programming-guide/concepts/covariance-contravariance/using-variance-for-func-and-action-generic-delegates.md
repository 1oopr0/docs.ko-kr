---
title: Func 및 Action 제네릭 대리자에 가변성 사용(C#)
description: 코드의 유연성을 높이기 위해 Func 및 Action 제네릭 대리자에 공변성(covariance) 및 반공변성(contravariance)을 사용하는 방법에 대해 알아봅니다.
ms.date: 07/20/2015
ms.assetid: 1826774f-2b7a-470f-b110-17cfdd6abdae
ms.openlocfilehash: 613470d7870aa6a917d19904a92e56f0e61f1ed9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176346"
---
# <a name="using-variance-for-func-and-action-generic-delegates-c"></a><span data-ttu-id="061f6-103">Func 및 Action 제네릭 대리자에 가변성 사용(C#)</span><span class="sxs-lookup"><span data-stu-id="061f6-103">Using Variance for Func and Action Generic Delegates (C#)</span></span>

<span data-ttu-id="061f6-104">이러한 예제는 메서드를 다시 사용하고 코드의 유연성을 높이기 위해 `Func` 및 `Action` 제네릭 대리자에서 공변성(covariance) 및 반공변성(contravariance)을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="061f6-104">These examples demonstrate how to use covariance and contravariance in the `Func` and `Action` generic delegates to enable reuse of methods and provide more flexibility in your code.</span></span>  
  
 <span data-ttu-id="061f6-105">공변성(covariance) 및 반공변성(contravariance)에 대한 자세한 내용은 [대리자에서의 분산(C#)](./variance-in-delegates.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="061f6-105">For more information about covariance and contravariance, see [Variance in Delegates (C#)](./variance-in-delegates.md).</span></span>  
  
## <a name="using-delegates-with-covariant-type-parameters"></a><span data-ttu-id="061f6-106">공변 형식 매개 변수가 있는 대리자 사용</span><span class="sxs-lookup"><span data-stu-id="061f6-106">Using Delegates with Covariant Type Parameters</span></span>  

 <span data-ttu-id="061f6-107">다음 예제는 `Func` 대리자에서 공변성(covariance) 지원의 이점을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="061f6-107">The following example illustrates the benefits of covariance support in the generic `Func` delegates.</span></span> <span data-ttu-id="061f6-108">`FindByTitle` 메서드는 `String` 형식의 매개 변수를 가져오고 `Employee` 형식의 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="061f6-108">The `FindByTitle` method takes a parameter of the `String` type and returns an object of the `Employee` type.</span></span> <span data-ttu-id="061f6-109">그러나 `Employee`는 `Person`을 상속하므로 이 메서드를 `Func<String, Person>` 대리자에 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="061f6-109">However, you can assign this method to the `Func<String, Person>` delegate because `Employee` inherits `Person`.</span></span>  
  
```csharp  
// Simple hierarchy of classes.  
public class Person { }  
public class Employee : Person { }  
class Program  
{  
    static Employee FindByTitle(String title)  
    {  
        // This is a stub for a method that returns  
        // an employee that has the specified title.  
        return new Employee();  
    }  
  
    static void Test()  
    {  
        // Create an instance of the delegate without using variance.  
        Func<String, Employee> findEmployee = FindByTitle;  
  
        // The delegate expects a method to return Person,  
        // but you can assign it a method that returns Employee.  
        Func<String, Person> findPerson = FindByTitle;  
  
        // You can also assign a delegate
        // that returns a more derived type
        // to a delegate that returns a less derived type.  
        findPerson = findEmployee;  
  
    }  
}  
```  
  
## <a name="using-delegates-with-contravariant-type-parameters"></a><span data-ttu-id="061f6-110">반공변 형식 매개 변수가 있는 대리자 사용</span><span class="sxs-lookup"><span data-stu-id="061f6-110">Using Delegates with Contravariant Type Parameters</span></span>  

 <span data-ttu-id="061f6-111">다음 예제에서는 제네릭 `Action` 대리자에서 반공변성(contravariance) 지원의 이점을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="061f6-111">The following example illustrates the benefits of contravariance support in the generic `Action` delegates.</span></span> <span data-ttu-id="061f6-112">`AddToContacts` 메서드는 `Person` 형식의 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="061f6-112">The `AddToContacts` method takes a parameter of the `Person` type.</span></span> <span data-ttu-id="061f6-113">그러나 `Employee`는 `Person`을 상속하므로 이 메서드를 `Action<Employee>` 대리자에 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="061f6-113">However, you can assign this method to the `Action<Employee>` delegate because `Employee` inherits `Person`.</span></span>  
  
```csharp  
public class Person { }  
public class Employee : Person { }  
class Program  
{  
    static void AddToContacts(Person person)  
    {  
        // This method adds a Person object  
        // to a contact list.  
    }  
  
    static void Test()  
    {  
        // Create an instance of the delegate without using variance.  
        Action<Person> addPersonToContacts = AddToContacts;  
  
        // The Action delegate expects
        // a method that has an Employee parameter,  
        // but you can assign it a method that has a Person parameter  
        // because Employee derives from Person.  
        Action<Employee> addEmployeeToContacts = AddToContacts;  
  
        // You can also assign a delegate
        // that accepts a less derived parameter to a delegate
        // that accepts a more derived parameter.  
        addEmployeeToContacts = addPersonToContacts;  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="061f6-114">참조</span><span class="sxs-lookup"><span data-stu-id="061f6-114">See also</span></span>

- [<span data-ttu-id="061f6-115">공변성(Covariance) 및 반공변성(Contravariance)(C#)</span><span class="sxs-lookup"><span data-stu-id="061f6-115">Covariance and Contravariance (C#)</span></span>](./index.md)
- [<span data-ttu-id="061f6-116">제네릭</span><span class="sxs-lookup"><span data-stu-id="061f6-116">Generics</span></span>](../../../../standard/generics/index.md)
