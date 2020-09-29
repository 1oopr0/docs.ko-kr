---
title: 리플렉션을 사용하여 특성 액세스(C#)
description: GetCustomAttributes 메서드를 사용하여 C#에서 사용자 지정 특성으로 정의된 정보를 가져오려면 리플렉션을 사용합니다.
ms.date: 07/20/2015
ms.assetid: dce3a696-4ceb-489a-b5e4-322a83052f18
ms.openlocfilehash: 2ed4e844d1c98bcf265572f201bce6679fd642e9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202632"
---
# <a name="accessing-attributes-by-using-reflection-c"></a><span data-ttu-id="bf833-103">리플렉션을 사용하여 특성 액세스(C#)</span><span class="sxs-lookup"><span data-stu-id="bf833-103">Accessing Attributes by Using Reflection (C#)</span></span>

<span data-ttu-id="bf833-104">어느 정도 해당 정보를 검색하고 이에 따라 작업을 수행하지 않는다면 사용자 지정 특성을 정의하고 소스 코드에 배치할 수 있다는 사실은 별로 중요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bf833-104">The fact that you can define custom attributes and place them in your source code would be of little value without some way of retrieving that information and acting on it.</span></span> <span data-ttu-id="bf833-105">리플렉션을 통해 사용자 지정 특성을 사용하여 정의된 정보를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf833-105">By using reflection, you can retrieve the information that was defined with custom attributes.</span></span> <span data-ttu-id="bf833-106">핵심 메서드는 소스 코드 특성에 해당하는 런타임 항목인 개체의 배열을 반환하는 `GetCustomAttributes`입니다.</span><span class="sxs-lookup"><span data-stu-id="bf833-106">The key method is `GetCustomAttributes`, which returns an array of objects that are the run-time equivalents of the source code attributes.</span></span> <span data-ttu-id="bf833-107">이 메서드에는 여러 개의 오버로드된 버전이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf833-107">This method has several overloaded versions.</span></span> <span data-ttu-id="bf833-108">자세한 내용은 <xref:System.Attribute>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bf833-108">For more information, see <xref:System.Attribute>.</span></span>  
  
 <span data-ttu-id="bf833-109">다음과 같은 특성 사양은</span><span class="sxs-lookup"><span data-stu-id="bf833-109">An attribute specification such as:</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
```  
  
 <span data-ttu-id="bf833-110">다음과 개념적으로 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="bf833-110">is conceptually equivalent to this:</span></span>  
  
```csharp  
Author anonymousAuthorObject = new Author("P. Ackerman");  
anonymousAuthorObject.version = 1.1;  
```  
  
 <span data-ttu-id="bf833-111">하지만 `SampleClass`에서 특성을 쿼리할 때까지 코드가 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bf833-111">However, the code is not executed until `SampleClass` is queried for attributes.</span></span> <span data-ttu-id="bf833-112">`SampleClass`에서 `GetCustomAttributes`를 호출하면 `Author` 개체가 위와 같이 구성 및 초기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf833-112">Calling `GetCustomAttributes` on `SampleClass` causes an `Author` object to be constructed and initialized as above.</span></span> <span data-ttu-id="bf833-113">클래스에 다른 특성이 있으면 다른 특성 개체가 비슷하게 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf833-113">If the class has other attributes, other attribute objects are constructed similarly.</span></span> <span data-ttu-id="bf833-114">그런 다음 `GetCustomAttributes`는 `Author` 개체 및 기타 특성 개체를 배열로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bf833-114">`GetCustomAttributes` then returns the `Author` object and any other attribute objects in an array.</span></span> <span data-ttu-id="bf833-115">이 배열을 반복하고, 각 배열 요소의 형식에 따라 적용된 특성을 확인하고, 특성 개체에서 정보를 추출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf833-115">You can then iterate over this array, determine what attributes were applied based on the type of each array element, and extract information from the attribute objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf833-116">예제</span><span class="sxs-lookup"><span data-stu-id="bf833-116">Example</span></span>  

 <span data-ttu-id="bf833-117">아래는 완성된 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="bf833-117">Here is a complete example.</span></span> <span data-ttu-id="bf833-118">사용자 지정 특성이 정의되어 있고 여러 엔터티에 적용되었으며 리플렉션을 통해 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="bf833-118">A custom attribute is defined, applied to several entities, and retrieved via reflection.</span></span>  
  
```csharp  
// Multiuse attribute.  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // Multiuse attribute.  
]  
public class Author : System.Attribute  
{  
    string name;  
    public double version;  
  
    public Author(string name)  
    {  
        this.name = name;  
  
        // Default value.  
        version = 1.0;  
    }  
  
    public string GetName()  
    {  
        return name;  
    }  
}  
  
// Class with the Author attribute.  
[Author("P. Ackerman")]  
public class FirstClass  
{  
    // ...  
}  
  
// Class without the Author attribute.  
public class SecondClass  
{  
    // ...  
}  
  
// Class with multiple Author attributes.  
[Author("P. Ackerman"), Author("R. Koch", version = 2.0)]  
public class ThirdClass  
{  
    // ...  
}  
  
class TestAuthorAttribute  
{  
    static void Test()  
    {  
        PrintAuthorInfo(typeof(FirstClass));  
        PrintAuthorInfo(typeof(SecondClass));  
        PrintAuthorInfo(typeof(ThirdClass));  
    }  
  
    private static void PrintAuthorInfo(System.Type t)  
    {  
        System.Console.WriteLine("Author information for {0}", t);  
  
        // Using reflection.  
        System.Attribute[] attrs = System.Attribute.GetCustomAttributes(t);  // Reflection.  
  
        // Displaying output.  
        foreach (System.Attribute attr in attrs)  
        {  
            if (attr is Author)  
            {  
                Author a = (Author)attr;  
                System.Console.WriteLine("   {0}, version {1:f}", a.GetName(), a.version);  
            }  
        }  
    }  
}  
/* Output:  
    Author information for FirstClass  
       P. Ackerman, version 1.00  
    Author information for SecondClass  
    Author information for ThirdClass  
       R. Koch, version 2.00  
       P. Ackerman, version 1.00  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="bf833-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bf833-119">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="bf833-120">C# 프로그래밍 가이드</span><span class="sxs-lookup"><span data-stu-id="bf833-120">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="bf833-121">특성에 저장된 정보 검색</span><span class="sxs-lookup"><span data-stu-id="bf833-121">Retrieving Information Stored in Attributes</span></span>](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)
- [<span data-ttu-id="bf833-122">리플렉션(C#)</span><span class="sxs-lookup"><span data-stu-id="bf833-122">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="bf833-123">특성(C#)</span><span class="sxs-lookup"><span data-stu-id="bf833-123">Attributes (C#)</span></span>](./index.md)
- [<span data-ttu-id="bf833-124">사용자 지정 특성 만들기(C#)</span><span class="sxs-lookup"><span data-stu-id="bf833-124">Creating Custom Attributes (C#)</span></span>](./creating-custom-attributes.md)
