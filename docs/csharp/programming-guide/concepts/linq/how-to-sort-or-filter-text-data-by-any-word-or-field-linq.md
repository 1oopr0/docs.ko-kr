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
# <a name="how-to-sort-or-filter-text-data-by-any-word-or-field-linq-c"></a>단어 또는 필드에 따라 텍스트 데이터를 정렬하거나 필터링하는 방법(LINQ)(C#)
다음 예제에서는 줄의 필드를 기준으로 쉼표로 구분된 값 등의 구조적 텍스트 줄을 정렬하는 방법을 보여 줍니다. 필드가 런타임에 동적으로 지정될 수도 있습니다. scores.csv의 필드가 학생의 ID 번호와 일련의 시험 성적 4개를 나타낸다고 가정합니다.  
  
### <a name="to-create-a-file-that-contains-data"></a>데이터가 포함된 파일을 만들려면  
  
1. [서로 다른 파일의 콘텐츠를 조인하는 방법(LINQ)(C#)](./how-to-join-content-from-dissimilar-files-linq.md) 항목에서 scores.csv 데이터를 복사하여 솔루션 폴더에 저장합니다.  
  
## <a name="example"></a>예제  
  
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
  
 이 예제에서는 메서드에서 쿼리 변수를 반환하는 방법도 보여 줍니다.  
  
## <a name="compiling-the-code"></a>코드 컴파일  

System.Linq 및 System.IO 네임스페이스에 대한 `using` 지시문을 통해 C# 콘솔 애플리케이션 프로젝트를 만듭니다.
  
## <a name="see-also"></a>참조

- [LINQ 및 문자열(C#)](./linq-and-strings.md)
