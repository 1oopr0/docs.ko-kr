---
title: 여러 소스로 개체 컬렉션을 채우는 방법(LINQ)(C#)
description: C#에서 LINQ를 사용하여 여러 소스의 데이터를 새 형식의 시퀀스에 병합하는 방법에 대해 알아봅니다. 이러한 예제에서는 익명 및 명명된 형식을 모두 사용합니다.
ms.date: 06/12/2018
ms.assetid: 8ad7d480-b46c-4ccc-8c57-76f2d04ccc6d
ms.openlocfilehash: 9dc9f98ae09e0fe3437b5d2ccab32b3dbcd93714
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104726"
---
# <a name="how-to-populate-object-collections-from-multiple-sources-linq-c"></a><span data-ttu-id="9ec29-104">여러 소스로 개체 컬렉션을 채우는 방법(LINQ)(C#)</span><span class="sxs-lookup"><span data-stu-id="9ec29-104">How to populate object collections from multiple sources (LINQ) (C#)</span></span>

<span data-ttu-id="9ec29-105">이 예제에서는 여러 소스의 데이터를 새 형식의 시퀀스에 병합하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9ec29-105">This example shows how to merge data from different sources into a sequence of new types.</span></span>

> [!NOTE]
> <span data-ttu-id="9ec29-106">메모리 내 데이터 또는 파일 시스템의 데이터와 아직 데이터베이스에 있는 데이터를 조인하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="9ec29-106">Don't try to join in-memory data or data in the file system with data that is still in a database.</span></span> <span data-ttu-id="9ec29-107">이러한 도메인 간 조인을 사용하면 데이터베이스 쿼리 및 다른 소스 유형에 대해 조인 작업이 정의될 수 있는 다양한 방법으로 인해 정의되지 않은 결과가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ec29-107">Such cross-domain joins can yield undefined results because of different ways in which join operations might be defined for database queries and other types of sources.</span></span> <span data-ttu-id="9ec29-108">또한 데이터베이스의 데이터 양이 충분히 큰 경우 이러한 작업으로 인해 메모리 부족 예외가 발생할 수 있는 위험이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ec29-108">Additionally, there is a risk that such an operation could cause an out-of-memory exception if the amount of data in the database is large enough.</span></span> <span data-ttu-id="9ec29-109">데이터베이스의 데이터를 메모리 내 데이터에 조인하려면 먼저 데이터베이스 쿼리에서 `ToList` 또는 `ToArray`를 호출한 다음 반환된 컬렉션에서 조인을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="9ec29-109">To join data from a database to in-memory data, first call `ToList` or `ToArray` on the database query, and then perform the join on the returned collection.</span></span>

## <a name="to-create-the-data-file"></a><span data-ttu-id="9ec29-110">데이터 파일을 만들려면</span><span class="sxs-lookup"><span data-stu-id="9ec29-110">To create the data file</span></span>

<span data-ttu-id="9ec29-111">[서로 다른 파일의 콘텐츠를 조인하는 방법(LINQ)(C#)](./how-to-join-content-from-dissimilar-files-linq.md)에 설명된 대로 names.csv 및 scores.csv 파일을 해당 프로젝트 폴더에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="9ec29-111">Copy the names.csv and scores.csv files into your project folder, as described in [How to join content from dissimilar files (LINQ) (C#)](./how-to-join-content-from-dissimilar-files-linq.md).</span></span>

## <a name="example"></a><span data-ttu-id="9ec29-112">예제</span><span class="sxs-lookup"><span data-stu-id="9ec29-112">Example</span></span>

<span data-ttu-id="9ec29-113">다음 예제에서는 명명된 형식 `Student`를 사용하여 스프레드시트 데이터를 시뮬레이트하는 두 개의 메모리 내 문자열 컬렉션의 병합된 데이터를 .csv 형식으로 저장하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9ec29-113">The following example shows how to use a named type `Student` to store merged data from two in-memory collections of strings that simulate spreadsheet data in .csv format.</span></span> <span data-ttu-id="9ec29-114">첫 번째 문자열 컬렉션은 학생 이름과 ID를 나타내고, 두 번째 컬렉션은 학생 ID(첫 번째 열)와 4개의 시험 점수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9ec29-114">The first collection of strings represents the student names and IDs, and the second collection represents the student ID (in the first column) and four exam scores.</span></span> <span data-ttu-id="9ec29-115">ID는 외래 키로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ec29-115">The ID is used as the foreign key.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;

class Student
{
    public string FirstName { get; set; }
    public string LastName { get; set; }
    public int ID { get; set; }
    public List<int> ExamScores { get; set; }
}

class PopulateCollection
{
    static void Main()
    {
        // These data files are defined in How to join content from
        // dissimilar files (LINQ).

        // Each line of names.csv consists of a last name, a first name, and an
        // ID number, separated by commas. For example, Omelchenko,Svetlana,111
        string[] names = System.IO.File.ReadAllLines(@"../../../names.csv");

        // Each line of scores.csv consists of an ID number and four test
        // scores, separated by commas. For example, 111, 97, 92, 81, 60
        string[] scores = System.IO.File.ReadAllLines(@"../../../scores.csv");

        // Merge the data sources using a named type.
        // var could be used instead of an explicit type. Note the dynamic
        // creation of a list of ints for the ExamScores member. The first item
        // is skipped in the split string because it is the student ID,
        // not an exam score.
        IEnumerable<Student> queryNamesScores =
            from nameLine in names
            let splitName = nameLine.Split(',')
            from scoreLine in scores
            let splitScoreLine = scoreLine.Split(',')
            where Convert.ToInt32(splitName[2]) == Convert.ToInt32(splitScoreLine[0])
            select new Student()
            {
                FirstName = splitName[0],
                LastName = splitName[1],
                ID = Convert.ToInt32(splitName[2]),
                ExamScores = (from scoreAsText in splitScoreLine.Skip(1)
                              select Convert.ToInt32(scoreAsText)).
                              ToList()
            };

        // Optional. Store the newly created student objects in memory
        // for faster access in future queries. This could be useful with
        // very large data files.
        List<Student> students = queryNamesScores.ToList();

        // Display each student's name and exam score average.
        foreach (var student in students)
        {
            Console.WriteLine("The average score of {0} {1} is {2}.",
                student.FirstName, student.LastName,
                student.ExamScores.Average());
        }

        //Keep console window open in debug mode
        Console.WriteLine("Press any key to exit.");
        Console.ReadKey();
    }
}
/* Output:
    The average score of Omelchenko Svetlana is 82.5.
    The average score of O'Donnell Claire is 72.25.
    The average score of Mortensen Sven is 84.5.
    The average score of Garcia Cesar is 88.25.
    The average score of Garcia Debra is 67.
    The average score of Fakhouri Fadi is 92.25.
    The average score of Feng Hanying is 88.
    The average score of Garcia Hugo is 85.75.
    The average score of Tucker Lance is 81.75.
    The average score of Adams Terry is 85.25.
    The average score of Zabokritski Eugene is 83.
    The average score of Tucker Michael is 92.
 */
```

<span data-ttu-id="9ec29-116">[select](../../../language-reference/keywords/select-clause.md) 절에서 개체 이니셜라이저는 두 소스의 데이터를 사용하여 새 `Student` 개체를 각각 인스턴스화하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ec29-116">In the [select](../../../language-reference/keywords/select-clause.md) clause, an object initializer is used to instantiate each new `Student` object by using the data from the two sources.</span></span>

<span data-ttu-id="9ec29-117">쿼리 결과를 저장할 필요가 없는 경우 무명 형식이 명명된 형식보다 더 편리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ec29-117">If you don't have to store the results of a query, anonymous types can be more convenient than named types.</span></span> <span data-ttu-id="9ec29-118">명명된 형식은 쿼리가 실행되는 메서드 외부로 쿼리 결과를 전달하는 경우에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="9ec29-118">Named types are required if you pass the query results outside the method in which the query is executed.</span></span> <span data-ttu-id="9ec29-119">다음 예제는 앞의 예제와 동일한 작업을 실행하지만 명명된 형식 대신 무명 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9ec29-119">The following example executes the same task as the previous example, but uses anonymous types instead of named types:</span></span>

```csharp
// Merge the data sources by using an anonymous type.
// Note the dynamic creation of a list of ints for the
// ExamScores member. We skip 1 because the first string
// in the array is the student ID, not an exam score.
var queryNamesScores2 =
    from nameLine in names
    let splitName = nameLine.Split(',')
    from scoreLine in scores
    let splitScoreLine = scoreLine.Split(',')
    where Convert.ToInt32(splitName[2]) == Convert.ToInt32(splitScoreLine[0])
    select new
    {
        First = splitName[0],
        Last = splitName[1],
        ExamScores = (from scoreAsText in splitScoreLine.Skip(1)
                      select Convert.ToInt32(scoreAsText))
                      .ToList()
    };

// Display each student's name and exam score average.
foreach (var student in queryNamesScores2)
{
    Console.WriteLine("The average score of {0} {1} is {2}.",
        student.First, student.Last, student.ExamScores.Average());
}
```

## <a name="see-also"></a><span data-ttu-id="9ec29-120">참조</span><span class="sxs-lookup"><span data-stu-id="9ec29-120">See also</span></span>

- [<span data-ttu-id="9ec29-121">LINQ 및 문자열(C#)</span><span class="sxs-lookup"><span data-stu-id="9ec29-121">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
- [<span data-ttu-id="9ec29-122">개체 이니셜라이저 및 컬렉션 이니셜라이저</span><span class="sxs-lookup"><span data-stu-id="9ec29-122">Object and Collection Initializers</span></span>](../../classes-and-structs/object-and-collection-initializers.md)
- [<span data-ttu-id="9ec29-123">익명 형식</span><span class="sxs-lookup"><span data-stu-id="9ec29-123">Anonymous Types</span></span>](../../classes-and-structs/anonymous-types.md)
