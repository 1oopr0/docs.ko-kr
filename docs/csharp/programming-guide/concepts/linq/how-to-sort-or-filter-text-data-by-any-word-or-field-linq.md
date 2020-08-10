---
title: 단어 또는 필드에 따라 텍스트 데이터를 정렬하거나 필터링하는 방법(LINQ)(C#)
description: 단어 또는 필드를 기준으로 텍스트 데이터를 정렬하거나 필터링하는 방법을 알아봅니다. 줄의 필드를 기준으로 구조화된 텍스트의 줄을 정렬하는 예제를 살펴봅니다.
ms.date: 07/20/2015
ms.assetid: 7c04d42f-4a78-42c8-9ec8-57ef18fe13a9
ms.openlocfilehash: f27ce44f4b0b05bc9094b7e108af8f65170bb58a
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301322"
---
# <a name="how-to-sort-or-filter-text-data-by-any-word-or-field-linq-c"></a><span data-ttu-id="ce3a1-104">단어 또는 필드에 따라 텍스트 데이터를 정렬하거나 필터링하는 방법(LINQ)(C#)</span><span class="sxs-lookup"><span data-stu-id="ce3a1-104">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>
<span data-ttu-id="ce3a1-105">다음 예제에서는 줄의 필드를 기준으로 쉼표로 구분된 값 등의 구조적 텍스트 줄을 정렬하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ce3a1-105">The following example shows how to sort lines of structured text, such as comma-separated values, by any field in the line.</span></span> <span data-ttu-id="ce3a1-106">필드가 런타임에 동적으로 지정될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce3a1-106">The field may be dynamically specified at runtime.</span></span> <span data-ttu-id="ce3a1-107">scores.csv의 필드가 학생의 ID 번호와 일련의 시험 성적 4개를 나타낸다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="ce3a1-107">Assume that the fields in scores.csv represent a student's ID number, followed by a series of four test scores.</span></span>  
  
### <a name="to-create-a-file-that-contains-data"></a><span data-ttu-id="ce3a1-108">데이터가 포함된 파일을 만들려면</span><span class="sxs-lookup"><span data-stu-id="ce3a1-108">To create a file that contains data</span></span>  
  
1. <span data-ttu-id="ce3a1-109">[서로 다른 파일의 콘텐츠를 조인하는 방법(LINQ)(C#)](./how-to-join-content-from-dissimilar-files-linq.md) 항목에서 scores.csv 데이터를 복사하여 솔루션 폴더에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="ce3a1-109">Copy the scores.csv data from the topic [How to join content from dissimilar files (LINQ) (C#)](./how-to-join-content-from-dissimilar-files-linq.md) and save it to your solution folder.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce3a1-110">예제</span><span class="sxs-lookup"><span data-stu-id="ce3a1-110">Example</span></span>  
  
```csharp  
public class SortLines  
{  
    static void Main()  
    {  
        // Create an IEnumerable data source  
        string[] scores = System.IO.File.ReadAllLines(@"../../../scores.csv");  
  
        // Change this to any value from 0 to 4.  
        int sortField = 1;  
  
        Console.WriteLine("Sorted highest to lowest by field [{0}]:", sortField);  
  
        // Demonstrates how to return query from a method.  
        // The query is executed here.  
        foreach (string str in RunQuery(scores, sortField))  
        {  
            Console.WriteLine(str);  
        }  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
  
    // Returns the query variable, not query results!  
    static IEnumerable<string> RunQuery(IEnumerable<string> source, int num)  
    {  
        // Split the string and sort on field[num]  
        var scoreQuery = from line in source  
                         let fields = line.Split(',')  
                         orderby fields[num] descending  
                         select line;  
  
        return scoreQuery;  
    }  
}  
/* Output (if sortField == 1):  
   Sorted highest to lowest by field [1]:  
    116, 99, 86, 90, 94  
    120, 99, 82, 81, 79  
    111, 97, 92, 81, 60  
    114, 97, 89, 85, 82  
    121, 96, 85, 91, 60  
    122, 94, 92, 91, 91  
    117, 93, 92, 80, 87  
    118, 92, 90, 83, 78  
    113, 88, 94, 65, 91  
    112, 75, 84, 91, 39  
    119, 68, 79, 88, 92  
    115, 35, 72, 91, 70  
 */  
```  
  
 <span data-ttu-id="ce3a1-111">이 예제에서는 메서드에서 쿼리 변수를 반환하는 방법도 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ce3a1-111">This example also demonstrates how to return a query variable from a method.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ce3a1-112">코드 컴파일</span><span class="sxs-lookup"><span data-stu-id="ce3a1-112">Compiling the Code</span></span>  

<span data-ttu-id="ce3a1-113">System.Linq 및 System.IO 네임스페이스에 대한 `using` 지시문을 통해 C# 콘솔 애플리케이션 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ce3a1-113">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ce3a1-114">참조</span><span class="sxs-lookup"><span data-stu-id="ce3a1-114">See also</span></span>

- [<span data-ttu-id="ce3a1-115">LINQ 및 문자열(C#)</span><span class="sxs-lookup"><span data-stu-id="ce3a1-115">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
