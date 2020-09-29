---
title: 두 폴더의 내용을 비교하는 방법(LINQ)(C#)
description: 이 예제에서는 C#에서 LINQ 쿼리를 사용하여 파일 목록을 비교하는 세 가지 방법을 보여줍니다. 이러한 기술을 조정하여 형식에 관계없이 개체의 시퀀스를 비교할 수 있습니다.
ms.date: 07/20/2015
ms.assetid: c7c4870e-c500-4de3-afa4-2c8e07f510e6
ms.openlocfilehash: 840fda1548f36d9b9ad39c2e0d1346dfc727b106
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91165262"
---
# <a name="how-to-compare-the-contents-of-two-folders-linq-c"></a><span data-ttu-id="f19c5-104">두 폴더의 내용을 비교하는 방법(LINQ)(C#)</span><span class="sxs-lookup"><span data-stu-id="f19c5-104">How to compare the contents of two folders (LINQ) (C#)</span></span>

<span data-ttu-id="f19c5-105">이 예제에서는 두 파일 목록을 비교하는 세 가지 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f19c5-105">This example demonstrates three ways to compare two file listings:</span></span>  
  
- <span data-ttu-id="f19c5-106">두 파일 목록이 똑같은지 여부를 지정하는 부울 값 쿼리.</span><span class="sxs-lookup"><span data-stu-id="f19c5-106">By querying for a Boolean value that specifies whether the two file lists are identical.</span></span>  
  
- <span data-ttu-id="f19c5-107">양쪽 폴더에 있는 파일을 검색하기 위해 교집합 쿼리.</span><span class="sxs-lookup"><span data-stu-id="f19c5-107">By querying for the intersection to retrieve the files that are in both folders.</span></span>  
  
- <span data-ttu-id="f19c5-108">두 개 중 한 폴더에만 있는 파일을 검색하기 위해 차집합 쿼리.</span><span class="sxs-lookup"><span data-stu-id="f19c5-108">By querying for the set difference to retrieve the files that are in one folder but not the other.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="f19c5-109">여기 표시된 방법은 형식에 관계없이 개체의 시퀀스를 비교하도록 조정될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f19c5-109">The techniques shown here can be adapted to compare sequences of objects of any type.</span></span>  
  
 <span data-ttu-id="f19c5-110">여기 표시된 `FileComparer` 클래스는 표준 쿼리 연산자와 함께 사용자 지정 비교자 클래스를 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f19c5-110">The `FileComparer` class shown here demonstrates how to use a custom comparer class together with the Standard Query Operators.</span></span> <span data-ttu-id="f19c5-111">이 클래스는 실제 시나리오에서 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f19c5-111">The class is not intended for use in real-world scenarios.</span></span> <span data-ttu-id="f19c5-112">단지 각 파일의 이름 및 길이(바이트)를 사용하여 각 폴더의 내용이 똑같은지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f19c5-112">It just uses the name and length in bytes of each file to determine whether the contents of each folder are identical or not.</span></span> <span data-ttu-id="f19c5-113">실제 시나리오에서는 더 엄격한 일치 검사를 수행하도록 이 비교자를 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f19c5-113">In a real-world scenario, you should modify this comparer to perform a more rigorous equality check.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f19c5-114">예제</span><span class="sxs-lookup"><span data-stu-id="f19c5-114">Example</span></span>  
  
```csharp  
namespace QueryCompareTwoDirs  
{  
    class CompareDirs  
    {  
  
        static void Main(string[] args)  
        {  
  
            // Create two identical or different temporary folders
            // on a local drive and change these file paths.  
            string pathA = @"C:\TestDir";  
            string pathB = @"C:\TestDir2";  
  
            System.IO.DirectoryInfo dir1 = new System.IO.DirectoryInfo(pathA);  
            System.IO.DirectoryInfo dir2 = new System.IO.DirectoryInfo(pathB);  
  
            // Take a snapshot of the file system.  
            IEnumerable<System.IO.FileInfo> list1 = dir1.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
            IEnumerable<System.IO.FileInfo> list2 = dir2.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
            //A custom file comparer defined below  
            FileCompare myFileCompare = new FileCompare();  
  
            // This query determines whether the two folders contain  
            // identical file lists, based on the custom file comparer  
            // that is defined in the FileCompare class.  
            // The query executes immediately because it returns a bool.  
            bool areIdentical = list1.SequenceEqual(list2, myFileCompare);  
  
            if (areIdentical == true)  
            {  
                Console.WriteLine("the two folders are the same");  
            }  
            else  
            {  
                Console.WriteLine("The two folders are not the same");  
            }  
  
            // Find the common files. It produces a sequence and doesn't
            // execute until the foreach statement.  
            var queryCommonFiles = list1.Intersect(list2, myFileCompare);  
  
            if (queryCommonFiles.Any())  
            {  
                Console.WriteLine("The following files are in both folders:");  
                foreach (var v in queryCommonFiles)  
                {  
                    Console.WriteLine(v.FullName); //shows which items end up in result list  
                }  
            }  
            else  
            {  
                Console.WriteLine("There are no common files in the two folders.");  
            }  
  
            // Find the set difference between the two folders.  
            // For this example we only check one way.  
            var queryList1Only = (from file in list1  
                                  select file).Except(list2, myFileCompare);  
  
            Console.WriteLine("The following files are in list1 but not list2:");  
            foreach (var v in queryList1Only)  
            {  
                Console.WriteLine(v.FullName);  
            }  
  
            // Keep the console window open in debug mode.  
            Console.WriteLine("Press any key to exit.");  
            Console.ReadKey();  
        }  
    }  
  
    // This implementation defines a very simple comparison  
    // between two FileInfo objects. It only compares the name  
    // of the files being compared and their length in bytes.  
    class FileCompare : System.Collections.Generic.IEqualityComparer<System.IO.FileInfo>  
    {  
        public FileCompare() { }  
  
        public bool Equals(System.IO.FileInfo f1, System.IO.FileInfo f2)  
        {  
            return (f1.Name == f2.Name &&  
                    f1.Length == f2.Length);  
        }  
  
        // Return a hash that reflects the comparison criteria. According to the
        // rules for IEqualityComparer<T>, if Equals is true, then the hash codes must  
        // also be equal. Because equality as defined here is a simple value equality, not  
        // reference identity, it is possible that two or more objects will produce the same  
        // hash code.  
        public int GetHashCode(System.IO.FileInfo fi)  
        {  
            string s = $"{fi.Name}{fi.Length}";
            return s.GetHashCode();  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f19c5-115">코드 컴파일</span><span class="sxs-lookup"><span data-stu-id="f19c5-115">Compiling the Code</span></span>  

 <span data-ttu-id="f19c5-116">System.Linq 및 System.IO 네임스페이스에 대한 `using` 지시문을 통해 C# 콘솔 애플리케이션 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f19c5-116">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f19c5-117">참조</span><span class="sxs-lookup"><span data-stu-id="f19c5-117">See also</span></span>

- [<span data-ttu-id="f19c5-118">LINQ to Objects(C#)</span><span class="sxs-lookup"><span data-stu-id="f19c5-118">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
- [<span data-ttu-id="f19c5-119">LINQ 및 파일 디렉터리(C#)</span><span class="sxs-lookup"><span data-stu-id="f19c5-119">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
