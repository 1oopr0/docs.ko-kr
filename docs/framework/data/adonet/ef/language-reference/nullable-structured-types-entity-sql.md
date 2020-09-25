---
title: null 허용 구조적 형식(Entity SQL)
ms.date: 03/30/2017
ms.assetid: ae006fa9-997e-45bb-8a04-a7f62026171e
ms.openlocfilehash: fc2230401ef98c005ab52a845de37482c0dcf698
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202266"
---
# <a name="nullable-structured-types-entity-sql"></a><span data-ttu-id="fe3aa-102">null 허용 구조적 형식(Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="fe3aa-102">Nullable Structured Types (Entity SQL)</span></span>

<span data-ttu-id="fe3aa-103">구조적 형식의 `null` 인스턴스는 존재하지 않는 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="fe3aa-103">A `null` instance of a structured type is an instance that does not exist.</span></span> <span data-ttu-id="fe3aa-104">이는 모든 속성에 `null` 값이 있는 기존 인스턴스와 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="fe3aa-104">This is different from an existing instance in which all properties have `null` values.</span></span>  
  
 <span data-ttu-id="fe3aa-105">이 항목에서는 어떤 형식이 nullable이고 어떤 코드 패턴이 구조적 nullable 형식의 `null` 인스턴스를 생성하는지를 비롯하여 구조적 nullable형식에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fe3aa-105">This topic describes the nullable structured types, including which types are nullable and which code patterns produce `null` instances of structured nullable types.</span></span>  
  
## <a name="kinds-of-nullable-structured-types"></a><span data-ttu-id="fe3aa-106">구조적 Nullable 형식의 종류</span><span class="sxs-lookup"><span data-stu-id="fe3aa-106">Kinds of Nullable Structured Types</span></span>  

 <span data-ttu-id="fe3aa-107">구조적 nullable 형식에는 세 가지 종류가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe3aa-107">There are three kinds of nullable structure types:</span></span>  
  
- <span data-ttu-id="fe3aa-108">행 형식</span><span class="sxs-lookup"><span data-stu-id="fe3aa-108">Row types.</span></span>  
  
- <span data-ttu-id="fe3aa-109">복합 형식</span><span class="sxs-lookup"><span data-stu-id="fe3aa-109">Complex types.</span></span>  
  
- <span data-ttu-id="fe3aa-110">엔터티 형식</span><span class="sxs-lookup"><span data-stu-id="fe3aa-110">Entity types.</span></span>  
  
## <a name="code-patterns-that-produce-null-instances-of-structured-types"></a><span data-ttu-id="fe3aa-111">구조적 형식의 Null 인스턴스를 생성하는 코드 패턴</span><span class="sxs-lookup"><span data-stu-id="fe3aa-111">Code Patterns that Produce Null Instances of Structured Types</span></span>  

 <span data-ttu-id="fe3aa-112">다음 시나리오에서는 `null` 인스턴스를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="fe3aa-112">The following scenarios produce `null` instances:</span></span>  
  
- <span data-ttu-id="fe3aa-113">`null`을 구조적 형식으로 모양 결정:</span><span class="sxs-lookup"><span data-stu-id="fe3aa-113">Shaping `null` as a structured type:</span></span>  
  
    ```sql  
    TREAT (NULL AS StructuredType)  
    ```  
  
- <span data-ttu-id="fe3aa-114">기본 형식을 파생 형식으로 업캐스트:</span><span class="sxs-lookup"><span data-stu-id="fe3aa-114">Upcasting of a base type to a derived type:</span></span>  
  
    ```sql  
    TREAT (BaseType AS DerivedType)  
    ```  
  
- <span data-ttu-id="fe3aa-115">False 조건에 대한 외부 조인:</span><span class="sxs-lookup"><span data-stu-id="fe3aa-115">Outer join on false condition:</span></span>  
  
    ```sql  
    Collection1 LEFT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="fe3aa-116">--또는</span><span class="sxs-lookup"><span data-stu-id="fe3aa-116">--or</span></span>  
  
    ```sql  
    Collection1 RIGHT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="fe3aa-117">--또는</span><span class="sxs-lookup"><span data-stu-id="fe3aa-117">--or</span></span>  
  
    ```sql  
    Collection1 FULL OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
- <span data-ttu-id="fe3aa-118">`null` 참조 역참조:</span><span class="sxs-lookup"><span data-stu-id="fe3aa-118">Dereferencing a `null` reference:</span></span>  
  
    ```sql  
    DEREF(NullRef)  
    ```  
  
- <span data-ttu-id="fe3aa-119">빈 컬렉션에서 ANYELEMENT 가져오기:</span><span class="sxs-lookup"><span data-stu-id="fe3aa-119">Obtaining ANYELEMENT from an empty collection:</span></span>  
  
    ```sql  
    ANYELEMENT(EmptyCollection)  
    ```  
  
- <span data-ttu-id="fe3aa-120">구조적 형식의 `null` 인스턴스 확인:</span><span class="sxs-lookup"><span data-stu-id="fe3aa-120">Checking for `null` instances of structured types:</span></span>  
  
    ```csharp  
    ...  
    for (int i = 0; i < reader.FieldCount; i++)  
    {  
        if (reader.IsDBNull(i))  
        {  
            Console.WriteLine("[NULL]");  
        }  
        else  
        {  
            Console.WriteLine(reader.GetValue(i).ToString());  
        }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="fe3aa-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fe3aa-121">See also</span></span>

- [<span data-ttu-id="fe3aa-122">Entity SQL 개요</span><span class="sxs-lookup"><span data-stu-id="fe3aa-122">Entity SQL Overview</span></span>](entity-sql-overview.md)
